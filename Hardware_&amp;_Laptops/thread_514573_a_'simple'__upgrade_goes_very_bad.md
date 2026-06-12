---
title: "a 'simple'  upgrade goes very bad"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by TravMan63 on 2007-07-31
All was good in the world, until I did this

[http://ubuntuforums.org/showthread.php?t=319336](http://ubuntuforums.org/showthread.php?t=319336)
(it installed at least 75 system updates)

I was just trying to get entrance to work.
I rebooted and BAM!...:confused:

Now - I have no wireless
the touchpad / eraser do not work

when I log in -  (to gnome/enlightenment)
I receive the following error:
error creating the child process for this terminal 

Besides re installing everything - what can I do?

I have a Dell C840 with ASUS WL-107g wireless NIC

nano /proc/bus/input/devices gives this:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd
B: EV=120013
B: KEY=1007 2002000 4380207a f840d001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7
```

I can ssh into it fine ... but what should I do ?

<edit> booting into safe mode makes no change.
system 'hangs' a bit while booting at the 'network config' stage

I've edited the fstab for the 'child process error' - n/c
Tried dis and re-enabling the pointing device (there are no hot keys for this function...)


TM

/more info
last install info in log file found :
root@laptop:/var/log# cat aptitude - there were 177 updates performed!

# update, link

it was faster to backup (via ssh/xp box and winscp3 (sftp)) and reinstall the system.
see also
"Updates available" (to break your computer) - Ubuntu Forums
[http://ubuntuforums.org/showthread.php?t=408264&highlight=reactivate+wireless](http://ubuntuforums.org/showthread.php?t=408264&highlight=reactivate+wireless)

---

