---
title: "Problem detecting a Wacom with xsetwacom"
date: 2018-01-29
forum: Hardware
---

### Post by avony on 2018-01-29
As stated i found myself at a loss when it come to my wacom device on ubuntu 

I did investigate a lot before asking and her is what i can say :
- wacom tablet work perfectly fine as soon as plugged 
- I can configure key and stylus with ease 
- xsetwacom and xinput don't seem to get it though 
**- my goal is to change to a 0.0 4500.6000 area (instead of a 10 000 x 12 000 smth)**

Out of the few things that i learn here is what i get 
```
lsusb | grep Wacom
```
return 
Bus 001 Device 003: ID 056a:030e Wacom Co., Ltd Intuos Pen Small (CTL480)

```
xinput list 

```
return 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:13                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:13                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-stylus:13                          id=9    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-eraser:13                          id=10    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-cursor:13                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pad:13                             id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:13                        id=8    [slave  keyboard (3)]

```
lsmod | grep wacom
```
wacom                 102400  0
hid                   118784  2 usbhid,wacom

I tried to uninstall and install again the package xserver-xorg-input-wacom
It worked perfectly fine but cannot see any device with xsetwacom yet 

I will be glad to have any insight on how I can solve this ^^ 
Thx in advance

---

