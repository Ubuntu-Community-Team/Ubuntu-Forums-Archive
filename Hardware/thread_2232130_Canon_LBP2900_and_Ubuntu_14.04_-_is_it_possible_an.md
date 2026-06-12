---
title: "Canon LBP2900 and Ubuntu 14.04 - is it possible anymore?"
date: 2014-06-30
forum: Hardware
---

### Post by forbajato on 2014-06-30
I have been using a Canon LBP2900 for years, solid printer, poorly supported.  I started out after this upgrade trying to get it to work on a Raspberry Pi Raspbian install as a network printer - finally came to a page on OpenText which identifies this printer as "Paperweight". Decided to switch to hooking it up directly to a desktop machine.

In the past I have been able to get it working with the tutorial  [here]("http://ubuntuforums.org/showthread.php?t=1983091").  The problem arises at step 2, trying to install old libraries that the Canon driver needs to access (I assume these are required by the Canon driver). The ia32libs package from Oneric, suggested by the tutorial is not longer available, the link for that library only has LTS packages available.  Also the lib32asound and lib32ffi6 libraries are not available in 14.04.

On a lark I even decided to try the instructions from Canon - also no go (the captstatusui command gives the error "Check the DevicePath of /etc/ccpd.conf" - checked it and it points to /dev/usb/lp0 as I think it is supposed to).

Is it even possible to still use this printer in Ubuntu 14.04?

thomas

---

### Post by pdc on 2014-07-01
Hi Thomas;

you don't say if you are using 32bit or 64bit: .............I would suggest that you would be best served with a 32bit system; 

Canon attempt to cover all the differing permutations of differing distros: for 64bit ubuntu they say you need to add 

libglade2
ia32-libs
libpopt0:i386

__________

I think a very good guide is here [http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp) 

........yes.........it is in French but google translate does a good job................*except for the spaces in the command lines* so one needs to refer back to the french; 

for the CAPT drivers there seem to be four steps:

1) install drivers
2) install in CUPS
3) register in the CCPD daemon
4) start the ccpd daemon 

( we have an LBP3100 working fine in a 32bit 12.04 ubuntu; using Sivella's excellent guide)

---

### Post by forbajato on 2014-07-02
This is actually what I have been thinking I may need to do, drop back to my old eeePC and set it up as a printer server for the network (just wish the drivers worked on ARM, my raspberryPi is just sitting there looking forlorn).  You don't happen to have gotten a Canon printer working on 14.04 have you?

---

### Post by pdc on 2014-07-02
> You don't happen to have gotten a Canon printer working on 14.04 have you?  ..........no; I let the brave explore new releases ........

---

### Post by forbajato on 2014-07-15
Got it working on a eeePC using Lubuntu 14.04.  Nothing unusual required, just followed the Canon instructions and the tutorial [here]("http://help.ubuntu.com/community/CanonCaptDrv190").  Bottom line - it is possible.

Now I just need to solve the network sharing problem - prints from the CUPS web interface but not from applications running on the networked computers.

thomas

---

### Post by pdc on 2014-07-15
glad to hear it is working well; well done; a very good solution; 32bit seems absolutely fine; 

> prints from the CUPS web interface but not from applications running on the networked computers.

is there anything here of help? It seems the "shared" option that can trip folks up: one needs to ensure the shared

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by forbajato on 2014-07-16
I have tried the pointers there and [here]("http://kb.haeringer.org/share-usb-printer-on-the-network-via-cups-and-ipp/") but still no joy.  This must be possible, just can't figure out what is going wrong!

thomas

---

### Post by pdc on 2014-07-16
would you wish to describe the relations between the Eee with the working LBP; and your other computers?

here is an ubuntu debugging wiki for printers: at the networking area [https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer](https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer)

---

### Post by forbajato on 2014-07-17
This printer is connected to an old eeePC via USB, not directly connected to the network.  The eeePC has a fixed IP address on the network and works fine with the printer itself.  When I connect to the eeePC's address, port 631 from a computer on the network I see the CUPS page (the general first page for the cups server).  From there I can go to Printers tab, choose my printer and from the maintenance drop down print a test page, all from a different computer on the network.  

I can install the printer on a networked computer using the Printers tab from Settings (using UbuntuGnome),  can set the printer as default.  The problem comes when I try to print to that printer from something running on the networked computer (like, say, LibreWriter).  The system tells me the job is sent, then I get a notification that the job is complete but nothing comes out of the printer and no job is registered on the CUPS server page.

Everything on that wiki page goes great until I get to step 8 - 
```
/usr/lib/cups/backend/snmp
```
returns nothing.  As suggested in step 9, doing snmp with sudo doesn't help.
```
sudo /usr/lib/cups/backend/dnssd
```
returns 
```
DEBUG: sent=0, count=0
DEBUG: sent=0, count=0
DEBUG: sent=0, count=0
DEBUG: sent=0, count=0
DEBUG: sent=0, count=0

```
Which looks kind of ominous.

I am not sure how to interpret the output of the ```
lpinfo -v
``` or the ```
avahi-browse -a -v -t -r
``` and the ```
ahvahi-browse -a -v -c -r
``` but the computer with the printer connected is not listed in their output at all.

It looks like, for whatever reason, the connection is not complete, any ideas how to fix that?

[EDIT] Casting about for a fix and found this: [http://ubuntuforums.org/showthread.php?t=2227748&highlight=Network+Printer](http://ubuntuforums.org/showthread.php?t=2227748&highlight=Network+Printer)

In that it looks like Paper Pusher got his working by allowing printing from the Internet on the computer serving the printer, that didn't work for me.  Also, the screenshot (attached) that I keep seeing has a check box that 14.04 doesn't seem to have anymore - I doubt it makes a difference but thought I would point it out.  On the screenshot there is a checkbox for "Show printers shared by other systems" - that doesn't show up anymore in the Printer>Server>Settings dialog box.

---

