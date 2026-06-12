---
title: "Epson Perfection 3590 Photo Scanner Not Working"
date: 2009-01-02
forum: Hardware
---

### Post by madmonkeyz on 2009-01-02
Xane Image scanner is having issues with Intrepid (failed to open device). Recently (2 - 3 months) I used the scanner with Hardy to scan documents. It seems that XSane is confused with the two usb devices (one a monitor the other the scanner) as they both appear in the device selection list - they didn't used to.

Here are the results from sane-find-scanner:

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

And the unfortunate results from scanimage -L

scanimage -L
device `v4l:/dev/video0' is a Noname ViewSonic 1.3M, USB2.0 Webcam virtual device
device `snapscan:libusb:001:003' is a EPSON EPSON Scanner flatbed scanner

I found lots of scanner-like problems - none seemed to help. I've uninstalled XSane and reinstalled. Any scanner gurus out there?

---

### Post by flamenco108 on 2011-04-07
Hello.

I have the same problem.


root@szmirnoff:/etc/sane.d# scanimage -L
device `snapscan:libusb:001:015' is a EPSON EPSON Scanner flatbed scanner

root@szmirnoff:/etc/sane.d# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 015: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


And I have the same error.

Have You found any solution? Anyone?

---

### Post by flamenco108 on 2011-04-07
Well, I found the work-around, that actually works:

1. Download iscan from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do) (if this address disappear, find it via google): iscan and iscan-plugin
2. Convert it:
```
# sudo alien --scripts iscan-blabla.rpm
# sudo alien --scripts iscan-plugin-blabla.rpm
```
3. Install it in your preferred way
4. Make sure, that everything is OK:
```
# iscan
```

The program in GNOME should appear and work.
5. Correct the /etc/sane.d/snapscan.conf
```

# whereis iscan
iscan: /usr/bin/iscan /usr/lib/iscan /usr/share/iscan /usr/share/man/man1/iscan.1.gz
# ls /usr/share/iscan/
esfw52.bin

# vim /etc/sane.d/snapscan.conf

```

At the very beginning of the file:
```

------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
# firmware /usr/share/sane/snapscan/your-firmwarefile.bin

 firmware /usr/share/iscan/esfw52.bin

```

---

### Post by digitography on 2011-08-28
I am having a similar issue.
However I can get the scanner to work when using a virtualized Win XP with the scanner drivers. So I know it's not hardware.
If I do lsusb in terminal the scanner is listed, so my guess is there is some driver missing.
I have tried using simple scan and xsane all with the same result.

any help would be appreciated.

---

### Post by demonipuch on 2011-09-05
Hello digitography

Open a terminal console and run these commands :
```
sudo mkdir -p /usr/share/sane/snapscan
cd /usr/share/sane/snapscan
sudo wget http://demonipuch.free.fr/Esfw52.bin
```

Now open file /etc/sane.d/snapscan.conf with gedit :
```
gksudo gedit /etc/sane.d/snapscan.conf
```
and change this line :
```
firmware /usr/share/sane/snapscan/your-firmwarefile.bin
```
to :
```
firmware /usr/share/sane/snapscan/Esfw52.bin
```
Save and exit.

Try to use your scanner (may need a reboot).

---

### Post by digitography on 2011-09-14
Demonipuch

Thank you so much for that, I now have a working scanner using simple scan.

however I do still have a problem with Xsane in that although it goes through the motions of working I only get a scan that is about 25cm wide. I am not able to adjust the parameters for the scan, any ideas?

anyway no matter what the outcome thanks, simple scan is better than nowt.

---

### Post by demonipuch on 2011-09-14
> **digitography said:**
> however I do still have a problem with Xsane in that although it goes through the motions of working I only get a scan that is about 25cm wide. I am not able to adjust the parameters for the scan, any ideas?


Sorry, I can't help much on that

---

### Post by digitography on 2011-09-14
It now works with simple scan and that's good enough for me.

Excellent advise, and again thanks.

---

