---
title: "HP Deskjet 3050 j610 - not printing"
date: 2011-01-11
forum: Hardware
---

### Post by m477r33d on 2011-01-11
I am trying to use an HP Deskjet 3050 j610 with Ubuntu 10.04 (Netbook remix) on an Acer AspireOne. I am using HPLIP 3.10.9, which detected and installed the printer via USB with no difficulty. 

When I try to print a job, I get a "HPLIP Device Status" message with an exclamation mark, stating "Started a print job". The job then queues normally. After a moment, I get another "HPLIP Device Status" message stating "print job has completed" and the job is removed from the queue. However, **the printer does not actually print**. 

I have been able to use other printers successfully in Ubuntu on this computer, including Canon and HP. Also, I am dual booting with Windows 7, where I am able to print with the current printer in question.

If you have any ideas, or would like any additional info, please reply! Thank you!

---

### Post by m477r33d on 2011-01-11
Got it - Just had to direct it to the correct PPD file (during setup):

[B]/usr/share/hplip[version]/ppd/hpijs/hp-deskjet_3050_j610_series-hpijs.ppd
[/B](after gunzip)

the default (incorrect) PPD file directory was:
**/usr/share/ppd/hplip/HP/**
...where there was no file for the 3050.

---

### Post by acraens on 2011-02-13
how did you get the HPLIP files installed.
I can't get it installed

---

### Post by imwithid on 2012-03-14
> **m477r33d said:**
> Got it - Just had to direct it to the correct PPD file (during setup):

[B]/usr/share/hplip[version]/ppd/hpijs/hp-deskjet_3050_j610_series-hpijs.ppd
[/B](after gunzip)

the default (incorrect) PPD file directory was:
**/usr/share/ppd/hplip/HP/**
...where there was no file for the 3050.

There is no such file. The closest it comes to is a 3500 or 3550 for the HP Deskjet models, unless you had mistaken "laserjet" for "deskjet". It's been a nightmare setting up this damn printer in the office. It works fine with Windows (except XP X64 edition) over the network but some computers use Ubuntu. I couldn't even sent a comment on the HP support page (when I went to submit it, it stated that I had entered the wrong URL).

When did you go wrong HP? I know that this is a cheapo printer but it's a backup to the ImageRunner 330, which is down. Way to disappoint, HP! It's rather ironic that I'm using an HP DV4-1225dx laptop that can't print to an HP printer.

---

