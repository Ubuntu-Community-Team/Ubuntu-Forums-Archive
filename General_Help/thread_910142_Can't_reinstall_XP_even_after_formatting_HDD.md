---
title: "Can't reinstall XP even after formatting HDD"
date: 2008-09-04
forum: General Help
---

### Post by pzs80 on 2008-09-04
I have a huge problem: I tried reviving my old laptop by installing  Xubuntu, but after at lot of hazzle I disided against it and reinstalled Xp with the recovery discs -  but when the computer restarted for the first time without the cd , it hangs with a black screen : "GRUB loading stage 1.5" 
GRUB loading please wait , Error 17

I then formatted the hdd on another computer to get rid of any linux left over, but the problem persists! What has Xubuntu done to my harddisk?? What can I do to install XP??
I'll really apreciate any help.

regards 
Peter

---

### Post by mrtomservo on 2008-09-04
Strange, I thought Windows would rewrite the boot sector, for some reason it doesn't seem like it did.  What you might want to try is removing the partition all together with something like fdisk or gparted (from a live cd) and then make a new partition.  Then format and try to reinstall.  Hope that helps!

---

### Post by daggerx on 2008-09-04
Not sure if this will help but give it a shot.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I'm sure someone else has more insight on this than I do. Hope it works out for you. I have a T22 that I still can't get linux on, it hangs at the "uncompressing linux" screen.

---

### Post by Archmage on 2008-09-04
You need to enable booting from the CD in the BIOS as the first option. At the moment it is still booting from the harddrive.

---

### Post by pzs80 on 2008-09-04
The laptop already boots from the CD rom first, then the hdd.

---

### Post by baruch60610 on 2008-09-04
The problem is that the MBR is still trying to find Linux.  For some reason, it wasn't rewritten to look for XP.

I'm not exactly sure how to fix this.  You need to get fdisk running on the computer, and then use the command:

fdisk /mbr

That will rewrite the instructions to look for XP instead of grub.  I don't know how to get fdisk running on your system, however.  That may be an option in your Windows installation CD.

---

### Post by fourthofjuly on 2008-09-04
> **pzs80 said:**
> The laptop already boots from the CD rom first, then the hdd.
windows will try to take over when you install it on a machine that is already loaded with linux...

if you do not have any important data, make a clean install of Windows FIRST and then install xubuntu...

cheers!

devang.

---

### Post by egalvan on 2008-09-04
For some reason, the MBR has not been re-written by the windows installer.

You have two ways to go:

1) try to re-write the MBR

2) erase the disk


First choice, boot with a dos disk (floppy, usb, cd)
 or hook it to another computer, boot , then use command prompt to run 

```
fdisk /mdr
```

note: even a dos boot disk will do this.


Second choice, boot with a partition editor (I like PartED Magic LiveCD, and have donated to the author) and delete all partitions
or use Darik's Boot and Nuke (DBAN) to erase the disk (I also like this program)

[www.dban.org](www.dban.org)


this is a simple, but powerful program, there is no "un-do" or "recover" option,
you must be careful to select the proper drive.
since you seem to want the drive erased, this should not be a problem

both of these are small downloads, and will run from cd's, or usb drives. OF course, your machine must be able to boot from usb.


Also, there are boot floppy images avaiable on the net, or find an old MS boot floppy for DOS or Win95/98

---

### Post by pzs80 on 2008-09-04
I tried another window xp installation disc, (instead of the recover discs) but it wouldnt let me boot from it, It hanged with a black screen that said non emulation installer (or something) 
i've tried deleting an recreating a partition with partition magic 8, but it won't complete any actions "Error the specified file system has no file I/O functions"  Man this is not my day.. 
I can't get into Fdisk from the recovery discs they only have one option: recreate the hdd as it was from the factory.

---

### Post by fourthofjuly on 2008-09-04
> **pzs80 said:**
> I tried another window xp installation disc, (instead of the recover discs) but it wouldnt let me boot from it, It hanged with a black screen that said non emulation installer (or something) 
i've tried deleting an recreating a partition with partition magic 8, but it won't complete any actions "Error the specified file system has no file I/O functions"  Man this is not my day.. 
I can't get into Fdisk from the recovery discs they only have one option: recreate the hdd as it was from the factory.
ok, here's a lenghty procedure using your ubuntu & windows install CDs...

use the ubuntu install CD... 

delete all partitions during installation and make fresh partitions for swap, root and home (ext3) AND make one more NTFS partition and mark it as "DO NOT USE".

after you have installed Ubuntu, use your windows install CD to start windows installation... here delete all partitions and make fresh NTFS partitions...

after windows is installed, you may install ubuntu with GRUB...

---

### Post by pzs80 on 2008-09-04
Ok, Now I tried using system recovery cd with Dos emulation. I used Fdisk to delete the partition an resize a dos primary partition. 
after that the message was still the same : GRUB loading stage 1.5"
GRUB loading please wait , Error 17
I tried loading the dos emulator again , ran C:/fdisk /mdr 
and it said: Error reading from drive C: DOS area general failure

---

### Post by egalvan on 2008-09-04
> **pzs80 said:**
> I tried loading the dos emulator again , ran C:/fdisk /mdr 
and it said: Error reading from drive C: DOS area general failure

OK, you may have deeper problems. 

Can you download DBAN? (see prev post)

dban.org


burn to cd, and nuke the drive.

This may clear out any cruft.

Also, depending on the drive, the manufacturer's web-site may have software to erase the drive.

---

### Post by pzs80 on 2008-09-04
Thanks for all the replys: I got it working by using the system rescue cd that I had. it included FDISK and I deleted all partitions and reformatted the drive. from there the reinstalled XP via the recovery discs
Cheers everyone!

---

