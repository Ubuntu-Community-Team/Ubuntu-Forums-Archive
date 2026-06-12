---
title: "Audigy 2 in ubuntu..."
date: 2005-02-04
forum: Hardware &amp; Laptops
---

### Post by sniperd on 2005-02-04
Hey everyone, im new to ubuntu but not linux.

Im having problems getting my Audigy 2 to work...
Ive tried multiple things but nothing seems to work, 
Ive even tried to recompile the kernel (2.6.10 Which failed, kernel panic and all)

Anyway, /dev/dsp doesnt even exist, and i dont know what else to try as far as configuring alsa goes, the emu10k1 drivers are loaded.

Whats the steps taken to get this card to work?

Thanks!

---

### Post by kleeman on 2005-02-05
Try this guide:

[http://alsa.opensrc.org/index.php?page=TroubleShooting](http://alsa.opensrc.org/index.php?page=TroubleShooting)

BTW I have Audigy 2 and it works REALLY well with Ubuntu providing you upgrade some of the alsa packages to 1.0.7. The effort it certainly worth it!

---

### Post by malegria on 2005-02-05
Have you tried downloading new drivers? Also, you may run into some problems compiling the drivers if you don't have the source to your kernel. So that when you run "./configure" it should look something like this:
```
./configure --with-kernel=/usr/src/your_kernel_source
``` 

Run into any troubles, hit me back.

In fact I'm using an AudigyLS but I know how frustrating it can be to get a sound card going.

---

### Post by sniperd on 2005-02-05
The only driver's i know about are the alsa ones, and ive tried with them endlessly.
Unless u know of some others i dont

---

### Post by malegria on 2005-02-05
The ALSA drivers are the very ones I am talking about. How have you tried them? Have you tried modprobing the sound module for your card? Did you get them from the ALSA site or through apt-get/synaptic?

---

### Post by kleeman on 2005-02-05
Did you try the alsa troubleshooter I listed above? If you don't follow anything maybe I can help...

---

### Post by sniperd on 2005-02-05
Ive tried all this stuff, 

Yes ive modprobed emu10k1 many times

Ive apt-get'd the alsa and also downloaded the packages.

I can re-download and compile them.

I did get sound working, but through [http://www.4front-tech.com/](http://www.4front-tech.com/) (OSS) which costs 50$ for a license, so i know for a *FACT* that  its not the system/bios config not letting it work.

---

### Post by malegria on 2005-02-06
It's sad that you had to shell out some money. I did that once, but I WAS able to get ALSA going when I thought only OSS would work. But I was wrong. I hope you get ALSA going because everyone considers OSS as deprecated. Also you CAN compile ALSA with OSS-Emulation thus rendering OSS unnecessary

---

