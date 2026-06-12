---
title: "Trying to install Canon Pixma MP620, help!"
date: 2009-01-10
forum: Hardware
---

### Post by Ubu4moi on 2009-01-10
Hello, anyone know how to install Canon Pixma MP620 on Ubuntu 8.04? This printer is not listed on the OS supported devices. I installed a generic driver but that didn't work.

---

### Post by buccaneere on 2009-01-10
[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

Might be some info here.

---

### Post by jaypmcwilliams on 2009-06-15
OK, got printer to work in Ubuntu Intrepid AMD64 (8.10). Thanks to all the forums, I brought this together & got it to work; 

First, you need to grab the needed files from LINUX section @ canon's website. (Just do a google search on each file) 
cnijfilter-common_2.80-1_i386.deb, cnijfilter-mp610series_2.80-1_i386.deb, scangearmp-common_1.10-1_i386.deb, scangearmp-mp610series_1.10-1_i386.deb.....

Then: 

Then find & download this file: ppdMP620-630en-1.5

Use sudo nautilus goto /usr/lib , /usr/lib32 & /usr/lib64 & create folder bjlib & copy new PPD files there.

Following files from Canon support site for the MP610:
Use terminal:

COMMON:
* sudo dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb
* sudo dpkg --force-architecture -i cnijfilter-mp610series_2.80-1_i386.deb

SCANGEAR
* sudo dpkg --force-architecture -i scangearmp-common_1.10-1_i386.deb
* sudo dpkg --force-architecture -i scangearmp-mp610series_1.10-1_i386.deb


Now here's the important part, DELETE ANY previous canon printers. Then add new using USB (mine is USB#1). Next, DO NOT USE PIXMA MP610!!!! Use "Canon MP610 series Ver.2.80". Then go into the printer settings under options / paper feed choose something like cassette or rear tray. I have not used paper feed switch yet so pls let me know.

Sorry about leaving out the direct links but they keep changing them. This works on AMD64 & i386.

Jay

---

### Post by imyth on 2009-06-17
Thanks jaypmcwilliams, your post helped me get my printer working. Have you tried printing photos? whats the best program for printing boarderless photos?

---

### Post by imyth on 2009-06-17
I was wondering if anyone out there has gotten the scanner to work with Ubuntu, honestly I haven't put that much time into it because the canon can scan to a usb stick or sd card which i can then read over the network. I still want to know what other people's experiences have been scanning and if anyone has used the scanner over the network.

Thanks
Imyth

---

### Post by thedlw on 2009-07-12
Also for those who want wireless.  I went to sourceforge and installed cups-bjnp
But first i had to do sudo apt-get install libcupsys2-dev and everything that came with it.

From there i had to manually build cups-bjnp 

Did a make install.  Then changed the usb printer location to.  

bjnp://192.168.1.47:8611 and poof worked great!

Now for scanner.  So far i've upgraded sane-backends to .20 (google sane and download latest

I've installed libusb-dev 

Mostly because if i can get the scanner working on USB then i'll try it on network.

But AFTER doing all this scanner works over the network.  so whatever they did in sane-backends everything is beautiful.  (using xsane)

Now i didn't play with color management so the quality isn't the best.  If someone can post and or pm me the best canon color management profiles i'll be happy to incorporate it here.

Also i can't make it load paper from the bottom tray.  (not a big deal) just would be nicer looking then the rear tray.

---

### Post by jaypmcwilliams on 2009-07-31
> **imyth said:**
> Thanks jaypmcwilliams, your post helped me get my printer working. Have you tried printing photos? whats the best program for printing boarderless photos?

YES. it's nice.

---

### Post by andrewbrown22 on 2009-07-31
> **thedlw said:**
> 
bjnp://192.168.1.47:8611 and poof worked great!


Is that port number (8611) standard across the board for this printer or was that just for your case? 

I'm having a hell of a time getting this to work. I hit print and the printer's screen lights up and says "Printing from PC" but still does nothing. On the computer end, it says the job was completed correctly. 

Any ideas as to why it would be doing that?

---

### Post by andrewbrown22 on 2009-07-31
I guess my question is in what order do you install all of these drivers (common, ij, bjnp), etc and copy over the ppd file, because whatever I've tried hasn't quite done the trick yet...

---

### Post by thedlw on 2009-08-01
You have to load paper from the back and specify it in your config sheet.

Otherwise thats all it does.  It will say processing but never print.

---

### Post by kaj on 2009-08-18
I have bought a Canon MP540, and I have the same problem as discribed here. I can't get the scanner to work.

I have downloaded and installed the factory drivers, and the printer works fine. But the scanner isn't recognized al all. In fact, the Canon MP540 is recognized as a usb-disk.

As recommended above, I have visited sane's website, and it seemes, that my scanner should work well with the same software, as other Canon MPxxx scanners. It is stated, that the backend version 0.16 should be used, but it is not possible to download anything newer than version 0.13 dated as far back as 2007.

Is there anything, I can do to get my scanner working?

Kaj Rasmussen
Denmark

---

### Post by thedlw on 2009-10-31
None of this works on Karmic.  Currently playing around.

---

### Post by skyh on 2009-11-04
> **thedlw said:**
> None of this works on Karmic.  Currently playing around.

I've been able to use my MP620 with Karmic by doing all of the standard steps -- installing cnij-common or whatever and the mp610 debs from the Canon site, along with installing cups-bjnp.

However, I haven't been able to get "bjnp" to return anything other than 

"Unknown" "Canon network printer"

Which means that Ubuntu can't discover the printer by itself. I can manually add a printer and use a method described earlier by getting the IP address of the printer and setting it's URI to

bjnp://IPaddress:8116

Then, after adding it, you can specify the PPD file.

Of course, I haven't gotten scanning to work, but at least printing will.

---

### Post by bsmith1051 on 2009-11-04
I was able to make the very most-basic print functions work using this,
[http://technicaltony.blogspot.com/2008/12/installing-canon-mp620-on-ubuntu.html](http://technicaltony.blogspot.com/2008/12/installing-canon-mp620-on-ubuntu.html)

But ever since the 9.04 > 9.10 upgrade I've lost the ability to print from the rear-tray (which is mandatory for 4x6 photo printing)

---

### Post by thedlw on 2009-11-22
I've gotten everything to work.  All though i don't use the rear tray so maybe i'll try.

What you need to do on a clean install is install this package

[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)

Then you'll be golden for all the other stuff from canon.

---

### Post by LequidMetal on 2009-11-24
heres a better method to install canon printers on Karmic .... 

[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

---

### Post by PeterB1945 on 2009-12-04
Have followed closely all the information in previous posts - thanks to everyone - and managed to get my MP620 printing from 8.10.

Then upgraded through 9.04 to 9.10. Of course didn't think to check the printer in 9.04, and then found to my dismay that it doesn't work in 9.10!

So far I've downloaded and installed all the .deb files:
cnijfilter-common_3.00-1_i386.deb
cnijfilter-mp610series_2.80-1_i386.deb
scangearmp-common_1.10-1_i386.deb
scangearmp-mp610series_1.10-1_i386.deb

downloaded and installed the files in:
ppdMP620-630en-1.5.tar.gz

and downloaded, configured and installed:
cups-bjnp-0.5.4.tar.gz
(Didn't carry out the re-direction from libcupssys2 to libcups2 per previous posting as I notice there is already a dummy libcupsys2 file to redirect to libcups2.)

bjnp reported the printer as:
network bjnp://192.168.0.3:8611 "Canon MP620 series" "Canon MP620 series 192.168.0.3" "MFG:Canon;CMD:BJL,BJRaster3,BSCCe,NCCe,PLI;SOJ:TXT01,BJNP2;MDL:MP620 series;CLS:PRINTER;DES:Canon MP620 series;VER:1.040;STA:10;HRI:EU;MSI:DAT,E3,HFSF;PDR:5;"

System>Administration>Printing found the printer at the above IP address and installed it OK.

Then comes the problem. When a page is sent to the printer, the printer reports 'processing', spits out a blank page, and goes back to 'ready' state.

That's what the printer reports.
The 'printer properties' window reports
Printer State: Processing - failed to read backchannel data:Success
and stays that way until the cows come home.

Can anyone tell me what I've done wrong and, more importantly, how to get the printer working?

Thanks in anticipation,
Peter.

---

### Post by Sendervictorius on 2009-12-17
All of this works on Karmic - I had no problems once I found this post. Thanks for the help.

> 64bit Karmic, usb, wireless and sane. I set my MP620 using windows to configure the wifi settings

---

### Post by jaypmcwilliams on 2010-01-14
> **jaypmcwilliams said:**
> OK, got printer to work in Ubuntu Intrepid AMD64 (8.10). Thanks to all the forums, I brought this together & got it to work; 

First, you need to grab the needed files from LINUX section @ canon's website. (Just do a google search on each file) 
cnijfilter-common_2.80-1_i386.deb, cnijfilter-mp610series_2.80-1_i386.deb, scangearmp-common_1.10-1_i386.deb, scangearmp-mp610series_1.10-1_i386.deb.....

Then: 

Then find & download this file: ppdMP620-630en-1.5

Use sudo nautilus goto /usr/lib , /usr/lib32 & /usr/lib64 & create folder bjlib & copy new PPD files there.

Following files from Canon support site for the MP610:
Use terminal:

COMMON:
* sudo dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb
* sudo dpkg --force-architecture -i cnijfilter-mp610series_2.80-1_i386.deb

SCANGEAR
* sudo dpkg --force-architecture -i scangearmp-common_1.10-1_i386.deb
* sudo dpkg --force-architecture -i scangearmp-mp610series_1.10-1_i386.deb


Now here's the important part, DELETE ANY previous canon printers. Then add new using USB (mine is USB#1). Next, DO NOT USE PIXMA MP610!!!! Use "Canon MP610 series Ver.2.80". Then go into the printer settings under options / paper feed choose something like cassette or rear tray. I have not used paper feed switch yet so pls let me know.

Sorry about leaving out the direct links but they keep changing them. This works on AMD64 & i386.

Jay

OK. After installing Ubuntu 9.10 Karmic AMD64, I had to tweak a few things to get this to work. I brought all this together here from others. "THANK YOU TO EVERYONE WHO FOUND & DEVELOPED THESE FILES." 

Download these first:
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download) 
[http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/) 
[http://support-au.canon.com.au/contents/AU/EN/0100083403.html](http://support-au.canon.com.au/contents/AU/EN/0100083403.html) 
[http://support-au.canon.com.au/contents/AU/EN/0100084001.html](http://support-au.canon.com.au/contents/AU/EN/0100084001.html) 

And download the bjlib file below. Extract all zipped files to your home directory. Now MAKE SURE TO UNPLUG PRINTER & REMOVE ALL CANON MP620 PRINTERS in printing!!!!! Then install libcupsys2. Then in the cups-bjnp open a terminal & run (without quotes) "make clean" "./configure" "make" "sudo make install". Then follow these instructions for the IJ Printer DEB's. 

# OK, got printer to work in Ubuntu Intrepid AMD64 (8.10). Thanks to all the forums, I brought this together & got it to work; 

# First, you need to grab the needed files from LINUX section @ canon's website. (Just do a google search on each file) 
# cnijfilter-common_2.80-1_i386.deb, cnijfilter-mp610series_2.80-1_i386.deb, scangearmp-common_1.10-1_i386.deb, scangearmp-mp610series_1.10-1_i386.deb.....

# Then: 

# Then find & download this file: ppdMP620-630en-1.5

# Use sudo nautilus goto /usr/lib , /usr/lib32 & /usr/lib64 & create folder bjlib & copy new PPD files there.

# Following files from Canon support site for the MP610:
# Use terminal:

# COMMON:
sudo dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb
sudo dpkg --force-architecture -i cnijfilter-mp610series_2.80-1_i386.deb

# SCANGEAR
sudo dpkg --force-architecture -i scangearmp-common_1.10-1_i386.deb
sudo dpkg --force-architecture -i scangearmp-mp610series_1.10-1_i386.deb

sudo cp canonmp620-630en.ppd /usr/share/ppd/
sudo cp canonmp620-630en.ppd /usr/lib/
sudo cp canonmp620-630en.ppd /usr/lib32/
sudo cp canonmp620-630en.ppd /usr/lib64/
sudo cp cifmp610.conf /usr/share/ppd/
sudo cp cifmp610.conf /usr/lib/
sudo cp cifmp610.conf /usr/lib32/
sudo cp cifmp610.conf /usr/lib64/


# Now here's the important part, DELETE ANY previous canon printers. Then add new using USB (mine is USB#1). 
# Next, DO NOT USE PIXMA MP610!!!! Use "Canon MP610 series Ver.2.80". Then go into the printer settings under 
# options / paper feed choose something like cassette or rear tray. I have not used paper feed switch yet so pls let me know.

# Sorry about leaving out the direct links but they keep changing them. This works on AMD64 & i386.

# Jay


Then VERIFY that the files exist in the locations stated above. If so, SHUTDOWN or RESTART your computer & Printer. Power On printer & computer. After both are FULLY up & running, plug in printer. If it doesn't automatically find the correct driver, locate it through PRINTING & follow instructions above for choosing correct driver.

Hope this helps because it is rambled, but here to help. Jay

---

### Post by rghv65c on 2010-09-17
Check out this site as it has detailed instructions on installing the MP620 on Ubuntu.  This worked for me.  Even scanning and wireless too.  

[http://bkintegration.com/?p=235 ]("http://bkintegration.com/?p=235")

Ubuntu 9.10 x86
Asus F8sn-B1 (laptop)

---

### Post by rghv65c on 2012-04-08
I know that this is an old thread though in case this helps anyone else.  there is a universal printer setup that works in all Debian based distributions. 

[http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/](http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/)

---

### Post by bobipod on 2012-07-21
This was very helpful, thank you to those who know more than me and who give their time up to create and share the knowledge.

---

