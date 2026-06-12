---
title: "Flatbed scanner not working after upgrade to 16.04"
date: 2016-05-17
forum: Hardware
---

### Post by stinktier2 on 2016-05-17
After I upgraded my PC from Ubuntu 15.10 to 16.04 LTS (32-bit) the flatbed scanner does not work anymore. I checked the device on another PC with xubuntu 15.04 and it was scanning flawlessly. So something broke during the upgrade...

The scanner is a simple Canon CanoScan LiDE 100 scanner that is connected via USB. When I start *xsane* I get an error message "**Failed to start scanner: Error during device I/O.**"
There is also a message from "hp-systray" (which may or may not relevant, but which was not popping up before the upgrade):[INDENT][I]HPLIP cannot detect devices in your network. This may be due to existing firewall settings blocking the required ports like (5353/udp). When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.
[http://hplipopensource.com/node/375](http://hplipopensource.com/node/375)[/I]
[/INDENT]

I reinstalled xsane/sane packages, but to no avail. The scanner is correctly displayed in xsane info, but neither scanning nor acquire preview works at all (see error message above).

I am stumped on how to proceed as the scanner was fully supported before and now I can't use it. :confused: Suggestions?

---

### Post by xin3 on 2016-07-02
hey, i had a similar problem - [[SOLVED] xsane not working in fresh 16.04 install]("http://ubuntuforums.org/showthread.php?t=2328712")
(found your post while looking for answers.)

does [FONT=courier new]**scanimage -L** [FONT=arial]return anything?

does [FONT=courier new]**scanimage > Desktop/test.pnm**[/FONT] give you an image?
[/FONT][/FONT]

---

### Post by pqwoerituytrueiwoq on 2016-07-02
If the system has usb3 support it could be this issue
[http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system](http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system)

---

### Post by stinktier2 on 2016-07-06
> **xin3 said:**
> hey, i had a similar problem - [[SOLVED] xsane not working in fresh 16.04 install]("http://ubuntuforums.org/showthread.php?t=2328712")
(found your post while looking for answers.)

does [FONT=courier new]**scanimage -L** [FONT=arial]return anything?[/FONT][/FONT][FONT=courier new][FONT=arial] Yes: [/FONT][/FONT][FONT=courier new]**device `genesys:libusb:001:004' is a Canon LiDE 100 flatbed scanner**[/FONT]
> **xin3 said:**
> [FONT=courier new][FONT=arial] does [FONT=courier new]**scanimage > Desktop/test.pnm**[/FONT] give you an image?[/FONT][/FONT]
Nope. [FONT=courier new]**scanimage: sane_start: Error during device I/O**[/FONT]

> **pqwoerituytrueiwoq said:**
> If the system has usb3 support it could be this issue
[http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system](http://askubuntu.com/questions/457901/usb-2-0-device-scanner-does-not-work-with-xhci-hcd-on-usb-3-0-system)

I doubt that as this PC is rather old (no USB 3 at all). I also tried already all USB ports but the results (or lack thereof) were always the same. :sad:

---

### Post by pqwoerituytrueiwoq on 2016-07-06
can we even get the device specific command options?
```
scanimage -A -d 'genesys:libusb:001:004'
```
the numbers 001 and 004 can change over time (reboot or usb disconnect), you can use scanimage -L again to find the numbers

---

### Post by stinktier2 on 2016-07-07
> **pqwoerituytrueiwoq said:**
> can we even get the device specific command options?
```
scanimage -A -d 'genesys:libusb:001:004'
```
the numbers 001 and 004 can change over time (reboot or usb disconnect), you can use scanimage -L again to find the numbers

This outputs:
```
All options specific to device `genesys:libusb:001:004':
  Scan Mode:
    --mode Color|Gray|Lineart [Gray]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --source Flatbed|Transparency Adapter [inactive]
        Selects the scan source (such as a document-feeder).
    --preview[=(yes|no)] [no]
        Request a preview-quality scan.
    --depth 8|16 [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --resolution 4800|2400|1200|600|300|200|150|100|75dpi [75]
        Sets the resolution of the scanned image.
  Geometry:
    -l 0..216.07mm [0]
        Top-left x position of scan area.
    -t 0..299mm [0]
        Top-left y position of scan area.
    -x 0..216.07mm [216.07]
        Width of scan-area.
    -y 0..299mm [299]
        Height of scan-area.
  Enhancement:
    --custom-gamma[=(yes|no)] [no]
        Determines whether a builtin or a custom gamma-table should be used.
    --gamma-table 0..65535,... [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..65535,... [inactive]
        Gamma-correction table for the red band.
    --green-gamma-table 0..65535,... [inactive]
        Gamma-correction table for the green band.
    --blue-gamma-table 0..65535,... [inactive]
        Gamma-correction table for the blue band.
    --swdeskew[=(yes|no)] [no]
        Request backend to rotate skewed pages digitally
    --swcrop[=(yes|no)] [no]
        Request backend to remove border from pages digitally
    --swdespeck[=(yes|no)] [no]
        Request backend to remove lone dots digitally
    --despeck 1..9 (in steps of 1) [1]
        Maximum diameter of lone dots to remove from scan
    --swskip 0..100% (in steps of 1) [0]
        Request driver to discard pages with low numbers of dark pixels
    --swderotate[=(yes|no)] [no]
        Request driver to detect and correct 90 degree image rotation
    --brightness -100..100 (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..100 (in steps of 1) [0]
        Controls the contrast of the acquired image.
  Extras:
    --lamp-off-time 0..60 [15]
        The lamp will be turned off after the given time (in minutes). A value
        of 0 means, that the lamp won't be turned off.
    --lamp-off-scan[=(yes|no)] [no]
        The lamp will be turned off during scan. 
    --threshold 0..100% (in steps of 1) [50]
        Select minimum-brightness to get a white point
    --threshold-curve 0..127 (in steps of 1) [50]
        Dynamic threshold curve, from light to dark, normally 50-65
    --disable-dynamic-lineart[=(yes|no)] [no]
        Disable use of a software adaptive algorithm to generate lineart
        relying instead on hardware lineart.
    --disable-interpolation[=(yes|no)] [no]
        When using high resolutions where the horizontal resolution is smaller
        than the vertical resolution this disables horizontal interpolation.
    --color-filter Red|Green|Blue [Green]
        When using gray or lineart this option selects the used color.
    --calibration-file <string> [/home/boris/.sane/canon-lide-100.cal]
        Specify the calibration file to use
    --expiration-time -1..30000 (in steps of 1) [-2134835368]
        Time (in minutes) before a cached calibration expires.A value of 0
        means cache is not used used. A negative value means cache never
        expires.
  Sensors:
    --scan[=(yes|no)] [no] [hardware]
        Scan button
    --file[=(yes|no)] [no] [hardware]
        File button
    --email[=(yes|no)] [no] [hardware]
        Email button
    --copy[=(yes|no)] [no] [hardware]
        Copy button
  Buttons:
    --clear-calibration
        Clear calibration cache
```

---

### Post by pqwoerituytrueiwoq on 2016-07-07
there is a ppa for the latest version of scanimage, maybe it has been fixed?
[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)
this ppa updates very frequently you never know when it will fix or break

i wonder if this could be a permission error...
```
sudo scanimage -d 'genesys:libusb:001:004' --source 'Flatbed' -l 0 -t 0 -x 215.9 -y 279.4 --resolution 75 --mode 'Color' --format=pnm > '/tmp/scan_file1.pnm'
```
open the file it creates: [FONT=courier new]/tmp/scan_file1.pnm[/FONT]
if it works with sudo this should be able to fix it (it is a bash script)
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2)

---

### Post by stinktier2 on 2016-07-11
> **pqwoerituytrueiwoq said:**
> there is a ppa for the latest version of scanimage, maybe it has been fixed?
[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)
this ppa updates very frequently you never know when it will fix or break
Even with the repository and a full software update the problem persists.

>  i wonder if this could be a permission error...
[code]sudo scanimage -d 'genesys:libusb:001:004' --source 'Flatbed' -l 0 -t 0 -x 215.9 -y 279.4 --resolution 75 --mode 'Color' --format=pnm > '/tmp/scan_file1.pnm'

This outputs: **scanimage: attempted to set inactive option source**

---

### Post by ardouronerous on 2016-07-11
I'm also experiencing the same problems with my CanoScan LiDE 110, I've tested my scanner on Live CDs of both Xubuntu 14.04 and 16.04 on VirtualBox, my scanner works on 14.04, but doesn't work on 16.04. There is clearly a bug.

[http://news.gmane.org/gmane.comp.graphics.scanning.sane.devel/cutoff=25795](http://news.gmane.org/gmane.comp.graphics.scanning.sane.devel/cutoff=25795)

This link discusses the same problems, plus some bug reports from Launchpad.

---

### Post by pqwoerituytrueiwoq on 2016-07-12
> **stinktier2 said:**
> Even with the repository and a full software update the problem persists.



This outputs: **scanimage: attempted to set inactive option source**
opps the help data did say there was no valid source option, try this one
```
sudo scanimage -d 'genesys:libusb:001:004' -l 0 -t 0 -x 215.9 -y 279.4 --resolution 75 --mode 'Color' --format=pnm > '/tmp/scan_file1.pnm'
```

---

### Post by stinktier2 on 2016-07-14
> **pqwoerituytrueiwoq said:**
> opps the help data did say there was no valid source option, try this one ```
sudo scanimage -d 'genesys:libusb:001:004' -l 0 -t 0 -x 215.9 -y 279.4 --resolution 75 --mode 'Color' --format=pnm > '/tmp/scan_file1.pnm'
```  This works. The scanner produces an image – which may not look like the page I scanned, but at least it the devices works at all.  How to I download and use that bash script you linked earlier?

---

### Post by pqwoerituytrueiwoq on 2016-07-18
does it work without using sudo if so you don't need to use the script
make sure you delete [FONT=Courier New]/tmp/scan_file1.pnm[/FONT] first

just open a terminal and type [FONT=Courier New]sudo bash[/FONT] followed by a space and drag/drop the decompressed script into the terminal and hit enter

if you don't mind using a different GUI there is a link in my signature that will work as well as that command for scanning

try some of the other format options maybe tiff or png will work better
pnm, tiff, png, and jpeg are all valid options

---

### Post by yourkunal on 2017-02-05
Hi
Am facing same problem as explained earlier.

I have tried everything, but the scanner keeps giving the error i/o as earlier.

Something crude did work, thought of sharing it with other people facing same/similar problem.

Solution:
 Download a proprietory software trial [[https://www.hamrick.com/download.html]](https://www.hamrick.com/download.html]) Vue Scan. 
 Extract the file downloaded, run the executable file. 
 Scan once, it works but software doesn't allow you to save without purchasing serial key. Don't save.
 Close the application.
 Run Simple Scan/Xscan, and voila everything works magically.

One major issue, the above process needs to be done every time you unplug device/restart computer.

---

### Post by olli-raatikainen on 2017-02-19
Any progress related to the problem? I have Canon Lide 110 and the exact same problem: worked fine before updating to 16.04.

---

### Post by JoachimDurchholz on 2018-01-03
I hear that 16.04 has SANE problems (sorry I can't find the link).
I upgraded to 17.04 and things seemed to work, I added the official driver from [http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/sp/software/ubuntu.html](http://www.fujitsu.com/global/support/products/computing/peripheral/scanners/sp/software/ubuntu.html), and things worked (I don't know whether it's the Ubuntu upgrade or the driver install that actually helped, nor am I 100% sure whether it's really that).

---

### Post by petmue on 2018-01-20
> **pqwoerituytrueiwoq said:**
> there is a ppa for the latest version of scanimage, maybe it has been fixed?
[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)
this ppa updates very frequently you never know when it will fix or break

i wonder if this could be a permission error...
```
sudo scanimage -d 'genesys:libusb:001:004' --source 'Flatbed' -l 0 -t 0 -x 215.9 -y 279.4 --resolution 75 --mode 'Color' --format=pnm > '/tmp/scan_file1.pnm'
```
open the file it creates: [FONT=courier new]/tmp/scan_file1.pnm[/FONT]
if it works with sudo this should be able to fix it (it is a bash script)
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/scanner-udev-rule-maker.tar.bz2)

Hallo, I am relatively new, but you helped me. It works with sudo ...
I loaded the script down. Now I want to know, how I can install the scipt to fix the problem. Or do I have to act as root every time?
Thanks a Lot, petmue.

---

### Post by Jan Greeff on 2018-02-25
X-Sane seems to have a blockage when it comes to scanning from Canon hardware. After much useless battling I found Skanlite in the software centre. It picked the scanner up immediately and works like a charm.

---

