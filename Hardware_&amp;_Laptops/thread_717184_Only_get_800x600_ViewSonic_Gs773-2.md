---
title: "Only get 800x600 ViewSonic Gs773-2"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by doug-M on 2008-03-06
This is an older monitor but it is capable to at least 1024x768 at decent refresh rates.
In fact it works fine with Knoppix and Windows 2000.

Unfortunately in Ubuntu 7.10 it keeps getting set back to 800x600.;

If I go to Administration -> Screen and Graphics

It comes up with 
ViewSonic Gs773-2
800x600 at 85 Hz

Selecting ViewSonic Gs773-2 comes up with a screen that lets you choose the model with buttons for [Add] [Detect].

[Detect] changes whatever the current selection is to the ViewSonic Gs773-2
  It lists Horizontal range: 30-70
  Vertical refresh rate: 50-180


It seems that this monitor entry is incorrect in the hardware database and only allows 800x600 and 640x480. I tried manually creating a xorg.conf by stealing parts of the knoppix one. That works but after a reboot it seems to detect the monitor and reset it back.

So anyone have any good solutions?

How do I go about getting the hardware database entry fixed properly? By that I mean on my system and whatever central repository the distribution uses.

---

### Post by overdrank on 2008-03-06
> **doug-M said:**
> This is an older monitor but it is capable to at least 1024x768 at decent refresh rates.
In fact it works fine with Knoppix and Windows 2000.

Unfortunately in Ubuntu 7.10 it keeps getting set back to 800x600.;

If I go to Administration -> Screen and Graphics

It comes up with 
ViewSonic Gs773-2
800x600 at 85 Hz

Selecting ViewSonic Gs773-2 comes up with a screen that lets you choose the model with buttons for [Add] [Detect].

[Detect] changes whatever the current selection is to the ViewSonic Gs773-2
  It lists Horizontal range: 30-70
  Vertical refresh rate: 50-180


It seems that this monitor entry is incorrect in the hardware database and only allows 800x600 and 640x480. I tried manually creating a xorg.conf by stealing parts of the knoppix one. That works but after a reboot it seems to detect the monitor and reset it back.

So anyone have any good solutions?

How do I go about getting the hardware database entry fixed properly? By that I mean on my system and whatever central repository the distribution uses.

Hi and if I may ask what is the graphics card in the system and have you install the drivers for it?

---

### Post by doug-M on 2008-03-06
Graphics card is ATI Mach64 3D Rage II
The driver comes up as:

 vesa - Generic VESA-compliant video cards

I went in and explicitly selected the ATI driver
  ati - ATI Mach8, Mach32, Mach 64, and Rage...

However it seems to reset back to vesa as well.

---

### Post by overdrank on 2008-03-06
> **doug-M said:**
> Graphics card is ATI Mach64 3D Rage II
The driver comes up as:

 vesa - Generic VESA-compliant video cards

I went in and explicitly selected the ATI driver
  ati - ATI Mach8, Mach32, Mach 64, and Rage...

However it seems to reset back to vesa as well.

HI and have you tried to reconfigure you xorg with this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by doug-M on 2008-03-06
Just gave this a try:
sudo dpkg-reconfigure -phigh xserver-xorg

Then ctrl-alt-backspace to restart the X server but no change.
Good idea though.

---

