---
title: "[SOLVED] Brother MFC-5460CN Multi-function printer"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by Slingshot on 2008-02-19
I have been considering purchasing a _[Brother MFC-5460CN]("http://www.brother.com.au/Products/MFC_productoverview.asp?ProductID=238&SubCategoryID=1")_ printer as it meets my requirments of a multi-function printer with network and auto document feeder with Linux support. However, _[Openprinting]("http://openprinting.org/test/show_printer.cgi?recnum=Brother-MFC-5460CN")_ reported that its has problems with Ubuntu and is rated as partially working.

Can anyone give me some good/bad feed back for this printer with Ubuntu or their experiance with another distro and this printer? What does/dusnt work.

Thanks
SlingShot

---

### Post by linuxwizard on 2008-02-21
Since no one replied with any suggestions or input. Have you searched the forum for that printer to see if anyone has used that printer and had any issues or problems ? Imo with the info from Open Printing knowing that their are issues and is classified as partially works I would say to look for another printer. Look for one that is classified as perfectly or mostly works. Also HP printers are very well supported in Linux.

---

### Post by Slingshot on 2008-02-21
Hi Linuxwizard, yes, I did search through the forums and found scattered fragments but nothing leading to a working printer. Well, a local office supplier had a special on these for half price so I decided to buy one. Will hope for the best and maybe get to post my first "how-to" on the Ubuntu forums. \\:D/

SlingShot

---

### Post by Slingshot on 2008-03-08
Contrary to the Openprinting site this multi function printer works in Ubuntu. Further more, the setup could not be easier. Big thumbs up to Brother for producing low cost printers with excellent features and Linux support. =D>

My setup is 7.04 Feisty 32bit using a ethernet connection, however some section may apply to a USB installation. *I set a static IP address for the printer as the drivers could not locate it by name. Read the manual how-to set the static IP address on the printer*

**_TESTED_**
[LIST]
[*]Printing (via CUPS)
[*]Scanning (via Xsane - *Yucky* interface --- Anyone know of something better)
[/LIST]

**_NOT TESTED_**
[LIST]
[*]PC Faxing
[/LIST]



***_[SIZE="4"]PRINTING[/SIZE]_***

[LIST=1]
[*]Download the Brother LPR package [HERE]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc5460cnlpr-1.0.1-1.i386.deb&lang=English_lpr") and the CUPS wrapper [HERE]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/mfc5460cncupswrapper-1.0.1-1.i386.deb&lang=English_gpl"). Simply install using GDebi by double clicking the file.

[*]Go to the CUPS config. [http://localhost:631]("http://localhost:631")

[*]Select ***Printers***. Select ***Modify printer***. Enter a a location and name this is for human readable detail. Select Continue.

[*]Click on the drop down box and select the ***Brother MFC-5460CN XXX.XXX.XXX.XXX*** and select continue.

[*]Select ***Brother*** for make select continue.

[*]Select the ***Brother MFC-5460CN CUPS V1.1*** for the model and select ***Modify printer***. You can now print a test page from ***System > Administration > Printing***. Right click on the MFC5460CN print and select ***Print test page***.
[/LIST]
[B][I][U][SIZE="4"]
SCANNING[/SIZE][/U][/I][/B]

Download the Brother scan2 driver [HERE]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/64bit/brscan2-0.2.4-0.amd64.deb&lang=English_sane") and the scankey tool [HERE]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/s-keytool/brscan-skey-0.2.1-1.i386.deb&lang=English_lpr").

Download sane and Xsane by entering in a terminal ```
sudo apt-get install sane xsane

```
Install the Brother scanner driver. ```
sudo dpkg -i brscan2-0.2.4-0.i386.deb
```
Setup the scanner by using. ```
brsaneconfig2 -a name=BRSCANNER model=MFC-5460CN ip=xxx.xxx.xxx.xxx
```
The "-a name=BRSCANNER" is a friendly name, you can change it to whatever you like. Enter your IP address.

The scan-key tool allows you to register the computer to the printer and use the "Scan to" functions on the printer, you can install as follows.

```
sudo  dpkg -i brscan-skey-0.2.1-1.i386.deb
```

You can start the tool manually simple by typing 

```
brscan-skey
```

You can change the name of of the computer like this

```
brscan-skey -u {name}
```

You need to set it to start up at boot. Go to ***System > Preference > Sessions***. Select new. Enter ***Brother scan-key*** for the name and ***brscan-skey*** for the commend to execute.

---

### Post by mr_boo1711 on 2008-03-17
> **Slingshot said:**
> Contrary to the Openprinting site this multi function printer works in Ubuntu. Further more, the setup could not be easier. Big thumbs up to Brother for producing low cost printers with excellent features and Linux support. =D> 

I would just like to say a HUGE 'thank you' to you - simple, easy, and a breeze to sort thanks to the 'How-to'....

A+

;) \\:D/

---

### Post by Crasharo on 2008-06-24
Slingshot I followed your guide and found that my MFC-5460CN was not listed in the printer list, so could not continue. I tried a number of the other MFC drivers in the list but none worked.

I am running Ubuntu 8.04. Any suggestions?

---

### Post by Slingshot on 2008-07-02
> **Crasharo said:**
> Slingshot I followed your guide and found that my MFC-5460CN was not listed in the printer list, so could not continue. I tried a number of the other MFC drivers in the list but none worked.

I am running Ubuntu 8.04. Any suggestions?

Sorry Crasharo, have not had a chance to play around with 8.04 as yet. Check the brother site for a update on 8.04 drivers.

Little more detail would help to. 
1. Is your connection via USB or ethernet?
2. When you say it was not listed in the printer list are you referring to the CUPS list or Ubuntu printer manager?

---

### Post by phblomberg on 2008-07-02
With these changes I have it working in 8.04.

for PRINTING
If you go to System> Administration> Synaptic Package Manager.
Then search for "brother bh7" this will locate both the lpr drivers and the cups wrapper that worked for me in 8.04.
Use these files instead of those in step 1 of Printing section.

for SCANNING
The scan2 driver linked to an AMD64 package vs an i386 package.

The i386 scan2 file is [here]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.4-0.i386.deb&lang=English_sane").

Other than double-clicking the files I downloaded to install the scan2 and s-key packages I followed the rest of the procedure and my Hardy Laptop is printing and scanning beautifully.

---

### Post by Crasharo on 2008-07-03
phblomberg, thankyou so much for your response. It worked a treat. Will move onto the scanning now. Fingers crossed. Thanks also to Slingshot for responding.

Very happy now.

---

### Post by ericderace on 2008-07-03
.

---

