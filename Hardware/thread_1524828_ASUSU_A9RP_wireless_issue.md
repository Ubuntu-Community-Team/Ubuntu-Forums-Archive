---
title: "ASUSU A9RP wireless issue"
date: 2010-07-05
forum: Hardware
---

### Post by Dhickm on 2010-07-05
Hi,

I have installed Ubuntu on an ASUS A9rp, dual booting with Vista to test before i ditch Vista completely. Have an issue with wireless, the wireless adapter is not being recognized. This is a recognised issue; I have seen the fix is; 
"Say your kernel source folder is like mine, /usr/src/linux-2.6.21-5,  open this file:
/usr/src/linux-2.6.21-5/drivers/net/wireless/zd_usb.c and add this line  to the ZD1211-B section:
  { USB_DEVICE(0x0b05, 0x171b), .driver_info = DEVICE_ZD1211B }, 
  Save the file."

but, the src file doesn't have a zd_usb.c file. Is this an issue with the latest version of Ubuntu, the fact that I am dual booting, or something else.

additionally, I have no idea what the kernel files are that i should download?

I am new to Linux and although I am fairly confident in a windows environment, this is new to me. 

Many thanks.

---

### Post by gordintoronto on 2010-07-06
Is the fix you quoted, specific to the wireless adapter in an Asus A9rp? It seems quite unusual. Do you know what the wireless adapter is? The commands lspci or lsusb should show it. Sadly, there are thousands of wireless adapters, maybe 70% work out of the box, and the others have individual solutions.

---

