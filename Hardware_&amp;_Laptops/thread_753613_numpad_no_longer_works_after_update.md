---
title: "numpad no longer works after update"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by deathguppie on 2008-04-12
after a recent update to my hardy heron install my keyboard numpad no longer works.

system info 

Dell Dimension E520


>  deathguppie@planet-gameron:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)


/proc/bus/usb/devices.. does not exist..  /usr/src/linux-headers-2.6.24-16-generic/.config shows  CONFIG_PROC_FS=y

Installed items of interest
```
2008-04-12 11:19:04 status installed udev 117-8
2008-04-12 11:19:02 status installed linux-image-generic 2.6.24.16.18

```

I could try to revert, but I think I would break things without knowing all of the dependencies..

---

### Post by gnulogic on 2008-04-12
I am guessing you already tried num lock?

---

### Post by Albatross1953 on 2008-04-13
I'm having the same problem with an E520. Dell told me to flash the BIOS, which did nothing. I'm assuming the update that caused this had something to do with the chipset since that's where the keyboard driver is located, so it's not reversible.  Do you know if it can be reflashed with Intel software? I believe it is a G965 chipset.

---

### Post by Slotos on 2008-04-18
I've had the same issue after the last update. Turning off "Allow to control the pointer using the keyboard" in *System - Preferences - Keyboard - Mouse tab* helped. I haven't checked it in past and last time I opened this dialog (several days ago) it was unchecked. So I guess it could be enabled with that recent update.

---

### Post by suoko on 2008-04-24
same problem here with dell inspiron 1720

UPDATE:
SOLVED by turning off "Allow to control the pointer using the keyboard" in System - Preferences - Keyboard - Mouse tab 
as the post above suggested.

---

