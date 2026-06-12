---
title: "Mouse Issue"
date: 2010-03-09
forum: Hardware
---

### Post by JohnSearle on 2010-03-09
Hello all,

I am currently having an issue with my mouse click that seems to have started occurring within the last week and a half.

The problem is that when I click my left mouse regardless of the environment (desktop or app), it seems to randomly choose what to do. Sometimes clicking left will click right; sometimes clicking right will auto-choose from the menu; sometimes clicking and dragging will fail repeatedly... and the list goes on. This happens 1/5 times.

I don't have any issue with the mouse in my Windows boot, just Ubuntu 9.10 (which I have had installed for a month or more). Mouse is a Logitech MX-400.

Any advice is appreciated.

Thanks,

- John

---

### Post by khelben1979 on 2010-03-10
I wonder how your xorg.conf file looks like. Can you post it in this thread? ( /etc/X11/xorg.conf )

The configuration file reveals what mouse driver + graphics driver you're currently using.

---

### Post by JohnSearle on 2010-03-10
> **khelben1979 said:**
> I wonder how your xorg.conf file looks like. Can you post it in this thread? ( /etc/X11/xorg.conf )

The configuration file reveals what mouse driver + graphics driver you're currently using.

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

---

### Post by khelben1979 on 2010-03-10
Okay, since the mouse is connected through usb I see that it's nothing which is gonna help in editing that file.

Have you ever rebooted the system to see if the problem with the mouse disappears?

---

### Post by JohnSearle on 2010-03-10
> **khelben1979 said:**
> Okay, since the mouse is connected through usb I see that it's nothing which is gonna help in editing that file.

Have you ever rebooted the system to see if the problem with the mouse disappears?

Yup, my computer goes off every night.

Thanks for the help, BTW.

---

