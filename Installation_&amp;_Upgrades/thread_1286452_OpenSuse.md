---
title: "OpenSuse??"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Rotax on 2009-10-09
I have Ubuntu 9.04 on hard drive wihout any windows on it. And today I install Fedora 11 as dual boot. But Ubuntu was first installation and Fedora is second installation. And then 
try add Ubuntu on menu Fedora  bootloader and then reboot then click ubuntu on menu. Nothing. So I decided to restore whole drive with Clonezilla back to orignal stage and Fedora is gone. Good grief. Now I am thinking on Opensuse as dual boot. Do Opensuse will take as dual boot on all Linux drive without any Window system?

---

### Post by tommcd on 2009-10-09
You can dual boot any number of distros from Ubuntu's grub menu. When both distros use grub, I like to install the 2nd distros grub to that distros root partition and then add this to the bottom of Ubuntu's /boot/grub/menu.lst
```

title  your_distros_name_here
configfile  (hdX,Y)/boot/grub/menu.lst

```
Replace X,Y with the drive and partition number of the 2nd distro. Remember, grub counts hard drives and partitions starting from 0.
This will chainload the 2nd distros grub after Ubuntu's grub. 
Note: This assumes Suse's menu.lst is in /boot/grub (the usual place). Also, I don't know if Suse is using grub 2 yet or not. If so, then this method will not work.
Alternatively, you could just add the 2nd distros boot info to the bottom of Ubuntu's menu.lst similar to this:
```

title    Suse
root     (hdX,Y)
kernel   /boot/vmlinuz-x.x.xx.x **root=dev/sdx,y** ro
initrd   /boot/initrd.img
savedefault
boot

```
The part I have in bold is the drive and partition numbers starting from 1, not zero as in the root line.
You can use grubs autocomplete feature to edit the above entries 'on the fly' if you can't boot Suse as per the 4th post in this old thread I dug up:
[http://ubuntuforums.org/archive/index.php/t-393379.html](http://ubuntuforums.org/archive/index.php/t-393379.html)

Also, if you have a separate home directory, and want both distros to share home, you may want to choose a different user name for Suse so all the hidden config files in home don't get mixed up.
Here is a good tutorial on grub:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

### Post by Rotax on 2009-10-09
Wow, it is long read.  I will print it. 
Thanks.

---

### Post by tommcd on 2009-10-10
> **Rotax said:**
> Wow, it is long read.  I will print it. 
Thanks.
The first link from the Ubuntu forums in my last post is all you really need to know to boot Suse from Ubuntu's grub.
The grub page from Herman's site in the second link is a good reference for grub. I have learned a lot from it.
Write back if you need more help.

---

