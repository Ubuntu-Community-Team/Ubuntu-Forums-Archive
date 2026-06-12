---
title: "Hardware error, possibly related to CPU microcode?"
date: 2019-09-12
forum: Hardware
---

### Post by rb643 on 2019-09-12
[COLOR=#242729][FONT=Arial][FONT=inherit]As a bit of a newbie to this I was wondering if anyone would be able to help me diagnose a potential hardware problem.[/FONT]
[FONT=inherit]Generally my system runs fine but with some memory/cpu intensive python code the system has completely crashed. The main error code I can find in my log is the following:


 ```

mce: [Hardware Error]: CPU 11: Machine Check: 0 Bank 0: b200000000070005
mce: [Hardware Error]: TSC 0 
mce: [Hardware Error]: PROCESSOR 0:50654 TIME 1568095380 SOCKET 0 APIC 18 microcode 200005e

```

[/FONT]
[FONT=inherit][FONT=inherit]Some googling has at least led me to check if I have the latest microcode (I do) and whether my system is generally up to date (it is). Overall my system runs fine and the code hasn't caused any errors on other machines so its definitely a system issue. Just not even sure where to start resolving it at this point..[/FONT][/FONT]
[FONT=inherit]
My setup:
Ubuntu 18.04.3 LTS
Intel i9-7940X @ 3.10GHz (14 core, 28 threads)
64GB RAM
ASUS ROG STRIX X299-E Gaming MB
GeForce GTX 1050i graphics[/FONT]

[/FONT][/COLOR]

---

### Post by cruzer001 on 2019-09-12
My guess is it cannot be solved on this level and IMO would be better off filing a bug report.  Its a simple process.  You will need to create a launchpad account and in terminal:
```
ubuntu-bug linux
```
Follow the prompts, it will auto process the necessary system logs to LaunchPad. 

One of the first things LaunchPad will ask is if you have tried the latest kernel.  An easy way to do that is load up 19.10.

---

