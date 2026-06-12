---
title: "Hard Disk Write Spikes"
date: 2009-06-06
forum: Hardware
---

### Post by impactdni on 2009-06-06
Been working on this for a few days, and can't seem to figure out why its happening... When doing any normal activity, and also in bonnie++, I get giant write-spikes (watching gkrellm)...  It will show my writes by seconds, going: 0, 20mb, 40mb, 60mb, 60mb, 300-400mb, 0, 0, repeat.

A screenshot is attached showing bonnie++ "Intelligent Write" section, and then "Intelligent Read" (graph vertical notches are 100mb)...

The hardware is running 2x1500gb Seagate drives (with the known good CC1H firmware), in a software RAID-1.

hdparm results look fine:
/dev/sda:
 Timing cached reads:   7986 MB in  2.00 seconds = 3996.63 MB/sec
 Timing buffered disk reads:  370 MB in  3.02 seconds = 122.65 MB/sec
/dev/sdb:
 Timing cached reads:   7484 MB in  2.00 seconds = 3744.96 MB/sec
 Timing buffered disk reads:  344 MB in  3.01 seconds = 114.17 MB/sec
/dev/md2:
 Timing cached reads:   7150 MB in  2.00 seconds = 3577.39 MB/sec
 Timing buffered disk reads:  370 MB in  3.00 seconds = 123.27 MB/sec


dd if=/dev/zero of=testfile bs=10M count=1500
gives a different spike-pattern on gkrellm (with an even bigger pause between writes)..

During both dd and bonnie tests, only that test, gkrellm, and gnome were running, and moving the mouse during the test was choppy/laggy (very odd).  The problem is easily reproducable (unzipping large files causes mouse/keyboard lag, as well as the same patterns on gkrellm).

Anyone have any idea where to start looking?

---

### Post by impactdni on 2009-06-21
Still having trouble with this one, anyone have any ideas?

---

