---
title: "Brother DCP-7070DW"
date: 2015-06-21
forum: Hardware
---

### Post by vitozabal on 2015-06-21
Hi, I have a problem with scanning on my Brother DCP-7070DWR, Ubuntu 14.04 via GUI software like xsane or simplescan

My printer connected via wifi. I have succesfully install printer and scanner Brother's drivers. Printing works just fine. But I can not scanning - xsane telling me "No devices available" (from root too)

Scanimage test show me all ok:
```
vito@vws:~$  scanimage -d test -T
scanimage: scanning image of size 157x196 pixels at 8 bits/pixel
scanimage: acquiring gray frame, 8 bits/sample
scanimage: reading one scanline, 157 bytes...    PASS
scanimage: reading one byte...        PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...     PASS
scanimage: stepped read, 32 bytes...     PASS
scanimage: stepped read, 64 bytes...     PASS
scanimage: stepped read, 128 bytes...     PASS
scanimage: stepped read, 256 bytes...     PASS
scanimage: stepped read, 255 bytes...     PASS
scanimage: stepped read, 127 bytes...     PASS
scanimage: stepped read, 63 bytes...     PASS
scanimage: stepped read, 31 bytes...     PASS
scanimage: stepped read, 15 bytes...     PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS

```
But sane find scanner shows me some pipe trouble:
```
vito@vws:~$ sudo sane-find-scanner


  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

However, I run evaluated VueScan - and it scans perfectly out of the box. Please give me some ideas how to fix xsane working.

---

### Post by plucky on 2015-06-22
You probably need to tell the driver the IP address of the scanner.

[Network scanner](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&redirect=on)

See step 5.

Can you post output for ```
dpkg -l | grep -i brother
```
This should show the drivers you installed.

Good Luck

---

### Post by vitozabal on 2015-06-26
here is:
> vito@vws:/opt/lampp/htdocs/qoot$ dpkg -l | grep -i brother
ii  brgenml1cupswrapper                                   3.1.0-1                                             i386         Brother BrGenML1 CUPS wrapper driver
ii  brgenml1lpr                                           3.1.0-1                                             i386         Brother BrGenML1 LPR driver
ii  brscan-skey                                           0.2.4-1                                             i386         Brother Linux scanner S-KEY tool
ii  brscan4                                               0.4.3-1                                             i386         Brother Scanner Driver
ii  printer-driver-ptouch                                 1.3-8                                               i386         printer driver Brother P-touch label printers




Thank you

---

### Post by vitozabal on 2015-06-26
please note that installed VueScan scanning software works good (scans successfully), so seems it is not IP address issue. But xsane/simplescan does not work and this is a problem (cause it is a free software)

---

### Post by vitozabal on 2015-07-02
Solved. 
Get scanner's IP Address by using the Menu button on the printer/scanner, select Network, then TCP / IP, then IP Address. Ping it:

```
brsaneconfig4 -p 192.168.0.107
```

not any answer in my case. So I set my scanner IP by brsaneconfig:

    ```
brsaneconfig4 -a name=DCP-7070DW model=DCP7070DW ip=192.168.0.107
```

Then restart computer and ping again. Ping now works fine and xsane detects scanner successfully.

---

