---
title: "New Core i7 860 based PC"
date: 2010-07-25
forum: Hardware
---

### Post by bingcrosby on 2010-07-25
Hey guys,

I'm about to buy a new PC, and will dual boot Windows 7 Ultimate 32-bit with Ubuntu 10.04 32-bit on it.  It's for general usage, numerical work and HD video and needs to be silent. However, I want to install each OS on separate hard disks, including their boot loaders and linux swap, so I switch with BIOS instead of GRUB.  If Windows is pre-installed, what do I need to do to make sure GRUB and linux swap go onto the Ubuntu hard disk?

Second, I'm going with a Core i7 860, Asus P7P55D-E Deluxe (Realtek 8112L), 4 Gb Corsair Dominator AL-CMP4GX3M2A1600C8 RAM, Asus Xonar ST sound card, Pioneer DVR-218L DVD drive, Zalman CNPS9900NT CPU FAN and Western Digital Black WD1001FALS hard disks.  I was going to get an NVIDIA GT240 but apparently its not quiet, so can you guys recommend me a card that is quiet, good for HD video watching and editing and works stably under 10.04?

Has anyone had any experience with these components on Lucid in regards to stability and what will and won't work?  Particularly, I'm worried about the Ethernet on the motherboard not working and hence Ubuntu not installing properly.  If the particular chip is not well supported, could you advice me as to what PCI/PCI-E card I could buy.  Does Lucid automatically control fan speeds for these components?  Is any driver hacking required?

Thanks and Kind Regards.

---

### Post by quixote on 2010-07-27
Re the grub question.  Assuming you install using a livecd, then when you choose which drive to install to, you'd avoid your Windows drive, and install to the other one, say /dev/sdb.  You'll want the "manual partitioning" option, I'm pretty sure.  I believe, by default, it'll put the bootloader in the MBR of the same physical drive, so it would put it on sdb.  To make sure, though, after selecting "manual partitioning" during install (it's about step 5 or 6), choose "advanced options".  That allows you to select which drive and/or partition the bootloader will be installed on.  (They say it's a bad idea to put it on a partition, and recommend putting it in the MBR of the drive itself.  I.e. /dev/sdb  not /dev/sdb1)

Then which drive was booted would depend on the boot order in the BIOS.

---

### Post by linux18 on 2010-07-27
you should really use 64-bit, my i7 loves it!

---

### Post by efflandt on 2010-07-27
I have an i5 650 3.2 GHz, 8 GB DDR3, 1 TB hd, GT220 video, and it seems pretty quite.   I have not opened the box to see if the video card has a fan, but I have not noticed it (like I have with older video cards).

A quick web search for GT240 found one that is silent.  Look up "zotac gt240".

---

### Post by bingcrosby on 2010-07-28
@quixote If I click the manual partitioning option will I have to create the ext4 and linux-swap myself?  Or can I just use it to check what's going on?  Or should I just unplug the Windows drive to be safest?
Thanks.

---

### Post by quixote on 2010-07-29
Yes, if you manually partition, you have the fun of doing it all yourself.  It's not too bad though.  After you make the partition the size you want, there's a dropdown menu to select filesystem type (ext4 etc), and go to the "mount point" box on the same window, and select whether it's / /home or swap. (Wait, I think the swap choice may be under the filesystem dropdown.  Either way, it's all pretty obvious.)

You can certainly unplug the Windows drive to be on the safe side.  Installs these days use UUIDs, which are unique to each drive.  So it won't be confused because it's suddenly /dev/sdb instead of /dev/sda.

---

