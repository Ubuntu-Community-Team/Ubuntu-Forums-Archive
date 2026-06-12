---
title: "Destroyed Graphic card?"
date: 2010-05-06
forum: Hardware
---

### Post by andreus on 2010-05-06
Some time ago my graphic on Ubuntu broke down. It looks like this:
```
http://img709.imageshack.us/img709/928/snc00047h.jpg
```

First time i repaired it by deleting gdm from /etc/rc2.d after this system boot into console and i could backup my data.After restart suddenly everythink was fine. So i put back gdm and then it broke down again. From this point i cant fix it anymore. Im booting to console and trying fix it..

after typing startx i get:
```

(**) May 04 19:12:57 NVIDIA(0): Enabling RENDER acceleration
(II) May 04 19:12:57 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 04 19:12:57 NVIDIA(0):     enabled.
(EE) May 04 19:12:57 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) May 04 19:12:57 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) May 04 19:12:57 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) May 04 19:12:57 NVIDIA(0):     README for additional information.
(EE) May 04 19:12:57 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```

dmesg:
```

[  105.561369] NVRM: RmInitAdapter failed! (0x26:0xffffffff:1076)
[  105.561375] NVRM: rm_init_adapter(0) failed

```

/proc/driver/nvidia/cards/0 :
```

Model: 		 GeForce 8600M GS
IRQ:   		 16
Video BIOS: 	 ??.??.??.??.??
Card Type: 	 PCI-E
DMA Size: 	 40 bits
DMA Mask: 	 0xffffffffff
Bus Location: 	 01.00.0

```

Any ideas how to fix it?
Isnt HW damaged? Because it looks like on the first picture in BIOS too. It looks like graphic card has some bad properties. I think its not burned, when system detect it correctly

P.S srry for my english

---

### Post by recluce on 2010-05-06
> **andreus said:**
> 
```

Model: 		 GeForce 8600M GS
IRQ:   		 16
Video BIOS: 	 ??.??.??.??.??
Card Type: 	 PCI-E
DMA Size: 	 40 bits
DMA Mask: 	 0xffffffffff
Bus Location: 	 01.00.0

```

Any ideas how to fix it?
Isnt HW damaged? Because it looks like on the first picture in BIOS too. It looks like graphic card has some bad properties. I think its not burned, when system detect it correctly

P.S srry for my english

If the BIOS display looks like the picture you posted, it is extremely likely that your graphics card is fried - Ubuntu and its drivers are not loaded at this point and thus cannot be responsible for the display errors. Your graphics chip is known to be victim to the "weak die" issues that NVidia had. Also, the question marks for the NVidia GPU BIOS version are not a good sign.

Use Google to check for possible warranty extensions by your notebook's manufacturer to cover that exact problem. For example: Dell extended the warranty of its notebooks by one year (in addition to whatever warranty you originally bought, only for this issue). So you might be covered under warranty without knowing it. If in doubt, call the manufacturer's service line.

BTW: Ubuntu has nothing to do with that failure, it will happen to all affected Nvidia GPUs - sooner or later.

---

### Post by andreus on 2010-05-06
I tried take it to service, but they wanted cca 300 Eur for repair. And that is too much.
How is possible it goes right after i remove gdm from rc2.d ? If Graphic card was fried it shouldnt boot in correct resolution and start normaly.

---

### Post by recluce on 2010-05-06
> **andreus said:**
> I tried take it to service, but they wanted cca 300 Eur for repair. And that is too much.
How is possible it goes right after i remove gdm from rc2.d ? If Graphic card was fried it shouldnt boot in correct resolution and start normaly.

What manufacturer? Did you call the manufacturer's hotline? This does not concern a retailer, they will charge you.

Regarding the point in time when this happened: coincidence

If you would google the problem, you would find out that the NVidia heat issues do start as intermittent problems (the notebook may run for a while without issues or only certain modes are affected) but will get worse more or less rapidly to the point of total failure.

Once again, if the problem is present at the BIOS screen, it cannot be Ubuntu or any other OS causing the problem.

---

