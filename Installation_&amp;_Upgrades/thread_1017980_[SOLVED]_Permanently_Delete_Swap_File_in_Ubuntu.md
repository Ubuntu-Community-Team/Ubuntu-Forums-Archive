---
title: "[SOLVED] Permanently Delete Swap File in Ubuntu"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by dcoaster on 2008-12-21
Hey all,

I am trying to install a 3rd OS, but I have reached the 4 partition limit of my one hard drive. I have read that you can delete the swap partition but I haven't found any specific instructions for deleting it. I still want to keep my Ubuntu partition though. Any help would be great! I am running Gutsy 7.10.

Thanks!

---

### Post by logos34 on 2008-12-21
You don't need to delete it permanently...Make an extended partition in its place and put everything inside.  Post your 

sudo fdisk -l

we can help you make room

*if you make a new /swap inside the extended, all you have to do is update /etc/fstab with the new UUID:

sudo blkid

---

### Post by nlz on 2008-12-21
don't delete the swap. Just change on partition from primary into logical. Then you can have a sheer infinite number of drives..  This way I also have 4 OS' running on my PC (and a separate /home partition and swap, so actually 6 partitions)

---

### Post by dcoaster on 2008-12-21
Thanks for your help! Here's fdisk:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        2586    20739915    7  HPFS/NTFS
/dev/sda3            3893        4817     7430062+  83  Linux
/dev/sda4            4818        4865      385560    5  Extended
/dev/sda5            4818        4865      385528+  82  Linux swap / Solaris

---

### Post by dcoaster on 2008-12-21
> **nlz said:**
> don't delete the swap. Just change on partition from primary into logical. Then you can have a sheer infinite number of drives..  This way I also have 4 OS' running on my PC (and a separate /home partition and swap, so actually 6 partitions)

How did you change it from primary to logical? I used the GParted liveCD and it has no options for changing the partitions. 

Thanks,

---

### Post by dcoaster on 2008-12-21
Forgot to mention, I already have 10GB of unallocated space from using GParted. Just trying to use GParted to make another partition gave me an error. Any ideas?

---

### Post by logos34 on 2008-12-21
ok, so the /swap is already a logical.  Still the same principle.  

sudo swapoff /dev/sda5

Use gparted to delete sda5.  Then delete the extended, sda4, that contains it.

Make a new **extended** partition in the unallocated space between windows sda2 and ubuntu sda3.  Create a new /swap inside along with other partitions.  Once that's done add them to fstab.  Use blkid to find the new uuids

---

### Post by dcoaster on 2008-12-21
What I actually did was use GParted to shift around the partitions so that I could extend the extended partition to include the unallocated space and just create the new partition inside of it. Sort of what you suggested but I didn't have to delete anything. Thanks for your help! I'm on a successful triple boot- Windows XP, Ubuntu, and Windows 7. =)

I have a quick question for you though. After installing Windows 7 to that new logical partition, the GRUB boot manager was (I guess) overwritten by 7's. I can get to XP and 7 fine, but Ubuntu is not listed. How can I add Ubuntu to the boot list? Thanks!

---

### Post by logos34 on 2008-12-21
> **dcoaster said:**
> What I actually did was use GParted to shift around the partitions so that I could extend the extended partition to include the unallocated space and just create the new partition inside of it. Sort of what you suggested but I didn't have to delete anything. Thanks for your help! I'm on a successful triple boot- Windows XP, Ubuntu, and Windows 7. =)


oh, so you opted to 'move' / -- would've been quicker the other way, but then at least you don't have to edit fstab, so I guess in the end it's all the same. :)
> 
I have a quick question for you though. After installing Windows 7 to that new logical partition, the GRUB boot manager was (I guess) overwritten by 7's. I can get to XP and 7 fine, but Ubuntu is not listed. How can I add Ubuntu to the boot list? Thanks!

See link in my signature below (Restoring grub from live cd)

good luck

---

### Post by dcoaster on 2008-12-21
Thanks for the idea, but I was wondering if there's a way of just adding a listing of the Ubuntu installation to the Windows Boot Manager?

---

### Post by logos34 on 2008-12-21
I believe you'll need to use [EasyBCD]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home") if windows 7/vista took over the bootup
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by dcoaster on 2008-12-21
Well, I've followed the instructions and I keep getting an error when selecting the newly created boot manager entry. It doesn't jump to GRUB and instead gives an error saying it can't find the boot manager file created by EasyBCD. Sigh. Any ideas?

---

### Post by logos34 on 2008-12-21
> **dcoaster said:**
> Well, I've followed the instructions and I keep getting an error when selecting the newly created boot manager entry. It doesn't jump to GRUB and instead gives an error saying it can't find the boot manager file created by EasyBCD. Sigh. Any ideas?

So you wrote Grub to the ubuntu / partition using the live cd?  And did you do the 'setup' step *twice* as instructed?  And it can't even find the linux entry just created?  Maybe something in the boot manager has changed with Windows 7. (it was compatible with the [Beta release]("http://neosmart.net/forums/showthread.php?t=2916") though)

Try Method 2 (NeoGrub)

---

### Post by dcoaster on 2008-12-21
Yes. I used the Live CD to boot into Ubuntu (not the installation, but the LiveCD) and did the steps shown. Yes, twice. While doing that however, I got two lines each time that said something had failed, but the final line output for each entry was "successful". I then tried NeoGrub and went into my Ubuntu installation to the menu.lst and copied that to the Windows 7 partition to copy into the NeoGrub menu.lst. Same error at the boot manager occurs. I'll reply with the exact message in a minute.

EDIT: Alright, in the boot manager it says:

File: \NST\nst_grub.mbr

Status: 0xc000000f

Info: The selected entry could not be loaded because the application is missing or corrupt.

----- *This occurs when I use NeoGrub or the manual way.

---

### Post by logos34 on 2008-12-21
> **dcoaster said:**
> I got two lines each time that said something had failed, but the final line output for each entry was "successful".

yeah, disregard the errors...if it ends with 'successful' you're ok.

---

### Post by dcoaster on 2008-12-22
Does it look as though the mbr file is pointed to the right place? I would think it should say C:\ before \NST. Not sure how you can change it though.

Another quick question: Is there a way I can boot my Ubuntu installation (for the time being) without having GRUB?

---

### Post by logos34 on 2008-12-22
> **dcoaster said:**
> 
EDIT: Alright, in the boot manager it says:

File: \NST\nst_grub.mbr

Status: 0xc000000f

Info: The selected entry could not be loaded because the application is missing or corrupt.

----- *This occurs when I use NeoGrub or the manual way.


BTW: the file 'nst_grub.mbr' is basically just a data dump of the first 512 bytes of the ubuntu root partition (containing grub stage1 you wrote to it in 'setup').  same as doing dd if=/dev/sda? of=/nst_grub.mbr bs=512 count=1

The file is apparently there, something is wrong with the 'application' (EasyBCD script?)

You might consider using Super Grub Disk cd (see link in my signature) to boot ubuntu in the meantime, until you straighten this out.

---

### Post by logos34 on 2008-12-22
> **dcoaster said:**
> Does it look as though the mbr file is pointed to the right place? I would think it should say C:\ before \NST. Not sure how you can change it though.

Could you post the file?  Maybe there's a typo in the contents, but I interpreted the error to mean it couldn't even read the file at all

> Another quick question: Is there a way I can boot my Ubuntu installation (for the time being) without having GRUB?

see my previous post

---

### Post by logos34 on 2008-12-22
dcoaster, I have to go now, I have to fix an issue with some updates I just tried to dl and install, then I have to get to sleep, been a long day.  I'll look for an answer over at the EasyBCD forums and let you know if I find any clues (I was just looking at [this thread]("http://neosmart.net/forums/showthread.php?t=315"))

later

---

### Post by logos34 on 2008-12-22
You might actually try doing the dd routine manually and copying the file top C: \NST\

-- worked for [this guy]("http://neosmart.net/forums/showpost.php?p=2978&postcount=1")

now I really have  to go

---

### Post by dcoaster on 2008-12-22
Thanks so much for your help logos! I think we may be getting somewhere. 

Agenda for today: 
Try the SuperGRUB CD to see if my Ubuntu installation is still functional.
Post the menu.lst file from EasyBCD.
Copy the file to C:\NST\ and relist the entries.

I have a quick question though. Since I am triple booting with Win XP and Win7, both have C: drives. How does the program tell the Win Boot Manager which partition (XP or 7) to look at to load the file? Maybe I have it in my 7 partition but it needs to be in the XP partition?

---

### Post by dcoaster on 2008-12-22
Alright, I have some success. I put the Super GRUB disk on a floppy and booted to the GRUB boot manager... so it still does exist. Now to find a way to add it to the Windows Boot Manager. I will open up the Ubuntu installation and see if I can regain that menu.lst.

---

### Post by dcoaster on 2008-12-22
SUCCESS! Wow, after looking back through, my mistake was pretty obvious. The EasyBCD program was pointing to the XP partition to look for the mbr file which was not created since I hadn't installed EasyBCD on XP (only 7). After installing EasyBCD on the XP partition and adding the entry to the bootloader, everything works great. Selecting the entry goes straight to the GRUB bootloader and things work as normal. Thanks for your time in helping solve this!

For future search references: SOLUTION TO GRUB TRIPLE BOOT. RESTORE UBUNTU IN WINDOWS BOOT MANAGER.

---

### Post by logos34 on 2008-12-22
> **dcoaster said:**
> SUCCESS! Wow, after looking back through, my mistake was pretty obvious. **The EasyBCD program was pointing to the XP partition to look for the mbr file which was not created since I hadn't installed EasyBCD on XP (only 7). After installing EasyBCD on the XP partition and adding the entry to the bootloader, everything works great.** Selecting the entry goes straight to the GRUB bootloader and things work as normal. Thanks for your time in helping solve this!

Ok, glad to help.  I'm still not clear on why EasyBCD didn't create an '\NST\nst_grub.mbr' file; you shouldn't have had to also install it in XP (the whole point of EasyBCD is to ease dual-boot)...Since windows 7 was installed after XP it should have taken over the boot process, placing the boot manager files on the prexisting active primary partition (i.e. XP).  Running EasyBCD from windows 7 should have created \NST\nst_grub file in the the base of the XP partition (the root directory)...But then judging from the number of forum posts on the issue the program can do strange things with grub function, not all of which can be chalked up to bugs in previous versions. 

Anyway, the important thing is it works now.  enjoy and feel free to post the winning entry--just for future ref.

happy holidays

---

