---
title: "USB/Parallel Port issue? (&quot;Printer not connected&quot;)"
date: 2014-08-01
forum: Hardware
---

### Post by baligirl on 2014-08-01
Hi everyone,

I'm on Ubuntu 12.04.LTS, trying to get my Canon PIXMA MX310 to work.  It has been working for several years, until recent months when it only prints when it feels like it, usually after a reboot.  My ultimate goal is to get the printer AND scanner to work.  I've been installing all sorts of stuff - CUPS, cnijfilter-common, gutenprint, downloading drivers from Asian Canon websites, I don't even know.  And uninstalled them all.  Even deleted my printer from the "Printing" app, and that was bad.  Took me a while to get that back, thanks to this thread:

[http://ubuntuforums.org/showthread.php?t=2084177](http://ubuntuforums.org/showthread.php?t=2084177)       The trick on that was to enter Device URI - parallel:/dev/usb/lp0

Fantastic, now it sees my printer!  The first time, I printed a test page, and got a blank page in the output tray.  But now, whether I try to print another test page, or  try to print a document, it says "Processing - not connected?"

So continuing to follow suggestions from the above thread, I do the following.  This is good, I believe, as it sees parport_pc, ppdev, and lp.

```

jennie@laverne2:~$ lsmod | grep par
parport_pc             32115  0 
sparse_keymap          13659  1 dell_wmi
parport                40931  3 parport_pc,ppdev,lp

```

Then I do the following, but I don't see a parallel port listed, as I was hoping:

```

jennie@laverne2:~$ lsusb
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)

```

I then try to "load" these modules, but this gives the same output as above.  So why does it not "load" these modules, why do I not see the parallel port listed when I do a "lsusb"?

```

$sudo modprobe ppdev
$sudo modprobe lp
$sudo modprobe parport_pc

```

I'm not sure if I'm on the right path here.  Any help would be appreciated, though please speak slowly(!) as I really don't know what I'm doing!

My next step after getting this printer to work, as I mentioned, would be the scanner.  Any recommendations on how to pursue that would also be appreciated.

thanks!!
Jennie

---

### Post by pdc on 2014-08-03
Hi Jennie;

I guess when I read Canon MX310 I think of a standard Canon printer; connected by usb cable to a stand-alone computer; so when you say > until recent months when it only prints when it feels like it, usually after a reboot. ...it is still connected by a usb connection?

I don't see the Canon listed in your > [COLOR="#FF0000"]lsusb[/COLOR] command: was it turned off when you did that command?

____________________

If you click on this link [http://localhost:631/printers/](http://localhost:631/printers/) it looks at printer admin on your system: in the right-hand column, is the only printer driver there called gutenprint? 

(Canon now supply linux drivers for all their printers but yours was a 2010 model and no linux driver is listed)

_____________

your post mentions parallel ports but that term is sort of misleading..........our usb connection printer is described as > direct parallel:/dev/lp0 in the command that asks the computer to list the printers (/usr/sbin/lpinfo -v) 

..........so the adjective parallel appears .............but it is not a parallel port ................... as we had 20yrs ago

---

### Post by baligirl on 2014-08-03
Hi PDC,

You say "is it connected?" and the error message says "printer not connected", and I thought "of course it's connected", but really, I should check on these things!  I saw the USB cable coming out of the back of the printer, and the USB cable going into my computer, but apparently they were not connected in the middle.  How many hours did that cost me, I wonder?

Just in case anyone else comes along with similar questions, I had in my notes (from before) to use the Canon MP150 driver, as the list doesn't have a driver choice for the MX310.  So now the CUPS website says:

```
Canon PIXMA MP150 - CUPS+Gutenprint v5.2.8-pre1
```

And when I type

```
lsusb
```

I see the following show up, which was not there before:

```

direct cnijusb:/dev/usb/lp0
direct cnijusb:/dev/usb/lp1
direct usb://Canon/MX310%20series?serial=117980&interface=1
direct usb://Canon/MX310%20series%20FAX?serial=117980&interface=2

```

It is a USB port, but I guess I was confused about the "lp0".  I will probably never understand that, and I'm okay with that...!

I got a lovely test page printout, plus a regular printout from one of my documents.

Thank you so much for replying, I had written myself off to a life of running to the library to make copies, never mind printing.  I am back in business again!!  Thank you so much!!!  :)

Jennie

---

### Post by baligirl on 2014-08-03
By the way, I also got the scanner to work!  Using gscan2pdf.  Before, it wasn't even finding a device.  Happy!!  :)

---

### Post by pdc on 2014-08-03
just checked back; delighted to hear all is working; enjoy

all the later commands you did looked much better!!!

By the way, do you have 2 printers connected? I ask because:

> [COLOR="#0000FF"]direct cnijusb:/dev/usb/lp0[/COLOR]
[COLOR="#008000"]direct cnijusb:/dev/usb/lp1[/COLOR]

suggests 2 canon printers and it is [COLOR="#EE82EE"]cnijusb[/COLOR]...................we also have 2 and they list as yours do..................so for the second to print I have to turn them on in the correct sequence...........till I get around to writing a udev rule

---

### Post by baligirl on 2014-08-03
Yes, much better!!

No, I only have the one printer, and in the standard "Printing" app, I have only the one listed as being present.   So why there seem to be two, I don't know.  I was playing with the "cnijfilter" drivers the other day, due to various posts pointing me in that direction, so maybe I have more installed than needed.  I am also wondering if the one is the "fax" portion of the printer.  I had tried to get that working several years ago, but I could not figure out the menus on the printer, and it kept spewing out fax reports without ever actually faxing.  So I somehow did a factory reset on it to make it stop.  Good thing there's a fax place down the street for that! haha....

---

### Post by pdc on 2014-08-03
> I am also wondering if the one is the "fax" portion of the printer.......could well be .......

> direct usb://Canon/MX310%20series%20FAX?serial=117980&interface=2

---

