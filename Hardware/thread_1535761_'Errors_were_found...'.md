---
title: "'Errors were found...'"
date: 2010-07-21
forum: Hardware
---

### Post by oaxacamatt1 on 2010-07-21
Hi all,
Recently, I was having a little trouble with OOo.  So I decided to reboot, 'old windows habit'.  The bios comes up alright but then I get this message:
```
Errors were found while checking the disk drive for /
Press F to attempt to fix errors, I to ignore, S to skip mounting or M for manual recovery.
```
I pressed F and then this message comes up:
```
The disk drive /tmp is not ready yet or not present.
```
This has happened once before and I found that any prog that pointed to /tmp (for example, deluge) does not point there after this issue. I am worried that this is a hardware issue, any merit?  What logs should I check?
Any suggestions,
Matt

---

### Post by oaxacamatt1 on 2010-08-02
Hi All,
After talking to and emailing other Linux geeks I found out what the story on this is.  

This error is usually found when one shutdowns Ubuntu prematurely.  For example, I have a habit to powerdown by pressing the power button.  Another way this error will present itself is if your battery dies or in my case the battery is not connected securely and can cause a premature shutdown.

The way to fix this error is to do one of several things.  
1) The easiest way to fix this error is IF when you reboot your screen comes up AND asks you to either FIX the root drive or /tmp folder.  This takes about 2-5 minutes and should fix it all.

2) The above help/fix screen does not show up then the simplest way is to load up your trust Ubuntu Live CD and MAKE sure you UN-MOUNT your hd.  Then from GParted goto Partition/Check and let the fireworks fly.
HTH
M

---

