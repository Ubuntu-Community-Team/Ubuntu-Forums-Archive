---
title: "HDD not recognised by Bios, Missing Operating system"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by SilverSnakeEyes on 2009-10-20
SHORT-
How do I install WD drivers, so that the HDD will be recognized by bios, when I cannot boot into windows, and all I have on hand is a puppy linux & DSL Live CD?

LONG-
I have an old hp that used to have a tiny 30gb hard drive. scrapping that, I added a new 160GB Western Digital IDE drive. I backed everything up on a portable 320GB hard drive, and reinstalled Windows first. It installed fine, but when I restarted, it gave me the 'operating system is missing' error. Didn't think this was such a big deal, as I planned to dual boot Windows, and Ubuntu using GRUB. However, after installing ubuntu to a seperate partition, and Grub to the root sector of the linux partition, it still didn't work. I reinstalled, and it still didn't work, then I reinstalled but put GRUB in the MBR. This still did not work, at this point, I found out that it was not being recognized by BIOS. The HDD is set as the master. I can't run the WD support  diagnostic, as I cannot access windows, so how do I get the computer to recognize it?

Also:

(Fdisk-ed in puppy linux)
My partitions are as follows--
DEVICE        Boot    System
/dev/sda1    *        HPFS/NTFS
___PARENT
/dev/sda2            Extended
    ___Child
        /dev/sda5    SWAP
        /dev/sda6    LINUX/EXT3

tried messing around with different combinations of bootflags, still didn't work.

---

### Post by PRC09 on 2009-10-20
Try setting the jumper on the drive to cable select and see if that helps.In the bios there should be an option to auto detect hard drives,try that and see what it detects.Hope this helps...

---

### Post by SilverSnakeEyes on 2009-10-20
Not sure about the jumper part, but auto just gives me the error all over again.

---

### Post by RJARRRPCGP on 2009-10-21
Your IDE controller probably has the 128 GB HDD limit. (because of using not having 48-bit LBA)

---

### Post by Mark Phelps on 2009-10-21
You need to pay attention to the jumper setting.  Unless you have more than one drive, the easiest solution is generally to REMOVE the jumper.

Also, on some older IDE drives, due to presence of 128GB size limitations prevalent in the BIOSs of the time, there is a jumper setting to limit the drive size. See if your drive has that.

You might also have to experiment with the BIOS drive settings to see if there is one that allows you to see the drive, even then, you're likely to be limited to using only 128GB of the drive.

---

### Post by SilverSnakeEyes on 2009-10-25
Thanks for the info guys, I went back and checked the documentation online, and I removed the jumper only to find out I'd wasted about a week trying to figure out that I needed to remove a speck of plastic. I meant to reply earlier, but my wifi was on the fritz too ^^;

---

