---
title: "Cannot get eGalax touchscreen calibrated."
date: 2011-05-04
forum: Hardware
---

### Post by lumix on 2011-05-04
I've serious put no less than 20 hours into this otherwise simple task.

Please, for the love of all holy tell me what I'm missing.

Netbook 10.10 on Acer Iconia W500 with eGalax touchscreen (1280x800)

I've installed the EETI drivers--not that I understand why, or what that has to do with D-WAV, or eGalax, or Wasabi-Icecream.  But if you spend 20 hours on this horrorshow you will end up doing the same thing.

I've run xinput_calibrator which doesn't really work, in that the 4th "touch" never seems to register, and the hourglass times out.

I've tried xinput set-prop using 0, x-resolution, 0, y-resolution.

But all I get is a pointer that goes in seemingly random directions, when it goes at all.

*Please help.*  I'd hate to have to revert this thing back to Windows.

---

### Post by lumix on 2011-05-05
I've now tried this with 10.10 out of the box--no additional drivers.  The touch screen works fine as a one-button mouse, but this still leaves out the convenience of being able to scroll the screen without pin-pointing the conventional scrollbar.  Not easy on a 10" screen, while using my finger. Which isn't to say I haven't found a use it.

---

### Post by lumix on 2011-05-07
Really...no one?  Nobody?

---

### Post by ArKay on 2011-05-19
> **lumix said:**
> Really...no one?  Nobody?

Indeed. I'm having the same problem under 11.04 with a Hoda technology / eGalax touch screen. No answers from anyone. :(

Oddly, if I run 11.04 as a live version from the SD card it works perfectly. Installing it makes it go whack-o. Same behavior your describing.

I posted a question in the same forum about it 2 days ago - no reply.

Doesn't -someone- have a bit of knowledge to share ? Even a snarky 'did you try this' comment ? Anything ?

---

### Post by lumix on 2011-05-19
Mine doesn't even work from the live-boot image--11.04 or 10.x.  Only as a a simple mouse--no gestures.

---

### Post by r00t3g on 2011-06-08
The same problem for me. The linux drivers from eGalax seem not to solve the problem. I guess, that Acer used some brand-new/modified eGalax touchscreen. 

lsusb shows the following about the touchscreen:
```
Bus 005 Device 002: ID 0eef:7302 D-WAV Scientific Co., Ltd
```

Such device does not even present in usb.ids, so I guess there's yet no support for it yet.

---

