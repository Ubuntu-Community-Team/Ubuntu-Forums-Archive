---
title: "sound card problem in ubuntu 7.10 on dell inspiron 1410"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by jaideep on 2008-01-29
Hi,
I just installed Ubuntu 7.10 from the CD. I am unable to get my sound working, I searched for the solution on internet and I have done following steps:
%sudo apt-get install module-assistant
%sudo m-a update
%sudo m-a prepare
%sudo m-a a-i alsa
I have Sigmatel audio card
All steps seemed to work without any problem and I could also find a module snd-hda-intel for the kernel (2.6.22-14-386), but still it's not working, It was working fine on Fedora 8.
Please help me in this matter. Any help is greatly appreciated.
- JD

PS: I am getting this in output of dmesg:
[   17.460000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/patch_sigmatel.c:1232: stac92xx_auto_fill_dac_nids: No available DAC for pin 0x0

---

