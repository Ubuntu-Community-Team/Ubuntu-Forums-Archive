---
title: "Unpredictable freezes on ThinkPad E431"
date: 2014-04-20
forum: Hardware
---

### Post by dewdrop_world on 2014-04-20
Hi,

I've been looking around for information about random freezes. None of these threads quite describes the situation I'm having, so...

I had been running 12.04* on an MSI A6200, until it went belly up the other week after 3.5 years of reliable, daily use. Over the weekend, I got a new ThinkPad E431.

```
* Linux dlm-A6200 3.2.0-60-lowlatency #62-Ubuntu SMP PREEMPT Tue Feb 25 00:11:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

^^ lowlatency because I do a lot of real-time audio work in SuperCollider.

Currently I'm running the Ubuntu installation from the A6200, because it has all the software I need and I have work to do. (It would take me a few days to get a new installation up to where I want it to be, and I can't drop all my other tasks for that. I'll set up the new environment bit by bit as I can.) The old hard disk is fine, so I took it out of the old laptop, put it in a USB enclosure, and I'm booting from that. This is working almost perfectly, except for occasional, but daily, freezing -- everything locks up -- the display freezes, mouse and keyboard are unresponsive. I couldn't even get REISUB to do anything (though I might not have been able to hit the right key combination).

I did have to install bcmwl-kernel-source for the WiFi card. (The old machine used the ath9k module.)

The possible causes I'm aware of:


[LIST]
[*]Video driver. Unlikely, as both machines are using Intel integrated graphics. 
[*]WiFi driver. Possible but unlikely. 
[*]Some other driver. Possible but I have no idea how to check. 
[*]Thermal management, possibly related to WiFi, possibly not. [1] I can't rule it out at this point. One interesting factoid is that, if the system is going to freeze, it tends to freeze within the first hour of use after the machine has been idle. Then it seems stable after that... "seems" since I don't really have enough data points right now to say for sure. 
[*]Bad memory chip. I haven't run memtest yet (will do so at lunchtime), but this seems unlikely as well. 
[*]Faulty connection to the USB disk. Also seems unlikely. 
[*]I experienced the freezes with multiple apps -- no pattern wrt any action on my part. 
[/LIST]

I think I'm going to try the thermal.off trick from [1], just as a test, and revert it if it doesn't make a difference. Also check the memory at lunchtime.

Just wondering if anyone here has some gut feelings about these symptoms... thanks in advance,

hjh

[1] [https://bbs.archlinux.org/viewtopic.php?pid=1117097#p1117097](https://bbs.archlinux.org/viewtopic.php?pid=1117097#p1117097)

---

### Post by tgalati4 on 2014-04-21
Make a Live USB and boot Ubuntu off of it and see if it runs any longer.  That may rule out the old disk.  How did your previous laptop die?  A bad hard disk controller can cause similar symptoms.  Did you experience similar, random freeze behaviors with your previous laptop?

---

### Post by dewdrop_world on 2014-04-21
> **tgalati4 said:**
> Make a Live USB and boot Ubuntu off of it and see if it runs any longer.  That may rule out the old disk. A bad hard disk controller can cause similar symptoms.

Soon I'll start configuring the new HD. That should tell me something.

> **tgalati4 said:**
> How did your previous laptop die?  Did you experience similar, random freeze behaviors with your previous laptop?

Power problem -- probably a short in the AC adapter or battery fried the firmware. Hit the power button, nothing happens. Two days before a short concert performance, too :mad:

I never had any freezes with that machine.

Also, further update: thermal.off=1 made no difference, and memtest86+ passed with no errors.

hjh

---

### Post by dewdrop_world on 2014-04-24
> **dewdrop_world said:**
> Soon I'll start configuring the new HD. That should tell me something.

Update (and solved) -- I've got the new laptop's internal HD up to where I need it to be -- Ubuntu + Windows dual boot and the main software tools I use daily -- and the freezes seem to have disappeared. So it must be an issue with the USB enclosure.

Thanks for the advice --
hjh

---

