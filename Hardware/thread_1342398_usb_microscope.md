---
title: "usb microscope"
date: 2009-11-30
forum: Hardware
---

### Post by frncz on 2009-11-30
I bought an inexpensive usb microscope (a small web cam, with a magnifying lens and 4 LEDs to provide illumination). It is fun to use, especially to look at small insects (under Windows, when I still used it). In Ubuntu, uvc manages the webcam very well, but does not control the LEDs. I need the LEDs to get local illumination. Any suggestion? The manufacturer's website has some linux support in the form of a Fedora snxcam.ko file, but I don't know what to do with a .ko file in Ubuntu. Can the program be installed?

Thanks

Mike

---

### Post by skotos on 2009-11-30
It should be a kernel *module* to load with *modprobe/insmod*.

If it is downloadable in an rpm package, you might try to install *alien* and then convert/install the module.

HTH

---

### Post by 4ebees on 2009-12-07
> **frncz said:**
> I bought an inexpensive usb microscope (a small web cam, with a magnifying lens and 4 LEDs to provide illumination). It is fun to use, especially to look at small insects (under Windows, when I still used it). In Ubuntu, uvc manages the webcam very well, but does not control the LEDs. I need the LEDs to get local illumination. Any suggestion? The manufacturer's website has some linux support in the form of a Fedora snxcam.ko file, but I don't know what to do with a .ko file in Ubuntu. Can the program be installed?

Thanks

Mike

Hi Mike,

It's likely the device has a Microdia chip.

See the following pages:

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?msg=cs)

I got mine working easily.

If you have Karmic installed, which it would appear to me you have, you'll need to uninstall the existing drivers and install the ones described.

Get back to me if you have any problems. 

I've now installed the drivers in Ubuntu NBR 8.10, Jaunty 9.04 and Karmic 9.10 and the microscope works really well.

Additionally, would you mind posting the site for the manufacturer? I wouldn't mind having a look at what they say.

Thanks.

---

### Post by sofasurfer on 2009-12-22
I'm thinking about getting a USB microscope for my pc. Sounds like a lot of fun. I'd like to see some pictures of things that you all have looked at with your scope. And do these scope all have "above" illumination or "below" illumination?

---

### Post by 4ebees on 2009-12-28
> **sofasurfer said:**
> I'm thinking about getting a USB microscope for my pc. Sounds like a lot of fun. I'd like to see some pictures of things that you all have looked at with your scope. And do these scope all have "above" illumination or "below" illumination?

Hi,

I'll post some photos tomorrow (time permitting).

The 'scopes have LEDs arranged around the camera lense so the lighting is 'from above' in the sense I believe you mean.

---

### Post by 4ebees on 2010-01-20
> **sofasurfer said:**
> I'm thinking about getting a USB microscope for my pc. Sounds like a lot of fun. I'd like to see some pictures of things that you all have looked at with your scope. And do these scope all have "above" illumination or "below" illumination?

Crap!

Sorry for the long delay. Christmas etc intervened :)

Here are some images (see attachments)

Enjoy :)

---

### Post by sofasurfer on 2010-01-20
Thanks for the pics. Better late than never.

---

