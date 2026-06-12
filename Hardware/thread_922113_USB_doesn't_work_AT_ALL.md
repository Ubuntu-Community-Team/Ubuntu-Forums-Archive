---
title: "USB doesn't work AT ALL"
date: 2008-09-17
forum: Hardware
---

### Post by screaminj3sus on 2008-09-17
I have a gateway m6862, just bought it a couple weeks ago, I installed ubuntu and everything seemed to work flawlessly..even wireless works great. But my USB ports don't work at all in linux! It works fine in vista. I can plug anything into a USB port, thumbdrive, ipod ect... it has absolutely no effect and nothing happens, is there anyway to fix this?

I am running ubuntu 8.04 64 bit.

Here's my laptop:
[http://www.bestbuy.com/site/olspage.jsp?skuId=8913241&type=product&id=1213399955100](http://www.bestbuy.com/site/olspage.jsp?skuId=8913241&type=product&id=1213399955100)

---

### Post by mkokotovich on 2008-09-17
Unplug any flashdrives you have in.

Open a terminal and enter ```
lsmod | grep usb
```Look for usbcore and usb_storage in the left hand columns. That means that the kernel modules are loaded for usb.

Now enter ```
lsusb
```Plug in your flashdrive, and run the same command again.

Do you see any new entries?  If so, that means what you plugged in was recognized by the computer.

If that last step was successful, enter ```
ls /dev/sd*
```Depending upon how many hard drives you have in the computer, you should see sda (and sda1, 2, 3, etc depending upon partitions, don't worry about the numbers) and maybe sdb, sdc, etc. When you plug in the jump drive, it creates one of these entries (in a normal case).  You can try unplugging and plugging it in to see if it is working. If it is working, then it is just the automount that doesn't work, and you'll either need to find how to fix that or just mount things manually.

---

### Post by screaminj3sus on 2008-09-17
Tried those commands, after typing lsub and plugging in the drive, nothing happens.

brandon@brandon-laptop:~$ lsmod | grep usb
usb_storage            82496  0 
libusual               23520  1 usb_storage
scsi_mod              178488  5 sr_mod,sg,sd_mod,usb_storage,libata
usbcore               169904  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
brandon@brandon-laptop:~$ lsusb

---

### Post by mkokotovich on 2008-09-17
Alright, enter ```
dmesg | tail
```Then plug in a flashdrive. Then run the command again.  Post results (if there is a change).

---

### Post by screaminj3sus on 2008-09-17
alright, had a little breakthrough, I restarted and now it works! It seems to completely stop working after it resumes from suspend though, which is not good because it's a laptop.

---

### Post by mkokotovich on 2008-09-17
No, that isn't good...

That was actually the next thing I was going to say.  I've read about problems where something needs to be plugged in during the boot process in order to be seen.  I don't know how to solve those problems, I've just read about them :)

Anything interesting in the dmesg output?

---

### Post by screaminj3sus on 2008-09-17
Alright here's what I get for that (this is after I restarted obviously :) )

brandon@brandon-laptop:~$ dmesg | tail
[   62.108025] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   62.108029] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   62.110639] sd 6:0:0:0: [sdc] 4013709 512-byte hardware sectors (2055 MB)
[   62.111263] sd 6:0:0:0: [sdc] Write Protect is off
[   62.111268] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   62.111272] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   62.111278]  sdc: sdc1
[   62.112749] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   62.112810] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  258.982275] usb 7-1: USB disconnect, address 3
brandon@brandon-laptop:~$ dmesg | tail
[  280.252066] sd 7:0:0:0: [sdc] Write Protect is off
[  280.252072] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  280.252076] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  280.255058] sd 7:0:0:0: [sdc] 4013709 512-byte hardware sectors (2055 MB)
[  280.255684] sd 7:0:0:0: [sdc] Write Protect is off
[  280.255690] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  280.255693] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  280.255699]  sdc: sdc1
[  280.257181] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[  280.257244] sd 7:0:0:0: Attached scsi generic sg3 type 0
brandon@brandon-laptop:~$

---

### Post by mkokotovich on 2008-09-17
Alright, so that was run after the reboot, so it was working?  Next time it isn't working try doing it again, and see if you see anything.

---

### Post by screaminj3sus on 2008-09-17
alright here's what I get when it is not working.

brandon@brandon-laptop:~$ dmesg | tail
[   24.186912] sd 0:0:0:0: [sdb] Sense not available.
[   24.186965] sd 0:0:0:0: [sdb] Write Protect is off
[   24.186969] sd 0:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   24.186973] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   24.187176] sd 0:0:0:0: [sdb] READ CAPACITY failed
[   24.187180] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   24.187185] sd 0:0:0:0: [sdb] Sense not available.
[   24.187236] sd 0:0:0:0: [sdb] Write Protect is off
[   24.187240] sd 0:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   24.187243] sd 0:0:0:0: [sdb] Assuming drive cache: write through
brandon@brandon-laptop:~$ dmesg | tail
[   26.405973] sd 0:0:0:0: [sdb] Sense not available.
[   26.406028] sd 0:0:0:0: [sdb] Write Protect is off
[   26.406032] sd 0:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   26.406036] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   26.406236] sd 0:0:0:0: [sdb] READ CAPACITY failed
[   26.406239] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   26.406244] sd 0:0:0:0: [sdb] Sense not available.
[   26.406295] sd 0:0:0:0: [sdb] Write Protect is off
[   26.406299] sd 0:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   26.406303] sd 0:0:0:0: [sdb] Assuming drive cache: write through
brandon@brandon-laptop:~$

---

### Post by mkokotovich on 2008-09-17
Hmm, I think some data got left out.  The tail command by default cuts to 10 lines, let's tell it to do 20.```
dmesg | tail -20
```Do it before you plug it in, then after, and post the results.  Hopefully we can see something helpful in there.

---

### Post by screaminj3sus on 2008-10-16
wewt it seems to be fixed in the 8.10 beta!

---

