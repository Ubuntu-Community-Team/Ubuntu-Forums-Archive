---
title: "CD Installation Issues"
date: 2008-07-27
forum: General Help
---

### Post by DrTaylor on 2008-07-27
Hi, guys!

I *finally* talked my friends into switching to Ubuntu after Vista *%#^$@ them over, but since Vista... is Vista, it's not letting go without a fight. We burned the Hardy ISO to a DVD-ROM and turned the BIOS settings to "Boot from DVD ROM Drive". Didn't work. We copied the ISO into my flash drive and set it to "Boot from USB". Didn't work. Both times it just booted normally into Vista instead.

---

### Post by Ryadt on 2008-07-27
Can you be more specific about what happened when you tried to boot from the DVD ROM.

---

### Post by DrTaylor on 2008-07-27
Nothing happened. In the ultimate sense of that term. We burned the disc, put it in the drive, rebooted, got into the BIOS, switched to "Boot from DVD ROM", hit enter, saved and exited, the dvd drive whirred for a couple of seconds, and then... did nothing. The computer booted into Vista. 

We went back into the BIOS and switched all three boot devices to "boot from dvd rom". The computer booted into vista. 

I threatened it with death. It booted into Vista. We put the ISO on my flash drive and plugged that in and switched the bios to "boot from usb drive". It booted into vista. 

I screamed at it. It booted into vista. We put the disc in the other cd drive just in case we had the wrong one and switched the first option to "boot from DVD drive", the second to "boot from USB drive" and the third to "boot from CD drive". It booted into Vista.

---

### Post by Ryadt on 2008-07-27
Can you provide some specs of the desktop or laptop.

---

### Post by DrTaylor on 2008-07-27
Well, it's a desktop, has a relatively new DVD drive, slightly less new CD drive, the computer itself is about six years old but all the vital components have been replaced at some point. Motherboard's about a year old.

It lets me see the scores Windows gives all the components under "Performance Information":

Processor - 3.6 Calculations per second
Memory - 4.0 operations per second
Graphics - 1.0 something or other
Gaming Graphics - 1.0
Primary Hard Disk - Data transfer Rate 4.0

Now, the last time we downloaded, we thought Vista might not be completing the download - that we were missing some small bit of it (which sounds like a typically Vista kind of thing to do). So I'm wondering if maybe we should just get a CD somewhere else and see if that will load.

---

### Post by wpshooter on 2008-07-27
Just to make positively sure, you are **BURNING** the downloaded images as an ISO to the CD/DVD and not just copying it as DATA ?

Also, are you going to still be using VISTA on this machine ?  If not, why don't you just get rid of it and that "MAY" solve this problem.

---

### Post by Ryadt on 2008-07-27
Try to go in BIOS and see if you can see something like flash modules. If you can see it disable it and then switch from ahcpi to ata in ata drives.
Then retry booting from the cd.Hope this helps.

---

