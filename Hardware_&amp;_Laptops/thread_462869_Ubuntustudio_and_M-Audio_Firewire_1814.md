---
title: "Ubuntustudio and M-Audio Firewire 1814"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by KillerBob-it on 2007-06-03
Hello,
I have an _[M-Audio Firewire 1814]("http://www.m-audio.com/products/en_us/FireWire1814-main.html")_ external soundcard and I would like to use it in Ubuntustudio, but it seems to be not recognized. If I double click in the audio settings icon on the panel and then I click "file->change device" I have two choices:
- NVidia nForce3 (Alsa mixer)
- Analog Devices AD198B (OSS Mixer)

Both refer to the intenal sound card.
I'm using a laptop (_[HP nx9105]("http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?&lang=en&cc=us&prodTypeId=321957&prodSeriesId=405820&lang=en&cc=us")_).

Does anyone had success in configuring an M-Audio Firewire device?

---

### Post by crimsun on 2007-06-03
> **KillerBob-it said:**
> Does anyone had success in configuring an M-Audio Firewire device?

Firewire audio devices are not supported directly per se by ALSA.  You can use them with FFADO (formerly FreeBOB), however, and JACK.

---

### Post by CityofAsh on 2007-06-04
I had asked the same question to M-Audio Tech support about my M-Audio FW-410.

Theyr Response:

> M-Audio uses a 3rd-party Vendor for Unix support.

4Front Technologies develops and supports Unix drivers for our Revolution and Delta series of products.

The software is available for free evaluation and non-profit use but 4Front charges a fee for technical support and commercial use.

They can be found at the following web address:

[http://www.opensound.com](http://www.opensound.com)


There are also Linux drivers available for some of our products on this website:

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix)

Please note that M-Audio does not endorse the use of these drivers and we have no direct involvement in developing them.

I looked this up and they have not developed drivers as of yet.

Hopefully soon.
~City

---

### Post by KillerBob-it on 2007-06-05
Uh... this is what M-Audio tech support told me yesterday...
> Unfortunately we do not support Linux ourselves however you may find some
driver support either on the FreeBOB open source site or on the
[www.alsa-project.org](www.alsa-project.org) website

Regards

---

### Post by CityofAsh on 2007-06-05
Yeah unfortunatlly i doubt drivers will ever be developed for our midi interfaces. I dont believe theyr popular enough to develope drivers for them. M-Audio should develope them. 

~City

---

### Post by veiloctane on 2008-07-17
i wish i could get my firewire 1814 working in ubuntu but it would be cool if there was a windows driver emulator for linux. then we could just run windows drivers to make this work.


sory but just brainstorming i am a newbie and do not know what is required to emulate drivers.

---

