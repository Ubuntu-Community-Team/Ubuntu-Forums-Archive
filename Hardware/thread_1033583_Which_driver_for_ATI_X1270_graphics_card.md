---
title: "Which driver for ATI X1270 graphics card?"
date: 2009-01-07
forum: Hardware
---

### Post by cdnaerogeek on 2009-01-07
I'm wondering if someone could help me decide which graphics driver to use with my video card.

I have a Gateway T-1625 laptop with integrated ATI Radeon X1270 graphics card that I converted from Vista to 64-bit Ubuntu 8.04. For a while, I was using a proprietary driver (fglrx - don't know the version, but it came from the Ubuntu repository) I recently switched back to the open source (ati) driver by following [_these instructions._]("https://help.ubuntu.com/community/RadeonDriver")

My big problem is compatibility with either a second monitor or an overhead projector through the VGA output. (I tried to give a presentation last month on my own laptop, and it didn't work, though that may also have been due to n00bishness on my part.) [_This site_]("https://wiki.ubuntu.com/X/RadeonXpress") suggests that external monitors shouldn't be a problem with the open source driver. I don't mind not having 3D eye candy provided the thing just works.

Just thought I'd see what the forum thinks.

I should also mention that I can't quite purge the proprietary driver off my system. I.e. Under System > Admin > Hardware Drivers, it still says that the proprietary driver is available (though disabled) even though I followed the community docs instructions to purge it.

---

### Post by cdnaerogeek on 2009-01-07
(bump) I'd really like an opinion on this from anyone who has used (or tried to use) similar hardware. I know ATI is not the best when in comes to Linux compatibility...

---

### Post by ELF_O8 on 2009-01-07
I have the exact same card in my laptop.
What you need to do is install Envy.
```
sudo apt-get install envyng-core envyng-gtk envyng-qt
```
After it's finished installing run
```
sudo envyng -g
```
Install the ATI driver automatically, then restart as it requests.
When you boot up again, there should be the ATI Catalyst Control Center (Yes, the one you're used to in Windows) in the Applications->Accessories tab.
You can configure all of the card properties from there.

---

### Post by cdnaerogeek on 2009-01-09
Thanks for that tip. The control center should make things much easier when interfacing with multiple screens!

---

### Post by dE_logics on 2009-04-02
[http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html](http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html)

Does this work? v1.2

---

