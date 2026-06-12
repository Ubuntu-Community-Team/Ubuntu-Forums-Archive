---
title: "Fingerworks Touchsteam"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by holomorph on 2005-03-07
Bit of an odd problem, I'm not really sure where to start troubleshooting; hopefully someone can help (hopefuly this is even the right forum).

I have a Fingerworks Touchstream keyboard, which works normally in windows XP on this laptop, and on my debian box.  It works almost as well on the same laptop running Ubuntu, except for one thing.  Click and drag.  Clicking and dragging is done by dropping three fingers  on the touch surface and then sliding them as you would mouse on any touchpad.  It works in Ubuntu, but the click part seems a bit delayed.  For instance if I am trying to move a window and don't wait half a second after dropping my three fingers before I move them, the cursor will usually not be on the header bar by the time the click registers.  Similarly, if I want to highlight text, I often find that I miss the first few letters of whatever I am trying to highlight.  I hope that makes sense.  

The touchstream is supposed to be just like a standard USB keyboard and  mouse, so doesn't require any special drivers;  I'm going to contact fingerworks as well, but the fact that it works perfectly on my debian box makes me  suspect that Ubuntu migdt be doing something different with reguards to USB input devices.  Any ideas about what to look at would be appriciated.

Bjorn

---

### Post by Roshan on 2005-06-01
I've just run up against the same problem, using a Fingerworks Touchstream keyboard on the Hoary Hedgehog.  Clicking works, with no problem, but dragging items doesn't work unless you give it a second or two to register.  Did you possibly find out the reason for this?

---

### Post by holomorph on 2005-06-01
I never did manage to figure it out, but I did find a solution which works for me.  There is a setting in your touchstream which allows you to use pinky/thumb/index fingers for different clicks, so you don't have to use the three finger drop to click and drag, which actually I find much nicer.  The way I have it set, I mouse with me middle and ring finger, drop the index finger to left click, pinky for right, and thumb for middle.  I think the setting is "enable [something] outside game mode".  

Anyway, the other strangeness is, I've now installed Ubuntu (Haory) on my desktop machine, and the three finger click and drag works as it should on this machine, just as it did when I had debian on it.  The really bizarre thing is, when  was troubleshooting I tried booting both Ubuntu and I think Morphix on this same box and experienced the buggy behavior I get on my laptop.  My strategy was to find a live distro that exibited the behavior, and one that did not, so that the fingerworks people, or someone with more knowlege, could compare and maybe figure out the problem.  Unfortunately, I didn't manage to find a live distro that works, and now fingerworks pretty much no longer exists.  Luckily, using the setting described above, I don't even notice anymore, since I find it easier to mouse that way anyway.

---

### Post by Roshan on 2005-06-02
Thanks for your reply and the tip.  In the interim, it seems I've found the reason for the Touchstream misbehaving with Ubuntu: the automatic /etc/X11/xorg.conf file that it generates assumes for whatever reason that the TouchStream is a Synaptics device (which of course it isn't), and makes the TouchStream use the synaptics driver.  I changed the driver from "synaptics" to "mouse" instead, and also set the protocol to be "ImPS/2", and now the TouchStream functions the way it should, responding immediately to drag events.  I'm guessing you could leave the protocol on "auto-dev", and it should still allow scrolling, but I haven't tested that.  I find that the default acceleration of the TouchStream in this configuration is quite high - need to look around to see how to lower that, but otherwise, all is well.

---

### Post by holomorph on 2005-06-02
Hmm, that's interesting.  Seems to me I played with the xorg.conf settings, commented out the synaptic touchpad bit, but perhaps it does cast some light on the situation.

When I installed Hoary on my desktop, I did not have the touchstream plugged in; It's possible that I did have it plugged in every time I reconfigured the xorg-server on my laptop.  Also since my laptop has a touchpad, perhaps that is a factor in getting a faulty configuration.

---

### Post by Roshan on 2005-06-02
True ...., maybe the fact that it's a laptop is leading it to pick the Synaptics driver, as I too am installing this on a laptop.  And any device plugged in on the USB bus after auto-detection would appear as a standard USB mouse and keyboard I guess, the way the TouchStream would want itself to appear.

---

