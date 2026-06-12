---
title: "toshiba laptop scren goes blank, unresponsive"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by mjumbewu on 2007-11-26
Hi all,

I have a Toshiba Tecra M6 laptop with Gutsy (7.10) installed.  Every so often, at irregular intervals (usually a few hours) the screen will go black (but not turn off, i.e. the backlight is still on) and the cpu fan will start to run high.  What's more, it will not respond to any keyboard or mouse input -- no Ctrl+Alt+Del, no Ctrl+Alt+F1, no nothing.

A few things I've noticed: if I have video or music playing it will stop as well (though the last video frame will remain displayed on the screen -- using Xv and compix+fusion), whereas if the computer were simply idle, the media would keep going in the background.  I've also looked at the messages log file, and the computer continues to post "-- MARK --" messages.

Any ideas on how to fix or even debug this would be deeply appreciated.
Thank you,
- Mjumbe

---

### Post by mjumbewu on 2007-11-27
Hello again,

So one "solution" I've found is to disable frequency scaling in the BIOS.  This gives the computer no opportunity to get so hot.  However, this means that I'm stuck at my cpu's lowest frequency.  I'd really prefer if I could take advantage of all that my processor can offer.

Has anyone else had and gotten around frequency scaling issues in ubuntu?

Thanks,
- Mjumbe

---

### Post by mjumbewu on 2007-12-01
So it turns out this is not a frequency scaling problem as it still happens even after frequency scaling is disabled.  Anyone have ideas on how i could debug this?

---

### Post by manark on 2007-12-26
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=623951](http://ubuntuforums.org/showthread.php?t=623951) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I own a 2 month old Toshiba Satellite P200D with Vista Home Premium that has the same problem of going blank at irregular times; between 5 &24 hours of operation,  no matter what program you are using. I have turned of all the start up programs with no success, I also completed a system Recovery with no success.

---

