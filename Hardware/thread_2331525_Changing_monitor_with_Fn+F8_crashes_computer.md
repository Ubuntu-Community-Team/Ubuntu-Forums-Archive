---
title: "Changing monitor with Fn+F8 crashes computer"
date: 2016-07-22
forum: Hardware
---

### Post by leozinho29_eu on 2016-07-22
Hello

I have a Asus M2400N notebook and it has some problems that I believe that have to do with:
```
[   17.349521] asus_laptop: Asus Laptop Support version 0.42
[   17.349652] asus_laptop: Error calling CWAP(1)
[   17.349713] asus_laptop:   M2NE model detected
[   17.349717] asus_laptop: Error setting bluetooth status to 1
[   17.371719] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input13
```
From  all its LEDs, only the wireless indicator do not work well: it is  always on after boot and always off after suspend, regardless if the  wireless receiver is activated or not. This thing is pretty minor.

From all the buttons it has, the buttons to choose the energy governor do not work. I can use xbindkeys to solve.

However, the Fn+F1 do nothing (it should suspend the computer, the key image is a zzz) and Fn+F8 makes the computer freeze.

The  Fn+F8 combinations have the function to switch the image from the  notebook LCD to a monitor/projector and vice-versa. The connection is a  VGA one. When a monitor/projector is connected, I can use the Fn+F8  without fear because it will work fine, if I disconnect later and use  Fn+F8, the LCD screen blinks and returns, as there is no other option  than the notebook's LCD, but if I use Fn+F8 if I have connected no  monitor/projector before, then the system crashes.

The crash  screen consists in a black screen and the mouse pointer, which became  frozen. Nothing works after the error: music hang and stop, NumLock and  CapsLock stop, everything stop, it became non-functional. To turn off, I  have to keep pressed the power button.

This is worrisome because  this function is on the side of the mute and turn off LCD functions, so  accidentally using the wrong one is possible.

I tested with  different versions of (L)(X)(K)Ubuntu(Mate), and all of them cause a  crash under the cited condition which no monitor was connected before  the Fn+F8 usage. And I have found no logs too.

I tried to find files with logs, but I was unable to. The file Xorg.0.log.old would be the most likely to have something, but it had nothing.

Thank you.

---

