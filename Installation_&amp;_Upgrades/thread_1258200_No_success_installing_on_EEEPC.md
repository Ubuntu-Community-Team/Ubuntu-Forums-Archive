---
title: "No success installing on EEEPC"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by JewelledDragon13 on 2009-09-04
I've got a working bootable flash drive of <a href="http://wiki.eeeuser.com/ubuntu:eeexubuntu:home">eeeXubuntu</a>.  It will boot on my desktop, but it won't boot on my eeePC.

I boot up the eeePC with the flash drive in the USB while holding down Esc.  The menu comes up that lets me choose to boot from the flash drive.  I select this.  The boot menu begins to execute, then prompts me to press Esc to boot, with an 8 second countdown.  Whether I press Esc or not, it boots normally into Xandros.

I have an eeePC 900 running Xandros.

---

### Post by JewelledDragon13 on 2009-09-05
Thanks, guys.  You're a big help.

---

### Post by Herman on 2009-09-05
I had the same trouble until I entered the eeepc's bios and made the USB drive number 1 drive, just telling the BIOS the USB should be first in the boot sequence didn't seem to be working for me either.

I'm not sure about the eeepc you're working on, it's a bigger model than the ones I've installed in, but I think it's F2 to enter the BIOS, then go to the BOOT tab, and there are two places with settings for the drives. One's the BIOS 'boot order'  and the other is the  'drive order', (numbering). Normally just setting the 'boot order' is enough in most computers, but the eeepc seems to need the drive order changed as well for some reason.

Luckily with modern versions of Ubuntu we use file system UUID numbers for identifying the partitions, so it won't matter what order the BIOS wants to have the drives numbered in, GRUB will still be set up okay. :D

---

### Post by Herman on 2009-09-05
:idea: The eeepc I was installing in has an SSD drive instead of a hard disk drive.
Many people believe that aligning the start of the partition up with the flash memory's erase block boundary will help to allow the operating system to run smoother  and faster and give the SSD drive a longer life expectancy.

I used GParted in my Ubuntu Jaunty Jackalope USB to pre-partition the eeepc's SSD drive before I began installing.
I removed the check mark from the 'align partition on cylinder boundaries' check box in GParted, and set the number '1' in the spinbox for how many MiB of free space I wanted to have before the start of the partition.
I made my partition fill all of the free space that was made by deleting the Xandros partition because later I made a swap file instead of a swap area.
I chose the ext4 file system because it is the most advanced file system at the moment and it has special features built into it for use in SSD drives and other kinds of flash drives.
Before I clicked 'apply', I clicked 'properties' in GParted to check, and GParted was going to make sector number 2048 the fist sector for my new partition. That's exactly what I wanted, I hit 'Apply', and created my new partition for Ubuntu.

The Jaunty Jackalope installer protested a little about me not letting it re-format the new partition and about me not creating any swap area, but fortunatley it let me proceed anyway.

If what I've just written doesn't make any sense to you then just ignore me. I have another eeepc that I have been using for quite a long time and it just has the standard partition alignment and it works quite alright. I'm only writing this here for geeks and perfectionists. Most people can skip this post and just click 'automatically install in the free space' and Ubuntu will install just fine. The difference is probably negligible and it's not worth getting a headache over.
Before this I thought we needed fdisk to customize the start point of our flash memory partition on an erase block boundary though.
Here are a couple of the links I've been reading so you might understand where I'm getting my ideas from,

[Thoughts by Ted]("http://thunk.org/tytso/blog/") - Theodore T'so's blog

[HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile") - by iva2k.

---

### Post by JewelledDragon13 on 2009-09-06
There's no drive order setting under the BOOT tab in my eeePC.  There's the boot order tab (I already have external media set to the first position), boot configuration, and a couple of toggle settings.  It also isn't hiding under any of the other tabs.  The closest thing is the IDE configuration, but I don't want to mess with that, do I?

Thanks for the ideas, though.

---

### Post by foobic on 2009-09-07
Perhaps it's different on the 900 but like Herman describes, on my 901 under the Boot menu I have:

[LIST]
[*]Boot device priority
[*]Hard disk drives
[/LIST]
Rather counter-intuitively, the first doesn't allow booting from USB drive (only hard disk or CD, which I don't have). Instead the USB drive appears in the list of hard disks and it needs to be at the top (chosen in second menu) in order to boot from it.

---

### Post by JewelledDragon13 on 2009-09-10
The plot thickens!

The hard disk drives menu is sometimes visible and sometimes not.  I rebooted it earlier today and saw it and was kicking myself for how I could have not noticed it.  Rebooted again just now: gone.  Just the boot device priority menu.

Anyone have any idea what might cause this?

---

