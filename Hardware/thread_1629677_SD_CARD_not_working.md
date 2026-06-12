---
title: "SD CARD not working"
date: 2010-11-24
forum: Hardware
---

### Post by lavezarez on 2010-11-24
My laptop (LENOVO 3000 G400) has a built-in card reader but Ubuntu (10.10) does not detect my SD card.

The SD card works fine in my other laptop with WINDOWS VISTA.

When I issue lspci, I don't see any mass storage entries:
```
lavezarez@lavez-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)


```

---

### Post by nasul on 2010-11-24
I think there could be some problems with the drivers.

---

### Post by IcarusR on 2010-11-24
Do you know the make & chipset of the card reader ? Mabe able to find from windows. Then you can google for it.
It may not be supported under linux (ubuntu) due to lack of available chipset specs from the manuacturer.

---

### Post by lavezarez on 2010-11-24
Today, the SDCARD was already in the card reader slot when I boot up Ubuntu.
It did not automount or was detected.  But after a few minutes Nautilus popped-up with the contents of the SDCARD, and now I can access.  What is this about?  Why is there a delay?

I also followed instructions yesterday on a blog post [here]("http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/") modifying the /etc/modules file and inserted a line with this: **tifm_sd**
but when I tested it, still no fix.

My dmesg output today (after the sdcard was seen by nautilus):
```
[   22.237240] Skipping EDID probe due to cached edid
[   22.264235] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   22.266078] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   22.325684] ppdev: user-space parallel port driver
[   22.335698] sd 2:0:0:0: [sdb] Attached SCSI removable disk

```then a bit further . . . 
```
[  522.235263] sd 2:0:0:0: [sdb] 3862528 512-byte logical blocks: (1.97 GB/1.84 GiB)
[  522.236098] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  522.237853] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  522.237866]  sdb: sdb1
[  820.818025] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
```
lspci output is the same as my first post.

I wish I could just simply make this work as easily as in Windows.  Getting frustrated.
Any help, much appreciated!

---

### Post by typhoon_tip on 2010-11-24
You need to find the exact right driver or it is working improperly with several kind of different behaviour.

For your LENOVO, have a look at Think Wiki:
[http://www.thinkwiki.org/wiki/Hardware_Specifications](http://www.thinkwiki.org/wiki/Hardware_Specifications)

Since your model is not listed (is it old or too new ?) you need to find the exact model of reader that you have, and then find the fix suggested by Think Wiki for other laptops (possibly the G series).

There are many types: 5 in 1, 7 in 1 (from Ricoh). For example, mine was 7 in 1 (PCMCIA and Firewire in the same device) so it wasn't working with the 5 in 1 driver, obviously.

Try also an lsusb output, maybe your card is not attached to the PCI bus.

---

