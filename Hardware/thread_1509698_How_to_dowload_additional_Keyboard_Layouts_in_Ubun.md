---
title: "How to dowload additional Keyboard Layouts in Ubuntu 10.04"
date: 2010-06-14
forum: Hardware
---

### Post by __B__ on 2010-06-14
I installed Ubuntu 10.04 in my machine.

I have a Brazilian Keyboard that I need to use in this machine for some testing, but none of Brazilian Layouts that came with Ubuntu Lucid Lynx release are 100% compatible (I'm missing question marks and "/").

How do I download additional keyboard layouts? Is it possible? My keyboard model is "HP KU-0316" (Brazilian Version).

If it's not possible to download this keyboard layout, can I at least try to use an utility to "map" my failing keys?

I'm new to Linux, but can learn new things.

Thanks!

---

### Post by __B__ on 2010-06-15
Anyone? My Ubuntu default language is set to English, and the keyboard is Brazilian. Does it matter?

---

### Post by yossell on 2010-06-15
the command xmodmap might be what you're looking for: that allows you to remap keys on the keyboard, and I believe there are ways of making the changes permanent. It's not completely straightforward - but htere are some links that might help:

[http://www.xfree86.org/4.2.0/xmodmap.1.html](http://www.xfree86.org/4.2.0/xmodmap.1.html)
[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

---

### Post by __B__ on 2010-06-15
Thanks!

I tried the xev utility to detect my keyboard, and when I press my question mark key, it isn't detected. I'm using this Ubuntu installation in a VM in VirtualBox. Maybe it's a virtualbox problem?

---

### Post by __B__ on 2010-06-16
I've tried showkey -k too and still no luck (no key is identified)... anyone?

---

### Post by yossell on 2010-06-16
sorry - not sure what you're trying to do at this stage.

Is it (a) your keyboard has a ? which isn't being detected by Ubuntu on virtual box, and you want this key detected in this system. If so, I can't be of much help here - I take it that the key is not faulty, it's detected outside of your virtual box and works fine? Only thing I can think of for seeing whether it's a ubuntu or virtualbox problem is to run a livecd on the computer and see if ? key works - that may help you make some progress to the solution.

Or
(b) you just want to be able to type ? under Ubuntu in virtual box and you're willing to forget that key - if so, I'm not sure why it's not possible to map that character onto some other key.

---

### Post by __B__ on 2010-06-16
Yes, thats the a) option. I have a Ubuntu 8.04 host, with this keyboard. It works great.

I have Ubuntu 10.04 as a guest, and in this VM the ? doesn't work.

When I run xev in my host, I get:

KeyRelease event, serial 30, synthetic
NO, window 0x3600001,
root 0x5d, subw 0x0, time 19346721, (726,722), root:(730,746),
state 0x2010, keycode 211 (keysym 0x2f, slash), same_screen YES,
XKeysymToKeycode returns keycode: 61
XLookupString gives 1 bytes: (2f) "/"
XFilterEvent returns: False

And when I run showkey -v:

0x59 0xd9

When I run xev and showkey in the guest, nothing happens.

I already can have ? using "Alt Gr + W", but it's not the optimal solution. This is the ONLY key that has a problem.

---

### Post by simosx on 2010-06-17
> **__B__ said:**
> Yes, thats the a) option. I have a Ubuntu 8.04 host, with this keyboard. It works great.

I have Ubuntu 10.04 as a guest, and in this VM the ? doesn't work.

When I run xev in my host, I get:

KeyRelease event, serial 30, synthetic
NO, window 0x3600001,
root 0x5d, subw 0x0, time 19346721, (726,722), root:(730,746),
state 0x2010, keycode 211 (keysym 0x2f, slash), same_screen YES,
XKeysymToKeycode returns keycode: 61
XLookupString gives 1 bytes: (2f) "/"
XFilterEvent returns: False

And when I run showkey -v:

0x59 0xd9

When I run xev and showkey in the guest, nothing happens.

I already can have ? using "Alt Gr + W", but it's not the optimal solution. This is the ONLY key that has a problem.

So the issue is not about adding a new keyboard layout but configuring the guest's keyboard layout under VirtualBox.
The fact that VirtualBox is used might be the real cause of the problem.

The latest Brazilian keyboard layouts are at 
[http://cgit.freedesktop.org/xkeyboard-config/tree/symbols/br](http://cgit.freedesktop.org/xkeyboard-config/tree/symbols/br)
You can compare with your working layout from Ubuntu 8.04 with above, and see if there has been a change.

You can google for more with 'virtualbox linux keyboard layout problem', etc. Also, it might be good to update the thread title.

---

### Post by __B__ on 2010-07-06
Solved. I was a VirtualBox bug, and it was fixed in ticket [#7022]("http://www.virtualbox.org/ticket/7022").

---

