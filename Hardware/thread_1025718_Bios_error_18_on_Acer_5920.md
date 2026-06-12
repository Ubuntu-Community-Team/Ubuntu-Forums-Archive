---
title: "Bios error 18 on Acer 5920"
date: 2008-12-30
forum: Hardware
---

### Post by jrawling on 2008-12-30
My multiboot laptop has developed a problem and will only boot with one old recovery image (the one I'm logged in with).

Googling for "error 18" has been less than useful, but I believe that there is a workaround in the bios which allows it to read the first part of the hard drive, then the OS (Ubutntu 8.10 or Vista) can carry on to see the rest of the drive.

Bios  settings are minimal - the only drive choices I found were SATA mode:IDE or ACPI (I think - I'm afraid to try a reboot in case it won't boot at all.)

Otherthan messing with the  partitions (not recently) this laptop is stock. If more info is required I'll reboot and take notes.


This seems like a good time for a complete backup, in case the drive is dying.

Anyway, if someone has experienced this problem and knows the cure, my gaming son would be very happy to be able to get Vista going and I'd be very happy to get some geek cred.

Cheers!
Jim

---

### Post by wizard10000 on 2008-12-30
This is a grub error, not a BIOS error.  Looky here -

[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

> [B]Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS[/B]

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. 

---

### Post by jrawling on 2008-12-30
Thanks. I found the piece you quoted and would just change my partitions around or add a boot partition at the front of the disk except that neither the partition scheme or the bios were deliberately changed. The computer just stopped booting from the grub menu and put up the error 18.

 It will boot from an older kernel that is lower in the pile that grub presents to me. I'll try to look for the details of what kernel works when I get brave enough to reboot.

Cheers!
Jim

---

### Post by caljohnsmith on 2008-12-30
> **jrawling said:**
> Thanks. I found the piece you quoted and would just change my partitions around or add a boot partition at the front of the disk except that neither the partition scheme or the bios were deliberately changed. The computer just stopped booting from the grub menu and put up the error 18.

 It will boot from an older kernel that is lower in the pile that grub presents to me. I'll try to look for the details of what kernel works when I get brave enough to reboot.

Cheers!
Jim
When you installed the new kernel, probably what happened is you finally bumped into your BIOS limitation where the BIOS can't see anything on a HDD past either 8.4 GB or 137 GB; in other words, the contents of your Ubuntu partition have been growing I would imagine, so the new kernel is physically located on your HDD past one of those limits, whereas the older kernels are closer to the beginning of the drive. That would explain why you can still boot from your old kernel but not the new one. So bottom line, I think making a ~200 MB boot partition at the beginning of your drive is the best thing to do, but it's up to you. If you would like help with the specifics of doing that, how about first posting the output of:
```
sudo fdisk -lu
```
And please identify your partitions. We can go from there if you want.

---

### Post by jrawling on 2008-12-31
OK here it is:
root@ace:~# fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x070b0b0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20467712   184716731    82124510    6  FAT16
/dev/sda3       194916645   481580504   143331930    5  Extended
/dev/sda4       481595392   488394751     3399680   12  Compaq diagnostics
/dev/sda5       194932710   266646869    35857080    7  HPFS/NTFS
/dev/sda6       266646933   328079429    30716248+  83  Linux
/dev/sda7       328079493   471443489    71681998+  83  Linux
/dev/sda8       471443553   481580504     5068476   82  Linux swap / Solaris
root@ace:~# 
my translation:
sda1      not sure, maybe Acer's Vista image
sda2      Vista D: mostly unused
sda3      no idea   
sda4      see sda1?
sda5      Vista
sda6      / 
sda7      /home
sda8      swap

All rather a kluge. The drive got to this irrational state because I didn't want to off Vista as my son uses it for gaming. I don't have a Vista install disk and I don't know if burning one would allow me to nuke the entire drive and partition it more logically. 

I wonder about the hypothesis that I have filled the drive beyond the reach of the bios as several images including Vista won't boot and return the error 18 though I haven't moved them and so it seems that something else is different.

The bios in this machine seems to be designed to be idiot proof as it doesn't offer any information or any options for the drive except the sata mode which seems to work or not work either way. If there is a top secret way to get at the real settings, I haven't found it.

Could there be a gizmo on the hard drive that tells the bios little white lies about the heads and cylinders and such so that the bios thinks that the drive is smaller than it really is? And could the drive controller be getting tired? If the answer is yes to either, I'll get a new drive and rebuild this thing.

Can anyone suggest a way of testing my idea that it's the drive controller?

Thanks,
Jim

---

### Post by caljohnsmith on 2008-12-31
> **jrawling said:**
> 

I wonder about the hypothesis that I have filled the drive beyond the reach of the bios as several images including Vista won't boot and return the error 18 though I haven't moved them and so it seems that something else is different.

So are you saying that you were able to boot Vista OK from Grub before, but now you can't and get an error 18? I notice that your sda6 linux partition starts at about 136.5 GB, which is right on the edge of the 137 GB BIOS limitation, so I'm wondering if you have a different issue with Grub. Do you know which of your two linux partitions has Grub? How about posting the output of the following:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return either (hd0,5) or (hd0,6), but use whatever it returns to replace (hdX,Y) below:
```
grub> root (hdX,Y)
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/grub/menu.lst

```
And please post the output of all the above commands. 
> **jrawling said:**
> 
Could there be a gizmo on the hard drive that tells the bios little white lies about the heads and cylinders and such so that the bios thinks that the drive is smaller than it really is? And could the drive controller be getting tired? If the answer is yes to either, I'll get a new drive and rebuild this thing.

Can anyone suggest a way of testing my idea that it's the drive controller?

Thanks,
Jim
All modern BIOSes that I'm aware of use LBA (Logical Block Addressing) to access the HDD now instead of CHS values (Cylinders, Heads, Sectors); if your BIOS was still using CHS to access the HDD, it would not be able to access anything past about 8.4 GB, so I don't think that is your issue, but I could be wrong.

---

### Post by jrawling on 2008-12-31
As requested:

grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> blocklist /boot/grub/stage2
(hd0,5)53673984+96,53674088+116

grub> blocklist /boot/grub/menu.lst
(hd0,5)53648936+15

grub> 

You have to love a command line. Now if I could remember the commands between incidents...

JIm

---

### Post by caljohnsmith on 2008-12-31
OK, I think that creating a boot partition at the beginning of your drive may not necessarily solve your problems, because according to the output you posted, both your Grub stage2 file and menu.lst are physically located at about 164 GB; that is clearly past 137 GB, so if your BIOS had that limitation, you would get a Grub error 18 before even seeing the Grub menu, which is not your case. 

Since you can at least boot an older kernel still, how about doing that, and then in Ubuntu do:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda
apt-cache policy grub
```
Please post the output of all the above commands, reboot, and let me know exactly what happens.

---

### Post by jrawling on 2009-01-01
Here is the output from the terminal: 

root@ace:~# grub
Probing devices to guess BIOS drives. This may take a long time.
root@ace:~#  apt-get purge grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:(
  libswfdec-0.6-90 linux-headers-2.6.24-19-generic libavutil1d libdc1394-13 linux-headers-2.6.27-10 libcvaux1 libgfortran2 libsvga1 libwxgtk2.8-0 libmp4v2-0 libcdk5 linux-headers-2.6.27-10-generic
  libpostproc1d libexiv2-2 libglide2 libamrnb3 libx264-57 libamrwb3 libggi2 libxml++2.6c2a libgii1 libwxbase2.8-0 libswscale1d libpano12-0 libgii1-target-x libcv1 khelpcenter libpano12-bin libhighgui1
  gcc-3.3-base linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 938kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 209041 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
Processing triggers for man-db ...
root@ace:~# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswfdec-0.6-90 linux-headers-2.6.24-19-generic libavutil1d libdc1394-13 linux-headers-2.6.27-10 libcvaux1 libgfortran2 libsvga1 libwxgtk2.8-0 libmp4v2-0 libcdk5 linux-headers-2.6.27-10-generic
  libpostproc1d libexiv2-2 libglide2 libamrnb3 libx264-57 libamrwb3 libggi2 libxml++2.6c2a libgii1 libwxbase2.8-0 libswscale1d libpano12-0 libgii1-target-x libcv1 khelpcenter libpano12-bin libhighgui1
  gcc-3.3-base linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/402kB of archives.
After this operation, 938kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub.
(Reading database ... 208989 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu45_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu45) ...

root@ace:~# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ace:~# apt-cache policy grub
grub:
  Installed: 0.97-29ubuntu45
  Candidate: 0.97-29ubuntu45
  Version table:
 *** 0.97-29ubuntI'd better senu45 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
root@ace:~# 

Now for the reboot.
Wait! I'll send this, then reboot. Message to follow shortly, I hope.

Jim

---

### Post by jrawling on 2009-01-01
Right, I'm back.

On reboot the grub menu looks the same as it did before the mis behaviour started. BTW is there any easy way to screen capture the grub menu?

I tried booting with all the kernels plus Vista and got the dreaded error 18 for each one. I then ctrl-alt-deleted to get a fresh boot screen. The kernel that was highlighted, an older recovery one worked, so I'm able to write this, but my son wants to play Spore. So I guess I need to find a way to fix the problem.

Thanks a million for the help so far. I would happily RTFM if I had a manual or new what to try reading. There is nothing like current experience when trying to beat a piece of gear into submission it seems.

Happy New Year!
Jim

---

### Post by caljohnsmith on 2009-01-01
Happy New Year to you and your family too. :) But about your Grub problem, it is really difficult to troubleshoot because the behavior is not consistent with a true Grub error 18. You mentioned in your first post that your BIOS could switch the SATA drive between IDE or ACPI; do you know if your Ubuntu/Vista drive is IDE or SATA? If it is an internal drive like I think it would be, then most likely it is IDE. But how about going ahead and toggling that BIOS SATA drive setting (if it's IDE, change it to ACPI, or vice versa), reboot, and see if Grub still gives you error 18 when trying to boot the different kernels or Vista. We can go from there.

---

### Post by jrawling on 2009-01-01
I think I tried that and got the error both ways, but I'll do it again and pay attention this time.

shutdown -r now

Jim

---

### Post by jrawling on 2009-01-01
Hey,
Things are looking up. Before I took look at the bios, I tried booting the kernel including Windows in reverse list order and surprise! 6 of 7 Ubuntu kernels and their recovery mode grub entries will boot as will Vista. 

If I try booting the top grub menu I (which used to work) I get the dreaded error 18 and if I try  to move down the list I get the same error.

I did look at the bios and found it set "sata mode = ide". but since this computer is almost completely functional now  wimped out and left it alone.
When I tried it before it didn't seem to make any difference. 

Do modern laptops use cmos batteries? Acers info is sketchy.

I don't understand how we got here, but I'm thrilled.

Jim

---

### Post by caljohnsmith on 2009-01-01
> **jrawling said:**
> Hey,
Things are looking up. Before I took look at the bios, I tried booting the kernel including Windows in reverse list order and surprise! 6 of 7 Ubuntu kernels and their recovery mode grub entries will boot as will Vista. 

If I try booting the top grub menu I (which used to work) I get the dreaded error 18 and if I try  to move down the list I get the same error.

Can you please explain a little more in detail, because I'm confused by your description; you say you tried to boot the kernels and Windows in "reverse list order"? What exactly happened between the time when all the Grub entries (except the one recovery kernel listing) returned error 18, and now that you are able to boot Windows and 6 of the 7 kernels?

---

### Post by jrawling on 2009-01-02
By reverse order I meant from the bottom of the grub menu list up. Vista appears (properly) at the bottom and Ubuntu in date order, above Vista. The most recent kernel is the one that causes the error 18 barf, 


The improvement in the boot situation occurred after I reinstalled grub per the suggestion caljohnsmith gave me quoted below:


Code:

sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install /dev/sda
apt-cache policy grub


The full terminal output from these commands is in a previous post in this thread.

Cheers!
Jim

---

