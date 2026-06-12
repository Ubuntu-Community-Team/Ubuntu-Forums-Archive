---
title: "Boot problem, I R STOPUD"
date: 2008-09-23
forum: Gentoo and derivatives
---

### Post by ratmandall on 2008-09-23
So I got up to installing a boot loader I chose grub but it failed(grub error, something like getdeptlist dept list empty)

Next time around I decided to skip installing a boot loader and choose none even tho it specified it may not be able to boot, it finished the install this time, restart my system gets to the point where it simply sit's there waiting for the operating system to boot and does nothing.

Ill get to my point, is there anyway to install grub off a live cd without installing another distro along with it, so that it recognises my gentoo install and I can boot into it.

:lolflag:

---

### Post by Bucky Ball on 2008-09-23
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That shows you how. :)

---

### Post by ratmandall on 2008-09-23
> **Bucky Ball said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That shows you how. :)

Thanks ill have a look.

Edit:can't find stage1 in grub
```
# find /boot/grub/stage1
# ERROR 15:File not found
```

---

### Post by trimeta on 2008-09-23
I don't know exactly which parts of the Gentoo install you skipped, but you can always boot back with the Gentoo LiveCD, mount and chroot into your hard drive, and pick up right where you left off (without repeating the steps you already performed). If you've done everything except installing Grub, you can just redo that one step and things should work.

---

### Post by Bucky Ball on 2008-09-23
> **ratmandall said:**
> 

Edit:can't find stage1 in grub
```
# find /boot/grub/stage1
# ERROR 15:File not found
```

Okay, to keep it simple, download supergrubdisk from here:

[www.supergrubdisk.org]("http://www.supergrubdisk.org")

Burn a bootable cd, boot from that and supergrub to the rescue, with any luck. If your are interested, the error, a common one, is outlined here:

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by caljohnsmith on 2008-09-23
If you didn't install Grub at all, then there won't be any Grub files in /boot/grub on your Gentoo partition, and thus you won't be able to use the procedure outlined in the link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That is why the Grub command "find /boot/grub/stage1" didn't find anything. :) But you can install Grub's system files (stage1, stage2, device.map, etc), and also install Grub to the MBR at the same time with the command "grub-install". To do so, you will of course need to know which is your Gentoo partition. So boot your Live CD, open a terminal, and do all following commands as root; to become root, use one of the following:
```
sudo -i
su -
```
If you are using a Ubuntu Live CD, use the first command, and if you are using a Gentoo Live CD, it will probably be the second command. Next do:
```
fdisk -l
```
Notice which is your Gentoo partition in the form /dev/sdX (or maybe /dev/hdX), and continue with that:
```
mount /dev/sdX /mnt
```
Then install Grub:
```
grub-install --root-directory=/mnt /dev/sda
```
Note that you might need to change "sda" to whichever HDD has Gentoo on it. All that is left is to create a Grub menu.lst. If you know the command in Gentoo to install the Grub package, similar to the following for Ubuntu:
```
sudo apt-get install grub
```
Then we can make this work. The reason why is because you will need to run the "update-grub" command after chrooting into your Gentoo partition as trimeta alluded to earlier, and to do that you'll have to have the grub package installed in Gentoo. If you can get this far, we can take it from here, otherwise let me know how it goes or if you need more details/info.

---

### Post by Bucky Ball on 2008-09-23
caljohnsmith, you have a very good point there!

---

### Post by ratmandall on 2008-09-25
What is the root password for gentoo liveCD?
I read somewhere that it was random, so how am I meant to get root privileges?

EDIT: nevermind found out how.

---

### Post by ratmandall on 2008-09-25
> **caljohnsmith said:**
> If you didn't install Grub at all, then there won't be any Grub files in /boot/grub on your Gentoo partition, and thus you won't be able to use the procedure outlined in the link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That is why the Grub command "find /boot/grub/stage1" didn't find anything. :) But you can install Grub's system files (stage1, stage2, device.map, etc), and also install Grub to the MBR at the same time with the command "grub-install". To do so, you will of course need to know which is your Gentoo partition. So boot your Live CD, open a terminal, and do all following commands as root; to become root, use one of the following:
```
sudo -i
su -
```
If you are using a Ubuntu Live CD, use the first command, and if you are using a Gentoo Live CD, it will probably be the second command. Next do:
```
fdisk -l
```
Notice which is your Gentoo partition in the form /dev/sdX (or maybe /dev/hdX), and continue with that:
```
mount /dev/sdX /mnt
```
I get up to here and start typing the grub install command then the screen just fills with
```

/usr/sbin/spind: line 10 /bin/sleep: no such file or directory
```

I am ready to give up gahh.

---

### Post by Bucky Ball on 2008-09-25
.

---

### Post by ratmandall on 2008-09-25
> **Bucky Ball said:**
> .

Well I was just about post what happen with the super grub disk and then my computer turns off randomly:mad: Turn it back on and had to run fsck to fix a hard drive problem so I could boot into ubuntu, 

now im back to low graphics mode that I just fixed today and that fix isn't working.

I couldn't install grub because I think SGD only restores the grub that was installed with a distro and got erased by windows or some other fault.(I never installed grub on the computer I'm trying to boot gentoo on)

Anyway thanks for your help, both of you:popcorn:
:lolflag:

---

### Post by trimeta on 2008-09-25
Did you try using the Gentoo install disc again? It's capable of installing Grub for a Gentoo system (naturally), and it doesn't know or care whether you're doing the install for the first time or fixing an existing installation.

---

