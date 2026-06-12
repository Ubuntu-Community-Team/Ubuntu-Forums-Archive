---
title: "no usb thumb drive detection"
date: 2008-07-27
forum: Hardware
---

### Post by mikey on 2008-07-27
hardy and tosh l25 satellite s121 celeron 1.7

does not recognize and obviously won't auto mount usb thumb drive.
fdisk -l only shows hd

tried all 3 ports with same result. please advise. thanks mikey

---

### Post by tamoneya on 2008-07-27
plug the drive in again and type:```
lsusb
``` and then post here.  Also do you know that the drive is good?  Can you test it on another computer (or another drive on your laptop) in order to confirm that the drive isnt bad.

---

### Post by mikey on 2008-07-27
mikey@mikey-tosh:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

the drive works in my desktop using linuxmint 4. it is formatted in fat 32. and the usb port is ok since this laptop is dual boot and the thunb works ok in xp.

---

### Post by mikey on 2008-07-28
the answer to this problem was rather simple. that is, not all thumb drives are created equal. I attached original drive to an adapter cable and then inserted it into the usb port and ,voila, it auto mounted. in another unit the same thumb drive performed well in linux mint but without the adapter cord. go figure. hoped this helped others.:)

---

