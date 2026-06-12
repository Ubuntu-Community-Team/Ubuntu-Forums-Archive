---
title: "First Linux Laptop - Problems with 4k External Display"
date: 2017-02-13
forum: Hardware
---

### Post by nixietube on 2017-02-13
Just purchased a Dell XPS 13 laptop with Ubuntu 16.04 preloaded.  The problem comes when I try to connect an external Dell P2715q (4k) display.  I'm using a USB-C to Display Port cable, and the display will work, but not at the correct resolution.  Here's the situation:

What works:
P2715q display at 2560x1440 with laptop at 3200x1800

What does not work:
P2715q display at 3840x2160 with laptop display off or at 3200x1800

The cable I'm using is a J5Create 4k x 2k @ 60Hz cable.

The P2715q display states that it will work up to 3840x2160 @ 60Hz.

I've updated my Ubuntu installation so that there are no updates left.  Can someone walk me through anything else I can do?

---

### Post by DuckHook on 2017-02-13
Hello nixietube and welcome to the forums.

[LIST=1]
[*]With monitor plugged in and powered up, please post output of:```
lspci -vk | grep -iA13 vga
``````
lsusb
``````
xrandr
``````
sudo apt update && sudo apt install read-edid && sudo get-edid | parse edid
```
[*]USB-C is a new-ish and still somewhat unconventional way to output video. Have you tried the HDMI port? If so, make sure to use HDMI 1.2 class cable. Cable quality is important. I've never heard of yours, but that means nothing because I have no knowledge of cable OEMs.
[*]Have you contacted Dell support? Since this is a new purchase and a developer laptop, they should be both willing and capable of helping you.
[/LIST]

---

### Post by nixietube on 2017-02-14
I figured it out.  With an HDMI cable into an Apple USB-C adapter, it works at 3840x2160 resolution, although it only works at 30 Hz (which still looks fine for my needs).  The short answer is don't buy the J5Create cable.

---

### Post by DuckHook on 2017-02-14
Glad you figured it out.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

Good Luck and Happy Ubuntu-ing!

---

