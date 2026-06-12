---
title: "Lost touchpad after recent update"
date: 2010-06-09
forum: Hardware
---

### Post by jazzgossen on 2010-06-09
After updating to kernel 2.6.32-22 yesterday, among some other updates, I can no longer use the touchpad on my laptop. It doesn't matter if I boot the new kernel or the old one.

What's strange is that it does work during the GDM login screen, but stops a few seconds after I've entered my password and pressed the login button. 

I have seen lines a little like this one
```
psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
```
in dmesg, although I don't have that at the moment. Attaching a USB mouse works fine.

I tried appending "i8042.nomux=1" to the kernel boot options, as recommended in some post, but that didn't work.

---

### Post by jazzgossen on 2010-06-09
I search around for help last night for a long time, but now I just saw that there's a bug report about this at [launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727"). 

Post #93 there helped. For some reason touchpad_enabled was set to false. Enabling it in gconf-editor solved the problem.

---

### Post by magicvince on 2010-10-12
Thanks for you're report, I had the same problem.

I don't know why I lost my touchpad, but the gconf-editor saved me.

(for noobs like me : launch gconf-editor with terminal and search gnome/desktop/peripherals/touchpad )

---

### Post by Simon Bridge on 2011-06-08
This monster reappears ... only now [the old solution](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727/comments/103) does not appear to work. (hp envy 14 - right after todays update)


$ uname -r
2.6.32-33-generic-pae

losing the touchpad was one of the reasons I didn't use 2.6.35

---

### Post by Hulmemanitarian on 2011-06-08
Many thanks magicvince! I've recently installed 11.04 on a friends laptop and lost the touchpad. I'll try your solution and let you know how I get on.

---

