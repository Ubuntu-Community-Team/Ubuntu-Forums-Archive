---
title: "Juniper XT constantly operating at 33mhz after updating Xubuntu and open-source drive"
date: 2014-05-25
forum: Hardware
---

### Post by soldiertheinsanitywarrior on 2014-05-25
Okay, this might be slightly cheating, because I'm using the very-latest development version of the drivers, but this is a little strange. Keep in mind that I already know a solution that involved FGLRX, but I don't want to use FGLRX.

Anyways, as the title says, my Radeon HD 5770 is operating at a speed below the lowest power state. Namely, it's 117mhz below the lowest power state. Of course, I cannot play video games like this. Is there any way that, with these drivers, I can fix this?

---

### Post by Yellow Pasque on 2014-05-25
Try turning off radeom's dpm (card will run at full clock speed at all times):
```
echo "options radeon dpm=0" | sudo tee -a /etc/modprobe.d/radeon.conf
```

---

### Post by soldiertheinsanitywarrior on 2014-05-26
All that command did was echo "options radeon dpm=0". It didn't even write to the driver's configuration, as I found to be evident with lshw, the thing that I found out of this with.

Though, my problem is probably completely different from what I first thought. Upon closer investigation, lshw reports every device in my computer that has an independent clock rate as operating at 33mhz, not just the GPU.

I'd like to also highlight that the performance issue that drove me to find this had not been present with FGLRX (which I never want to use ever again) or Mesa 9.1.2, which came with Xubuntu 13.10, which was what this installation originally was. It has been converted to Xubuntu 14.04.

---

### Post by Yellow Pasque on 2014-05-26
Don't use lshw to check GPU clock speed. See: [http://www.botchco.com/agd5f/?p=57](http://www.botchco.com/agd5f/?p=57)

---

