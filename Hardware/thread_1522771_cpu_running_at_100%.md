---
title: "cpu running at 100%"
date: 2010-07-02
forum: Hardware
---

### Post by thebiguglyone on 2010-07-02
I have run top and it is showing the following-

PID    User    PR  NI   VIRT     RES    SHR    S   %CPU   %MEM   TIME+   COMMAND
1716  root     20  0      8184    4408  2080    R    90.5     0.2         32:30    backend

Any pointers here?

Thanks

---

### Post by khelben1979 on 2010-07-02
Try with sudo top to see if it displays any processes in there. You can also try with: ```
sudo ps -A
```

Check up the process which probably have hung and kill the process with: ```
kill -9 [process number]
```

---

### Post by stressmonkey on 2010-07-02
Hi, I noticed this thread while searching the forums for a solution my current problem with CPU usage.  My CPU is also running at 100%, but it is in spikes. I took pictures of system monitor and htop, in the thread

[http://ubuntuforums.org/showthread.php?t=1520716]("http://ubuntuforums.org/showthread.php?t=1520716")

if anyone has an idea of what could be the problem, I would greatly appreciate the help. I have never experienced anything like this, and in searching the forums I have not found any solutions!

Thanks a lot

---

### Post by User_1 on 2010-07-11
ignore.

---

