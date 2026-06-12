---
title: "No game sound with pulse pre-comand, startup sound stops to fast. Proper config???"
date: 2008-11-18
forum: General Help
---

### Post by Neobuntu on 2008-11-18
I'm on 8.10 Kubuntu and the startup sound gets muted after it starts. I can not find a fix. Is it a unresolved bug? Do I need to set-up Pulse; for specifically my Kubuntu 8.10 or not try Pulse, and set-up something else?

Should I just wait or what should I do?

---

### Post by Crafty Kisses on 2008-11-18
What are the results of this command?
```
lspci
```

---

### Post by Neobuntu on 2008-11-20
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:09.0 USB Controller: NEC Corporation USB (rev 43)
02:09.1 USB Controller: NEC Corporation USB (rev 43)
02:09.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
```

No motherboard sound card (It's on a PCI card)

---

### Post by Neobuntu on 2008-11-27
I reinstalled Kubuntu Intrepid as a clean install and upgraded. Still the start  sound gets chopped off.

---

