---
title: "[SOLVED] CUPS Server error"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by tropdoug on 2008-03-25
I am having an issue with my canon LBP3200 and Gutsy. Even though it is supposed to be able to install it directly when the printer is connected, and it does appear to be doing so, when I try to print a test page, this is the error I get.

CUPS SERVER ERROR

There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

Does anyone have an idea of how to rectify the issue?

Thanks in advance

Douglas

---

### Post by ranger_cole on 2008-05-07
I am having the same exact error messsage with 1320c Dell laser printer.  Cannot print. Please help.

---

### Post by miceagol on 2008-05-25
You mark the thread as solved, but do not post a solution? You should tell us how you solved it, tropdoug, so that other people might learn how to solve it.

---

### Post by tropdoug on 2008-05-25
yup your right sorry, I will try to go through the steps again and write the explanation here ASAP

---

### Post by tropdoug on 2008-06-05
[FONT=Arial][SIZE=2]After some confusion and wandering around many threads, I realised that this is both a common issue, and yet in the end a relatively easy issue to solve. 

From what I understand, the issue is caused not by the OS or by CUPS but by Canon requiring a particular driver available directly from it's site, and also requiring Ghostscript to be installed first. 

I can only speak for my laser printer, the Canon LBP 3200, however from the information on Canons own site, [http://software.canon-europe.com/products/0010044.asp](http://software.canon-europe.com/products/0010044.asp) it appears that this is across many of the laser printers of canons, and probably applies for all linux distros. 

Ok, first thing is visit the site, find your model and language and download the appropriate package for your distro. NOTE: Before you use this driver, you need to install Ghostscript which includes the common API. [COLOR=#0000ff].You can download from the following web site [http://opfc.sourceforge.jp/index.html.en](http://opfc.sourceforge.jp/index.html.en)[/COLOR] 

Personally I simply installed Ghostscript via Synaptic Package manager, a much simpler way of doing it. 

Below is an extract from Canons site showing the models and some other info I thought might be helpful.

```
Canon CAPT Printer Driver for Linux
 
This software is a CAPT printer driver that provides printing functions for Canon LBP printers operating under 
the CUPS (Common UNIX Printing System) environment, a printing system that operates on Linux
operating systems.

To use this software, please read the online manual before installing the driver.
 
 Version  1.60
 Released on   21-01-2007
 Description:
 Operation check has been made on: 
 Turbolinux 10 Desktop 
 Turbolinux 10 F... 
 Turbolinux 10 S 
 Turbolinux FUJI 
 Turbolinux Home 
 MIRACLE LINUX V3.0(Asianux Inside) 
 MIRACLE LINUX V4.0(Asianux Inside) 
 Red Hat9 
 Red Hat Professional Workstation 
 Red Hat Enterprise Linux V.4 
 Red Hat Enterprise Linux V.5 
 SUSE LINUX PROFESSIONAL 9.1 
 SUSE LINUX PROFESSIONAL 9.2 
 SUSE LINUX PROFESSIONAL 9.3 
 Novell Linux Desktop9 
 SUSE Linux 10.0(openSUSE) 
 SUSE Linux 10.1(openSUSE) 
 SUSE Linux 10.2(openSUSE) 
 Fedora Core 4 
 Fedora Core 5 
 Fedora Core 6 
 Fedora Core 7 
 Ubuntu 7.04 Desktop 
 Vine Linux 3.1/3.1CR 
 Debian GNU/Linux 3.1 rev2 
 Debian GNU/Linux 4.0 
  
[COLOR=#0000ff]Before you use this driver, you need to install Ghostscript which includes the common API.
Please install the Ghostscript before you install the driver.
You can download from the following web site[/COLOR]

[COLOR=#0000ff]http://opfc.sourceforge.jp/index.html.en[/COLOR]
 
Compatibility:
 Operating system(s):      Linux
 Language(s):                 English
 Downloads
 Below are the available downloads. Depending on the file, you may be asked to enter the serial number 
of the product. Please have it ready for your convenience.
 

 Software File size                _CAPTDRV160.tar._gz                 10311.21 Kb.
 Manual                                guide-capt-1.6xE.tar.gz            257.15 Kb.
 Installation instructions        LICENSE-captdrv-1.60E.txt       27.05 Kb.
                                             README-capt-1.6xE.txt             15.79 Kb.
 
 Supported product(s)
 
    i-SENSYS LBP-2900   
 i-SENSYS LBP3000   
 Laser Shot LBP-1120   
 Laser Shot LBP-1210   
 Laser Shot LBP2900   
 LaserShot LBP3000   
 Laser Shot LBP3300   
 LBP-3200   
 LBP5000   
 LBP5100   
 LBP5300  

```Having downloaded and installed Ghostscript I went to 

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

and followed the step by step process, very carefully. and it worked! 

within the tar from Canon is the installation guide as well, that you can navigate to, mine is at 

[/SIZE][/FONT][FONT=Arial][SIZE=2]/home/douglas/Downloaded-Programs/Canon lbp 3200 drivers/CAPTDRV160/doc/guide-capt-1.6xE/**manual_contents.html**[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial][SIZE=2]This guide is a very complete multi sectioned guide with a whole heap of information. 

Rather than re invent the wheel, which would probably be a little wobbly, if I was doing it, please just follow the above links and I think most of the cups server issues will be solved.

I hope this helps a little.
[/SIZE][/FONT]

---

### Post by giruzz on 2008-06-29
> **tropdoug said:**
> [FONT=Arial][SIZE=2]After some confusion and wandering around many threads, I realised that this is both a common issue, and yet in the end a relatively easy issue to solve. 

From what I understand, the issue is caused not by the OS or by CUPS but by Canon requiring a particular driver available directly from it's site, and also requiring Ghostscript to be installed first. 

I can only speak for my laser printer, the Canon LBP 3200, however from the information on Canons own site, [http://software.canon-europe.com/products/0010044.asp](http://software.canon-europe.com/products/0010044.asp) it appears that this is across many of the laser printers of canons, and probably applies for all linux distros. 

Ok, first thing is visit the site, find your model and language and download the appropriate package for your distro. NOTE: Before you use this driver, you need to install Ghostscript which includes the common API. [COLOR=#0000ff].You can download from the following web site [http://opfc.sourceforge.jp/index.html.en](http://opfc.sourceforge.jp/index.html.en)[/COLOR] 

Personally I simply installed Ghostscript via Synaptic Package manager, a much simpler way of doing it. 

Below is an extract from Canons site showing the models and some other info I thought might be helpful.

```
Canon CAPT Printer Driver for Linux
 
This software is a CAPT printer driver that provides printing functions for Canon LBP printers operating under 
the CUPS (Common UNIX Printing System) environment, a printing system that operates on Linux
operating systems.

To use this software, please read the online manual before installing the driver.
 
 Version  1.60
 Released on   21-01-2007
 Description:
 Operation check has been made on: 
 Turbolinux 10 Desktop 
 Turbolinux 10 F... 
 Turbolinux 10 S 
 Turbolinux FUJI 
 Turbolinux Home 
 MIRACLE LINUX V3.0(Asianux Inside) 
 MIRACLE LINUX V4.0(Asianux Inside) 
 Red Hat9 
 Red Hat Professional Workstation 
 Red Hat Enterprise Linux V.4 
 Red Hat Enterprise Linux V.5 
 SUSE LINUX PROFESSIONAL 9.1 
 SUSE LINUX PROFESSIONAL 9.2 
 SUSE LINUX PROFESSIONAL 9.3 
 Novell Linux Desktop9 
 SUSE Linux 10.0(openSUSE) 
 SUSE Linux 10.1(openSUSE) 
 SUSE Linux 10.2(openSUSE) 
 Fedora Core 4 
 Fedora Core 5 
 Fedora Core 6 
 Fedora Core 7 
 Ubuntu 7.04 Desktop 
 Vine Linux 3.1/3.1CR 
 Debian GNU/Linux 3.1 rev2 
 Debian GNU/Linux 4.0 
  
[COLOR=#0000ff]Before you use this driver, you need to install Ghostscript which includes the common API.
Please install the Ghostscript before you install the driver.
You can download from the following web site[/COLOR]

[COLOR=#0000ff]http://opfc.sourceforge.jp/index.html.en[/COLOR]
 
Compatibility:
 Operating system(s):      Linux
 Language(s):                 English
 Downloads
 Below are the available downloads. Depending on the file, you may be asked to enter the serial number 
of the product. Please have it ready for your convenience.
 

 Software File size                _CAPTDRV160.tar._gz                 10311.21 Kb.
 Manual                                guide-capt-1.6xE.tar.gz            257.15 Kb.
 Installation instructions        LICENSE-captdrv-1.60E.txt       27.05 Kb.
                                             README-capt-1.6xE.txt             15.79 Kb.
 
 Supported product(s)
 
    i-SENSYS LBP-2900   
 i-SENSYS LBP3000   
 Laser Shot LBP-1120   
 Laser Shot LBP-1210   
 Laser Shot LBP2900   
 LaserShot LBP3000   
 Laser Shot LBP3300   
 LBP-3200   
 LBP5000   
 LBP5100   
 LBP5300  

```Having downloaded and installed Ghostscript I went to 

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

and followed the step by step process, very carefully. and it worked! 

within the tar from Canon is the installation guide as well, that you can navigate to, mine is at 

[/SIZE][/FONT][FONT=Arial][SIZE=2]/home/douglas/Downloaded-Programs/Canon lbp 3200 drivers/CAPTDRV160/doc/guide-capt-1.6xE/**manual_contents.html**[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial][SIZE=2]This guide is a very complete multi sectioned guide with a whole heap of information. 

Rather than re invent the wheel, which would probably be a little wobbly, if I was doing it, please just follow the above links and I think most of the cups server issues will be solved.

I hope this helps a little.
[/SIZE][/FONT]

This doesn't work for me :-(

My printer was working flawless then an update broke-it

giruzz

---

