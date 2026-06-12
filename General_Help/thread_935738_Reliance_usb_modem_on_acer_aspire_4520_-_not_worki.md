---
title: "Reliance usb modem on acer aspire 4520 - not working"
date: 2008-10-02
forum: General Help
---

### Post by avinashtjoshi on 2008-10-02
Hi all.

I have an Acer Aspire 4520 laptop.

I tried to get the Reliance usb working on my laptop, but it is not working.

when i do a dmesg, it gives:
[FONT="Courier New"]
[  347.631121] usb 3-1: new full speed USB device using ohci_hcd and address 8
[  347.714534] usb 3-1: device descriptor read/64, error -62
[  347.840569] usb 3-1: device descriptor read/64, error -62
[  347.964209] usb 3-1: new full speed USB device using ohci_hcd and address 9
[  348.044710] usb 3-1: device descriptor read/64, error -62
[/FONT]

A /dev/ttyUSB* is not created!!!

i.e., It is usbserial_generic is not creating a ttyUSB0.

Please help me on this...

[FONT="Courier New"]
sudo wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
[/FONT]

I tried all possible ways to get it working. but it is not happening.

I am able to connect to the net using the same usb modem from my HP laptop.

Please help me out with this.

---

### Post by avinashtjoshi on 2008-10-11
Someone please help me out!!!!

---

