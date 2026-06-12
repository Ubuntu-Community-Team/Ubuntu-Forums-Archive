---
title: "burning dvd ... i can't find any good answers."
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by dmizer on 2006-09-02
i've already created an iso for the movie i wish to burn.  but when i attempt to burn, i always get:
"/dev/hdc/; media is not recognized as recordable DVD: 10015"
"Fatal error at startup: wrong medium type."

here's the output in terminal when i run k3b:
```
$ gksudo k3b
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_japan_localhost_10
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open devicLaunched ok, pid = 7539

```
and my dvd burner is as follows:
```
$ dmesg | grep hdc
[17179577.620000]     ide1: BM-DMA at 0x10c8-0x10cf, BIOS settings: hdc:DMA, hdd:pio
[17179579.332000] hdc: TSSTcorpCD/DVDW TS-H652L, ATAPI CD/DVD-ROM drive
[17179580.124000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
```
according to the manufacture, this dvd burner can handle anything except dvd+rw +/-r and -rw is fine.  for testing purposes, i purchased a very high quality dvd-r disk.

it doesn't seem to mind burning cd's though.

---

### Post by dbd on 2006-09-03
I don't understand error messages, but I'm guessing the problem is probably that the DVD writer needs it's firmware updated so that it can handle those disks (I had the same problem with my DVD writer).

Just head over to your DVD writer's manufacturer and look around for the new firmware. Unfortunately these updates may only be for windows, and I wouldn't risk wine for something like this. So if you're not dual booting you'll need to use a friend's windows system, or just try some different disks. :(

Good luck

---

### Post by dmizer on 2006-09-03
first of all, i sincerely appreciate your reply.

no firmware updates available for my drive (it's brand new). in case you'd care to veryify for yourself, the drive is a samsung model TS-H652L:
[http://www.samsung.com/support/productsupport/download/index.aspx](http://www.samsung.com/support/productsupport/download/index.aspx)

per the manufacture, the following products are writable:
[LIST]
[*]DVD-R For General Ver 2.1
[*]DVD-RW Ver 1.1
[*]DVD+R(Dual) Basic Ver 1.11
[*]DVD-R(Dual)
[*]DVD+RW Basic Ver 1.2
[*]DVD-RAM
[/LIST]

the following disk types are recommended by the manufacture:
Taiyo-Yuden, TDK, MKM, Hitachi Maxell, Fuji Film, PVC, Panasonic, RiTEK, CMC, UNIFINO

my disk is a maxell dvd-r dual

---

