---
title: "Can't install XP laptop won't boot from XP cd"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by cawlef on 2009-08-16
I've been using ubuntu on a HP compaq nc4200 laptop for the past few months, I wiped the laptop and installed a full version.  I need to go back to XP now because I need to use Adobe CS4 for college in September.

Anyway I deleted my primary partition in Gparted and set it to Fat32, when I set the bios to boot from the CD first, but when I reboot it goes straight into the GRUB loader and I get error 17.  I can't boot from the HD because I deleted the primary partition.  What do I need to do to wipe the drive and install a fresh copy of XP, I can't get into DOS to run any of the fixmbr commands.  Any help appreciated.

---

### Post by AmerNewbieInDE on 2009-08-16
i am assumming you have an install cd for xp not an upgrade cd? normally, when you boot with a bootible cd, it asks you if you want to boot by cd by `enter` or an F key. if it times out it automatically boot the hard drive.

---

### Post by cawlef on 2009-08-16
Yep its a full version of XP, I've wiped the laptop in the past and it worked.  I think I need to somehow edit the GRUB loader so I can boot from the CD

---

### Post by running_rabbit07 on 2009-08-16
Instead of using BIOS, hit the key that takes you straight to the boot order. That is what I have always had to do with my HP and my Lenovo.

Edit: For my Lenovo it is F12 but I think it was F2 or F8 for the HP.

---

### Post by cawlef on 2009-08-16
thanks there is no cd in my laptop its built into the docking station its a usb cd and I've enabled the multi boot functionality it gives me 2 options 1) bot from usb cd and 2) boot from hdd when I put in the xp cd and reboot choosing the usb cd I get "grub loading Error 17"  I get the same error when I boot from the hdd.

---

### Post by AmerNewbieInDE on 2009-08-16
try booting with a linux cd, the same way as you are with the windows cd..

---

### Post by cawlef on 2009-08-16
I'm using my Ubuntu iso cd at the moment so it will boot from the linux cd.

---

### Post by ajgreeny on 2009-08-16
> **cawlef said:**
> thanks there is no cd in my laptop its built into the docking station its a usb cd and I've enabled the multi boot functionality it gives me 2 options 1) bot from usb cd and 2) boot from hdd when I put in the xp cd and reboot choosing the usb cd I get "grub loading Error 17"  I get the same error when I boot from the hdd.
There is pbviously some problem with either the naming of the usb CD in the bios list, or the usb CD drive is not recognised (bad usb socket?) as grub will only appear when the hard drive is booting, but not when the usb CD drive boots.  Go to the bios again and check all the different usb booting options (my machine has several differently named usb options) try each one separately, and hopefully one will work.  Also try other usb sockets separately from the one in the docking station, if possible.  If you can't do that, and assuming you have a usb socket on the machine, try another usb CD drive, if you can borrow one somehow.

---

### Post by AmerNewbieInDE on 2009-08-16
> **cawlef said:**
> I'm using my Ubuntu iso cd at the moment so it will boot from the linux cd.

then i would have to say something is wrong with your windows cd, since you r using the cd to boot to linux, putyour windows cd in and see what is on the disk..

---

### Post by running_rabbit07 on 2009-08-16
> **AmerNewbieInDE said:**
> then i would have to say something is wrong with your windows cd,

I would agree with this being your system is seeing the Ubuntu LiveCD.

Your next option would be to reinstall Ubuntu being you formatted the partition it was installed in and use a Virtual Box to run the XP from there. I haven't done it yet myself, but I thought I would throw that out there. I am waiting for the new semester so i can get Vista or 7 from the college IT department.

---

### Post by AmerNewbieInDE on 2009-08-16
> **running_rabbit07 said:**
> I would agree with this being your system is seeing the Ubuntu LiveCD.

Your next option would be to reinstall Ubuntu being you formatted the partition it was installed in and use a Virtual Box to run the XP from there. I haven't done it yet myself, but I thought I would throw that out there. I am waiting for the new semester so i can get Vista or 7 from the college IT department.

dont get vista, i have heard it will only be supported till 2012, but it is funny, ms will keep xp going.

---

### Post by running_rabbit07 on 2009-08-16
> **AmerNewbieInDE said:**
> dont get vista, i have heard it will only be supported till 2012, but it is funny, ms will keep xp going.

I'd get it for free anyway. You have to be enrolled in IT related classes to get the free software. At least it is free to check out like a book for a week or for like 35 bucks I can get my own copy with a key.

---

### Post by cawlef on 2009-08-16
Thanks Ronnie, unfortunatley I don't want to use ubuntu, I like some applications like Gimp, but its missing far too many applications that I use on a daily basis, I can't use CS4 suite, or my Pentax software for editing RAW picture formats, Google earth goes bananas with my graphics card, can't use iTunes, can't use Visio, Oracle, VPN connection for work the list goes on.  I just want to wipe the disk and start from Scratch.  I'm pretty sure the XP cd is ok, and I know that the CD drive is ok because I'm booting from it now into Ubuntu.  The error I get is "grub loading stage 1.5 Grub loading Error 17"  I'm not an IT Guru but I'd imagine that my master boot record is screwed and that I need to run a fixmbr command from DOS but I can't get into DOS.  I know nothing really about Linux, and I havn't a clue about GRUB, could I create a new DOS partition in G Parted and somehow download some boot files that would allow me to use the new partition to access my CD, and then I should be able to install XP from there ?

---

### Post by AmerNewbieInDE on 2009-08-16
the thing is, the mbr is on the hard drive, it you tell the pc to load from cd, it loads linux cd but skips windows cd..(well, unless your pc just like linux better and doesnt want windows back)..?? is your had drive partitioned? is there data you need/want to keep? if not, run gparted, delete all the partitions, and format it complete, then there will be no more grub loader... but a boot windows cd should load with or without grub there.. do you know the make of harddrive you have? maybe you can get a boot image from them to format the drive..

---

### Post by cawlef on 2009-08-16
cheers that sounds like its exactly what I want to do, but I don't know how to use Gparted to format the disk.  At the moment, I have 1 single partition /dev/sda1 file system is FAT32, size is 55.89gib it tells me I have used 27.97 and unused 55.86  Not sure why the math doesn't add up.  All my data is backed up so I'm good to go as long as I can figure out how to use Gparted to format the disk.

---

### Post by running_rabbit07 on 2009-08-16
> **cawlef said:**
>   I know nothing really about Linux, and I havn't a clue about GRUB, could I create a new DOS partition in G Parted and somehow download some boot files that would allow me to use the new partition to access my CD, and then I should be able to install XP from there ?
  I am very new to the IT world myself. The big problem really that needs to be figured out is why your system doesn't see the Windows install disk, yet it sees your LiveCD. It can not be because of partitons, they waould just cause a problem later.

Before you started with Ubuntu did you have a restore partition? 

I know when I was working with my brother-in-laws Gateway system had a restore partition but that only had enough software to start the restore process from his install CDs.

My Lenovo had the same thing and it had become corrupted and I was able to download an ISO from their site that basically kicked off the restore process.

---

### Post by AmerNewbieInDE on 2009-08-16
/dev/sda1 is a partition on the hard drive. the drive is /dev/sda.. the `a` is the first drive, sdb would be the second hard drive, the numbers after are the partition

---

### Post by raymondh on 2009-08-16
> **cawlef said:**
> cheers that sounds like its exactly what I want to do, but I don't know how to use Gparted to format the disk.  All my data is backed up so I'm good to go as long as I can figure out how to use Gparted to format the disk.

To use gparted:

-   Boot into the liveCD and in live session.
-   Access gparted (system > administration)
-   Gparted (live) ought to unmount all partitions/drives.  Just to be sure, rt. click on each partition and if given the option to unmount, do so.  For SWAP, select SWAPOFF.
-   Delete partitions as you have decided/preferred.  If your former Ubuntu and swap resided inside an extended, you'll have to delete those partitions first and then delete the Extended.  You know you're done when you have a complete 'unallocated' space.
-   You can choose to format the newly unallocated space now or, choose to have XP format as you install XP.
-    Quit and close gparted.
-   Quit and close the live session.

For more info about [gparted]("http://www.dedoimedo.com/computers/gparted.html")

For info on the [error 17]("http://members.iinet.net.au/~herman546/p15.html#17")

For info/reference in [installing XP]("http://support.microsoft.com/kb/316941")


Good luck.

---

### Post by theozzlives on 2009-08-16
> use a Virtual Box to run the XP from there

Use the one from here: [http://www.virtualbox.org/]("http://www.virtualbox.org/"). The one in the repoes (ose) doesn't support USB.

---

### Post by cawlef on 2009-08-17
Thanks Raymond, I'll give that a shot.

---

