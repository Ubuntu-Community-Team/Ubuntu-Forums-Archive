---
title: "RELEASE: Kernel for Acer Aspire One"
date: 2009-01-11
forum: Hardware
---

### Post by SlCKB0Y on 2009-01-11
[http://http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=9608]("http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=9608")

Hi All,

I have released a new version of my kernel for the Acer Aspire One.

As far as I know, this kernel should support almost all the hardware for the AAO, with the exception of the usual issues with the wifi kill switch. Some people also seem to be having issues with certain memory cards as well.

In addition to the stock hardware, I have added in support for various other stuff:

      Intel wireless cards

      Broadcom wireless support

      Bluetooth

      Extra filesystem support

      usb-serial for 3g USB modems

      Ath5k patches for the wifi LED


I am also releasing a seperate experimental kernel which contains support for TuxOnIce hibernation - Hopefully this will be faster than the default.

Included is ALSA 1.0.18a for fully functioning sound and mic, even after suspend/resume. To take advantage of this, you need to edit /etc/modprobe.d/alsa-base and add this line to the end of the file

```
options snd-hda-intel model=acer-aspire
```

I also had to play around with the mixer settings to get the mic to record at a usable volume.

This kernel will also install under the Ubuntu Netbook Remix image, but since it is LPIA, you will need to install with

```
sudo dpkg -i --force-architecture linux-image-2.6.28_Sickboy.Kuki.0.1_i386.deb
```

The files can be found at [http://www.ug.it.usyd.edu.au/~scole/](http://www.ug.it.usyd.edu.au/~scole/) and in a very short time, they will be up on [http://www.kuki.me/kernel](http://www.kuki.me/kernel)

Remember, use at your own risk, thanks for all the support and feedback - keep it coming :D

The next release will feature among other things Truecrypt support.

Stuart. a.k.a SlCKB0Y

---

### Post by pjalegria on 2009-01-22
Well, i see that you have release a new version, can you tell me what are the improve???

thanks

---

### Post by halovivek on 2009-01-22
will this work acer 5530 laptop also?

---

### Post by leifoelgaard on 2009-01-27
It works like a dream in my Acer ONE (150GB) with standard Ubuntu 8.10 + SICKBOY's kernel! I can't wait until next "release is ready. :D

Any dates?

Best regs.

Leif

---

### Post by herzzreh on 2009-01-30
Hmm... Does it really have usbserial compiled in it? modprobe usbserial says no such modules...

---

