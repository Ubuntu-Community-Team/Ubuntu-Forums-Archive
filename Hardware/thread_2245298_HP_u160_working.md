---
title: "HP u160 working?"
date: 2014-09-22
forum: Hardware
---

### Post by stkeg on 2014-09-22
anyone get this to work with any version of ubuntu? i've tried on 12.04 lts unsuccessfully.

wondering if it might work out of the box for some other version.

---

### Post by mastablasta on 2014-09-23
if it's a newer PC then you should use something with newer kernel. for starters 14.04

---

### Post by stkeg on 2014-09-25
yes, i'm trying to find out if it even works on the latest and greatest ubuntu (if any), otherwise it's a waste of time and not worth it for me to upgrade at this time.

---

### Post by xc3RnbFO8P on 2014-09-25
What is the output off :
> grep udl /etc/modprobe.d/blacklist-framebuffer.conf

---

### Post by Vladlenin5000 on 2014-09-26
The thing is you asked about a MONITOR and nobody knew until googling...

Your specialty monitor is in itself an external USB graphics card. HP supports Windows 7/8 only. There are no open source drivers.

Try selling it on eBay...




[http://h20621.www2.hp.com/video-gallery/us/en/45BCE112-5370-4F6F-8267-07B4078E4B43/r/video/](http://h20621.www2.hp.com/video-gallery/us/en/45BCE112-5370-4F6F-8267-07B4078E4B43/r/video/)

---

### Post by xc3RnbFO8P on 2014-09-26
Googling :)
[http://jochen.kirstaetter.name/blog/linux/using-aoc-usb-monitor-in-ubuntu-1304-displaylink-e1649fwu.html]("http://jochen.kirstaetter.name/blog/linux/using-aoc-usb-monitor-in-ubuntu-1304-displaylink-e1649fwu.html")

---

### Post by stkeg on 2014-09-26
i use this monitor with windows so i don't want to sell it.

yes i was looking for input from people that may have this monitor and may have used it successfully with ubuntu out of the box.

appreciate your input and trying to help though.

> **Vladlenin5000 said:**
> The thing is you asked about a MONITOR and nobody knew until googling...

Your specialty monitor is in itself an external USB graphics card. HP supports Windows 7/8 only. There are no open source drivers.

Try selling it on eBay...




[http://h20621.www2.hp.com/video-gallery/us/en/45BCE112-5370-4F6F-8267-07B4078E4B43/r/video/](http://h20621.www2.hp.com/video-gallery/us/en/45BCE112-5370-4F6F-8267-07B4078E4B43/r/video/)

---

### Post by stkeg on 2014-09-26
i found a lot of info online about usb monitors. read a lot of things before this post. tried somethings but it didn't work 100%.

not trying to find a way to hack this to work, already tried it. my question was more of yes or no.

> **Ringi said:**
> Googling :)
[http://jochen.kirstaetter.name/blog/linux/using-aoc-usb-monitor-in-ubuntu-1304-displaylink-e1649fwu.html](http://jochen.kirstaetter.name/blog/linux/using-aoc-usb-monitor-in-ubuntu-1304-displaylink-e1649fwu.html)

---

### Post by Vladlenin5000 on 2014-09-27
It there were known standards for this it should be easy but there aren't. Each manufacturer may use proprietary technology only accessible through the use of a proprietary driver.

---

