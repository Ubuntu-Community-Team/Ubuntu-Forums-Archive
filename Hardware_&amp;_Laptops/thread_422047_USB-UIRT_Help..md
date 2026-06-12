---
title: "USB-UIRT Help."
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by lonegeek on 2007-04-24
So I've got my mythtv setup working pretty good. Able to watch and record hdtv, although 1080i live tv is a bit skippy. 

But anyways...

I still have to get my dish box working, I have it setup and I can view through svideo ; however, the channel changer doesn't work.

I have an usb-uirt. It lights up when it receives commands. And when I first install it with lirc. It recieves commands, but then after trying anything after that I always get errors saying it cannot connect.

Does anyone know how to get this working or of a guide that explains?

Thanks, zach.

---

### Post by djsaltarelli on 2007-05-13
I just figured out how to do it in Ubuntu yesterday, so I wrote the documentation. Thankfully it was really easy to register and create a page!  The page is at:

[http://help.ubuntu.com/community/Lirc_USB-UIRT]("http://help.ubuntu.com/community/Lirc_USB-UIRT")

The biggest hurdle was realizing that the uirt2_raw driver was built in to the lirc package. I kept looking for this in the lirc-module-sources wondering why it didn't appear as an option like it does for the regular lirc tar file setup.sh routine. Eventually I realized that since the kernel has the ftdi_sio module, it's seen as a usb-serial device and the daemon part of lirc has the support for that already. Anyway, it's just a matter of putting the right magic words in /etc/lirc/hardware.conf and you're good to go.

/djsaltarelli

---

