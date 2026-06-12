---
title: "Laptop freezes on resume from suspend"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by rshields on 2008-01-23
That's it really. It doesn't happen every time, just when it's been suspended for the second time after reboot. Laptop is an Thinkpad X60s running Gutsy Gibbon.

```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)

```

Is there anything else I can post that would help?

---

### Post by rshields on 2008-01-23
Found this in dmesg:

```

[    7.152000] Attempting manual resume
[    7.152000] swsusp: Resume From Partition 8:3
[    7.152000] PM: Checking swsusp image.
[    7.152000] PM: Resume from disk failed.
[    7.780000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4060045205a]

```

Not a very helpful error message :( Also, I have only suspended to ram, not to disk.

---

### Post by henriquemaia on 2008-01-23
Try changing some of the options available on /etc/default/acpi-support

On my laptop, changing the 
SAVE_VBE_STATE=true 

and 
 
POST_VIDEO=true

to **false** did the trick. You can try other options available there if that doesn&#8217;t help.

---

### Post by rshields on 2008-01-24
Many thanks, that seems to have done the trick :):):)

---

### Post by rshields on 2008-02-25
Actually, this hasn't solved the problem. My laptop still freezes randomly about once in every 4 resumes from suspend.

Another weird problem is that I have to hit enter several times during suspend and resume, otherwise it just sits there with the suspend light flashing.

Any ideas?

Thanks :)

---

### Post by rshields on 2008-02-26
I have gone back to xfwm4 from compiz and this seems to have fixed the freezing during resume from suspend, fingers crossed... I still have to hit enter a few times during resume though.

EDIT: no, it's still freezing sometimes during resume

---

