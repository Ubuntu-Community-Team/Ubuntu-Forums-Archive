---
title: "epson 4490 in Hardy"
date: 2008-06-07
forum: Hardware
---

### Post by weemikey on 2008-06-07
It was a struggle, but I got my Epson 4490 working in Dapper.  Now I've upped to Hardy and I've lost my scanner again.
Here's the output from:  id: lusb; sane-find-scanner: ls -l /dev/bus/usb/004/002

michael@michael-desktop:~$ id
uid=1000(michael) gid=1000(michael) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(michael)
michael@michael-desktop:~$ lsusb
Bus 004 Device 002: ID 04b8:0119 Seiko Epson Corp. Perfection 4490 Photo
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
michael@michael-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
michael@michael-desktop:~$ ls -l /dev/bus/usb/004/002
crw-rw-r--+ 1 root scanner 189, 385 2008-06-07 08:44 /dev/bus/usb/004/002



Any suggestions as it's a great scanner when working.
Even Vuescan can see it but can't open it!
Mike

---

### Post by weemikey on 2008-06-08
Well! not only can't I get my Epson 4490 scanner to work, but now my Lexmark Z35 printer has stopped.  And I only got it working 3 days ago.
What's up with this Hard Hardy.:confused:

---

### Post by Payteer on 2008-06-11
Hello, in Gutsy, i had my 4490 working, and the same with me in Hardy, it just sits there.  The thing is it is a really nice scanner when it works.

---

### Post by Payteer on 2008-06-23
Someone must have an answer,  the xsane image scanner can not see it in its present form unfortunately.
Please somebody, we need help on this.

---

### Post by kcrotty2 on 2008-09-05
I am looking for an Epson 4490 Photo driver for 64 bit PC version of Ubuntu Linux.  If any ideas, please email Ken at [email]kcrotty2@nycap.rr.com[/email]

---

