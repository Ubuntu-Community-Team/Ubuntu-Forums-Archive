---
title: "How to load dev/ttyUSB*?"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by jdyim on 2007-07-23
Hi, I'm setting up Liberty, a 3D tracking sensor manufactured by Polhemus, into my Ubuntu 2.6.15-28-386 kernel. It comes as ID 0f44:ff11 when usb plugged in first, and changes into 0f44:ff12 after I use the following command (I got the hex files at Polhemus website):

*/sbin/fxload -t fx -D /dev/bus/usb/001/004 -s /usr/share/usb/a3load.hex -I /usr/share/usb/LibertyUSB.hex*

Then I edited my usb.ids file to give the idVendor and idProduct (though I couldn't figure out how I identify the iManufacturer and iProduct). Anyway, so far so good I thought, but now I have a trouble in loading an usbserial port. I opened etc/usbmgr/usbmgr.conf and added a line as below to make a dev/ttyUSB0 when the device hotplugged:

*vendor 0xf44 product 0xff12 module usbserial , visor*

But I couldn't load dev/ttyUSB0 or any ttyUSB*. 
I'll apprecite if anybody please tell me what I did wrong with it. Following is what shows up with dmesg when I plugged in the device (I couldn't get any other message other than this):

*usb 1-1: new full speed USB device using uhci_hcd and address 4*


Thanks in advance!

- JD :confused:

---

### Post by jdyim on 2007-07-24
Hi, I think I've partly figured it out. I used the command following and finally got /dev/ttyUSB0 and ttyUSB1:

*modprobe usbserial vendor=0x0f44 product=0xff12*

Then I could make a demo program communicate with Liberty device through /dev/ttyUSB0. But still I don't have any idea how to identify the iManufacturer and iProduct strings, and how to automate the procedures by using a script or module. Can anyone teach me how to do those?

---

### Post by geraldm on 2007-07-24
In simpler times, one could obtain the parameter names by using the command:
/sbin/modinfo  {full path to kernel module}

Afterwords, the values for the parameters could be entered in the command line
after the module name, and these are passed to the kernel.
modprobe {module path} parm1=0x3256 ...

As times became more complex, one module could drive many devices with different
vendor product names.  These were created in the file /etc/modules.conf through
the use of aliases.  (fill in the * with interesting parameters) This is from module usb720.ko
alias:          usb:v1293p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0729p1284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0557p2001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v047Ep1001d*dc*dsc*dp*ic*isc*ip*

Another variation uses specific *.conf files that are installed with the package.
Refer to the man pages for the package.

Gerald

---

