---
title: "Getting external VGA and S-Video working on Dell 700m?"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by naked on 2006-06-17
Can anyone point me in the right direction?

I'm needing to plug into a projector (vga), external lcd (vga), and a T.V. (s-video) to do some presentations in the next month.  How do I go about getting this to work in Ubuntu.  I've tried the function key that has the CRT/LCD button, but I can't get it to work. 

Are there any programs out there that can manage display settings?

Luke

---

### Post by x64Jimbo on 2006-06-17
I'd also be interested in this, as I would love to start doing my presentations in Linux to wow the classroom and to show that it really is usable and better than Windows in many ways.

---

### Post by Paul Chang on 2006-06-23
I am also interested in this. Do you guys have any luck?

---

### Post by ntwrkguy on 2006-06-29
If it helps to bump it up, I am a 700m user as well and am wondering too!

---

### Post by evil_elman on 2006-06-29
What's the hardware of the GPU (ATi, Nvidia, Intel)...

For ATi cards (I've only got exeprience with this) there is a tool called 'aticonfig' which can be used to activate external monitors / TV's. There's also a GUI for multi-monitor management (not TV's) which is called 'fireglcontrolpanel' for ATi cards.

For Nvidia and Intel, I don't know.

---

### Post by naked on 2006-06-29
[http://www.celifornia.com/documents/dell700m.html#Video-out](http://www.celifornia.com/documents/dell700m.html#Video-out)

That link has a xorg.conf file at the bottom.  I've been messing with it for a few minutes and it works fine.  You will need to manually edit it to get it how you like.  I hate extended desktops, so I turned that off.

When I have a little more time, I'm going to compare my original xorg.conf to this new one and make sure everything is in order.  My touchpad wont scroll now for instance.  Little things that are easy to fix I'm sure.  I'll post my finished fine when I'm done... if that ever happens.

L

---

### Post by shooters on 2006-09-26
I've posted my xorg.conf on [http://www.ubuntuforums.org/showthread.php?t=130322]("http://www.ubuntuforums.org/showthread.php?t=130322")

I can extend Desktop + Use projector...

Shooters

---

