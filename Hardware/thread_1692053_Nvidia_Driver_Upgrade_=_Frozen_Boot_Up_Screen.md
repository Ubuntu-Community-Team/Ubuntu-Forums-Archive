---
title: "Nvidia Driver Upgrade = Frozen Boot Up Screen?"
date: 2011-02-20
forum: Hardware
---

### Post by frankthetank727 on 2011-02-20
Just started using Ubuntu 10.10. Running on Sony Vaio and an external monitor with 4GB Ram, Nvidia Gforce Graphics card. I was running Ubuntu today and the screen on my Laptop, not the monitor would go black and flicker. I thought maybe upgrading the graphics card drivers would fix this. I went to System > Administrative > Drivers and it said that the latest Nvidia drivers were inactive. I installed them. It asked me to reboot, and now I cannot get into Ubuntu. It shows "Ubuntu 10.10" in a normal text font, then the screen freezes. What is happening? I cannot get back on it.

---

### Post by frankthetank727 on 2011-02-20
Recently installed Ubuntu 10.10, and after an attempted installation of Nvidia drivers, the bootup screen is frozen and I cannot access Login Screen, Ubunutu, anything at all. Please help. I am very frustrated.

---

### Post by frankthetank727 on 2011-02-20
Running a Sony Vaio VPCF12AFM Laptop. Ubuntu 10.10 installed great, was running fine when all of sudden screen started to flicker and dim. I thought the graphics card drivers might need updating, and I tried that via System > Administrative > Drivers and now I cannot boot up Ubuntu. The screen freezes before I can get to the login. Recovery mode is difficult, and I do not know what I am doing, and the few commands i found from other forums do not work, yielding the message "file could not be parsed or opened." I am very frustrated so if anyone has any ideas please help!

Also running dual boot with Windos 7 64 Bit, Nvidia Gforce grpahics card.

---

### Post by cariboo on 2011-02-21
Please don't create multiple threads on the same subject, I have merged your three threads.

---

### Post by mörgæs on 2011-02-21
> **frankthetank727 said:**
>  Recovery mode is difficult

Does this mean that you did get into recovery mode, or that you are trying to get there?

---

### Post by realzippy on 2011-02-21
This laptop has hybrid graphics,do not know if it is "optimus" or
a sony derivate...anyway,you will not be able to install the
nvidia driver unless you have a switch in your BIOS for the hybrid graphics.
Read [this]("http://ubuntuforums.org/showthread.php?t=1657660").

---

### Post by frankthetank727 on 2011-02-21
I got into Recovery Mode, but whenever I typed in some commands that I had found from some other threads, it would just give me the same message saying "file could not be parsed or opened" and I could not get past the screen

---

### Post by frankthetank727 on 2011-02-21
OK so i was able to get in a delete the NVidia driver, and now I am getting a flickering black screen (this is what was happening before I installed the driver). SO now what happens?

---

### Post by frankthetank727 on 2011-02-21
Ok, well now there is some new stuff going on. I let Ubuntu install a bunch of updates, and now I can:

-Get onto Ubuntu
-Use the computer without the screen flickering

However, 

The Nvidia Graphics Card is apparently "not in use" and when I try to run nvidia-xconfig it says "command not found." I Cannot seemto fix this issue, and when I install it via System > Administrative > Additional Drivers, it messed up Ubuntu and it freezes before getting to the login. As a result, my resolution cannot be set to its optimal resolution, and the monitors are unknown.

---

### Post by realzippy on 2011-02-21
Can you post the output from 

```
lspci | grep VGA
```

---

### Post by frankthetank727 on 2011-02-21
Here it is: 

```
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

```

---

### Post by frankthetank727 on 2011-02-21
Dig through some more threads and fixed it myself.

---

### Post by shredder12 on 2011-03-19
Hi! could you post the solution. I'm having a similar trouble and the only work around I have got is to disable the nvidia driver. But I hope there is another way to solve the issue.

---

