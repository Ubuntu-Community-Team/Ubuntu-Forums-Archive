---
title: "[ubuntu] Cannot connect to mobile network after upgrade to ubuntu 22.04 - Modem stuck"
date: 2022-07-22
forum: Hardware
---

### Post by honzanav on 2022-07-22
After upgrading to ubuntu 22.04 i couldn't find a way to connect to mobile network with my internal modem which worked under 21.10. Under Windows it works just fine.
 The system can dettect the device and it shows me option mobile networks in settings. When I choose Network and set, it shows error:

```
gdbus.error.org.freedesktop.modemmanager1.error.core.wrongstate: Cannot register modem: not yet enabled

```
or if I try to switch off the automatic option

```
gdbus.error.org.freedesktop.modemmanager1.error.core.wrongstate: Cannot scan networks: not enabled yet

```

When I try to connect via quick setting on the main panel, the mobile network icon is constantly switching between states 'Mobile network is off' and 'Mobile network is preparing' (I think. It is switching so fast it's hard to read).
 I succesfully deleted all existing mobile connections. But that didn't fix the problem.
The output of mmcli -m 0 is
```

  -----------------------------
  General  |              path: /org/freedesktop/ModemManager1/Modem/0
           |         device id: 3575bd4e67612908019cc8351876c89a2e1a4855
  -----------------------------
  Hardware |      manufacturer: Sierra Wireless, Incorporated
           |             model: Sierra Wireless EM7455 Qualcomm Snapdragon X7 LTE-A
           | firmware revision: SWI9X30C_02.33.03.00
           |    carrier config: default
           |      h/w revision: EM7455
           |         supported: gsm-umts, lte
           |           current: gsm-umts, lte
           |      equipment id: 014582008208853
  -----------------------------
  System   |            device: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2
           |           drivers: cdc_mbim
           |            plugin: sierra
           |      primary port: cdc-wdm0
           |             ports: cdc-wdm0 (mbim), wwan0 (net)
  -----------------------------
  Status   |    unlock retries: sim-pin2 (3)
           |             state: enabling
           |       power state: low
           |    signal quality: 0% (cached)
  -----------------------------
  Modes    |         supported: allowed: 3g; preferred: none
           |                    allowed: 4g; preferred: none
           |                    allowed: 3g, 4g; preferred: 4g
           |                    allowed: 3g, 4g; preferred: 3g
           |           current: allowed: 3g, 4g; preferred: 4g
  -----------------------------
  Bands    |         supported: utran-1, utran-3, utran-4, utran-5, utran-8, utran-2, 
           |                    eutran-1, eutran-2, eutran-3, eutran-4, eutran-5, eutran-7, eutran-8, 
           |                    eutran-12, eutran-13, eutran-20, eutran-25, eutran-26, eutran-41
           |           current: utran-1, utran-3, utran-4, utran-5, utran-8, utran-2, 
           |                    eutran-1, eutran-2, eutran-3, eutran-4, eutran-5, eutran-7, eutran-8, 
           |                    eutran-12, eutran-13, eutran-20, eutran-25, eutran-26, eutran-41
  -----------------------------
  IP       |         supported: ipv4, ipv6, ipv4v6
  -----------------------------
  3GPP     |              imei: 014582008208853
           |     enabled locks: fixed-dialing
  -----------------------------
  SIM      |  primary sim path: /org/freedesktop/ModemManager1/SIM/0

```

Does anyone know how to make it work as before the upgrade?

---

### Post by honzanav on 2022-08-07
Well. I don't know how reinstalling GRUB helped to fix the problem, but it did for some magical reason once. After next reboot, it is in the same state again.

---

### Post by honzanav on 2022-08-11
Problem had to be solved by doing:

> ln -sft /etc/ModemManager/fcc-unlock.d /usr/share/ModemManager/fcc-unlock.available.d/*

as suggested here: [https://askubuntu.com/questions/1419088/lte-modem-em7455-stop-working-after-ubuntu-22-04-upgrade]("http://Problem had to be solved by doing:  ln -sft /etc/ModemManager/fcc-unlock.d /usr/share/ModemManager/fcc-unlock.available.d/*  as suggested here: https://askubuntu.com/questions/1419088/lte-modem-em7455-stop-working-after-ubuntu-22-04-upgrade")

---

