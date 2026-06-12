---
title: "Epson wf-2540 can't setup in Ubuntu 14.04 64-bit"
date: 2014-06-05
forum: Hardware
---

### Post by Bao_Niu on 2014-06-05
I have tried every means that I can search online but it still not working. 
I've downloaded and tried every package from Epson's website, both for printer and for scanner.
And no luck at all, Ubuntu keeps saying that it cannot connect to the printer.

Does someone have any successful experience with epson wf-2540 under Ubuntu 14.04 64-bit? It becomes quite inconvenient.

---

### Post by Bao_Niu on 2014-06-05
If it is this particular make and model that is causing the problem, I don't mind investing another all-in-one printer/scanner. What is the most Ubuntu-compatible printer/scanner on the market? for 64-bit Ubuntu.

---

### Post by pdc on 2014-06-06
if you can open a terminal what does 

> dpkg -l | grep epson-inkjet-printer if you **copy** and **paste** it into a terminal?

and what does

> dpkg -l | grep iscan

how many printer drivers are listed here? [http://localhost:631/printers/](http://localhost:631/printers/)

Can you do a screenshot of this page?

Have you tried connecting the printer to your computer with a usb cable? Can you try that?

here is a debugging page [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) if you want to work through it

---

### Post by Bao_Niu on 2014-06-06
Hello pdc,

Thank you very much for helping.

Here is what I got from the terminal:
```
njh@njh:~$ dpkg -l | grep epson-inkjet-printer
njh@njh:~$ dpkg -l | grep iscan
ii  iscan                                                 2.29.3-1~usb0.1.ltdl7                               amd64        simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                                            1.28.0-2                                            all          Image Scan! for Linux data files
njh@njh:~$ 
```

Here is the screen capture for printers:
[ATTACH=CONFIG]253768[/ATTACH]

I've tried the whole afternoon and getting nowhere:(

By the way, I have been using the usb method all along, and no luck. I didn't even bother to try wifi, knowing it won't work.

---

### Post by pdc on 2014-06-06
so you seem to have the iscan data file; and the main iscan package installed; but you don't seem to have a printer driver installed;

Epson supply a printer driver from here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff)

for the printer: you need to click on [COLOR="#008000"]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_amd64.deb[/COLOR]

If you click to download, your system may offer to install with Ubuntu Software Centre: if it does, accept that kind offer; 

If you have already downloaded that file; and saved it to your Downloads directory, if you open that directory from your Desktop; and double-click on the file, your system should again offer to install with Ubuntu Software Centre: if it does, accept that kind offer; 

_________________________

If you get the installed, [COLOR="#008000"]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_amd64.deb[/COLOR] that should allow you to see an Epson WF-2540 icon to activate printing 

let us know how it goes

____________________--

also have a look at this page

[http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=Videos&oid=209708&prodoid=63095161&category=Products](http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&infoType=Videos&oid=209708&prodoid=63095161&category=Products)

Epson make a series of videos to help you; the video at top left talks about using the buttons on the Epson to connect to your router; the printer should find it; and you enter a password with the keypad on the Epson; you make like to do that in the future; but if we get you printing from usb first ...

---

### Post by Bao_Niu on 2014-06-06
Thank you very much pdc! It's really appreciated when someone in our forum goes this far to help!

I got the printer working at last! but not scanner. Simple Scan just freezes a while then disappear, without even trying to preview the scanning. Now that the printer is working, I have my hopes up and not junking this printer/scanner. Could you also help look into how to set up the scanner part?:P Many thanks!

Here is what I got from terminal:
njh@njh:~/Downloads$ dpkg -l | grep iscan 
ii  iscan                                                 2.29.3-1~usb0.1.ltdl7                               amd64        simple, easy to use scanner utility for EPSON scanners
ii  iscan-data                                            1.28.0-2                                            all          Image Scan! for Linux data files

---

### Post by pdc on 2014-06-06
I think that with Canon; and also I think Epson;

for the scanner........you either use their programmes: eg [COLOR="#0000FF"]ScanGearMP[/COLOR] for Canon                 [COLOR="#800080"] Iscan[/COLOR] for Epson

or use SANE which is the open-source derivative; so Simple Scan comes from SANE [http://www.sane-project.org/](http://www.sane-project.org/)

the SANE project folks don't necessarily own all the devices; so they need folks with these devices to tell them the ID of these devices; eg the WF series from Epson is not listed [http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

____________________--

so can you type > [COLOR="#FF0000"]lsusb[/COLOR] in a terminal please; and paste back what you get please

also > [COLOR="#FF0000"]sane-find-scanner[/COLOR]

____________________

Point is: to use [COLOR="#0000FF"]ScanGearMP[/COLOR] (for Canon devices) you need to type > [COLOR="#FF0000"]scangearmp[/COLOR] in a terminal...........and/or set up a launcher

so I think the same for [COLOR="#800080"] Iscan[/COLOR]      .........you need to open a terminal and type in > [COLOR="#FF0000"]iscan[/COLOR]   and if it is not good, try > sudo iscan

__________________________________________________________

I see that Epson say you can also run [COLOR="#EE82EE"]Iscan[/COLOR] from within GIMP: so perhaps you open [COLOR="#A52A2A"]GIMP[/COLOR] and see if you can spot an [COLOR="#EE82EE"]Iscan[/COLOR] entry: ..........start at **FILE** top left; down 2 to **CREATE** and out to the sub-menu.............is there an Iscan entry there?

---

### Post by Bao_Niu on 2014-06-06
Hi pdc, thanks again for your help. Here is the feedback from my terminal:
> 
njh@njh:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 005: ID 0489:e056 Foxconn / Hon Hai 
Bus 002 Device 002: ID 1bcf:2c67 Sunplus Innovation Technology Inc. 
Bus 002 Device 006: ID 04b8:08a6 Seiko Epson Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
njh@njh:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x8000 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc00e at 002:004: Access denied (insufficient permissions)
could not open USB device 0x0489/0xe056 at 002:005: Access denied (insufficient permissions)
could not open USB device 0x1bcf/0x2c67 at 002:002: Access denied (insufficient permissions)
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
njh@njh:~$ 


In addition, typing in either "iscan" or "sudo iscan" will only cause long time waiting with the cursor flashing pointlessly. 
> njh@njh:~$ iscan
^C
njh@njh:~$ sudo iscan
[sudo] password for njh: 


Looks like the shell located the application called "iscan" but doesn't know what to do about it...

I just tried GIMP, yes there is an Iscan entry there, but after clicking on it, nothing happens, just the same with simple scan or from terminal.

---

### Post by Bao_Niu on 2014-06-06
I just tried using sudo with sane-find-scanner and here is the feedback:
> njh@njh:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
njh@njh:~$ 


This is weird, the scanner is connected and powered on, actually I just printed a test page to ensure the connection is ok. All the drivers are installed. It still can't detect my scanner.

---

### Post by Bao_Niu on 2014-06-06
Could this have something to do with the 64-bit kernel? I remember last year I successfully scanned once using Ubuntu 13.04 32-bit connected to this same scanner/printer. Does anybody have any success with this make and model under Ubuntu 14.04 64-bit so far?

---

### Post by pdc on 2014-06-06
there seem to be epson ..........scanning..........and 14.04 issues ..................

if we see what groups you are a member of ......if you type > groups .........you should be in plugdev; can you copy and paste what you get

---

### Post by Bao_Niu on 2014-06-06
Ok, here is what I got:
> njh@njh:~$ groups
njh adm cdrom sudo dip plugdev lpadmin sambashare
njh@njh:~$ 


---

### Post by cfuser on 2014-12-08
Did this ever get resolved?  I'm having the same issue w/ a networked WF-2540.  TIA.

---

