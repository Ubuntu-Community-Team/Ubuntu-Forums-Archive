---
title: "Can't get MTP to work correctly on my laptop in order to connect my Samsung Galaxy S4"
date: 2015-09-24
forum: Hardware
---

### Post by redmage123 on 2015-09-24
Hello all,

I'm running Ubuntu 14.04 on my Laptop and I'm trying to connect a Samsung Galaxy S4 via the USB port. 
I get the following when trying to find the product Id and product Vendor strings...

xvarix2:~/src/python% mtp-detect | grep idProduct
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device

I've verified that the phone is connected as a media device.  

Googling for the solution hasn't produced anything useful. 

Any assistance appreciated. 

--redmage123

---

### Post by Bucky Ball on 2015-09-24
*Thread moved to **Hardware**.*

---

