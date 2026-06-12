---
title: "Problem detecting soundcard"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by MattVogt on 2005-08-20
I have just installed Ubuntu Warty on a Shuttle SN41G2 v2 box, and immediately upgraded to Hoary.  Most things seem to have worked correctly, except that the sound card has not been recognised.

The on-board sound is nVidia, based on a Realtek ACL650.  I have a notion that the correct module for this chip is snd_intel8x0, but after I manually modprobe this module, alsamixer still says 'alsamixer: function snd_ctl_open failed for default: No such device'

The box also has a Hauppauge TV-PVR 150, which may be complicating matters; I haven't yet tried to see if this device is working.

My lspci output (below) is noticeably lacking information compared to that found on this gentoo installation: 'http://www.linuxquestions.org/hcl/showproduct.php?product=1903&sort=8&cat=57&page=1'

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0080 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0084 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 0088 (rev a2)
0000:00:04.0 Bridge: nVidia Corporation: Unknown device 008c (rev a3)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008a (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation: Unknown device 008b (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 0085 (rev a3)
0000:00:0b.0 IDE interface: nVidia Corporation: Unknown device 008e (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:01:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)

Thanks for any assistance,
Matt

---

### Post by MattVogt on 2005-08-20
Well, I think I can rule out interference from the capture card, since the behaviour is identical with and without that device in the box...

---

### Post by MattVogt on 2005-08-23
FWIW, I updated to breezy and the audio is detected now.

---

