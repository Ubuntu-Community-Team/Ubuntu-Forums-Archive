---
title: "GlakkeClock - ATI GPU Utility - Bug test"
date: 2010-10-24
forum: Hardware
---

### Post by Glaucous on 2010-10-24
Hello.

I'm developing a ATI/AMD GPU utility for (mainly) Linux, it's still in Alpha and I'd appreciate it if people could help me and try it out. Right now it is command line only, but I will soon feature a Qt GUI (sorry GTK).

The program requires ATI proprietary drivers, at least version 9.3. The fglrx drivers from Ubuntu repositories are fine (they are at 10.10). 

Command line arguments from "--help".
[http://pastebin.ubuntu.com/519251/](http://pastebin.ubuntu.com/519251/)

Example output of "--get-info"
[http://pastebin.ubuntu.com/519253/](http://pastebin.ubuntu.com/519253/)

If you're afraid of touching overclocking on your card, no worries, all the "--get" arguments are completely safe.

And here is download link:
[https://sourceforge.net/projects/glakkeclock/files/](https://sourceforge.net/projects/glakkeclock/files/)

Now both x86 and x86_64 are available!

Things I can't test myself:
- If crossfire/multiple graphic cards are detected properly.
- If 32 bit work.

Need input on:
- Everything.
- If program always can find the libatiadlxx.so (/usr/lib32/fglrx, /usr/lib/fglrx).
- If performance levels are working properly (--get-info-levels)

Any input is appreciated.

**All download links are down because of licensing problems.**

---

