---
title: "Cannot install Ubuntu on SATA drive"
date: 2008-05-08
forum: Hardware
---

### Post by leo11877 on 2008-05-08
Hi
 Not sure what I am doing wrong here.

I have a Gigabyte GA-K8NS Socket 754 Mobo with AMD 64 3200+ cpu. I have 1 Western Digital SATA Disk with 250gb, another one is Samsung 120GB SATA too.

I have Win XP loaded on the 250GB drive. From XP, I can read/write on both Drives well. So I dont think its a hardware issue.

The Mobo supports RAID , but I have disabled it.

I tried installing Ubuntu from livedisk, but it cannot install on either the entire Samsung (2nd) SATA drive or try to repartition the big drive and install there. but neither of them works. It cannot create the partition on either of them. 

When I boot from livedisk , the 1st drive is mounted and i can browse the file etc. When I use the partition manager (Gparted), I can see the Samsung drive if its formatted in NTFS in Windows. However, when I try to reformat it to EXT3, it fails. 

I get something like this
"Attempt to read block from filesystem resulted in short read while creating root dir."

Once this happens, the 2nd drive "sdb" doesnt show up in the partition manager and fdisk -l.
I have tired both 64 and 32 bit Ubuntu disks but same error from both the disks. The 32 disk works on my laptop so i dont think its a matter of bad media.

Not sure what is going on. Someone please help me. I tried searching on google but cant find anything solid.

Thanks

---

### Post by Invader Amoto on 2008-05-08
Hello,
What might help is disabling JMicron. I know that you said you disabled RAID, but in my BIOS JMicron can be on and RAID disabled and it still screws up my system. Turning JMicron off helped me a ton. I hope it works for you.

-Invader Amoto

---

### Post by leo11877 on 2008-05-08
> **Invader Amoto said:**
> Hello,
What might help is disabling JMicron. I know that you said you disabled RAID, but in my BIOS JMicron can be on and RAID disabled and it still screws up my system. Turning JMicron off helped me a ton. I hope it works for you.

-Invader Amoto

Thanks but I didnt see any reference of JMicron on the BIOS. Do you know what its under or how do I turn it off after I boot on livedisk?

Thanks

---

### Post by leo11877 on 2008-05-09
one thing i noticed is that Ubuntu is showing SATA drives as SCSI. Not sure if this is a problem.

---

### Post by Invader Amoto on 2008-05-09
JMicron isn't on all computers. It's a company that makes software drivers for RAID setups. There are other RAID drivers but I think JMicron is the only one that is screwy with linux. I hope you solve your problem.

-Invader Amoto

---

### Post by leo11877 on 2008-05-10
I could format the drive using the Alternate cd and text based installation. The installation goes well, but when its time to start GRUB, it hangs there. After a few tweaks, the GRUB menus shows up but neither of the options work.

Finally, I had to fix the MBR from Windows disk and atleast got XP running back. I think I will try running Ubuntu from inside windows, if it still doesnt work then I will replace SATA with IDE.

Thanks all.

---

