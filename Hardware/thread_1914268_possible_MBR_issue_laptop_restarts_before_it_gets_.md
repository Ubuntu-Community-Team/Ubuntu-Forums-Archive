---
title: "possible MBR issue? laptop restarts before it gets to grub screen"
date: 2012-01-24
forum: Hardware
---

### Post by steve.a on 2012-01-24
Hi everyone,

I have a Sony VAIO FZ490 laptop on which i have installed ubuntu 10.04.3 LTS and it has been working well for quite a well until suddenly yesterday morning it no longer booted. When i boot the machine it restarts before it gets to the grub screen and keeps doing just that. I have grub 2 btw.
I could boot from a DVD drive so I started ubuntu in live mode and i could mount alll the partitions on my hard drive. I guess that means that the drive is ok. Could this be a possible corruption of the master boot record. if so how can i fix it?
Any suggestions much appreciated.
thanks

---

### Post by WthIteh on 2012-01-24
Considering that your "/" partition is on /dev/sda1 you could install grub and MBR stuff again from live CD as follow (run as root):
```
mount /dev/sda1 /mnt
grub-install --boot-directory=/mnt/boot /dev/sda
umount /mnt
```

---

### Post by steve.a on 2012-01-24
i have a boot partition under /dev/sda6. could it harm it if i reinstall the MBR when the problem is somewhere else?

---

### Post by WthIteh on 2012-01-24
> **steve.a said:**
> i have a boot partition under /dev/sda6. could it harm it if i reinstall the MBR when the problem is somewhere else?
Logically it should not, but nobody can be sure. So backing up important data is always a worthy work.
The grub is already there, so reinstalling it must not cause any other issue.

---

### Post by nipunshakya on 2012-01-24
> **steve.a said:**
> Hi everyone,

I have a Sony VAIO FZ490 laptop on which i have installed ubuntu 10.04.3 LTS and it has been working well for quite a well until suddenly yesterday morning it no longer booted. When i boot the machine it restarts before it gets to the grub screen and keeps doing just that. I have grub 2 btw.
I could boot from a DVD drive so I started ubuntu in live mode and i could mount alll the partitions on my hard drive. I guess that means that the drive is ok. Could this be a possible corruption of the master boot record. if so how can i fix it?
Any suggestions much appreciated.
thanks

Hi. if you want a graphical method to fix your problem out, i would suggest you see the following link:

[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair](http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair)

boot in live mode, and install as adviced in the link and act accordingly. Hope that helps.

Regards,WinuxUser

---

### Post by steve.a on 2012-01-26
ok so i tried the boot repair option and it did not work. I got thrown to a grub resuce prompt at startup. So i rebooted off the live CD and reinstalled manually. Since i have separate partitions for home and boot, I mounted my / partition under mnt, my boot partition under mnt/boot and my home partition under mnt/home and then issued grub-install --root-directory=mnt/boot /dev/sda

I rebooted and now i get thrown to a grub prompt console.

Please help

---

### Post by oldfred on 2012-01-26
Reinstall of grub is different if you have a separate /boot partition. You also have to mount the /boot as well as the / partition on reinstall. Standard desktops do not have a separte /boot.

The Boot-Repair lets also specify a separate /boot partition on fixes. If that does not work from Boot Repair run the bootinfoscript and post the link it creates so we can review your entire configuration.

---

### Post by Zimmer on 2012-01-26
Reinstall GRUB 

 GRUB 2 can be installed even while you are booted in the OS. You do not need a live environment for that. Just execute the grub-install command against the device or the partition you desire. 

 grub-install <target> 

<target> can be /dev/sda, /dev/sdb, /dev/sdc4, and so forth.

However, you NEED the live CD as this is your only install and it does not boot!.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

item 13. shows the command required (after mounting your main / partition and in your case  your /boot partition ) as

> sudo grub-install --root-directory=/mnt /dev/sdX

where X is the letter related to your main drive, normally 'a'  thus /dev/sda.

This will place GRUB on the MBR (and link to your /boot partition).

Read the forum thread section 13.thoroughly before you begin...

---

