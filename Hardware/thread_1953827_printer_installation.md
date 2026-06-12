---
title: "printer installation"
date: 2012-04-07
forum: Hardware
---

### Post by Ozplanman on 2012-04-07
Hi,

Yes I'm new at this, sorry.  I've checked through some of the other messages named "printer installation" and became a bit lost with some of the concepts.  I come from a Windows environment and superusers and roots seem to have different meanings here.  I downloaded the two files - lpr and cupswrapper drivers for my Brother MFC6490cw printer and ran the    	 	 	 	 	 	   sudo aa-complain cupsd
   command which returned a command not found error
I tried the su command, entered a password (the only one I have) and authentication failed.

A bit lost as to what to do next.

My printer is wireless and networked.

I would appreciate any assistance.

Regards

Oz.

---

### Post by dandnsmith on 2012-04-08
I'm not clear about installing Brother printer drivers, but can comment that you're not expected to use the su command with ubuntu.
Instead you use 'sudo' command, and supply your own password to authenticate.
The basic intent for superusers and root is the same as Windows, but some of the detail differs (as does the structure of the filesystems), and you're bound to find differences as you move between OSs from different platforms.

---

### Post by dontquoteme on 2012-04-08
Ubuntu limits root access by default, which as a new user is one of the first sources of problems. 
**By default, the Root account password is locked in Ubuntu.** This means that you cannot login as Root directly or use the su command to become the Root user.

1. Several Root options.
sudo 
 If you ever need a quick way to "go root" I use sudo -s or sudo -i. 
I believe that sudo -s creates a root session as the user, while sudo -i creates a root session as the root user.
Source:
[http://askubuntu.com/questions/6676/why-is-there-no-option-to-login-as-root](http://askubuntu.com/questions/6676/why-is-there-no-option-to-login-as-root)

That should get you root access. :)

2. Brother specific install.
The good news is that Brothers' Linux support is the best I've found.

Presumed that you've got the latest drivers from the Brother site?
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6490CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-6490CW)

Brother's Linux drivers are very good.

Install notes from the Brother site are:
Step 1. Login as a superuser ( or use "sudo" option if it is required )   Step 2. Check if pre-required procedures are completed[**For openSUSE**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#001")[**For Debian/Ubuntu 64 bit**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004")[**For Ubuntu8.04/8.04.1, Ubuntu8.10, Ubuntu9.04**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002")[**For Fedora10, 11, 12 64 bit**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#007")[**For the following products**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#003")
DCP-1000, DCP-1400, DCP-8020, DCP-8025D, DCP-8040, DCP-8045D, DCP-8060, DCP-8065DN,  FAX-2850, FAX-2900, FAX-3800, FAX-4100, FAX-4750e, FAX-5750e,  HL-1030, HL-1230, HL-1240, HL-1250, HL-1270N, HL-1430, HL-1440, HL-1450,  HL-1470N, HL-1650, HL-1670N, HL-1850, HL-1870N, HL-5030, HL-5040, HL-5050, HL-5070N,  HL-5130, HL-5140, HL-5150D, HL-5170DN, HL-5240, HL-5250DN, HL-5270DN, HL-5280DW,  HL-6050, HL-6050D, MFC-4800, MFC-6800, MFC-8420, MFC-8440, MFC-8460N, MFC-8500,  MFC-8660DN, MFC-8820D, MFC-8840D, MFC-8860DN, MFC-8870DW, MFC-9030,  MFC-9070, MFC-9160, MFC-9180, MFC-9420CN, MFC-9660, MFC-9700, MFC-9760, MFC-9800, MFC-9860, MFC-9880[**For the following products**]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#005")
DCP-110C,  DCP-310CN, FAX-1815C, FAX-1820C, FAX-1835C, FAX-1840C, FAX-1920CN,  FAX-1940CN, FAX-2440C, MFC-210C, MFC-3220C, MFC-3240C, MFC-3320CN,  MFC-3340CN, MFC-3420C, MFC-3820CN, MFC-410CN, MFC-420CN, MFC-5440CN,  MFC-5840CN, MFC-620CN   Step 3. Download driversDownload LPR driver and cupswrapper driver.[Printer Driver download page]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html")   Step 4. Install LPR driver and cupswrapper driver4-1. Turn on the printer and connect the USB cable.4-2. Open the terminal and go to the directory where the drivers are.4-3. Install LPR driver.The install process may take some time. Please wait until it is complete.                   Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)         Command (for rpm)  :  rpm  -ihv  --nodeps  (lpr-drivername)     [Example(for dpkg)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#dpkg1") | [Example(for rpm)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#rpm1") 4-4. Install cupswrapper driver.The install process may take some time. Please wait until it is complete.  Command (for dpkg)  :  dpkg  -i  --force-all  (cupswrapper-drivername) Command (for rpm)  :  rpm  -ihv  --nodeps  (cupswrapper-drivername) [Example(for dpkg)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#dpkg2") | [Example(for rpm)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#rpm2") 4-5. Check if the LPR driver and cupswrapper driver are installed  Command (for dpkg)  :  dpkg  -l  |  grep  Brother Command (for rpm)  :  rpm  -qa  |  grep  -e  (lpr-drivername)  -e  (cupswrapper-drivername) [Example(for dpkg)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#dpkg3") | [Example(for rpm)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#rpm3")     Step 5a. (for USB Connection) Check your printer on the cups web interface5a-1. Open a web browser and go to **"http://localhost:631/printers"**.     Check if the Device URI of your printer is **"usb://Brother/(your printer's model name)"**      [Example of a USB printer entry]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#cwi_img1")If the device URI is different from the example above, please go to  "Modify Printer" of your printer to select proper device and driver.      If your printer is not listed on "http://localhost:631/printers", please go to **"http://localhost:631/admin"** and click "Add printer" and select proper device and driver.    Step 5b. (for Network Connection) Configure your printer on the cups web interface5b-1. Open a web browser and go to **"http://localhost:631/printers"**. 5b-2. Click "Modify Printer" and set following parameters.                    - "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect"              for Device               - lpd://(Your printer's IP address)/binary_p1              for Device URI               - Brother              for Make/Manufacturer Selection               - Your printer's name              for Model/Driver Selection                    [Example of a network printer entry]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#cwi_img2")    Step 6. Try a test print6-1. Open a text editor, write something and select "print" from the menu.

***
As an aside, my Brother printer works great with Ubuntu 10.10, 11.04 and 11.10  and I'm sure yours will too.  You've made a great choice buying a Brother printer. :)

Good luck! :)

---

