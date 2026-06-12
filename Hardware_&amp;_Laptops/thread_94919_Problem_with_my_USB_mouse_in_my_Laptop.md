---
title: "Problem with my USB mouse in my Laptop"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by cazz on 2005-11-25
I have a a HP Pavilion  zv5000 and a touchpad and that works fine.
The mouse is a Logitech Pilot Optical mouse

Now I like to have a USB mouse on the laptop but that is the problem, nothing happend when I move the mouse.
Is no light either.

I try this guide [http://ubuntuforums.org/showthread.php?t=4357](http://ubuntuforums.org/showthread.php?t=4357) but when I write *lsusb* it say

```
001.001: 0000:0000 Not a Logitech device
```

*lsusb*
```
Bus 001 Device 001: ID 0000:0000
```

*dmesg*
```
4294801.374000] usb 1-3: USB disconnect, address 3
```

The USB work fine because I use my mp3 player to see if it works and it did.

*cat /etc/modules*
```
lp
mousedev
psmouse
nvidia
```

I have no idea how to fix this problem.

---

### Post by cazz on 2006-02-12
Still same problem but now I have problem with my camera so I can't move any picture from my camera to Ubuntu

I have seen something at startup that something is problem with USB

---

### Post by joao.vitor on 2006-03-04
I have the same Laptop and the same problems.
When you figure out how to have the usb mouse recognized please post here. ;) 

Do you figured out how to make the touchscreen roll pages up and down?

---

