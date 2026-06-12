---
title: "Is Ubuntu crash-prone?"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by mikeklein on 2007-01-12
I've never had these issues with older RH releases...the things only crashed on me once or twice...but this was on server.

With Ubuntu (6.10) on laptop...I seem to crash like once daily.

Biggest crashes were when playing mpeg/etc. Using Automatix to finalize distro fixed those problems.

But still...if I make bad x config I am forced to reboot and do terminal login. Why can't X be nuked and I drop in to terminal automatically? X seems hung.

Also...I had lirc running for Myth and decided to yank usb ir dongle to switch into another port. System appeared to be completely hung and I had to reboot.

Is there some magic keystroke I'm missing to get past these hangs? I've tried ctrl-alt backspace...but this doesn't usually work.

Don't even get me talking about suspend/hibernate...crash city. Anybody get this to work right? I am using fairly modern Toshiba P25-S609 laptop.

---

### Post by jpeddicord on 2007-01-12
> **mikeklein said:**
> I've never had these issues with older RH releases...the things only crashed on me once or twice...but this was on server.

With Ubuntu (6.10) on laptop...I seem to crash like once daily.

Biggest crashes were when playing mpeg/etc. Using Automatix to finalize distro fixed those problems.

But still...if I make bad x config I am forced to reboot and do terminal login. Why can't X be nuked and I drop in to terminal automatically? X seems hung.

Also...I had lirc running for Myth and decided to yank usb ir dongle to switch into another port. System appeared to be completely hung and I had to reboot.

Is there some magic keystroke I'm missing to get past these hangs? I've tried ctrl-alt backspace...but this doesn't usually work.

Don't even get me talking about suspend/hibernate...crash city. Anybody get this to work right? I am using fairly modern Toshiba P25-S609 laptop.

For the X issue, you should be able to hit Ctrl+Alt+F1 to switch to a terminal login, as the screen with X on it doesn't do anything other than display the error.

As for IR, you should always shut off IR before you remove the dongle to prevent anything locking.

Suspend/hibernate seems to be a common problem on laptops. Check [http://bugs.launchpad.net](http://bugs.launchpad.net) for this issue and see if there are any workarounds.

I personally have never had any problems with crashes except for one time when I yanked out my USB key while it was still being written to. Oops. :rolleyes:

---

### Post by LiamRB on 2007-07-18
I have the same computer and suspend hangs in windows as well. I am not too worried about that. Want to get it up and running with Linux. Any advice?

---

