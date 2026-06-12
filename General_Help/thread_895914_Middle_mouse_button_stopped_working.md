---
title: "Middle mouse button stopped working"
date: 2008-08-20
forum: General Help
---

### Post by kabbage on 2008-08-20
Hey.

I'm on Hardy Heron, using a Microsoft Wireless Optical Mouse 2.0.
My middle mouse button was working fine until about a week ago when it seemingly randomly stopped responding.
For some reason, I can scroll, but I clicking the scroller doesn't do anything.
I checked xev, and clicking it doesn't get any response.

Could anyone help?
Thanks in advance.

---

### Post by silkstone on 2008-08-20
Is this in Firefox?

If so, Edit > Preferences > Advanced and tick the box 'Use autoscrolling'.

You'll probably have to restart FF for it to work.

---

### Post by kabbage on 2008-08-21
No, it's not that.
Ubuntu doesn't acknowledge the middle button at all.
It doesn't know it exists.

---

### Post by kabbage on 2008-08-22
Anyone?

---

### Post by randyr505 on 2008-09-11
> **kabbage said:**
> Hey.

I'm on Hardy Heron, using a Microsoft Wireless Optical Mouse 2.0.
My middle mouse button was working fine until about a week ago when it seemingly randomly stopped responding.
For some reason, I can scroll, but I clicking the scroller doesn't do anything.
I checked xev, and clicking it doesn't get any response.

Could anyone help?
Thanks in advance.

I am having the same problem. I used to copy with my middle mouse then paste but that quit working a month or so ago. I am running 2.6.22-14-generic which I have been running since probably Feb. 2008 according to /boot. Not sure why the links are from July though. My probably may have been since then.
/boot:
lrwxrwxrwx  1 root root      25 2008-07-11 22:15 vmlinuz -> vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1743752 2008-02-11 22:30 vmlinuz-2.6.22-14-generic

I generally don't like to do kernel updates because it almost always breaks something.

BTW, I am using a Dell Vostro with the Dell Bluetooth mouse and keyboard.

Randy

---

### Post by pie1pah on 2008-11-19
I'm experiencing similar issues on 64-bit Ubuntu 8.10 with a Logitech MX Revolution wireless mouse.

My precious middle button worked perfectly for a day or so, but after a few updates and in a completely unspectacular manner, it just stopped doing anything at all.

Didn't have a reason to run xev before, but as far as I can tell, the middle button used to be "button 3". Now xev doesn't even report it anymore.

Tested it in different usb slots, and also successfully tried all buttons/wheels/tilts in WinXP just before posting this, so I think it is safe to rule out hardware problems.

---

### Post by jaxxm on 2009-02-27
can any one help please. also on 8.10. new install but getting the same error.. must be a kernel thing.

---

### Post by fraktalek on 2010-03-05
I started having this problem too...out of nothing. Some ideas how to solve it?
The middle button stopped working, xev shows no events for it..

---

### Post by fraktalek on 2010-03-05
I found out it was likely a hardware problem. I tried out a different mouse of exactly the same type and it works fine.

---

### Post by norm.h on 2010-03-06
> **fraktalek said:**
> I started having this problem too...out of nothing. Some ideas how to solve it?
The middle button stopped working, xev shows no events for it..

I have the opposite problem:
When doing "copy and paste", I sometimes find that I've pasted in multiple places as well as the required destination, particularly when using Open Office Writer.
I know my mouse scroll wheel is configured to paste when depressed, and I suspect that it's over sensitive.
How can I configure the mouse to prevent this happening?

---

### Post by dbkliv on 2011-07-08
I recently had this hit me on Jaunty Jackalope. I've run this distro on this machine for several years, and haven't done any software updates recently.

I did move things around on my desk though, and in so doing I unplugged my mouse from a front USB port and stuck it in the back of my desktop.

Switching the mouse back to the front USB port made my middle mouse button start working again.

---

