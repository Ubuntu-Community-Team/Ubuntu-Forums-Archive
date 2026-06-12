---
title: "Epson V500 Scanner"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by ukulele_ninja on 2007-12-26
Hi all, its been a while but im thinking about coming back to Ubuntu but I had a few questions. I have a big photo project I will be starting soon and need to use my new Epson V500 photo scanner, but wanted to see if it was possible to get it functioning properly in Ubuntu. Any help would be great!

---

### Post by icheyne on 2007-12-26
It doesn't look good.

[http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/359e83e2829694a7](http://groups.google.com/group/alt.os.linux.suse/browse_thread/thread/359e83e2829694a7)

Report your experiences here:
[https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson)

---

### Post by drbusch on 2007-12-28
Take a look at vuescan- I haven't used it with this scanner, but the v500 is on the supported list.

---

### Post by ArtInvent on 2008-04-27
I've just bought the Epson V500 and am doing a slide scan right now in Gutsy. Actually there's good news/bad news. If you need dust removal, there's still no good Linux solution as VueScan Linux doesn't seem to support transparency scans with this hardware due to some bug. However, both VueScan and Epson Scan work just fine in Virtual Box/XP. Frankly, I prefer Epson scan as it's exposure/color controls make a little more sense.

Ubuntu did not recognize the scanner out of the box. Fortunately, Epson actually have a website where you can download Linux drivers and a basic scanning program they provide called iscan. There are no Ubuntu specific packages, and selecting Debian as your OS provides no deb packages. There's only rpm's and source. You can use the rpm's and make deb's out of them. It's about the same procedure to install as for the previous version of this scanner, the Perfection 4490. I found the procedure in the forum archives and am updating/reprinting it below.

Basically it took me half an hour to figure this out and get the packages installed, and now I've just scanned my first slide. The iscan utility is a rather rudimentary scan program and not at all the equal of the Epson Windows software. Controls are extremely basic and you can't use Digital ICE dust removal capability. That said, it gives quality results and is fairly fast, and I'm scanning mostly Kodachrome anyway; you can't really use dust removal with Kodachrome slides.

I've used the non-Free VueScan just fine with earlier Epson scanner to do slides. proprietary package and it looks like there's a bug with it's transparency scanning with the V500. The preview is extremely under-exposed and the actual scans have all kinds of problems. 

As I said, I installed the Epson driver and software discs just fine in VirtualBox. Vuescan also works well in VirtualBox with none of the slide screwups of the Linux version. 



Anyway, this looks to be a good buy for scanning slides at $200 direct from Epson, and Epson is to be commended for their Linux support and porting a driver and software to Linux. If only they would port their excellent scan software completely to Linux. It would also be nice if Sane supported IR channel dust removal.


Here is an updated reprint of installing the driver. It went virtually just as described for me:

*********************

EPSON V500 SCANNER - DRIVER & SOFTWARE INSTALL

Step 1.  From the Ubuntu repositories for your version, install sane and 
related packages (libsane, libsane-extras, sane, sane-utils, xsane, 
xsane-common, quiteinsane) All of these may not be strictly required, but I 
do not know which ones are and which are not. That is just a list of what I 
have installed. 

Step 2. Connect and power up the scanner. Wait 60 seconds for the scanner to 
warm up -- this seems to be important as it won't report it's presence until 
it is ready. (I think the V500 is actually pretty fast to warm up.)

Step 3. make sure the scanner is detected. In a terminal window run:

sane-find-scanner

it should report :

found USB scanner (vendor=0x04b8 [EPSON], product=0x0130 [EPSON Scanner]) at libusb:001:006


or, run (also from a terminal window)

scanimage -L

and it should report finding an Epson Perfection V500 flatbed scanner 

The libsub address will probably be different depending on which port you have 
connected the scanner. If sane-find-scanner or scanimage -L do not find a 
scanner at all, stop. You have to solve that problem first. (Can't help there.)

Step 4. Get the V500 linux package from the Epkowa site: 

[http://www.avasys.jp/english/](http://www.avasys.jp/english/) 

There is a Linux Driver link there.

Answer their questionnaire. Select Perfection V500 Photo. I told them I was 
using Debian and selected "other" in the version dialog. Clicking on 
the "next" button will take you to a download page 

Step 5. The source code tarball will not build on Edgy or Feisty, so take the 
two .rpm files (you need both the iScan and the driver package) from the 
appropriate GCC version section for your distro. For Edgy or Feisty [or Gutsy] the GCC 3.4 files work.  

step 6. If you haven't already done so, install alien from repository to 
convert the .rpm files to .deb. (sudo apt-get install alien). 

Step 7. Convert the .rpm files.  In a terminal window change to the directory 
where the two downloaded driver files are located then (change these lines to reflect actual version numbers of drivers): 

sudo alien iscan-2.11.0-1.c2.i386.rpm 
sudo alien  iscan-plugin-gt-x770-2.1.0-0.c2.i386.rpm

This should produce the two .deb packages:

iscan_2.11.0-2_i386.deb 
iscan-plugin-gt-x770_2.1.0-1_i386.deb

Ignore any errors that you may see here. 

Step 8. Install the two .deb packages from a terminal window with dpkg, doing 
the main iscan package first.

sudo dpkg -i iscan_2.11.0-2_i386.deb
sudo dpkg -i iscan-plugin-gt-x770_2.1.0-1_i386.deb

Step 8a.

The main iscan package will likely not install cleanly, reporting file 
conflicts with certain sane-related packages previously installed, just go 
ahead and force dpkg to overwrite.

sudo dpkg -i --force-overwrite iscan_2.5.0-0.c2.i386.deb

The plugin should install with no conflict.

This completes the installation. To test things out make sure the scanner is 
powered up and connected and then type 

iscan

from a terminal, It should start and identify the scanner. I find the V500 to be ready to go pretty much immediately.

Once iscan is installed, the xsane and quiteinsane front-ends also should find 
and control the scanner.

---

