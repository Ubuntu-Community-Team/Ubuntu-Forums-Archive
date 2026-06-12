---
title: "DVD drive not working"
date: 2012-08-25
forum: Hardware
---

### Post by MaWiSo on 2012-08-25
I recently installed 12.04 and found that the DVD drive is not working . it is not listed in devices in file manager and gives no response when inserting DVDs. it was working before on 11.10

the device is readable on bios setup menu though.

I've tried this before inserting a disc:
```
sudo lshw
```
it returns this :
```
*-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT30N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: LC01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

``` 
I tried it again just after inserting a disc 
it says status=busy instead of nodisc
and the LED keeps blinking

a while after it returns back to nodisc and the blinking stops


I tried this too :
```
sudo mount /dev/sr0 /mnt
```
it returns : 
```
mount: no medium found on /dev/sr0
```

any help ??

---

### Post by MaWiSo on 2012-08-29
any help please

---

### Post by dandnsmith on 2012-08-31
The amount of detail you've so far posted is appreciated, and useful.
Just as a confirmation, have you tried booting from a CD or using a LiveCD of 11.10?
It's quite possible that one 'side' of the device has gone non-functional - the lasers used for DVD and CD have to be of different frequencies, but the optical path usually uses a common channel so you only see one lens, and one can go below spec without affecting the other.
It is always a good move to use a lens cleaning CD/DVD to eliminate dirt on the lens as a possibility.

---

