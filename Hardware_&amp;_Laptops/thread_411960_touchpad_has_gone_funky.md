---
title: "touchpad has gone funky"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by Goonie on 2007-04-17
Hi

Ok now I've got my Acer 6460 laptop running smoothly the way I like except for one thing. After my first install a few days ago en some updated the touchpad worked just fine and the 4-way scroll button on the touchpad worked fine as well. But then I seemed to have done something to mess it up because now the touchpad is way too sensitive and the scroll button does things it shouldn't. If I press down on the scroll button it acts as if I pressed the right mouse button. The synaptic driver entry in xorg.conf doesn't really have many options to try and change. Is there a config file fore the touchpad somewhere or something I can do to get it back to what it was like before? Forgive me if I sound like a newbie... It's because I am :$

Thx

---

### Post by dday376 on 2007-04-17
Hi goonie,

I had similar problems on my HP w/Synaptic touchpad with the sensitivity.  I use a small program called syndaemon (found in package xserver-xorg-input-synaptics, which you may have installed already).  You can use it to help adjust sensitivity.  Add to your session something like:

```
/usr/bin/syndaemon -di .5s
```

That tells it that a push has to be .5 seconds before registering.  It's not perfect, but it's the best I've been able to manage.  I never got anywhere with trying to set the xorg.conf settings.

---

### Post by Goonie on 2007-04-18
I found out what was giving me this headache. The driver entry for "configured mouse" in xorg.conf gets automatically changed from "synaptics" to "mouse" if I boot up with an usb mouse plugged in. I changed the entry back to "synaptics" and everything was smooth again. I haven't really tested it more to see if I can produce this "bug" any other way than booting with the mouse plugged but I will when I get the time.

Regards,
Goonie

---

### Post by stenka on 2007-04-18
Wow, nice that you found where this problem comes from.
I exactly noticed the same mistake in the xorg.conf. The driver entry was inverted between the mouse and the touchpad !
I think that we should do a bug report... didn't you ?

---

### Post by Goonie on 2007-04-20
Yes we should if there isn't one already. Unfortunately I've never filed a bug report before so I'm not sure how to go about it. I will try and read up on the process when I get the time.

Regards,
Goonie

---

