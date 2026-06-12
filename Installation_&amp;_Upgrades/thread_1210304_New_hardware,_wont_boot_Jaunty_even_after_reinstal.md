---
title: "New hardware, wont boot Jaunty even after reinstall"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by axeman71 on 2009-07-11
I have been running Ubuntu Studio 9.04 with WinXP dual boot for a few months now with no problems.   I bought a new motherboard (Gigabyte MA770T-ud3p), AMD PhenomII X2 (I unlocked the other two cores making it an X4), ATI HD-4850 video card, 4 Gb ram and a SATA HDD to replace an older EIDE HDD.

After the new hardware install WinXP still runs fine but Ubuntu wouldn't boot.  No surprise there with all the hardware changes.  I don't know how to update Linux for new hardware so I just did a fresh install after formatting my Linux partitions (I have root, home and swap partitions).  The install seemed to run just fine but I still can't run Ubuntu.  After selecting it in grub the screen fills with a bunch of technical info for about 1 second then everything freezes up.  I wiped everything again and reinstalled again and am still having the same trouble.

What should I try?  Are there some driver issues with my new hardware I don't know about?  I can write down some of the info on the screen during the crash if needed, though none of it looks like error warnings to my untrained eye.

---

### Post by Sef on 2009-07-11
If you run the Live CD, do you have any problems?

---

### Post by axeman71 on 2009-07-11
I haven't tried and I'm not sure what I need to do.  I rebooted using my DVD but I didn't see an option to run Ubuntu from the DVD just some install options.  I went to the Ubuntu download page but didn't see a Live CD/DVD download option.

---

### Post by merlinus on 2009-07-11
Many problems with 9.04 and older ATI cards, which are no longer supported.

I believe Sef was referring to the ubuntu live install cd, which you can get from ubuntu.com's download page.

---

### Post by axeman71 on 2009-07-11
My older video card is the main reason for all the upgrades.  The HD-4850 is one of ATI's newest line of cards so I hope it is compatible.

I tried the standard Ubuntu CD (apparently Ubuntu Studio doesn't have a live CD version) and it worked just fine running off the CD so I guess it is not a driver issue.

After thinking about it I bet it is a boot loader issue.  I hate boot loaders they never work like I expect.  Anyway... in my old system the Seagate hdd was hd0 and had both WinXP and the /root Ubuntu partitions on it.  The Maxtor HDD was hd1 and had the linux swap file and some other partitions on it.  With the new hardware the Maxtor hdd was replaced by the SATA hdd.  This bios lists SATA drives before EIDE drives so I think the SATA is now hd0 (or maybe sda??? I get confused as it seems to be called one thing in one place and something else in another) and the Seagate with the two OS's is now hd1.

I tried to "rescue" the install using my Ubuntu Studio DVD and using the grub installer I tried to force it to write grub to hd1 to overwrite the old grub.  It didn't work.  How can I solve the boot loader problem?

---

### Post by axeman71 on 2009-07-11
Ok maybe it is not Grub.  I've been reading how-to's for the last hour and trying different things with grub and I still have the same problem.  Besides, it still boots WinXP just fine, if grub were pointing at the wrong drive XP wouldn't work either.

So I wrote down the last 2 lines of the error message I get when trying to start Ubuntu, maybe it will give someone a clue about what is going wrong:

[  0.459000] EIP:[<c015d141] tick_periodic+0x11/0x70 SS:ESP 0068:f6079f28
[  0.459000] ---[end trace 4eaa2a86a8e2da22]---

---

### Post by merlinus on 2009-07-11
Can you boot into recovery mode from the grub menu?

Another thing to try is superdisk.

---

### Post by axeman71 on 2009-07-11
When I try to boot in recovery mode I get the same error screen as trying to boot regular mode.  I'll check out superdisk.

---

### Post by merlinus on 2009-07-11
supergrub....  my bad.

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by axeman71 on 2009-07-11
I don't think its grub.  I've tried everything on the superGrubdisk and it won't boot Unbutu.  It won't boot from within suberGrubDisk, it won't boot no matter which disk I write grub too.  I even erased grub and put the windows boot loader back on, nuked all the linux partitions, then went back with a full Ubuntu Studio 9.04 install and I get the same error.  What could it be other than the boot loader?

---

