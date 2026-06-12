---
title: "SSIDs changed, boot hung at grub"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by ensnare on 2009-02-03
Hi -- I used acronis to re-image my linux machine but it seems that the SSIDs of the partitions changed and now GRUB can't find my operating system.  How can I find the current SSIDs of the drives and/or boot directly from my /dev/sda1 from grub?

Thank you.

---

### Post by stefangr1 on 2009-02-03
> **ensnare said:**
> Hi -- I used acronis to re-image my linux machine but it seems that the SSIDs of the partitions changed and now GRUB can't find my operating system.  How can I find the current SSIDs of the drives and/or boot directly from my /dev/sda1 from grub?

Thank you.

The easiest way would be to use a live cd to change your fstab, and just change the UUID's to regular filesystem names.

---

### Post by mcduck on 2009-02-03
I suppose you mean UUIDs? ;)

Just run the "blkid" command in a terminal, and it will list UUIDs for all your partitions. Then edit /etc/fstab to use those correct UUIDs and you'll be fine.

---

### Post by cyfur01 on 2009-02-03
First, since SSID's are wireless router names, I assume that you mean UUID's. Just a simple opps. ;)

Next, I would recommend using a Ubuntu Live CD to boot into Ubuntu so you can then run "blkid" from a terminal. This will print out the UUID's and label's for each drive. You can then copy and paste these appropriately to your /etc/fstab and /boot/grub/menu.lst files. Please note the obvious associated risk of editing system files, just as a personal waiver.

The only other option would be that if you know which partition your Ubuntu installation is on, you can edit the grub command. When the grub menu appears while booting, go to your Ubuntu installation and press "e" for edit. This should bring up all the commands used for booting, and one line should include the UUID of the partition. Highlight that line and press "e" again to edit it. Delete everything and replace it with:
```
 root (hd#,#)
```
The numbers correspond to the drive number and partition number, starting from zero. Thus /dev/sda1 would be "(hd0,0)", /dev/sda3 would be "(hd0,2)", /dev/sdc2 would be "(hd2,1)", etc. Once done, press enter, and then "b" to try booting. If this works, then do what I mentioned earlier to fix the UUID's and all should be well.

---

### Post by ensnare on 2009-02-03
Thanks very much for the quick response.  Yes, I meant UUIDs :-\.  This is a RAID0 device with some quirky drivers, will the LiveCD still be able to detect and mount the RAID device?  Does the LiveCD automatically attempt to mount the local file system?  When I installed this machine the first time, I had to use the alternate cd.  Thanks for your help !!

---

### Post by cyfur01 on 2009-02-03
Easiest way to find out is to boot from the Live CD and then open the partition editor (System->Administration->Partition Editor or "sudo gparted" from the terminal) and look to see if it detected individual drives or a volume (I assume that's how it's supposed to differ).

I'm relatively green when it comes to raids. I'm running a hardware RAID5 controller and it's perfectly transparent within Ubuntu (all I see is a 1.3TB volume), but other forms or RAID can be more problematic.

---

