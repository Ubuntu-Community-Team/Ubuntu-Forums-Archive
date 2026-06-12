---
title: "HP Hauppauge TV card with conexant cx23885"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by aldeby on 2007-09-13
Hi!
I am trying to use a TV express card on my laptop: Hauppauge WinTV 885 model 77001 branded HP 
which came with my HP Pavilion dv6000.
It has conexant cx23885 decoder and audio tuner. 
Video tuner is Xceive xc3028

lspci shows: 04:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)

$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-11-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

any idea?
Thank you very much for your support.

---

### Post by aldeby on 2007-09-13
This is just to add that I installed (make & sudo make install) v4l-dvb files from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) where I found reference about cx23885 support (ie here: [http://linuxtv.org/hg/v4l-dvb/rev/a3b27cb9ce3a](http://linuxtv.org/hg/v4l-dvb/rev/a3b27cb9ce3a) )

I don't know if I was supposed to do something else (in readme file there wasn't suggested anything more) however despite so the kernel doesn't auto load the correct drivers, and by hand I got that error. furthermore TvTime tells me that it cannot open capture device at  /dev/video0 also the express card led is always off.

---

### Post by aldeby on 2007-09-13
OK things are getting better now: issuing command ```
sudo modprobe cx23885
``` actually loads the driver for my tv card. Nonetheless Kaffeine says that *No DVB-Devices found. The DVB related functions will be hidden.* and TVtime as well.

How should I proceed from this point?

dmesg output sounds good:
```
[   28.553377] cx23885 driver version 0.0.1 loaded
[   28.553690] cx23885[0]: Your board isn't known (yet) to the driver.  You can
[   28.553691] cx23885[0]: try to pick one of the existing card configs via
[   28.553692] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   28.553693] cx23885[0]: version might help as well.
[   28.554028] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   28.554124] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   28.554206] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   28.554289] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   28.554372] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   28.554455] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   28.554550] CORE cx23885[0]: subsystem: 0070:7717, board: UNKNOWN/GENERIC [card=0,autodetected]
[   28.654715] cx23885[0]: i2c bus 0 registered
[   28.654825] cx23885[0]: i2c bus 1 registered
[   28.654916] cx23885[0]: i2c bus 2 registered
[   28.682883] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xf4000000

```
thanks for your support!

---

### Post by rsambuca on 2007-09-13
One thread is plenty next time.

---

### Post by aldeby on 2007-10-07
bump, any news out there?

---

