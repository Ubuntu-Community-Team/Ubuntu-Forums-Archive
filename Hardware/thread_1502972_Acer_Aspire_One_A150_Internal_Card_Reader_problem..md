---
title: "Acer Aspire One A150 Internal Card Reader problem."
date: 2010-06-06
forum: Hardware
---

### Post by matt-fender on 2010-06-06
Hiya guys, happily installed 10.04 today, everything except the Internal Card Reader has worked straight out of the box, when inserting my SD Card and XD Card, it doesn't mount. anyone got any ideas?

---

### Post by dileepm on 2010-06-06
Try this [http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html](http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html)

---

### Post by matt-fender on 2010-06-06
> **dileepm said:**
> Try this [http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html](http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html)


Unfortunately, still not a winner. Anything i can post to help?

---

### Post by efflandt on 2010-06-06
What does the tail end of dmesg show after inserting memory in the slot?

Do USB flash or drives auto mount?  If not, do you see any errors in dmesg about attempting to read a floppy drive fd0 (when you have no floppy)?

---

### Post by matt-fender on 2010-06-20
> **efflandt said:**
> What does the tail end of dmesg show after inserting memory in the slot?

Do USB flash or drives auto mount?  If not, do you see any errors in dmesg about attempting to read a floppy drive fd0 (when you have no floppy)?


Tail end of dmesg:

[  195.557413] scsi3 : SCSI emulation for USB Mass Storage devices
[  195.572693] usb-storage: device found at 4
[  195.572701] usb-storage: waiting for device to settle before scanning
[  200.573467] usb-storage: device scan complete
[  200.574159] scsi 3:0:0:0: Direct-Access     Generic  External         1.04 PQ: 0 ANSI: 4
[  200.583213] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  200.598207] sd 3:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  200.598967] sd 3:0:0:0: [sdc] Write Protect is off
[  200.598980] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  200.598988] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  200.601278] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  200.601296]  sdc: sdc1
[  200.669125] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  200.669152] sd 3:0:0:0: [sdc] Attached SCSI disk
[  782.773196] CE: hpet increasing min_delta_ns to 15000 nsec
[  787.834899] ath5k phy0: noise floor calibration timeout (2462MHz)
[ 2044.545364] usb 1-2: USB disconnect, address 2
[ 3976.586933] ath5k phy0: unsupported jumbo
[ 5932.971761] ath5k phy0: unsupported jumbo
[ 6256.604498] ath5k phy0: unsupported jumbo

-------------------------------------------------------------------------------------------


As you can see if it's mounting my 500GB External (USB) no problem at all,

have attached FULL log of dmesg after inserting XD card. Would you mind taking a look? The only thing i could find was something along the lines of "fd0 virtual something" :(

Thankyou so much for your help:lolflag:

---

### Post by matt-fender on 2010-06-21
Bump! Please help, anyone!!

---

### Post by sisyphus1978 on 2010-06-21
Check out this blog:

[http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html](http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html)

It helped me when I was installing Lucid on my Aspire One.

---

### Post by matt-fender on 2010-06-21
> **sisyphus1978 said:**
> Check out this blog:

[http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html](http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html)

It helped me when I was installing Lucid on my Aspire One.


Thankyou, this fixed the card reader to SOME EXTENT. SD Cards are hot pluggable, Both left hand reader and right hand reader,however it completely refuses to recognise my XD Card. Any ideas? I'll see what happens in dmesg after inserting XD cards.

Thanks for finding that fix!

---

### Post by Quarn on 2010-07-28
> **sisyphus1978 said:**
> Check out this blog:

[http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html](http://subbass.blogspot.com/2010/05/howto-ubuntu-1004-lucid-post-install.html)

It helped me when I was installing Lucid on my Aspire One.

 
It worked, at least for the left one:p
 i could not try the right one, the battery is death :(

But still, Thanks a lot :)

---

