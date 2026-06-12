---
title: "Cant get 2 screens on Radeon 7000"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by Azyx on 2007-11-30
Hi.

I have Ubuntu Gutsy.
My fan on the gfx-card from nvidia stop vworking so I Change to an ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE], . The card have 2 vga- connectors and the problem is that I can not see the second vga or screen in Administration-->Screens and graphics. Screen and Grafic say that there only are one screen.

When I look in /etc/X11/xorg.conf and under Section "Device"

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:2:0:0"
        Driver          "radeon"
        Screen  0
        Option          "MergedFB"      "off"

When I trie to activate "Propretarian device" Gutsy says:

"Your hardware does not need any restricted drivers"

What can I do, so I get 2 screens?

/azyx

---

### Post by jcsteele on 2007-12-01
In my experience, the graphical utility to control dual screens and change graphic card drivers in gutsy is a little bit flawed, and has hosed my xorg on many occasions...

Check out [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

for me, to clone output to a projector I use 

$ xrandr --auto

Maybe this will help you...I am not exactly on what you were trying todo (clone output, extend desktop, etc.)

//jcs

---

### Post by Azyx on 2007-12-01
When I run on VESA failsafe i can clone my screen. But ut only allow 600x800 resolution.

/Azyx

---

