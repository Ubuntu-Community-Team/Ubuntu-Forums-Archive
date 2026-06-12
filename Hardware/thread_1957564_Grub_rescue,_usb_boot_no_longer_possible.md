---
title: "Grub rescue, usb boot no longer possible"
date: 2012-04-12
forum: Hardware
---

### Post by Malavi on 2012-04-12
Hello everyone ):P,

I'm currently experiencing a really tough issue, I just spent 5 days trying to find a solution, but without success. 

Here is the problem, recently I delete my Ubuntu partition from windows. That hasn't been the idea of the year, because as many users who did the same, my computer can't boot normally since the dual-boot (handled by Grub) is all messed up. It starts with "Grub rescue" and nothing can be done. 

Pretty classic thing though, the solution is to repair the boot manager, either by installing suber grub or using the recovery windows disc...

But in my case... My optical drive doesn't work anymore since few years. So I use a USB booting device, but all I get on booting is the "dark screen cursor blink"...

Few indications related :
1) I already installed ubuntu and windows by USB booting with the SAME key on the SAME computer.
2) I tried windows installation and super grub installation, still "dark screen cursor blink"..
3) I tried all the options on the BIOS.
4) I tried to usb install win on a friend's computer with the usb key I'm using, IT WORKED perfectly.



I am now out of idea:confused: on what could be the problem and starting to slowly lose hope. Would you have any suggestions ?


My computer is a laptop Fujitsu AMILO PA 1538.

Thanks by advance.

---

### Post by oldfred on 2012-04-12
Welcome to the forums.

Often a video issue with the newer versions. You may need nomodeset or other parameter depending on what video you have.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Malavi on 2012-04-12
Thank you, but I am currently trying to boot on windows 7 32 bits, and like I said I did it before with the same computer, the same usb key and the same win version.

Could it be that it messed up the partitions files so much (since I also refitted some on the way) that a windows installation is impossible ?

---

### Post by oldfred on 2012-04-12
Windows only installs to primary NTFS partitions with the boot flag or empty/unallocated space where it can create a primary NTFS active (or boot) partition. It will not install to a logical unless you have another Windows install and does not see the Linux partitions, so it usually is better to create the NTFS partition so Windows does not mess too much with partition table. 

Some have reported that even a primary partition that was available but after the extended on the drive did not work. Not sure if they had not partitioned in advance or Windows just got confused on extended. Windows can use logical partitions for data or even a second install as it boots thru the first install in a primary.

---

### Post by Malavi on 2012-04-13
I tried to boot on Gparted to check out the partitions, but all I got is again this "dark screen blinking cursor" after selecting usb boot.

---

### Post by oldfred on 2012-04-13
Did you add the nomodeset parameter? That is the most common solution to the lack of video.

---

### Post by efflandt on 2012-04-14
When you boot from USB flash memory it takes much longer to boot, so are you sure that you are giving it enough time?  Depending upon what you are using, it may take over a minute.

Were you using Wubi to run Ubuntu withing Windows or did you actually have a separate Linux partition?

Often a different partition boots Windows than you think, and even if you restore the mbr to a suitable Windows mbr or using an mbr from syslinux (which does the same thing) you need to have the proper partition marked as **boot** for Windows to boot, which may be a different partition than you think (especially for Win7).

For example when I tried Ubuntu on a Dell laptop that I was setting up for someone I used Win7 to shrink its own partition and put Ubuntu with grub on sda4 with sda4 marked as boot partition (leaving Windows mbr intact), so I thought Ubuntu would be easy to remove.  However, I neglected to do an **sudo fdisk -l** before installing Ubuntu, so when I removed sda4 and marked the Win7 partition as boot, Win7 would not boot until I repaired it several times with a Win7 system disk.

When I bought a Dell desktop I discovered that Windows was actually booting from sda2 (RECOVERY) instead of sda3 (OS).  I currently have 64-bit 10.10 and its grub on sda4 and 11.10 on sdb1, and boot everything from 11.10's grub on sdb.  That is because some Dell program (I think Dell Datasafe) steps on grub2 saving data in what it "thinks" is an unused part of the sda mbr.

---

### Post by Malavi on 2012-04-15
Case closed !!

Finally, I formated my usb key in NTFS, instead of FAT32, and.. it worked like a charm.

Thanks anyway ;)

---

