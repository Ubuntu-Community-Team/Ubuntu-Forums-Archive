---
title: "Disabling USB 3.0 Support For a Device"
date: 2012-11-19
forum: Hardware
---

### Post by jamiejessup90 on 2012-11-19
I have a USB 2.0 Soundcard, the Presonus Audiobox 1818VSL. It works very well for me out of the box on my desktop, on a USB 2.0 port. However It does not work well on my laptop the Asus Zenbook Prime UX31A, which has exclusively USB 3.0 ports. This is due to incompatibility with the Ivy Bridge USB Controller. The sound card will play for a moment, stop, then resume.

Windows and Mac users are experiencing the same issues with Usb 3.0 ports with Ivy Bridge chipsets. I know that Windows users have found solutions by simply uninstalling the driver "Intel USB 3.0 eXtensible Host Controller" in the Control Panel.

I was wondering if there was a way to disable the usb 3.0 controller in Linux with something like a udev rule.

---

