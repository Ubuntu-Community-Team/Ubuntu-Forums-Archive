---
title: "nvidia driver 256.53 64x on 10.10"
date: 2010-10-26
forum: Hardware
---

### Post by gufide on 2010-10-26
I want to change to this driver for driver issue: blank screen, compiz problem... So, I don't know how to install it, I read many threads that it say to ```
sudo sh NVIDIA-Linux-x86_64-256.53.run

```and that what's happens:
```
master@comput1:~$ sudo sh NVIDIA-Linux-x86_64-256.53.run
sh: Can't open NVIDIA-Linux-x86_64-256.53.run
master@comput1:~$ 

```what should I do?

---

### Post by boghadab on 2010-10-26
first thing you should ever consider doing is .....
go to start in linux then SYSTEM/ADDITIONAL DRIVERS, make sure the driver is installed and activated, if not do so and see the results, ofcourse if it works then the commands are not needed.

---

### Post by gufide on 2010-10-27
no. There is only the beta driver and it cause problem on my system

---

### Post by gufide on 2010-10-27
okay, I found a way to run it but I'm not able to install it it say:```
 You appear to be running in runlevel 1; this may cause problems.  For        
  example: some distributions that use devfs do not run the devfs daemon in    
  runlevel 1, making it difficult for `nvidia-installer` to correctly setup    
  the kernel module configuration files.  It is recommended that you quit      
  installation now and switch to runlevel 3 (`telinit 3`) before installing.   

  Quit installation now? (select 'No' to continue installation)

                               Yes           No   

```

when I say no it say that I have nouveau and it cause conflict. How can I solve this?

---

### Post by RicardoAR on 2010-10-28
switch to tty1: ctrl + alt + 1
login
sudo killall Xorg
sudo telinit 3
login again
go to the folder containing the NVIDIA-Linux-x86_64-256.53.run file
sudo sh NVIDIA-Linux-x86_64-256.53.run

Hope this help you.

Salu2.

---

### Post by gufide on 2010-10-28
ha, thank you, that work perfectly!

---

