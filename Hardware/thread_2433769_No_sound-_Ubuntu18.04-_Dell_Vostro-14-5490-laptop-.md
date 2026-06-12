---
title: "No sound- Ubuntu18.04- Dell Vostro-14-5490-laptop- Kernal 5.0.0-1032-oem-osp1"
date: 2019-12-25
forum: Hardware
---

### Post by gouravgargg on 2019-12-25
[COLOR=#333333][FONT=Ubuntu]My audio card is not working either driver is not there or card is not recognising.
I tried lot of forums answers but nothing worked.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]lspci -v[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]00:1f.3 Multimedia audio controller: Intel Corporation Device 02c8
 Subsystem: Dell Device 0959
 Flags: bus master, fast devsel, latency 64, IRQ 150
 Memory at c231c000 (64-bit, non-prefetchable) [size=16K]
 Memory at c2000000 (64-bit, non-prefetchable) [size=1M]
 Capabilities: <access denied>
 Kernel driver in use: sof-audio-pci
 Kernel modules: snd_hda_intel, sof_pci_dev[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]uname -a :
Linux ubuntuVostro5490 5.0.0-1032-oem-osp1 #36-Ubuntu SMP Wed Dec 4 11:44:12 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]It's showing dummy sound card.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Please assist on this. Neither I am able to use audio from any following apps : skype, google chrome , bluetooth[/FONT][/COLOR]

---

### Post by gouravgargg on 2019-12-25
On my laptop 4 kernal versions are installed 


5.0.0-1032-oem-osp1
5.0.0-1033-oem-osp1
5.0.0-37-generic
5.3.0-26-generic


5.0.0-1032-oem-osp1 & 5.0.0-1033-oem-osp1 are working for Wifi drivers but not working with audio drivers.
 
5.0.0-37-generic & 5.3.0-26-generic are working for audio drivers but not working with Wifi drivers. 


How can i resolve my issue ?

---

### Post by mörgæs on 2019-12-26
How does it work in a live boot of 19.10?

---

### Post by gouravgargg on 2019-12-26
[COLOR=#242729][FONT=Arial]Somehow i manage to install Wifi Driver on Kernal 5.0.0-37-generic[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]As of now problem has been solved :)[/FONT][/COLOR]

---

### Post by pedr0-r on 2020-01-08
> **gouravgargg said:**
> [COLOR=#242729][FONT=Arial]Somehow i manage to install Wifi Driver on Kernal 5.0.0-37-generic[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]As of now problem has been solved :)[/FONT][/COLOR]

How did you installed wifi driver on 5.0.0-37-generic?
I gave up using 5.0.0-1032-oem-osp1

---

