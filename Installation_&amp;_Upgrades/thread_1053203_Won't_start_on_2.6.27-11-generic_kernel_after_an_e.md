---
title: "Won't start on 2.6.27-11-generic kernel after an error while performing update"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by razvanescu on 2009-01-28
hello!
I've got this problem:
tried to perform a software update, and the indicator bar stopped for a while, and recovered after 2 minutes. Later on, while trying to install a package from terminal, I've realized that i hadn't enough space on disk, so I deleted some movies from my desktop. When I rebooted my PC, I've got this error:
```
Gave up waiting for root device. Common problems:
 - Boot args (at /proc/cmdline)
    - Check rootdelay = (did the system wait long enough?)
    - Check root = (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/BA046C9D046C5E7F does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell(ash)

Enter 'help' for a list of built-in commands
(initramfs)
```
What should I do?

I'm writing now from 2.6.27-9-generic kernel - how can I remove 2.6.27-11-generic kernel and reinstall it?

Big thanks! Any help is very appreciated!

---

### Post by birddog165 on 2009-01-28
Sounds like your computer got bored with you. lolz

I wouldn't play too much with removing kernels. Can I ask what you hope to accomplish in doing so? (And then maybe I can help you out)

---

### Post by razvanescu on 2009-01-28
actually, I want a solution to this problem so that my computer starts on 2.6.27-11-generic kernel, without giving me this error

any ideas ?

---

### Post by Ug on 2009-01-29
I've just encountered the same problem when I've tried to upgrade from Ubuntu 8.04.2 LTS to Ubuntu 8.10. My compounded problem is that the original 8.10 kernel doesn't work on my system either for some reason. So now I'm stuck with no Ubuntu at all! (See _[here](http://ubuntuforums.org/showthread.php?t=1052341&highlight=keyboard+freeze)_ for more info if interested).

Any progress with this thread would be great.

---

### Post by prabhuft on 2009-01-29
I have the exact same problem, after downloading updates this morning, got stuck in the same place, then rebooted under recovery mode, tried to "ifx" the problem, didn't work, then rebootred again and came through safe / recovery mode to Kernel 9.

IN addition to this from yesterday, my firefox stopped showing the forward / backward buttons as active buttons (visible, but greyed out), and that was also after downloading updates yesterday. Not sure if this is in anyway related. Thanks
Prabhu

---

### Post by razvanescu on 2009-01-29
sudo dpkg --configure --pending
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean

sudo apt-get update
sudo apt-get --reinstall install linux-image-2.6.27.11-generic


this solved my problem !

Good luck!

---

### Post by prabhuft on 2009-01-30
it did not work for me. says it could not find the kernel. However just saw 4 updates come up all for -11 kernel. Hopefully that fixes the problem

---

### Post by hg21 on 2009-01-30
I'm also puzzled since updating to 27-11. The update did not re-write the grub menu (which has always happened before) so I'm still booting 27-9.

It has, however, put 27-11 things in /boot eg vmlinuz-2.6.27-11-generic

In /usr/src I have only  linux-headers-2.6.27-11 & linux-headers-2.6.27-11-generic

In /lib/modules I have 2.6.27-11-generic & 2.6.27-9-generic



I am a relatively new (k)ubunu user and have always configured and compiled kernel updates in the past (using Fedora).  Is there a useful doc explaining how kernel updates should work in ubuntu (what is all this "generic" stuff about?)?

---

### Post by hg21 on 2009-01-30
I have now modified the grub menu and 27-11 has booted without problem (so far).

---

### Post by killchaos6669 on 2009-04-23
I have this same problem and i see someone had solved it using sudo dpkg --configure how to i use sudo from initramfs? when i try to put in a sudo command it tells me "/bin/sh: sudo: not found"

---

