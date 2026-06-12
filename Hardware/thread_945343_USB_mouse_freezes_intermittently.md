---
title: "USB mouse freezes intermittently"
date: 2008-10-12
forum: Hardware
---

### Post by tentotwo on 2008-10-12
Hello everyone,

this is just to keep people with a similar problem from wasting time by looking for software errors:

My USB-connected mouse had started to freeze up intermittently, always for slightly less than a second, with sometimes five, sometimes 60 seconds between freezes. The touchpad worked fine during the freezes.

The mouse showed up fine in lsusb, dmesg didn't show any error messages.

Forum/Google searches didn't turn up this problem, usually "intermittent freezes" showed up as disconnects/connects in dmesg.

I left the problem overnight, and when I started my computer the next morning, the mouse didn't react at all (touchpad still working fine) and also didn't show up in lsusb anymore. That's when I tried out the mouse on a different computer running windows, also with the result of the mouse being neither recognised nor working.

It seems that this behaviour (freezing in irregular intervals) can be a sign of hardware failure. So before you reconfigure your X or update your BIOS (that would have been my next step...), just hook the mouse up to a different computer...

Jake

---

### Post by Sef on 2008-10-12
> It seems that this behaviour (freezing in irregular intervals) can be a sign of hardware failure. So before you reconfigure your X or update your BIOS (that would have been my next step...), just hook the mouse up to a different computer...

Weird things happening can be a hardware failure sign.  I had a mouse that would shut two tabs when I only clicked on one.  Drove me nuts till I figured out the mouse was bad.

---

### Post by madestro on 2008-10-16
I had the same issue in my ubuntu install as far as 7.10 goes, also with other distros as openSUSE, mandriva and kubuntu. After 2 to 10 minutes my mouse would freeze totally, BUT the keyboard would work just fine.
After much looking into the forums I found this page, [http://www.hidpoint.com/features.html](http://www.hidpoint.com/features.html) now I can't assure you this will work since half way through the install I could not select a check mark and had to quit the installation and after rebooting the issue magically dissapeared and I've been using the mouse without a problema at all, maybe it'll magically fix yours.

---

