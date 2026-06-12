---
title: "Dual Boot Problem - GPT error"
date: 2013-01-06
forum: Hardware
---

### Post by kenweill on 2013-01-06
Need help on this GPT error.

Last time, I'm dual booting Windows 7 and Ubuntu 12.10. Both we're working except for the NVIDIA optimus which is not detected on Ubuntu 12.10.

As for curiosity, I tried triple booting with Sabayon as the 3rd OS. Installation of Sabayon was successful, booted to Sabayon and update then after restart, problem arises. Can't boot to Windows, can't boot to Ubuntu, can only boot to Sabayon. Other problem on Sabayon, after update, wireless stopped working, LAN stopped working and there's no way I can connect to the internet. So I decided to just reinstall everything.

This time, I installed Windows 7 and was successful. Tried to install Ubuntu again and failed. I can no longer install Ubuntu alongside Windows 7.
This time, on installing Ubuntu, I get an error about GPT.

[CENTER][IMG]http://s14.postimage.org/sf223plch/Screenshot_from_2013_01_06_14_25_19.png[/IMG][/CENTER]

And after pressing YES, partition shown as empty. No windows is detected with gparted. Same with NO, outcome is still the same. No windows partition is detected. As if hard disk is empty.

[CENTER][IMG]http://s13.postimage.org/odey4fsif/Screenshot_from_2013_01_06_14_25_44.png[/IMG][/CENTER]

The same error above occurs when I tried to install Ubuntu via WUBI. 

Weird. It works before but this time, it won't.

Anyone have experience something like this? Can anyone share their experiences and how they fixed it?

Thanks.

---

### Post by TheFu on 2013-01-06
It looks like one of the OSes used an old, out of date partition manager.  Some of the old ones do not support GPT yet.  I know that Win7 and Ubuntu 12.04+ handle this later, so guess which OS was the problem?  You can say it.  Go ahead.

In the future, you need to avoid using older OSes to manage GPT format disks.  Don't use WinXP either as an example. **Don't use fdisk** under any OS, always use **Gparted **or **parted** going forward. These tools handle both MBR and GPT partitioning perfectly.

Don't use WUBI unless you don't have **any** other choice. You will thank me.

So boot into a liveCD or off a flash drive running Ubuntu 12.04 or later.  Then drop to a shell, run $ **sudo parted -l **and post the results.  

If you are in a real hurry, you might try **boot-repair**, but I wouldn't until you see all the appropriate partitions again. Search for "**boot-repair ubuntu**" to learn more.

If you need to run an older OS release, just put it into a virtual machine, like KVM or VirtualBox supports.

Also, you didn't say, but does your BIOS use UEFI too?

---

### Post by YannBuntu on 2013-01-06
Please indicate your BootInfo URL: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by kenweill on 2013-01-06
> **TheFu said:**
> 

Don't use WUBI unless you don't have **any** other choice. You will thank me.

Also, you didn't say, but does your BIOS use UEFI too?

I don't plan on installing via WUBI. I just tested it on WUBI to see if it works on WUBI but I still got the same GPT error.

As with UEFI, I'm not sure. But on boot sequence, I got [UEFI] Slimtype DVD and that's where I'm installing from, from DVD. I tried the other P1 - Slimtype DVD and still the same. Don't know what's the difference between P1 and UEFI.

> **YannBuntu said:**
> Please indicate your BootInfo URL: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I'll post BootInfo later as my laptop is at home and I'm currently on an internet cafe, I'm on a travel. I didn't bring my laptop.

Thanks.

---

### Post by kenweill on 2013-01-07
> **YannBuntu said:**
> Please indicate your BootInfo URL: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

[http://paste.ubuntu.com/1506088/](http://paste.ubuntu.com/1506088/)

---

### Post by TheFu on 2013-01-07
Wish I knew how to help, but my guess is that your **Sabayon** install used fdisk and hosed the GPT partitions.  

All of the partitions are marked as NTFS, which is unlikely.  GPT stores a 2nd copy of the partition table at the far end of the disk (this is one of the major improvements that GPT has over MBR).  Somehow that seems to be missing too.  Ouch.

First step, I would ask **parted** to export the partition table in a machine readable format. This will be your backup so you don't do any more harm by accident.

Second step, I would use a bit-by-bit copy program to mirror this disk somewhere else.  **ddrescue** is my tool of choice, but dd would work too.  I'd want an exact copy of all the bits, including errors, problems, and raw data before I attempted any fixes.

Then I'd do some research on how to restore corrupted GPT tables and try that.  Hopefully, someone will post some better ideas here.  I found this [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) , but cannot vouch for any of the the data. He claims the software is beta level, but also recommends a complete disk backup (though his provided dd command will be extremely slow, always use a reasonable block size with dd).

I did see a message inside the bootinfo asking for an email concerning an UEFI thing.  I'd email a link to the pastebin to that address too.

At least we have more data to work from. Thanks for running the bootinfo.

---

### Post by oldfred on 2013-01-07
As mentioned gpt has a backup gpt partition table at the end of the drive. But if drive was gpt and you install Windows in BIOS mode it converts to MBR, but does not erase the backup gpt table. Then Linux tools see the MBR table & the gpt backup and get confused.

Many have used this, from the author of gdisk.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by kenweill on 2013-01-07
Currently, gparted doesn't seem to detect any partition when used, even if there are actual partitions. What if I'll let gparted create a parition? What will happen to the existing one that is not detected? Will they be replaced? And will it fixed the GPT error I have?

I still have all my files backed up on my external drive. It doesn't matter if I'll repartition or reformat this drive as I still have everything backed up. But before doing so, how can I prevent this error from happening again?

I still want to dual boot Win 7 and Ubuntu 12.10 (both 64bit). I still want to test everything on Ubuntu if all laptop features are working or not, while use Win 7 for work when not testing. Just like what I did on my older laptop. Older laptop is using Ubuntu now, no dual boot. And I also want the same on this new laptop.

I was thinking on using gparted to create the following partitions:
partition 1 - Windows System
partition 2 - My Documents (on a separate drive)
partition 3 - Ubuntu ( / )
partition 4 - Ubuntu ( /home )
partition 5 - swap

But I'm not sure if doing so will actually fixed the problem. I may be able to create these partitions but I don't know what will happen after installing windows, probably back to GPT error.

---

### Post by TheFu on 2013-01-07
I think you need to use the "**fixparts**" program as Oldfred suggests.

It would be really bad to let **gparted** overwrite at this stage.  You haven't necessarily lost any data yet, it is just that the partition table was most like screwed by your **Sabayon **installation. If you do not attempt to re-install that, then you should be fine.Windows7 and later AND ubuntu 12.04 and later (perhaps earlier too) work fine with GPT partitions.
After using **fixparts,** you may be able to boot both Windows and Ubuntu. If not, use **boot-repair**.In theory, only the Sabayon install it toastand even it may not be lost.Hopefully, the explanation is clear[B].
[/B]

---

### Post by kenweill on 2013-01-08
I just did "Recommended repair" with boot-info and I still got the same problem.
Run boot-info again and got this [http://paste.ubuntu.com/1508946/](http://paste.ubuntu.com/1508946/) 
Recommended repair is still the same.

I'll try to use gparted to create partitions then install Win 7 (first) and see if this may solve the problem.

---

### Post by kenweill on 2013-01-08
I just installed Ubuntu, selecting Erase disc, it gives me a warning about GPT but was able to install Ubuntu.

I opened up gparted again and this time, without error.
Last time I installed ubuntu on other machines, I get /boot with ext3 or ext4 on that partition. This time, I get /boot/efi with FAT32. Is this normal? FAT32 for /boot/efi ?

Currently, I'm tring to figure out how to install my machine's NVIDIA Optimus driver, found on [http://ubuntuforums.org/showthread.php?t=2101540](http://ubuntuforums.org/showthread.php?t=2101540)
If this would work, then it's bye-bye win7 in this machine. Else, I'll be back with a dual boot. But this time, I'll use gparted to repartition the hard drive ready for Win 7 (without the system reserved) to install and then Ubuntu as 2nd OS.

I won't ditch Win7 in this machine until all features in this laptop is usable or working on my Ubuntu install.

I won't mark this as solved yet. Not until my other problem is solved, or when after reinstalling Win 7 and able to dual boot with Ubuntu.

---

### Post by TheFu on 2013-01-08
> **kenweill said:**
> I just did "Recommended repair" with boot-info and I still got the same problem.
Run boot-info again and got this [http://paste.ubuntu.com/1508946/](http://paste.ubuntu.com/1508946/) 
Recommended repair is still the same.

I'll try to use gparted to create partitions then install Win 7 (first) and see if this may solve the problem.


Did you run the **fixparts** program?

---

### Post by kenweill on 2013-01-08
> **TheFu said:**
> Did you run the **fixparts** program?

Nope. I just decided to wipe entire disk and decided to install Ubuntu in it. It works. Gparted is is now able to view partitions without the GPT error.

Now, going back to dual booting, I repartition my HDD with:
partition 1 = NTFS (for windows system)
partition 2 = NTFS (for my documents)
partition 3 = blank partition

It was a success.

Then I tried to install Win 7 SP1 64bit, but can't install this time on the HDD. I get "Windows cannot be installed to this disk. The selected disk is of the GPT partition style". This is now a windows issue on GPT partition but I'm wondering why the Windows preinstalled on this laptop was able to work with Ubuntu before. This time with my installer, it won't even install on GPT partitions. :(

As of now, I'll look into this matter for solutions. If not, then I'll be forced to repartition using Windows installer and back to MBR with Ubuntu giving GPT error.

I'll keep this thread updated.

---

### Post by oldfred on 2013-01-08
Somewhere you had gpt and installed Windows in MBR. If you had run fixparts it would have removed the backup partition table.

If you have an efi partition as the first partition you have a new UEFI system and Ubuntu installed in that mode. Windows then will only install to gpt partitioned drives with UEFI. Or both systems need to be UEFI or both systems BIOS based installs.

Both Windows & Ubuntu should from the UEFI menu offer to boot a UEFI or BIOS/legacy/whatever version and how the installer or liveCD boots if how it will install.

If Windows 8 and secure boot:
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
    
But if Windows 7 you can install 12.04 as it works with UEFI but not with secure boot. 12.10 has the newest grub2 2.00 that supports UEFI secure boot. With the next point release of 12.04 it is also supposed to get grub2 2.00, but has 1.99 now.

---

### Post by kenweill on 2013-01-08
Problem is solved.

From Live boot, I used gparted to delete all partitions. Then create a new partition table as "msdos" as it's type, created 2 ntfs partition and an empty 50gig space for Ubuntu.

I installed Windows 7 this time without problem. After installing Windows 7, tried Ubuntu Liveboot again and all partitions are now visible without any error.

Ubuntu works on "msdos" and "gpt" partition type but the Win7 I have only works on "msdos". So I just decided to just use "msdos" to have Win 7 installed, dual booted with Ubuntu.

Thanks for all your help guys. :)

---

