---
title: "TSSTcorp TS-L632D: DVDs don't read or burn."
date: 2008-12-30
forum: Hardware
---

### Post by TheCelloFellow on 2008-12-30
I've got a Gateway MT3423 laptop with TS-L632D CD/DVD Burner. The optical drive has never been great shakes, rather noise and slow to rip CDs, glad I don't often. But the last few months, I think since I upgraded (using apt, not clean install) to Intrepid but I'm not suer, it has not worked with DVDs at all. They do not play, they cannot be ripped, put one in and type lsdvd and it simply says "No Media" after a few minutes of spinning the drive.

It still works for reading and writing CDs and does so acceptably, but commercial or burned video DVDs do not. I cannot burn DVDs either, it doesn't recognize blanks. I have a Data DVD burned on DVD5 media, somewhere, but haven't tried it. I also haven't tried to boot this machine into Vista to see if it works---I haven't booted Vista in months an would like to keep it that way, been thinking of wiping it.

Well, so my question is what is the matter with my drive, or how do I found out? and how do I fix it?

Here's output from lswh on the drive.

```
  *-cdrom
       description: DVD-RAM writer
       product: CD/DVDW TS-L632D
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: GA06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

---

### Post by JohnBris on 2008-12-30
I have the same problem with my Samsung TSSTcorp. I have dual boot with XP but no DVDs will burn there either. I can read data DVDs with it but it simply won't burn anything, not with Brasero or K3b.

CDs play fine.

In WinXP I have tried burning CDs, the strange thing is it will tell me that all went fine and I can see it actually burning on the screen - bummer. When I take out the CD it is completely empty and all other computers will recognise the CD-R as empty. In Ubuntu, K3b will simply tell me that burning at X speed is not supported.

I use a desktop which is pretty new which I built myself, and I can't remember if I have used the drive before I upgraded to Insipid. I'm getting pretty desperate and I suspect Ubuntu upgrade did something to it, but that is a wild guess with no solid ground. I use a mixed SATS and IDE system (optical drive as IDE, HD as SATA), wondering if that could be it?

Any thought are welcome!

---

### Post by dogscoff on 2009-07-11
I have the same problem under jaunty 64bit. Gnomebaker works where brasero fails, but I also have problems with playing back certain newer DVDs. I have also run into other people on IRC with similar problems.

---

