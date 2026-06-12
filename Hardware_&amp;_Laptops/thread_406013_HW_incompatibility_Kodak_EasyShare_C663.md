---
title: "HW incompatibility: Kodak EasyShare C663"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by nevbear666 on 2007-04-10
Hello Everybody.

I have been running into minor problems while trying to access my new Digital Camera from within Ubuntu Edgy Eft.

A Few information on the Device:

Link to the Product detail page: [http://www.kodak.com/eknec/PageQuerier.jhtml?pq-locale=en_US&pq-path=8030](http://www.kodak.com/eknec/PageQuerier.jhtml?pq-locale=en_US&pq-path=8030)

**System base info:**
```
Linux whitestar 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
```

**lsusb output:**
```
Bus 002 Device 004: ID 040a:05a8 Kodak Co.
```

**error output while trying to "read" from the camera via f-spot imagery (i have tried gtkcam and digikam, they dont even know the camera...):**

Ein Fehler trat in der IO-Bibliothek auf (Â»Konnte das USB-GerÃ€t nicht
beanspruchenÂ«): Konnte Schnittstelle 0 nicht reservieren (Operation not
permitted). Stellen Sie sicher, dass kein
anderes Programm oder Kernelmodul (z.B. sdc2xx, stv680, spca50x) das
GerÃ€t verwendet und Sie
Lese- und Schreibrechte fÃŒr das GerÃ€t haben.

**or in english:**
```
"there has been an error: could not reserve interface 0 (operation not permitted). please take sure, that no other program or kernel module (e.g. sdc2xx, stv680, spca50x) is using the device and you have read and write permissions on the device.
```

**logfile entries that come from the cam look like this:**
```
[17251029.412000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[17251029.612000] usb 2-1: configuration #1 chosen from 1 choice
```

i did an update-usbids, still no go...

of course ive tried unloading and reloading all usb modules in use step by step, still didnt do.
sounds to me, like the device is a bit too new, but any help is highly appreciated...

btw. i tried to access the hardware databases in the sticky threads in this forum, cannot load the pages... (pages down?)

---

