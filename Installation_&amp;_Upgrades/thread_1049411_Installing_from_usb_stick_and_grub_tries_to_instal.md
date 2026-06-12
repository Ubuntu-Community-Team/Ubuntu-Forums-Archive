---
title: "Installing from usb stick and grub tries to install on the usb stick"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by packet_ninja on 2009-01-24
I'm trying to install Ubuntu with a USB stick.

So, I boot off my USB stick that has the Ubuntu 8.10 netinstall image on it which I created with Unetbootin.

Now the problem I'm having is that the Linux install process finds the USB stick as the first hard drive (sda) so when it gets to the GRUB install part it automatically installs GRUB onto the USB stick instead of the internal hard drive.

Does anybody know of a way to get the USB stick to not show up as the first hard drive so GRUB can be installed properly?

Thanks in advance!

---

### Post by packet_ninja on 2009-01-25
I was able to fix my own problem.

I created a new USB stick with the Ubuntu 8.10 live desktop image instead of the netinstall and the install process worked flawlessly.

---

