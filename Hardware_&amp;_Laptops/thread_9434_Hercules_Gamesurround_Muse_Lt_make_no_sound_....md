---
title: "Hercules Gamesurround Muse Lt make no sound ..."
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by sissou on 2004-12-28
...except when CD-Audio playing.

(*First, please Xcuse me for my bad writing in english...*)

My soundcard don't play any sound except with audio CD and many embedded sounds in web pages. I tried many things seen in this forum but never could make it work.

Here's what a **LSPCI** shows :

root@NEIGHBORHOOD:/home/vince # lspci
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (r ev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BA/CA/DB/EB/ER Hub interface to PCI Br idge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 12)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 12)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
0000:02:00.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:00.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:02:01.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev  86)
**0000:02:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10 )**

My soundcard is detected ;-) 

Does someone own that model of soundcard and has encountered the same problem ?

_More informations :_
**- /etc/modules.conf : **

" ...
 ### update-modules: start processing /etc/modutils/alsa-base
above snd-pcm snd-pcm-oss

### update-modules: end processing /etc/modutils/alsa-base
... "

**- /etc/modprobe.d/alsa-base :**

"install snd-pcm /sbin/modprobe --ignore-install snd-pcm && /sbin/modprobe snd-pcm-oss"

I would really appreciate if someone could give me a little help.
Thank you !

---

