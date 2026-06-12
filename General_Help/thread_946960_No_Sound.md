---
title: "No Sound"
date: 2008-10-13
forum: General Help
---

### Post by skipsbro on 2008-10-13
Recently my sound just went out on my laptop (Dell Insipion 8600) Nothing comes out of the speakers or headphone jack, but if you try to open a media file, it plays like everything's fine, sans audio output. 

How can this be fixed?

---

### Post by Crafty Kisses on 2008-10-13
What are the results of this command?
```
lspci
```

---

### Post by skipsbro on 2008-10-13
```

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

```

---

### Post by parajuito on 2008-10-13
did you suspend/hibernate your computer before the sound disappeared?

---

### Post by WorldEvolution on 2008-10-14
Yea I Have no Sound At All. Can't Figure Out How To Get It To Work. It Wont Even Let Me To Connect To The Forums From It.

---

### Post by skipsbro on 2008-10-14
No I had not

---

### Post by parajuito on 2008-10-14
> **skipsbro said:**
> No I had not

try 

right click on the volume icon in the top panel. choose “Open Volume Control.”

In the Volume Control,  select VIA 8237 if it’s not selected.

select  Edit/Preferences in the menu, and on the dialog that pops up, checkmark “External Amplifier.”

now Volume Control should have a third tab, “Switches.” The only setting on that tab is “External Amplifier,” a checkbox.  uncheck the checkbox

---

### Post by skipsbro on 2008-10-14
Nothing seemed to happen

---

### Post by gitboxgreg on 2008-10-15
hmm i was looking for a thread about this t fix my problem, but i think i figured it out. I opened the volume control and changed the device to 3:Playback ALSA PCM on front:0 (ALC883 Analog) via DMA (PulseAudio Mixer) I have no idea if this helps you or if it is the same for you but it seemed to work for me. good luck!

---

