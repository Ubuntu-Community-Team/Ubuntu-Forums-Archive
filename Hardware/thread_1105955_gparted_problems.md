---
title: "gparted problems"
date: 2009-03-25
forum: Hardware
---

### Post by peauxdunk on 2009-03-25
I'm a bit stunned, so bear with me: Laptop is Asus F8VA-C1

I was using gparted to just move a partition (left) about 10 gigs. A few percent into it (about 3%) I accidentally hit the "X" instead of minimizing. Upon restarting, naturally my windows boot was dead (it was Vista). I now get a the BSOD Stop error:)x0000007b. 

I've already wiped the drive clean, reset the MBR, done everything but a chkdsk /f (I can't get to a prompt to do so). I can still run ubuntu fine, but I don't have a vista disk so I can't get to a recovery console. The recovery partition is gone also. What exactly did gparted do to make reloading windows fail every time at XP setup? Any ideas on how to fix it?

Note: I've been going through every programon UltimatebootCD for 2 days.. no dice yet. I'm open to any suggestions. Thanks in advance.

---

### Post by mhgsys on 2009-03-25
> 

What exactly did gparted do to make reloading windows fail every time at XP setup? Any ideas on how to fix it?



If you mean that Xp setup is not installing onto your hard drive.
My guess is that windows doesn't recognize the partitions anymore.

you could run gparted in ubuntu, remove the false ntfs partitions and make it free space so Xp can use that. 
Or you could make a new ntfs partition wich windows will see also.

Anyway, Remember that if you reinstall your windows, you'll also have to reinstall grub, cause windows will write over the mbr, leaving you with the Xp bootloader, and you won't be able to boot your linux

anyway, to reinstall grub,  this is a good way to do that:

Boot the ubuntu live cd

Open a Terminal and type:
```

sudo grub

```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```

find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```

root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```

setup (hd0)

```
Finally exit the grub shell
```

quit

```

Then, Boot ubuntu from your harddisk again, 
open a terminal 
```

sudo nano /boot/grub/menu.lst

```

scroll down to ### END DEBIAN AUTOMAGIC KERNELS LIST

and add 
```

title           XP-Professional
root            (hd0,0)
chainloader     +1


```

Hit Ctrl + O to write it
enter.
Hit Ctrl + X to exit

reboot, 
and you should have a working dual boot again.

---

### Post by peauxdunk on 2009-03-26
Now I can see the XP-Professional in Grub, but when I go to do the setup, it BSOD's on me, giving me that Stop error. Dang. I'll keep trying, but thank you for your help.

---

### Post by mhgsys on 2009-03-26
could you Open up a terminal.
```

sudo fdisk -l

```
it will ask for you password, enter it and then post the output here.
also do

```
cat /etc/fstab 

```

and post the output here.

---

