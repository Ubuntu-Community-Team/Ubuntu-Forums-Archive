---
title: "clock running &quot;slow&quot;"
date: 2008-11-12
forum: General Help
---

### Post by KoenEeckhoudt on 2008-11-12
Hey guys.

I've installed 8.10 after having had very much troubles with 8.04. Crashes due to wifi stuff. Anyways, everything is working VERY nice in 8.10, except for one small thingy... The clock of my pc has completely lost its mind.

If I let my pc idle for about 3 hours, it's already a time difference of about +/- 10 minutes, that it's going slower then the actual time.

Example:

```
koen@koen-desktop:~$ sudo ntpdate -u pool.ntp.org
12 Nov 18:40:42 ntpdate[8842]: step time server 79.99.122.30 offset 8.356309 sec
koen@koen-desktop:~$ sudo ntpdate -u pool.ntp.org
[sudo] password for koen: 
12 Nov 21:28:55 ntpdate[9046]: step time server 80.200.254.25 offset 489.574887 sec

```

What can I do to fix this problem? 

Thx, 
Koen (very very happy that I've left XP, but the clock is a bit a strange thingy to me... )

Oh btw: it's a dual core intel processor, 2 gigs of ram, OS running of a SATA disk, 64bit 8.10.

If you need further information, please let me know :)

Thx!

---

### Post by KoenEeckhoudt on 2008-11-12
Just to show you: between typing the above message and this one:

```

koen@koen-desktop:~$ sudo ntpdate -u pool.ntp.org
12 Nov 21:33:29 ntpdate[9058]: step time server 80.200.254.25 offset 13.260979 sec

```

---

### Post by KoenEeckhoudt on 2008-11-13
anybody please? :(

any help is appreciated... between booting and this post (uptime about 5 minutes) there's again 7 seconds difference... :(

---

### Post by KoenEeckhoudt on 2008-11-13
Problem found. The issue was that Dynamic Overclocking mode was enabled in my BIOS settings. Ubuntu didn't like that very much. Haven't had problems in XP with that setting, but then again, I was very eager to search for stuff that was wrong with this Ubuntu. The time has now come that I officially can't find a thing. 

A big thanks to Christophe for pointing me in the correct direction ;)

Regards,
Koen

---

