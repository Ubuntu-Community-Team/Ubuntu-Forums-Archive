---
title: "runs hotter with gutsy gibbon"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by karvec on 2007-10-18
I just installed Gutsy Gibbon on a new laptop (I was running feisty fawn for the first ~2 weeks, then got Gutsy) and now about a month later it seems it was running hotter than ever.  Fan kicks in all the time, etc., etc...  It's sitting on my desk about 2 cm off of it, and I figured that was plenty of room--  No moving air in the room, ambient temperature is around 70 degrees, screen brightness is minimal, and powertop has been used.  It's hovering around 54 degrees C and before it was around 42-46...  Any ideas?  Is there anything I can do to keep it cooler w/o purchasing a cooler?  I have a usb wireless mouse...  I also have CUPS disabled, bluetooth, tracker, etc., etc...  Just not cron, log, and dbus. and acpi.  (apm is disabled.)

So, any suggestions for removing services?  When I run top it says there are 109 total, 108 sleeping.  When not using the mouse in powertop I get ~250 wakeups per second, part of that is wireless.  The "extra timer interrupt" causes for ~75-100 of those though...  And I'm in C3 in only ~3ms of the time.

What can I do to get rid of all unnecessary services and reduce my CPU load, and increase C3 time?  I don't know what the extra timer interrupt is...  futex_wait (hrtimer_wakeup) also accounts for 60 of those, and obviously wireless right now for ~60 also.

What is hrtimer_wakeup or futex_wait, and what is extra timer interrupt?  How can I prevent them from causing so many wakeups?

Thanks everyone...

Let me know what you guys have done to increase battery life, reduce heat, and increase C3 powerstate...  I'm interested.


~~karvec

---

### Post by 444 on 2007-10-18
Make sure the cpu frequency scaling is on the right setting, ie ondemand setting instead of full blast. Easy way to do that is run "sudo dpkg-reconfigure gnome-applets" to enable the gui control for it, then just adding the cpu frequency applet to a panel.

As for powertop and C3 it's usually not services but userspace apps and drivers. For me my ATI driver was causing the most trouble. Firefox wakes up alot too on certain pages or if it's been on for a while.

Biggest thing you can do, if you're willing, is undervolt with Linux-PHC. I'll attach the patched 2.6.22 driver here since compiling it is can be a hassle to compile it. You'll have to figure out the voltage codes and test via trial & error (ie repeated crashes), but once you get it working it makes a huge difference.

---

### Post by karvec on 2007-10-19
Thanks man!  I have been using on-demand for a while and notice the difference--  Getting a cooler {unfortunately} but getting a really nice one and looking forward to it.  I'll play around with this driver...  Not sure what I'm doing but should be fun.  Don't have ATI, I have intel_915 or somesuch, so that wouldn't affect it.

But I'll tweak everything I can and run as little as possible.  Thanks for your feedback....


~~karvec

---

