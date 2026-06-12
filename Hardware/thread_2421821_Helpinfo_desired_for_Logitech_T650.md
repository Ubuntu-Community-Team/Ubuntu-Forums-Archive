---
title: "Help/info desired for Logitech T650"
date: 2019-06-27
forum: Hardware
---

### Post by nonenone123 on 2019-06-27
Hello,

First, some details about my system:

OS: Ubuntu 19.04
Kernel: 5.0.0-17-lowlatency
Unifying Receiver Firmware: RQR24.03_B0027 (reported by fwupdmgr)
T650 Firmware: RQM 41.00.B0033 (reported by Solaar)

Basic functionality works as expected. I can do the following:

  * Move mouse cursor (drag)
  * Tap to click (1 finger)
  * Right click (2 fingers)
  * Scroll up, down, left, and right (2 finger drag)

Here's where things start to get confusing. 
```

~ xinput list | grep -i t650
&#9116;   &#8627; Logitech Rechargeable Touchpad T650         id=16    [slave  pointer  (2)]

~ xinput get-button-map 16
1 2 3 4 5 6 7
```

In contrast to the above,[ this webpage indicates I should see a much larger map]("http://franklinstrube.com/blog/logitech-t650-wireless-touchpad-ubuntu/") when using xnput to query. I should be seeing 1-24 rather than just 1-7.

I tried setting it with xinput set-button-map 16 1 2 3 4 5 6 7 8 9... (you get the idea), but that did nothing.

I know the firmware for the T650 can only be updated via a windoze box. As soon as I unpacked it, I borrowed a friend's computer and attempted to do just that. I think it updated to the latest but... who really knows, right? Anyway, there's a good chance it's running the latest firmware.

So I'm curious to see the following. If you have a functional T650, can you show the results of a xinput get-button-map (your device id)?

If you know how or why I'm only seeing 1-7, can you point me in the right direction?

Thanks in advance

---

