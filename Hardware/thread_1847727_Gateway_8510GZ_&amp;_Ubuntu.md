---
title: "Gateway 8510GZ &amp; Ubuntu"
date: 2011-09-21
forum: Hardware
---

### Post by StarStrider on 2011-09-21
Hi all, I searched and found two relevant threads, but they were unanswered so I decided to post my own thread. I also did not find my laptop listed in either the compatibility or incompatibility list.

I recently resurrected my old laptop from its previous hard-disk failure. It's an older Gateway laptop, model 8510GZ, purchased in 2005. It was quite the beast with WinXP, and even in 2010 it was working better than new laptops. Heck, I was able to play Oblivion on it with High settings and no problems.

Anyway. I didn't want to go back to XP (my new desktop uses 64-bit Win 7), so I thought I'd try Natty. This of course was before I knew Ubuntu often has problems with laptops. I'm trying to get the system totally stable (i.e. reliable) because at the end of the week I will be house-sitting for slightly over two weeks, and I really need to be able to use the laptop or I will probably go [more] insane.

Installation for 11.04 went just fine. I used a CD and nothing special, and for the last two days it has been running perfectly. I had a minor glitch when installing Office 2007 through PlayOnLinux, which was quickly resolved, and another glitch when I was installing software through the Terminal (which was my fault, as a total n00b Linux user), which was resolved after a restart.

My only problem has been that last night I started it up and my touchpad and mouse would not work. I was, however, able to use a USB mouse. I put it to hibernate at one point and after it woke, the laptop's touchpad was working just fine again.

So my question is this. A user on a computer-support forum I'd been using previously indicated that was the problem that led to Ubuntu failing on his laptop (different maker and model, though). Is this the case; does this sound like it'll be the "first of many" problems to come? Or does it sound like it's only a minor glitch in a pairing that should otherwise continue to run smoothly?

Any insight/suggestions?

Specs on my machine [can be found here]("http://support.gateway.com/support/srt/docs.asp?sn=T225701007262"). Let me know if you want any other technical information.

---

### Post by Toz on 2011-09-21
Hello and welcome to the forums.

Was this a one-time occurance, or does it always happen now that when you start your computer - that you have no touchpad/mouse activity?

Being an older laptop, some of the links are dated.

- from: [https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad") there is an information regarding a disabled touchpad. You can try enabling it by typing in the following command in a terminal window:
```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

- post #50 of this bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all") suggests creating a new file: **/etc/modprobe.d/touchpad.conf** and adding **options psmouse proto=imps** to it. Save and reboot.

- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59867?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/59867?comments=all") - describes a bug where the touchpad/mouse stopped working after suspend. Not the smae but similar. You're notebook is referenced there as one of the systems affected by this bug. The solution to that problem appears to be adding **atkbd.reset** to the kernel command line. (I've also seem references to using **i8042.reset** as a kernel parameter)

Maybe you can give them a try and see if any work.

---

### Post by StarStrider on 2011-09-21
So far it has only happened the once, but then again I've only been using Natty for about three days. And I haven't used hibernate or suspend very much, so I'll give those states some run-throughs and see if I can fetch some repeated instances.

That code is perfect; just what I was looking for. I thought I'd seen that thread, I just must have missed the post.

I've made a note of the other two fixes and I'll try them if the touchpad fails again after running in the hibernate/suspend.

Thanks!

---

