---
title: "Canon MX420"
date: 2014-05-04
forum: Hardware
---

### Post by linux.leep on 2014-05-04
Hi all. There is some stuff that needs to be fixed in my eyes. I have had issues in the past with Fedora missing packages and it drove me away from that distro back to this one. Ubuntu is normally well put together and I can resolve many issue by a simple Google. Well not this time. I had my Canon MX420 printer/scanner/fax working flawlessly in Fedora with a simple plug in and play. This seems not to be the case in Ubuntu 14.04.

I stumbed across several post about the same issue with Canon devices and decided to follow this one -> [http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mx-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/](http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mx-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/) . Was very straight forward and easy to follow. Except for the missing package from the Ubuntu repo. No big deal, I will just download it from the provided link. Nope, wrong again the link throws up a 404 error through wget. Ok, I will just visit the page through my browser, might have typed something wrong. NOPE file not found. Googled for some time and finally found a download for Ubuntu 13.10. Figured why not try and install it. Installed the package then I could install the recommended cnijfilter-mx420series package. 

Good, everything should work now. Let me try to run a test scan. NOPE just sits there like it did before. 

Why did this software work on under Fedora (the biggest package/repo mess known to man) just fine and not the Ubuntu 14.04? Why is the package libtiff4 not available from the Ubuntu repos? This printer is not a million years old or brand spankin' new. It should be a simple plug and play. 

Missing packages are a huge pain, especially when it is related to time sensitve work. This is what drove me away from Fedora. Missing packages and broken repos. PLEASE FOR THE LOVE OF GOD do not turn Ubuntu into this.

That being said does anyone have another way to download the file at [COLOR=#ff0000]ftp.us.debian.org/debian/pool/main/t/tiff3/libtiff4_3.9.7-3_i386.deb[/COLOR] since it has magically disappeared off the face of the earth?

---

### Post by pdc on 2014-05-05
sorry to hear of your distress; you sound very frustrated and extremely bothered; 

a post a couple of days talked about libtiff4 and getting it from the debian site [http://ubuntuforums.org/showthread.php?t=2220935&highlight=libtiff4](http://ubuntuforums.org/showthread.php?t=2220935&highlight=libtiff4)

the version of libtiff4 that I can find on the debian site [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) is definitely there: it is inside that tiff3 directory and is currently sitting at [COLOR="#0000FF"]libtiff4_3.9.6-11_i386.deb[/COLOR] that I can see: (thumbnail enclosed)

so you can click directly on the package you want; and gdebi installer will likely install it for you there and then 

(and then on to install the Canon package?)

best wishes
______

a lot of folks recommend the michael gruz site;

you can just download what you need; the Canon 420 series debian package driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100329702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100329702.html) as the cnijfilter-mx420series-3.50-1-deb.tar.gz and the 4 commands to install; as you may well know very well: are:
cd Downloads
tar -zxvf cnijfilter-mx420series-3.50-1-deb.tar.gz
cd cnijfilter-mx420series-3.50-1-deb
./install.sh

(scanner package from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100330702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100330702.html)

---

### Post by linux.leep on 2014-05-07
pdc thank you for your time and help. Also, I apologize for being aggravated. 

I used your links for libtiff4, cnijfilter-mx420series-3.50-1-deb.tar.gz (printer), and scangearmp-mx420series-1.70-1 (scanner). While trying to install I realized I had force installed some i386 and some older versions of Ubuntu files on my system (I am on amd64, part of my error in the first place). I removed all conflicting packages with "dpkg --purge" and some dependencies and blah blah. 

Ok now we are doing great. I install the libtiff4_3.9.6-11_amd64.deb without any issues. Then proceed to extract and install the cnijfilter-mx420series-1.70-1-deb.tar.gz. Excellent, it installs no problems and makes me choose a few options within the installer (usb, printer name, etc.). Installs and I print a test page.

While printing the test page, I notice that the auto-installed printer that ran when I plugged in the printer the first time was still there, removed it and printed another test page. SUCCESS! Now a warning pops up about updates that need to be downloaded (Ubuntu Software Updater, or what ever it is). Install them, suggest reboot, so I reboot. 

After reboot I turn on the printer and it installs the plug-n-play version of the printer again. The usb printer setup during the install process is still there. Print test again and still works. (Left auto-installed one this time. Made sure mine was checked as default.) Time to install the scanner software. Extract and install scangearmp-mx420series-1.70-1-deb.tar.gz. It installs fine (no errors thrown) and does not ask any options like in the previous installer. Run a test scan and it does not scan. Reboot, test, remove, reboot, re-install, test, reboot, test and I still get the same thing. 

It is very weird though, I am using simple scan and it notices the scanner. (When powered off it says error: no scanner connected) When I tell it to scan through the software my scanner wakes from sleep mode but just sits there. So I try from the scan buttons on the printer (both color and black & white) and still the same thing. It acts like it wants to do something but just hangs. 

Also I tried several times to use th Michael Gruz PPA that you suggested. It shows me his key info and installs fine but will not connect when I do a "sudo apt-get update". I get a 404 error every time. Tried hours and days apart. 

Any ideas on what or where I messed up? 
Any more info I can provide?

-Ubuntu GNOME (not Unity) 14.04 LTS amd64
-Canon MX420 copy/fax/scan/print ([Link to Canon site]("http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mx_series/pixma_mx420"))

---

### Post by pdc on 2014-05-08
well done to get the Canon driver installed; good it works well

so I think you have two printer drivers now installed; 

1) is probably a gutenprint driver; 
2) would be the Canon MX420 driver; in CUPS you can see the full name and description [http://localhost:631/printers/](http://localhost:631/printers/)     ...if you either click on the link to open a web page; or paste localhost:631/printers/ into a web page address at the top: you should see both and what they have been named

I guess you just choose which you wish to use; 

__________________________________

>  Run a test scan and it does not scan.

I am wondering how you did that: to run [COLOR="#0000FF"]ScanGearMP[/COLOR] that Canon supply you must start it from a terminal

> [COLOR="#FF0000"]scangearmp[/COLOR]

and after that you create a launcher ............to launch it ............. EDIT: you have gnome so you can create a launcher easily by right-clicking on the bottom panel.................

one way is > [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR]

then 

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]   ......opens a dialogue window: call it what you wish but the command must be > scangearmp

does that help?

---

### Post by linux.leep on 2014-05-08
Thank you again.

You are correct it is the gutenprint driver. It automatically re-installs after every reboot if I remove the gutenprint printer. So I will just leave it unless you know a way to disable it. I visited [http://localhost:631/printers](http://localhost:631/printers) (attached file = screen-1) to confirm. I also visited 'System Settings' -> 'Printers' and made sure that the MX420USB was my default printer.

I ran the test scan with a program called "Simple Scan" (attached file = screen-2) which is available through the default repos. It was what I have used in other flavors of Linux and was used to it. This ["ScanningHowTo"]("https://help.ubuntu.com/community/ScanningHowTo") through the Ubuntu Community Help Wiki is what made me search for it and use it in Ubuntu.

Today after reading your response I used in the Terminal:```
scangearmp
```
It successfully scanned and saved images. THANK YOU, you are a life saver! Also thank you for the tip on making the launcher for faster access.

Although I am very happy and thank you again, is there any way you know of to make the "Simple Scan" program work with the scanner? It has a nice function where I can scan multiple images and save them in a single .pdf file quickly and easily. It is just a program I am familiar with and would like to use. 

Once again, I cannot thank you enough for your help. Hope your week is going well, because you have turned my whole week around!

---

### Post by aikishugyo on 2014-05-08
Probably "simple scan" uses SANE as a backend, so you would need to install the development version of SANE where the MX420 series is supported (presumably it is not supported in the version shipped with Ubuntu). The SANE website has download instructions for obtaining the development (git) code, and the linux README file has specific instructions for Ubuntu. Also, the developer of the Canon backend has his own repo which you could try. For more info, see the SANE webpage and search the SANE mailing list archives (and take part if you ever want to help out as tester).
Regards,
Gernot Hassenpflug

---

### Post by pdc on 2014-05-09
thanks very much for your very kind comments; delighted to hear we have been able to help you; very good of you;

great that Gernot comes in at this stage; aka aikishugyo and hugely knowledgable on sane;

I just looked up the sane page, and it would seem [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) if one scrolls down to MX420 that it has [COLOR="#008000"]COMPLETE[/COLOR] support; I can't remember if you have posted the results of > [COLOR="#FF0000"]sane-find-scanner[/COLOR] and > [COLOR="#FF0000"]scanimage -L[/COLOR]

__________

Gernot may like to comment more but the standard version of sane .....*should* ..........identify your scanner.......... I have used xsane as the front-end for sane for us; I too had assumed simple-scan was a frontend for sane: yes, it is [https://apps.ubuntu.com/cat/applications/simple-scan/](https://apps.ubuntu.com/cat/applications/simple-scan/)

backend for the MX420 is listed as [COLOR="#0000FF"]pixma[/COLOR] [http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/) and man-page is [COLOR="#0000FF"]sane-pixma[/COLOR] [http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html) (and this again says MX420 is supported ...............)

---

