---
title: "Alot of Errors when trying to boot Ubuntu..."
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by Tartin on 2005-07-13
I just wanted to try Ubuntu on my new computer, so I booted up the Live-CD for AMD64 but it won't start the X server.

It sais my monitor ain't configurated or something, so I tryed "sudo xorgconfig" to access the setup and use some other drivers for my videocard.

At Sudo xorgconfig, first it askes me about my Mouse. Since I have a Logitech MX500, I select the Microsoft Compatible setup for it.

Then, It asks me about my keyboard, and I enter my keyboard model with USB. This works fine I think.

After that, it askes me about my monitor. I've got a brand new ViewSonic VP191s so I choose 31.5 - 64.3; Monitors that can do 1280x1024 @ 60 Hz

After configurating my monitor, it wants me to select a videodriver. I've got a ATI Radeon X850XT 256mb so I select the Radeon drivers.

Then, I save my xorg.conf.

Everything seems fine, I've configurated the xorg.conf to my system now.

But... "startx" <screen fades to black for a moment>

```

(==) Log file "/var/log/Xorg.0.log", Time: Wed Jul 13 18:44:10 2005
(==) Using config file: "/etc/X11/xorg.conf"
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o": No symbols found
(EE) xf86OpenSerial: Cannot open device /dev/mouse
           No such file or directory.
(EE) Mouse1: cannot open input device
(EE) PreInit failed for input device "Mouse1"
No core pointer

Fatal server error:
failed to initialize core devices

[yadayada contact X.Org team at http://wiki.X.org]

XIO: Fatal IO error 104 (Connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining.

ubuntu@c-7fd7e055:~$ _
```

My system is: AMD Athlon64 4000+, 1,5GB RAM, Radeon X850XT, 2x 400 gb harddisks (not relevant due to live-cd), MX500 (USB) mouse, Logitech Keyboard (seems to work fine to config the keyboard).

I've tryed with the Live-DVD for A64, the Live-CD for A64 and the Live-CD for x86. Getting the same error on all of them.

Please tell me if I forgot to add anything.

---

### Post by varunus on 2005-07-13
When you ran xorgconfig, did you select a USB mouse?  It seems that X is looking for a serial or PS2 mouse.

---

### Post by Tartin on 2005-07-13
[QUOTE=varunus]When you ran xorgconfig, did you select a USB mouse?  It seems that X is looking for a serial or PS2 mouse.[/QUOTE]

There isn't any options to choose USB Mouse. I tryed choosing "Logitech" but it's only for _really_ old logitech mices. Also, I tryed Auto but It's giving me the same errors as Microsoft Compatible Mouse.

When I choose MS Compatible Mouse, It sais It's what I chould choose if I have a Logitech mouse.

---

