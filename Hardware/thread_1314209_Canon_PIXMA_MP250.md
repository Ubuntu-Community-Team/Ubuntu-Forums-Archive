---
title: "Canon PIXMA MP250"
date: 2009-11-04
forum: Hardware
---

### Post by utilitytrack on 2009-11-04
Hello everybody!

I purchased these device several day ago. Coming home and plug MP250 to computer (with Ubuntu 9.04), I unable to make it work.

The fact is that for MP250 don't exist the drivers (today).

On a official site Canon is written that drivers be available "Autumn 2009" ([http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp]("http://ubuntuforums.org/Hello%20anybody%21%20%20I%20purchased%20these%20device%20several%20day%20ago.%20Coming%20home%20and%20plug%20MP250%20to%20computer,%20I%20unable%20to%20make%20it%20work.%20%20The%20fact%20is%20that%20for%20MP250%20don%27t%20exist%20the%20drivers%20%28today%29.%20%20On%20a%20official%20site%20Canon%20is%20written%20that%20drivers%20be%20available%20%22Autumn%202009%22%20%28http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp%29"))

Please advise me how to make these device work. Any ideas?


UPDATE: These messages appear when i plug mp250 into USB port:

```
primer@ubuntu:~$ tail -f /var/log/messages
...
Nov  2 23:29:53 debian kernel: [ 5679.264028] usb 2-3: new high speed USB device using ehci_hcd and address 3
Nov  2 23:29:53 debian kernel: [ 5679.398706] usb 2-3: configuration #1 chosen from 1 choice
Nov  2 23:29:53 debian kernel: [ 5679.401183] usb 2-3: New USB device found, idVendor=04a9, idProduct=173a
Nov  2 23:29:53 debian kernel: [ 5679.401194] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov  2 23:29:53 debian kernel: [ 5679.401197] usb 2-3: Product: MP250 series
Nov  2 23:29:53 debian kernel: [ 5679.401199] usb 2-3: Manufacturer: Canon
Nov  2 23:29:53 debian kernel: [ 5679.401201] usb 2-3: SerialNumber: E01D68
Nov  2 23:29:53 debian kernel: [ 5679.525207] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x173A
Nov  2 23:29:53 debian kernel: [ 5679.525231] usbcore: registered new interface driver usblp
...

```PS 
don't tell me about "take back it into shop!"

[SIZE=6]**UPDATE**[/SIZE][SIZE=6] ([/SIZE][SIZE=6]21 november 2009[/SIZE][SIZE=6])[/SIZE]

[SIZE=4]Several day ago problems with drivers for this hardware has been solved. Canon Inc. made available (finally!) official drivers: 1) for printing **cnijfilter-mp250series** (v3.20-1) and **cnijfilter-common** (v3.20-1); 2) for scanning **scangearmp-common** (v1.40-1) and **scangearmp-mp250series** (v1.40-1). You can download their from [http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux)
[/SIZE]
also don't forget that manuals will be useful: [http://support-au.canon.com.au/P/search?model=PIXMA%20MP250&filter=0&menu=Manual](http://support-au.canon.com.au/P/search?model=PIXMA%20MP250&filter=0&menu=Manual)

**they work well with with CUPS (all newer versions until v1.4.4 incl.)**[SIZE=4]

good luck!
[/SIZE]

[SIZE="6"]*******[/SIZE]

[SIZE="6"]**UPDATE2:**[/SIZE][SIZE="5"]** the new version of Canon drivers (3 september 2010)**[/SIZE]

[SIZE="4"]**For further details please see my post: [http://ubuntuforums.org/showpost.php?p=9969327&postcount=40]("http://ubuntuforums.org/showpost.php?p=9969327&postcount=40")**[/SIZE]

---

### Post by hal10000 on 2009-11-04
Install [COLOR="Red"]cupsys-driver-gutenprint[/COLOR] and use the driver for Canin Pixma MP 220. Maybe you can get it work with these.

---

### Post by utilitytrack on 2009-11-04
Thanks. I will try and then write about the results

---

### Post by utilitytrack on 2009-11-04
I used drivers MP220, MP150, MP180, MP500 MP610 and others. No reaction. Test page don't printed. Full silence.

On a CUPS page:

**Description:** Canon_pixma_MP250 
**Location: **home 
**Driver:** Canon PIXMA MP220 - CUPS+Gutenprint v5.2.4 (color, 2-sided printing)
**Connection:** usb://Canon/MP250%20series 
**Defaults:** job-sheets=none, none media=iso_a4_210x297mm sides=one-sided

What am I doing wrong?

---

### Post by da_pingwin on 2009-11-04
Just picked up this printer for the wife, she also is on 9.04 and it does nothing. The queue show's the job processing and then completing, but the printer appears to have no reaction to the job.

---

### Post by utilitytrack on 2009-11-05
**da_pingwin, **this is bad and not funny advise. I need real ideas.

---

### Post by utilitytrack on 2009-11-07
subject

---

### Post by milawynsrealm on 2009-11-14
I'm having the same problem here. I have the same exact printer (MP250) and trying the other printer options gives me no results. I tried to use the driver on the CD with WINE, but it kept crashing on me before the install could start (maybe using WINE wasn't the best idea, but it was all I had left). Is there no active driver support for this printer?

---

### Post by utilitytrack on 2009-11-14
As far I know, no some support (today). Canon is no offer drivers, Gutenprint is no offer drivers... The situation is difficult and unpleasant. So, I think that we made mistake when purchased this device. However I don't lose hope that everything will be fine. 

PS Nevertheless the commercial solution exist. Look at Turboprint.

---

### Post by Jan S on 2009-11-17
Hi!

I bought the PIXMA MP270 and had the same problem until I stumbled on the Canon Australian site. They have the drivers for MP250 there too.

[http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP250%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

My problem is that I can't get the scanner working. I installed the drivers but sane can't find the scanner.

---

### Post by Procuro on 2009-11-19
Thanks for the driver link. Good news, I was able to get the scanner working in addition to the printer :) You need to install the latest git version of Sane and compile it yourself. There are excellent directions here:

[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

This scanner isn't supported with Sane 1.0.20 or older. And guess which version Ubuntu 9.10 ships with? 1.0.20... meaning we just missed the mark, but I'm guessing this will be supported out of the box with the next version of Ubuntu with an updated package. Good luck :popcorn:

---

### Post by Jan S on 2009-11-20
Stupid me... The scanner drivers come with a scanning software scangearmp.

---

### Post by utilitytrack on 2009-11-20
[B]

[SIZE=4][COLOR=Black]YES! Now drivers is exist![/COLOR][/SIZE][/B]  See first post ([http://ubuntuforums.org/showthread.php?p=8240701#post8240701](http://ubuntuforums.org/showthread.php?p=8240701#post8240701))


> **Jan S said:**
>  ... The scanner drivers come with a scanning software scangearmp.

Yes, now we can make scanning with scangearmp. However IMHO programs from SANE Project really better. For use it you need download fresh (CVS) tarball with backends: [http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/) . After unpack and compile (don't forget first install libusb-dev), you need copy all sane-libraries from /usr/local/lib into /usr/lib. After this, command [FONT=Courier New]scanimage -L[/FONT] will found device.

---

### Post by Jan S on 2009-11-20
> Yes, now we can make scanning with scangearmp. However IMHO programs from SANE Project really better. For use it you need download fresh (CVS) tarball with backends: [http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/) . After unpack and compile (don't forget first install libusb-dev), you need copy all sane-libraries from /usr/local/lib into /usr/lib. After this, command [FONT=Courier New]scanimage -L[/FONT] will found device.

Thanks... I was almost about to do this, but then I got it to work. The Canon drivers are good enough for me. So I'll stick with them untill I find some problems with them.

---

### Post by rugbywarrior on 2009-11-30
I downloaded the manual and followed the instructions to install the scanner.  It still didn't work at first until I restarted my computer, then it worked fine.  That might help.

---

### Post by utilitytrack on 2009-11-30
Please tell us that you make when installing the device. Step by step. What drivers and OS do you use?

---

### Post by SteveFoerster on 2009-12-06
> **utilitytrack said:**
> Yes, now we can make scanning with scangearmp. However IMHO programs from SANE Project really better. For use it you need download fresh (CVS) tarball with backends: [http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/) . After unpack and compile (don't forget first install libusb-dev), you need copy all sane-libraries from /usr/local/lib into /usr/lib. After this, command [FONT=Courier New]scanimage -L[/FONT] will found device.
That's a bit intimidating to us newbies!  Alternatively, is there a software source we can add so that XSane will be automatically kept more up to date by the Update Manager without going through all that?

I mean, I have the drivers installed and I'm printing and scanning okay, I'm just curious because it would be nice for my wife and kids not to have to open a terminal to scan things.

-=Steve=-

---

### Post by spyderpride on 2009-12-30
[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

Try this.  You do it once and xsane should start working.


Summary:

$ sudo apt-get install libusb-dev build-essential

Download the latest sane-backends git, cd into the directory wherever you saved it.

$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

$ make

$ sudo make install

---

### Post by Sennacherib on 2010-02-03
Sorry to resurrect this threat, but I'm missing something in my own MP350 installation.

I plugged it in and Karmic got some drivers by itself and installed itself, but when I tried to print off a test document nothing came out; though, the print queue history said it was printed.

I got the two drivers from the canon australia site and installed them. Restarted the computer and printer, but it's just the same.  The computer thinks it printed, but nothing comes out.  

What is interesting is that in Printer Properties all the buttons for test pages and print head cleaning become active and grey out as I turn the printer on and off, so there is some communication from the printer to the computer.

Is there something I've missed or should try?

---

### Post by MasterNetra on 2010-03-04
> **SteveFoerster said:**
> That's a bit intimidating to us newbies!  Alternatively, is there a software source we can add so that XSane will be automatically kept more up to date by the Update Manager without going through all that?

I mean, I have the drivers installed and I'm printing and scanning okay, I'm just curious because it would be nice for my wife and kids not to have to open a terminal to scan things.

-=Steve=-

I know this is really late but there are these PPAs: (xsane) [https://launchpad.net/~dpm/+archive/ppa](https://launchpad.net/~dpm/+archive/ppa) (sane): [https://launchpad.net/~robert-ancell/+archive/sane-backends](https://launchpad.net/~robert-ancell/+archive/sane-backends) however its only for Karmic. But I suppose you could attempt to use karmic's entry, no guarantee it will work right for ya though. But as they say, nothing ventured, nothing gained.

---

### Post by ngkengyap on 2010-03-15
The driver works for me on Ubuntu Karmic. The bad bit of this is that the driver does not allow me to print in grayscale by default. Although it has a printuimp250 command installed, which is hidden, it does not seem to work.

After reading the manual from Canon, I have made the grayscale printing working too. For those who need it, here is the fast tip:

Under System-->Administration-->Printing

right click MP250 that you have already setup, then select Properties from the popup menu, go to Job Options, scroll down to the bottom, add this option in:

CNGrayscale

click the Add button to add the option to the list.

Beside the CNGrayscale option, type in TRUE in the textfield, then click Apply, and close the Properties dialog.

By doing this, this printer is setup to be Grayscale printing by default. You can definitely have another copy of printer setup, pointing to the same printer, but for color printing. This is what i have done. 

For those who are really fluent in Linux and PPD, here is something perhaps you can help me up. I ve tried to edit the ppd file, it does not seem to work. Any idea?

Good luck
[]("http://www.canon.co.uk/Terms_and_Conditions/index.asp")

---

### Post by kayakfisher on 2010-03-15
Many thanks, but for me Karmic does not work. Seems for now I'm stuck with 8.04 on a Compaq Armada M700. All distro's above 8.04 turn my machine into a lump until pulling the battery pack and restarting to Win98Se (sorry to cuss). I need this printer/scanner to work and have very little time left yo fix it.

---

### Post by vbgunz on 2010-04-13
Fellas I have a 64bit system and am considering getting this all-in-one. For those of you who got this working using the official Canon debian packages (32bit), are you successful on your 64 systems? Is everything OK?

---

### Post by blueridgedog on 2010-04-18
I am considering this as well, due to the price of the ink (vs HP and vs Kodak which has no Linux driver).  Before ordering it, I would love to hear from someone using it on a 64 bit 9.10 install.

---

### Post by vbgunz on 2010-04-18
I went ahead and sort of dived into just getting this printer. On my Kubuntu 9.10 64 bit system the 32 bit drivers available at the Canon site worked a charm.

There is some admonition though. I personally used dpkg and if you will too you will need the --force-architecture option in order to successfully install the 32 bit Debian packages on a 64 bit system.

Also, you can use the install.sh script included in the bundle OR you can install the drivers one by one starting with 'common'. If you use the install.sh script use bash and not sh to execute it.

I have not tested the scanner in any way (really don't need it) and am sort of waiting on 10.4 before I ever try. Supposedly the sane packages required for full functionality are in 10.4.

---

### Post by teeliina on 2010-04-19
Hi all. I've got the pixma mp270, and I'm using ubu 9.10 and it should be the 64-bit. I have a smallish problem: I can't scan. I got &installed both scangear and print- downloads from the aussie-site. Now, the printing worked fine from the start, but gimp tells me that 'cannot find available scanner, check cable connections, scanner status and try again' But the power is on, cable connected and nothing happens eeven if I hit the scan button on the printer.
:confused:
How do I add a scanner, change the default scanner or something, that is get my computer to recognize the one I already have? The scanner works fine if I connect it to my windows-laptop, so I've been scanning through it. but that's just a workaround...

---

### Post by alf21 on 2010-05-08
I have the same problem ... printer works now after installing drivers, scanner doesn't work!

---

### Post by alf21 on 2010-05-08
I followed the instructions from 

[http://ubuntica.com/pixma-mp250-on-ubuntu.html](http://ubuntica.com/pixma-mp250-on-ubuntu.html)

Scanner and printer both work now :)

---

### Post by vbgunz on 2010-05-08
> **alf21 said:**
> I followed the instructions from 

[http://ubuntica.com/pixma-mp250-on-ubuntu.html](http://ubuntica.com/pixma-mp250-on-ubuntu.html)

Scanner and printer both work now :)

I followed those directions but when it came to the ```
sudo make install
``` part I replaced it with sudo checkinstall and pretty much followed the defaults from there on out. Scanner works.

Check here for why I used checkinstall
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

Some notes on the linked article are
```
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
``` is correct here using double dashes. The article corrupts the double dashes.

```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE:="0666"
SUBSYSTEM=="usb_device",MODE:="0666"
``` should be safer here using double quotes Vs &#8243;.

If you have a 64bit processor the dpkg files provided by Canon won't automatically install with dpkg -i. You'll need to use ```
sudo dpkg --force-architecture -i ...
```.

I am using Kubuntu and xsane and libsane-extras are not installed by default. I installed these packages too (prior to following the article).

Good luck!

---

### Post by opt1k on 2010-05-24
[[IMG]http://img526.imageshack.us/img526/1959/screenshoteqw.th.png[/IMG]](http://img526.imageshack.us/i/screenshoteqw.png/)


Hi. Uploaded my custom ppd for this printer, and posted basic install instructions. 

ppd features:

1. defaults to fast draft in gray scale mode.
2. allows dpi selection
3. adds other hidden features only available via tweaking the ppd
4. full graphical configuration of most used settings.



This printer is now for sale for $40 at [Walmart]("http://www.walmart.com/ip/Canon-Pixma-MP250-Photo-All-In-One-Inkjet-Printer-Copier-Scanner/12534987") in store and available via site to store. And the proper driver is available from the Canon site.  Very good deal IMO.

Quick info:
[http://www.techsaver.com/2010/04/canon_pixma_mp250_inkjet_multi.php]("http://www.techsaver.com/2010/04/canon_pixma_mp250_inkjet_multi.php")

**Driver Install:**
> 
Get them from the canon site. Or from my links.
[http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux)
[quote]
Printer Driver:
[http://hotfile.com/dl/44541796/1296085/cnijfilter-mp250series-3.20-1-i386-deb.tar.gz.html](http://hotfile.com/dl/44541796/1296085/cnijfilter-mp250series-3.20-1-i386-deb.tar.gz.html)
0. Open Terminal
1. tar xvjf cnijfilter-mp250series-3.20-1-i386-deb.tar.gz
2. cd cnijfilter*
3. sudo bash ./install.sh

method 2:
extract and double click all .deb packages and install

[http://hotfile.com/dl/44541932/d0da651/scangearmp-mp250series-1.40-1-i386-deb.tar.gz.html](http://hotfile.com/dl/44541932/d0da651/scangearmp-mp250series-1.40-1-i386-deb.tar.gz.html)
0. Open Terminal
1. tar xvjf scangearmp-mp250series-1.40-1-i386-deb.tar.gz
2. cd scangearmp*
3. sudo bash ./install.sh

method 2:
extract and double click all .deb packages and install


Icon for Canon scanner software:
[http://hotfile.com/dl/45122555/510f90a/mpg250-scanner.desktop.html](http://hotfile.com/dl/45122555/510f90a/mpg250-scanner.desktop.html)
save as:
/usr/share/applications/scangearmp.desktop
> 
[Desktop Entry]
Name=Canon MP250 Scanner
Comment=Scan Documents
Exec=scangearmp
Icon=scanner
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Graphics;Scanning;
X-GNOME-Gettext-Domain=simple-scan



**Alternate scanner install method using cups/simple-scan/xsane**
> 
1. Menu: System - Administration - Software Sources
2. Click Tab: Other Software
3. Click Add, and enter in ppa:robert-ancell/sane-backends
4. Close/Update

5. Menu: System - Administration - Update Manager
6. Update all software.

7. Press ALT+F2
8. Enter in gksudo gedit /etc/udev/rules.d/40-scanner-permissions.rules
9. Paste the following in and save. 
[quote] SUBSYSTEM==&#8221;usb&#8221;, ENV{DEVTYPE}==&#8221;usb_device&#8221;, MODE:=&#8221;0666&#8243;

SUBSYSTEM==&#8221;usb_device&#8221;,MODE:=&#8221;0666&#8243; 

10. Use simple-scan software from the Graphics menu as usual.

(thanks vbgunz/Robert Ancell)
[/quote]

[/quote]

**Custom ppd install:**
> 
[http://hotfile.com/dl/45122411/328a2ac/canonmp250.ppd.html](http://hotfile.com/dl/45122411/328a2ac/canonmp250.ppd.html)
save as:
/usr/share/cups/model/canonmp250.ppd

Config:
1. put the ppd in /usr/share/cups/model overwriting the canon ppd
2. go to system-administration-printing
3. delete your printer and add it again. 

new options will show for adjusting dpi, gray scale, and the amount of ink used with gamma and density in the printer options portion of properties.

to disable fast draft mode set gamma to 1.8 and density to 0

[quote]
*PPD-Adobe: "4.3"
*%  CUPS add-on PPD file for Canon Inkjet Printer Driver.
*%  Copyright CANON INC. 2001-2009
*%  All Rights Reserved.
*%
*%  This program is free software; you can redistribute it and/or modify
*%  it under the terms of the GNU General Public License as published by
*%  the Free Software Foundation; version 2 of the License.
*%
*%  This program is distributed in the hope that it will be useful,
*%  but WITHOUT ANY WARRANTY; without even the implied warranty of
*%  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
*%  GNU General Public License for more details.
*%
*%  You should have received a copy of the GNU General Public License
*%  along with this program; if not, write to the Free Software
*%  Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307, USA.

*FileVersion: "1.0"
*FormatVersion:	"4.3"
*LanguageEncoding: ISOLatin1
*LanguageVersion: English
*Manufacturer: "Canon"
*ModelName: "Canon MP250 series"
*NickName: "Canon MP250 series Ver.3.20"
*PCFileName: "CNMP250.PPD"
*Product: "(mp250)"
*PSVersion: "(3010.000) 550"
*PSVersion: "(3010.000) 651"
*PSVersion: "(3010.000) 705"
*PSVersion: "(3010.000) 715"
*ShortNickName: "MP250"

*ColorDevice: True
*DefaultColorSpace: RGB
*Throughput: "1"
*LandscapeOrientation: Plus90
*LanguageLevel: "3"
*FileSystem: False
*TTRasterizer: Type42

*cupsFilter: "application/vnd.cups-postscript 0 pstocanonij"
*cupsManualCopies: True
*cupsModelNumber: 356
*cupsVersion: 1.1

*MaxMediaWidth: "612"
*MaxMediaHeight: "1917"
*CenterRegistered: False
*HWMargins: 9.64 14.17 9.64 8.50
*LeadingEdge Short: ""
*DefaultLeadingEdge: Short
*VariablePaperSize: True
*ParamCustomPageSize Width: 1 points 155.91 612.00
*ParamCustomPageSize Height: 2 points 257.96 1916.23
*ParamCustomPageSize WidthOffset: 3 points 0 0
*ParamCustomPageSize HeightOffset: 4 points 0 0
*ParamCustomPageSize Orientation: 5 int 1 1
*CustomPageSize True: "pop pop pop <</PageSize [5 -2 roll] /ImagingBBox null>>setpagedevice"

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 150
*Resolution 75/75 dpi: "<</HWResolution[75 75]>>setpagedevice"
*Resolution 100/100 dpi: "<</HWResolution[100 100]>>setpagedevice"
*Resolution 150/150 dpi: "<</HWResolution[150 150]>>setpagedevice"
*Resolution 300/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 4800/4800 dpi: "<</HWResolution[4800 4800]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

*OpenUI *PageSize/Page Size: PickOne
*DefaultPageSize: A4
*PageSize Letter/Letter 8.5"x11" 215.9x279.4mm: "<</CNPageSizeName(Letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize Letter.bl/Letter 8.5"x11" 215.9x279.4mm (borderless): "<</CNPageSizeName(Letter.bl)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageSize Legal/Legal 8.5"x14" 215.9x355.6mm: "<</CNPageSizeName(Legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageSize A5/A5 148.0x210.0mm: "<</CNPageSizeName(A5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageSize A4/A4 210.0x297.0mm: "<</CNPageSizeName(A4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize A4.bl/A4 210.0x297.0mm (borderless): "<</CNPageSizeName(A4.bl)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageSize B5/B5 182.0x257.0mm: "<</CNPageSizeName(B5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageSize 4X6/4"x6" 10x15cm 101.6x152.4mm: "<</CNPageSizeName(4X6)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize 4X6.bl/4"x6" 10x15cm 101.6x152.4mm (borderless): "<</CNPageSizeName(4X6.bl)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageSize 4X8/4"x8" 101.6x203.2mm: "<</CNPageSizeName(4X8)/PageSize[288 576]/ImagingBBox null>>setpagedevice"
*PageSize 4X8.bl/4"x8" 101.6x203.2mm (borderless): "<</CNPageSizeName(4X8.bl)/PageSize[288 576]/ImagingBBox null>>setpagedevice"
*PageSize 5X7/5"x7" 13x18cm 127.0x177.8mm: "<</CNPageSizeName(5X7)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageSize 5X7.bl/5"x7" 13x18cm 127.0x177.8mm (borderless): "<</CNPageSizeName(5X7.bl)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageSize 8X10/8"x10" 20x25cm 203.2x254.0mm: "<</CNPageSizeName(8X10)/PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageSize 8X10.bl/8"x10" 20x25cm 203.2x254.0mm (borderless): "<</CNPageSizeName(8X10.bl)/PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageSize l/L 89.0x127.0mm: "<</CNPageSizeName(l)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageSize l.bl/L 89.0x127.0mm (borderless): "<</CNPageSizeName(l.bl)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageSize 2l/2L 127.0x178.0mm: "<</CNPageSizeName(2l)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageSize 2l.bl/2L 127.0x178.0mm (borderless): "<</CNPageSizeName(2l.bl)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageSize postcard/Hagaki 100.0x148.0mm: "<</CNPageSizeName(postcard)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageSize postcard.bl/Hagaki 100.0x148.0mm (borderless): "<</CNPageSizeName(postcard.bl)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageSize postdbl/Hagaki 2 200.0x148.0mm: "<</CNPageSizeName(postdbl)/PageSize[567 420]/ImagingBBox null>>setpagedevice"
*PageSize envelop10p/Comm. Env. #10 4.12"x9.5" 104.6x241.3mm: "<</CNPageSizeName(envelop10p)/PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageSize envelopdlp/DL Env. 110.0x220.0mm: "<</CNPageSizeName(envelopdlp)/PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageSize envj4p/Youkei 4 105.0x235.0mm: "<</CNPageSizeName(envj4p)/PageSize[298 666]/ImagingBBox null>>setpagedevice"
*PageSize envj6p/Youkei 6 98.0x190.0mm: "<</CNPageSizeName(envj6p)/PageSize[278 539]/ImagingBBox null>>setpagedevice"
*PageSize businesscard/Card 2.16"x3.58" 55.0x91.0mm: "<</CNPageSizeName(businesscard)/PageSize[156 258]/ImagingBBox null>>setpagedevice"
*PageSize businesscard.bl/Card 2.16"x3.58" 55.0x91.0mm (borderless): "<</CNPageSizeName(businesscard.bl)/PageSize[156 258]/ImagingBBox null>>setpagedevice"
*PageSize wide/Wide 4"x7.1" 101.6x180.6mm: "<</CNPageSizeName(wide)/PageSize[288 512]/ImagingBBox null>>setpagedevice"
*PageSize wide.bl/Wide 4"x7.1" 101.6x180.6mm (borderless): "<</CNPageSizeName(wide.bl)/PageSize[288 512]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageSize

*OpenUI *PageRegion: PickOne
*DefaultPageRegion: A4
*PageRegion Letter/Letter 8.5"x11" 215.9x279.4mm: "<</CNPageSizeName(Letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion Letter.bl/Letter 8.5"x11" 215.9x279.4mm (borderless): "<</CNPageSizeName(Letter.bl)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
*PageRegion Legal/Legal 8.5"x14" 215.9x355.6mm: "<</CNPageSizeName(Legal)/PageSize[612 1008]/ImagingBBox null>>setpagedevice"
*PageRegion A5/A5 148.0x210.0mm: "<</CNPageSizeName(A5)/PageSize[420 595]/ImagingBBox null>>setpagedevice"
*PageRegion A4/A4 210.0x297.0mm: "<</CNPageSizeName(A4)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion A4.bl/A4 210.0x297.0mm (borderless): "<</CNPageSizeName(A4.bl)/PageSize[595 842]/ImagingBBox null>>setpagedevice"
*PageRegion B5/B5 182.0x257.0mm: "<</CNPageSizeName(B5)/PageSize[516 729]/ImagingBBox null>>setpagedevice"
*PageRegion 4X6/4"x6" 10x15cm 101.6x152.4mm: "<</CNPageSizeName(4X6)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion 4X6.bl/4"x6" 10x15cm 101.6x152.4mm (borderless): "<</CNPageSizeName(4X6.bl)/PageSize[288 432]/ImagingBBox null>>setpagedevice"
*PageRegion 4X8/4"x8" 101.6x203.2mm: "<</CNPageSizeName(4X8)/PageSize[288 576]/ImagingBBox null>>setpagedevice"
*PageRegion 4X8.bl/4"x8" 101.6x203.2mm (borderless): "<</CNPageSizeName(4X8.bl)/PageSize[288 576]/ImagingBBox null>>setpagedevice"
*PageRegion 5X7/5"x7" 13x18cm 127.0x177.8mm: "<</CNPageSizeName(5X7)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageRegion 5X7.bl/5"x7" 13x18cm 127.0x177.8mm (borderless): "<</CNPageSizeName(5X7.bl)/PageSize[360 504]/ImagingBBox null>>setpagedevice"
*PageRegion 8X10/8"x10" 20x25cm 203.2x254.0mm: "<</CNPageSizeName(8X10)/PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageRegion 8X10.bl/8"x10" 20x25cm 203.2x254.0mm (borderless): "<</CNPageSizeName(8X10.bl)/PageSize[576 720]/ImagingBBox null>>setpagedevice"
*PageRegion l/L 89.0x127.0mm: "<</CNPageSizeName(l)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageRegion l.bl/L 89.0x127.0mm (borderless): "<</CNPageSizeName(l.bl)/PageSize[252 360]/ImagingBBox null>>setpagedevice"
*PageRegion 2l/2L 127.0x178.0mm: "<</CNPageSizeName(2l)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageRegion 2l.bl/2L 127.0x178.0mm (borderless): "<</CNPageSizeName(2l.bl)/PageSize[360 505]/ImagingBBox null>>setpagedevice"
*PageRegion postcard/Hagaki 100.0x148.0mm: "<</CNPageSizeName(postcard)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageRegion postcard.bl/Hagaki 100.0x148.0mm (borderless): "<</CNPageSizeName(postcard.bl)/PageSize[283 420]/ImagingBBox null>>setpagedevice"
*PageRegion postdbl/Hagaki 2 200.0x148.0mm: "<</CNPageSizeName(postdbl)/PageSize[567 420]/ImagingBBox null>>setpagedevice"
*PageRegion envelop10p/Comm. Env. #10 4.12"x9.5" 104.6x241.3mm: "<</CNPageSizeName(envelop10p)/PageSize[297 684]/ImagingBBox null>>setpagedevice"
*PageRegion envelopdlp/DL Env. 110.0x220.0mm: "<</CNPageSizeName(envelopdlp)/PageSize[312 624]/ImagingBBox null>>setpagedevice"
*PageRegion envj4p/Youkei 4 105.0x235.0mm: "<</CNPageSizeName(envj4p)/PageSize[298 666]/ImagingBBox null>>setpagedevice"
*PageRegion envj6p/Youkei 6 98.0x190.0mm: "<</CNPageSizeName(envj6p)/PageSize[278 539]/ImagingBBox null>>setpagedevice"
*PageRegion businesscard/Card 2.16"x3.58" 55.0x91.0mm: "<</CNPageSizeName(businesscard)/PageSize[156 258]/ImagingBBox null>>setpagedevice"
*PageRegion businesscard.bl/Card 2.16"x3.58" 55.0x91.0mm (borderless): "<</CNPageSizeName(businesscard.bl)/PageSize[156 258]/ImagingBBox null>>setpagedevice"
*PageRegion wide/Wide 4"x7.1" 101.6x180.6mm: "<</CNPageSizeName(wide)/PageSize[288 512]/ImagingBBox null>>setpagedevice"
*PageRegion wide.bl/Wide 4"x7.1" 101.6x180.6mm (borderless): "<</CNPageSizeName(wide.bl)/PageSize[288 512]/ImagingBBox null>>setpagedevice"
*CloseUI: *PageRegion

*OpenUI *MediaType/Media Type: PickOne
*DefaultMediaType: plain
*MediaType plain/Plain Paper: "<</MediaType(plain)>>setpagedevice"
*MediaType glossygold/Photo Paper Plus Glossy II: "<</MediaType(glossygold)>>setpagedevice"
*MediaType prophoto2/Photo Paper Pro II: "<</MediaType(prophoto2)>>setpagedevice"
*MediaType proplatinum/Photo Paper Pro Platinum: "<</MediaType(proplatinum)>>setpagedevice"
*MediaType semigloss/Photo Paper Plus Semi-gloss: "<</MediaType(semigloss)>>setpagedevice"
*MediaType glossypaper/Glossy Photo Paper: "<</MediaType(glossypaper)>>setpagedevice"
*MediaType matte/Matte Photo Paper: "<</MediaType(matte)>>setpagedevice"
*MediaType highres/High Resolution Paper: "<</MediaType(highres)>>setpagedevice"
*MediaType postcardaddress/Hagaki A: "<</MediaType(postcardaddress)>>setpagedevice"
*MediaType ijpostcard/Ink Jet Hagaki: "<</MediaType(ijpostcard)>>setpagedevice"
*MediaType glossypost/Hagaki K: "<</MediaType(glossypost)>>setpagedevice"
*MediaType prophotopost/Hagaki P: "<</MediaType(prophotopost)>>setpagedevice"
*MediaType postcard/Hagaki: "<</MediaType(postcard)>>setpagedevice"
*MediaType tshirt/T-Shirt Transfers: "<</MediaType(tshirt)>>setpagedevice"
*MediaType envelope/Envelope: "<</MediaType(envelope)>>setpagedevice"
*MediaType otherphoto/Other Photo Paper: "<</MediaType(otherphoto)>>setpagedevice"
*CloseUI: *MediaType

*OpenUI *InputSlot/Paper Source: PickOne
*DefaultInputSlot: asf
*InputSlot asf/Rear Tray: "<</MediaPosition 0>>setpagedevice"
*CloseUI: *InputSlot

*OpenUI *CNExtension/Amount of Extension: PickOne
*DefaultCNExtension: 2
*CNExtension 0/0: "<</CNExtension(0)>>setpagedevice"
*CNExtension 1/1: "<</CNExtension(1)>>setpagedevice"
*CNExtension 2/2: "<</CNExtension(2)>>setpagedevice"
*CNExtension 3/3: "<</CNExtension(3)>>setpagedevice"
*CloseUI: *CNExtension

*DefaultImageableArea: A4
*ImageableArea Letter: "18.14 14.17 594.14 783.50"
*ImageableArea Letter.bl: "0 0 612 792"
*ImageableArea Legal: "18.14 14.17 594.14 999.50"
*ImageableArea A5: "9.64 14.17 409.89 586.77"
*ImageableArea A4: "9.64 14.17 585.64 833.39"
*ImageableArea A4.bl: "0 0 595 842"
*ImageableArea B5: "9.64 14.17 506.27 720.00"
*ImageableArea 4X6: "9.64 14.17 278.36 423.50"
*ImageableArea 4X6.bl: "0 0 288 432"
*ImageableArea 4X8: "9.64 14.17 278.36 567.50"
*ImageableArea 4X8.bl: "0 0 288 576"
*ImageableArea 5X7: "9.64 14.17 350.36 495.50"
*ImageableArea 5X7.bl: "0 0 360 504"
*ImageableArea 8X10: "9.64 14.17 566.36 711.50"
*ImageableArea 8X10.bl: "0 0 576 720"
*ImageableArea l: "9.64 14.17 242.65 351.50"
*ImageableArea l.bl: "0 0 252 360"
*ImageableArea 2l: "9.64 14.17 350.36 496.06"
*ImageableArea 2l.bl: "0 0 360 505"
*ImageableArea postcard: "9.64 14.17 273.83 411.02"
*ImageableArea postcard.bl: "0 0 283 420"
*ImageableArea postdbl: "9.64 14.17 557.29 411.02"
*ImageableArea envelop10p: "9.64 92.13 287.35 661.32"
*ImageableArea envelopdlp: "9.64 92.13 302.17 600.94"
*ImageableArea envj4p: "9.64 92.13 288.00 643.46"
*ImageableArea envj6p: "9.64 92.13 268.16 515.91"
*ImageableArea businesscard: "9.64 14.17 146.27 249.45"
*ImageableArea businesscard.bl: "0 0 156 258"
*ImageableArea wide: "9.64 14.17 278.36 503.49"
*ImageableArea wide.bl: "0 0 288 512"

*DefaultPaperDimension: A4
*PaperDimension Letter: "612 792"
*PaperDimension Letter.bl: "613 793"
*PaperDimension Legal: "612 1008"
*PaperDimension A5: "420 595"
*PaperDimension A4: "595 842"
*PaperDimension A4.bl: "596 843"
*PaperDimension B5: "516 729"
*PaperDimension 4X6: "288 432"
*PaperDimension 4X6.bl: "289 433"
*PaperDimension 4X8: "288 576"
*PaperDimension 4X8.bl: "289 577"
*PaperDimension 5X7: "360 504"
*PaperDimension 5X7.bl: "361 505"
*PaperDimension 8X10: "576 720"
*PaperDimension 8X10.bl: "577 721"
*PaperDimension l: "252 360"
*PaperDimension l.bl: "253 361"
*PaperDimension 2l: "360 505"
*PaperDimension 2l.bl: "361 506"
*PaperDimension postcard: "283 420"
*PaperDimension postcard.bl: "284 421"
*PaperDimension postdbl: "567 420"
*PaperDimension envelop10p: "297 684"
*PaperDimension envelopdlp: "312 624"
*PaperDimension envj4p: "298 666"
*PaperDimension envj6p: "278 539"
*PaperDimension businesscard: "156 258"
*PaperDimension businesscard.bl: "157 259"
*PaperDimension wide: "288 512"
*PaperDimension wide.bl: "289 513"



*UIConstraints: *MediaType highres *PageSize Letter.bl
*UIConstraints: *PageSize Letter.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize A4.bl
*UIConstraints: *PageSize A4.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize 4X6.bl
*UIConstraints: *PageSize 4X6.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize 4X8.bl
*UIConstraints: *PageSize 4X8.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize 5X7.bl
*UIConstraints: *PageSize 5X7.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize 8X10.bl
*UIConstraints: *PageSize 8X10.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize l.bl
*UIConstraints: *PageSize l.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize 2l.bl
*UIConstraints: *PageSize 2l.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize postcard.bl
*UIConstraints: *PageSize postcard.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize businesscard.bl
*UIConstraints: *PageSize businesscard.bl *MediaType highres
*UIConstraints: *MediaType highres *PageSize wide.bl
*UIConstraints: *PageSize wide.bl *MediaType highres
*UIConstraints: *MediaType tshirt *PageSize Letter.bl
*UIConstraints: *PageSize Letter.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize A4.bl
*UIConstraints: *PageSize A4.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize 4X6.bl
*UIConstraints: *PageSize 4X6.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize 4X8.bl
*UIConstraints: *PageSize 4X8.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize 5X7.bl
*UIConstraints: *PageSize 5X7.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize 8X10.bl
*UIConstraints: *PageSize 8X10.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize l.bl
*UIConstraints: *PageSize l.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize 2l.bl
*UIConstraints: *PageSize 2l.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize postcard.bl
*UIConstraints: *PageSize postcard.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize businesscard.bl
*UIConstraints: *PageSize businesscard.bl *MediaType tshirt
*UIConstraints: *MediaType tshirt *PageSize wide.bl
*UIConstraints: *PageSize wide.bl *MediaType tshirt
*UIConstraints: *MediaType envelope *PageSize Letter.bl
*UIConstraints: *PageSize Letter.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize A4.bl
*UIConstraints: *PageSize A4.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize 4X6.bl
*UIConstraints: *PageSize 4X6.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize 4X8.bl
*UIConstraints: *PageSize 4X8.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize 5X7.bl
*UIConstraints: *PageSize 5X7.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize 8X10.bl
*UIConstraints: *PageSize 8X10.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize l.bl
*UIConstraints: *PageSize l.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize 2l.bl
*UIConstraints: *PageSize 2l.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize postcard.bl
*UIConstraints: *PageSize postcard.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize businesscard.bl
*UIConstraints: *PageSize businesscard.bl *MediaType envelope
*UIConstraints: *MediaType envelope *PageSize wide.bl
*UIConstraints: *PageSize wide.bl *MediaType envelope

*DefaultFont: Courier
*Font Courier: Standard "(001.001)" Standard ROM

*%CNPpdToOptKey PageSize --papersize
*%CNPpdToOptKey MediaType --media
*%CNPpdToOptKey InputSlot --paperload
*%CNPpdToOptKey CNCartridge --cartridge
*%CNPpdToOptKey CNQuality --quality
*%CNPpdToOptKey CNHalftoning --halftoning
*%CNPpdToOptKey CNRenderIntent --renderintent
*%CNPpdToOptKey CNGamma --gamma
*%CNPpdToOptKey CNBalanceC --balance_c
*%CNPpdToOptKey CNBalanceM --balance_m
*%CNPpdToOptKey CNBalanceY --balance_y
*%CNPpdToOptKey CNDensity --density
*%CNPpdToOptKey CNGrayscale --grayscale
*%CNPpdToOptKey CNCopies --copies
*%CNPpdToOptKey CNContrast --contrast
*%CNPpdToOptKey CNInkCartridgeSettings --inkcartridgesettings
*%CNPpdToOptKey CNExtension --extension

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 4
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard-Economy: "4"
*%DoesntWORK CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

*OpenUI *CNGrayscale/Grayscale: PickOne
*DefaultCNGrayscale: true
*CNGrayscale false/Off: "false"
*CNGrayscale true/On: "true"
*CloseUI: *CNGrayscale

*OpenGroup: Color Adjustment 

*OpenUI *CNGamma/Gamma Adjustment: PickOne 
*DefaultCNGamma: 1.4                      
*CNGamma 1.4/1.4: "<</CNGamma(1.4)>>setpagedevice" 
*CNGamma 1.8/1.8: "<</CNGamma(1.8)>>setpagedevice" 
*CNGamma 2.2/2.2: "<</CNGamma(2.2)>>setpagedevice" 
*CloseUI: *CNRenderIntent                          


*OpenUI *CNBalanceC/Balance Cyan: PickOne 
*DefaultCNBalanceC: 0                    
*CNBalanceC -50/-50: "<</CNBalanceC(-50)>>setpagedevice" 
*CNBalanceC -40/-40: "<</CNBalanceC(-40)>>setpagedevice" 
*CNBalanceC -30/-30: "<</CNBalanceC(-30)>>setpagedevice" 
*CNBalanceC -20/-20: "<</CNBalanceC(-20)>>setpagedevice" 
*CNBalanceC -10/-10: "<</CNBalanceC(-10)>>setpagedevice" 
*CNBalanceC 0/0: "<</CNBalanceC(0)>>setpagedevice"      
*CNBalanceC 10/10: "<</CNBalanceC(10)>>setpagedevice"    
*CNBalanceC 20/20: "<</CNBalanceC(20)>>setpagedevice"    
*CNBalanceC 30/30: "<</CNBalanceC(30)>>setpagedevice"    
*CNBalanceC 40/40: "<</CNBalanceC(40)>>setpagedevice"    
*CNBalanceC 50/50: "<</CNBalanceC(50)>>setpagedevice"    
*CloseUI: *CNBalanceC                                    

*OpenUI *CNBalanceM/Balance Magenta: PickOne 
*DefaultCNBalanceM: 0                        
*CNBalanceM -50/-50: "<</CNBalanceM(-50)>>setpagedevice" 
*CNBalanceM -40/-40: "<</CNBalanceM(-40)>>setpagedevice" 
*CNBalanceM -30/-30: "<</CNBalanceM(-30)>>setpagedevice" 
*CNBalanceM -20/-20: "<</CNBalanceM(-20)>>setpagedevice" 
*CNBalanceM -10/-10: "<</CNBalanceM(-10)>>setpagedevice" 
*CNBalanceM 0/0: "<</CNBalanceM(0)>>setpagedevice"      
*CNBalanceM 10/10: "<</CNBalanceM(10)>>setpagedevice"    
*CNBalanceM 20/20: "<</CNBalanceM(20)>>setpagedevice"    
*CNBalanceM 30/30: "<</CNBalanceM(30)>>setpagedevice"    
*CNBalanceM 40/40: "<</CNBalanceM(40)>>setpagedevice"    
*CNBalanceM 50/50: "<</CNBalanceM(50)>>setpagedevice"    
*CloseUI: *CNBalanceM                                    

*OpenUI *CNBalanceY/Balance Yellow: PickOne 
*DefaultCNBalanceY: 0                      
*CNBalanceY -50/-50: "<</CNBalanceY(-50)>>setpagedevice" 
*CNBalanceY -40/-40: "<</CNBalanceY(-40)>>setpagedevice" 
*CNBalanceY -30/-30: "<</CNBalanceY(-30)>>setpagedevice" 
*CNBalanceY -20/-20: "<</CNBalanceY(-20)>>setpagedevice" 
*CNBalanceY -10/-10: "<</CNBalanceY(-10)>>setpagedevice" 
*CNBalanceY 0/0: "<</CNBalanceY(0)>>setpagedevice"      
*CNBalanceY 10/10: "<</CNBalanceY(10)>>setpagedevice"    
*CNBalanceY 20/20: "<</CNBalanceY(20)>>setpagedevice"    
*CNBalanceY 30/30: "<</CNBalanceY(30)>>setpagedevice"    
*CNBalanceY 40/40: "<</CNBalanceY(40)>>setpagedevice"    
*CNBalanceY 50/50: "<</CNBalanceY(50)>>setpagedevice"    
*CloseUI: *CNBalanceY                                    

*OpenUI *CNBalanceK/Balance Black: PickOne 
*DefaultCNBalanceK: 0                      
*CNBalanceK -50/-50: "<</CNBalanceK(-50)>>setpagedevice" 
*CNBalanceK -40/-40: "<</CNBalanceK(-40)>>setpagedevice" 
*CNBalanceK -30/-30: "<</CNBalanceK(-30)>>setpagedevice" 
*CNBalanceK -20/-20: "<</CNBalanceK(-20)>>setpagedevice" 
*CNBalanceK -10/-10: "<</CNBalanceK(-10)>>setpagedevice" 
*CNBalanceK 0/0: "<</CNBalanceK(0)>>setpagedevice"      
*CNBalanceK 10/10: "<</CNBalanceK(10)>>setpagedevice"    
*CNBalanceK 20/20: "<</CNBalanceK(20)>>setpagedevice"    
*CNBalanceK 30/30: "<</CNBalanceK(30)>>setpagedevice"    
*CNBalanceK 40/40: "<</CNBalanceK(40)>>setpagedevice"    
*CNBalanceK 50/50: "<</CNBalanceK(50)>>setpagedevice"    
*CloseUI: *CNBalanceK                                    

*OpenUI *CNDensity/Density: PickOne 
*DefaultCNDensity: -50                
*CNDensity -50/-50: "<</CNDensity(-50)>>setpagedevice" 
*CNDensity -40/-40: "<</CNDensity(-40)>>setpagedevice" 
*CNDensity -30/-30: "<</CNDensity(-30)>>setpagedevice" 
*CNDensity -20/-20: "<</CNDensity(-20)>>setpagedevice" 
*CNDensity -10/-10: "<</CNDensity(-10)>>setpagedevice" 
*CNDensity 0/0: "<</CNDensity(0)>>setpagedevice"      
*CNDensity 10/10: "<</CNDensity(10)>>setpagedevice"    
*CNDensity 20/20: "<</CNDensity(20)>>setpagedevice"    
*CNDensity 30/30: "<</CNDensity(30)>>setpagedevice"    
*CNDensity 40/40: "<</CNDensity(40)>>setpagedevice"    
*CNDensity 50/50: "<</CNDensity(50)>>setpagedevice"    
*CloseUI: *CNDensity                                  

*CloseGroup: Color Adjustment 



*%
*% internalversion : 3.20.01.001
*%


[/quote]

---

### Post by vbgunz on 2010-05-26
No joke, the easiest method for getting the scanner to work does not involve downloading the sane-backends sources. It does not involve configuring/building sane-backends. It does *not* involve creating the 40-scanner-permissions.rule.

Just add this repo/update/upgrade and be done with it.
ppa:robert-ancell/sane-backends

This works perfectly for Kubuntu 10.04. Thank you Robert!

---

### Post by opt1k on 2010-05-27
Thanks for the ppa.  That makes it a lot less painless and now no more canon scanner software.

Try my modified ppd for the printer from my previous post.  Its really helpful for easily saving ink.

> **vbgunz said:**
> No joke, the easiest method for getting the scanner to work does not involve downloading the sane-backends sources. It does not involve configuring/building sane-backends. It does involve creating the 40-scanner-permissions.rule.

Just add this repo/update/upgrade and be done with it.
ppa:robert-ancell/sane-backends

This works perfectly for Kubuntu 10.04. Thank you Robert!

> sudo gedit

Onne Gedit is opened, copy and paste the following text into the empty gedit file

SUBSYSTEM==”usb”, ENV{DEVTYPE}==”usb_device”, MODE:=”0666&#8243;

SUBSYSTEM==”usb_device”,MODE:=”0666&#8243;

Save the file in the /etc/udev/rules.d/ directory, titled 40-scanner-permissions.rules

Your PIXMA MP250 scanner is now installed. You may now fire up the Xsane scanning utility and scan away.

---

### Post by texla on 2010-06-18
> **ngkengyap said:**
> The driver works for me on Ubuntu Karmic. The bad bit of this is that the driver does not allow me to print in grayscale by default. Although it has a printuimp250 command installed, which is hidden, it does not seem to work.

After reading the manual from Canon, I have made the grayscale printing working too. For those who need it, here is the fast tip:

Under System-->Administration-->Printing

right click MP250 that you have already setup, then select Properties from the popup menu, go to Job Options, scroll down to the bottom, add this option in:

CNGrayscale

click the Add button to add the option to the list.

Beside the CNGrayscale option, type in TRUE in the textfield, then click Apply, and close the Properties dialog.

By doing this, this printer is setup to be Grayscale printing by default. You can definitely have another copy of printer setup, pointing to the same printer, but for color printing. This is what i have done. 

For those who are really fluent in Linux and PPD, here is something perhaps you can help me up. I ve tried to edit the ppd file, it does not seem to work. Any idea?

Good luck

This worked for me - THANKS!

As for the scanner - it was easy, I installed the drivers from the deb files at the Cannon website which included a scangear program for linux.

[http://software.canon-europe.com/products/0010698.asp](http://software.canon-europe.com/products/0010698.asp)

then I just added a launch button to the panel with the command scangearmp - scangear works great - you can select all or sections of the document to scan and go up to 1200dpi - oh, BTW I'm using the Pixma 330...

---

### Post by utilitytrack on 2010-08-04
to **opt1k**

Thanks for the modified [FONT=Courier New]ppd[/FONT] file. You work is great. It's make print settings more fine and add many useful properties. But I might say that I don't use your custom [FONT=Courier New]ppd[/FONT] because no difference for my how rapid spend the inks. I'm not worried about it since I purchased few pots with inks (for example if somebody interested it's InkTek C2010 black pigment inks for PG-510 cartridge) and refilled the heads. It's works perfectly. And it's my economy :)

---

### Post by harbhag on 2010-09-23
I have posted a complete tutorial to get canon pixma mp250 printer scanner to work on Ubuntu. Check out the link below

[http://harbhag.wordpress.com/2010/04/09/canon-pixma-mp258-or-any-mp250-series-printer-on-ubuntu-debian-fedora-and-arch-linux/](http://harbhag.wordpress.com/2010/04/09/canon-pixma-mp258-or-any-mp250-series-printer-on-ubuntu-debian-fedora-and-arch-linux/)

---

### Post by utilitytrack on 2010-09-23
to **harbhag**

Huh! Guy, you had made a strong campaign to promote your blog on this forum. You are crafty, though.

---

### Post by harbhag on 2010-09-25
I am just trying to help. Dont think I am spamming or something and please excuse my english.
Thanks

---

### Post by blueridgedog on 2010-09-26
> **harbhag said:**
> I am just trying to help. Dont think I am spamming or something and please excuse my english.
Thanks

Thanks for your contribution...I don't see it as spamming.

---

### Post by Jeroen De Dauw on 2010-10-13
Thanks for this! Just confirmed it works with my device :)

---

### Post by utilitytrack on 2010-10-14
[SIZE="3"]**Hello again to all PIXMA-people**[/SIZE]

I have for you two news: good and bad at the same time.

As all of you can see, some time ago Canon Inc. released new versions of their printer and scanner drivers.
The new versions are: 

[FONT="Courier New"]cnijfilter-mp250series[/FONT] v3.40 (for printing) and
[FONT="Courier New"]scangearmp-mp250series[/FONT] v1.60 (for scanning)

All of what I will say next related only to printer driver (version for 32bit CPU).

So, it's would be nice if these new version still being working. 
However, in my experience all of I got when I sent documents to printing it's the silence.

As you can understand, this problems with printing appear only when I install new version, because on previous (v3.20) all work excellent.

My environment:

OS: 
```
Debian GNU/Linux (testing)
```

```
$ uname -a
Linux lenovo-laptop 2.6.35.4-custom #1 SMP PREEMPT Mon Sep 6 03:36:21 GMT 2010 i686 GNU/Linux

```

Relevant packages:
```
user@lenovo-laptop:~$ dpkg-query --show cups\* libcups\* cnij\* ghostscript\* libgs8\* system-config-printer\* | column -t
cnijfilter-common             3.40-1
cnijfilter-mp250series        3.40-1
cups                          1.4.4-3
cups-bsd                      1.4.4-3
cups-client                   1.4.4-3
cups-common                   1.4.4-3
cups-driver-gutenprint
cups-pdf
cups-ppdc                     1.4.4-3
cups-pt
cupsddk
cupsddk-drivers
cupsomatic-ppd
cupsys
cupsys-bsd
cupsys-client
cupsys-common
ghostscript                   8.71~dfsg2-6
ghostscript-cups              8.71~dfsg2-6
ghostscript-doc               8.71~dfsg2-6
ghostscript-x                 8.71~dfsg2-6
libcups2                      1.4.4-3
libcups2-dev                  1.4.4-3
libcupscgi1                   1.4.4-3
libcupscgi1-dev               1.4.4-3
libcupsdriver1                1.4.4-3
libcupsdriver1-dev            1.4.4-3
libcupsimage2                 1.4.4-3
libcupsimage2-dev             1.4.4-3
libcupsmime1                  1.4.4-3
libcupsmime1-dev              1.4.4-3
libcupsppdc1                  1.4.4-3
libcupsppdc1-dev              1.4.4-3
libcupsys2
libcupsys2-dev
libgs8                        8.71~dfsg2-6
system-config-printer
system-config-printer-common
system-config-printer-gnome
system-config-printer-kde
system-config-printer-udev

```

Used device URI: 
```
cnijusb:/dev/usb/lp0

```

```
LANG=ru_RU.utf8
LANGUAGE=ru_RU:ru:en_US:en

```


So, dear people, I can advice you don't rush with updates. What the reason of these problems it's we will find out some day.
At the moment I suppose that new version of [FONT="Courier New"]cnijfilter[/FONT] contains some errors and bugs. What are these bugs I don't know exactly.
And I will be grateful if somebody point me where to look :) 

Anyway thanks you Canon for not forgetting us.

---

### Post by Krallus on 2010-10-17
The latest Canon drivers (pre-built!) for Debian work in 64-bit Ubuntu 10.04 - Lucid Lynx.  That's right!  64-bit!  Stop looking and fiddling and just install these! (I wish I had).

Australian Canon Site:


PRINTER DRIVER:

MP250 series IJ Printer Driver Ver. 3.40 for Linux (debian Packagearchive)
Last Updated : 03-Sep-2010
Issue Number : 0100236101
File name : cnijfilter-mp250series-3.40-1-deb.tar.gz
[http://support-au.canon.com.au/contents/AU/EN/0100236101.html](http://support-au.canon.com.au/contents/AU/EN/0100236101.html)

Documentation: [http://support-au.canon.com.au/contents/AU/EN/0300277201.html](http://support-au.canon.com.au/contents/AU/EN/0300277201.html)


SCANNER DRIVER AND SOFTWARE (run "scangearmp" after installation):

MP250 series ScanGear MP Ver. 1.60 for Linux (debian Packagearchive)
Last Updated : 03-Sep-2010
Issue Number : 0100237401
File name : scangearmp-mp250series-1.60-1-deb.tar.gz
[http://support-au.canon.com.au/contents/AU/EN/0100237401.html](http://support-au.canon.com.au/contents/AU/EN/0100237401.html)

Documentation: [http://support-au.canon.com.au/contents/AU/EN/0300278301.html](http://support-au.canon.com.au/contents/AU/EN/0300278301.html)

---

### Post by ParadoxBlue on 2010-10-29
Just installed the drivers for this printer yesterday (haven't installed the scanner drivers yet) but it seems to work flawlessly. One thing I haven't figured out (maybe I'm just not paying attention) is how do I print in grayscale only? No need to waste the colour ink when not needed or wanted. Any help/tips appreciated.

---

### Post by ken78724 on 2011-04-19
has anyone solved the "No drivers issue for the Pixma MX 420? I get no outputs at all and have not found the drivers. 
Kenneth

---

### Post by mjones41 on 2011-05-07
[http://support-au.canon.com.au/contents/AU/EN/0100236101.html](http://support-au.canon.com.au/contents/AU/EN/0100236101.html)

worked for me on both Ubuntu 10.4 and Mint 10.  Comes up in the drivers list as just MP250, so you can miss it if you are not looking closely.

---

### Post by HannuMR on 2011-07-02
> **mjones41 said:**
> [http://support-au.canon.com.au/contents/AU/EN/0100236101.html](http://support-au.canon.com.au/contents/AU/EN/0100236101.html)

worked for me on both Ubuntu 10.4 and Mint 10.  Comes up in the drivers list as just MP250, so you can miss it if you are not looking closely.

Please, can somebody explain step by step installation of those packages:
File name : cnijfilter-mp250series-3.40-1-deb.tar.gz.
File name : scangearmp-mp250series-1.60-1-deb.tar.gz
and how I do this: (run "scangearmp" after installation):

Thanks

---

### Post by lastwordsmith on 2011-07-02
Thanks for pointing us to the Aussie Canon site.  I downloaded the correct driver, and it worked fine.  

Regarding [HannuMR]("http://ubuntuforums.org/member.php?u=945041")'s question above, I downloaded the software and ran the executable file, install.sh, with the Autorun program.  It took me through a few menu items, and successfully installed in a couple minutes.

---

### Post by HannuMR on 2011-07-02
Thanks Krallus, mjones41 and lastwordsmith, and sorry guys in Canon.
This is defenetly my first and last Canon-printer.
Next one is only HP. 
It works with Linux without this kind of...

---

### Post by engrin on 2011-07-21
I've been searching and searching for solution to this problem and I finally found this thread. I tried installing the recommended 64 bit debs but nothing happens when I use the "autorun" to open in the install.sh Any suggestions? :confused:

---

### Post by Krallus on 2011-07-25
> **engrin said:**
> I've been searching and searching for solution to this problem and I finally found this thread. I tried installing the recommended 64 bit debs but nothing happens when I use the "autorun" to open in the install.sh Any suggestions? :confused:

It's been quite a while since I installed this, so don't hate me if what I'm about to tell you doesn't work.


Click Applications=>Accessories=>Terminal to open a command line shell.

If, let's say, you extracted the package to the folder "Downloads/pixma-mp250/cnijfilter-mp250series-3.40-1-deb/cnijfilter-mp250series-3.40-1-deb", then type at the command line (not the '$'.. I'm just using that to show that it's a command line command):

[FONT="System"]$ cd Downloads/pixma-mp250/cnijfilter-mp250series-3.40-1-deb/cnijfilter-mp250series-3.40-1-deb[/FONT]

now type:

[FONT="System"]$ sudo ./install.sh[/FONT]

you'll be prompted for the root password.

I think that should work.

Regards.

---

### Post by engrin on 2011-07-25
Thanks for the help Krallus but it didn't work. Does the printer need to be hooked up with the computer when I run the package? Also, is there a way to see what drivers I already have and delete them. I've been searching around and installing different packages :(
[IMG]http://img51.imageshack.us/img51/7427/screenshot3rh.png[/IMG]

---

### Post by Krallus on 2011-07-28
Engrin, can you elaborate, please?  Do you get an error message when you run install.sh?  If so, what message?  If not and it seems to install without any problem, then when you try in print something, what is in your list of available printers?  What happens when you try to print with MP250?  Error message?

---

### Post by engrin on 2011-07-28
This is what the terminal says...
steve@steve-Dell-System-Vostro-3450:~$ cd Downloads/cnijfilter-mp250series-3.40-1-deb
steve@steve-Dell-System-Vostro-3450:~/Downloads/cnijfilter-mp250series-3.40-1-deb$ sudo ./install.sh
[sudo] password for steve: 
==================================================

Canon Inkjet Printer Driver Ver.3.40-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
**An error occurred. The package management system cannot be identified.**
steve@steve-Dell-System-Vostro-3450:~/Downloads/cnijfilter-mp250series-3.40-1-deb$ ^C
steve@steve-Dell-System-Vostro-3450:~/Downloads/cnijfilter-mp250series-3.40-1-deb$ ^C
steve@steve-Dell-System-Vostro-3450:~/Downloads/cnijfilter-mp250series-3.40-1-deb$

---

### Post by engrin on 2011-07-28
When I plug the MP250 in, Ubuntu starts searching for drivers because it is not installed.

---

### Post by Krallus on 2011-07-30
Engrin, sorry but I just don't know without putting a lot of time into experimenting.  Are you using Ubuntu 10.04 LTS (System=>About Ubuntu)?  The documentation for the driver specifically states that it requires "Ubuntu 10.04(32bit/64bit)".  A different style package (RPM a la Red Hat) can be found here: [http://support-au.canon.com.au/contents/AU/EN/0100235401.html](http://support-au.canon.com.au/contents/AU/EN/0100235401.html) .  If that doesn't work you can try making the driver from source which can be found here: [http://support-au.canon.com.au/contents/AU/EN/0100302002.html](http://support-au.canon.com.au/contents/AU/EN/0100302002.html) .  Building from source is often the best bet when pre-built packages don't work.  Good luck!

---

### Post by engrin on 2011-07-31
> **Krallus said:**
> Engrin, sorry but I just don't know without putting a lot of time into experimenting.  Are you using Ubuntu 10.04 LTS (System=>About Ubuntu)?  The documentation for the driver specifically states that it requires "Ubuntu 10.04(32bit/64bit)".  A different style package (RPM a la Red Hat) can be found here: [http://support-au.canon.com.au/contents/AU/EN/0100235401.html](http://support-au.canon.com.au/contents/AU/EN/0100235401.html) .  If that doesn't work you can try making the driver from source which can be found here: [http://support-au.canon.com.au/contents/AU/EN/0100302002.html](http://support-au.canon.com.au/contents/AU/EN/0100302002.html) .  Building from source is often the best bet when pre-built packages don't work.  Good luck!

Thanks for sticking in there with me! I am using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.

---

### Post by Krallus on 2011-08-02
> **engrin said:**
> Thanks for sticking in there with me! I am using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.

When I upgraded to Lucid Lynx, I made the decision to stick with LTS versions only.  So far, I think that was a good decision.  My guess (and only a guess) is that the difference in versions is the reason you're having problems.  If it were me (if I was running Natty Narwhal and having the problems you're having), I'd try building the driver from source.  Sometimes that's easy.  Other times, it gets to be tricky.

---

### Post by engrin on 2011-08-03
How do I build from source? I am a pretty basic user but I can follow a guide if there is one.

---

### Post by ParadoxBlue on 2011-08-04
> **Krallus said:**
> When I upgraded to Lucid Lynx, I made the decision to stick with LTS versions only.  So far, I think that was a good decision.  My guess (and only a guess) is that the difference in versions is the reason you're having problems.  If it were me (if I was running Natty Narwhal and having the problems you're having), I'd try building the driver from source.  Sometimes that's easy.  Other times, it gets to be tricky.
I got the MP250 working fine on 32bit 10.04 from info on this website: [http://ubuntica.com/pixma-mp250-on-ubuntu.html](http://ubuntica.com/pixma-mp250-on-ubuntu.html) but I haven't checked it out lately and not sure if any of the info pertains to 11.04. I saved all the files necessary for installation but I only have the 32bit stuff.
Have to agree about sticking to the LTS versions. I believe the next LTS will be 12.04. Natty is a lot different than the previous Ubuntu releases and as far as I'm concerned it's still a beta. Let the folks who enjoy being guinea pigs get the kinks worked out of it.  ;-)

---

### Post by demonipuch on 2011-08-04
> **engrin said:**
> This is what the terminal says...
steve@steve-Dell-System-Vostro-3450:~$ cd Downloads/cnijfilter-mp250series-3.40-1-deb
steve@steve-Dell-System-Vostro-3450:~/Downloads/cnijfilter-mp250series-3.40-1-deb$ sudo ./install.sh
[sudo] password for steve: 
==================================================

Canon Inkjet Printer Driver Ver.3.40-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
**An error occurred. The package management system cannot be identified.**
steve@steve-Dell-System-Vostro-3450:~/Downloads/cnijfilter-mp250series-3.40-1-deb$

Hello

The script returns this error when it can't choose which package management system to use between dpkg and rpm. You should remove the rpm package.

To remove rpm, run the following command :
```
dpkg -P alien rpm
```

And run the installation script again.

---

### Post by rapture79 on 2011-09-09
> **Krallus said:**
> Engrin, sorry but I just don't know without putting a lot of time into experimenting.  Are you using Ubuntu 10.04 LTS (System=>About Ubuntu)?  The documentation for the driver specifically states that it requires "Ubuntu 10.04(32bit/64bit)".  A different style package (RPM a la Red Hat) can be found here: [http://support-au.canon.com.au/contents/AU/EN/0100235401.html](http://support-au.canon.com.au/contents/AU/EN/0100235401.html) .  If that doesn't work you can try making the driver from source which can be found here: [http://support-au.canon.com.au/contents/AU/EN/0100302002.html](http://support-au.canon.com.au/contents/AU/EN/0100302002.html) .  Building from source is often the best bet when pre-built packages don't work.  Good luck!



My thoughts, and this is only what I'm thinking, is.........if the drivers work in and older version, then why not back up your files, install the older version, add the drivers, then let the auto updates do there magic to upgrade to the newest version.  I mean in theory it should keep the drivers and update ubuntu to the version that you want.  I have the same printer, and I have tried to add the drivers using terminal as a was instructed to do so, but I can't use terminal worth crap...LOL.   If someone would take the time to place these drivers on a disk just to use with linux and ubuntu, I would pay the money to buy it, or even have an UPDATE or PLACE THEM IN THE SOFTWARE CENTER to make life easier.  I am now using ubuntu, Zorin(another Linux OS), and windows.  I only use the windows os for the printer, since after using linux os' windows just seems suck.  I would welcome any thoughts or idea anyone has. Thanks!!:)

---

### Post by pe7er on 2011-09-15
> **alf21 said:**
> I have the same problem ... printer works now after installing drivers, scanner doesn't work!

I was able to get the scanner of MP 250 working with on Ubuntu 10.10 (32 bit) using SANE (Scanner Access Now Easy): [http://www.sane-project.org/](http://www.sane-project.org/)

And I got the printer working using the instruction from [http://ubuntuforums.org/showpost.php?p=10539616&postcount=4](http://ubuntuforums.org/showpost.php?p=10539616&postcount=4)

---

