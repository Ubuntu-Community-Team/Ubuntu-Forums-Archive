---
title: "Getting HP ScanJet 4C to work with sane"
date: 2010-01-16
forum: Hardware
---

### Post by ka1ssr on 2010-01-16
I am trying to get an HP ScanJet 4C to work with sane.  When I run sane, it complains that it can't find any scanners.  I am connecting the scanner to the computer via a Symbios SYM20402 SCSI card.  Dmesg shows that IsAPNP reports the card as "sym 53c416."

I've done all the obvious things like completely power down the system, power up the scanner first then boot the computer, but no luck.  Changing the LUN does nothing either.

Does anyone know if this card needs a driver that's not being loaded?

Many thanks for your help.

Bill

---

### Post by ka1ssr on 2010-01-16
ADDENDUM:

modprobe -l reports that the sym53c416 module is loaded (kernel/drivers/scsi/sym53c416.ko)

cat /proc/scsi/scsi returns:

```
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Maxtor 2F040L0   Rev: VAM5
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: ATA      Model: WDC WD153BA      Rev: 16.1
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: SAMSUNG  Model: CDRW/DVD SM-308B Rev: T100
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: STORAGE DEVICE   Rev: 0113
  Type:   Direct-Access                    ANSI  SCSI revision: 00

```

Do you think the scanner is on scsi2?  If so, why don't the vendor and model fields say HP and ScanJet 4C respectively?

Bill

---

### Post by andrevanzuydam on 2010-02-06
I hope this will help as I had a similar problem,  my SCSI device was installed but I couldn't access the scanner.  If I ran sane-find-scanner I received no results.  I added the module sg to the /etc/modules file and rebooted.  

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
sg
lp
```


Running sane-find-scanner again resulted in xsane finding the scanner.

```
found SCSI processor "HP C5110A 3638" at /dev/sg3
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

```

Seeing as it was found on /dev/sg3 and the permissions were for root I needed to give permission for my username to access this device.  The easy way to do this (but not the best way)

```
chmod 777 /dev/sg3
```

or

```
chown .<username> /dev/sg3 
```

---

### Post by ka1ssr on 2010-02-06
Hi!  Thanks for getting back to me.

I may have kinda-sorta fixed the problem by ditching the Symbios card altogether and installing an Adaptec PCI SCSI card in its place.  This card works great with a SCSI tape drive, but I haven't tried it with the scanner yet because I don't have the proper cable.  I'll keep your post in mind when I do get around to making the scanner play in about a month, though.

Many thanks!

Bill

---

### Post by grazioso on 2010-02-11
anything new here around sane/xsane? we have hp 4c scanjet connected through aha-2940U and it just bombs with I/O error. it is recognized as sg2  with 777 and it still won't go :( , i already tried both options - dumb-read, scsi-connect in hp.conf 
but to no avail...it is shame since we just need to use it for the first time in like 10 years....and it is our last pc  we have left and no windoze to test the scanner on... of course...so it is hard to tell what is the problem - scanner? os? sane?

---

### Post by ka1ssr on 2010-02-13
As I said previously, I ditched the HP-issue Symbios ISA card in favour of an Adaptec AHA-2940 which does work with a DDS2 tape drive.  I haven't been able to try the scanner out on the adaptor yet because I don't have an HD50 to LD50 cable.  I'll re-post when I get the scanner hooked up.

Good luck in your quest!

Bill

---

### Post by amoht on 2010-02-16
If you go to [http://jhansonxi.blogspot.com](http://jhansonxi.blogspot.com) and scroll down you will find instructions to get Xsane to use the scanner. I followed the advice and was able to get Xsane to use my HP Scanjet 4P SCSI scanner.

Alan

---

### Post by grazioso on 2010-02-18
that is very nice howto but that does not help and i tried that already before posting ...in case of my hp 4c...it is recognized by xsane and it does have all the proper permissions and it still hangs for about three minutes and comes with i/o error when prescan  or scan button is used ... it would be nice to have working a3 format scanner..so we have to do with slow a4 usb 600x600 now...shame 1200x1200 on scsi used to work just fine like 10 years ago when scsi was working ok and terminal was not well hidden "application"... but main feature of the desktop instead...;)

---

### Post by ka1ssr on 2010-05-10
The cable finally came at about the same time I did an upgrade to 10.04.  I started simple scan, pressed the scan button and *PRESTO!*; it scans!  All I did was plug the scanner in.

Doesn't really fix your problem with sane but I thought you'd like to know that there is some light at the end of the tunnel.

Bill

---

