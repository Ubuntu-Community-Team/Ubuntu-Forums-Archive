---
title: "Microsoft Wireless Laser Mouse 5000"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by isenguard on 2007-11-04
Hi,

I've got a Microsoft Wireless Laser Mouse 5000 mouse, which works for the basic functionality (three buttons + vertical scroll wheel).  However, there are two extra buttons and a horizontal scroll wheel which I can't get to work.  Using xev, the horizontal scroll wheel doesn't generate any events, and the two extra buttons are mapped to buttons 2 & 3 respectively.  Does anyone else know how to get this mouse working?  Should I be using the evdev driver rather than the mouse driver?

Regards,
Lyndon

---

### Post by erlinux on 2007-11-04
i have the a similar problem with my [ms comfort optical mouse 3000]("http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=041"). in xev the horizontal scroll has the same problem, and with extra buttons, except i only have one extra button (says Button9)and it doesnt have a function

---

### Post by beefbowel on 2008-02-24
i have this mouse and it does not work very well with ubuntu.  i tried btnx and that too does not work.  i wish ubuntu had the ability to recognize and support hardware when the driver/software cd that comes with hardware does not work in linux.  

if any of you have the microsoft laser mouse 5000 could you explain how you configured it.  thanks in advance :)

---

### Post by Vermind on 2008-03-25
Hello, I have a Microsoft Notebook Optical Mouse with Tilt Wheel (Name from /proc/bus/input/devices)
And it has the usual buttons plus a tilt wheel (buttons 6 and 7) and an extra button called 9 for the thumb. It works very well with the evdev driver on my Ubuntu Feisty amd64 desktop. On my HP Pavilion dv6500 Ubuntu Gutsy 32-bit laptop, the horizontal scroll wheel does not work. On the Feisty, I also have a Logitech Optical mouse with tilt wheel. My configuration that works on the Feisty is:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "Name" "Logitech USB-PS/2 Optical Mouse"
    Option         "CorePointer"
    Option         "AlwaysCore"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse2"
    Driver         "evdev"
    Option         "Name" "Microsoft Microsoft Notebook Optical Mouse with Tilt Wheel"
    Option         "CorePointer"
    Option         "AlwaysCore"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

```

The same configuration on my laptop makes the Logitech mouse work very well, but the Microsoft one does not work. So, I would assume some problem has been introduced in Gutsy.

---

### Post by Vermind on 2008-03-25
Hello,
Update: tried to use feisty version of evdev. No luck.
Also tried feisty version of Xorg core. No luck.

---

### Post by Vermind on 2008-03-28
Hello,
I am officially abandoning fixing the Microsoft mouse. I returned it and got a Logitech one instead. It works great.

---

