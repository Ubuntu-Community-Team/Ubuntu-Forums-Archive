---
title: "HELP: I've screwed up my Brother Printer Settings and can't connect anymore"
date: 2016-10-24
forum: Hardware
---

### Post by stevecoh1 on 2016-10-24
About 2 hours ago in a fit of stupidity, I connected to my Brother HL-5370DW printer's web interface and mistakenly turned on the APIPA setting, thinking this might help my wife's windows PC connect to it.

I can't undo this.  I can no longer connect via the old IP address.  I don't know what the APIPA IP address is (it is "automatically" chosen from a range, which is, in any event, outside my router's network).  If I connect the printer via USB, the utilities available (BRAdminLight from a Windows box) do not find the printer.  Yet, when I connect the USB cable to my Ubuntu box, I can print.  Please, how may I talk to the network's interface to turn APIPA back off.

---

### Post by ajgreeny on 2016-10-24
Does your browser keep history which will show you the web IP address?

---

### Post by howefield on 2016-10-24
Try browsing the cups webpage at localhost:631

Go to the Printers page and click on your model..

---

### Post by stevecoh1 on 2016-10-24
> **ajgreeny said:**
> Does your browser keep history which will show you the web IP address?

That's just the point.  APIPA changes to the IP address of the printer to one that is both not on my network and unknown to me even if it was on my network.

---

### Post by stevecoh1 on 2016-10-24
> **howefield said:**
> Try browsing the cups webpage at localhost:631

Go to the Printers page and click on your model..

Tried this - the most promising idea I've had so far - but localhost:631 is looking for a username/password that I don't know.  It's not my username/password on the machine, nor is it the default username/password of the printer (after resetting to factory defaults).  Anybody know what it is looking for?

---

### Post by Bucky Ball on 2016-10-24
I have a Brother printer. The HL-2270DW. Best thing to do is take it offline altogether for the moment, jam a USB cable in and work with it that way. They can be stubborn. If you have a Win machine, even better as they have an easy setup app which you can use to configure the machine how you like and 'prepare' it for running with Linux, set static IP address, set up for wireless etc. 

That may be the only way to get around this. I've had to resort to the Win option once to access mine when things got pear-shaped with the wireless.

---

### Post by stevecoh1 on 2016-10-24
> **Bucky Ball said:**
> I have a Brother printer. The HL-2270DW. Best thing to do is take it offline altogether for the moment, jam a USB cable in and work with it that way. They can be stubborn. If you have a Win machine, even better as they have an easy setup app which you can use to configure the machine how you like and 'prepare' it for running with Linux, set static IP address, set up for wireless etc. 

That may be the only way to get around this. I've had to resort to the Win option once to access mine when things got pear-shaped with the wireless.

Thanks.  Not having any luck with this.  Though I was at least printing through USB before, now that I've removed the ethernet cable from the printer, I can't get the printer detected either on my LInux machine or a windows box, either to print with or to configure!  Almost thinking of getting rid of this piece of junk.  Only question is what's better.

---

### Post by howefield on 2016-10-24
> **stevecoh1 said:**
> Tried this - the most promising idea I've had so far - but localhost:631 is looking for a username/password that I don't know.  It's not my username/password on the machine, nor is it the default username/password of the printer (after resetting to factory defaults).  Anybody know what it is looking for?

Hmm, that's a blow.. what does the "Restrict access to the admin pages" section look like in the /etc/cups/cupsd.conf file ?

Mine look like the following..

```
# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>
```

---

### Post by stevecoh1 on 2016-10-24
> **stevecoh1 said:**
> Thanks.  Not having any luck with this.  Though I was at least printing through USB before, now that I've removed the ethernet cable from the printer, I can't get the printer detected either on my LInux machine or a windows box, either to print with or to configure!  Almost thinking of getting rid of this piece of junk.  Only question is what's better.

And where to find such info.  I go to the Open Printing website ([http://www.openprinting.org/printer/Brother/Brother-HL-5370DW](http://www.openprinting.org/printer/Brother/Brother-HL-5370DW)) where I am directed to the ["Printers From Brother Forum"]("http://forums.openprinting.org/list.php?24"), which turns out to be an unmoderated collection of random crap having nothing to do with the supposed subject at hand.  Where does the Linux user go these days to find real information about good printers?

---

### Post by stevecoh1 on 2016-10-24
> **howefield said:**
> Hmm, that's a blow.. what does the "Restrict access to the admin pages" section look like in the /etc/cups/cupsd.conf file ?

Mine look like the following..

```
# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>
```

Mine is the same.

---

### Post by stevecoh1 on 2016-10-24
Hmm, I think that the root of my problem is that the printer or my usb cable is bad:
running the command 

```
sudo udevadm monitor --udev
```


I start to see output like this cycling every couple of seconds:

```
UDEV  [70933.177922] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/usbmisc/lp1 (usbmisc)
UDEV  [70938.177599] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/usbmisc/lp1 (usbmisc)
UDEV  [70938.180722] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/usbmisc/lp1 (usbmisc)
UDEV  [70943.185443] remove   /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/usbmisc/lp1 (usbmisc)
UDEV  [70943.189899] add      /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/usbmisc/lp1 (usbmisc)
```

Something is causing the computer not to maintain a stable connection with the printer.  This would explain why I'm not having any success with any computer Linux or Windows that I try to connect this beast to.

---

### Post by Bucky Ball on 2016-10-24
While I understand your frustration, no idea why you're in 'open printing' site. This is easy. [Go here]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl5370dw_us&os=128") and download the 'Driver Install Tool' for Linux. Follow the instructions and see how that goes. 

Failing that, [go here]("http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hl5370dw_us") and download the Win driver and use that. Even easier. 

Seem to be making this harder than it is. I'd be suprised if the Win installer didn't pick the machine up with a USB. Suprised if the Linux Driver Install Tool didn't either, but that may not fix your issue. The Win one probably will.

---

### Post by stevecoh1 on 2016-10-25
> **Bucky Ball said:**
> While I understand your frustration, no idea why you're in 'open printing' site. This is easy. [Go here]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl5370dw_us&os=128") and download the 'Driver Install Tool' for Linux. Follow the instructions and see how that goes. 

Failing that, [go here]("http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hl5370dw_us") and download the Win driver and use that. Even easier. 

Seem to be making this harder than it is. I'd be suprised if the Win installer didn't pick the machine up with a USB. Suprised if the Linux Driver Install Tool didn't either, but that may not fix your issue. The Win one probably will.

Was in Open Printing because already thinking of getting new printer, doing research.  Now, have ordered one.  See my previous message.  When I saw that the printer couldn't maintain a solid USB connection, that explained everything.  ON 3 different computers I couldn't get anything to recognize the USB connection.  I could possibly have tried a different USB cable, but in truth, I'm tired of fighting with Brother and my wife wanted a printer that can do color.

---

