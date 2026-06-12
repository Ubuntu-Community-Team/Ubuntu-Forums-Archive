---
title: "Jaunty kernel panic (flashing caps lock) - anyone else get this?"
date: 2009-06-13
forum: Hardware
---

### Post by ishii255 on 2009-06-13
hi all:

I'm running Jaunty on a Lenovo r61 thinkpad and I have to deal with my machine freezing in a kernel panic - usually when I leave it on overnight to torrent. So this only happens after I've left it on for 12+ hours.

I had the same problem when I had Intrepid on my lappy, and I read a previous thread that prescribed installing an intrepid backports package to fix a problem with my intel wireless card, and this worked fine then. So with Jaunty, I figured the same quickfix would work, but I installed the Jaunty backports package, and I still have kernel panics.

This is package I installed to no avail:

*linux-backports-modules-jaunty *

and this is the [thread]("http://ubuntuforums.org/showthread.php?t=968792") that used to work for me.

Anyone else have a lenovo? Anyone know how to fix it?

Thanks in advance.

---

### Post by chekhovs1 on 2009-09-26
Dear [ishii255]("http://ubuntuforums.org/member.php?u=213438"), were you able to find a solution?  I seem to be having a similar problem.  Thanks!  Sasha

---

### Post by thaislump on 2009-10-15
I have a Lenovo ThinkPad T500, running Jaunty x86_64, and it has been the crashiest Linux machine I've ever owned. Happens at least once a day. Same problem: freezes, unresponsive, flashing caps lock LED. There's no trace of what went wrong -- I suppose I need to enable core dumps ...

---

### Post by kwesadilo on 2009-10-24
I'm running Jaunty 64-bit on a Thinkpad T61p. I too get fairly frequent kernel panics. Almost every time, it is when I am watching videos full-screen on Hulu (using native Flash 10 alpha). This occurs in both Firefox and Chrome. Perhaps three times, it has crashed when I was playing Half-Life 2 or Portal full-screen using Wine. Once, it crashed when I was just browsing (can't remember the nature of the website or which browser I was using). Once, it crashed overnight while I wasn't looking, so I don't know what it was doing at the time. The only reason that I am still able to use this as my main computer for school is that it never crashes except when I am goofing off.

Do any of you know some useful diagnostic procedures for debugging kernel panics? /var/log/messages doesn't record anything abnormal, and I can't query the system after a panic has started.

---

### Post by jamesobooth on 2009-11-06
I have a Z60t and am experiencing this as well.

Sometimes the caps lock flashes and the system locks, sometimes it locks without the caps lock flashing.

I'm pretty new to Linux and don't know how to get to logs and whatnot in order to figure out what's going on.

I'm going to keep digging the web and if I find anything, I'll report it here.  If anyone else catches wind of something, please let us know.

---

### Post by ishii255 on 2009-11-06
Here's the thing guys: I was able to fix this problem in Intrepid using the Backports, I could never figure it out in Jaunty, but in Karmic I haven't had a single hiccup. period. except with gnome do, but that's for another thread. So the best thing I can say is upgrade to Karmic (fresh install) and cross them fingers 'n toes.

good luck

---

### Post by jamesobooth on 2009-11-06
Solved mine.  I was testing different drivers with my Intel chipset

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I just rolled them back to the default and the system is running smoothly now.  You might try tweaking them and see how your system responds.

---

