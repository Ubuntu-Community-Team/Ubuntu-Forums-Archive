---
title: "Configuring HP laserjet 1020 in ubuntu 8.10"
date: 2009-09-11
forum: Hardware
---

### Post by dmadhawie on 2009-09-11
Hi,

I am new to ubuntu and I'm using ubuntu 8.10. I faced a problem in configuring my printer (HP laserjet 1020) in ubuntu environment. I tried several forums, but still no help. I would be very grateful if someone can help me for this.

Thanks in advance.

Madhawie

---

### Post by steinaro on 2009-09-11
What have you tried so far?
I have an HP printer at home. To set it up I just installed HPLIP which (if I remember correctly) is available under the "Add/Remove" installer button. (Not sure about this though, I do not have access to an Ubuntu system at work).

---

### Post by dmadhawie on 2009-09-11
I tried hplip, but when I print a test page, the printer state change from idle->started a print job -> print job completed -> idle.
But no output.
I can even see the printer icon on the panel. It also disappear when it says that the job completed.
But nothing happens. :(

---

### Post by dmadhawie on 2009-09-26
Will Someone pls help me to configure my printer?

---

### Post by dmadhawie on 2009-09-26
Now I have installed HPLIP-3.9.8 and now it says the printer may not be connected...
Pls be kind to help
thanks

Madhawie

---

### Post by craigrose on 2010-02-20
I'm using Ubuntu 9.10 with the printer connected and turned on.  The printer was on when I booted.

When I try to use the HPLIP 3.9.12 I get a message "No installed HP devices found" and advice to run hp-setup, CUPS or a printer installation utility that came with the operating system.

So I try hp-setup selecting the USB connection type option.  This results in "No devices found".  Then I:
```
sudo lsusb
Bus 001 Device 004 ID 03f0:2b17 Hewlett-Packard LaserJet 1020

```
Then use manual discovery in hp-setup with bbb:ddd as 001:004.  Still reports no devices found.  Not sure if I have used the right numbers here?

CUPS 1.4.1 does not find the printer eithier.  There is just not a USB option available in the Local Printers list.

I presume the "Application that came with the operating system" refers to System->Administration->Printing.  Once again USB is not listed as an option so trying the "Other" option and the device URI.  Don't know the URI so I try "hp-info |fgrep device-uri" to find out.  This returns  error: no devices found.

Can anyone help?

---

