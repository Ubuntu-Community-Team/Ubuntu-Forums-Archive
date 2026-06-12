---
title: "Scanner not working, Artec e+48U"
date: 2013-05-19
forum: Hardware
---

### Post by arashiko28 on 2013-05-19
I have tried pretty much everything, and still can't get my scanner to work. lsusb does show the scanner, but with simple scan, the message is "Failed to scan", however in preferences, contains all the information about my scanner.
I installed sane and went to usr/share/sane created the folder artec_eplus48u and copied the Artec48.usb file in it, but still can't scan anything, I also tried by copying this file to the simple-scan folder, but nothing. I need this desperately! How can I get my scanner to work? It was working on the previous version of ubuntu.

---

### Post by arashiko28 on 2013-05-19
UPDATE

lsusb output: > Bus 006 Device 002: ID 05d8:4003 Ultima Electronics Corp. Artec E+ 48U

BUT

sane-find-scanner output: > # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x04f2/0xb105 at 002:003: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 007:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 008:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


So... where do I go from here?

---

### Post by ajgreeny on 2013-05-19
I've never heard of that scanner, but that is of no consequence as you asked this same question in March 2010 and found the answer which you then reported in [http://ubuntuforums.org/showthread.php?t=1422729](http://ubuntuforums.org/showthread.php?t=1422729).

---

### Post by arashiko28 on 2013-05-19
Yes but that does not work now. I don't know why but I'm having the hardest time ever to configure this scanner with the new release.

---

### Post by luisricardoram on 2013-06-25
Hello, you've done right, the scanner is working properly, just run the xsane as root. "sudo xsane" and a message box will appear, press ok and you're good to go.

---

### Post by pqwoerituytrueiwoq on 2013-06-25
What does [FONT=courier new]sudo scanimage -L[/FONT] give you
If that sees your scanner, this should get it working
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2)

---

