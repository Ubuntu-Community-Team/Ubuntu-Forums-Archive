---
title: "How to log in with a fingerprint ?"
date: 2022-09-18
forum: Hardware
---

### Post by georgesgiralt on 2022-09-18
Hello !
My Lenovo ThinkBook 15 G2 ITL came with a fingerprint scanner (Device 005: ID 04f3:0c4b Elan Microelectronics Corp. ELAN:Fingerprint). It seems to be supported according to [https://fprint.freedesktop.org/supported-devices.html](https://fprint.freedesktop.org/supported-devices.html).
I've just upgraded to Ubuntu Jammy 22.04.1 LTS and thought I could, now, use a finger print to log in. 
Alas, I can't make it working :
```
fprintd-enroll <user> 
Impossible to enroll: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available

```
I can't find how to check if the sensor is recognized and if the fprint system is working or not.
So all your help will be appreciated ! 
Many thanks in advance for this !

---

### Post by #&amp;thj^% on 2022-09-18
> **georgesgiralt said:**
> 

I can't find how to check if the sensor is recognized and if the fprint system is working or not.
So all your help will be appreciated ! 
Many thanks in advance for this !

Have a look in lsusb:
```
lsusb
```

check if this is installed
```
apt policy libpam-fprintd
```
try again after and show any errors please.

---

### Post by georgesgiralt on 2022-09-18
Ok, here are the answer : 
```
lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 04f3:0c4b Elan Microelectronics Corp. ELAN:Fingerprint
Bus 003 Device 003: ID 174f:2459 Syntek Integrated Camera
Bus 003 Device 008: ID 0c76:153f JMTek, LLC. USB PnP Audio Device
Bus 003 Device 006: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 004: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. Hub
Bus 003 Device 007: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 006: ID 05e3:0749 Genesys Logic, Inc. SD Card Reader and Writer
Bus 002 Device 005: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 002 Device 004: ID 05e3:0626 Genesys Logic, Inc. USB3.1 Hub
Bus 002 Device 003: ID 174c:55aa ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge, ASM1153E SATA 6Gb/s bridge
Bus 002 Device 002: ID 05e3:0620 Genesys Logic, Inc. USB3.2 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And : ```

apt policy libpam-fprintd
libpam-fprintd:
  Installé*: 1.94.2-1ubuntu0.22.04.1
  Candidat*: 1.94.2-1ubuntu0.22.04.1
 Table de version*:
 *** 1.94.2-1ubuntu0.22.04.1 500
        500 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.94.2-1 500
        500 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages

```


But it still does not work ;-)
And I've no errors. The finger print tab does not show in the users tab....

---

### Post by #&amp;thj^% on 2022-09-18
> **georgesgiralt said:**
> 

But it still does not work ;-)
And I've no errors. The finger print tab does not show in the users tab....
Well the good news is >>> your Sound is now working....;)
Now the Bad News: [https://github.com/uunicorn/python-validity/issues/105](https://github.com/uunicorn/python-validity/issues/105)
Yours "Elan Microelectronics Corp. ELAN:Fingerprint" ATM dose not have a driver yet
EDIT: Wait I'm not done yet, I wonder how close it is to being Beta? Give this a try:
```
sudo apt install fprintd libpam-fprintd
fprintd-enroll
sudo pam-auth-update --enable fprintd
```
I wouldn't rely on this as stable.

---

### Post by georgesgiralt on 2022-09-19
Well, according to this : [https://fprint.freedesktop.org/supported-devices.html](https://fprint.freedesktop.org/supported-devices.html) my device is supported but in dev branch...
So maybe it will be sometime in the future when the library gets updated...

---

### Post by #&amp;thj^% on 2022-09-19
> **georgesgiralt said:**
> Well, according to this : [https://fprint.freedesktop.org/supported-devices.html](https://fprint.freedesktop.org/supported-devices.html) my device is supported but in dev branch...
So maybe it will be sometime in the future when the library gets updated...

Good Detective work. ;)
I'm betting sooner, possibly with a stable kernel version 5.19 at some point.

---

