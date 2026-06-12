---
title: "I'm finally gonna do it!"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2006-01-15
I got a teeny tiny 4.1 gig harddrive for my Windows machine, have placed it in the computer, formatted it for Windows (dont ask me why. probably stupid considering I'm just going to put Linux on there), and currently burning the Badger iso onto CD.

But I'm a little nervous. When installing it on my imac, everything went very smoothly, but there was no other OS to worry about. I can't imagine anything screwy will happen with this install, but I wondered if anyone could warn me ahead of time of potential snags.

For example, will it be obvious which drive is which? Will I be able to just tell Ubuntu to erase the whole F drive without it overwriting my C drive? Is four gigs even enough space for the OS plus several applications? Do I need to press a special button (ie:F12) on bootup to access my Linux Drive? 

Any reassurance would be appreciated. I'm probably being silly, but I always get nervous and I won't have internet access until I'm finished.

Thanks y'all

---

### Post by bored2k on 2006-01-15
[LIST=1]
[*]For example, will it be obvious which drive is which?
Yeah. During the disk partitioner step, you'll see the name of the drive **and** its total size, so you **have** to be able to deduct which one's what just by its size.
[*]Will I be able to just tell Ubuntu to erase the whole F drive without it overwriting my C drive? 
Yeah.
[*]Is four gigs even enough space for the OS plus several applications? 
Yeah. My old Ubuntu / partition (that's the one where everything installs to and gets saved by default) used to be just 5gigs big, and most of the time I had about a little 1.8gigs free. Of course, if you pretend on installing another display manager like KDE, expect an increase of about 600mb in disk usage.
[*]Do I need to press a special button (ie:F12) on bootup to access my Linux Drive?
No, it should install boot loader.
[/LIST]

---

### Post by DirtDawg on 2006-01-15
Sweet, thanks alot! I'm writing down any [information]("http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/ch03s03.html") I actually understand (wot's a "port?") from the installation guide just in case. :KS

---

### Post by DirtDawg on 2006-01-15
Oh no. I've run into a problem. I was prompted for user name and password then told to remove the disk so everything would load from the hard drive. 

Then it tried to reboot, but when it got to the GRUB stage, it said "please wait" thenm ominously, "error 21". 

Same thing happened when I manually rebooted. Luckily old Warty Live CD still works.

Help please?

---

### Post by DirtDawg on 2006-01-15
Hmm, I found something about going into BIOS and changing the Master HD: "Type=user, Mode=LBA" and the slave HD to "Type=Auto, Mode=Auto". Now, I have no idea what this means and, even if I manage this, the error happened mid-installation. So... am I screwed or what?

---

