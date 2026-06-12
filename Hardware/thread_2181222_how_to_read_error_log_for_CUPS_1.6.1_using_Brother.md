---
title: "how to read error log for CUPS 1.6.1 using Brother printer/scanner MFC-7840W"
date: 2013-10-16
forum: Hardware
---

### Post by datamason on 2013-10-16
I am trying to learn how to interprete the error logs so I can fix various problems with Brother printing. I am using 64bit Mint 14 Cinanamon on a no-name machine. For the same printer, MFC-7840W All-in-One, I installed two drivers, one viewing the printer as a LAN printer, the other through the USB port. I followed Brother's driver installation instructions and did this some months ago, so I no longer can say specifically which steps I took to do the installation, other than follow Brother's instructions the best I can. When I say, two drivers, I cannot say if they are different drivers from Brother, or merely the result of following the separate instructions for first a printer, then the scanner. I only remember that I could get the scanner to work only through the USB port. 

I cannot print from Firefox, but can print from the Evince Document Viewer, so let's stick my printing from a local file.

My goal is to learn how to read the error logs so I can fix my printer issues without posting to the forum for each one. 

I tried uploading 3 files, but the one of 15 kb zipped will not upload. Don't know why and I cannot find the rules for uploading on this forum. Instead there is my config file plus the error log of successful printing from Evince File Viewer using the USB port. Printing from Okular on USB failed. 

I cannot find via Google instructions for interpreting the error logs. I would appreciate anyone pointing me in the right direction.
mm

---

### Post by tgalati4 on 2013-10-17
Rather than post the entire error log, just post the lines of the first few errors.  Use cut and paste and use quote tags.  Brother printers can be problematic, but with some effort, you should be able to get everything fixed.  Patience is key.

---

### Post by datamason on 2013-10-18
Ok,tgalait4, thanks for the tip.

The following log was generated while printing from Evince Doc Viewer. Nonetheless, the document printed successfully.
> D [16/Oct/2013:20:27:48 -0400] Created device "/org/freedesktop/ColorManager/devices/cups_BrotherMFC_7840W_USB".
D [16/Oct/2013:20:27:48 -0400] Calling /org/freedesktop/ColorManager/devices/cups_BrotherMFC_7840W_USB:AddProfile(/org/freedesktop/ColorManager/profiles/BrotherMFC_7840W_USB_Gray__) [soft]
W [16/Oct/2013:20:27:48 -0400] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_BrotherMFC_7840W_USB
D [16/Oct/2013:20:27:48 -0400] Calling FindDeviceById(cups-MFC-7840W)

The following log was generated while printing from Okular. The document did not print.
> D [16/Oct/2013:20:05:49 -0400] Created device "/org/freedesktop/ColorManager/devices/cups_BrotherMFC_7840W_USB".
D [16/Oct/2013:20:05:49 -0400] Calling /org/freedesktop/ColorManager/devices/cups_BrotherMFC_7840W_USB:AddProfile(/org/freedesktop/ColorManager/profiles/BrotherMFC_7840W_USB_Gray__) [soft]
W [16/Oct/2013:20:05:49 -0400] AddProfile failed: org.freedesktop.DBus.Error.UnknownMethod:No such interface `org.freedesktop.ColorManager' on object at path /org/freedesktop/ColorManager/devices/cups_BrotherMFC_7840W_USB
D [16/Oct/2013:20:05:49 -0400] Calling FindDeviceById(cups-MFC-7840W)


Hope this is intelligible to someone here.

---

### Post by tgalati4 on 2013-10-18
A little search brought up this link:  [http://unix.stackexchange.com/questions/80571/cups-error-log-contains-no-such-interface-org-freedesktop-colormanager](http://unix.stackexchange.com/questions/80571/cups-error-log-contains-no-such-interface-org-freedesktop-colormanager)

The second print job (with the error) has a Black&White color profile which is either not supported or incorrectly configured.  Try just printing with no color profile or use a generic color profile.

Color profiles are used for matching real colors with print-out colors.  If you are not doing graphic design, then you don't normally need color profiles.  It's possible that the printers have special color profiles defined in the front panel and CUPs doesn't know how to handle that because the ColorManager is either not installed or not configured.

---

### Post by datamason on 2013-10-23
By the way, in my examples above, each one has the same error, but the Okular job failed to print, while the Evince one did print.

The link was interesting -- the questioner had the same type error as I found, but  also noted that the error was not fatal. The answerer explained that the color manager is searching for color profile which the printer driver does not have or is not supplying. Within my printer config utility, there is no option to print regarding color, so nothing I can do here via the user interface.

Going on to my case:
First, if I am reading the error log correctly, CUPS is reporting the error while polling the device. Today I find the error at 7:55 a.m., when I was not even using the computer. Since the USB connection was set up in particular to access my scanner in the All-in-One, CUPS is supposing it should have a color profile. I am not seeing that CUPS looks for a color profile for the LAN connection as I installed that driver as a printer driver. Make sense?

CUPS will not print a test page to the USB printer, but will to the LAN printer. 

This is all a little screwey, but I have figured out what I need to do. Basically, when printing, always choose the LAN connection. And when scanning, I can only use the USB connection. Not great, but it works. And at the moment, given that other items are pressing me in my schedule, I need to attend to them, even though my obsession is to always fix every error message. 

Thanks for the help.

---

### Post by tgalati4 on 2013-10-23
You can scan over the network (LAN) with HP printers because they use a protocol that allows the scan to flow through the network without interference--it is a raw file of data that has to flow through without errors.  It's possible that the Brother only allows scanning through USB or you need a Windows driver to be able to scan through the network.  

Color profiles are often used in scanning to correct for color casts so that the scan matches the original.  I'm not an expert on ColorManager, so you will have to do more research on how to set and manage color profiles.  But as you have pointed out, that is probably not the error tripping up the printer.

I only have access to HP printers on my network, so I can't provide any more troubleshooting on your particular Brother printer/scanner.

Keep at it though, I'm sure there are others that could benefit from your troubleshooting.

---

### Post by kurt18947 on 2013-10-23
You can scan over a network using Brother printers as well.  I wonder if having two connections to the same machines  is causing some sort of config file confusion.  I have an MFC-7820 and it works 'out of the box'.  I'm using a USB & WiFi connection on one printer but the network connection if not from the machine with the USB connection. The only additional thing I did was to use the Brother CUPS driver found in the repository instead of the Brother driver.  The CUPS driver was much faster on second and subsequent pages.  I was getting 2-3 pages per minute using the Brother Brscript driver, 15-20 using the CUPS laser driver from the repository.  This was over a LAN connection.

---

### Post by tgalati4 on 2013-10-23
Yes, HP printers have a similar limitation, plugged in with ethernet or USB but not both.  You have to cycle the power on the printer for the last connection to take effect.

---

### Post by datamason on 2013-10-29
Hello Kurt18947,
If I understand you correctly, you have one printer, and one of your machines is hooked to it via USB while the other machines use a WiFi(LAN) link to it.  Right?? That way you don't have two drivers on one machine.

In Synaptic I don´t see a driver for my 7840W, so do you have any suggestions which driver to pick from the list? I suppose I would not chose those drivers which clearly list a subset of Brother's printer models, as that driver must be something unique to it to support just that list. Or I could chose "brother-cups-wrapper-laser 2.0.1-2ubuntu6" that lists the MFC-7820N which is the closest model number to my model.


On the other hand, for scanning, I already have installed the drivers that Synaptic lists. 

(And just for clarification: an lpr driver is for sending files to the printer solely via the command prompt, right??)


ps -- I installed the above-mentioned driver from synaptic anyway, just to see what would happen. After using the Mint printer utility to install another printer, I went to CUPS/Printers to see what driver was automatically used: BR-script3, which is the driver that I installed from the Brother website. I don't see a way to force it to use a driver (and maybe I shouldn't).

---

### Post by datamason on 2013-10-29
I am tempted to just buy an HP printer as it appears that HP takes the linux world seriously.

---

### Post by tgalati4 on 2013-10-29
HP printers do tend to work out-of-the-box under linux.

---

### Post by kurt18947 on 2013-11-01
> **datamason said:**
> Hello Kurt18947,
If I understand you correctly, you have one printer, and one of your machines is hooked to it via USB while the other machines use a WiFi(LAN) link to it.  Right?? That way you don't have two drivers on one machine.

In Synaptic I don´t see a driver for my 7840W, so do you have any suggestions which driver to pick from the list? I suppose I would not chose those drivers which clearly list a subset of Brother's printer models, as that driver must be something unique to it to support just that list. Or I could chose "brother-cups-wrapper-laser 2.0.1-2ubuntu6" that lists the MFC-7820N which is the closest model number to my model.


On the other hand, for scanning, I already have installed the drivers that Synaptic lists. 

(And just for clarification: an lpr driver is for sending files to the printer solely via the command prompt, right??)


ps -- I installed the above-mentioned driver from synaptic anyway, just to see what would happen. After using the Mint printer utility to install another printer, I went to CUPS/Printers to see what driver was automatically used: BR-script3, which is the driver that I installed from the Brother website. I don't see a way to force it to use a driver (and maybe I shouldn't).

Yes, I have two connections from 2 separate PC's so one connection/PC.  A Brother printer may have 3 possible connections - 1)USB 2)Ethernet 3) WiFi.  It can have only USB + 1 network connection, either wired or wireless.  At least that's the case with my machine.   I find the easiest way to manage connections on Brother printers is to use the package "system-config-printer" from the repositories.  I'm using gnome-shell so I need to install it, Xubuntu and I think Lubuntu use it by default.  To launch it, I use <alt>F2 then type "system-config-printer" without the quotes.  Right-click on the printer's icon and left-click 'properties'. A window will open with a menu on the left and a window on the right.  'Device URI' is the 'printer address'.  For a USB connection, it should look something like this:

```

Device URI:  usb://Brother/MFC-6490CW?serial=xxxxxxxxx

```

For a network connection, it may look something like this.  I use socket because I've had good luck with it.  Using socket, I assign a static I.P. address to each printer.  :9100 is the port and I think is standard.  There are other networking choices.

```

Device URI:  socket://192.168.1.xxx:9100

```

I hope this makes sense.

---

### Post by datamason on 2013-11-04
@Kurt,
Good tip on the system-config-printer. I discovered myself a week ago or so while surfing www. My connections for the LAN connection look similar to yours. And those connections work for printing.

Do you know of anything analogous for setting up a connection for scanners? I am thinking I will drop the USB connection, but not until I have set up a LAN connection to the scanner part of my All-in-One.

---

