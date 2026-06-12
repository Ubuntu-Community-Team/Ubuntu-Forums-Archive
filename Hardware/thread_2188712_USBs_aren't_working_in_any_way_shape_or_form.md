---
title: "USBs aren't working in any way shape or form"
date: 2013-11-18
forum: Hardware
---

### Post by bitsandbytes001 on 2013-11-18
I am so sorry that I'm even here. I mean it. I just want to get a new computer, but that isn't going to happen any time soon. so here I am, struggling to make use out of the oldest working computer on this side of the globe. this laptop is at the very least five years old, and I had no choice but to use ubuntu, seeing as I had been forced to deal with a pirated version of windows XP for years. for a laptop that has been functioning reasonably well for half a decade, I'm kind of proud of its ability to stick around so long.  but with the switch to ubuntu I began to notice that nothing happens when I plug things into the USB ports. nothing at all.  if there really is no saving this computer then I'm fine with it, I suppose. I mean, there's a bunch of ways to dance around using USBs. but it would be great if they actually could work. I mean. I wouldn't be complaining.  I think switching to an older version would work as well, but I'm not sure how far I should go back and how terrible that would be to do.  so does anyone have any suggestions?  I'm kinda new at this whole linux thing, yes.

---

### Post by philinux on 2013-11-18
Sounds like a hardware failure.  Plug something in open a terminal ctrl alt t and use the command lsusb post back what it says.

Going older version won't make any difference.

---

### Post by bitsandbytes001 on 2013-11-18
well the USBs worked just fine on my old pirated version of windows, so I didn't think it was hardware, but I could be wrong.
I mean the thing is ancient.


unable to initialize libusb: -99

---

### Post by philinux on 2013-11-19
> **bitsandbytes001 said:**
> well the USBs worked just fine on my old pirated version of windows, so I didn't think it was hardware, but I could be wrong.
I mean the thing is ancient.


unable to initialize libusb: -99

The command you need is LSUSB but in small caps.

```
lsusb
```

This is the output from my laptop.
```
lsusb
Bus 002 Device 002: ID 04f2:b175 Chicony Electronics Co., Ltd 4-Port Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by bitsandbytes001 on 2013-11-19
yeah, that's what I did

lsusb
unable to initialize libusb: -99

that's all I get.

---

### Post by steeldriver on 2013-11-19
What version of Ubuntu are you running? it sounds like you don't have usb support compiled in to the kernel NOR loaded as a module - I can replicate that error on a Debian 'Wheezy' box by force unloading the usb module(s)

BTW that's running on a 2002 Thinkpad X30 so no, your computer is not 'old' :)

---

### Post by electrohandyman501 on 2013-11-19
By chance you aren't trying a 64bit version are you? Can you LiveCD boot a 32bit ver and see if your usb works?

---

### Post by bitsandbytes001 on 2013-11-19
AAAAH, yep that might be the problem.
I'm running a 64 bit one, instead of a 32 bit one.
I was so desperate to get away from the pirated windows I didn't even notice what I was downloading, so long as it booted.

the problem is my laptop can't burn to DVDs, so I have to steal my friend's computer in order to burn another one.

---

