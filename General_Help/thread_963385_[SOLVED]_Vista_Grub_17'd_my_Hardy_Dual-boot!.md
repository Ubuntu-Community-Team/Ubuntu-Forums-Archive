---
title: "[SOLVED] Vista Grub 17'd my Hardy Dual-boot!"
date: 2008-10-30
forum: General Help
---

### Post by soluphobe on 2008-10-30
I've looked around about Grub 17 for a while, but I'm really nervous about screwing up my hdd farther (BIOS still works), so I'm posting my story here.  I'm kinda scared to do anything at this point, because I'm unsure what to do:

I recently purchased a laptop with Vista installed (ONE hdd).  I booted it a few times, and it worked.  But I wanted Linux on there, so I examined the partitons.  It was divided into two main partitions of about equal sizes (C: and D:```

```) so I went ahead and installed Ubuntu on what had been D: (sda5 I think, when I was done making a swap file: sda4).

I booted Ubuntu a few times, and got it configured.  I got my driver packages, moved my files from my old PC, and started being happy.

Then, I decided to boot back into Vista (don't recall why).  There were two entries for Vista/Longhorn in my menu.lst, one looking at (0, 0) and the other at (0, 1).  I tried the (0, 0) one first.

That's when the trouble began.  Vista didn't act normally and seemed to boot from a different . . . theme, almost.  Then it flashed to 800x600 res and gave me a message about RECOVERY.DAT, and how there was an ERROR.

Darn, I thought. Well, I guess I'll try the second loader.  I powered it down and restarted.

```
Grub loading stage 1.5

Grub Error 17
```

Anyway, now I've got Grub 17 and it won't boot anything (won't get to the menu).  I booted from a Hardy livecd, forcemounted the VistaOS partition (my other partition mounted fine), and commented out the Vista/Longhorn loaders in my menu.lst, thinking one of those would do the trick ('cos grub wouldn't have to look for them).  Still nothing.  In addition, the partition I installed Ubuntu on shows up as '148.5 GB Media' even though Ubuntu's files are still there

In my fstab (the one on 148.5GBMedia), only sda4 and sda5 show up.  These are my swap file and the partition I installed linux on.

I received a message about adding lines to my devices.map (?, anyway its the .map file in /boot/grub/) that represented the Vista hdd.  This happened when I tried to mount the VistaOS partition by clicking on it.  I looked, and sure enough that line isn't there (this is when I forcemounted it).  

If you guys have any advice about fixing Grub 17, I'd be **overjoyed **to hear it.

For the record, here are my thoughts about continuing next:

1.  Use GParted from the Livecd to wipe the disk, then reinstall vista from my OEM disk and forget about linux.  This is very hard for me.
2.  Use the Livecd install to format the entire hdd and ditch vista altogether.  I'd like to do this, but I want a windows installation in case I run into compatability.
3.  I don't have any precious data, I've owned the laptop for <36 hrs and it's all backed up.
4.  Should I be worried that sda5 is such a large number?

---

### Post by garyedwardjohnston on 2008-10-30
Sounds like a big mess.

I'd reinstall Ubuntu on the whole computer and use virtualbox to run vista when you periodically want to use it.  I find this much easier when Linux is the main system and Vista is used only on occasion.

[www.virtualbox.org](www.virtualbox.org)

---

### Post by caljohnsmith on 2008-10-30
Since your computer is new and you don't have any data you want to recover, I would recommend reinstalling Vista via your OEM disks, and once you confirm that Vista boots OK again, then use Vista's disk management to resize the HDD to make room for Ubuntu (if you need to make room). It's important to try to use Vista's disk management for any partition changes, because Vista maintains its own partition table outside of the main partition table in the MBR (Master Boot Record); in practical terms that means you can break Vista if you use some other partition editor to do your partition changes (although you can usually fix Vista afterwards, but it is a hassle). 

Also, my guess is that the (hd0,0) entry you used to boot Vista might have launched the Vista recovery partition, and that's what really screwed everything up. Therefore, after you install Ubuntu, I would delete any options in Grub that would boot any Vista Recovery partitions you might have. Then I think you will be fine. 

If you need any other info/details, let me know, otherwise let me know how it goes. :)

---

### Post by soluphobe on 2008-10-30
Thanks, guys.

I'm away from home now, and I've got the ubuntu livecd, but not vista.  I'm checking out virtualbox now, that might solve it.

---

### Post by soluphobe on 2008-10-30
Solved:

VirtualBox seems to take care of my needs.  I've overwritten the hdd w/ubuntu, and I've got it back to the way it used to be.  I didn't like Vista anyway, so I'm counting this as a plus.

Thanks!

---

