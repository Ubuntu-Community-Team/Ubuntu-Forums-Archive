---
title: "Will touchscreen support/multitouch be easier in 12.04?"
date: 2012-03-18
forum: Hardware
---

### Post by heyho on 2012-03-18
Apologies if this has been covered elsewhere, but I have been searching and reading until my eyes hurt, and don't seen to be able to find a definitive answer.

I have a generic chinese tablet PC - Atom 1.6, 2gb ram and 320gb hdd.  The touchscreen is identified as a Hanvon 10.1 overlay.  It works well out of the box in Win7, which is not surprising as that is what it ships with.

I installed Mint-Debian at first, as I've wanted to try it for some time.  The touchscreen was unusable.  Terrible lag and inconsistent selections.  I then proceeded to install 11.10, (with low expectations) thinking that unity might be better suited to this type of device.  To my delight, it worked, and worked well - the touch response is as good as it was under Win7, but there is no multitouch.

Having read a little on the subject, I made sure that ginn was installed, and also installed utouch, but I'm not too sure where I go now to try to configure anything.  I understand that ginn uses a wishes.xml file, but there are reports of it being problematic in terms of reliability.

If it is likely that 12.04 will offer more in terms of function, I'll wait.  I usually use LTS releases exclusively anyhow.  All I really want it right-click (long screen press), and 2-finger scrolling.

---

### Post by Favux on 2012-03-18
Hi heyho,

There's really two issues.  The first is whether the Hanvon 10.1 has support in the kernel's HID section for multi-touch.  It is clearly there since you have single finger touch.  The capability may be inherently there but you may need to change how it is handled by blacklisting it in hid-core and adding a multi-touch quirk for it in usbhid or some such.  Unless you're real lucky figuring that out usually requires a developer.

The other is X support for multi-touch.  They finished adding multi-touch to XI 1.2 in December I think.  Don't know if Precise will have that.  But improvements should be propagating through this year.  Peter Hutterer writes about it in his blog:  [http://who-t.blogspot.com/2011/12/multitouch-in-x-getting-events.html](http://who-t.blogspot.com/2011/12/multitouch-in-x-getting-events.html)  In the meantime the [N-trig HOW TO]("http://ubuntuforums.org/showthread.php?t=1252492") has links to several ginn wishlists and to some multi-touch sites.  You might want to install the little app that tells you if you are getting multi-finger recognition.  I think it's on the linked Ubuntu multi-touchn wiki.

---

### Post by heyho on 2012-03-18
Thanks Favux, I will read and digest the information you have kindly linked to.

I will probably wait until the LTS is released before I persue this problem, as that's what I usually stick to.

---

