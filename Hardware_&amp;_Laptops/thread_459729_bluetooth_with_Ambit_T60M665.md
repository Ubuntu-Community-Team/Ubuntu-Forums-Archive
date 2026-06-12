---
title: "bluetooth with Ambit T60M665?"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by slab on 2007-05-31
I have a Sony Vaio S150, running Ubuntu 7.04.

The S-series has Bluetooth as an option, but only for models from the UK-- it's possible to get the part directly from Sony (it [looks like this]("http://www.siliconpopculture.com/images/reviews/trbtupg/module.jpg") and gets inserted [at the white-bordered area in this picture]("http://www.notebookreview.com/assets/6299.jpg")), but it costs about $90, which is a bit pricey.

My roommate, however, has a dead Acer Ferrari 3200, from which I pulled out the builtin Bluetooth module. However, it's not the same sort of module, nor does it connect in the same place-- it's a combination Bluetooth/modem Mobile Daughter Card, an Ambit Microsystems T60M665. [It looks like this]("http://www.pchub.com/uph/photos/item/6327389292118750002_MBLTA.JPG"). My laptop has a MDC slot (it's on the underside of where the Sony Bluetooth module goes), occupied by a Conexant RD01-D480, which I've never used, so I swapped the two. After all, free Bluetooth is better than $90 Bluetooth, especially for a three-year-old laptop.

However, from here, I don't know how to get the Bluetooth device to work. Some googling around for installing Linux on a Ferrari 3200 seems to indicate that the Bluetooth device gets powered on and recognized as a USB device when one presses the Bluetooth button on the front panel; however, my Vaio lacks such a button, and hci_usb doesn't see it. ('hcitool dev' returns nothing). spicctrl has a --setbluetoothpower=1 setting, but I think that's only turning on the slot where the Sony Bluetooth adapter is supposed to be.

ALSA seems to be okay with the modem part of it with the snd_intel8x0m driver, recognizing the card (Intel 82801DB-ICH4 Modem, same as before) and the chip (Silicon Laboratory Si3036,8 rev 7)-- I haven't tried setting up a modem connection or anything to test it further.

Is there something here that I'm missing? Is this sort of reconfiguration even supposed to be possible? (I've never worked with MDC cards at all.)

[Edit: With the old board in, ALSA sees it as a chip 'Conexant id 23'; thus the laptop does seem to be able to accept different MDC cards. I just don't know how to enable the Bluetooth on the Ambit one.]

---

