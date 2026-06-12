---
title: "Keyboard LED not working"
date: 2011-09-24
forum: Hardware
---

### Post by squeeish on 2011-09-24
Hi all,

I recently took the plunge and installed Ubuntu 11.04 again on my PC, dual booting with Windows 7. Loving it so far! All of the hardware works well, including my dual monitor setup. However, I've hit this little snag.

I can't get the Caps Lock LED on my keyboard (Ducky DK9008) to work. Scroll lock as well as its LED doesn't work too, but that's ok because Scroll lock doesn't work on Linux in general right?

Num Lock LED works fine, it toggles on and off when I press it. However the Caps Lock LED doesn't toggle on and off, although caps lock is enabled/disabled.

I know there's the app to indicate on the dock whether caps lock is on or off, but I'd just love it if the LED on my keyboard works too.

Any ideas?

---

### Post by livemott on 2011-09-24
Well, check USB connecting line, may be LED is broken, or power is not engough

---

### Post by squeeish on 2011-09-24
It works fine when I log in back to Windows 7.

---

### Post by Precariat on 2011-12-17
I just picked up a Ducky DK9008 mechanical keyboard and installed Ubuntu 11.10, and just noticed a few moments ago that the only working LED seems to be the NUM-Lock.

---

### Post by Shdwdrgn on 2012-04-05
Bumping this thread, hoping for a solution.  My capslock indicator works fine from grub, and through the initial kernel load.  The system hangs for a couple seconds displaying "Begin running scripts init/Bottom", and it is during this period that the capslock and scrolllock indicators stop working.

I have four desktop PCs with various hardware, using basic US 105-key ps/2 keyboards - all showing the same symptoms.

I have a fifth desktop machine, also using a ps/2 US keyboard, on which none of the three indicators work.

In all cases, pressing capslock or numlock does change the output of the keyboard.  The keys are functioning, it is just the indicator LEDs that no longer work.  This issue appeared after upgrading from Maverick to Natty (the indicators were working correctly before upgrading).

---

### Post by Shdwdrgn on 2012-06-01
Interesting trend of spam we have going in this thread...

Just thought I would update to say that I upgraded my systems to 11.10 this week (now with the 3.0 kernel) and my caps-lock LED still does not function after the initial boot sequence.  The LEDs work fine within CMOS and from grub, but go dark during the boot-up procedure.

---

### Post by arthurdent22 on 2012-06-18
For what it's worth you can turn the leds on or off with a command or script, for example.

Turn on scroll lock led
xset led named "Scroll Lock";

Turn off scroll lock led
xset -led named "Scroll Lock"

Other leds can also be controlled, see xset man page.

---

