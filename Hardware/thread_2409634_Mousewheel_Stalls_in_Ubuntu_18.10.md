---
title: "Mousewheel Stalls in Ubuntu 18.10"
date: 2019-01-04
forum: Hardware
---

### Post by ubonetu2 on 2019-01-04
Ever since I started using Fluxbox off and on, my external mousewheel stalls.  The touchpad doesn't do it, just the usb mouse.  As soon as it disappears from lack of motion, you have to move the wheel back and forth to get it to respond.

Here's the result of lsusb:

```
Bus 002 Device 007: ID 08a8:0016 Andrea Electronics Bus 002 Device 006: ID 04ca:0061 Lite-On Technology Corp. 
Bus 002 Device 005: ID 0079:0006 DragonRise Inc. PC TWIN SHOCK Gamepad
Bus 002 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 002 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 002 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 001 Device 005: ID 05ac:0245 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 009: ID 05ac:821a Apple, Inc. Bluetooth Host Controller
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2513 Standard Microsystems Corp. 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```

Thanks, any ideas on this one would be great.

Ward

---

### Post by mikasu on 2019-01-05
Can you provide a lsusb when your wheel works and when it doesn't? I cannot help you much but I'm quite sure that might help other people help you.

---

### Post by ubonetu2 on 2019-01-12
> **mikasu said:**
> Can you provide a lsusb when your wheel works and when it doesn't? I cannot help you much but I'm quite sure that might help other people help you.

Thank you for responding, mikasu! I didn't get an email so I thought nobody had replied!

I solved it! It's this line in ~/.fluxbox/startup

```
unclutter -idle 2 &
```

When unclutter idles the mouse the scroll-wheel turns off.

I'm still tweaking to find the best setting but this is why it was happening, it's a default setting in Fluxbox.

If anybody needs to know this:

In the Terminal enter:

```
nano ~/.fluxbox/startup
```

Scroll down to "unclutter -idle 2 &"

Change that to:

```
#unclutter &
```

Or you can experiment with an idle time that works better for you, i.e.:

```
unclutter -idle 5 &
```

Control "o" save the file,

Exit Fluxbox from the menu and log back in.

---

### Post by mikasu on 2019-01-12
Nice that you were able to fix it! Have a nice day!

---

