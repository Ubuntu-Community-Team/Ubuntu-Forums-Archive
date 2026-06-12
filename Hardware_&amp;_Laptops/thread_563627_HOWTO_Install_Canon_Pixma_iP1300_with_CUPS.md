---
title: "HOWTO: Install Canon Pixma iP1300 with CUPS"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by age6racer on 2007-09-30
**Credit:** This is a translated version of [Reinaldo's post]("http://forums.linux-foundation.org/read.php?25,1032") on the openprinting forums. All credit goes to Reinaldo 

**Prerequisites:** You will need to have alien installed to convert the .rpm's into .debs for installation in Ubuntu.

Step 1:
Follow this [link]("http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz")
and download the archive from Canon's website.

Step 2:
Unpack the archive
$tar -xf iP2200_Linux_260.tar.gz

Step 3:
Delete an unwanted .rpm
$rm cnijfilter-common-2.60-1.src.rpm

Step 4:
Convert the remaining rpm's into .deb's
$sudo alien -d -c *.rpm

Step 4: 
Install the .deb files
$sudo dpkg -i *.deb

Step 5:
Install libgtk1.2
$sudo apt-get install libgtk1.2

Step 6:
Create symbolic links
$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.3
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

Step 7: (optional)
Configure the iP2200 ppd file
$sudo gedit /usr/share/cups/model/canonip2200.ppd (default config works fine @ 600dpi)

Make your choices as to which detail level you require.

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQuality

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution 

Step 8:
Restart CUPS

$sudo killall cupsd
$sudo cupsd

Step 9:
Add your new printer

Open printing dialog in system settings
Add new printer
Choose Canon IP1300 USB # entry
When asked choose to manually choosea PPD file
browse to /usr/share/cups/model/canonip2200.ppd
Apply all settings and close wizard.

Step 10:
Print a test page! Your Canon Pixma iP1300 should be working at long last!!

Happy printing!

---

### Post by por100pre1 on 2007-10-01
This should be in Tutorials & Tips, good job. :)

---

### Post by burakerenn on 2007-10-04
Any way to make the prints greyscale (using only black cartridge) instead of RGB??

---

### Post by FkJ on 2007-11-03
It doesn't works, printer only spits the paper in blank

---

### Post by goodrench on 2007-11-05
> **FkJ said:**
> It doesn't works, printer only spits the paper in blank

Same here.
Any suggestions?

---

### Post by ReiSei on 2007-11-10
I installed the Kubuntu gusty now and this driver also and I functioned perfectly for me.:lolflag:
You need two cartridges for work - black and color. 
you need install libgtk1.2 and fixes dependences.
Follow the instructions above and see images below for setup the printer.
[ATTACH]49713[/ATTACH]

[ATTACH]49714[/ATTACH]

[ATTACH]49715[/ATTACH]

[ATTACH]49716[/ATTACH]

[ATTACH]49717[/ATTACH]

Following all the steps you will have success.
Sorry my bad english.

---

### Post by Tavathlon on 2007-12-26
Hi all!  I just posted a message in this thread: [http://ubuntuforums.org/showthread.php?p=4017815](http://ubuntuforums.org/showthread.php?p=4017815)
Just want to make sure that people using the iP1300 printer will see that message, so that is why I'm posting here as well.  =)

Please take a look, and help me if you are able to.  =)

Btw, great howto, printing as such is no problem after following this guide - thanks a lot!

Best regards
Patrik

---

### Post by mandras on 2008-05-21
Hi, thank you very much! For me it works fine. I've just got a test page with fresh ink!!!:)
For those who haven't been successful: I read somewhere that although with windows the printer works with only 1 cartridge (the color one) to use it on Linux you have to install both cartridges. My printer also has a black cartridge installed. So I suggest you try again with this howto after you have both cartridges installed, maybe that will solve the problem. At least it worked for me, I hope it'll work for you as well.
Thank you again!

---

### Post by dnile on 2008-06-20
wow!! Thanks very much works fine first try!  cheers.

---

