---
title: "Help:  adding HP Laserjet 1100 printer connected via USB"
date: 2009-06-04
forum: Hardware
---

### Post by wacky_keyboards on 2009-06-04
I'm running Ubuntu 8.04 (Intrepid Ibix) and am trying to connect an old HP Laserjet 1100.  The twist is that the printer relies on the old mini-Centronics (aka DB-25 and Centronics-25) parallel connector, but my laptop does not have any such port.  It *does* however have plenty of USB ports, so I bought a USB<->mini-Centronics adapter and plugged it in.  Unfortunately, I have been unable to get the system to recognize that there is a printer now connected via USB.

Any help would be greatly appreciated!

---

### Post by Lampi on 2009-06-04
first make sure your usb2parallel adapter gets recognized correctly by your ubuntu

Usually you plug it in and watch dmesg and syslog - it should assign a new /dev device if you plug it in. Dmesg shows you which one it is.

---

### Post by wacky_keyboards on 2009-06-04
Thanks for the suggestions!

Checking dmesg, I see 3 new messages when I plug the usb2parallel
adapter:

     [ 5130.890404] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
     [ 5131.440198] usb 2-2: new full speed USB device using uhci_hcd and address 4
     [ 5131.595039] usb 2-2: configuration #1 chosen from 1 choice

There are also 4 recent /dev/usb* entries:

     /dev/usbdev2.4_ep00
     /dev/usbdev2.4_ep02
     /dev/usbdev2.4_ep81
     /dev/usbdev2.4_ep87

What should I do next?

---

### Post by wacky_keyboards on 2009-09-10
In case anyone is wondering, here's my "final" resolution on this:

I decided to see if a solution existed under Windows.  While a
lack of one doesn't necessarily imply that it won't exist under
Linux (or Ubuntu), I'm more likely to throw in the towel in such
a case.

A bit of searching turned up numerous posts of people having
tried this and failed, in particular because there is no
suitable driver for Windows Vista (64-bits).  There were a
couple of customer comments that I had discovered on Amazon.com
and elsewhere for different manufacturers of the USB<->DB25
adapter that pretty much said "stay away; this 'solution' does
not work."

So, my solution is to recycle the printer (at a store that is
providing me $50 credit for bringing in old HP printers), and
buy a networked one (which should eliminate the connectivity
issue for as long as Ethernet survives B-).

---

