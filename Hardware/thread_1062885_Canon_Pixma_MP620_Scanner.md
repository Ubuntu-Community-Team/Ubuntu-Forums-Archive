---
title: "Canon Pixma MP620 Scanner"
date: 2009-02-07
forum: Hardware
---

### Post by squirrelplayingtag on 2009-02-07
I can not get Sane to recognize my scanner. I followed the guide here, [http://mp610.blogspot.com/](http://mp610.blogspot.com/), but when I run scanimage -L I get the message
```

dave@dave-laptop:~/sane-backends$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

Next I ran sane-find-scanner and it did find it.

```

dave@dave-laptop:~/sane-backends$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x08ff, product=0x2580 [Fingerprint Sensor]) at libusb:004:002
**found USB scanner (vendor=0x04a9 [Canon], product=0x172f [MP620 series]) at libusb:001:007**
found USB scanner (vendor=0x0c45, product=0x624f [USB20 Camera    ]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```

---

### Post by squirrelplayingtag on 2009-02-18
Anyone?

---

### Post by desertdog on 2009-03-24
Try:
$sudo scanimage -L

If it works with sudo, but not as a user, then you have a permissions problem. You'll want to go to System/Administration/Users and Groups and add the user to the scanner group.

---

### Post by union two levers on 2009-04-30
hi anyone know what 'error during cms conversions:could not open scanner ICM profile' means please, i get this when i try to use sane with my canon mp610...thanks

---

### Post by MakisM1 on 2009-06-24
My take to the missing ICM profile problem and the solution that worked.

[http://ubuntuforums.org/showpost.php?p=7500006&postcount=3](http://ubuntuforums.org/showpost.php?p=7500006&postcount=3)

However, I would like to find and install more ICM profiles. In XP I had a bunch available and they do make a difference on how things LOOK on the monitor.

Unfortunately, with my vast 2-day experience base in Ubuntu, I need to be baby-fed, because there is so much to learn, Anybody that knows, please help!

Best regards

MakisM

---

### Post by guillolb on 2009-07-16
This solved my configuration problem:

[http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/](http://www.nervous.it/2009/04/canon-pixma-mp620-wireless-on-ubuntu/)

Some source links (cvs) for the scanner are messed up, but just go to the Nicholas page at the bottom of the link above... or ([http://mp610.blogspot.com/](http://mp610.blogspot.com/)) and you will see the new links.

---

