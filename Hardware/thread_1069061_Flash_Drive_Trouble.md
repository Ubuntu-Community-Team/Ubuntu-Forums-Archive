---
title: "Flash Drive Trouble"
date: 2009-02-13
forum: Hardware
---

### Post by winzer on 2009-02-13
The brand name is adata and is a 16GB Flash stick for USB. When I insert it into the usb port it doesn't get fully recognized. If I goto /media it's not even on the list. When I go to the file browser, it shows up as an icon, but when I goto access it does nothing. I know my ports work fine since I have used other brand USB drives on it. On the adata website it says I need at least the kernel version 2.4, I have 2.6. I am not sure what the problem is.

---

### Post by kestrel1 on 2009-02-13
Do you have other things plugged in via USB?
If so unplug some & try the stick again. It could be lack of power to the USB ports. Are you plugging it in directly to the USB ports on the motherboard or are the ports at the front of the case?

---

### Post by winzer on 2009-02-13
Sorry, I have failed to mention that it is a laptop. I have three USB ports. One on the right and two stacked on the left. The only thing I have left is my usb mouse. But this should not be a problem since it has worked with other usb flash drives before.

---

### Post by kestrel1 on 2009-02-13
Plug the drive in & give us the result of```
lsusb
```

---

### Post by winzer on 2009-02-13
I get:

Bus 005 Device 010: ID 125f:1036 A-DATA Technology Co., Ltd. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1130:6606 Tenx Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it looks like it is recognized . It's just the access that's the trouble.

---

### Post by kestrel1 on 2009-02-13
Have you tried the USB stick in any other machines to make sure that it is working correctly with them?

---

### Post by winzer on 2009-02-13
No I haven't. I'll go try it on a windows machine.

---

### Post by JK3mp on 2009-02-13
Let us know how that goes. My best guess at this is that the ADATA has some kind of initial setup program that only works with windows...much like the cruzer USB drives..if it won't allow you after a setup of it on a windows machine...then in order to use it on you linux you'll probably have to delete the USB management program off the usb stick and just use it as a plain old storage device. ONly down part is can't use whatever "EXTRA"* features came with the Usb stick...manager,password protection,Application install etc....Not a big woop really did it with mine..as far as password protections theres other linux compatable programs that can install on it..

---

### Post by winzer on 2009-02-13
Well I hooked it up to a Vista machine and it looks fine. I did not see any special software of any kind. Just for the heck of it I am reformatting it to NTFS and I'll try again. I still don't see what problem there would be. The website says it should work with linux. :mad:

---

### Post by ALIENDUDE5300 on 2009-02-13
> **winzer said:**
> Well I hooked it up to a Vista machine and it looks fine. I did not see any special software of any kind. Just for the heck of it I am reformatting it to NTFS and I'll try again. I still don't see what problem there would be. The website says it should work with linux. :mad:

NTFS might be the problem. Try reformatting to FAT32.

---

### Post by winzer on 2009-02-13
It was Fat32 originally, I am reformatting it to NTFS.

---

### Post by winzer on 2009-02-13
So I reformatted the USB to NTFS. When I plugged in the flash drive I got response, not a good one.

The first message that came up was:
Cannot mount volume

And unable to mount 16.2 GB media

I could not copy paste the error so I took a screen shot.

---

### Post by kestrel1 on 2009-02-14
It seems to be indicating an unclean shutdown when you removed it in Vista. Did you go through the routine of a clean shutdown & not just unplug the drive?
You could try forcably mounting the drive by using the command that is given in the error message or just take it back to the Vista machine & cleanly remove it.
Should be an icon in the task bar of Vista that you should then be able to select the drive to remove it correctly from the system.

---

