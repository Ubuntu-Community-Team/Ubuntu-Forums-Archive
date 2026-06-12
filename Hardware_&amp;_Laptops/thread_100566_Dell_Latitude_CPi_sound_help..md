---
title: "Dell Latitude CPi sound help."
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by saintdev on 2005-12-07
I'm not sure if this should go here, or in Video/Sound, but hopefully someone here can help. I have an old Dell Latitude CPi D266XT that I'm having trouble getting the sound working on. I know that this laptop uses a CS4237B chipset.

I've found various settings that others have used to get their card working, but none of them work. All I get when I try to modprobe is
> [93880.867848] CS4236+ soundcard not found or device busy

The most common setting I've found for the Latitude CPi is:
> index=0 port=0x530 cport=0x210 irq=5 dma1=0 dma2=1 mpu_port=0x330 isapnp=0 fm_port=0x388 mpu_irq=9

Now, by looking at lspci I've found:
> 0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
        Flags: medium devsel, IRQ 9
This is with acpi=off! Although, /proc/interrupts doesn't show anything on IRQ 9.
Does anyone have any idea how I could get this sound card working?

---

### Post by rmestre on 2006-04-30
did you ever figure this out, because I have the same problem and cannot find any way to get my sound to work either

---

### Post by saintdev on 2006-04-30
No I didn't :( Unfortunatly it was a friend's laptop, and he needed it back a few days later so I just had to re-install 98SE on it :mad: 

I got it to work with a few 2.4 kernel based distros, but not ubuntu or any 2.6 kernel.

---

### Post by jonthysell on 2006-07-12
I'm not sure if this'll work (I'm trying to setup Xubuntu 6.06 on my CPi now and I want sound to work)

[http://ubuntuforums.org/archive/index.php/t-22180.html](http://ubuntuforums.org/archive/index.php/t-22180.html)

It's from Warty, but who knows?

---

### Post by circut on 2006-07-14
I had an old CPi myself. The kernel drivers for whatever reason never worked for me. I ended up having to use OSS to get it working.

[http://www.opensound.com/oss.html](http://www.opensound.com/oss.html)

You need a license to use it. But crafty people find them. I'm still using my license, otherwise I would let you have it.

-circut

---

### Post by jonthysell on 2006-07-14
Here it is!

[http://www.ubuntuforums.org/showthread.php?t=90869](http://www.ubuntuforums.org/showthread.php?t=90869)

Followed the directions and ALSA works great! I finally have sound on my CPi D266XT running Xubuntu 6.06.

Edited to specify that it's using ALSA, not OSS.

---

### Post by andlinux21 on 2007-02-06
I have tried your guides and I cant get the sound to work but I am using a OEM version of Ubuntu 6.06 I like it but the sound just isnt working I got sound working before with Breezy

---

