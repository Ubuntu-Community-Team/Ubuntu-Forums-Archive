---
title: "MP3 and other multimedia codecs."
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Roadbloc on 2009-01-26
Ubuntu is excellent, but i cant play mp3's. I dont have an internet connection at home, and i cant download mp3 support to put on a memory stick. Can it be possible that u guys who make ubuntu make it so i can download software or codec packages to a memory stick to run and install at home instead of having to have an interent connection on the computer running. PS. i am writing this on a school computer ;).

---

### Post by ajgreeny on 2009-01-26
Unfortunately, it is very difficult, though not impossible, to use ubuntu, and most other linux distros without an active internet connection.  If possible, to get a distro that works "out of the box" for most multimedia file types, download Linux Mint version 5 or 6, which are based on ubuntu, but have all the codecs included.  You will not be able to update it easily with no internet, but at least you will be able to play videos, DVDs and MP3s with no problem.  I realise this means another big download, but it could be the easiest way to go.

If you must stick with ubuntu, you will need to download all the packages you need on to another internet enabled computer, probably using the live CD and a usb flash drive.  The live CD will put all the downloaded packages into /var/cache/apt/archives and you can copy them to your usb drive, then install them to your own machine using ```
sudo dpkg -i /path/to/usbdisk/*.deb
```

Probably easier to go the Mint route!

---

