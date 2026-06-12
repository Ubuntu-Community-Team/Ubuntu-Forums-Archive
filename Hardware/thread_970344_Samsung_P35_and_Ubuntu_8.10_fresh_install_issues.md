---
title: "Samsung P35 and Ubuntu 8.10 fresh install issues"
date: 2008-11-04
forum: Hardware
---

### Post by pentel on 2008-11-04
Hi,
I'm running ubuntu 8.10 for two days on my laptop and I think it's better than the old one but I have some problems like the suspend feature

When I suspend my laptop and I try to get out of that state it appears some weird screen like the following one:

[[IMG]http://img513.imageshack.us/img513/6440/dscf2550dh3.th.jpg[/IMG]](http://img513.imageshack.us/my.php?image=dscf2550dh3.jpg)[[IMG]http://img513.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Another problem is that I cannot install the restricted driver for my mobility radeon 9700. It simply don't appear in the hardware drivers window like in the previous version.

And for finally, my laptop have a wireless switch(on/off) and when I it off, I cant turn on again the adapter. The only way to work with the wireless adapter again is to restart the system.

Thanks in Advance and keep the good work!;)

Ps:
My laptop specifications are:
Samsung P35
Ati Mobility Radeon 9700
Intel Pro Wireless 2200Bg

---

### Post by Talarion on 2009-02-19
I just found this rather old thread.

I have exactly the same hardware and the same problems as pentel.
I just switched from kubuntu to ubuntu. On kubuntu at least the hardware issues were total without difficulty. I just liked the ubuntu better now and wanted to switch. Now I have those hardware problems.

I don't worry too much about the suspend and the ati driver problem. I just don't use suspend and I can live with the 3D features that the open radeon driver gives me.
The Wireless problem is bothering me, though. Is there anybody who has fixed this?
the dmesg output corresponds to some bugs that are already listed, but are fairly old. I was hoping that they might be fixed by now!?

dmesg | grep ipw:
[   14.623245] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   14.623249] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.672443] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   14.786389] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   14.786453] firmware: requesting ipw2200-bss.fw
[   19.076667] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[ 1851.628062] ipw2200: Failed to send SSID: Command timed out.
[ 1852.628061] ipw2200: Failed to send CARD_DISABLE: Command timed out.


Also I notice that the CPU is running fairly hot. The fan is blowing constantly and the air is actually pretty warm...
This was not the case with kubuntu and is definitely no problem with windows...

I hope somebody can help me. Ubuntu started really well, but those issues are not too nice compared to the Kubuntu version.

Thanks a lot
Talarion

---

### Post by pentel on 2009-06-09
Hi,
I installed some time ago the Ubuntu 9.04 and I continue with the same problems but I found a way to suspend.
Using the package s2ram I can successfully suspend my laptop using the following line:
sudo s2ram -f -p -s

Hope it helps someone ;)

Bye

---

