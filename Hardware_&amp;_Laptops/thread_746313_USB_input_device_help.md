---
title: "USB input device help"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by jimmyhilldrix on 2008-04-05
Hello,

I have a USB joystick that I'm having some issues with.  If I restart my computer and plug the joystick in, it generally works fine, however if I unplug it and plug it back in, it stops working.  I also have noticed that after plugging it in and unplugging it, apps like lsusb and modprobe lock up when I try to list usb devices and remove the module in question.  The only clue I have for this problem is that when I attempt to rmmod the module, it says the module is still in use even though I've unplugged the joystick.

So my question is, is there a way to forceably unload a module or is there a way to complete restart the USB subsystem so that i don't have to restart the computer every time I plug the joystick in?

Thanks

---

