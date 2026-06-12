---
title: "Disable driver-less fingerprint reader?"
date: 2018-08-25
forum: Hardware
---

### Post by js211 on 2018-08-25
[COLOR=#242729][FONT=Arial]Currently running ubuntu 18.04.1, I have a laptop (Acer Swift 3) with an unsupported fingerprint reader:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]lsusb:[/FONT][/COLOR]
> Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1c7a:0570 LighTuning Technology Inc. 
Bus 001 Device 003: ID 04f2:b5c5 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=#242729][FONT=Arial]dmesg | grep "1c7a" :[/FONT][/COLOR]
> usb 1-9: New USB device found, idVendor=1c7a, idProduct=0570
[COLOR=#242729][FONT=Arial]powetop is saying that the device is 100% usage while lsusb -v is showing that it can draw up to 100mA.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is there any harm in leaving a driver-less device enabled or is there any way to cut power to it in order to stop it from running?

[/FONT][/COLOR]I have tried the bios but unfortunately Acer does not give that as an option

[COLOR=#242729][FONT=Arial]Thanks![/FONT][/COLOR]

---

### Post by Autodave on 2018-08-25
Go to Settings -> Session & Startup. You should be able to disable it there.

---

