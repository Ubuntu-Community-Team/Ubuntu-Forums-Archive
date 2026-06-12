---
title: "Opinions about the Epson Perfection V30 scanner"
date: 2009-10-25
forum: Hardware
---

### Post by Garret88 on 2009-10-25
I would buy this scanner ([Epson Perfection V30]("http://www.epson.co.uk/Store/Scanners/Epson-Perfection-V30/Tech-Specs")). I know it works with proprietary drivers and for me it's ok if they work good.
[IMG]http://img194.imageshack.us/img194/6162/epsonperfectionv30p4951.png[/IMG]

I'd like to know if you recommend it as my new scanner.
Does The Image Scan application have all the XSane features?
Did you encounter any annoying issues?

---

### Post by makoto149 on 2010-11-04
I bought this scanner, and it works fine. But... you have to download and install some software from the Avasys website:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

First, I downloaded the data package:

 - iscan-data_1.4.0-1_all.deb

I'm running on a 64-bit AMD PhenomII system, so I selected these .deb files:

 - iscan_2.26.0-3.ltdl7_amd64.deb
 - esci-interpreter-gt-f720_0.0.1-2_amd64.deb

(Select the files right for your distro)

And they need to be installed in the order above for them to work correctly. The first time I didn't see the "esci-interpreter-gt-f720_0.0.1-2_amd64.deb" file and couldn't figure out why iScan didn't see my scanner. That file is, apparently, the plugin for the V30.

Good luck!

---

### Post by Garret88 on 2010-11-04
> **makoto149 said:**
> I bought this scanner, and it works fine. But... you have to download and install some software from the Avasys website

Yes, but can you turn off the scanner through its button?

---

### Post by Dartan on 2010-11-07
Thanks makoto for the instructions on getting this scanner working.  I have been using it on a dual boot system (Windows 7 and Ubuntu 10.10) and it works great for both.  The Simple Scan app allows you to crop the image before saving it and also gives you the option to save as a pdf or email.  I can use the button on the scanner to turn it off in Ubuntu but the other 3 buttons do not work. The software can perform the necessary functions though.  The quality of the scans and the ease of use makes this a definite recommend for an all around scanner.

---

### Post by Hodge_1974 on 2010-11-30
Bam!

I love you guys. The drivers page was a little wonky; not a lot of instruction, but if you follow the order in which Makoto lists to install the packages, everything is happy.
Gotta say i love these boards; seems like most any peripheral works, sometimes out of the box and sometimes with a little doing. In either case the stability and performance is always worth the extra research. :p

---

### Post by Keith_Beef on 2012-01-11
> **makoto149 said:**
> I bought this scanner, and it works fine. But... you have to download and install some software from the Avasys website:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

First, I downloaded the data package:

 - iscan-data_1.4.0-1_all.deb

I'm running on a 64-bit AMD PhenomII system, so I selected these .deb files:

 - iscan_2.26.0-3.ltdl7_amd64.deb
 - esci-interpreter-gt-f720_0.0.1-2_amd64.deb

(Select the files right for your distro)

And they need to be installed in the order above for them to work correctly. The first time I didn't see the "esci-interpreter-gt-f720_0.0.1-2_amd64.deb" file and couldn't figure out why iScan didn't see my scanner. That file is, apparently, the plugin for the V30.

Good luck!


Thanks for that.

The files have been updated since then...
Installed through the Ubuntu Software Centre, when I clicked on the links at the Avasys site:
[LIST=1]
[*]iscan-data_1.13.0-1_all.deb
[*]iscan_2.28.1-3_amd64.deb
[*]esci-interpreter-gt-f720_0.1.1-2_amd64.deb
[/LIST]

I had watch lsusb running in a terminal, so switched on the scanner and waited a whole second and a half to see the scanner appear
```
Bus 001 Device 009: ID 04b8:0131 Seiko Epson Corp.
```

I put a book on the glass bed.

I started up Gimp, and chose File - Create - Scanning (iscan). The scanner whirred into action; a light came on under the lid and the Image Scan! dialog appeared.

In this Image Scan! dialog I clicked the Preview button, and the scanning head moved beneath the bed, and the preview image appeared.

So I clicked the scan button, and got an image in the main Gimp window.

---

