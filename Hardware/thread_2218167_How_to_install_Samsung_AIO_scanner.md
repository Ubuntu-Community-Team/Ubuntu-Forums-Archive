---
title: "How to install Samsung AIO scanner?"
date: 2014-04-19
forum: Hardware
---

### Post by Odyssey1942 on 2014-04-19
We have an oldie (but goldie) Samsung All In One networked printer/copier/scanner/fax machine, model SCX-4826FN which until very recently has been connected to an XP computer which did little other than scanning and as a guest computer. XP has gone away, and so this computer will be converted to Ubuntu.

This is being written on a 12.04 computer which, after a considerable amount of hocus-pocus, finally will print on the AIO. Hocus-pocus because I really do not understand how I managed to make it print. Took awhile though.

I do remember that I downloaded a universal linux package from the Samsung website, but could find no instructions on the Samsung site as to how to install it. So there was a lot of googling, guessing, and trying to get the printing working.

I have not a clue as to how to get the scanner to operate from this computer. On "System Settings", there is a printer icon, but nothing for a scanner

Any suggestions will be appreciated.

---

### Post by Elfy on 2014-04-20
*Thread moved to **Hardware**.*

---

### Post by pdc on 2014-04-20
there is a place called SANE in the linux world: it stands for Scanner Access Now Easy;

[http://www.sane-project.org/](http://www.sane-project.org/)

If one drills down inside the site and looks for Samsung, your printer is not mentioned but a cluster of numbers around yours suggests it should be good;

> SCX-4824 (SCX-4x24 Series) USB 	0x04e8/0x342c 	[COLOR="#0000FF"]Good [/COLOR]	  	xerox_mfp (1.0-13) 	sane-xerox_mfp
              SCX-4825FN (SCX-4x25 Series) 	USB 	0x04e8/0x343c 	[COLOR="#0000FF"]Good [/COLOR]	  	xerox_mfp (1.0-13) 	sane-xerox_mfp
              SCX-4828FN (SCX-4x28 Series) 	USB 	0x04e8/0x342d 	[COLOR="#0000FF"]Good [/COLOR]	  	xerox_mfp (1.0-13) 	sane-xerox_mfp

You should have a programme called simple scan on  your system: if you use the Dash, the search button and type simple scan into it .............can it find it? 

First thing to see is will it scan without any tinkering.................

If found, but not working....................

If we check if you are in the scanner group; so permitted to use a scanner! If you are able to paste this command into a terminal please

> [COLOR="#FF0000"]grep -e scanner /etc/group[/COLOR]

and if you install the supplementary libraries for sane 

> [COLOR="#FF0000"]sudo apt-get install libsane-extras[/COLOR]

(with the sudo command, you will asked for your password, so if you have it handy......)

---

### Post by Odyssey1942 on 2014-04-20
Thanks for yours. 

1) I did find simple scan which was under Graphics, not Office. Feel silly in retrospect, but did not look there before. It could not find a scanner.

2) Went to the sane URL you mentioned and clicked on the link beside: "SCX-4828FN (SCX-4x28 Series)" which took me to a page:

[http://www.sane-project.org/man/sane-xerox_mfp.5.html](http://www.sane-project.org/man/sane-xerox_mfp.5.html)

It wasn't clear to me what to do next so I clicked on 

sane-xerox_mfp(5)

but I could not tell anything happened.

3) opened simple scan again and it just said it could not find a scanner. Do I need to somehow input an IP# or something?

Completely confounded by this.

---

### Post by pdc on 2014-04-20
pleased to help Odyssey;

if you do the 2 commands I suggested; > grep -e scanner /etc/group and > sudo apt-get install libsane-extras

and as well can you 

> [COLOR="#FF0000"]sane-find-scanner[/COLOR]

> [COLOR="#FF0000"]scanimage -L[/COLOR]

> [COLOR="#FF0000"]sudo sane-find-scanner[/COLOR]

> [COLOR="#FF0000"]sudo scanimage -L[/COLOR]

If you paste back details; if it gives you details; if it says: no scanner........well, you can tell me that

oh, and this command > [COLOR="#FF0000"]lsusb[/COLOR]

---

### Post by Odyssey1942 on 2014-04-20
Sorry, I forgot to mention that I did run the two commands with these results:

> $ grep -e scanner /etc/group
scanner: x:107:


and this:
> ~$ sudo apt-get install libsane-extras
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1 thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsane-extras-common
The following NEW packages will be installed:
  libsane-extras libsane-extras-common
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 65.5 kB of archives.
After this operation, 303 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libsane-extras-common amd64 1.0.22.2 [7,534 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libsane-extras amd64 1.0.22.2 [57.9 kB]
Fetched 65.5 kB in 1s (38.1 kB/s)    
Selecting previously unselected package libsane-extras-common.
(Reading database ... 270793 files and directories currently installed.)
Unpacking libsane-extras-common (from .../libsane-extras-common_1.0.22.2_amd64.deb) ...
Selecting previously unselected package libsane-extras.
Unpacking libsane-extras (from .../libsane-extras_1.0.22.2_amd64.deb) ...
Processing triggers for man-db ...
Setting up libsane-extras-common (1.0.22.2) ...
Setting up libsane-extras (1.0.22.2) ...


Here are the results of the other commands:

> ~$ sudo sane-find-scanner
[sudo] password for robert: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


> $ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


> $ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

> $ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


> ~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver

Also attempted again to run Simple Scan/scan and got this result:

> Failed to scan

No scanners available. Please connect a scanner.

---

### Post by pdc on 2014-04-20
thanks;

so you aren't a member of the scanning group; from my system I get > pdc@pdc-MS-7610 ~ $ grep -e scanner /etc/group scanner:x:107:[COLOR="#0000FF"]pdc[/COLOR] 

.........but we can do that later; 

........I can't see your Samsung listed at all in the lsusb reading .........can you see it mentioned there..........?? (it should say 0x[COLOR="#0000FF"]**04e8**[/COLOR]/0x342c or something similar ........)        *04e8 is Samsung's manufacturer's callsign*

so we check out the usual suspects.................plugged in.........turned on ..........usb3 port?? ........usb hub..??............. these can all be problems ...plug it into a port you know works..........try lsusb again (it is saying: LIST what is connected to USB)..............

.............does it show up..........it needs to be seen there first of all ...................

---

### Post by Odyssey1942 on 2014-04-21
Thanks for your additional. Apology, I should have understood sooner, but the AIO is networked. It works fine with the old XP machine which remains offline except when we need to scan something when we unplug from the internet, plug in the eth cable to the PC, do our scanning, remove the eth cable, and go back online. (Works OK til I can get the 12.04 to see the AIO) In any case it is functioning correctly with the XP and it seems to be a matter of getting 12.04 to locate it and setting up the appropriate software to drive it (so all connections are OK)

BTW, in case it matters, I use Gnome Classic in 12.04 rather than Unity.

---

### Post by pdc on 2014-04-21
I think we do need you to join it by usb cable;

to identify its ID: (found out by typing lsusb when plugged in and joined up);

if you click on the link you said you had read [http://www.sane-project.org/man/sane-xerox_mfp.5.html](http://www.sane-project.org/man/sane-xerox_mfp.5.html)

you can see near the end the AUTHOR of the file...........that make Samsung devices work on linux;

you will need to tell that to him; (to help you and others); (he gives his email address and is keen to have the ID of devices); and then your file can be edited; so the computer knows it is seeing your device as a scanner; 

...........I am guessing once recognised over usb that it can then be set up as a network scanner........................

---

### Post by Odyssey1942 on 2014-04-21
Great stuff. Off on a trip tomorrow through next week, but will work on this upon return and report back in due course.

---

### Post by Odyssey1942 on 2014-05-03
I can do as requested, but don't have a long enough USB cable and so will involve a lot of moving things around.

Before I do that, the printer can print out network info (and maybe other stuff)  such as 
Host Name, 
MAC address, 
IP address, 
Printer URI

Would any of these be the ID needed? I did not see anything with any of the "0x04e8/0x342c" mentioned above.

There is a menu system built into the AIO, so if none in the above list would produce the desired ID, might there be another menu selection that would produce the desired info?

---

### Post by Odyssey1942 on 2014-05-05
Have obtained this device ids from Samsung. It is for a SCX-4828, but the tech thought it would be the same for the 4826

0x04e8/0x342d

---

### Post by pdc on 2014-05-05
..........to get a scannner going over the network, you need some or all of what is in here .......... [https://help.ubuntu.com/community/ScanningHowTo#Sharing_a_Scanner_Over_a_Network](https://help.ubuntu.com/community/ScanningHowTo#Sharing_a_Scanner_Over_a_Network) (which we can give you commands to paste into a terminal)

I don't know who set up your network; but a bit of lateral thinking suggests that one can buy a second-hand scanner; to connect via usb port; many countries have lists you can search for such things; for about $US30 in many countries one can buy a printer with a scanner built-in; eg the I see the CanonMG2100 series at that price; and Brother and Epson have similar models; just a thought;

---

### Post by Odyssey1942 on 2014-05-05
pdc, many thanks for that link. Will give it a good read and follow those instructions. Doubtless will have more questions, and if so, will be back.

Excellent suggestion (lateral thinking), but the scanner worked very well with the XP computer, so if we can get it working with Linux, that will be our preference. It also has an automatic document feed which is a very desirable feature, plus copying and faxing, and there isn't very much desk space so adding another item is problematic. Very tempting nonetheless so that I could skip all this configuration challenge.

---

