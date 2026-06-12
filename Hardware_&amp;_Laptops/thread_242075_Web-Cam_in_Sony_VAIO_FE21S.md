---
title: "Web-Cam in Sony VAIO FE21S"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by alberto666 on 2006-08-23
Hi.

I cannot install my webcam in my VAIO FE21S, it is inside the monitor, and I think that is it recognised as an USB cam in Windows.

How can I install it?

It doesn't works with video for linux, I think.

Thanks

---

### Post by alberto666 on 2006-08-27
At least, there is any place where I can find information about installing webcam on linux or ubuntulinux and about that for laptops?

Thank you.

---

### Post by ranf on 2006-08-28
> **alberto666 said:**
> At least, there is any place where I can find information about installing webcam on linux or ubuntulinux and about that for laptops?

Thank you.

Try this site: [http://qbik.ch/usb/devices/](http://qbik.ch/usb/devices/)

---

### Post by Belyel on 2006-08-28
> **alberto666 said:**
> Hi.

I cannot install my webcam in my VAIO FE21S, it is inside the monitor, and I think that is it recognised as an USB cam in Windows.

How can I install it?

It doesn't works with video for linux, I think.

Thanks

> **alberto666 said:**
> At least, there is any place where I can find information about installing webcam on linux or ubuntulinux and about that for laptops?

Thank you.

You can see if the camera is recognized as a USB device in Linux by using the command ***lsusb*** in a terminal.  The command will also give you the vendor and product IDs in the form of the paired four-digit codes ****:****, where the vendor code is the first four digits.  The vendor name will be the furthest right piece of information on each line.  With that information you can look at the [spca5xx module site]("http://mxhaard.free.fr/spca5xx.html") or the [Linux UVC site]("http://linux-uvc.berlios.de/") to see if your camera is supported.  Use the search function in the top right corner of the page to find threads on how to install either or both of those modules.  A google search is also a good way to find more info on either utility.

---

### Post by KaMZaTa on 2006-09-28
I've a Sony Vaio FE-21M... how can I do? (Ubuntu Edgy knot)

---

### Post by Cyfr on 2007-04-19
I have this laptop and as of Feisty Fawn update the webcam works out of the box.

However the image is really crappy I think this might be due to hue and things, how can I change them?

---

### Post by alberto666 on 2007-04-23
I wasn't so worried about that, I just wanted the camera working.

That is possible, I saw in some place how to do it, but finally I didn't do it. But I think the information was somewhere in the driver page.

If you have success, tell us ;)

---

