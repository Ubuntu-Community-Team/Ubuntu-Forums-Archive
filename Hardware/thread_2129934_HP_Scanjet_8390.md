---
title: "HP Scanjet 8390"
date: 2013-03-27
forum: Hardware
---

### Post by d0006 on 2013-03-27
Ubuntu 12.10 64-bit (fresh install)
HP Scanjet 8390
This scanner is SUPPOSED to be supported by the avision backend.

Scanner is detected by:
```
@jg-GA:~$ sane-find-scanner
found USB scanner (vendor=0x07d1, product=0x3c11) at libusb:001:004
found USB scanner (vendor=0x03f0 [hp], product=0x3805 [hp scanjet 8300]) at libusb:001:002
```
ALSO
```
root@jg-GA:~# lsusb
Bus 001 Device 002: ID 03f0:3805 Hewlett-Packard 
```
BUT:
```
root@jg-GA:~#  scanimage -L
No scanners were identified.
```
When I ran XSANE, it warned about multiple versions installed. SO, I uninstalled everything I could find labeled SANE and attempted to reinstall.  I got an error message:
```
E: /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_amd64.deb: trying to overwrite shared '/etc/sane.d/fujitsu.conf', which is different from other instances of package libsane:amd64
```
SO, I deleted this file and tried again.  I got another error message about another file in /etc/sane.d/.  There were A LOT of foobar.conf files in /etc/sane.d/ SO I "just" deleted /etc/sane.d/ and the reinstall seemed to go O.K. but scanimage still could not find my scanner.

Hmmmm...  Check /etc/sane.d/, now the only files present are:
.
&#9500;&#9472;&#9472; dll.d
&#9474;   &#9492;&#9472;&#9472; libsane-extras
&#9492;&#9472;&#9472; geniusvp2.conf

Now all the foobar.conf files are in: /usr/local/etc/sane.d/, does this matter?
I also installed the latest backends from git:
```
jg@jg-GA:~$ scanimage -V
scanimage (sane-backends) 1.0.24git; backend version 1.0.24
```

This site gives these instructions:
[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)
(I DID NOT compile from source but if I have to I will.)

To make sure that the newest version of sane (in /usr/local/lib/sane) is used
```
gksu gedit /etc/ld.so.conf

```
To use the old version it should read
```
include /etc/ld.so.conf.d/*.conf
include /usr/lib
```
To use the new version, change it to
```
include /etc/ld.so.conf.d/*.conf
include /usr/local/lib
```

Then run
```
sudo ldconfig
```
and you should be running the latest sane.  NO HELP.

I first added
```
usb libusb:001:002
```
and then tried
```
usb libusb:001:004
```

to avision.conf - no help.

A group named "scanner" exists and I am a member.

I have exhausted my limited Linux skills. Any help will be greatly appreciated.

P.S. Now I have another problem! Running
```
sane-find-scanner
```
or
```
scanimage
```
kills my USB wireless modem!

I will make a separate post for this. ](*,)

---

### Post by d0006 on 2013-03-30
The problem was the POS scanner!  ROM corruption is a known defect in these scanners.  The EEPROM in this scanner was corrupted by a windows virus.  I asked if this was even possible on the HP forum and my post was deleted immediately.  Apparently HP does not want anyone to know they are using defective EEPROMs in their scanners.  HP's solution was for me to buy a reconditioned scanner for $400 AND return mine!  I could buy a reconditioned scanner outright for $300!  Oh and it only took HP an hour to come up with this brilliant solution!

On another site a user described the same problem I had and fixed it by repeatedly flashing the firmware update. On the fifth EEPROM flash my scanner is now working.  Of course I had to do this on a windows machine.  I just hope this fix lasts!

I'm never buying another HP product!  My next scanner will be a KODAK i2900.  KODAK even offers Linux drivers!

Bill Hewlett and David Packard are spinning in their graves!

---

### Post by agillator on 2013-03-30
To each his own. However, I have used HP printers for years and had no problems. But that is a personal preference. Your experience certainly sounds different from any other contacts I have heard of from HP. Perhaps a complaint to corporation headquarters? As to Linux drivers, I have found that HP has outstanding Linux drivers, just for future reference. You simply install HPLIP and almost any HP printer is supported. One caution, though. If trying to install a scanner be sure to uninstall the version of HPLIP Ubuntu installs. I have found that there is always a problem with their version's scanner support. Get the version directly from HP and that always works.

---

### Post by d0006 on 2013-03-31
> **agillator said:**
> To each his own. However, I have used HP printers for years and had no problems. But that is a personal preference. Your experience certainly sounds different from any other contacts I have heard of from HP. Perhaps a complaint to corporation headquarters? As to Linux drivers, I have found that HP has outstanding Linux drivers, just for future reference. You simply install HPLIP and almost any HP printer is supported. One caution, though. If trying to install a scanner be sure to uninstall the version of HPLIP Ubuntu installs. I have found that there is always a problem with their version's scanner support. Get the version directly from HP and that always works.

Directly from [http://hplipopensource.com/hplip-web/supported_devices/index.html:](http://hplipopensource.com/hplip-web/supported_devices/index.html:)

"Sorry, HP Scanjet single function scanners are not supported by HPLIP. For possible Linux support, please visit: http://www.sane-project.org/"

This means you MUST use a windows machine to flash the ROMs.

I have a Laserjet 4plus (with hacked RAM), it is great but I bought that in 1994. It is built like a tank and still works perfectly.  I also have a variety of HP calculators going all the way back to the HP-65.  I still prefer HP calculators and RPN.  I have also used high end HP test equipment.

I stand by my statement that anything built by HP in the last ten years is crap.  Bill Hewlett and Dave Packard would be ashamed to see what has become of their company.

---

