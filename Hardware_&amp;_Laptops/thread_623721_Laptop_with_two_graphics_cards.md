---
title: "Laptop with two graphics cards"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by nickdaniels on 2007-11-26
My laptop has two graphics cards, an in-built Intel Corporation Mobile 915GM and an Nvidia Go 6600. I am able to choose which one to use via a switch on the laptop.

I have just installed Ubuntu 7.10 (only just changed over to linux woo!!) with the Intel card enabled, Unfortunately when I try to boot with the Nvidia graphics card the desktop interface does not load and I just have the plain text console view.

I assume this is because X or Gnome etc. is still trying to run with the Intel drivers...

Is there a way to save something like a hardware profile (in xp) for each card or to make sure the desktop loads correctly with both cards?

Thanks in advance,
Nick

---

### Post by subs on 2007-11-26
in the text mode... login to ur account....

once there... reconfigure xserver by typing...

> sudo dpkg-reconfigure xserver-xorg

stick to using the nvidia card as some intel cards dont have available drivers for ubuntu for 3d acceleration... so u wont be able to use compiz and all the other 3d effects that ubuntu offers on ur desktop

---

### Post by Daelyn on 2007-11-26
> **nickdaniels said:**
> My laptop has two graphics cards, an in-built Intel Corporation Mobile 915GM and an Nvidia Go 6600. I am able to choose which one to use via a switch on the laptop.

I have just installed Ubuntu 7.10 (only just changed over to linux woo!!) with the Intel card enabled, Unfortunately when I try to boot with the Nvidia graphics card the desktop interface does not load and I just have the plain text console view.

I assume this is because X or Gnome etc. is still trying to run with the Intel drivers...

Is there a way to save something like a hardware profile (in xp) for each card or to make sure the desktop loads correctly with both cards?

Thanks in advance,
Nick

[http://ubuntuforums.org/showthread.php?t=606686](http://ubuntuforums.org/showthread.php?t=606686)

---

### Post by nickdaniels on 2007-11-26
Thanks for the quick reply! 

however it would be good if i could use the intel as well as it is perfect for word processing etc. because it uses much less battery life and make the laptop run cooler...

is there a way to make x reconfigure itself automatically on start up each time the graphics card changes?

---

### Post by nickdaniels on 2007-11-26
ah thanks Daelyn!

---

### Post by Daelyn on 2007-11-26
It's cool, mate. 

Enjoy the new geek function of your laptop :)

---

