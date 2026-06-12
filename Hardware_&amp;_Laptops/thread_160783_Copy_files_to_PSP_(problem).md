---
title: "Copy files to PSP (problem)"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by wizardStan on 2006-04-15
Here's what I know:
I plug in my PSP, it automounts, I can copy stuff off of it, no problem.
When I try to copy files back onto (237 MP3s, for example) it fails in a not so brilliant way.  In the case of my copying 237 MP3s, it got to 59, and stopped.  The copying dialog was still up, but it was no longer transfering.  The time remaining kept going up.  I eventually gave up, and hit cancel.  No surprise, no files had been copied.
I eventually figured out that I can copy one file of at most 5 megs, unmount my psp, wait for the light on it to indicate it's finished copying, unplug the USB cable and repeat, but doing that everytime I want to copy a file is not good.  And no chance of getting videos and the like onto it either.
Anyone else have problems like this?  Is there something I can change in the way it mounts my PSP to prevent the write cache?
Thanks.

---

### Post by 146lily on 2006-04-15
whats a psp...I have 15000mp3's on portable hdd?

---

### Post by wizardStan on 2006-04-15
PlayStation Portable.
My 250gig external USB HD doesn't seem to have any troubles copying files on or off it, thankfully.

edit: An update.  I've added the line
/dev/sdc1 /media/psp vfat noauto,defaults,user,sync,shortname=winnt,noexec,nosuid,nodev,quiet 0 0
(thought I've little idea what all of that means) to my fstab on advice from another thread I was reading, and now I get what seems to be a realtime copy (as opposed to cached writing) except it still dies while copying files.  I start the copy, the copy dialog comes up, it gets about halfway through, and the copy just halts.  The transfer led on the psp even goes out.
I'm starting to think it's a problem with my actual hardware, as it works fine on other systems I've tried, just not mine.

---

### Post by superdj1 on 2006-09-19
same thing with mmy sidekick

---

### Post by wizardStan on 2006-09-19
Woah, dude.  Really old thread.
In case you (or anyone else) are interested, I "solved" the problem by disabling USB2 support from my bios.  Forces my PSP to use USB1, which works flawlessly.  When finished, I restart and re-enable USB2 support.  I'm sure there's a software solution that would accomplish the same thing without the restart, but I'm far too lazy to try and find it.
Cheers.

---

