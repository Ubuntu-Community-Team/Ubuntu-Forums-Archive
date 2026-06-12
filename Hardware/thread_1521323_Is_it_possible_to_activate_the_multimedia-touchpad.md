---
title: "Is it possible to activate the multimedia-touchpad?"
date: 2010-06-30
forum: Hardware
---

### Post by dreKion on 2010-06-30
Hello friends!


Is it possible to activate the multimedia-touchpad?

My laptop is an Acer Aspire Ethos 8943G


[IMG]http://hothardware.com/newsimages/Item12669/ethos-pad.jpg[/IMG]

---

### Post by yaddoshi on 2011-08-18
I second this question...:popcorn:

...er yeah - I'm gonna see if it's possible to use ndiswrapper on something like this in the meantime... (shhh... proprietary hardware...)

> **dreKion said:**
> Hello friends!


Is it possible to activate the multimedia-touchpad?

My laptop is an Acer Aspire Ethos 8943G


[IMG]http://hothardware.com/newsimages/Item12669/ethos-pad.jpg[/IMG]

---

### Post by yaddoshi on 2011-08-19
No luck with ndiswrapper - seems to be more oriented toward WIFI drivers anyway.

I did manage to install gsynaptics and get it working upon modifying xorg.conf as per [this article]("https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey").  This is good because it permits the enabling of different scrolling options and better sensitivity customization than the default touchpad config settings.

However, gsynaptics does not seem to support the multimedia input functionality of this touchpad.  Pushing the round button in between the left & right buttons does nothing - the multimedia inputs like in the photo above do not light up.

If anybody else out there has any ideas on this, I'm all ears.

---

