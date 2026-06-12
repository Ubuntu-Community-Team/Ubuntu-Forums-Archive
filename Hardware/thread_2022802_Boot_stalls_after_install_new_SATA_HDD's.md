---
title: "Boot stalls after install new SATA HDD's"
date: 2012-07-11
forum: Hardware
---

### Post by DullEdge on 2012-07-11
Today I installed two 3TB Seagate HDD's in a desktop that had two internal HDD's all ready, a 150GB one that runs the OS and a 1TB that is mounted for storage.  After fighting with the bios to get the drive number correct so that it would boot from the right drive the boot stalls after "Checking Battery Life."  Removing the two new drives doesn't help.  If enter single user mode I can mount all the drive by hand and startx.  

Any suggestions?

---

### Post by oldfred on 2012-07-11
Checking battery state seems to often be the last command posted but has little or nothing to do with issues. 

What video card do you have and did you change it?

You can look in Log File Viewer and look at dmesg. That is the same list that booting without quiet splash shows and you want to look for any task that repeats and then fails or fails or has a very long time before it actually loads.

What setting is BIOS in? It should be AHCI with newer drives, but if also booting XP that may not work in XP and with 7 you have to have the drivers installed before changing to AHCI.

I find that the drives are mounted in the same order as the port numbers on the motherboard. I do not have them filled in order and often when I plug in a flash drive that goes into the gap in port order, but sometimes goes at the end? Grub always sees the BIOS boot drive as hd0.

Post link to run of BootInfo from this, but if grub is loading ok, it may not tell much:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

