---
title: "Recover Data from HDD or Reformat"
date: 2011-07-23
forum: Hardware
---

### Post by pgn674 on 2011-07-23
A friend found a laptop in her front lawn by the road, with no name or company info on it. She tried turning it on, but it asked for a password, so she brought it to Best Buy's Geek Squad. They said the hard drive was encrypted (not sure how much I trust their analysis). She called the computer manufacturer (HP), and they said it hadn't been registered so they don't know whose it is. Now the battery is dead, and there was no power cord left with the laptop on my friend's front lawn.

She brought it to me to look at. I would like to try and get a name off the hard drive, or failing that, reformat it since we can't return the computer to the owner. I've got the hard drive hooked up to a SATA to USB adapter.

The drive is showing up in /dev/ as sdb, but there is no sdb# showing up, and sdb doesn't appear in /proc/partitions. I tried running dd and ddrescue on /dev/sdb to try running some partition recovery tools on an image of the drive, and both complete successfully right away with 0 bytes copied.

I've run a lot of hardware viewing commands, including:
lspci
lsusb
hwinfo
lshw
fdisk -l
cat /proc/partitions
ls /dev/sd*
I've attached the outputs of all these to this post.

I would like to know what is going on here. Might there be some BIOS- or ROM-enabled switch on the drive that prevents reading without the right BIOS or ROM and the right password? If so, is there any way to verify this is the case for sure? And can I reformat the drive for reuse?

---

### Post by Blasphemist on 2011-07-23
I don't think I can help with the direction you are going. For a small price you could buy a universal power adaptor that would work for it. They come with a bunch of different power plug ends and aren't totally universal but you will very likely be able to find one that will work easily.

With that, you can just try booting to a live ubuntu cd and using nautilus to just try and explore the files after mounting the partition(s). I think. If not, there are utilities such as testdisk/photorec that should work to get more.

---

### Post by pgn674 on 2011-07-23
Yeah, hate to get a power supply without knowing if the hard drive is usable, but my friend or I might have to.

I also tried using the SATA to USB adapter with Windows, and Windows says the hard drive is not initialized, and offers to write a Master Boot Record. Still not getting even a hard drive size, though.

---

