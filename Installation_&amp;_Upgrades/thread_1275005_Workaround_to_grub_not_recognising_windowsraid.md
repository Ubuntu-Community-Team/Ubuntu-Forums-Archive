---
title: "Workaround to grub not recognising windows/raid"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by kaprikawn on 2009-09-25
Hi,

I've got a Windows Vista installation on a striped raid array.  And I installed Ubuntu (Jaunty 64bit) on the same desktop on another seperate HDD.  However, my Ubuntu installation/Grub did not recognise the raid and thus it didn't create an option to boot into Vista.  So currently, my only way of swapping between Vista and Ubuntu is going into the bios and changing the HDD priority to change which bootloader my system loads (hardly ideal).

I've done a bit of googling and think I have come up with a solution.  My plan is to format the HDD which currently has my Ubuntu installation on it, then select that disk as the boot disk in my bios.  Then I will 'repair' my Vista installation using the Vista installation disk.  From my googling I understand that Vista automatically places its bootloader onto whatever HDD is set as the boot disk in the bios.  So this should place Vista's bootloader onto the disk that Ubuntu/Grub should have no problem recognising.  Then I install Ubuntu and Grub should recognise the Vista bootloader and set it up accordingly.  That's the plan anyway.

There's a couple of things I would like to check though.  Firstly (and I know this is an Ubuntu forum but...), how will Vista install it's bootloader onto the blank drive?  Will it do it automatically without me having to do anything, can it install the bootloader onto a disk that has no partitions on it?  Or will I need to create a partition first for it to go on and/or format it to ntfs first?  Secondly, once the Vista bootloader is on this otherwise blank HDD, and I go to install Ubuntu on it, will Ubuntu automatically recognise that and not overwrite it?  Or will I have to be careful with how I set up my partitions when I'm doing my Ubuntu installation?

Any guidance would be greatly appreciated.  My Vista installation is all setup how I like it so I would rather do this process without messing around with or having to reinstall my Windows installation.  So I just wanted to run this by someone knowledgeable before I went off messing with my system.

Thanks in advance.

---

### Post by lemming465 on 2009-10-03
I haven't tried your specific scenario.  I speculate that the minimum requirement to get it to work would be to put a small primary NTFS (partition type 7) marked with the boot flag as the first thing on the separate disk.  Windows needs somewhere to put its boot files.

---

### Post by DSL5 on 2009-10-03
I am doing almost the exact same thing and am struggling with the same problem. If you get this working, please post how you did it here, as it would be much appreciated.

---

