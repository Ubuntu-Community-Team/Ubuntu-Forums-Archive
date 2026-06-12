---
title: "SATA craziness"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by daverave999 on 2007-01-10
I'm a little confused here.

I've just booted up my machine, and I'm missing a drive. Ubuntu is installed on /dev/hda and I also have two 320 GB SATA drives running from an onboard controller. The Western Digital (/dev/sdb) has been kind of flakey for a while, so I'm never surprised when that doesn't show up-I keep meaning to RMA that...

Anyways, the seagate (/dev/sdb) is a couple of months old at the most and it wasn't there on my desktop like it usually is when I booted up.

Is there an easy way to tell whether it's a hardware problem or an OS one?

---

### Post by hal10000 on 2007-01-10
If you think that one of your sata drives is damaged then plug this one off and see what happens.

Can you tell something about your mainboard?

you may install the lshw package (sudo apt-get install lshw) and run it in a terminal window. This gives you lot of info's about your hardware, e.g. you can look if sata controller/disks are recognized. If the output is too long you may use [COLOR="Red"]sudo lshw | less[/COLOR] so you can scroll up and down.

Post what you have found.
Also post the output of [COLOR="Red"]sudo lspci[/COLOR]

Also look into your BIOS to verify that the setting there are correct.

---

### Post by daverave999 on 2007-01-12
I know this isn't what you asked but...
I tried the drive manufacturers diagnostics utilities first, to see what the verdict was from them.  Bizarrely, the Western Digital came up fine, but even running the quick test on the Seagate caused the software to hang at 99%, although it could have still been scanning...

To cut a long story short, I ran fsck on the Seagate and it popped back up again.  Upon reboot, it had gone again.  More fsck and things seem to be getting worse. By this time, I had also managed to get the Western Digital drive back up and running (spurred on by discovering there was nothing wrong with it...)

After much messing about with fsck and altering /etc/fstab (which had worked as intended before) I have now managed to get both drives back online.  For those interested, I found [tuxfiles]("http://www.tuxfiles.org/linuxhelp/fstab.html") and [this place]("http://www.humbug.org.au/talks/fstab/fstab_options.html") very useful when adjusting fstab.

I still have no idea what was wrong but it seems to be sorted for the moment. Thanks for the pointers hal10000.

---

