---
title: "Ubuntu or libsane scanning issue?"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by yetanothersteve on 2005-08-04
My Acer/Benq 310U Prisa USB scanner is having issues with Ubuntu. It attempts to scan but the images are not usable.

For example, this coaster scanned from Suse 9.2 and libsane 1.0.14 looks as expected:
[http://coding.home.comcast.net/suse92libsane1014.png](http://coding.home.comcast.net/suse92libsane1014.png) 

From Ubuntu 5.04 and libsane 1.0.15, not good.
[http://coding.home.comcast.net/ubuntu504libsane1015.png](http://coding.home.comcast.net/ubuntu504libsane1015.png) 

Good scan:
```
From Suse 9.2
ouz@linux:~> sane-find-scanner
found USB scanner (vendor=0x04a5, product=0x1a20 [FlatbedScanner 5]) at libusb:002:002

ouz@linux:~> scanimage -L
device `snapscan:libusb:002:002' is a Acer FlatbedScanner_5 flatbed scanner

ouz@linux:~> scanimage --version
scanimage (sane-backends) 1.0.14; backend version 1.0.14

```

Bad scan:
```
From Ubuntu 5.04
ouz@debderiv:~$ sane-find-scanner
found USB scanner (vendor=0x04a5, product=0x1a20 [FlatbedScanner 5]) at libusb:001:003

ouz@debderiv:~$ scanimage -L
device `snapscan:libusb:001:003' is a Acer FlatbedScanner_5 flatbed scanner

ouz@debderiv:~$ scanimage --version
scanimage (sane-backends) 1.0.15; backend version 1.0.15

```

I could also submit this to the sane developers as it could just as easily be a libsane issue with 1.0.15 and not anything to do with the Ubuntu package.

Any ideas or suggestions are appreciated.

---

### Post by yetanothersteve on 2006-02-02
I finally fixed this in Breezy.

Posted here. It was Sane after all.

[http://www.ubuntuforums.org/showthread.php?t=123757]("http://www.ubuntuforums.org/showthread.php?t=123757")

---

