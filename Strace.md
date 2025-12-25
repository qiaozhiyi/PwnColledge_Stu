## Strace 
Strace is a powerful diagnostic, debugging and instructional userspace utility for Linux. It is used to monitor the system calls used by a program and all the signals it receives. This tool is invaluable for developers and system administrators who need to understand how a program interacts with the operating system.

About how to use it just run:
```bash
strace <filedir>
```
then it will output all the system calls.

for example(in the pwncolledge):
```bash
hacker@practice~introspecting~tracing-syscalls:~$ strace /challenge/trace-me 
execve("/challenge/trace-me", ["/challenge/trace-me"], 0x7ffce1e456d0 /* 15 vars */) = 0
alarm(11305)                            = 0
exit(0)                                 = ?
+++ exited with 0 +++
```
the output shows about the execve system call, alarm system call and exit system call.

* 1. execve: the first parameter is the file path, the second parameter is the arguments and the third parameter is the environment variables. Return value 0 means success, -1 means fail. In the example, the execve system call,

etc. about the first parameter, is about arg[0],normally is the file path.

* 2. alarm: the parameter is the time limit for the program to run.

etc. you normally seek it in pwn challenge.cause it helps to avoid infinite loop(crack).

* 3. exit: the parameter is the return value of the program.Just like the other side of execve.The return value if 0 means success,other value means fail.