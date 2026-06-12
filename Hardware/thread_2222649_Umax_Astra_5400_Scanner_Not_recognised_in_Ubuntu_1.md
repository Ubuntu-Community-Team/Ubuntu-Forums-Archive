---
title: "Umax Astra 5400 Scanner Not recognised in Ubuntu 12.04"
date: 2014-05-07
forum: Hardware
---

### Post by davethesteam on 2014-05-07
Please help me on this - I am at my wits end in trying to get this thing to work!!!.
I have gone through all the processes on the Community help page - very well written and understandable to the likes of me.
Still no working scanner though. 
The read out on simple scan debug is as follows:

]david@david-All-Series:~$ simple-scan -d Umax

** (simple-scan:5783): WARNING **: scanner.vala:818: Unable to get open device: Invalid argument

** (simple-scan:5783): WARNING **: scanner.vala:1151: Unable to start device: Error during device I/O[/I]

I have also reviewed scanimage -L which reads as follows:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

And tried 
Sane-find-scanner with following readout:
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x1606 [UMAX], product=0x0160 [USB SCANNER]) at libusb:003:007
found USB scanner (vendor=0x0471, product=0x0330) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
I have gone into gedit and written in the 2 scanner types identified (deleting one before the other inputted) - still no functioning scanner.

Could you please help me??
Many thanks in  anticipation

---

### Post by pdc on 2014-05-08
Hi Dave; you have certainly done your homework: I feel very concerned your device is not recognised or mentioned on the SANE supported devices list: UMAX seems to have a lot of unsupported devices ...............

[http://www.sane-project.org/sane-mfgs.html#Z-UMAX](http://www.sane-project.org/sane-mfgs.html#Z-UMAX)

this is your device?

[http://www.ebay.co.uk/itm/Umax-Astra-5400-Flatbed-Scanner-with-PSU-USB-Cable-/181293426027](http://www.ebay.co.uk/itm/Umax-Astra-5400-Flatbed-Scanner-with-PSU-USB-Cable-/181293426027)

you can pull your hair out for weeks on end with something like this ............ I have suggested to a number of folks in similar circumstances they consider looking for a second-hand compatible device: eg we picked up a Canon CanoScan N560U for a song and it literally was plug and play; ( in comparison, one can't even find a backend listed that might drive your device); 

eg this 

[http://www.ebay.co.uk/itm/Canon-CanoScan-N670U-Flatbed-Scanner-/271476966215?pt=UK_Scanners&hash=item3f3549c347](http://www.ebay.co.uk/itm/Canon-CanoScan-N670U-Flatbed-Scanner-/271476966215?pt=UK_Scanners&hash=item3f3549c347) is completely supported; sorry if this irritates you

---

### Post by davethesteam on 2014-05-10
Hi pdc
Thank you for taking the time to answer.

The following is the entry in SANE:
UMAX 5400 	USB 	0x1606/0x0160 	Complete 	  	plustek
(0.52) 	sane-plustek

so I now need to know how to get that backend into my system - my knowledge of installing such things is minus 0

or, by it being there, does it not neccesarlity mean the machine will work?
Or should I rebuild the gedit files - if so, how can I do this?

To answer your question - yes, it is the machine I have - I hate to say it, but it works perfectly in Windows XP but not at all on Win Vista

---

### Post by pdc on 2014-05-10
from here ........ [http://www.sane-project.org/sane-mfgs.html#Z-UMAX](http://www.sane-project.org/sane-mfgs.html#Z-UMAX)

```
UMAX 5400 	USB 	0x1606/0x0160 	[COLOR="#008000"]Complete[/COLOR] 	  	plustek (0.52) 	sane-plustek
```

.............well............I was searching under Astra and I couldn't find it ........as you say it is just called Umax 5400 and ......complete support..........our Canon with a similar rating was plug and play ............

the backend plustek [http://www.gjaeger.de/scanner/plustek/](http://www.gjaeger.de/scanner/plustek/) should be installed already; and the man-page is sane-plustek [http://www.sane-project.org/man/sane-plustek.5.html](http://www.sane-project.org/man/sane-plustek.5.html)

and it is mentioned clearly in the sane-plustek.5 page

```
Vendor UMAX - ID: 0x1606
       ----------------------------------------------------------
       USB Model:         ASIC:  Properties:              Prod-ID
       ----------------------------------------------------------
       UMAX 3400          LM9832  600x1200dpi 42bit 512Kb 0x0050
       UMAX 3400/3450     LM9832  600x1200dpi 42bit 512Kb 0x0060
       UMAX 5400          LM9832 1200x2400dpi 42bit 512Kb 0x0160
```

I looked in the file /etc/sane.d/plustek.conf and I am thinking you need to create an entry there to mention your device; 

you can read the file with the command > [COLOR="#FF0000"]gedit /etc/sane.d/plustek.conf[/COLOR]             and you can EDIT the file by closing gedit (which is a text editor) and then this command > [COLOR="#FF0000"]gksudo gedit /etc/sane.d/plustek.conf[/COLOR]


so the file plustek.conf says 

```
# each device needs at least two lines:
# - [usb] vendor-ID and product-ID
# - device devicename
# i.e. for Plustek (0x07B3) UT12/16/24 (0x0017)
# [usb] 0x07B3 0x0017
# device /dev/usbscanner
```

and [http://www.sane-project.org/man/sane-plustek.5.html](http://www.sane-project.org/man/sane-plustek.5.html) says the same ...............

> [COLOR="#A52A2A"]To use your scanner with this backend, you need at least two entries in the configuration file /etc/sane.d/plustek.conf[/COLOR]
              [usb] vendor-id product-id
              device /dev/usbscanner

[usb] tells the backend, that the following devicename (here  /dev/usbscanner) has to be interpreted as USB scanner device.

so I think you would paste in an entry .........anywhere in the file..........saying

> 
# UMAX 5400 USB
usb 0x1606 0x0160
device /dev/usbscanner


 SAVE and CLOSE gedit; 

______________________________________________________________________________________________________________

I also think we should register your scanner in the file /lib/udev/rules.d/40-libsane.rules

again > gksudo gedit /lib/udev/rules.d/40-libsane.rules 

add > ATTRS{idVendor}=="1606", ATTRS{idProduct}=="0160", ENV{libsane_matched}="yes"
# UMAX Astra 5400

SAVE: close

reboot...............any joy?

---

### Post by davethesteam on 2014-05-19
Hello pdc
Again, many thanks for the reply and apologies for taking so long to reply.
Regret however, that the solutions proposed did not work.
I have to take a break for now as my computer is going into storage for about 2 weeks.
Perhaps you could help again for my return. 
All help much appreciated

---

### Post by pdc on 2014-05-19
I think if you carry out the recommendations of the previous post; and evaluate from there

have a good break

---

