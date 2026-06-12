---
title: "XP Grub probs"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by brad1138 on 2009-08-23
I have XP installed on the primary HD and Ubuntu on the secondary (both 40gig) I am trying to reinstall XP. I deleted the main partition in XP setup, recreated the partition, formatted and started install. I would have thought that would have removed Grub, but when it restarts after copying the setup files, grub comes up and I get an error after selecting XP. I want to completely remove grub but I don't have a floppy drive, I can't select "R" from the XP install because it doesn't give that option when XP isn't installed. 

I plan on reinstalling XP and Ubuntu (if I need to) but I can't if I can't get rid of Grub. I can boot into Ubuntu, can I do it from there?

Thanks,
Brad

---

### Post by j7%&lt;RmUg on 2009-08-24
Well if you wiped the XP disk and then reinstalled XP on it, wouldnt grub be on ubuntu?, it usually is.

---

### Post by Monkey.feets on 2009-08-24
Maybe check grub boot settings to see if it is pointing to the right partition to boot XP.  After you deleted partition and made a new one the XP partition number probably changed.

---

### Post by brad1138 on 2009-08-24
> **nisshh said:**
> Well if you wiped the XP disk and then reinstalled XP on it, wouldnt grub be on ubuntu?, it usually is.

No, I think it is on the master, it is still there (although doesn't work) if I unplug the secondary, ubuntu drive.


And this is my grub, I think it is correct.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
# savedefault
# makeactive
# map		(hd0) (hd1)
# map		(hd1) (hd0)
chainloader	+1


I am thinking of putting in a new Master drive (I have a few), grub would definitely be gone then, but then I still have a problem drive I'll have to deal with later.

---

### Post by j7%&lt;RmUg on 2009-08-24
Well if you only reformatted one partition on the XP drive, maybe grub is on one of the other partitions on the XP drive?

Im gonna be that if you wipe the ENTIRE XP drive clean then grub will disappear.

---

### Post by wojmur on 2009-08-24
As far as I understand, GRUB stage1 and 1_5 live in the MasterBootRecord and immediately after it, which is **outside** of any partitions. It's together with the partition table. And I think if there is no stage1 in the MBR the BIOS will look for an active partition and try to run a boot loader from its boot sector. And I think that's what XP might be counting on, by default. Your repartitioning and reinstalling windows have not necessarily touched the MBR, so your old GRUB might still live there!

Unfortunately, I don't know how to wipe the MBR. Maybe GRUB in your working linux has an 'uninstall' option of some sort? Or maybe there is a command in GRUB shell to do it? You would enter it by pressing 'c' instead of selecting operating system from the menu.

I don't have access to any of that software atm, so can only suggest what I'm thinking.

Good luck!

---

### Post by brad1138 on 2009-08-24
Ya, this is getting to be a real pain in the neck. I downloaded "killdisk" and completely wiped the XP drive and Grub is STILL there!!! Killdisc is supposed to write 0's to every single area of the drive, making it like new, how is Grub still there?

Nisshh, The Master/XP drive has no partitions, I use it all for the OS.

I do also have a 500 gig SATA drive I use for storage, Maybe I'll unplug that drive also. But then it screws with the drive numbers after install, and I really doubt that grub is there.

Thanks again,
Brad

---

### Post by Moop on 2009-08-24
If you installed XP and grub still comes up, then you're booting from the wrong hard drive. 

XP will overwrite grub.

---

### Post by brad1138 on 2009-08-24
> **Moop said:**
> If you installed XP and grub still comes up, then you're booting from the wrong hard drive. 

XP will overwrite grub.

Thats the problem, I can't install XP. XP copies all the setup files from the cd to the HD, then restarts the comp to install all the software properly, but when it restarts it runs into grub and when I select XP (which is there from before) it crashes.

I unplugged my SATA drive and grub didn't come up. Then I plugged it back in and grub still didn't come up. XP wouldn't load because of some missing file but at least grub didn't come up. 

It doesn't make sense why grub would be on my SATA drive, I don't want it there, it is just a storage drive that I may want to swap later and that would crash the whole system. It also doesn't make sense why grub didn't come back when I plugged the SATA drive back in. My only guess is that it was on the SATA drive but when I disconnected it, the computer stopped looking for it there which is why it didn't look for it there when I plugged the SATA drive back in, sound plausible anyway.

I feel like I need to wipe every drive. This is the kind of problem that may make me leave Linux after 3+ years of having Ubuntu installed. I wouldn't be dealing with this crap if I just ran XP.

Don't get me wrong I LOVE Ubuntu but this is getting really frustrating. Grub seems to be so secretive, no one really knows much about it but you have to use it to dual boot.

Brad

---

### Post by brad1138 on 2009-08-24
That seams to have fixed it (unplugging and plugging back in of the SATA drive) not sure why (which bugs me also) but grub is gone and XP is now mostly installed on my other pc. I probably will need to reinstall Ubuntu but I wanted to try the 64 bit version anyway so no big deal. As long as grub doesn't some how "re-appear" before I want it, I'll be OK.

Thanks,
Brad

---

