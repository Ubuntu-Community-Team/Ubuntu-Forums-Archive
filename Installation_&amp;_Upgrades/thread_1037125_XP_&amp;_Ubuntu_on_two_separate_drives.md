---
title: "XP &amp; Ubuntu on two separate drives?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by SVEN1 on 2009-01-11
I plan on adding a new SATA drive as my primary and installing on it a fresh copy of Windows XP..

I tried out the Ubuntu using the Ubuntu disc, actually quite like it. But, still a rank newbie....

With my older IDE drive, can I still use it as a slave with only Ubuntu   installed on it?

How do I get both to work on the same computer?

Thanks

---

### Post by Herman on 2009-01-11
> With my older IDE drive, can I still use it as a slave with only Ubuntu   installed on it? :) Yes, you can.
> How do I get both to work on the same computer?You first make a backup of data on your other hard disk just in case you do make a mistake or something goes wrong. A variety of things such as a little grain of dust on the CD or on the optical drive lens can cause some erratic behaviour in the installer/partitioner, although that's fairly rare, and most installations go smoothly. Understand though, that you're not just playing music or a movie, where a small problem would go un-noticed, this is software, and even one decimal point or dot in some program's code that's read wrongly, can result in unpredictable consequences. That's why it's worth making a backup first, even though it's rarely needed.

It's normally very easy to run the Ubuntu installer and when you get to the partitioning part of the process, you choose 'Guided - use entire disk', and then make sure you point the Ubuntu installer at the hard drive you want to use for Ubuntu.

Here's a link to some illustrations of what it looks like when you're installing Ubuntu so you'll have an idea of what to expect, it's for a single disc installation though, [COLOR=#000000][Hardy Heron LTS / Windows XP Dual Boot Installation A]("http://www.herman.linuxmaniac.net/p24.html")[/COLOR].

You have one SATA disk and one IDE hard disk. Your BIOS will normally boot whichever one is listed as the 'first' hard drive.
Ubuntu's boot loader, 'GRUB', (stands for 'Grand Unified Bootloader', will try to guess which hard disc's Master Boot Record to install itself to, and it will scan your computer for other operating systems and try to configure itself automatically. As far as I know, it's the only boot loader in the world that can do that.
Sometimes, especially when there are different types of hard disks, GRUB installs to the wrong hard disk.  If you finish the installation and reboot and you just reboot into Windows, just go into your BIOS and reverse the hard drive numbering order by the settings in your BIOS. Most likely though, everything will be correct already. For most of the time, installing Ubuntu is very simple, easy and quick.

Regards, Herman :)

---

