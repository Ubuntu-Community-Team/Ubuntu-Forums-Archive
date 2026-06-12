---
title: "USB not recognised unless plugged in on boot"
date: 2010-10-26
forum: Hardware
---

### Post by samden on 2010-10-26
I have an IBM ThinkCentre M51 8142, dual booting Ubuntu 10.04 and Windows XP. Ubuntu will only recognise USB devices that are plugged in when the computer is booted. These devices display correctly in lsusb.

If a device is plugged in after boot it is not recognised, and is not visible in lsusb. If a device that was connected at boot is disconnected then plugged back in, it is no longer recognised either.

Windows recognises all devices with no problems.

This is identical to an issue noted at the below link in Debian Lenny:
[http://linux.derkeiler.com/Mailing-Lists/Debian/2008-09/msg00452.html]("http://linux.derkeiler.com/Mailing-Lists/Debian/2008-09/msg00452.html")

I have tried a number of different distros. Linux Mint 8, PCLinuxOS 2010.07 and SimplyMEPIS 8.5.01 all have the same issue on this machine.

The BIOS is updated to the latest version, and I have tried altering many different options in the BIOS related to USB support with no effect.

lsusb output with a flash drive connected on boot:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 0419:8002 Samsung Info. Systems America, Inc. SyncMaster 757DFX HID Device
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04f2:a13c Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0457:0151 Silicon Integrated Systems Corp. Super Flash 1GB / GXT  64MB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsusb output following removal and reattachment of the flash drive:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 0419:8002 Samsung Info. Systems America, Inc. SyncMaster 757DFX HID Device
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04f2:a13c Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Does anyone have any suggestions as to what could be causing this?

---

### Post by MatthiasG on 2011-04-05
Hello Samden,
sorry that Ido not have a answer, but need to tell you that I have the same problem with a thinkcentre M51 8144. I am using opensuse 11.1 / 11.4 (same problem in both versions).
I remember that the problem first appears since I flashed the Bios to the latest version.

Did you find a solution for the problem in the meantime? Would be interesting to hear. I decided to downgrade the BIOS in steps. I think I am now using version 2bj953a. There are three older versions provided by lenovo. If I get better results with any of those I will tell you.

Matthias

---

### Post by samden on 2011-04-05
I just tried every other distro I could until I gave up on the computer. I tried some old versions I thought had worked and found similar issues turning up too.

I've moved the wife to my laptop for now. This is running 9.04 still and because it's working I'm too nervous to upgrade in case something goes wrong with that computer too. The whole incident has really shaken my confidence in Linux unfortunately, especially when Windows runs perfectly on that machine. Sorry I can't offer any help.

---

### Post by Starfleet on 2011-04-05
Have you tried switching on Operating System Plug and Play in the BIOS to allow Linux to detect added extras after boot up rather than letting the BIOS do all the configuring? This should allow Linux to detect the USB stick when you plug it in. If your machine fails to boot after making this adjustment then go back into the BIOS ans switch it off again as that clearly won't be the answer.

---

### Post by samden on 2011-04-05
I tried every different BIOS option possible relating to this, with no improvement. However it is something anyone with a similar issue should try, as it could solve the problem for them.

---

### Post by Starfleet on 2011-04-06
The other thing I can think of is that your USB stick has a chipset in it that is just not recognised by Linux with OS PnP active. Clearly your BIOS recognises it in Windows and Linux after boot up with the stick in place. This has happened to me some while ago with a stick that had the, at the time, little known 'Chipsbank' microchip set in it.

---

### Post by samden on 2011-04-06
For me the problem is with any USB device (including keyboard or mouse), not just a single pen drive. I wish it was that simple, then I could just buy a different one!

---

### Post by MatthiasG on 2011-04-14
Hello Samden,
sorry for the delay. But I think I have good news. As I posted last time I had the same problem with opensuse on a Thinkcentre M51 8144. I managed to solve it just yesterday by downgrading the BIOS to this version : [http://download.lenovo.com/ibmdl/pub/pc/pccbbs/thinkcentre_bios/2bj950a.iso](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/thinkcentre_bios/2bj950a.iso)
I checked every step in between, but this was the first one that was working again. When you look at the version information it says that they changed some strage behaviour about USB. It seems that this change doesn't support the current Kernel versions ... I hope this could solve your problems also.
Matthias

---

### Post by GUBAZ on 2011-09-06
Thank you MathiasG, your solution worked for me on a newly purchased thinkcentre 8424. Five or so nights,  installing 11.04,then 10.10, then installed xp pro to find the same symptoms on that. Downgraded the Bios with your link and was up and running with a sweet install of 11.04 back. Who would have thought that an up to date bios was an issue.
Thank you again.

---

