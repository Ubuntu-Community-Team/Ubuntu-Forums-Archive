---
title: "Resolution problem"
date: 2010-06-09
forum: Hardware
---

### Post by Nicolice on 2010-06-09
I just finished installing ubuntu 10.04 on my desktop, but I'm quite frustrated on configuring one of the basic setting - resolution problem...

I have nvidia 9800GT with all latest driver installed [drivers enabled] and my monitor is BenQ FP71G+ and the resolution is locked on 1024x768 with "unknown monitor" status.

I've followed everything as this thread, as I experiences the same problem as this guy
[http://ubuntuforums.org/showthread.php?t=1119018](http://ubuntuforums.org/showthread.php?t=1119018)

It's really annoying when changes everything, still recognized as "unknown monitor". I've even tried xrandr, everything... NOT WORKING.

Seriously, this is becoming so annoying already...

Any helps :(?

---

### Post by Nicolice on 2010-06-09
Sorry for the double post, but I found out that...

When I'm not using nvidia driver, which I used sudo apt-get purge nvidia*, and reconfigure my xorg back, I can get highest resolution setting and my monitor is detected.

But when I installed back the nvidia drivers via System-Administration->Hardware Drivers, and restart...I'll get lowest resolution that is 800x600, or even lower...and my monitor will detected as "unknown monitor".

Anyway to solve this? Or should I not use nvidia drivers at all at the moment?

---

### Post by Nicolice on 2010-06-09
Double post again.. but I solved it, like here
- [http://www.linuxquestions.org/questions/linux-desktop-74/resolution-problem-813078/#post3997950](http://www.linuxquestions.org/questions/linux-desktop-74/resolution-problem-813078/#post3997950)

Hopefully it does help others as well.

---

