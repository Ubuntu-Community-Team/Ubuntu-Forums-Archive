---
title: "Problem with step 4 (partition) in 8.10 installer"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by kurt_l on 2009-02-22
Hi, I am a relative newcomer to Linux (ran it on an old Mac for a while a couple of years ago).  I recently came into possession (legally, shame on you!) of a Toshiba Satellite A205 S5804, and Vista Home Premium is such a dog on it that it seemed a perfect time to play around with Ubuntu again.  So I downloaded the i386 8.10 iso, burned it to disk, and booted up, after having done a total wipe and reinstall of Vista from the Toshiba recovery CDs.  The 8.10 LiveCD works very nice.

I had planned ahead and installed Vista into a 40GB partition during the Toshiba recovery install process, leaving 70GB for Ubuntu.  However, when I get to step 4 of the Ubuntu LiveCD install process the partition table is totally blank, and all the buttons are greyed out.  I can't go forward to step 5.

So, I bail on the install, and poke around by looking at the properties of the NTFS drive visible on the Ubuntu desktop.  The NTFS Vista partition really is 40GB in size, as seen under Linux.

I did some googling, and one recommendation I saw was to run GParted.  Luckily it is available on the LiveCD, so I fire it up. It runs OK, and says that there are four partitions: unallocated 1MiB, 1.46GiB Toshiba System Volume, the 40GiB Vista partition, and then 70.32 unallocated, more or less as I expected.  I tried assigning that last unallocated partition to an ext3 filesystem, but re-running the installer still gave me the blank table again.  So I set it back to unallocated with GParted.

So, more searching in the forums... I saw that CalJohnSmith had helped someone with a corrupted partition table; maybe that is what I'm dealing with?  The info he requested is here:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc04bccd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    86960127    41943040    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  3072000, Id=27
/dev/sda2 : start=  3074048, size= 83886080, Id= 7, bootable
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
ubuntu@ubuntu:~$ 

```

I also a forum posting where ElizabethJoan had a somewhat similar problem that appeared to be related the fact that she had a SATA disk (which the A205 has, also). CalJohnSmith, are you out there?  What do you recommend?

Thanks for any help you can give,

Kurt L.

---

### Post by caljohnsmith on 2009-02-22
Hi Kurt, I don't see anything wrong with your HDD's partition table, and the fact that gparted can correctly display the partitions confirms that your partition table should be OK; thus I think the problem must be with the Ubuntu installer. Just as a sanity check, have you run the "check CD for defects" option from the main menu of the Live CD? Also, which partition option are you choosing with the installer, the "guided - use available space" or the "manual" option?

---

### Post by kurt_l on 2009-02-22
Hi,

Thanks for replying... I had done a verify when I burned the CD with Toast under the Mac.  But I went back and ran the Ubuntu start-up check just now, and it's OK, too.

The funny thing is, the installer never gives me that option screen with the choices for "Use largest free space," etc.  It goes straight from "Choose your keyboard" to the blank partition table.  So maybe it is an installer build bug.

Since the partition table seems to look OK, do you think I should just drop back and install using 8.04?  I saw that procedure recommended in a few places in the forum when 8.10 didn't install right off the bat.  Then I could go forward to 8.10 from there if I want.

I also have a junky old desktop laying around here that I will try the 8.10 install on later; that will tell me whether it is computer-specific.

Kurt L.

---

### Post by caljohnsmith on 2009-02-22
Are you using the "Install Ubuntu" option from the Live CD main menu, or do you use the "Try Ubuntu without making changes" option, boot to the Ubuntu desktop, and then run the Ubuntu installer that's on the desktop?

---

### Post by kurt_l on 2009-02-22
I have been doing the "Try Ubuntu without making changes" and then clicking on the Install icon on the Gnome desktop.

Kurt

---

### Post by caljohnsmith on 2009-02-22
It sounds like it might be a bug then with the Ubuntu installer since you don't even get a chance to choose "guided" or "manual" partition options. Have you tried downloading and installing using the Alternate Ubuntu CD? There's links for it at the ubuntu.com website, and I'm thinking that might work for you. Others with a similar problem have done that with success:

[http://ubuntuforums.org/showthread.php?p=6081365](http://ubuntuforums.org/showthread.php?p=6081365)

If you decide to try it, let me know how it goes.

---

