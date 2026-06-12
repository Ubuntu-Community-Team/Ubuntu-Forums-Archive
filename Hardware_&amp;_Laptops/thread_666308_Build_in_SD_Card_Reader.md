---
title: "Build in SD Card Reader"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by yon2501 on 2008-01-13
So on my dell precision m90 laptop has a build in SD card reader but when i put a card into it the card doesn't mount. im running 7.10 so i obviously have the 2.6.22-14 kernel. another thread said that all kernels since 2.6.17 have built in SD support so i know thats not it. how  do i fix this so that when i put in a SD card it will auto mount to the desktop like everything else?

---

### Post by chewearn on 2008-01-13
After you plug-in a SD card, open a terminal, type:
```
dmesg | tail
```

Any error message?  Post the output here.

---

### Post by yon2501 on 2008-01-13
ok this is what i got

```
[71838.496000] sd 28:0:0:0: [sdb] Mode Sense: 00 6a 20 00
[71838.496000] sd 28:0:0:0: [sdb] Assuming drive cache: write through
[71838.500000] sd 28:0:0:0: [sdb] 960512 512-byte hardware sectors (492 MB)
[71838.504000] sd 28:0:0:0: [sdb] Write Protect is off
[71838.504000] sd 28:0:0:0: [sdb] Mode Sense: 00 6a 20 00
[71838.504000] sd 28:0:0:0: [sdb] Assuming drive cache: write through
[71838.504000]  sdb: sdb1
[71838.508000] sd 28:0:0:0: [sdb] Attached SCSI removable disk
[71838.508000] sd 28:0:0:0: Attached scsi generic sg2 type 0
[71947.876000] usb 5-6: USB disconnect, address 29

```

---

### Post by chewearn on 2008-01-13
Ok, I'm not sure what is wrong; but your dmesg output has 3 additional lines which I'm not sure what is about.  As a comparison, here is what I got from plugging in a SD card into my card reader:
```
[112764.065335] sd 2:0:0:1: [sdb] 498176 512-byte hardware sectors (255 MB)
[112764.068954] sd 2:0:0:1: [sdb] Write Protect is off
[112764.068957] sd 2:0:0:1: [sdb] Mode Sense: 03 00 00 00
[112764.068959] sd 2:0:0:1: [sdb] Assuming drive cache: write through
[112764.072072] sd 2:0:0:1: [sdb] 498176 512-byte hardware sectors (255 MB)
[112764.074944] sd 2:0:0:1: [sdb] Write Protect is off
[112764.074947] sd 2:0:0:1: [sdb] Mode Sense: 03 00 00 00
[112764.074949] sd 2:0:0:1: [sdb] Assuming drive cache: write through
[112764.074952]  sdb: sdb1

```You can see, your output has 3 additional lines.  Good news, the card reader is probably working.  Other than that, I can only offer some suggestions:

1. do you have another SD card you can try?

2. is the SD card properly formatted?  Are you able to plug the card into a WIndows system and check the file system format?

3. can you manually mount sdb1?
```
sudo mkdir /media/sdcard
sudo mount /dev/sdb1 /media/sdcard
```

---

### Post by yon2501 on 2008-01-13
ok i tried that last one manually mounting it but i got this 
```

xxxxxxxxxx:~$ sudo mkdir /media/sdcard
[sudo] password for xxxxxxxxx:
xxxxxxxxxx:~$ sudo mount /dev/sdb1 /media/sdcard
mount: special device /dev/sdb1 does not exist

```
 and i think the  three extra lines was the fact that my psp was plugged in but i dont know for sure.

---

### Post by chewearn on 2008-01-13
So, if you plug-in the SD card, and immediately run dmesg | tail (and not plug/unplug something else in between), do you still get the 3 lines?

---

### Post by yon2501 on 2008-01-13
yep i still get the same thing :\

---

### Post by chewearn on 2008-01-13
Ok, I did a bit of googling, this might or might not work:

First, find out if the SD card ends up in sg2:
```
ls /dev/sg2
```if you see an output: /dev/sg2

then try:
```
sudo mount /dev/sg2 /media/sdcard
```Edit:
Upon further investigation, it might not work.  You can try fdisk -l to find out if the SD card is mapped to another /dev/xxx

See here:
[http://www.cs.sfu.ca/~ggbaker/personal/cf-linux](http://www.cs.sfu.ca/~ggbaker/personal/cf-linux)
It advice to use sg3-utils (I found sg3-utils is there in the ubuntu repositories).  But I'm not familiar with this, so you will have to experiment with it.

---

### Post by yon2501 on 2008-01-13
ok "no such file or directory"
```

xxxxxxxxxxx:~$ ls /dev/sg2
ls: /dev/sg2: No such file or directory

```

---

