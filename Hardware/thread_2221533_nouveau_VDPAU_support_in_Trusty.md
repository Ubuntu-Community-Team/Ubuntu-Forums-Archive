---
title: "nouveau VDPAU support in Trusty"
date: 2014-05-02
forum: Hardware
---

### Post by elventear on 2014-05-02
I have GeForce 8300 and as far as I can read this page:

[http://nouveau.freedesktop.org/wiki/VideoAcceleration/](http://nouveau.freedesktop.org/wiki/VideoAcceleration/)

some VDPAU decoding acceleration should be supported by the nouveau drivers for my card.

I have been testing and I haven't been able to make it work. Is there something that needs to be done on Trusty to enable those features?

---

### Post by bazsound on 2014-05-02
Install the restricted drivers. Its worth it.

I have an old nvidia geforce gt610. with the right restricted drivers i get vpdau showing up in nvidia settings and i assume its being used in xbmc as the vdpau setting is enabled and not causing issues.

unless your card is not supported yet i wouldnt think the open source driver would for that level of hardware acceleration.

opensource driver is always behind the propriety driver. If your card is supported, id install the propriety driver

---

### Post by Yellow Pasque on 2014-05-02
You have to extract the blob's firmware (it worked for me on an 8400GS): [http://nouveau.freedesktop.org/wiki/VideoAcceleration/](http://nouveau.freedesktop.org/wiki/VideoAcceleration/)

Just copy/paste the commands because you need to use version 325.15 for that extraction script to work.

---

### Post by martijntje on 2014-05-04
I am also having issues getting VDPAU to work using the nouveau driver. I have a laptop with a GF119M chipset, which falls under the VP5 category according to the nouveau page. After installing libvdpau1, mesa-vdpau-drivers and nouveau-firmware packages vdpauinfo recognized the card, but does not show any decoder capabilities.

After searching I found that there is a bug in the mesa driver for this particular class of cards: [https://bugs.freedesktop.org/show_bug.cgi?id=77102](https://bugs.freedesktop.org/show_bug.cgi?id=77102), so I downloaded the source for the mesa vdpau driver and applied the patch. After rebuilding initramfs and rebooting I can confirm there are no error messages in the kernel log about loading the device firmware, though no decoder capabilities show up still.

I'm at a loss now, I have no idea why it would not report any decoder capabilities.

---

### Post by Yellow Pasque on 2014-05-04
> **martijntje said:**
> nouveau-firmware package

That's not the only firmware you need. Follow the directions in my previous post.

---

### Post by martijntje on 2014-05-05
Aha! Silly me assumed that the nouveau-firmware package would install the necessary firmware. Extracting and copying the firmware files from the nvidia driver does work and vdpauinfo reports the necessary decoder capabilities now.

---

