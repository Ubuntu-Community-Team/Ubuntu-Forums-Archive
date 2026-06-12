---
title: "epson perfection 1670 scanner"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by namedontwant on 2005-07-24
If you have this scanner, just follow the procedure here, written by remix_88 !!!
Thanks, remix_88!!!

[http://www.ubuntuforums.org/showthread.php?t=26911&highlight=epson+perfection+1670](http://www.ubuntuforums.org/showthread.php?t=26911&highlight=epson+perfection+1670)

Here it is:
HOWTO: Epson Perfection 1670 Scanner

The scanner firmware comes in a file called ESFW30.BIN, which apparently is only available if you install the software on the CD-ROM provided with the scanner. Unfortunately, the software only installs under Windows and then you have to copy the software from the Windows machine to the linux machine. Or you can follow this simple process to download the firmware (provided by Jeff Silverman) and then update your /etc/sane/saned.conf

Code:

$ wget [http://www.commercialventvac.com/~jeffs/ESFW30.BIN](http://www.commercialventvac.com/~jeffs/ESFW30.BIN) $ sudo cp ESFW30.BIN /etc/sane.d



Edit /etc/saned.d/snapscan.conf and change the line...

firmware /path/to/your/firmware/file.bin

...to point to /etc/sane.d/ESFW30.BIN

Code:

$ scanimage -L



You should see that your scanner is now detected. If so, you can now scan using XSane.

Other Similar Scanners - [http://snapscan.sourceforge.net](http://snapscan.sourceforge.net)

The process should be the very similar (you should just need to appropriate firmware) for other snapscan scanners. See the SnapScan Backend for SANE page for more details about the following scanners...

Acer / Benq 300f SCSI
Acer / Benq 310s SCSI
Acer / Benq 610s SCSI
Acer / Benq 620S SCSI
Acer / Benq 620ST SCSI
Acer / Benq 620+ SCSI
Acer / Benq 640s SCSI
Acer / Benq 310U USB
Acer / Benq 320U USB
Acer / Benq 340U USB
Acer / Benq 620U USB
Acer / Benq 620UT USB
Acer / Benq 640U USB
Acer / Benq 640UT USB
Acer / Benq 640BU USB
Acer / Benq 640BT USB
Acer / Benq 1240 USB
Acer / Benq 3300 USB
Acer / Benq 4300 USB
Acer / Benq 5000 USB
Acer / Benq 5300 USB
Agfa SnapScan 300 SCSI
Agfa SnapScan 310s SCSI
Agfa SnapScan 600 SCSI
Agfa SnapScan 1236s SCSI
Agfa SnapScan 1236u USB
Agfa SnapScan 1212U USB
Agfa SnapScan e10 USB
Agfa SnapScan e20 USB
Agfa SnapScan e25 USB
Agfa SnapScan e26 USB
Agfa SnapScan e40 USB
Agfa SnapScan e42 USB
Agfa SnapScan e50 USB
Agfa SnapScan e52 USB
Agfa Arcus 1200 SCSI
Epson Perfection 660 USB
Epson Perfection 1270 USB
Epson Perfection 1670 USB
Epson Perfection 2480 USB
Epson Perfection 2580 USB
Guillemot / Hercules MaxiScan A4 Deluxe SCSI
Guillemot / Hercules Scan @home Touch 1248 USB
Guillemot / Hercules Maxi A4 36bit USB
Mitsubishi Diamondview 648UT USB
Mitsubishi Diamondview 650U USB

Reference

- [http://www.commercialventvac.com/~j...0andFedora.html](http://www.commercialventvac.com/~j...0andFedora.html)
- [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)
Add to Remix_88's Reputation Report Bad Post   	Reply With Quote

---

