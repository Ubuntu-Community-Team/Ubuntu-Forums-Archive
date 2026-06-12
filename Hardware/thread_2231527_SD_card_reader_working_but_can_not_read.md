---
title: "SD card reader working but can not read"
date: 2014-06-26
forum: Hardware
---

### Post by tridephysique on 2014-06-26
Hi,

I am using UbuntuGnome in an Acer Aspire 4745G. The laptop has a built-in SD card reader. The card reader is working but it doesn't read anything.
I tried a microSD card with an adapter and Disks (default disks manager in UbuntuGnome) said "No media". This is not because the microSD card because it works when I use an usb card reader.
How can I make the card reader work properly?
[ATTACH=CONFIG]254254[/ATTACH]
Thanks

---

### Post by tgalati4 on 2014-06-26
Open a terminal.  Plug in the microSD card.  Post the output of:  (just the SD card stuff)

```
dmesg | tail -50
```

---

### Post by tridephysique on 2014-06-29
> **tgalati4 said:**
> Open a terminal.  Plug in the microSD card.  Post the output of:  (just the SD card stuff)

```
dmesg | tail -50
```

Here, it is. Thank for reply:
```

[  312.862598] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[  312.956268] usb 1-1.5: New USB device found, idVendor=058f, idProduct=6366
[  312.956278] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  312.956283] usb 1-1.5: Product: Mass Storage Device
[  312.956288] usb 1-1.5: Manufacturer: Generic
[  312.956292] usb 1-1.5: SerialNumber: 058F63666433
[  313.008654] usb-storage 1-1.5:1.0: USB Mass Storage device detected
[  313.009692] scsi4 : usb-storage 1-1.5:1.0
[  313.009844] usbcore: registered new interface driver usb-storage
[  313.051535] keucr: module is from the staging directory, the quality is unknown, you have been warned.
[  313.052089] usbcore: registered new interface driver eucr
[  314.136193] scsi 4:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[  314.136670] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  314.515749] sd 4:0:0:0: [sdb] Attached SCSI removable disk



```

---

### Post by tgalati4 on 2014-06-29
I would try a variety of SD card types and sizes and stick with those that can be read correctly.  

On this Acer laptop, I have a Texas Instruments 5-1 reader:

> tgalati4@Mint14-Extensa ~ $ lspci | grep Mass
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/M

Putting in a card results in a short message:

> [136886.020718] mmc1: new SDHC card at address e624
[136886.024092] mmcblk0: mmc1:e624 SU16G 14.8 GiB 


So it appears that a generic driver is being loaded on your laptop with limited functionality.

---

### Post by tridephysique on 2014-06-29
So I cannot do any thing about it? The problem has appeared since Ubuntu* 13.10. I'll use a usb card reader instead.
Any way, thank you.

---

### Post by tgalati4 on 2014-06-29
You can do some research on what type of card reader you have:

```
lspci | grep Mass
```

Make a list of types of SD cards that work and cards that don't work.  Do some research on the *keucr* module--it appears to be the driver that is having problems.  Because it is a regression (something that worked before and now is no longer working) I would file a bug against 14.04.

Boot a LiveUSB of 13.10 and check the functionality of the reader and capture the dmesg output as you did earlier.  Compare the two.

---

