---
title: "Canon MP600 not working after Lucid upgrade"
date: 2010-09-24
forum: Hardware
---

### Post by woodmaster on 2010-09-24
I really can't remember how, but I got the canon mp600 working by trial and error and reading a lot of proposed "solutions" in 9.10.  I have done a fresh install of 10.04.1 and now when I try to install the linux driver from Canon(aliened from rpm), I get:

> Printer 'Canon-MP600' requires the 'pstocanonij' program but it is not currently installed.  Please install it before using this printer.Any idea what that program is?

---

### Post by woodmaster on 2010-09-25
bump?

---

### Post by woodmaster on 2010-09-27
bump...anyone?

---

### Post by woodmaster on 2010-09-27
Found the pstocanonij file by installing the second package from here that I missed b4
[http://support-in.canon-asia.com/P/search?model=PIXMA+MP600&menu=download&filter=0&tagname=g_os&g_os=Linux]("http://http://support-in.canon-asia.com/P/search?model=PIXMA+MP600&menu=download&filter=0&tagname=g_os&g_os=Linux")
But, I still can't print...tried /etc/init.d/cups restart after reinstalling printer and still no luck...I'm grasping straws now.  No idea what could be wrong...

---

### Post by woodmaster on 2010-09-28
bump

---

### Post by woodmaster on 2010-09-30
bump...anyone?  Did everyone just give up on this printer.  My wife is going freaking insane!

---

### Post by woodmaster on 2010-10-06
should I bother bumping anymore?

---

### Post by Xero Xenith on 2010-10-07
> **woodmaster said:**
> should I bother bumping anymore?

You could try some parts of this guide for the MP600R - 

[http://ubuntuforums.org/showthread.php?t=1095406](http://ubuntuforums.org/showthread.php?t=1095406)

Note that a lot of it is trying to get it working on the network. (The key may just be to use the Canon MP500 driver.)

This also seems to have some good info:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/496635](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/496635)

---

### Post by woodmaster on 2010-10-07
mp 500 driver doesn't print correctly.  There's really not anything in those links I haven't already tried...  Thanks anyhow.

---

### Post by kkruecke on 2010-12-18
I don't know what driver I installed, it's been so long ago. But I have had my MP600 working for at least two years. Through each upgrade to the latest version of Ubuntu -- now 10.100 -- the printer has continued to work.

---

### Post by nonovo on 2011-01-04
I was facing the same issues with MP600, managed to get it print using cocktail of drivers from Canon, but NOT with good quality results.
At the end I have invested a little money and bought printer driver from [http://www.turboprint.info/printers_Canon.html](http://www.turboprint.info/printers_Canon.html)
This solved all problems and works very well even after complete re-install/upgrade using 10.4 & 10.10.

---

