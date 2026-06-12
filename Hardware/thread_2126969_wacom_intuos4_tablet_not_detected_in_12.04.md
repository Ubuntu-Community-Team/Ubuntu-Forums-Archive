---
title: "wacom intuos4 tablet not detected in 12.04"
date: 2013-03-18
forum: Hardware
---

### Post by gnr609 on 2013-03-18
Hey guys, very new to linux. Have a acer c7 chromebook running ubuntu 12.04. Wacom graphics tablet in settings shows "tablet not detected". Any help will be greatly appreciated.

---

### Post by Favux on 2013-03-18
Hi gnr609,

Welcome to Ubuntu forums!


So you installed Ubuntu Precise 12.04 on your Chromebook?

Run the following commands in a terminal with the Intuos4 plugged in and post the output.
```
lsusb
and
xinput list
```

---

### Post by gnr609 on 2013-03-19
Hey Favux, thx for the quick reply. Yeah followed some instructions from google and installed ubuntu. 
Everything seems to be running fine but this is the first problem I ran into. This is what I get:

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 004: ID 064e:d251 Suyin Corp. 
Bus 002 Device 003: ID 056a:00b8 Wacom Co., Ltd Intuos4 4x6

and

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; cyapa                                   	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

---

### Post by Favux on 2013-03-19
Alright, it is showing up in **lsusb** but not **xinput list**.  Let's check if the Wacom usb kernel driver/module wacom.ko is auto-loading.
```
lsmod | grep [Ww]acom
```
What's the output?

---

### Post by gnr609 on 2013-03-19
I don't seem to be getting anything

user@ChrUbuntu:~$ lsmod | grep [Ww]acom
user@ChrUbuntu:~$ lsmod | grep wacom
user@ChrUbuntu:~$ lsmod | grep Wacom
user@ChrUbuntu:~$

---

### Post by Favux on 2013-03-19
To "force" the module to auto-load add **wacom** to the bottom of the list of modules in the modules file at /etc/modules.
```
gksudo gedit /etc/modules
```
Should end up looking something like:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
wacom
```

---

### Post by gnr609 on 2013-03-19
Ok, after running  gksudo gedit /etc/modules, a modules(/etc)-gedit window opens up showing

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


lp
rtc

do I just type wacom on the bottom and save?
sorry for the newbness, its my first experience with linux.

---

### Post by Favux on 2013-03-19
> do I just type wacom on the bottom and save?
Yes.

Then restart.

---

### Post by gnr609 on 2013-03-19
Ok, saved and restarted. Im still not getting any output when I run  "lsmod | grep [Ww]acom"
wacom does show on the bottom of the list when I run " gksudo gedit /etc/modules"

---

### Post by Favux on 2013-03-19
OK, now we need to check if wacom.ko is present on your system.  It should be located in this directory:
```
/lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
Where **`uname -r`** is kernel version you are running currently.  There should be other modules in the tablet directory other than wacom.ko.  Is it there?

---

### Post by gnr609 on 2013-03-19
user@ChrUbuntu:~$ /lib/modules/3.4.0/kernel/drivers/input/tablet/wacom.ko
bash: /lib/modules/3.4.0/kernel/drivers/input/tablet/wacom.ko: No such file or directory

this is what I'm getting.

---

### Post by Favux on 2013-03-19
You have to use the output of:
```
uname -r
```
in a terminal in the directory path.  I just meant for you to look with Nautilus (the file manager).

---

### Post by gnr609 on 2013-03-19
Ok, under input there is no tablet listed. There are 4 folders Joystick, Misc, Mouse, and Serio
along with joydev.ko and sparse-keymap.ko. Also checked each folder and there seems to be
no wacom.ko listed.
Under modules however, there are also four 3.2.0 generic kernels listed. Those four do have a tablet folder containing 
acecad.ko, aiptek.ko, gtco.ko, hanwang.ko, kbtab.ko, and wacom.ko

---

### Post by Favux on 2013-03-19
> Under modules however, there are also four 3.2.0 generic kernels listed. Those four do have a tablet folder containing
acecad.ko, aiptek.ko, gtco.ko, hanwang.ko, kbtab.ko, and wacom.ko 
That's what I expected to see.

Generic is the most common kernel.  What is the output you get with?
```
uname -r
```
Are we dealing with some sort of chrome kernel?

---

### Post by gnr609 on 2013-03-19
user@ChrUbuntu:~$ uname -r
3.4.0

---

### Post by Favux on 2013-03-19
> 3.4.0 
What?  What the heck is that?  And by the way Precise 12.04 has the 3.2 kernel.  No Ubuntu release has the 3.4 kernel.  Does this chrome book have an ARM CPU?

I'd expect to see something like:
> 3.2.0-39-generic
Normally you could reinstall your kernel's wacom.ko by reinstalling the kernel's linux-image using Synaptic Package Manager.

> followed some instructions from google and installed ubuntu
My eyes glaze over at the thought of looking at those instructions and trying to figure out what is going on.

---

### Post by gnr609 on 2013-03-19
It has a Intel. This is the website where I got the instructions from
[http://liliputing.com/2012/11/how-to-install-ubuntu-12-04-on-the-199-acer-c7-chromebook.html](http://liliputing.com/2012/11/how-to-install-ubuntu-12-04-on-the-199-acer-c7-chromebook.html)
Is there a way I could switch over to one of the generic 3.2 kernels?

---

### Post by Favux on 2013-03-19
Seems I have been here before, sometime in the last 6 months I think.  But the other one was an ARM processor.  We thought hey, just compile input-wacom to get a working wacom.ko and we're good to go.  But it turned out there wasn't a kernel-header for the custom ARM kernel so there wasn't any way to compile wacom.ko.

With an Intel Atom processor I'd think there would be a chance.  But I have no idea how to go about doing it unless you can find a kernel-header for your current running 3.4.0.  I tend to doubt the guy who produced the custom kernel produced a kernel-header for it.  The wacom.ko has to be compiled against the kernel you are actually running, you can't "borrow" one from the generics.

---

### Post by gnr609 on 2013-03-20
I'll do some more research on. From what I understand the machine boots up with the signed kernel which i think is a chrome kernel and then switches user space to run ubuntu.
Thanks again for all your help.

---

