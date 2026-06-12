---
title: "Omnikey CardMan 3121 problem"
date: 2008-08-19
forum: Hardware
---

### Post by janip on 2008-08-19
Hi!

I have Ubuntu 8.04.1 32bit and I'm trying to get my smart card reader OmniKey CardMan 3121 working. I installed driver from debian package [http://packages.debian.org/sid/misc/pcsc-omnikey](http://packages.debian.org/sid/misc/pcsc-omnikey) and also libpcsclite and pcscd. Lsusb shows that device is present:

Bus 001 Device 005: ID 076b:3021 OmniKey AG CardMan 3121

When I unplug/plug back the device, following lines are written to dmesg:

[ 1643.233167] usb 1-1: USB disconnect, address 4
[ 1649.577071] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 1649.789681] usb 1-1: configuration #1 chosen from 1 choice

Could someone give me an advice how I check if the driver is loaded or somehow else test if the reader works.

The actual problem is that when I'm trying to use mpollux-digisign-client_1.0.1-1511_i386.deb (official - if that's the right term - card management software for finnish electronic ID cards), it shows that no reader device present.

-Jani

---

### Post by janip on 2008-08-20
Could someone give me general advice of how to check if some driver is loaded or not.

Jani

---

### Post by bugslayr on 2010-01-28
Hello Jani, did you make any further progress?

I got the 3121 to work and also a different one by compiling an extra driver.
The Omnikey 3121 shour work out of the box ...

Here are my steps:
Install the following packages:
libpcslite1
libpcsc-perl (possibly required for gscriptor only)
pcscd
pcsc-tools (-> pcsc_scan)
make sure usbfs is mounted properly ...
If not, execute:
*mount -t usbfs none /proc/bus/usb*
Write the following line into /etc/fstab to make it permanent
*usbfs /proc/bus/usb usbfs auto 0 0*

Restart pcscd and follow log file (/var/log/messages on my machine)

Start pcsc_scan to follow card insertion and removal 

Here is what I get when isnserting a chipcard ...
[I]Reader 0: OmniKey CardMan 3121 00 00
  Card state: Card inserted, Unresponsive card,[/I]

I hope this helps!
   ;-) Martin

---

### Post by AhmedZaki on 2011-11-01
I have the same problem 
I have ubuntu 11.10  and Omnikey cardMan 3121
after installing all drivers and library pcsc-tool , .... pcscd , and the omnikey driver from HID 
the pcsc-scan run perfect , while the other program can't detect the card like eclipse, smart card shell  , xcard ,...

What can I do ?
:confused:

---

