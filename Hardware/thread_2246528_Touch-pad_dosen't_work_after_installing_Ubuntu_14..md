---
title: "Touch-pad dosen't work after installing Ubuntu 14.04 [Dual boot with Windows 8]"
date: 2014-10-01
forum: Hardware
---

### Post by hallstrom-eric on 2014-10-01
[COLOR=#333333][FONT=UbuntuRegular]Hello! i'm new to Ubuntu and this forum, My problem is:

I just bought a new Acer Aspire V 15 Nitro computer with a pre-installed Windows 8. I installed Ubuntu so I can run dual-boot. Everything works fine now except my touch-pad that isn't working in Ubuntu but works fine when i boot into Windows. **And when i'm in Ubuntu my USB mouse works fine aswell.**

When I run
```
xinput --list
```[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
There is no touchpad:
[/FONT][/COLOR]```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;                                             id=11    [slave  pointer  (2)]

&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=15    [slave  pointer  (2)]

```[COLOR=#333333][FONT=UbuntuRegular]

[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I think my touchpad should be under ID 11.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In my system settings I can see the touch-pad and turn it on/off but nothing happens. I also installed Touch-pad indicator but nothing happens aswell.

When I run:

[/FONT][/COLOR]```

cat /var/log/Xorg.0.log | grep -i synaptics


    [     4.362] (**)    : Applying InputClass "enable synaptics SHMConfig"
    [     4.362] (II) LoadModule: "synaptics"
    [     4.362] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
    [     4.362] (II) Module synaptics: vendor="X.Org Foundation"
    [     4.362] (II) Using input driver 'synaptics' for '   '
    [     4.388] (--) synaptics:    : x-axis range 0 - 1236 (res 12)
    [     4.388] (--) synaptics:    : y-axis range 0 - 898 (res 12)
    [     4.388] (II) synaptics:    : device does not report pressure, will use                 touch data.
    [     4.388] (II) synaptics:    : device does not report finger width.
    [     4.388] (--) synaptics:    : buttons: left double triple
    [     4.388] (--) synaptics:    : Vendor 0x6cb Product 0x2970        
    [     4.388] (--) synaptics:    : invalid pressure range.  defaulting to 0 -         255
    [     4.388] (--) synaptics:    : invalid finger width range.  defaulting to 0         - 15
    [     4.388] (--) synaptics:    : touchpad found
    [     4.404] (**) synaptics:    : (accel) MinSpeed is now constant deceleration 2.5
    [     4.404] (**) synaptics:    : (accel) MaxSpeed is now 1.75
    [     4.404] (**) synaptics:    : (accel) AccelFactor is now 0.131
    [     4.404] (--) synaptics:    : touchpad found[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular]

Last row says touchpad found and after running:

[/FONT][/COLOR]```

grep -i touchpad /var/log/Xorg.0.log

  [     4.362] (**)    : Applying InputClass "evdev touchpad catchall"
      [     4.362] (**)    : Applying InputClass "touchpad catchall"
      [     4.388] (--) synaptics:    : touchpad found
      [     4.404] (II) XINPUT: Adding extended input device "   " (type: TOUCHPAD, id 12)
      [     4.404] (--) synaptics:    : touchpad found
      [     4.404] (**)    : Ignoring device from InputClass "touchpad ignore duplicates"
```[COLOR=#333333][FONT=UbuntuRegular]

But there is still nothing found under xinput -list.

Would love some guidance!

[/FONT][/COLOR]

---

### Post by giac-leonzi on 2014-11-17
Hi,
I had solve it pressing fn+F5, that is the short key to activate the touchpad in the old Toshiba computer, but when i was in the BIOS (F2).

so enter in the BIOS and press it.

---

