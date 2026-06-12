---
title: "All USB ports don't work"
date: 2012-03-04
forum: Hardware
---

### Post by vittynoz@yahoo.es on 2012-03-04
Hello, I'm new in Ubuntu and later the installation 11.1 in January all my usb ports don't work.
Previously, I had a W7 partition and my sub ports work fine. But later the ubuntu installation my board don't recognize any USB ports even in the BIOS panel.

I have try different solutions but none works. I have this: dmesg | grep error


[    7.392252] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,user_xattr
[   22.869047] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   29.320037] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[  232.481143] usb 8-3: device descriptor read/all, error -62
[  232.781130] usb 8-3: device descriptor read/all, error -62
[  232.945122] usb 8-3: device descriptor read/8, error -62
[  233.069148] usb 8-3: device descriptor read/8, error -62
[  233.333137] usb 8-3: device descriptor read/8, error -62
[  233.457133] usb 8-3: device descriptor read/8, error -62

I think that the kernel blocked the Board but I clear the CMOS and it don't recognize any usb port. Currently, I have a external multiusb. But I need to fix the problem. Thanks
My HW is: chinese ATX, Phenon X4 955, MSI880GMS-E35, 8GbRAM 1333MHz, WD500Gb.

---

### Post by Sonsum on 2012-03-04
> **vittynoz@yahoo.es said:**
> Hello, I'm new in Ubuntu and later the installation 11.1 in January all my usb ports don't work.
Previously, I had a W7 partition and my sub ports work fine. But later the ubuntu installation my board don't recognize any USB ports even in the BIOS panel.

I have try different solutions but none works. I have this: dmesg | grep error


[    7.392252] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,user_xattr
[   22.869047] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   29.320037] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[  232.481143] usb 8-3: device descriptor read/all, error -62
[  232.781130] usb 8-3: device descriptor read/all, error -62
[  232.945122] usb 8-3: device descriptor read/8, error -62
[  233.069148] usb 8-3: device descriptor read/8, error -62
[  233.333137] usb 8-3: device descriptor read/8, error -62
[  233.457133] usb 8-3: device descriptor read/8, error -62

I think that the kernel blocked the Board but I clear the CMOS and it don't recognize any usb port. Currently, I have a external multiusb. But I need to fix the problem. Thanks
My HW is: chinese ATX, Phenon X4 955, MSI880GMS-E35, 8GbRAM 1333MHz, WD500Gb.

Your USB ports aren't recognized even in the BIOS panel? Your OS rarely has anything to do with your BIOS. This means that your USB hub or something most likely went dead. I'm not a hardware guy, but that's what it sounds like to me.

---

### Post by vidtek on 2012-03-04
Vitty-

I had the same thing happen to me on an old acer laptop.

I removed the battery for 1/2 hr and reinstalled a Windows O/S and it all worked again.  I don't know how, but the Linux install just broke my USB.

I was able to re-install Linux after and all worked well.  It's a mystery as is so much in the computing world, things seem to happen randomly for no apparent reason.

Best of luck with it, Tony

---

### Post by vittynoz@yahoo.es on 2012-03-04
@somsun I think that the problem is not HW because when I typed lsusb the system detect the usb ports. When I said that the BIOS don't recognize the usb, I try to say that the keyboard or anything else isn't active when open the BIOS menu. 

I not sure that it's the OS but it's so weird that W7 and Ubuntu 11.1 detect the usb ports but report error i.e. the usb cable is wrong or something like that. Besides all my usb ports work during the ubuntu installation (I made that using USB stick). I think that the kernel blocked the usb port assigning less power or something like that.

---

### Post by vittynoz@yahoo.es on 2012-03-04
Thanks @vidtek. 
Actually, it's the second time for me with this problem. The first time, it happened like you said. But I installed again ubuntu 11.1 and kapput. My technician checked the board and this worked fine in his office (he didn't do anything). I was so happy but in january I installed ubuntu 11.1 again and kapput.

I will format all my disk and try to install W7.

---

### Post by Harryx1 on 2012-06-22
Hi guys,

Ubuntu 12.04 LTS
Netbook

I am connecting my USB Tata Photon but nothing happens , its not detetcing any USB device, What should i do please let me know.

Welcome you all.

Thanks

---

