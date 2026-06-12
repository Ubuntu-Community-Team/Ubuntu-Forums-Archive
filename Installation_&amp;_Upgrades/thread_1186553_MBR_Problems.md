---
title: "MBR Problems"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Pratherdude on 2009-06-13
Ok I am haveing a problem with my install of Ubuntu 9.04, I had a dual boot with XP, but after finding WINE and getting all of my mail out of Outlook and wiped everything and am just useing Ubuntu. 

Now comes the problem, after deleting all of the partitions and reformating I installed Ubuntu. After the reboot it comes up saying MBR error 1 press any key to boot from floppy, then it gives the error MBR error 2 press any key to boot from floppy. b

I have tried booting from a dos disk and run fdisk /mbr with no help, then I tried booting from an XP disk and running fixmbr and fixboot with no help. I have tried reloading grub from the live disk with no help either. Any suggestions? I really need to get this fixed by tomorrow if possible as I need my system for work.

---

### Post by merlinus on 2009-06-13
Try supergrub.

---

### Post by Zimmer on 2009-06-13
[http://www.pcadvisor.co.uk/forums/index.cfm?action=showthread&threadid=310845&forumid=1](http://www.pcadvisor.co.uk/forums/index.cfm?action=showthread&threadid=310845&forumid=1)

Might be a BIOS problem (from looking at that link above..)

or maybe your reformatting has left the boot flag not set for the Ubuntu partition... you will need to use some rescuing software if that is the case..
(Supergrub disc, the Ubuntu Live CD etc)
One step at a time...

---

### Post by ajgreeny on 2009-06-13
Do you have more than one disk, and if so, is the correct one set to boot in the BIOS?

---

### Post by merlinus on 2009-06-13
@Zimmer

FWIW, linux does not need a boot flag.

---

### Post by hal8000 on 2009-06-13
Can you boot with the Jaunty Live CD?

Booting with a live linux CD will always work, even with no hard drive.
Should this fail, your system is trying to boot from a device other then the cd/dvd drive.

If you can get the live CD to work,
post the output of

sudo fdisk -l

---

### Post by Pratherdude on 2009-06-13
> **ajgreeny said:**
> Do you have more than one disk, and if so, is the correct one set to boot in the BIOS?

Yes I have more then one disk installed, I have already checked that and verified that the correct disk is booting.

---

### Post by Pratherdude on 2009-06-14
> **hal8000 said:**
> Can you boot with the Jaunty Live CD?

Booting with a live linux CD will always work, even with no hard drive.
Should this fail, your system is trying to boot from a device other then the cd/dvd drive.

If you can get the live CD to work,
post the output of

sudo fdisk -l


Ok here is what was in terminal, I did notice that Ubuntu was showing my SATA drive as the boot drive and that is not correct, my boot drive is suppose to be my primary IDE drive anyway to change that?

   ubuntu@ubuntu:~$ sudo fdisk -l
  
   
   
  Disk /dev/sda: 500.1 GB, 500107862016 bytes
  
  255 heads, 63 sectors/track, 60801 cylinders
  
  Units = cylinders of 16065 * 512 = 8225280 bytes
  
  Disk identifier: 0x8995f229
  
   
   
     Device Boot      Start         End      Blocks   Id  System
  
  /dev/sda1   *           1       60801   488384001    7  HPFS/NTFS
  
   
   
  Disk /dev/sdb: 120.0 GB, 120034123776 bytes
  
  255 heads, 63 sectors/track, 14593 cylinders
  
  Units = cylinders of 16065 * 512 = 8225280 bytes
  
  Disk identifier: 0xe4b800bb
  
   
   
     Device Boot      Start         End      Blocks   Id  System
  
  /dev/sdb1               1       14593   117218241    7  HPFS/NTFS
  
   
   
  Disk /dev/sdc: 320.0 GB, 320072933376 bytes
  
  255 heads, 63 sectors/track, 38913 cylinders
  
  Units = cylinders of 16065 * 512 = 8225280 bytes
  
  Disk identifier: 0x000418d6
  
   
   
     Device Boot      Start         End      Blocks   Id  System
  
  /dev/sdc1               1        8199    65858436   83  Linux
  
  /dev/sdc2            8200        8503     2441880    5  Extended
  
  /dev/sdc5            8200        8503     2441848+  82  Linux swap / Solaris
  
   
   
  Disk /dev/sdd: 120.0 GB, 120034123776 bytes
  
  255 heads, 63 sectors/track, 14593 cylinders
  
  Units = cylinders of 16065 * 512 = 8225280 bytes
  
  Disk identifier: 0xadf8f0a0
  
   
   
     Device Boot      Start         End      Blocks   Id  System
  
  /dev/sdd1               1       14593   117218241    7  HPFS/NTFS
  
   
   
  Disk /dev/sde: 250.0 GB, 250059350016 bytes
  
  255 heads, 63 sectors/track, 30401 cylinders
  
  Units = cylinders of 16065 * 512 = 8225280 bytes
  
  Disk identifier: 0x7b326452
  
   
   
     Device Boot      Start         End      Blocks   Id  System
  
  /dev/sde1               1       30401   244196001    7  HPFS/NTFS
  
  ubuntu@ubuntu:~$ 
  
  ubuntu@ubuntu:~$

---

### Post by Zimmer on 2009-06-14
So, looks like you have 5 separate drives a-e  ?

You installed Linux to partition sdc1..

Where did you install GRUB ? To the MBR of sdc?  The MBR of sda?  Can't remember?

[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

You can find a link to the SuperGRUB disk here.

and a guide to Multi booting Windows here
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

No experience of multibooting using multiple drives , only single drive multipartition and external USB HDD.

If BIOS picks a drive to boot it will look for the MBR to tell it what to do next.
Yours (whichever drive it is) cannot tell what to do. 

Suggest you investigate EasyBCD and see if that will go some way to providing a solution for your multiboot purposes as you have 5 drives....
and to work out which MBR's need restoring, and what they need restoring to.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by ajgreeny on 2009-06-14
> **Pratherdude said:**
> Yes I have more then one disk installed, I have already checked that and verified that the correct disk is booting.
When you say "the correct one" do you mean the one with ubuntu on it?  If grub is on the mbr of the windows drive (sda) then that is the one which should be first in the boot order list in BIOS, not the ubuntu disk.  When I say grub, I do not mean the partition on which the /boot/grub folder is found, as that is not actually grub, just the configuration for grub.

If you already understand this, my apologies; just trying to help in what must be a very frustrating situation.

---

### Post by Pratherdude on 2009-06-14
> **Zimmer said:**
> So, looks like you have 5 separate drives a-e  ?

You installed Linux to partition sdc1..

Where did you install GRUB ? To the MBR of sdc?  The MBR of sda?  Can't remember?

[http://members.iinet.net.au/~herman546/p15.html]("http://members.iinet.net.au/%7Eherman546/p15.html")

You can find a link to the SuperGRUB disk here.

and a guide to Multi booting Windows here
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

No experience of multibooting using multiple drives , only single drive multipartition and external USB HDD.

If BIOS picks a drive to boot it will look for the MBR to tell it what to do next.
Yours (whichever drive it is) cannot tell what to do. 

Suggest you investigate EasyBCD and see if that will go some way to providing a solution for your multiboot purposes as you have 5 drives....
and to work out which MBR's need restoring, and what they need restoring to.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Yeah 5 drives, I had ubuntu and windows on my primary IDE drive which is Disk /dev/sdc. I assume grub is installed to this drive as when I tell grub to find the stage1 file it says it on drive (hd2,0). I only boot from my primary IDE drive all others are for storage. I'll give supergrub a try.

---

