---
title: "Periodic freezes on Media player box"
date: 2015-04-14
forum: Hardware
---

### Post by morganpatrick on 2015-04-14
Hi, I'm running Kodi on an ubuntu box that I only use as an entertainment system. It periodically freezes and nothing will unfreeze it: ctrl+alt+delete, ctrl+alt+backspace, sysreg+r,e,i,s,u,b, ctrl+alt+f1, nothing. The only thing I can do is hold in the power button to force it off.

I have run memtest and everything comes out fine. I have even run it for 12 hours straight. Luckily, there have been a couple times recently when the machine froze but I got some output on the screen, to I took [three photos]("https://imgur.com/emtiQ1g,aKo9XKj,AcvTCs6#0").

Also, one time it froze but ssh still worked (it normally doesn't) so I got the output of [Xorg.0.log]("http://pastebin.com/1JTYkxEr") and [dmesg]("http://pastebin.com/idEqWmyT"). 

Could someone help me sort out what's going wrong here? Thanks so much.

---

### Post by weatherman2 on 2015-04-14
The usual things to try:
- run Memtest (you've done that)
- check the hard drive health (GSmartControl).  Look for Attributes flagged in pink on the Attributes tab
- overheating?  check the CPU and chipset temperatures

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Make sure the fans are working inside and that the heat sink(s) aren't clogged and dirty; if so, clean them out.

If you want to stress test your CPU, open a terminal and type this (same thing twice)

```

cat /dev/zero | gzip -c > /dev/null &
cat /dev/zero | gzip -c > /dev/null &

```

This should max out both CPUs.  If you have an overheating problem, this will soon show it.  (Memtest doesn't necessarily tax the CPU much.)

(To end those two jobs, type "killall gzip" .)

Otherwise, you may have some other hardware issues: failing motherboard (look on the motherboard for blown caps; do a web search for "blown caps motherboard" for more info) or a failing power supply.


Or it could be a software issue.

---

