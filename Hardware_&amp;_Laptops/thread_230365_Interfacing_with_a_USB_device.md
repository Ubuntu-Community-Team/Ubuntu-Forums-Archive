---
title: "Interfacing with a USB device"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by That Other Guy on 2006-08-05
I have a USB device (for interfacing with ham radios, a West Mountain Radio RigBlaster Plug & Play) that I would like to try with hamlib-related apps.  It works fine under Windows, so I know the basic connections are good.

Since it doesn't have a file system, I don't think it will automatically mount anywhere, but I need to find it to direct applications to it. Most of the apps are looking for a /dev/tty* type of connection.

Here's what little I know about it:

upon connecting it via the USB jack:

```
$ dmesg | tail
usb 1-1.4: new full speed USB device using uhci_hcd and address 6
```

```
$ lsusb
Bus 001 Device 006: ID 10c4:814a Cygnal Integrated Products, Inc.
```

And that's all I know about it....  Any help?

---

### Post by neilp85 on 2006-08-05
If you read a little higher up on dmesg it should tell you where the device was mounted. It should be mounted somewhere like /dev/sr0.

---

### Post by That Other Guy on 2006-08-05
Thanks for the reply, neilp85, but unfortunately, that IS all dmesg puts out.

As an example, I removed it just after booting, then plugged it back in.
```

$ dmesg | tail
[17179775.880000] vmnet1: no IPv6 routers present
[17179778.100000] cpufreq: change failed with new_state 0 and result 0
[17179783.756000] ide-cd: cmd 0x3 timed out
[17179783.756000] hdc: irq timeout: status=0xd0 { Busy }
[17179783.756000] ide: failed opcode was: unknown
[17179783.756000] hdc: DMA disabled
[17179783.804000] hdc: ATAPI reset complete
[17179827.444000] cpufreq: change failed with new_state 1 and result 0
[17180013.492000] usb 1-1.4: USB disconnect, address 4
[17180030.712000] usb 1-1.4: new full speed USB device using uhci_hcd and address 5
```

I checked while it was plugged in, and there are no devices in the /dev/s** series.

I figured since lsusb reads it, doesn't that at least mean the kernel recognizes it?

Is there a way to query the device further for chip info?

---

### Post by jhellan on 2007-02-23
Did you make any progress on this?
From a quick scan of the kernel sources, it looks like the CP2101 driver could work. Try adding 
	{ USB_DEVICE(0x10C5, 0x814A) }, /* West Mountain RigBlaster Plug & Play */
 to the  struct usb_device_id id_table array in drivers/usb/serial/cp2101.c in the kernel sources (line 68 in Edgy), and build a new kernel.

Do you know how to build your own kernel? If not, can you find somebody who can show you how?

73 de LA4RT Jon, Trondheim, Norway

---

### Post by jhellan on 2007-02-28
Oops, typo. Make that

{ USB_DEVICE(0x10C4, 0x814A) }, /* West Mountain RigBlaster Plug & Play */

West Mountain Radio have confirmed that the USB chip is a CP2102, which the cp2101 driver can handle. I'm submitting a patch.

The RIGtalk CAT/CIV interface has the same chip, and needs the line
 
{ USB_DEVICE(0x10C4, 0x814B) }, /* West Mountain Radip RIGtalk */

73 de LA4RT Jon, Trondheim, Norway

---

### Post by jhellan on 2007-03-07
My RigBlaster Plug & Play has now arrived, and I am now QRV on digital modes with Linux with my patch above. The device shows up as /dev/ttyUSB0 (or USB1, USB2, .. if some other USB serial device got USB0).

The patch will be included in Feisty and is on its way into the official kernel tree. It will probably be in 2.6.22.

---

### Post by jhellan on 2007-03-10
RIGblaster Plug&Play and RIGtalk support will be in the official kernel in 2.6.21, and in Feisty.

---

