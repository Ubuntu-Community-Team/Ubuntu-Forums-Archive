---
title: "boot from sata?"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by DarkManX4lf on 2005-07-08
i installed ubuntu on a sata hard drive, it went thru the first stage of install and it rebooted but when it tried to boot from the sata hard drive it hung there with an error, im pretty sure that for some reason Ubuntu doesnt load up sda drives first along with hda drivers...what ever the case how can i get ubuntu to boot from a sata drive?

also i should add that in my bios i do have it set to boot from my sata drive, and this is not a raid array it is one single, physical 80gig hard drive.

---

### Post by varunus on 2005-07-08
What was the exact error?  I'm pretty sure Ubuntu can boot from SATA drives...

---

### Post by DarkManX4lf on 2005-07-08
ok here is what i did now, i plugged in my windows drive (hd0, PATA IDE drive) and installed ubuntu on the SATA drive, and it installed GRUB on hd0, when the computer boots up and i select ubuntu it says cannot mount the partition. ive tired to reinstall and it does and says the same thing.  it wont boot windows xp either...

here is the exact error:

ERROR 17: Cannot mount the selected partition

Press any key to continue...






and it takes me back to the grub menu.....i dont get it....

---

### Post by Gezzer on 2005-07-08
unplug/disconnect the IDE drives attached to your system

install ubuntu on the pata drive

reboot in to ubuntu

close down

re-attach the IDE drives

start up the system
hit the ESC key while the boot manager is loading
use the recovery mode to ensure the IDE drives are picked up by the kernel


then the pata drive will have the MBR installed on it and the IDE drives will not be used to boot from ...

---

### Post by DarkManX4lf on 2005-07-08
do you mean SATA in stead of pata?

if so ive tried that, when i install ubuntu on the SATA drive (its the only one connected while doing this) it wont boot it says something like it cant mount /dev/sda or something like that.

---

### Post by Gezzer on 2005-07-08
sorry
yes sata

the whole install including the MBR will be on that sata drive

the system will pick up the other drives when they have been re-connected

by default they will boot (try) from the IDE drives if attached while installing the system

but this way the other drives are controlled by the boot manager on the sata ...


its the same with a windows XP install it just seems to work if the IDE drives are dis-connected when installing on sata  ...

---

### Post by DarkManX4lf on 2005-07-08
ok this is weird, when the sata drive is the only drive connected to the system its fine, and it boots ubuntu fine, but when i connect the windows drive and try to boot ubuntu, it gives me that error i mentioned above......what wrong here?

---

### Post by DarkManX4lf on 2005-07-08
thanks i got ubuntu to boot properly....now ihave a problem with my network.....usualy when i install ubuntu or windows xp it will auto detect my network and it willl work on boot...but for some reason after i installed ubuntu on the sata drive, and when booting into ubuntu my network wont work...i woudl have to go to the network s ettings and then activate eth0....also when booting into ubuntu, and when it loads all the hardware i see somewhere it said it failed, someting about "ifstate".....how do i fix   this?

---

### Post by jeremy on 2005-07-09
Have you checked your BIOS settings?

---

### Post by DarkManX4lf on 2005-07-09
i got my net connection in linux to work fine now....but i ran into another problem, since linux is installed in the SATA drive (sdb), i want to add the windws xp drive (hda) to grub, and i followed the starter guide to do it but when i select windows xp it gives    me some error and also it says its  a ext3 partition ???? but its really not....how do i fix this?

here is what i get from "fdisk -l"

root@ubuntu:~ # sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes   <---------------------- LINUX DRIVE
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9399    75497436   83  Linux
/dev/sdb2            9400        9729     2650725    5  Extended
/dev/sdb5            9400        9729     2650693+  82  Linux swap / Solaris

Disk /dev/hda: 40.0 GB, 40027029504 bytes  <-------------------------- WIN XP DRIVE
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14593   117218241    7  HPFS/NTFS






and here is the windows part from my menu.lst


title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


any suggestions ?

---

### Post by DarkManX4lf on 2005-07-09
ok i think i should add some more information, the mbr is on sdb1 (the 80gig SATA drive) and windows is located on hda1, i added windows the grub menu.lst ( i made sure it was hd0,0 which is hda) and it wont boot....

---

### Post by DarkManX4lf on 2005-07-09
ok, when i  change the option in my bios to boot from the  "hda1" drive it will boot into windows and its fine....when i change the option in the bios to boot from "sdb1" drive it will load grub and i can boot into ubuntu fine, but i cant boot into windows from grub......

---

### Post by DarkManX4lf on 2005-07-09
come on someone should know...

---

### Post by Gezzer on 2005-07-09
i believe u will have to add to the

grub~config file the other hard drive so u can boot from it via grub

sorry cant help beyond that as i only use ubuntu ...

---

### Post by DarkManX4lf on 2005-07-09
thanks but i'd rather not fiddle around with the boot stuff myself, is there anyone who knows for sure how to do this ?

---

### Post by DarkManX4lf on 2005-07-10
bump

---

### Post by DarkManX4lf on 2005-07-10
someone?

---

### Post by DarkManX4lf on 2005-07-11
anyone ?

---

### Post by al7kz on 2005-07-11
corrected

---

### Post by DarkManX4lf on 2005-07-11
[QUOTE=al7kz]Hi,

From the grub manual:

"Note that GRUB does not distinguish IDE from SCSI - it simply counts the drive numbers from zero, regardless of their type. Normally, any IDE drive number is less than any SCSI drive number, although that is not true if you change the boot sequence by swapping IDE and SCSI drives in your BIOS."

The manual is at 

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Gentoo has a pretty good explanation of installing grub manually at

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?style=printable&full=1](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?style=printable&full=1)

& search it for "grub"

and grub has a very good tab completion feature that helps you find out what drives have which designation, ie hd0, hd1, etc, and what is on each partition. It's explained in the manual and the gentoo handbook too.

I think you need to set up grub but don't change the boot sequence in bios - that switches the hd0, hd1, etc settings then the ones listed in menu.lst are incorrect.[/QUOTE]



ok according to that manual, and my bios settings, it would mean that my 80gig SATA drive which linux resides on is hd0, and in the bios i have made the WindowsXP drive as the second drive listed, and i guess that makes it hd1, so when i change the windows boot options to hd1 it says its a unknown file system....when i change it to hd2, or hd3, they both come up as ext2fs which is correct, becuse they both are...when i change it to hd4, it says it doesnt exist which is correct.  Which means that hd1 has to be the windows drive in grub, but it wont boot and it says its a unknown filesytem and it, it just hangs there, it wotn even let me go back to the grub menu....but i know for sure that windows is working and is proper because in my bios if i change the boot setting to the windows drive it boots windows perfectly fine......so.... what do i do ?

---

### Post by al7kz on 2005-07-11
corrected

---

### Post by DarkManX4lf on 2005-07-11
[QUOTE=al7kz]"so when i change the windows boot options to hd1 it says its a unknown file system...."

What are your menu.lst entries for ubuntu and windows when you get that error message?[/QUOTE]


here is my menu.lst

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

map (hd0) (hd1)
map (hd1) (hd0)

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1



this is the menu.lst with all the "#" lines taken out.

---

### Post by al7kz on 2005-07-11
corrected

---

### Post by DarkManX4lf on 2005-07-11
[QUOTE=al7kz]So you are swapping the disks:

"If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command map (see map), like this:

     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)
     

This performs a virtual swap between your first and second hard drive.

Caution: This is effective only if DOS (or Windows) uses BIOS to access the swapped disks. If that OS uses a special driver for the disks, this probably won't work."

above from the grub manual. That's it for me. I'm in way over my head. But what I think I would do is make the windows disk the first boot disk in bios, and reinstall grub on it's mbr. Bonne chance![/QUOTE]



i think im doing that,


map (hd0) (hd1)
map (hd1) (hd0)

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1


that is in my menu.lst but i will try it out, from the grub command line

---

### Post by al7kz on 2005-07-12
corrected

---

### Post by DarkManX4lf on 2005-07-12
[QUOTE=al7kz]Found this at:

[http://www.mepis.org/node/6474](http://www.mepis.org/node/6474)

try

map (hd0) (hd1)
map (hd1) (hd0)

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1

from [http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html:](http://www.faqs.org/docs/Linux-HOWTO/Linux+Win9x+Grub-HOWTO.html:)

"The "map" lines under the Windows section are essential for getting your installation to work. These are the magical lines that trick Windows into believing that it's installed on the first partition of the first disk. If you don't map the Windows partition to (hd0,0), Windows will destroy your partition table and you won't be able to boot anything.

"rootnoverify" tells GRUB to boot from the Windows partition, but not to attempt to mount it, and "chainloader +1" tells GRUB to chain to Windows' bootloader which will start Windows. "[/QUOTE]


thanks i will try it out.

---

### Post by DarkManX4lf on 2005-07-12
damn, that didnt work either.....then i thought to try to use the windows boot loader to load both windows and then linux, so i did a bit of searching in google and i found this:


[http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49](http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49)


and i followed that, and used the program called "bootpart" in windows to make the windows boot loader load linux....but still that didnt work either....


so far it seems to me that it is impossible to load windows if you have linux installed on a sata drive and is the primary drive......

there is one more option i am willing to do, and it might work

1) set bios to boot from windows drive (primary ide, first drive)
2)install grub on that drive
3) set it up to boot linux and windows


but how would i go about doing this?

---

### Post by al7kz on 2005-07-12
corrected

---

### Post by al7kz on 2005-07-12
corrected

---

### Post by drummer on 2005-07-12
I had the same problem when installing to my sata drive while a secondary pata was in my system. The problem was with grub, it installed to hd0, but i think that it thought that that was the pata drive. From memory, it thought the sata was hd1 and it put this in it's config. 

I booted from a live cd (Slax) and edited the /boot/grub/menu.lst file and changed the any entries from (hd1,x) to (hd0,x). My system is now booting fine, but I found out that grub reverted to hd1 when I updated my kernel, so keep that in mind if you do a kernel upgrade so you don't have to use a live cd to edit menu.lst

Hope that helps..

---

### Post by DarkManX4lf on 2005-07-12
hmm well ive got nothign to lose i will try both ways, thanks guys

---

### Post by DarkManX4lf on 2005-07-13
[QUOTE=al7kz]I assume you have a floppy. It's not too difficult. Basically you will make a grub boot disk, then edit menu.lst to change hd0 to hd1 and hd1 to hd0 and delete the map lines. Then reboot and in bios change to boot from the windoze drive. Then boot from the grub floppy, issue a couple of grub commands, remove the floppy and reboot.

1) First create the grub boot disk. Insert a formatted disk in the floppy drive and issue the following three commands in a ubuntu terminal: (following shows the output too, just issue the commands shown after the prompt symbols):

joey@ubuntu:~$ cd /lib/grub/i386-pc
joey@ubuntu:/lib/grub/i386-pc$ dd if=stage1 of=/dev/fd0 bs=512 count=1
1+0 records in
1+0 records out
512 bytes transferred in 0.090971 seconds (5628 bytes/sec)
joey@ubuntu:/lib/grub/i386-pc$ dd if=stage2 of=/dev/fd0 bs=512 seek=1
211+1 records in
211+1 records out
108104 bytes transferred in 7.551520 seconds (14316 bytes/sec)
joey@ubuntu:/lib/grub/i386-pc$

2) make a backup copy of menu.lst

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

3) edit menu.lst to change hd0 to hd1, hd1 to hd0, and remark out or delete the map lines:

sudo gedit /boot/grub/menu.lst 

title Ubuntu, kernel 2.6.10-5-686
root (hd1,0)
kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-686
savedefault
boot

(etc, etc for the other ubuntu entries) 

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

#map (hd0) (hd1)   -make sure this is remarked out or deleted
#map (hd1) (hd0)   -make sure this is remarked out or deleted

title Windoze
rootnoverify (hd0,0)
makeactive
chainloader +1

4) save the file.
5) restart the computer and bring up the bios menu.
6) in bios, change boot sequence to boot first from the floppy, and first boot hard drive to the windoze drive, save and reboot.
7) the computer boots the floppy to a grub shell. Issue the following grub command:

grub> find /boot/grub/stage1

this should give an output of (hd1,0) verifying the linux boot directory is at the first partition of the second hard drive. 

8) then issue the following grub command 

grub> root (hd1,0)

9) The next command installs grub on the mbr of the first hard drive (XP). It will overwrite the mbr - it can be restored but don't ask me how - there's lots of info in the forums on how to do that.

grub> setup (hd0)

10) Remove the grub floppy and reboot and là voilà! - it should boot to the grub menu you edited.
11) If you want to edit menu.lst further at this point, select the entry you want to edit and hit the "e" key, and follow the instructions. Or, hit "c" to go to the grub shell again. You can also boot windoze or linux direct from the grub shell. It's all in the GRUB Manual.
12) Bonne chance & have fun!! Over and out - al7kz.[/QUOTE]



Hahah !!!! it works !!!! thanks man, 
thanks guys for helping me out

---

