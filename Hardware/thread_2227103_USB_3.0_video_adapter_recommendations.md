---
title: "USB 3.0 video adapter recommendations"
date: 2014-05-30
forum: Hardware
---

### Post by Nickolai_Leschov on 2014-05-30
I am thinking about buying a USB 3.0 video adapter ([like those]("http://www.amazon.com/s/ref=nb_sb_noss_1?url=search-alias%3Daps&field-keywords=usb%203.0%20video%20adapter&sprefix=usb+3%2Caps&rh=i%3Aaps%2Ck%3Ausb%203.0%20video%20adapter")) to use with my laptop, when it is docked in a docking station. Docking station only has one video output (DisplayPort), but maybe I could have a second one via a USB 3.0 video adapter.

How well (if at all) do those work in Ubuntu? What kind of performance can I expect? (I intend to use a second monitor for programming and office work, not very demanding applications video-performance-wise, but it would be nice to know what can I expect: is playing video not out of the question? Games?)

Any specific recommendations?

---

### Post by lukeiamyourfather on 2014-05-30
See the section about Linux compatibility on the website from the chipset manufacturer.

[http://www.displaylink.com/for-business/common_questions.php](http://www.displaylink.com/for-business/common_questions.php)

There's an open source driver for older adapters that run on USB 2.0 but the USB 3.0 adapters use a newer chipset that has no open source driver that I'm aware of. Proprietary drivers are provided only for Windows and Mac.

---

### Post by mcduck on 2014-05-30
You might also want to check what version your DisplayPort adapter is, as it might support multiple monitors by daisy-chaining them on the single connector. (For example my laptop supports up to 4 displays through the one DisplayPort connector it has)

---

### Post by lukeiamyourfather on 2014-06-02
> **mcduck said:**
> You might also want to check what version your DisplayPort adapter is, as it might support multiple monitors by daisy-chaining them on the single connector. (For example my laptop supports up to 4 displays through the one DisplayPort connector it has)

DisplayLink and DisplayPort are not the same. The original poster is asking about DisplayLink.

[http://en.wikipedia.org/wiki/DisplayLink](http://en.wikipedia.org/wiki/DisplayLink)
[http://en.wikipedia.org/wiki/DisplayPort](http://en.wikipedia.org/wiki/DisplayPort)

---

### Post by mcduck on 2014-06-02
> **lukeiamyourfather said:**
> DisplayLink and DisplayPort are not the same. The original poster is asking about DisplayLink.

[http://en.wikipedia.org/wiki/DisplayLink](http://en.wikipedia.org/wiki/DisplayLink)
[http://en.wikipedia.org/wiki/DisplayPort](http://en.wikipedia.org/wiki/DisplayPort)

From the original post:
> Docking station only has one video output (DisplayPort)...

...which is what I was referring to. Since there is DisplayPort available, using Multi-Stream Transport (part of DisplayPort 1.2 specification and supported on some devices) might be an option and wouldn't require purchasing anything.

---

### Post by lukeiamyourfather on 2014-06-03
> **mcduck said:**
> 
...which is what I was referring to. Since there is DisplayPort available, using Multi-Stream Transport (part of DisplayPort 1.2 specification and supported on some devices) might be an option and wouldn't require purchasing anything.

That makes sense. My bad.

---

