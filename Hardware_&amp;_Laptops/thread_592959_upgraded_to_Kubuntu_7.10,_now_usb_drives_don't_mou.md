---
title: "upgraded to Kubuntu 7.10, now usb drives don't mount"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by agent-s on 2007-10-26
pretty self explanatory... no mention of the usb drives in dmesg. any help?  nb: i am using kubuntu, but it used to be ubuntu before i installed kubuntu-desktop and removed most gnome packages.

---

### Post by agent-s on 2007-10-26
not only that, but X doesn't redraw the screen properly, so after I close a window, there'll be a big blank spot on the screen until i move something.

---

### Post by agent-s on 2007-10-30
bump

---

### Post by oodarthvader on 2007-10-31
I am having the same problem on my laptop (Compaq v6000) running Kubuntu 7.10.  When I insert the flash drive in the usb port nothing happens.  There is a light on the top of the device to show activity which never turns on and there is no event anywhere in dmesg. When I plug the same drive into my desktop running Kubuntu 7.10 it lights up and automounts just fine. 

 Is there a problem somewhere in the laptop power saving feature that is turning off the usb ports?

---

### Post by oodarthvader on 2007-10-31
found a fix.
In my boot options I added IRQFIXUP and now usb is working fine.
another option I saw was IRQPOLL

I hope this helps your problem agent-s

---

### Post by agent-s on 2007-10-31
what do you mean your boot options?  like the /boot/grub/menu.lst or something else?

---

