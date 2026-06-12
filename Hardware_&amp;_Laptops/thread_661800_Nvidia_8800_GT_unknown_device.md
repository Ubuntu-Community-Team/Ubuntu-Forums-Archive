---
title: "Nvidia 8800 GT unknown device"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by Helmi on 2008-01-08
Hi,

i recently plugged a Nvidia 880GT w/ 1GB GRam into my machine and finally got it working with the newest envy.

Unfortunately lspci still lists it as unknown device:

```
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
```

Therefore i'm unable to get it running with nvclock to thrill down the fan which is currently running in 100% fullnoise mode.

Any idea?

Thanks!

---

### Post by Helmi on 2008-01-08
ok i managed to update pciids via

```
sudo update-pciids
```

unfortunately nvclock still says it doesn't support my card or better my card doesn't support fanspeed adjustments :(

---

### Post by Helmi on 2008-01-08
compiling the latest beta3 of nvclock did the job: [http://www.linuxhardware.org/nvclock/#download](http://www.linuxhardware.org/nvclock/#download)

sorry for talking to myself here ;)

---

### Post by jespdj on 2008-01-08
> **Helmi said:**
> sorry for talking to myself here ;)
Thanks for providing valuable information for other people who have this card. ;)

---

### Post by gdp77 on 2008-02-16
I have a 7900GTX + Ubuntu 7.10 32bit. I am going to swap it today with a 8800 GT. Any chance it will work?

---

### Post by macaholic on 2008-06-23
I'm still having this problem after updating pciids... (512mb instead of a gig) Any other suggestions?

---

