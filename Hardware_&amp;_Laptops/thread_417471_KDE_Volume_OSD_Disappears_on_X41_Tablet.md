---
title: "KDE Volume OSD Disappears on X41 Tablet"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by caecus314 on 2007-04-21
Hello, everyone.  I have been running Kubuntu on my Lenovo (IBM) X41 Tablet ever since Hoary, and as far as I can remember, this has always presented itself as a minor annoyance.  I just did a fresh install of 7.04, and sure enough, the problem is still here.

The first time I've run Kubuntu after installation, the volume up, down, and mute buttons have all worked perfectly.  That is--when they are pressed, they change the master volume and cause a (somewhat ugly) on-screen display to pop up that shows the new volume.  For some reason that I can't seem to figure out, the second or third time that I restart the computer, none of these buttons work.  The buttons still adjust the hardware volume, but the master volume does not change to reflect this adjustment, and no OSD pops up.  So I can still change the hardware volume, but I have no way of knowing what level it is at unless I actually play a sound, and the software master volume listed in KMix is now completely independent.

I do have one theory as to what could be causing this.  I always like to use the Caps Lock key as my Compose key.  I set this up by going to System Settings > Regional & Language > Keyboard Layout, enabling xkb options, and checking the box that says "Caps Lock is Compose."  Perhaps this inadvertently breaks the keyboard-volume-control system?  That is my best guess.

Whatever the case may be, I would appreciate any advice regarding how to get the system back.  Thank you!

---

### Post by kobewan on 2007-04-26
Yeah, that is what breaks it. My X41 had the same problem when I tried doing a similiar thing, and I got it back by going to Keyboard Layout and disabling the check box (the one that says "Enable xkb options"). Apparently this is a known bug with KMix. There was a workaround solution suggested (I can't remember where) which suggested installing older versions of KMilo and configuring it yourself. I'm sorry I can't help any more, but I didn't need the xkb options much so I just turned it off. If you have any success, please post here.

---

### Post by caecus314 on 2007-04-28
Hey!  Thanks for the response!

I guess I never thought to restart the computer after disabling the xkb options.  But you're right; it magically works again once I do.

I'll look into this some more when I have time, and hopefully I'll come up with some sort of solution to post here.

---

