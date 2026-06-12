---
title: "How to Scan to a wireless Network Printer"
date: 2014-01-11
forum: Hardware
---

### Post by seanmoir99 on 2014-01-11
Hello I have a Canon Pixma MG3260 I setup the Wireless printer to print and that works perfectly fine but, I do wonder as how to scan from the printer to my computer as there is a utility for that, that came with the printer for Windows and Mac OS X but how can I do this in Ubuntu or any other Linux Distro

---

### Post by theDaveTheRave on 2014-01-11
Hi,

I'm not expert, but does the printer have an 'ip address' for when you print ?

If so, could you not tell your scan application (I use simple scan) that the 'source' of the scan is that particular IP address ?

The other thing is that when you set up the printer, I guess you give it a name of some form and the OS does the rest. For my usb print / scanner I can just use the name of this printer in the 'source' field of simple scan's settings.

Otherwise, I guess the whole things works like an 'embeded network print server + printer' and you could probably use a similar idea to set this as a print / scan server somehow.

These are just a few ideas to research, if you haven't already.

Also what package do you use for scanning ? It may make a difference.

Can you connect the printer to your dhcp server (ie the router / box from your ISP), then go down the 'networked route' above.

Whatever solution you find, I would be interested in how you resolve, and I expect others would also.

David

---

### Post by bill-wilken-wilkenmail on 2014-03-12
I have two printer/scanner devices on my network; a wired HP7200 OfficeJet and a wireless HP Photosmart 7520.  Using Ubuntu 12.04 (with all current updates), I can print to both without any problems.  Scanning, however, is another matter.  If I connect the Photosmart to my Ubuntu box via a USB cable, XSane sees the scanning capabilities of both devices.  But XSane cannot see the Photosmart unit via wireless networking.  Does anyone have any suggestions for dealing with this problem?

---

