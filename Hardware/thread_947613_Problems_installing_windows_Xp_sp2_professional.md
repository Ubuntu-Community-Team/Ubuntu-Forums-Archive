---
title: "Problems installing windows Xp sp2 professional"
date: 2008-10-14
forum: Hardware
---

### Post by jmecosta on 2008-10-14
Hi all,

I'm having problems installing windows, the install cd boots and it shows "inspecting hardware configuration message". After this i would expect a blue screen for the remaining install procedure. The only thing i get is a black screen and nothing more.

I'm putting here this because since i have installed ubuntu it might be related to that.

My partition table is:

/dev/sda1             766        2436    13422307+  83  Linux
/dev/sda2   *        2437        4868    19535040   83  Linux
/dev/sda3            4869       14593    78116062+   5  Extended
/dev/sda4               1         765     6144831    b  W95 FAT32
/dev/sda5            5637       11715    48829567+  83  Linux
/dev/sda6           11716       14471    22137538+  83  Linux
/dev/sda7            4869        5636     6168897   83  Linux
/dev/sda8           14472       14593      979933+  82  Linux swap / Solaris

I'm certain windows is able to install only in the first partition on disk, and i want to install it in /media/sda4. However in gparted the /media/sda4 is show in the first section of the disk.

I'm almost sure that the problem is related to this. Did anyone had problems before with this. 

Thanks in advance

Jorge Costa

---

### Post by Vert on 2008-10-14
The Partition shouldn't matter so long as it is a Main Partition and you specify that the partition be formatted into NTFS. As for your CD hanging on a certain screen (doesn't matter which screen it hangs on), you need to make sure that the CD is not scratched, etc., etc. Ubuntu (Linux in general to be honest) has nothing to do with it; it goes straight from your BIOS to your CD-ROM Drive to your CD to your RAM/HDD (It will cache what the CD needs to operate in your RAM before actually writing to your HDD). It skips Linux completely.  -- I believe this is all correct, however, if I made any mistakes please correct me! ^^

---

### Post by jmecosta on 2008-10-15
So i don't know why it hangs, i've try with 2 cds, one of those the original copy from Dell, and i've installed using vmware one of the copys, so i'm sure the problem is not the cd. Could it be because its a Dell laptop and normally these laptops come with a rescue partition that i've erase before?

---

### Post by dorkizzle on 2008-10-15
i've found it easier to install Windows first.

---

### Post by jmecosta on 2008-10-15
Ok i rulled out the fact that sda1 was used by a linux partition. I change the partition table to:

/dev/sda2   *        2437        4868    19535040   83  Linux
/dev/sda3            4869       14593    78116062+   5  Extended
/dev/sda5            4869       11715    54998496   83  Linux
/dev/sda6           11716       14471    22137538+  83  Linux
/dev/sda7           14472       14593      979933+  82  Linux swap / Solaris

So it must be something with the hardware configuration of the Laptop, that's the only thing that i can think off.

I don't want to erase all the disk since i want to keep my linux configuration. But as a last resort i will do it, if no one has other alternatives.

---

### Post by jmecosta on 2008-10-21
The problem was indeed with the partition table, and what was written in the master boot record. To solve this i had to erase completely the disk and install windows after that.

---

