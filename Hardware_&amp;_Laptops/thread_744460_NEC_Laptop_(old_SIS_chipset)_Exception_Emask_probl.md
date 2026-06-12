---
title: "NEC Laptop (old SIS chipset) Exception Emask problem"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by SergeiFranco on 2008-04-03
I have installed kUbuntu 7.10 on an old NEC laptop, it is based on SIS chipset (everything is SIS, video, ATA, audio etc.) it does not have SATA (it is about 8years old) it does not have usb.
The biggest problem right now is booting is way too long, it hangs for about 2-3min, if I switch to tty1 it gives message like this:
```
[] ata1.00: exception Emask 0x0 Sact 0x0 SEtt 0x0 action 0x2 frozen
[] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096
```

then after displaying this message for about 2 - 3 times (and after another minute) it boots up fine, what I have noticed is when you remove "quiet" in boot option it also gives error on (timeout), and it happens while it tries to run @  UDMA100, once it error's out it switches to UDMA66 and boots fine.
Right now it uses libata, for old hardware libata is utter **** (I had problems before of not being able to enable DMA on PATA controller because of stupid SDx nomenclature, making hdparm useless), as I cannot force it to use UDMA66 (if I use force=udma66, it has no effect). This all happens just after usplash.

When I try with all_generic_ide option it does not come up with error, but boots up slowly (no wait this time), and every thing is slow.

Basically I have choice right now of either 5 min boot time and ~20Mb/s transfer rate (result from hdparm) or 3 min boot time and 3Mb/s transfer rate (some people have faster internet than that).

I have tried to recompile the kernel (from the master kernel thread), with new kernel it drops out after 5min wait to busy box (even if I have all_generic_ide)...

When I unplug the hdd and boot from LiveCD it does not give errors. With hdd in it used to give error with LiveCD.

I have not tried yet another hdd as I did not had laptop hdd at home, I will borrow one today and see what happens.

The laptop is pretty old:
NEC Versa Premium
800Mhz Celeron
256Mb RAM - 8Mb video shared
10Gb fujitsu hdd
SIS everything (apart from PCMCIA adapter which is TI).
Stupid laptop BIOS with no useful option apart from boot order and HDD detection.

I have checked the SMART parameters and have no errors or excessive load cycles.

This thing really frustrates me, I will probably end up installing XP on it (it has OEM XP licence sticker on  it anyway) if I will not manage to fix this issue...

Thank You very much.

Sergei.

---

### Post by SergeiFranco on 2008-06-08
Update: 8.04 works beautifully.

---

