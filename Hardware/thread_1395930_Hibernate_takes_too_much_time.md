---
title: "Hibernate takes too much time"
date: 2010-02-01
forum: Hardware
---

### Post by cmavr8 on 2010-02-01
[EDIT: This has been solved! See post #5 for solution]

Hi, I have an i7-920 machine with 3 GB of RAM and a slow WD Green 320GB drive.

My swap partition is 3 GB.

**The computer Hibernates in 60" but it takes more than 3 minutes to resume.**

Suspend (to ram) works fine (7" to sleep, 15" to wakeup).

The detailed description of a wakening goes like this:
0" - I press the power button
18" - grub has done its selection, start of Ubuntu 9.10 (64bit) boot. HD led goes fully ON
49" - HD led still brightly lit all the time. All of the screen is covered with artifacts

1'14" - Blank screen (not black, BLANK)
1'35" - black screen with cursor (underscore) blinkin on top left
1'44" - Blank screen 
1'50" - some artifacts on black screen
_____ - Blank screen 
1'58" - some artifacts on black screen

2'30" - mouse cursor along with artifacts - cursor not responding
2'55" - cursor slowly moving when I move mouse
3'10" - screen cleans up from artifacts but cursor still slow
3'20" - clean screen, responsive cursor, HD activity slows down, lock scren shown - Everything ok.


[B]What should I log and provide to help anyone help me?
[/B]
Thanks
[EDIT: This has been solved! See post #5 for solution]

---

### Post by t4thfavor on 2010-02-01
This probably has to do with the fact that you have to read 3GB or data off your disk in order to resume. Im not sure, but it's probably faster to dump out the ram to swap, anyone else have any ideas?

bump :)

---

### Post by cmavr8 on 2010-02-01
Hi, thanks for the reply.

Swap is already the place used for hibernation and it's located in the HD.
Also:
1. Windows does the same thing (saving 3gb to HD, then restoring it) and needs less than a minute.

2. It takes 1 min to write data and 3 mins to read it? doesn't make sense... it's just a bug.

---

### Post by cmavr8 on 2010-02-12
bump...

I noticed something strange that happens the very moment I resume from hibernation. See attached pic please.

---

### Post by cmavr8 on 2010-03-02
Finally figured it out!
It was the "legacy IDE" sata setting in BIOS!

I changed it to AHCI and it now hibernates in 25" and resumes in 55"!

---

