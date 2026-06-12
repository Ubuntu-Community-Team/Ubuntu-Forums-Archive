---
title: "modprobe fglrx vx insmod fglrx.ko"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by cakars on 2007-06-19
hello
everybody
i have a little problem
with loading fglrx module
modprobe doesn't give any error messages, so it should be loaded, but lsmod shows that it isn't loaded
if i execute command insmod fglrx.ko everything works fine
but i would the module allready to be loaded during startup
fglrx is added in /etc/modules and restricted drivers are disabled
the driver version is 8.37.6

terminal output 
osis@osis-laptop:~$ sudo depmod -ae
osis@osis-laptop:~$ sudo modprobe fglrx
osis@osis-laptop:~$ lsmod | grep fglrx
osis@osis-laptop:~$ cd /lib/modules/2.6.20-16-generic/misc
osis@osis-laptop:/lib/modules/2.6.20-16-generic/misc$ sudo insmod fglrx.ko
osis@osis-laptop:/lib/modules/2.6.20-16-generic/misc$ lsmod | grep fglrx
fglrx                 652512  0 
agpgart                35400  2 fglrx,ati_agp

---

### Post by mitch.c on 2007-06-20
Why don't you try the -v switch to modprobe and  see what it 'thinks' is happening.

What is the output of:
```
$ uname -r
```
[URL="http://ubuntuforums.org/showthread.php?t=377083"]
[COLOR="Red"]UAResolved[/COLOR][/URL]

---

