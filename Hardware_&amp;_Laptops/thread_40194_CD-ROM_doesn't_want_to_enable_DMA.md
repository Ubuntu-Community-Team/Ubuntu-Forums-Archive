---
title: "CD-ROM doesn't want to enable DMA"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by PryGuy on 2005-06-08
Hello all!
I've got a Teac DW-548D DVD drive and it's sooo slow! I tried to speed it up following [these recommendations](http://ubuntuguide.org/#speedupcddvdrom)  but it didn't work for me. Everytime I try to make this:```
sudo hdparm -d1 /dev/cdrom
``` It says that "Operation not permitted" though the device is unmounted and all.
Please help! Thank you!

---

### Post by Markrian on 2005-06-08
/dev/cdrom is usually a symbolic link to /dev/hdX, where X is a, b, c, d or whatever the actual device name of the drive is.

Check whether or not the link actually points to the correct device with```
$ file /dev/cdrom
```Other than that, you could try pointing hdparm directly to the device file.

Being a DVD drive it *should* support DMA, so not sure what that's about.

---

### Post by PryGuy on 2005-06-08
file /dev/cdrom says "/dev/cdrom: symbolic link to `hda'" (I've got SATA stuff and the DVD-ROM is the only device that uses old PATA, that's why), sudo hdparm -d1 /dev/hda says > /dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)I'm confused actually. Any ideas?

---

### Post by jeremy on 2005-06-08
[http://ubuntuforums.org/showpost.php?p=93238&postcount=5](http://ubuntuforums.org/showpost.php?p=93238&postcount=5) has the info you need.

---

### Post by PryGuy on 2005-06-08
Thank you! It worked!!! Strange that Ubuntu can't detect Intel chipsets. Though i915 is probably something new for Ubuntu so far!
Thanks again! :)

---

