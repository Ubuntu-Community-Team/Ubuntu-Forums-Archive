---
title: "[B]Need help installing Ubuntu onto SATA disk[/B]"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by idiotech on 2005-09-10
Hello All. I am obviously a noob, so please be gentle with me, and please remember that noobs are Human Beings too.
By the way I googled this topic, and a lot of the replies in threads were either too convoluted, or way over my head.

OK This is the problem. 
I just finished building my pc, and really would love to set up a dual boot system,so I can start learning to use Linux.  I have 2 Sata 160gb drives. ECS RS480-M motherboard, Athlon 64 3000+ (939), and so on.  On one of my drives I installed XP with x64 . I have already fully partitioned it. So I planned to install Ubuntu 5.04 on the second  disk. Everything seemed to be going well until it got to the partitioning step. I got the error "No partitionable media were found" Check to make sure disk is plugged in. Of course it was plugged in, and  I have run into this brick wall, and being that I am partially retarded  would appreciate if anyone could help me figure out what I should do to have the installer detect my disks. I tried with an old dinky IDE drive, and it was able to get to the partitioning step.


By the way, in my Bios config under SATA Controller, I select IDE mode instead of RAID mode. Under Hard Disk Boot Priority, I have the Windows drive booting first,  and the the 2nd drive. CMOS lists my Windows drive as slave on IDE channel 3, and the one I plan for Ubuntu as Channel 3 master if that helps any.

In themeantime I'll be doing this.
 ](*,) .

Thanks in advance.

---

### Post by netneo on 2005-09-17
Hi everyone

Even i seem to facing the same problem with SATA drive

My system is:
Processor---->AMD Athlon A64 3000+ having Socket 939
Motherboard----->MSI RS480 with ATI x300 Onboard gfx
Ram------>512 Mb DDR
Hard Disk----->Samsung 80 Gb SATA

I had installed WinXp with NTFS and 3 partitions of sizes 29.2,29.2 and 15.9 gb respectively

Has anyone tried out what one person has suggested--to try and change BIOS settings of SATA drive from Combination to Normal?

Will it work for our systems as well?

Should be doing this without my WinXP getting affected?

This wont affect the GRUB loader will it?

Have any of you faced any problems with Hoary 5.04 after that?

Thank you

---

### Post by docmanny on 2005-09-17
I have an SATA and an IDE on my setup. 
Does the partitioner even see the 2d drive?
Maybe try partitioning the new drive under Windows first. You can always rewrite the partition table...

Just a thought, I'm a relative noob too.

---

