---
title: "Touchpad &amp; Brightness issue on Acer Aspire One 725"
date: 2012-09-28
forum: Hardware
---

### Post by omiazad on 2012-09-28
Just installed Ubuntu 12.04 on a friend's laptop, it's Acer Aspire One 725. Everything is fine except two issues.

The mouse touchpad and Brightness controller. The touchpad is not responding and I tried with Ubuntu 12.10 (Beta 2) Live, but no luck. But the touchpad is working fine on Kubuntu 12.04.

Also when I tried to change the brightness of the screen, it didn't work, but on the screen the level shows changing. 

I upgraded the BIOS thinking it may help. But it didn't. Do you know any solution for this?

---

### Post by cortman on 2012-09-28
I have the Acer Aspire One 722- have you tried running

```
synclient TouchPadOff=0
```

in a terminal to get the touchpad working?

---

### Post by omiazad on 2012-09-28
Pressing Fn+F7 shows the screen animation that the touchpad is turning on or off, but the physical hardware is not working. Will try that code tomorrow when I'll go to him.

---

### Post by cortman on 2012-09-28
[This post]("http://ubuntuforums.org/showpost.php?p=12209752&postcount=14") also seems to have been helpful.

---

### Post by omiazad on 2012-09-29
Followed that post. Did not have any ```
/etc/X11/xorg.conf
``` so created one. But did not help :(

---

### Post by milkacow on 2012-10-03
i had these same problems on an acer aspire 725-0899.  I noticed with the touchpad, if you hit Fn-F7 at the login screen before logging in, the touchpad works.

---

### Post by omiazad on 2012-10-04
> **milkacow said:**
> i had these same problems on an acer aspire 725-0899.  I noticed with the touchpad, if you hit Fn-F7 at the login screen before logging in, the touchpad works.


AWESOME
IT WORKED....

:guitar:

---

### Post by ivonnep on 2012-10-06
> **omiazad said:**
> AWESOME
IT WORKED....

:guitar:

yeah! it worked for me too!:p

But there must be a way to have it always on even if netbook restarts... I guess...

---

