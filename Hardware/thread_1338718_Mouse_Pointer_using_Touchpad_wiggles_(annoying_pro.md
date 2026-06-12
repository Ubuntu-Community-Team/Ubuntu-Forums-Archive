---
title: "Mouse Pointer using Touchpad wiggles (annoying problem)"
date: 2009-11-26
forum: Hardware
---

### Post by harry000 on 2009-11-26
Hello,

I am using Ubuntu 9.10 (64bit) on a HP dv5000 laptop (AMD Turion 64bit processor)

The problem is small but very annoying. The mouse pointer wiggles when I have my finger on the touchpad and not moving the pointer. 

It is very annoying when I am selecting a menu item, checking checkboxes, or clicking on links in a website. It reduces the accuracy of the pointer.

I have created a video of this behavior, please have a look: [http://www.youtube.com/watch?v=FvmrtAq07eA](http://www.youtube.com/watch?v=FvmrtAq07eA) 

I have installed "gsynaptics" package and tried reducing the sensitivity, but it does not resolve the issue.

Last week, I installed Fedora, the mouse works perfectly in Fedora. Actually, I have been having this issue for a long time (with previous Ubuntu versions too)

Please help me resolving this issue.

---

### Post by clevertomato on 2009-12-01
I was trying to hold off replying while this thread was still at zero replies, but I'm going to go ahead and chime in here and say that this same thing has been bugging me too. I've experienced it on with 32 & 64-bit Jaunty and Karmic on a Gateway MX7118 with Synaptics Touchpad and a brand new Lenovo IdeaPad Y550. It sounds like a minor thing but it's REALLY annoying.

It'd be great if there's a fix for it, especially since other Linuces don't have the problem.

---

### Post by alldunn on 2009-12-28
Having the same problem on an HP 2510p.  Any updates?

---

### Post by Debreshnev on 2010-01-20
I ran into this problem as well. Here is what I did to correct it. 

Follow these instructions:
[http://brettshaffer.com/blog/linux/multi-touch-touchpad-in-ubuntu-9-10/](http://brettshaffer.com/blog/linux/multi-touch-touchpad-in-ubuntu-9-10/)

When you create the file 11-x11-synaptics.fdi I used this as the values you can find at [http://pastebin.com/f9293cc4](http://pastebin.com/f9293cc4)

You can use any of the parameters available in "MAN synaptics"
[http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/karmic/man4/synaptics.4.html)

The parameter that seems to affect this problem is the JumpyCursorThreshold = setting this value to 200 helps this problem.

---

### Post by clevertomato on 2010-01-20
GREAT. Thanks. This works for me. What a nice improvement. I set mine to 300 for now. No more jumpy cursor! I can't seem to get multitouch to work but that's another issue.

FYI I did not have to create the file /etc/hal/fdi/policy/shmconfig.fdi but I followed all the other instructions.

---

### Post by nortexoid on 2011-01-20
I have the same problem but it's very minor. Still annoying. The blogpost that Debreshnev pointed to no longer exists. Can you guys tell me what you did? By the looks of the pastebin code, you set jumpy cursor to 200 or 90. Both didn't do anything for me.

---

### Post by clevertomato on 2011-01-24
nortexoid, what release of ubuntu are you running?

---

### Post by tws1220 on 2011-02-19
> **Debreshnev said:**
> I ran into this problem as well. Here is what I did to correct it. 

Follow these instructions:
[http://brettshaffer.com/blog/linux/multi-touch-touchpad-in-ubuntu-9-10/](http://brettshaffer.com/blog/linux/multi-touch-touchpad-in-ubuntu-9-10/)



Link is no longer valid. Is there anywhere else I can find the instructions?

---

