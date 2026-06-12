---
title: "Hard Drives are recognized randomly"
date: 2010-12-09
forum: Hardware
---

### Post by Avithohol on 2010-12-09
Hello

I have browsed a lot in this forum about my case without success,
let me reveal it in nutshell: External Hard drives are randomly  recognized.


Laptop: Compaq HP nc8430
OS: Ubuntu 10.10

External cases:
-CoolerMaster External HDD enclosure
-External USB 2.0 HarDrive docking station

Harddrives:
-1 Terra Western Digital HDD
-1 Terra Samsung HDD
-350 Gbyte Samsung HDD


All the 2 external cases are connected via USB cable to the laptop.



As i connect an external HDD via USB to the laptop,
the following things happen randomly:
1. HDDs start to blink heavily for about 5-10 minutes then recognized as a not partitioned HDD
2. Recognized and mounted immediately, but cannot launch it, as it says the device is busy.
3. Recognized, mounted and usable as it should, without any problem !



I sacrificed the Samsung 1 Terra HDD to see whether its a filesystem issue or not. So i have repartitioned and formatted it several times to NTFS or FAT32 (i have to use one of these to have compatibility with M$). I did several time with Gparte and KDE Disk Partition and also put it to another PC which has Windows XP installed and did the same there with Diskpart and Disk Manager. Does not matter where or which way i managed the HDD it still behaves the same way as described in 3 points above.

Under Windows XP and Windows 7 all the HDD drives work fluently without any issue with all the external cases and with all the HDD drive combination.


I have an 8 Gbyte USB drive it seems to be working fine though.



Any idea ? I would close out the hardware problem as all the HDDs are checked (Samsung is brand new) and in 100% condition.



Thank You for Reading this

---

### Post by Avithohol on 2010-12-13
One more hint:

If i attach the external HDD to my Windows Desktop PC, it recognizes it without issue,
then if i attach it to my Ubuntu laptop, i have approx 90% chances to be recognized
and get mounted without any issue.

Now if i safely remove from Ubuntu, and attach it back to Ubuntu,
my 90% chance decreases each time.


One more thing: if i manage to attach, mount and use then in Ubuntu,
and try to safely remove it has 20% chance to get error during the deattaching process. 


-------------------------------------------------------------------------------------------------------
Error Message during safe remove:
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.4)
SYNCHRONIZE CACHE: OK
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory


If this happens then i get 0% chance to attach the drive again to Ubuntu,
in that case i have to attach back to Windows again as described above.

---

### Post by Avithohol on 2010-12-21
I had to revert back to W7 :(,
but will follow Ubuntu progress though,
and come back to a later version.

---

