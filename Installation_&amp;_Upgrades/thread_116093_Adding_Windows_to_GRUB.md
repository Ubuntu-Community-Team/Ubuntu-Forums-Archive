---
title: "Adding Windows to GRUB"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Zatu on 2006-01-11
This might get a bit hard to follow, but please bear with me.

My system has two hard drives. It came with a 40 gig Windows drive. I stuck some old 6 gig drive out of a dated PC in there to install Ubuntu, and set up GRUB on the Windows drive (which was the master).

Then I got a shiny new 250 gig drive. (All of this is PATA if that matters.)

I removed the 6 gig drive and unhooked the Windows drive (don't quite remember why I did that, probably to avoid a master/slave issue) and put in the 250 gig drive and set it as master. Installed Ubuntu. Happy happy happy. Hooked the Windows drive back up as slave.

I'm not surprised GRUB has no idea that there's a Windows installation on the system right now.

But it's a problem because I need to get into Windows for some things.

I looked up "How to add Windows entry into GRUB menu?" in the FAQ guide.

It referred to "How do I check disk space and view the partition table?" I didn't find anything relevant to reinstalling GRUB there. So I went to the next step.

Problem is that there is no "System->Administration->Boot". There's System, and there's Administration under that, but there's no Boot.

So:

How do I get "Boot" to show up in the administration menu?
In case I can't, how can I get GRUB to see the Windows installation?
If that fails, how do I reinstall GRUB without reinstalling Ubuntu?

Thanks in advance.

---

### Post by southernman on 2006-01-11
Running a quick search on the forum for "reinstall grub" returned this 
( [http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub") ) among many others.

HTH's

---

### Post by Zatu on 2006-01-11
Yes, I saw that, and this post made me think twice and seek other ways:

[http://ubuntuforums.org/showpost.php?p=207680&postcount=8](http://ubuntuforums.org/showpost.php?p=207680&postcount=8)

I'd really much prefer not to ruin my current install, and my understanding is that it's a potential side effect of that first method.

The other methods on that page require things that I don't know (I don't know what hd0,0 is, I'm used to seeing hda1/hdb5 etc.) or are for circumstances that I don't believe I have.

---

### Post by micjustmic on 2006-01-12
It's actually not very difficult, but you may need to experiment a little.

in a terminal type, "sudo gedit /boot/grub/menu.lst" without the quotes, of course.

(I suggest you make a backup before doing this, just in case.)

Scroll to the bottom of the file, you'll see the entry(s) for your Linux partition(s).

Right under that add these lines.


title		Windows 95/98/NT/2000 (make this whatever you want it to say)
rootnoverify		(hd0,0) 
makeactive
chainloader	+1

Now here's the trick, where it says, "root       (hd0,0)" you'll have to figure out what drive and partition your Windows partition is.  The format is this, hd is of course, always the first identifier in grub.  It doesn't use sda or hda, ALWAYS hd#,#.

The first number is the drive, and this is dependant on how your BIOS arranges the drives, so if it lists SATA drives first, then the first partition on the first SATA drive is (hd0,0)  the second partition is (hda0,1) and so on, if your PATA drive is listed first, (as reported to the OS) then your first PATA drive and partition is (hd0,0) making your next drive and its first partition (hd1,0).

Just remember the first number is the drive, the second is the partition.

In some cases with SATA (I don't know about mixed systems, I have two SATA drives in mine) you have to do a little trickery to get Windows to load, for example, here's the boot menu from my system.

```
title		Ubuntu, kernel 2.6.12-10-686-smp 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda1 ro vga=788
initrd		/boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-10-686-smp
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		
root

title		Other operating systems:
root

title		
root

title		WindowsXP Pro
rootnoverify 		(hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

I put the blank lines just for space in the menu, but notice the (hd1,1) under the Windows title.  Second drive, second partition.  

Also, I have to map the drives opposite one another just as control is handed to the OS (Windows) or I get an error.  I'm not exactly sure why this is needed, perhaps someone with more than 6 months experience with Linux can explain it.  I haven't been using Linux very long . . . 24 years in computers and I'm a virgin all over again.  ;) 

Works just fine for me (and it's a myth that you have to install Widows before Linux or you can't get to your Linux partitions.  It's EASIER, if you install Windows first, but I installed Linux, then Windows and simply set grub up using a Linux Live CD. I only did this for two reasons, one, to see if it could be done, and two, I simply forgot to install Windows first.  :rolleyes: )

Some may tell you that you have to add a "hide" command as well, all this did for me was make my Linux partition STAY HIDDEN, I had to re-run grub from a Live CD and unhide the partition before grub would even load properly.  Glitch, I'm guessing, but eveything works just fine without the "hide" command.

I hope this helps, and hopefully someone else with more knowledge will expand on this, and correct any mistakes I may have made.

Mic

---

### Post by Zatu on 2006-01-12
Thanks, I added the lines to menu.lst and the option was there at boot, but when I selected it it just displayed the lines that were there and did nothing else.

If it's a relevant detail, GRUB is on both drives.

Also, I noticed that in the example given (which I later found exploring the file) XP isn't there. Does that matter? Because I'm trying to boot XP Home.

EDIT: I'm the experimenting type, so I added the stuff to remap the drives and it works now. Never thought I'd be so happy to be in Windows again. Thanks!

Also, I heard Windows likes to be on the C drive, so remapping the drives might be what makes Windows think it's on C and not D.

---

### Post by micjustmic on 2006-01-12
While it's a common belief that Windows itself prefers C:\, it's actually older programs that cause a problem if Windows isn't on the C: drive.

They are "hard-wired" to look for windows there instead of %sysdir%.

Windows is fine on any drive letter/partition.  My copy is sitting and running just fine on the D: drive.  :) 

I think it has more to do with mapping the Windows boot-loader to the first drive than anything else.  To install Windows I had to swap the drive with the other in BIOS so Windows would install its boot-loader on that drive, it couldn't install it's bootloader on the Linux drive, it doesn't understand the file system at all, or the way the boot-loader is formatted, and Windows INSISTS on installing its own boot-loader . . .

So, and I'm speculating here, mapping the drives to "swap," so to speak fools Windows bootloader into "thinking" it's on the first drive.  The Windows boot-loader always needs to be on the first drive in the system, no exceptions, or it won't load, but the Windows directory can be anywhere on the system.

Mic

PS,
I'm glad you got it working and that I was able to help in a small way, but ultimately I only gave you a starting point and you figured it out yourself.  Good job.  :D

---

