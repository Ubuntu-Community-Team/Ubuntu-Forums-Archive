---
title: "Video Capture Device (USB 2828x) Not Detected?"
date: 2017-12-29
forum: Hardware
---

### Post by amihart on 2017-12-29
I recently purchased a composite/component to USB capture device and Linux does not seem to detect its existence at all.
I believe it uses [this]("http://empiatech.com/wp/2828x-usb-grabber/") chip, which eMPIA claims has Linux support on the site.

However, Ubuntu doesn't seem to detect it at all, when I launch OBS I don't see it as an option and the only "/dev/video"  device listed is video0 which is my webcam. 
I'm guessing there's simply no support because I found [this]("https://www.linuxtv.org/wiki/index.php/USB_2828x#Making_it_Work") web page that says "Only audio is working with snd-usb-audio.".

Is there just no support for this at all and am I out of luck? I have the Windows driver but I don't suppose there's any way to install that on Linux, is there?
Even if it's some experimental unofficial driver that's better than nothing...

I don't know much about this kinda stuff so if anyone could help me out that would be nice.

---

### Post by #&amp;thj^% on 2017-12-29
It would help if we knew what it was. Perhaps a Link to that Device would/might help.
And do you see anything related to your device with:
```
lsusb
```

---

### Post by amihart on 2017-12-29
> **1fallen said:**
> It would help if we knew what it was. Perhaps a Link to that Device would/might help.
And do you see anything related to your device with:
```
lsusb
```
The device is just called "Gamecap" but the chip in it is the one I linked to which is the same chip used in a few other devices. 
For lsusb the output for the device is
```
us 002 Device 003: ID eb1a:8285 eMPIA Technology, Inc.
```

If I do "lsusb -v" I get the same output for [that Wiki page I linked to](https://www.linuxtv.org/wiki/index.php/USB_2828x), so I'm pretty confident that Wiki article is the same driver I need and that the eMPIA link is the correct chip.

---

### Post by #&amp;thj^% on 2017-12-29
> **amihart said:**
> 
If I do "lsusb -v" I get the same output for [that Wiki page I linked to](https://www.linuxtv.org/wiki/index.php/USB_2828x), so I'm pretty confident that Wiki article is the same driver I need and that the eMPIA link is the correct chip.
Yep you was right. :(
Making it Work >>Only audio is working with **"snd-usb-audio"**. 
And I've seen no information for Video yet. (That dose not mean there isn't.) 
maybe someone wiser will have better news.
Good Luck

---

### Post by deadflowr on 2017-12-30
You can get a better idea of what's what by running dmesg against the driver like
```
dmesg | grep em28
```

---

