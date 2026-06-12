---
title: "Acer Aspire One touchpad not working on Intrepid"
date: 2008-11-12
forum: Hardware
---

### Post by Peter Shillan on 2008-11-12
Hi there,

I have been using Xubuntu Intrepid Ibex (8.10) since beta.  I have been keeping up with all the updates and things have been really good!  Until yesterday that is, when my touchpad stopped working completely for no reason I could see.

Things I have tried so far:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I looked at this page.  My touchpad appears to have been detected when I use:

xinput list

but is not responding at all.  I tried adding configuration to /etc/X11/xorg.conf, even though I believe it is not used.  Still no luck.

I tried a live CD of Ubuntu 8.10 and the touchpad still wasn't working.

I have been using suspend/resume and it was fine but I have seen hints somewhere that this can cause touchpad problems, but even after rebooting?  Seems unlikely...

I would appreciate any ideas/debug help anyone could come up with as, even though I hate the touchpad and will get a wireless mouse, I'd like it to work.

Everything else is still working brilliantly.  Even my HTC TyTn II was automatically recognised as a modem!  Let's hope we can sort this little problem out... ;)

Thanks,

Peter

---

### Post by poldie on 2008-11-12
> **Peter Shillan said:**
> Hi there,

I have been using Xubuntu Intrepid Ibex (8.10) since beta.  I have been keeping up with all the updates and things have been really good!  Until yesterday that is, when my touchpad stopped working completely for no reason I could see.

Things I have tried so far:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I looked at this page.  My touchpad appears to have been detected when I use:

xinput list

but is not responding at all.  I tried adding configuration to /etc/X11/xorg.conf, even though I believe it is not used.  Still no luck.

I tried a live CD of Ubuntu 8.10 and the touchpad still wasn't working.

I have been using suspend/resume and it was fine but I have seen hints somewhere that this can cause touchpad problems, but even after rebooting?  Seems unlikely...

I would appreciate any ideas/debug help anyone could come up with as, even though I hate the touchpad and will get a wireless mouse, I'd like it to work.

Everything else is still working brilliantly.  Even my HTC TyTn II was automatically recognised as a modem!  Let's hope we can sort this little problem out... ;)

Thanks,

Peter

I'm in the same boat as you. I'm working my way through that page. My hardware is detected.  I installed Touchpad, which made no difference.  I'm going to try this next:

[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

I don't understand how some people have no issues at all.  Isn't a laptop like the Aspire One effectively a console - each one identical?

I will report back on this thread if I have any joy, as well as here:

[http://ubuntuforums.org/showthread.php?t=928052](http://ubuntuforums.org/showthread.php?t=928052)


Edit:  I found a solution on that other thread - you might want to check it out!

---

