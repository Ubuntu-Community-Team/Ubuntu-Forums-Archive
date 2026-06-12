---
title: "Epson stylus dx4400 (cx4400) and Ubuntu, how to setup ?"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by Axx83 on 2007-11-22
[http://ubuntuforums.org/showthread.php?t=627471](http://ubuntuforums.org/showthread.php?t=627471)

---

### Post by Axx83 on 2007-11-22
Update:

There is a guy who made Epson photo stylus RX640 scanner work with the "official" epson driver, which is called epkowa and I GUESS it's the same you can download as a rpm on avasys website, the one I already posted. This is what he did:

[http://www.uluga.ubuntuforums.org/showthread.php?t=576594](http://www.uluga.ubuntuforums.org/showthread.php?t=576594)

BUT on sane external backend website they say that: Stylus DX4400 requires DFSG non-free iscan-plugin-cx4400, this is the documentation page: (just scroll down to epkowa backend)
[http://www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA](http://www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA)

does this mean that ALL dx4*** series scanners work BUT this one ? Very very unlucky as always...

---

### Post by Axx83 on 2007-11-23
Is it possible that NO ONE has bought this printer/scanner ? It seems to be very cheap and popular around here, please let me know.

---

### Post by Axx83 on 2007-11-30
New procedure inserted, please try it out.

---

### Post by cOzAtS on 2008-04-05
Anyone found a solution on how to get the scanner work? the whole operation didn't work out for me :(

---

### Post by Dai777 on 2008-04-05
This is what I did to get my DX-8400 working
go to:
 [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
download the drivers for your printer/scanner (rpm)
convert the rpm's to deb's using Alien

Install both debs for printer and scanner then do the following to get the scanner working.
1.Make sure that scanning users are added to group scanner
2. Edit sudo gedit /etc/sane.d/epkowa.conf
add:
usb [COLOR="Red"]0x04b8 0x0839[/COLOR]

and commented out:
SCSI EPSON

3. Edit sudo gedit /etc/udev/rules.d/45-libsane.rules
Add:
# Epson DX-8400
SYSFS{idVendor}=="[COLOR="Red"]04b8[/COLOR]", SYSFS{idProduct}=="[COLOR="Red"]0839[/COLOR]", MODE="664", GROUP="scanner"

**[COLOR="Red"]change above to suit your printer/scanner[/COLOR]**

Reboot and all is well.. Kooka, xsane, and everything else works swimmingly.

If sane does not work open a terminal and type iscan for the epson scanner software

---

