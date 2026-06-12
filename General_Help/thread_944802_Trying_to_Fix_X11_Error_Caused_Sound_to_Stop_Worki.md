---
title: "Trying to Fix X11 Error Caused Sound to Stop Working"
date: 2008-10-11
forum: General Help
---

### Post by Unanimated on 2008-10-11
```
sam@sam-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
00:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)
sam@sam-desktop:~$ 


```

When I was trying to fix something with Xorg, my sound suddenly stopped working. It started with an error, so I took the X11 folder from the LiveCD and overwrote my current folder. That caused the error message to go away, but not my sound to come back. Looking at xorg.conf shows that there is no speaker configured, but lspci clearly shows that there is a sound card enabled. I have PulseAudio up and running, everything shows that the sound should be playing - but it's not.

---

### Post by Unanimated on 2008-10-11
bump

---

