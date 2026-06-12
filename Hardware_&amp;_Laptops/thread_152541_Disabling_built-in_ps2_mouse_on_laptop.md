---
title: "Disabling built-in ps2 mouse on laptop"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by kylefarlow on 2006-03-30
I have an HP Omnibook 6000 that has a built-in trackpad and pointing stick.  The pointing stick has issues and needs to be disabled.  This cannot be done in the BIOS.  In Windows, this is a simple matter of pulling up the Synaptics control panel and disabling the point stick.  But I cannot figure out how to do this in Ubuntu.

My goal is simple.  I want to be able to plug in an external USB mouse when I work at my desk, but when I disconnect the USB mouse I still want to be able to use the trackpad.  Simple!

There are two entries in my xorg.conf file.  One is for "/dev/psaux" referencing the "synaptics" driver.  The other is for "/dev/input/mice" referencing the "mouse" driver.  

I've tried disabling the synaptics device, and all it does is disable my trackpad... the pointing stick is still operational, with all its problems.  And if I disable the mouse device, it disables both the pointing stick AND my external USB mouse.

So what can I do?

Thanks,
Kyle

---

### Post by kylefarlow on 2006-03-30
Ping?

Incidentally, how do I tell which actual device is plumbed to a particular device file?

For instance, I see the following device files:

/dev/input/mouse0
/dev/input/mouse1
/dev/input/mouse2
/dev/input/mice

But I have no idea which of these files corresponds to an actual device.  I checked my dmesg output, but the device drivers for mouse and synaptics don't seem to print out the device file path...

I'd like to figure out which one corresponds to my USB HID mouse and try specifically enabling only that one in my xorg.conf file.  I tried to do this by process of elimination (Trial and error), but when I switched to /dev/input/mouse1, I ended up causing a system black-screen hang on X startup.

Please help!

Thanks,
Kyle

---

### Post by kylefarlow on 2006-04-01
Does anyone know how this stuff works?

The fact that I can't even disable a mouse doesn't bode well for other types of activities in Ubuntu...

---

### Post by zcox on 2006-08-27
Did you ever find out how to disable that stupid pointing stick?  I have the same problem with the pointing stick on my Dell Inspiron 4100.

---

