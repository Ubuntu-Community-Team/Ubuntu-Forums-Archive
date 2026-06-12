---
title: "libgphoto2-2 udev rule prevents webcam usage"
date: 2012-11-08
forum: Hardware
---

### Post by StiltonSandwich on 2012-11-08
In the past few months, I can no longer use my Creative PC CAM 300 webcam (USB, 041e:400a). When I plug it in, no video device appears in /dev/ for it.

Poking around, I've discovered that this model of camera has an entry in /lib/udev/rules.d/40-libgphoto2-2.rules which seems to load some sort of photo downloading driver which takes precedence over the video functionality that I actually require. (This model of camera can, in theory, be used as a portable stills camera with very low image quality, but I only ever use it as a webcam.)

When I comment out the relevant line in /lib/udev/rules.d/40-libgphoto2-2.rules, the webcam works exactly as it should do. When I uncomment the line, it stops working again.

Commenting out a line in a udev rules file in /lib/udev/rules.d/ is not a proper solution, as it is liable to be overwritten during software updates.

Can anyone guide me towards a proper solution to this problem?

I do not care if I can no longer download photos from the camera. I only use it as a webcam.

I have tried copying the libgphoto2-2.rules file into a new file /etc/udev/rules.d/45-libgphoto2-2.rules and then commenting out the relevant line. This does not solve the problem.

I have tried fudging together a rule ```
SUBSYSTEM=="video4linux", BUS=="usb", ATTRS{idVendor}=="041e", ATTRS{idProduct}=="400a"
``` but I don't know enough about udev and it doesn't work.

Apparently I need libgphoto2-2 to satisfy dependencies for the likes of wine and libsane, so I can't just remove the package.

Thanks to anyone who can help.

---

