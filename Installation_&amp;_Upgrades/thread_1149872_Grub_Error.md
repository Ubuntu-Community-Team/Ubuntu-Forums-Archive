---
title: "Grub Error"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Peter-1992 on 2009-05-05
HI all, 
 
For some months I've been running a dual boot on my laptop with regularly-updated Ubuntu and Vista Home Premium. I recently lent my latop to a friend so he could familiarise himself with ubuntu before deciding whether or not he wanted to install it for himself, being very much computer-illiterate. 
 
After getting my laptop back, I tried to boot and received Gurb Error 17 error message. I asked what he'd been doing and he's reformatted my linux hardrive partition, from windows, without restoring/resetting the mbr. As a result, I cannot now boot into either windows or linux as the partition its trying to boot into no longer exists. 
 
WHilst I am still a relative novice on ubuntu (a basic grasp of terminal commands etc) please reply as if talking to an absolute beginner for fear of further damage . . .
 
So, is there any way to either reset the mbr to enable grub to work and boot into vista, or to re-install windows boot manager and bypass Grub completely? Bear in mind, i cannot boot into vista, so all changes will be run from a live Ubuntu 7.10 CD. 
 
Thanks in advance for any advice and help given, 
 
Pete

---

### Post by Mark Phelps on 2009-05-05
> **Peter-1992 said:**
> After getting my laptop back, I tried to boot and received Gurb Error 17 error message. I asked what he'd been doing and he's reformatted my linux hardrive partition, from windows, without restoring/resetting the mbr. As a result, I cannot now boot into either windows or linux as the partition its trying to boot into no longer exists. 
 
WHilst I am still a relative novice on ubuntu (a basic grasp of terminal commands etc) please reply as if talking to an absolute beginner for fear of further damage . . .
 
So, is there any way to either reset the mbr to enable grub to work and boot into vista, or to re-install windows boot manager and bypass Grub completely? Bear in mind, i cannot boot into vista, so all changes will be run from a live Ubuntu 7.10 CD. 
 
Thanks in advance for any advice and help given, 
 
Pete
wow - some "friend" -- reformats YOUR drive!!

Do you know for sure that the Vista partition is still there?  How do you know that your "friend" didn't reformat the entire hard drive?  Since you can't boot, it's hard to tell.

You'll need an Ubuntu LiveCD and a Vista DVD (or Vista Repair CD).

Using the first, boot into the LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one). This will list the partitions that remain on your drive.  If Vista is still there, we may be able to reinstall GRUB and get you back into Vista.

IF we can't reinstall or fix GRUB, you will need to boot from the Vista disc in order to do a Startup Repair.  That will restore your ability to boot into Vista but it will overwrite GRUB in the process.

---

### Post by raymondh on 2009-05-05
> **Mark Phelps said:**
> 

IF we can't reinstall or fix GRUB, you will need to boot from the Vista disc in order to do a Startup Repair.  That will restore your ability to boot into Vista but it will overwrite GRUB in the process.

Peter .. mark has a point.  Boot into the vista install/recovery disk and navigate to system repair.  once there, go to command prompt and type

bootrec.exe/FixMbr

If the format has changed to FAT, you'll need to FixBoot first and then FixMbr

Reboot.  With Vista up, you can now decide whether you want a fresh ubuntu install and even modify your partitions to suit your needs (i.e. separating /home, etc)

Good luck

---

### Post by caljohnsmith on 2009-05-05
I just wanted to mention that you don't need a Vista Repair CD to install a Windows MBR to your HDD; you can do it from your Ubuntu Live CD by doing the following commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Those commands will install a Windows equivalent MBR to your sda drive so you should be able to boot directly in Vista again (assuming your Vista partition is still there and OK). Let us know how it goes or if you run into problems.

John

---

### Post by Peter-1992 on 2009-05-06
Thanks for the replies. 
 
Mark, I'm fairly sure he didn't touch my C drive partition holding Vsita - for one, he was still using the OS after the format - surely he couldn't be running an OS if the partion holding it had been formatted? Also, and more tellingly, when i explore the hardive from a linux live CD I can still see all the windows files untouched so i'm fairly sure. 
 
I'll have a go at re-installing GRUB though, i'm just mainly nervous about playing with the machine further in grey areas but I've just got an external HDD to back up all my documents - i'll be much more confident playing after that's done.
 
I have had a read on countless forums over the last week and a few have pointed me towards a windows recovery disk - if only I had one supplied with the laptop . . . The only things I have a factory set up restore disks which probably would work but until i'm sure I can't solve this without a fresh install I'll try to defer this. 
 
lilo? I'd read this as well in a few places so this will be my next port of call in the moring. 
 
Thanks again for all the help guys - I'll post again on my findings after trying the above
 
Peter

---

### Post by scooterkool on 2009-05-06
Peter,
I had the same problem with the grub error 17.
My scenario was the same. 
I used a super grub cd [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) to fix it.
Quick and easily. 
Ubuntu is gone, but grub thinks it is still there.
The Super grub cd will give you the option to remove ubuntu.
Search the super grub site for more details.

:guitar:

---

