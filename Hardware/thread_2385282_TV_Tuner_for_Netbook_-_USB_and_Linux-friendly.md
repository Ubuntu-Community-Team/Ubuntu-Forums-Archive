---
title: "TV Tuner for Netbook - USB and Linux-friendly"
date: 2018-02-18
forum: Hardware
---

### Post by galacticstone on 2018-02-18
Does anyone know of a cheap USB TV-tuner that is Linux friendly?

Secondly, it must have built-in drivers or drivers I can download from the web - my laptop does not have a CD-ROM.

Thanks in advance!

MikeG

---

### Post by muddpup64 on 2018-02-18
You mean something like this?
[https://www.amazon.com/gp/product/B0036VO2BI/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0036VO2BI/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)


And here's how to make it work.
[http://tedfelix.com/linux/hauppauge-usb-live-2-linux.html](http://tedfelix.com/linux/hauppauge-usb-live-2-linux.html)

---

### Post by deadflowr on 2018-02-18
*Thread moved to **Hardware***

It'll depend on what kind of Tv viewing (over the air or cable) and where you live.
In the USA, where I am, over the air requires an ATSC supported device.
Other places have other requirements.
Cable typically  requires QAM support.

Look at linuxtv's hardware section to find listings of devices:
[https://www.linuxtv.org/wiki/index.php/Hardware_device_information]("https://www.linuxtv.org/wiki/index.php/Hardware_device_information")

---

### Post by galacticstone on 2018-02-18
> **deadflowr said:**
> *Thread moved to **Hardware***

It'll depend on what kind of Tv viewing (over the air or cable) and where you live.
In the USA, where I am, over the air requires an ATSC supported device.
Other places have other requirements.
Cable typically  requires QAM support.

Look at linuxtv's hardware section to find listings of devices:
[https://www.linuxtv.org/wiki/index.php/Hardware_device_information](https://www.linuxtv.org/wiki/index.php/Hardware_device_information)

I am looking for over the air.  :)

Thanks for this link! - [https://www.linuxtv.org/wiki/index.php/ATSC_USB_devices](https://www.linuxtv.org/wiki/index.php/ATSC_USB_devices)

---

### Post by galacticstone on 2018-02-18
> **muddpup64 said:**
> You mean something like this?
[https://www.amazon.com/gp/product/B0036VO2BI/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0036VO2BI/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)


And here's how to make it work.
[http://tedfelix.com/linux/hauppauge-usb-live-2-linux.html](http://tedfelix.com/linux/hauppauge-usb-live-2-linux.html)
Something along those lines. It doesn't need to record (and preferably cheaper). This is a lark, so I am trying to keep it to less than $20.  :)

---

### Post by muddpup64 on 2018-02-18
A bunch of the Hauppauge products come with Linux support right out of the box. [http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html)

It may be worth looking into some of their other stuff. I think they even produce a TV Tuner program for it. Good Luck!!:p





P.S. When you originally posting in Gaming and Leisure my mind instantly went to video game recording, lol.

Sorry about that.

---

### Post by User-007 on 2018-02-19
[https://www.aliexpress.com/item/1762667746/1762667746.html](https://www.aliexpress.com/item/1762667746/1762667746.html)

Works great in Linux. DVB-T out-of-the-box and DVB-T2 after copying firmware file (download [https://github.com/bas-t/dvbloopback/blob/master/tbs-tuner-firmwares_v1.0/dvb-demod-mn88473-01.fw](https://github.com/bas-t/dvbloopback/blob/master/tbs-tuner-firmwares_v1.0/dvb-demod-mn88473-01.fw)) to /lib/firmware.

---

