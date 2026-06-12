---
title: "No boot sector on USB HDD after installing Ubuntu 9.04"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by Sick boy on 2009-08-25
Ok, so, I have a 500 Gb Western Digital usb drive with which I am trying to run Ubuntu. Awhile back I tried installing Ubuntu 8.10 to the external drive, but my computer couldn't find a boot sector. My internal MBR was untouched and I had tried installing grub both to the drive (hd1) and the linux partition on the drive (hd1,0). I eventually gave up, but a few days ago I was looking into it again and someone mentioned putting a 1Gb boot partition at the beginning of the drive for computers with older bioses. So, I tried installing 9.04 with my partitions set up as so:

1: 1 Gb ext2 mounted at /boot beginning at sector 1 of the drive

2: 4 Gb swap partition

3: 50 Gb ext3 mounted at root

4: remaining space formatted to ntfs

During installation I specified that the bootloader be installed to (hd1), which should be the external drive. Again my internal mbr is perfectly fine, but my computer still can't find the boot sector when I try to boot from usb.

So, does anyone have any ideas as to how to get Ubuntu booting from my usb? Thanks, any help is appreciated!

---

### Post by mikewhatever on 2009-08-25
There are two things to keep in mind, first, you must boot from the external hdd (bios setting), and second, something must be in the MBR of the external hdd.

---

### Post by Sick boy on 2009-08-25
Alrighty, so I do have my bios set to boot from usb first, however I get an error message saying there is no boot sector on the usb device.

As for the MBR, my understanding was that installing the bootloader to the target drive (in my case, the external) should automatically write the MBR of that device.

So do I have to write the MBR seperate from installing grub? I've tried reinstalling grub a couple times and still no boot sector, so my assumption was either it's writing it to the wrong spot, or it isn't writing the MBR at all.

---

