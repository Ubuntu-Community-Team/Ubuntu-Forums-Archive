---
title: "Installing Ubuntu problem with harddrive"
date: 2008-08-16
forum: General Help
---

### Post by jbkemp on 2008-08-16
I have a computer that I have recently tried installing Ubuntu on.  It previously had Windows XP.  When I tried installing, it didn't even see my harddrive.  I researched and researched and am thinking its something to do with the way my drive is formatted?  I have since used the windows XP cd to delete the whole drive and it still doesn't see it.  I have used the windows 98 cd to format the harddrive and it still won't seeit on Ubuntu's setup.  I have tried using Linix System Rescue Disk and still can't figure this out.  I just simply want to install Ubuntu onto my computer.  Please help me because I am a noob with this.  Thanks in advance.

---

### Post by BTMark on 2008-08-16
When you boot from the Ubuntu CD, and it brings you to the partitioning phase, can you select "Guided - use entire disk"? Ubuntu can't install on partitions already there, and if you're not going to dual boot, you can always set up your partitions later.

---

### Post by iaculallad on 2008-08-16
-Disregard-

---

### Post by jbkemp on 2008-08-16
> **BTMark said:**
> When you boot from the Ubuntu CD, and it brings you to the partitioning phase, can you select "Guided - use entire disk"? Ubuntu can't install on partitions already there, and if you're not going to dual boot, you can always set up your partitions later.



When it gets to the "prepare partitions" screen in setup, it doesn't list any options.  It also has "new partition table, new partition, edit partition, delete partition, undo changes to partitions" all glazed over so I can't select them.  It lets me click forward though and when I do it says, "No root file system is defned. Please correct this from the partitionin menu."  I am stumped.


Update: It is now about 30 minutes later.  I used my windows XP cd to delete the partition so its unformated at this time.  I used the Ubuntu CD and it again would not see my harddrive.  Same symptoms as above states.

---

### Post by PegM_4 on 2008-08-16
I am having the exact problem.:confused:

---

### Post by jbkemp on 2008-08-17
> **PegM_4 said:**
> I am having the exact problem.:confused:

I hope someone out there can help us. : /  I really want to cut the strings with Microsofts leash.

---

### Post by jbkemp on 2008-08-17
> **PegM_4 said:**
> I am having the exact problem.:confused:

What kind of motherboard do you have??

---

### Post by todak on 2008-08-17
Assuming you are using the LiveCD, during installation, you should get a screen that asks if you want use the entire disk for ubuntu..."Guided - use entire disk". Make sure it is checked. ;) It should work no matter what formatting you have on the disk, if you choose that option.

---

### Post by jerome1232 on 2008-08-17
> **jbkemp said:**
> What kind of motherboard do you have??
 Yes motherboard models would be helpful it sounds like Ubuntu isn't recognizing the hard disk controller. Knowing the chipset/motherboard model would help to see if there are known issues with your chipset or if there are workarounds.

---

### Post by jbkemp on 2008-08-17
> **todak said:**
> Assuming you are using the LiveCD, during installation, you should get a screen that asks if you want use the entire disk for ubuntu..."Guided - use entire disk". Make sure it is checked. ;) It should work no matter what formatting you have on the disk, if you choose that option.

Not even getting that option yet.

---

### Post by jbkemp on 2008-08-17
> **jerome1232 said:**
> Yes motherboard models would be helpful it sounds like Ubuntu isn't recognizing the hard disk controller. Knowing the chipset/motherboard model would help to see if there are known issues with your chipset or if there are workarounds.

I bought this as a second computer recently and don't remember the motherboard model but do know that its Desktop 64 bit 1.8 GHz AMD Processor.  Having a hard time finding the computer info from ubuntu when I run it from the CD.

---

### Post by PegM_4 on 2008-08-17
> **jerome1232 said:**
> Yes motherboard models would be helpful it sounds like Ubuntu isn't recognizing the hard disk controller. Knowing the chipset/motherboard model would help to see if there are known issues with your chipset or if there are workarounds.

I know just enough about computers to be dangerous.  Hopefully, this is the info you need.  I'm copying it from Everest Home Edition:

Motherboard
  CPU Type:  Intel Pentium 4HT, 2800 MHz (14x200)
  Motherboard Name:  Asus P4SD-VX
  Motherboard Chipset:  Intel Springdale i865PE
  System Memory 1024 MB (DDR SDRAM)
  BIOS Type:  AMI (09/19/03)
  
Is that what you need?

> **todak said:**
> Assuming you are using the LiveCD, during installation, you should get a screen that asks if you want use the entire disk for ubuntu..."Guided - use entire disk". Make sure it is checked. ;) It should work no matter what formatting you have on the disk, if you choose that option.

Yes, I'm using LiveCD, however, it never asks if I want to use the entire disk for ubuntu.  I never see "Guided - use entire disk".

---

### Post by PegM_4 on 2008-08-17
I also tried it as in this page [https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix), but even though when Knoppix loads, it shows my partitions on the desktop, when I try to run qtparted, it still won't let me do anything.:confused:

---

### Post by PegM_4 on 2008-08-18
Me again.  I have now, after much struggle with files that I couldn't delete, deleted the drive and re-established it as an empty drive.  All that is now on the computer is drive C:\ with WinXP Pro and and empty D: drive.  Ubuntu's gparted still won't recognize it or give me any options.  Could there be a problem with the version I downloaded?  I got it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and chose Ubuntu 8.04 LTS Desktop Edition - Supported to 2011.  

Using Paragon Partition Magic, I deleted D: drive and converted it to Ext3FS as it said it was for Linux.  Still, the gparted won't recognize it.

This is starting to get very frustrating, but what I have experienced with the LiveCD, except for the partitioning problem, I think I will really like it.

---

