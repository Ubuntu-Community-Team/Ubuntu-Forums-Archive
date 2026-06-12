---
title: "Screen remains off after resume from lid-closure suspend on HP Mini 110"
date: 2010-03-13
forum: Hardware
---

### Post by torquill on 2010-03-13
Hi, all -- I have an HP Mini 110-1134CL running UNR 9.10 with all updates.  I neglected to tell it not to suspend when the lid is closed, and I found that when I open it again, the screen remains off (no backlight) even when the machine has resumed.  If I suspend by Fn-F1 without closing the lid, when it comes back the screen works fine.

When the screen is black, I can SSH in easily, and the logs show nothing unusual that I can see during suspend or resume.  I can attach an external monitor and switch to it via Fn-F2; I get an oddly-scaled desktop (it seems so huge everything is off-screen), Alt-Tab shows me what windows are open but does not move them into view.  Hitting Fn-F2 repeatedly toggles the external monitor on and off but does not awaken the native display.  Keyboard and mouse respond properly.

I have tried unloading and reloading the whole set of video driver modules (i915 drm video i2c_algo_bit output intel_agp agpgart).  It complained that i915 was in use, but there were no other errors; rmmod-f succeeded, and they reloaded without error, but still no display.  I tried 'sudo vbetool dpms on', it executed without comment, but it didn't work either.

A reboot fixes the problem (of course), or hitting Fn-F1 will bring the screen back after a second sleep/resume cycle.  That keeps me from losing work, and I can tell it never to suspend when the lid closes, but it should be possible to track this down.  I suspect an ACPI event handler issue, but I can't tell - perhaps the signal that the lid has been opened is lacking?  There's nothing in the logs.

I'm attaching the output of lspci, lsmod, and /var/log/syslog during suspend/resume, both a failed one and a successful one.  Thank you.

---

### Post by LinerJoe on 2010-03-20
Have you found any fixes?  I just picked up a HP Mini 110 for my wife and installed 9.10 NR on it.  I really like the interface, but sleep not functioning correctly is a deal breaker.

If I can't get the display working properly, I will have to leave it on win7, which isn't my preference (or hers).

Thanks!

joe

EDIT - Apparently changing the backlight level triggers the screen to come back on.  I can probably get her to work around that issue.  If I can a way to do that automatically, it would certainly be better.

---

### Post by torquill on 2010-03-21
Interesting.  I'll try the backlight change, see if it works on mine.

My workarounds have been:

1) If the display is black because of a lid closure suspend, hit Fn-F1 and then the power button to quickly run it through another suspend cycle (changing the backlight brightness would be even faster here), and 

2) Turn off the "suspend when lid closes" setting and instead suspend the machine with Fn-F1, then close the lid; that works fine.  As I'd like to be able to close the lid briefly and keep it running anyway, it's not a bad solution for me.  It's certainly easier for an end user than leaving it buggy and remembering to tweak the settings to bring it back.

---

### Post by torquill on 2010-03-21
Confirmed: changing screen brightness by adjusting the backlight (Fn-F3/F4) revives the display on my machine.  Thanks for noticing that.  :)

Additional complication: if the machine suspends on idle while the lid is closed, the black screen occurs on resume.  It is not necessary for the suspend event to be triggered by lid closure.

---

### Post by adam35413 on 2010-04-06
I too have experienced this issue.  Has there been any resolution?

---

### Post by djuke04 on 2010-04-25
Using an older HP dv9000, I am having the same issues.  After any sort of resume, regardless of how the suspend was triggered, the backlight and screen just won't turn back on.  

Changing the screen brightness does NOT affect this for my dv9000.  Fn + F5 (different on dv9000 I guess) to force another cycle doesn't work either.  It in fact doesn't even make it suspend.  

With my limited knowledge of Linux, I haven't been able to find any workarounds or solutions whatsoever.  

Any ideas would be much appreciated! Thanks in advance!

---

### Post by ccw127 on 2010-04-27
I just purchased a used mini110-1025dx. It had XP which I wiped and reinstalled using my own copy(for security). Found the same exact problem; only messing with the brightness, or using the sleep button wouldn't help. 

Upon updating to SP3 it worked fine. Just installed 10.04rc Netbook, and it is doing the same thing. At least the above comments about brightness (alt-f4) work. 

While using Backtrack4, I noticed opening the lid sends a key stroke combo, so I am wondering if it has something to do with a non standard notification to the OS as to the waking of the computer.

Chris

---

### Post by ChesterBr on 2010-06-16
Hi. I'm using Ubuntu 10.4, installed from scratch on an HP Mini 110 (the 1115CA variant) and have this very same issue: when I re-open the lid, the computer comes back from sleep, but does not turn on the backlight unless I hit fn+f3 or fn+f4 - which is sometimes hard to do when I open it in the dark.

Does anyone have any tips about this?

---

