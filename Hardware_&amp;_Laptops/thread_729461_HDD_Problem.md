---
title: "HDD Problem"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by HanaD on 2008-03-19
Hello,

I Have a western digital external portable HDD and i ma trying to plug that into my X61 tablet.
I had used this HDD before and it was working fine, but now when i plug it in to th eUSB i cannot see any additional HDD.

I tries it in windows as well, it did not show up, in windows i did get an error message though saying that the USB device encountered some problems and there were no drivers to handle it.

fdisk -l does not show me any such device plugged in 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe11595f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10612    80226688+   7  HPFS/NTFS
/dev/sda2           11395       11533     1050840   82  Linux swap / Solaris
/dev/sda3           10613       11394     5911920   12  Compaq diagnostics
/dev/sda4           11534       12921    10493280   83  Linux

Partition table entries are not in disk order
hana@X61:~$ 



Please Help
Regards

---

### Post by michaelaly on 2008-03-20
1) Try a different USB port
2) Try a different computer, if possible
3) Try a different USB cable
4) Open up the external HDD case and make sure the drive plug(IDE or SATA) is seated firmly.
5) Listen for abnormal grinding or clicking noises from the drive when you plug it in. If you hear these noises the drive is likely toast.

---

### Post by nick_h on 2008-03-20
Does *lsusb* show anything?

---

### Post by HanaD on 2008-03-20
hana@X61:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

Also other comp i have is desktop running windows,
i get message saying that usb connected is not recognised by windows,

---

### Post by nick_h on 2008-03-21
It doesn't show up.  I would have a look at michaelaly's suggestions.

---

