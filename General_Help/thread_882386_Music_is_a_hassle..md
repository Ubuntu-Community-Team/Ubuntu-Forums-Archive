---
title: "Music is a hassle."
date: 2008-08-06
forum: General Help
---

### Post by kaldor on 2008-08-06
Music is not working right on Gnome. I have tried with 3 different programs. Amarok, Rhythmbox, and Movie Player. Sometimes music works fine, other times it will not play at all and I have to relogin for things to work. How can I fix this?

---

### Post by Yuki_Nagato on 2008-08-06
Have you installed the "ubuntu-restricted-extras" package in the repositories?

This allows support for MP3 files and such.

---

### Post by Crafty Kisses on 2008-08-06
> **kaldor said:**
> Music is not working right on Gnome. I have tried with 3 different programs. Amarok, Rhythmbox, and Movie Player. Sometimes music works fine, other times it will not play at all and I have to relogin for things to work. How can I fix this?

Post the following output of:
```
lspci
```

---

### Post by kaldor on 2008-08-06
> **Codename said:**
> Post the following output of:
```
lspci
```

```
michael@Michael-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

And no, I did not install that package yet, tyring that now.

---

### Post by jerome1232 on 2008-08-06
Have you made any changes to pulse audio? When I set pulse audio to 6 channels (for 5.1 surround sound) alsa would incorrectly tell pulse that my card didn't support 6 channels and pulse audio would crash 20-40 minutes into the session. it caused my media players to hang and not play sound.

this is just a shot in the dark though.

---

### Post by kaldor on 2008-08-06
I installed the ubuntu restricted extras, and it worked fine. Suddenly, rythmbox froze and now the problem is back.

No, I didn't change anything with pulse audio.

---

### Post by SureStandar on 2008-08-09
try installing audacious or vlc:guitar:

---

