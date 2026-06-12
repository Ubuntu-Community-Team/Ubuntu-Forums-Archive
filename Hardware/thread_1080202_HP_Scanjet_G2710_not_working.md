---
title: "HP Scanjet G2710 not working"
date: 2009-02-25
forum: Hardware
---

### Post by bazzer on 2009-02-25
...and would you believe it, I can't get much sense out of HP.... 

sane-find-scanner
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [hewlett packard], product=0x2805 [hp scanjet], chip=RTS8822) at libusb:005:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```
scanimage -L
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```
I have seen [a blog]("http://tom.knaupp.com/2008/06/11/hp-scanjet-g2710-ubuntu-804-hardy-heron/comment-page-1/") that says the hp3900 backend works, but it doesn't. :(
Any help?

---

### Post by Markor on 2009-03-05
It seems that HP G2710 scanner works on ubuntu linux with some tweaks
but only with resolutions of 600dpi or less, with hp3900 driver.

[http://tom.knaupp.com/2008/06/11/hp-scanjet-g2710-ubuntu-804-hardy-heron/comment-page-1/](http://tom.knaupp.com/2008/06/11/hp-scanjet-g2710-ubuntu-804-hardy-heron/comment-page-1/)
[http://www.sane-project.org/lists/sane-backends-cvs.html#S-HP3900](http://www.sane-project.org/lists/sane-backends-cvs.html#S-HP3900)

Author used Ubuntu Hardy (I suppose any later will work, too)

HowTo:
Get the latest drivers from the sourceforge project:
[http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)

Unpack the files and change into the new directory:
tar xfz hp3900-series_0.12.tar.gz
cd hp3900-series_0.12/

Install the drivers:
sudo ./INSTALL.sh
application: 2 - SANE Backend
distro: 3 - Ubuntu

Add your username to the scanner group:
sudo adduser your-user-name scanner

Start XSane : )

PS: Fastest and best results with 200 or 300 dpi

Update June 22th, 2008:
I forgot to mention that it only works with resolutions equal and less than 600dpi

---

### Post by mike.thorton on 2009-03-09
I've got this problem as well. I use latest jaunty 64bit.

The tutorial Markor posted doesn't work for me and as I found on the Internet, I'm not alone :(

Can anyone help?

---

### Post by AlexGret on 2009-05-06
Maybe, you don't have the group 'scanner' in your system. So, you should manually create it.
Try this: 
create the group 'scanner': sudo addgroup scanner
Then, install the drivers. (see Markor's post in this thread).
And then reboot your system - that XSane got name in the scanner group

---

### Post by ubie0 on 2009-06-18
I got the same problem under 64 bit 9.04. I installed hp3900-series_0.12.tar.gz as described in [Tom's blog]("http://tom.knaupp.com/2008/06/11/hp-scanjet-g2710-ubuntu-804-hardy-heron/"), but it's still not found by XSane.

```
$ uname -a
Linux <<system name>> 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

```
$ sane-find-scanner
...
found USB scanner (vendor=0x03f0 [hewlett packard], product=0x2805 [hp scanjet], chip=RTS8822) at libusb:001:005
...
```

```
$ ls -l /dev/bus/usb/001/005 
crw-rw-r-- 1 root scanner 189, 4 2009-06-18 14:43 /dev/bus/usb/001/005
```

```
$ grep scanner /etc/group
scanner:x:105:<<my username>>
```

```
$ scanimage -L
No scanners were identified. ...
```

```
$ cat /etc/sane.d/hp3900.conf 
...
# HP Scanjet G2710
usb 0x03f0 0x2805
...
```

Mike: did you ever solve this?

---

### Post by ubie0 on 2009-06-18
Got it! \\:D/

I manually installed the amd64 packages from karmic
[LIST]
[*][URL="http://packages.ubuntu.com/sv/karmic/libgphoto2-port0"]http://packages.ubuntu.com/sv/karmic/libgphoto2-port0
[*][http://packages.ubuntu.com/sv/karmic/libgphoto2-2]("http://packages.ubuntu.com/sv/karmic/libgphoto2-2")
[*][http://packages.ubuntu.com/sv/karmic/libsane]("http://packages.ubuntu.com/sv/karmic/libsane")
[/LIST][/URL]

Listing devices with scanimage explodes:
```
$ scanimage -L
device `hp3900:libusb:001:005' is a Hewlett-Packard Scanjet G2710 flatbed scanner
Segmentationfault
```

XSane was able to scan an image with 600 DPI. The picture looks a little strange though.. maybe a bit too much red and there are (slightly) visible vertical lines.. :neutral: I guess the colors can be compensated for in XSane, but how can I get rid of those vertical lines?

Note: Before I did installed a lot of other stuff too.. like try to compile the SourceForge hp3900 package. My guess is that anyone who tries this has to add themselves to the "scanner" group.

---

### Post by ubie0 on 2009-06-19
The brain behind the hp3900 gave me some great hints on how to solve this. (Thanks man!) The calibration part was at least to some extent implemented in the SVN version of the sane backend.

This is what I did to make it work on a 9.04 x86 (different system than before):

```
sudo apt-get install subversion build-essential libusb-dev libtiff-dev cvs
svn co https://hp3900-series.svn.sourceforge.net/svnroot/hp3900-series hp3900-series 
cd hp3900-series/
./stdcompile.sh 
./pack.sh 
cd ~/hp3900-series-190609-1550/
./COMPILE.sh 
sudo ./INSTALL.sh
   Chose to install the backend version
sudo adduser user scanner
*Reboot, log in logout or make sure the *
sane-find-scanner
scanimage -L
```

In XSane I was only able to adjust to global gamma, contrast and brightness, but this was sufficient to correct the colors. (I started by scanning a white paper and tried to make sure all the colors in the histogram overlapped.) There are still some weak vertical lines, but not more than I can live with.

I've asked HP for some more details on how the calibration works, but I wont get my hope up too much..

---

