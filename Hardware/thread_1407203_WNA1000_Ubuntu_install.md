---
title: "WNA1000 Ubuntu install"
date: 2010-02-15
forum: Hardware
---

### Post by FixIt PeteC on 2010-02-15
Here's the fix that worked for me! 1. Download and install compat-wireless-2010-02-01, 2. go to the compat-wireless-2010-02-01/drivers/net/wireless/ath/ar9170 folder, 3. open the file "usb.c" at line 62 there will be a list of devices with their device IDs, 4. Edit one of the existing devices to "Netgear WNA1000" and device ID "0x0846, 0x9040" you have to edit one of the existing devices since a usb driver can only control 18 devices, which are already listed. 

The ar9170usb driver is the closest match for the WNA1000, but it must recognize your device ID. If for some reason your WNA1000 device ID is different, use you IDs. I had to plug mine into a windows pc and look at its properties first.

Mine looks like: 

static struct usb_device_id ar9170_usb_ids[] = {
/* Atheros 9170 */
{ USB_DEVICE(0x0cf3, 0x9170) },
/* [COLOR="Blue"]Netgear WNA1000 */[/COLOR]
{ USB_DEVICE([COLOR="Magenta"]0x0846, 0x9040[/COLOR]) },
/* TP-Link TL-WN821N v2 */
{ USB_DEVICE(0x0cf3, 0x1002) },

If everything else in the system is correct, just reboot and there it is!  I did not use ndiswrapper.

Good luck!

---

### Post by Billsey on 2010-08-19
OK,

Now, how do we get that done without the end user having to recompile the kernel, or recompile anything, for that matter?

I'm thinking about a patch utility that, upon the user inserting the adapter in question, could be launched (whether by the user or by the OS), read the information from the adapter, determine the driver, compare the USB ID of the adapter with the USB ID's compiled into the driver, and patch if necessary or applicable. If the driver is not immediately available, the user could be prompted to download it (telling them either what the driver is, or what the controller chip is, so they can seek the driver out online).

---

