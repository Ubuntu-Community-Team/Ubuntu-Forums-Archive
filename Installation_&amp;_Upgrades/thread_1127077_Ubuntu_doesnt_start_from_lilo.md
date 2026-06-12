---
title: "Ubuntu doesnt start from lilo"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by kranny on 2009-04-16
i have installed slackware on an existing ubuntu installation.I installed lilo in partition boot sector coz i wanted to boot it from grub installed with ubuntu ...but the chainloading was unsuccessful..So i  installed lilo in MBR and added the ubuntu and windows entries...now the problem is ubuntu isnt booting as expected...A low grpahics mode window is prompted when booted into ubuntu...mouse doesnt work...

My guess is it isnt booting into the right kernel...In lilo i can find only 
image=/boot/vmlinuz line under ubuntu entry...Any help is appreciated

---

### Post by tommcd on 2009-04-16
I also boot both Ubuntu and Slackware.
IMO, grub is simply much easier to manage when booting multiple linux distros than lilo.
I would recommend reinstalling grub from Ubuntu to the MBR. Hopefully it should detect your Slackware install and add it to your grub menu. See this to reinstall grub to the MBR:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
For refernce, here is my entries in grub's menu.lst from Ubuntu for booting Slackware 12.2. I have entries for both the huge and the generic kernel in my menu.lst:
```

title           Slackware-12.2-generic-smp (on /dev/sda5)
root            (hd0,4)
kernel          /boot/vmlinuz-generic-smp-2.6.27.7-smp root=/dev/sda5 ro
initrd          /boot/initrd.gz
savedefault
boot

title           Slackware-12.2-huge-smp (on /dev/sda5)
root            (hd0,4)
kernel          /boot/vmlinuz-huge-smp-2.6.27.7-smp root=/dev/sda5 ro
savedefault
boot

```
Note: The generic kernel needs an initrd line (which you must build yourself according to the instructions in /boot/README in your Slackware install). The huge kernel does not need an initrd line.

---

### Post by andrew.46 on 2009-04-17
Hi kranny,

> **kranny said:**
> i  installed lilo in MBR and added the ubuntu and windows entries...

The safest method is to install Lilo to the MBR as you have done but also install grub to the root of the Ubuntu partition. You can then chainload Ubuntu from Lilo with something like the following:


```
other=/dev/sda3
label= Ubuntu
table=/dev/sda
```

which then boots to the Ubuntu grub. You might be interested in a short thread where this was [discussed some time back]("http://www.linuxquestions.org/questions/slackware-14/advice-for-lilo-setup-dual-boot-slackware-ubuntu-613632/?highlight=chainload+ubuntu+lilo"), several different options are discussed with yours truly in the middle of it :-).

BTW don't listen to people who say lilo is dead: it is a fantastic, solid bootloader!

Andrew

---

