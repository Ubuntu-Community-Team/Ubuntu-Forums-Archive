---
title: "ubuntu in toshiba c650-110"
date: 2010-12-11
forum: Hardware
---

### Post by zwitter666 on 2010-12-11
Hello,

I have a toshiba c650-110, here are the specifications

Satellite C650-110
Part Number : PSC08E-00G001EN
Key Features
- Genuine Windows® 7 Home Premium 64-bit (pre-installed, Toshiba-HDD recovery)
- Intel® Celeron® Processor T3300
- DVD-RW SuperMulti drive (Double Layer)
- 4096 MB (2048 +2048) DDR2 RAM (800MHZ)
- 39.6cm (15.6") TruBrite® HD (1366 x 768) High Brightness display with LED backlight with 16:9 aspect ratio

I was wondering if ubuntu would run perfect in this laptop, if so, what should I install, desktop or netbook edition?

Thank you very much for your help.

Regards.

---

### Post by gameboy87 on 2011-01-22
I have Toshiba C650 Satellite Laptop. Installed 10.10 Ubuntu version. It's throwing Kernel exception errors ...Pls help ! Ubuntu + Toshiba ...What they are doing ?

---

### Post by daengbo on 2011-01-22
My gal was having the same problem with her Toshiba, and I ended up having to turn off APIC. The BIOS is buggy. Someone told me he decompiled the BIOS, figured out what was wrong, and patched his kernel, but that's beyond me.

---

### Post by dine874 on 2011-01-22
me too get the same problem in my lap wen i installed Ubuntu 10.10

So i installed Ubuntu 8 but auto eth0 is disappeared can any body help me out..

---

### Post by daengbo on 2011-01-22
I got the answer to this. Update the /etc/default/grub file to include "acpi=dsdt_copy" in the default Linux args line, then run "sudo update-grub2" -- bingo, no more corrupted dsdt table. No more kernel panics. Full ACPI (suspend, etc.).

---

### Post by zwitter666 on 2011-04-12
So, apparently it will be a lot of work to have my laptop working fine with Ubuntu, right?

---

### Post by daengbo on 2011-04-12
> **zwitter666 said:**
> So, apparently it will be a lot of work to have my laptop working fine with Ubuntu, right?

Not difficult at all. Please read the post above yours.

---

### Post by zwitter666 on 2011-04-13
Hi,

the thing is that I tried with the live CD but half the things didn't work, like the plug for the headset or the web cam, and besides that you are saying that there are problems with the BIOS, that's why I say that I will have to do some work to have everything working but that would not be a problem, my real question is if, even if I have to do a lot of stuff, is possible to have everything working or I would loose for example the web cam?

And another thing, should I use 32bit or 64bit version?

Thanks for your answers!

---

### Post by daengbo on 2011-04-13
My advice is to wait for 11.04 and try that. all my hw problems got solved.

---

### Post by zwitter666 on 2011-04-14
Hi, I think I will do that, because I installed yesterday 10.10 desktop 64bit and everything works but the web cam and the headphones and the internal mic, which means that I can use skype or nothing like that.

Do you think it would be better to install netbook edition?

Regards.

---

### Post by zwitter666 on 2011-04-15
hi! I was able to fix it.

I request help on the Technical Answer System on the Ubuntu site and the problem was with the asla-driver and now everything is working perfectly!

---

### Post by sudip313 on 2011-09-06
Plz write how u fix it...........

---

### Post by .... on 2011-09-06
Toshiba 650's often need this in /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=ideapad
```

---

