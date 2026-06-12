---
title: "Kernel Panic DURING forced disk check, won't boot."
date: 2008-10-11
forum: General Help
---

### Post by HousieMousie2 on 2008-10-11
I stepped away from my machine and when I came back the screensaver was frozen, nothing was responding (oddly it did NOT have two out of three keyboard lights flashing) and I was forced to hit the reset switch.

When Hardy rebooted I got to the log in screen, put in password and was given the following error:

```
Could not start Kstartup.config.
```

I clicked Okay and it took me to a terminal, I tried to reboot, but bad timing caught up with me, a forced disk check started.

Then the screen went crazy.  Instead of the usual white text on a black background, the whole screen filled up with gibberish in an array of flashing colors.  At the bottom of the screen I was able to make out that it was trying to display the words 'kernel panic.'  Nothing would respond at that point.

I tried booting into failsafe:

```
There was an error setting up inter-process communications for KDE.  The message returned by the system was:
Could not read network connection list.
//.DCOPserver_<my computer's name>_O
```

It then went on to say:

```
Will not save configuration.
Configuration file "//.kde/share/config/Konsolerc" not writeable.
Configuration file "//.kde/share/config/Kdeglobals" not writeable.
```

But would go no further.

I was in the process of trying to gather info about system lockups because it had done it a few other times, but had not had a full melt down like this, and would reboot without complaint.

Before the melt down:
I read that the swap might be a problem, I know I gave it plenty of space for swap (I don't recall the exact amount, but I believe it was more than twice my RAM, which is 4GB... I think I gave it 10 or 20GB.)  I had tried loading up my system with multiple instances of Firefox, Gimp, Open Office and any other program I thought might use a lot of RAM/Swap, then typed "free" in a Konsole but the Used number never changed from zero.  I followed directions to swap off/swap on, but no change... don't know if that is the problem.

When I installed the nVidia driver for my video card, it jacked with the kernel... don't know if that is the problem either.

Just a few minutes ago I read that SATA drives should use a special kernel... don't know if that is the problem either.

As it sits, I am using Live CD to write this, and do not know where to go from here.

ANY help would be GREATLY appreciated!

Thank you for reading this lengthy post.

---

### Post by Yannick Le Saint kyncani on 2008-10-11
Hi HousieMousie2,

You could open your hard drive from the live cd, this will make sure the filesystem is clean, then reboot into your standard ubuntu install.

If this does not work, you could fsck your ubuntu install from the livecd (howtos on the web).

Hope it helps :)

Regards.

---

### Post by HousieMousie2 on 2008-10-11
Yannick Le Saint kyncani, thank you for the suggestions, I have pulled up some pages to go over later (when my brain has more than two cells to rub together.. haven't slept yet.)

I need to power down though and disconnect the extra hard drives, since there is a known broken installation of Gutsy, that I don't want fsck to mess with... and rather than exclude it with fsck, I will remove all chance for computer (or more likely) human error.

I will post back, probably very late tonight or some time tomorrow.

Thank you again!

---

### Post by HousieMousie2 on 2008-10-12
> **Yannick Le Saint kyncani said:**
> Hi HousieMousie2,

You could open your hard drive from the live cd, this will make sure the filesystem is clean, then reboot into your standard ubuntu install.

If this does not work, you could fsck your ubuntu install from the livecd (howtos on the web).

Hope it helps :)

Regards.

Thanks again, Yannick Le Saint kyncani!

I did both with Live CD, to make sure that the fsck would go smoothly... I am now happily back in my Hardy install.  Of course, now I have the daunting task of trying to figure out what caused it (/var/log/<pick your favorite file> was of no use,) but that's a whole 'nother adventure.

Cheers!

---

### Post by Yannick Le Saint kyncani on 2008-10-12
> **HousieMousie2 said:**
> Of course, now I have the daunting task of trying to figure out what caused it

Hi HousieMousie2, glad it all worked out :)

There are (insert any number you want) things + 1 at least that can cause a filesystem corruption, in rough order :

1- Unclean shutdown (power failure, ...)
2- Hard drive failure
3- Some other hardware failure (ram, high temperature causing trouble)
4- Kernel bug or proprietary module bug

You should always cleanly shutdown, this will take care of (1). As for power failure, well we can't all have our own powerplant, right ?

You can't do much against (2), maybe check from time to time your smart counters (check smartctl on the web). The only thing you can do is have multiple backups and a restore plan (which you should, err must do, or prepare to suffer the consequences of total data loss, which you will have sooner rather than later).

You can check your ram with memtest86+, this will take care of ram-related point (3). I don't know much about high temperatures.

As for number (4), stay away from proprietary modules as much as possible.

Regards :)

---

### Post by HousieMousie2 on 2010-08-11
Wow, I could have sworn I posted back on this.  Sheesh.

The kernel panic during fsck was caused by a racing condition between two separate hard drives.

I used e2label to label the various (major) partitions, eg. Root, Boot, Home, XP, etc.

fsck now uses the labels instead of the sda1/sdb1 type designators, which were changing randomly at start-up, causing fsck to try to scan the NTFS hard drive, and understandably, freak out.

I still do not know what was causing the machine to freeze (after a successful start-up) but that was not a related issue and not mentioned in the thread title.

---

