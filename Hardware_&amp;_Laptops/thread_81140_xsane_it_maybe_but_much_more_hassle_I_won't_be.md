---
title: "xsane it maybe but much more hassle I won't be"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by teaker1s on 2005-10-23
battling xsane I've got a trust 240h easy webscan gold which is a 

found USB scanner (vendor=0x05d8, product=0x4007, chip=GT-6816?) at libusb:006:002

all seems good and from reading various reports on the internet and specifying my firmware file location all would be fine in the gt68xx.conf file

#############################################################################
# For testing scanners that are not yet supported by this backend add the
# vendor and product ids in the usb line below. Also fill in the override
# and firmware lines. For more details, see:
# [http://www.meier-geinitz.de/sane/gt68xx-backend/adding.html](http://www.meier-geinitz.de/sane/gt68xx-backend/adding.html)
#trust ultima 240h daniel custom

 usb 0x05d8 0x4007
 override "Daniel ultima trust240"
 firmware "/usr/share/sane/gt68xx/1200.usb"
###############################################

so far so good but still no scanner so I run as root(yes I know) and am presented with "Error failed to open device '
gt68xx:libusb:006:002': operation not supported"

Does this mean that libusb which is latest avaliable to synaptic is not new enough as suggested by some people and am i right that libusb needs compiling into kernel to upgrade and if so how would I go about it as three weeks with linux from years of ms I feel a little out of my depth

thanks

---

### Post by ChrisTheGeek on 2005-12-01
What's the output of:

sudo scanimage -L

That will tell you if sane itself is able to detect the scanner.  If so, then you should be able to do a test scan straight from the command line using something like:

sudo scanimage > ~/Desktop/testscan.pnm

If it's not detected, then take a look at the sane webpage faq here: [www.sane-project.org](www.sane-project.org) for some troubleshooting hints.  Also check the scanner is supported by version 1.0.15 of sane which is what breezy shipped with.

---

