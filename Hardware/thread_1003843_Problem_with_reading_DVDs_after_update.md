---
title: "Problem with reading DVDs after update"
date: 2008-12-06
forum: Hardware
---

### Post by J-Rod on 2008-12-06
*solved* 

The issue was a bad IDE cable. Put in a newer one, and drive works fine. To make sure that's what it was, put old cable back in, and sure enough, failure. Go figure, eh?

Well here's the skinny. Performed an update through automatic updates. I found I could no longer mount DVDs. I check lshw, and it looks like my DVD drive has been assigned a different /dev id. No big deal, I'll just change it in fstab. Still no worky. I check dmesg after inserting a DVD/CD, and I get this:

```
[ 1793.068072] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1793.068085] sr: Sense Key : Hardware Error [current] 
[ 1793.068089] sr: Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.771960] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.771969] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.771974] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.771980] end_request: I/O error, dev sr0, sector 64
[ 1796.771984] printk: 18 messages suppressed.
[ 1796.771988] Buffer I/O error on device sr0, logical block 16
[ 1796.771994] Buffer I/O error on device sr0, logical block 17
[ 1796.793052] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.793061] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.793066] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.793072] end_request: I/O error, dev sr0, sector 64
[ 1796.793077] Buffer I/O error on device sr0, logical block 16
[ 1796.793083] Buffer I/O error on device sr0, logical block 17
[ 1796.825997] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.826006] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.826011] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.826016] end_request: I/O error, dev sr0, sector 0
[ 1796.826021] Buffer I/O error on device sr0, logical block 0
[ 1796.829725] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.829729] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.829732] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.829736] end_request: I/O error, dev sr0, sector 4
[ 1796.829738] Buffer I/O error on device sr0, logical block 1
[ 1796.829742] Buffer I/O error on device sr0, logical block 2
[ 1796.829745] Buffer I/O error on device sr0, logical block 3
[ 1796.849556] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.849560] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.849563] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.849568] end_request: I/O error, dev sr0, sector 0
[ 1796.849570] Buffer I/O error on device sr0, logical block 0
[ 1796.849573] Buffer I/O error on device sr0, logical block 1
[ 1796.858760] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 1796.858769] sr: Sense Key : Hardware Error [current] 
[ 1796.858772] sr: Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.882730] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.882739] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.882744] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.882749] end_request: I/O error, dev sr0, sector 0
[ 1796.887331] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.887335] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.887338] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.887342] end_request: I/O error, dev sr0, sector 4
[ 1796.904237] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.904242] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.904244] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.904248] end_request: I/O error, dev sr0, sector 0
[ 1796.908257] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1796.908261] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1796.908264] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1796.908268] end_request: I/O error, dev sr0, sector 4
jrodder@jrodder-desktop:~$ 


```

I don't know what to think, my first guess is the drive is failing, or some sort of other hardware issue. Everything worked fine before i updated. Coincidence?

Any help or input is greatly appreciated!

---

### Post by rossofiorentino on 2009-02-12
I have found that an solved my problem with Dvd.
It is something about of Udev rules.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221983](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221983)

---

