---
title: "Opinion on my hdparm.conf entry for cdrom."
date: 2005-11-16
forum: General Help
---

### Post by chaumurky on 2005-11-16
I am currently using the following line in my hdparm.conf for my LG GSA-4160B DVD writer (/dev/hdd). Can people comment on the validity of the switches I've used (especially the 'c' and 'm' switches)? Perhaps some aren't needed or others are. Thank you all in advance for your input, here's the line:

```
command_line {
hdparm -c1 -d1 -m16 -E40 /dev/hdd
}

```

---

### Post by chaumurky on 2005-11-16
I should say why I ask - when I burn cd's it slows down at 40% (during this period the cdrom spindle speed fluctuates and the HDD shows bursts of activity instead of continuous) but then at about 60% it speeds back up. Perhaps my burner is having issues? Anyway sudo hdparm -tT /dev/hdd gives:

[B]/dev/hdd:
 Timing cached reads:   1860 MB in  2.00 seconds = 927.82 MB/sec
 Timing buffered disk reads:    8 MB in  3.20 seconds =   2.50 MB/sec[/B]

---

### Post by chaumurky on 2005-12-12
Hmm, looks like the drive might have been dying anyway. It now won't read DVD's but CD's are fine. Perhaps 'unmaskirq' option may help with the burning issue. I now have a Pioneer 110D. Now using:

>  command_line {
hdparm -c1 -d1 -u1 /dev/hdd
} 

---

