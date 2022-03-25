## Write in .exe command window from a Python scrip
```
Q:I have an application (.exe) that is coded in Fortran and when it is opened the user is intended to type 1, 2 or 3, in order to choose the calculation to run. I need to run this calculation from a Python script (open the .exe and type 1\n).

I know how to open the application with os.startfile, but I don't know how to type on it. Perhaps there is a more direct way of doing it without opening the application.

Thanks.
```

You can solve your problem with subprocess, here is an example.

```
import subprocess

# call the application (.exe)  you have
s = subprocess.Popen("main.exe", stdout=subprocess.PIPE, stdin=subprocess.PIPE, shell=True)

#input your number 1,2, or3
s.stdin.write(b"1\n")
s.stdin.close()

# get the result
out = s.stdout.read()
s.stdout.close()
print(out)
```
It's a rough program, but it might solve your problem.