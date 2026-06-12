---
title: "damaged SD card? How to repair?"
date: 2009-10-16
forum: Hardware
---

### Post by robgr85 on 2009-10-16
Hi!

I have one SD card, which sudenly stopped working. It is impossible to read it... for me, I hope that there is a chance of it...

dmesg output after pluging the card

```
[11377.801352] usb 7-2: new high speed USB device using ehci_hcd and address 4
[11377.935648] usb 7-2: configuration #1 chosen from 1 choice
[11377.939319] scsi6 : SCSI emulation for USB Mass Storage devices
[11377.947917] usb-storage: device found at 4
[11377.947923] usb-storage: waiting for device to settle before scanning
[11382.945238] usb-storage: device scan complete
[11382.955089] scsi 6:0:0:0: Direct-Access     SanDisk  SD Plus          0.1  PQ: 0 ANSI: 2
[11382.959290] sd 6:0:0:0: [sdb] 1984000 512-byte hardware sectors (1016 MB)
[11382.959877] sd 6:0:0:0: [sdb] Write Protect is off
[11382.959883] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11382.959885] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[11382.962413] sd 6:0:0:0: [sdb] 1984000 512-byte hardware sectors (1016 MB)
[11382.963037] sd 6:0:0:0: [sdb] Write Protect is off
[11382.963041] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[11382.963043] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[11382.963090]  sdb: sdb1
[11382.967907] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[11382.979113] sd 6:0:0:0: Attached scsi generic sg2 type 0
[11413.164068] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[11443.408062] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[11473.652065] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[11503.896083] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[11534.141067] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[11564.384294] usb 7-2: reset high speed USB device using ehci_hcd and address 4
[11564.517202] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[11564.517212] end_request: I/O error, dev sdb, sector 0
[11564.517219] Buffer I/O error on device sdb, logical block 0
[11564.517229] Buffer I/O error on device sdb, logical block 1
[11564.517232] Buffer I/O error on device sdb, logical block 2
[11564.517234] Buffer I/O error on device sdb, logical block 3


```

qtparted doesn't see that card, any tries of manual mounting are showing the following error message:
```

mount: special device /dev/sdb1 does not exist

```

is there any chance of making it work/(read) again?

---

### Post by quixote on 2009-10-17
Do you just want to be able to see it so you can reformat it?  Or do you need to recover data from it first?

Will any other partition editors, eg gparted, see it?  How about other OSes, eg Windows?

---

### Post by stinger30au on 2009-10-18
theres i/o errors on the card

you MIGHT be able to recover some data off it

it be suprised if you can get it all back

got a backup?

---

### Post by robgr85 on 2009-10-18
> **quixote said:**
> Do you just want to be able to see it so you can reformat it?  Or do you need to recover data from it first?

Will any other partition editors, eg gparted, see it?  How about other OSes, eg Windows?

It would be nice to get the data back, but it is not so important, I would like to make it usable again.

gparted doesn't see the card, and it wrote message at the terminal
```

======================
libparted : 1.8.9
======================
Can not check device /dev/sdb - No such file or directory.

```

windows explorer hangs after the card is plugged in...

Cheers,

---

### Post by quixote on 2009-10-18
Well, it sounds to me like that card is toast.  I'm not an expert, and I may be wrong.  I had a situation like that, and what I wound up doing was using a low level reformatter you can download for free from Panasonic: [http://panasonic.jp/support/global/cs/sd/download/sd_formatter.html](http://panasonic.jp/support/global/cs/sd/download/sd_formatter.html)  The download button is way at the bottom.

It runs only under Windows, and all data on the card is permanently lost.  However, you do get a usable card back.  In my case 2GB on an 8GB card just disappeared and even the low level formatter wouldn't touch it, but at least I had 6GB I could still use.  

Sorry not to have better news. :(

---

### Post by robgr85 on 2009-10-18
> **quixote said:**
> Well, it sounds to me like that card is toast.  I'm not an expert, and I may be wrong.  I had a situation like that, and what I wound up doing was using a low level reformatter you can download for free from Panasonic: [http://panasonic.jp/support/global/cs/sd/download/sd_formatter.html](http://panasonic.jp/support/global/cs/sd/download/sd_formatter.html)  The download button is way at the bottom.

It runs only under Windows, and all data on the card is permanently lost.  However, you do get a usable card back.  In my case 2GB on an 8GB card just disappeared and even the low level formatter wouldn't touch it, but at least I had 6GB I could still use.  

Sorry not to have better news. :(

It didn't worked, when I put the card into, it is no responding... wonder if I can force linux to format it at low level...

---

### Post by quixote on 2009-10-18
Do you mean you downloaded the Panasonic formatter and tried to access the card from that program?  Windows isn't going to see the card.  The Panasonic program generally would.  If it doesn't, then as far as I know, the manufacturers are capable of reformatting the card, but at that point you're better off buying a new one.  

I wonder what happened to fry it so totally.  From what you say, it sounds like you put it in the computer and it didn't work.  Very mysterious.  Did it sit in the sun or get hot, perhaps?  In a car, for instance?  Did somebody put a bar magnet on it??  Took it out of the slot without unmounting?

---

