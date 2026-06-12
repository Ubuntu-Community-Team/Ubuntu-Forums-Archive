---
title: "Installing Brother Printer DCP-135C on Hardy Heron"
date: 2008-08-05
forum: Hardware
---

### Post by growingneeds on 2008-08-05
I recently performed a fresh install of Hardy Heron on my Dell Inspiron 640m. Hence, I had to re-install my printer. Coming from a Microsoft Windows background, this setup took me quite a while to figure out. The [Brother: Linux Driver Homepage]("http://solutions.brother.com/linux/en_us/index.html") did not help much in terms of the procedure. Their FAQ was confusing. But, they did provide the drivers that would actually work. Hardy Heron auto-detected the printer but the default driver could not print.
[LIST=1]
[*]From the [Brother Linux Driver Homepage]("http://solutions.brother.com/linux/en_us/index.html"), download the appropriate [LPR Printer Driver]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html") and [CUPS Printer Driver]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html"). Note that you should get the Debian package. These turned out to be [dcp135clpr-1.0.1-1.i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp135clpr-1.0.1-1.i386.deb") and [dcp135ccupswrapper-1.0.1-1.i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/dcp135ccupswrapper-1.0.1-1.i386.deb") respectively.

[*]In a terminal, type the following ```
sudo mkdir /usr/share/cups/model
sudo mkdir /var/spool/lpd/
sudo mkdir /var/spool/lpd/dcp135c
```These should be performed sequentially. (For some reason, the mkdir command can't seem to create nested directories.)


[*]Install the debian driver package for LPR Printer Driver.
[*]Install the debian driver package for CUPS Printer Driver.
[/LIST]
The Brother printer is now installed. The required ppd file will be installed in /usr/share/cups/model. For some odd reason, the /var/spool/lpd/dcp135c directory cannot be viewed. It claims that I am not the owner. The owner is "lp" and the group is "lp". I presume this to be  an issue with access rights.

---

### Post by kdb424 on 2008-08-05
> **growingneeds said:**
> The Brother printer is now installed. The required ppd file will be installed in /usr/share/cups/model. For some odd reason, the /var/spool/lpd/dcp135c directory cannot be viewed. It claims that I am not the owner. The owner is "lp" and the group is "lp". I presume this to be  an issue with access rights.

Just sudo up a file browser, or change the permissions by command line.

Thanks for the tutorial!

---

### Post by growingneeds on 2008-09-08
There is a better way to install the DCP-135C. Before connecting the printer, fire up Synaptic Package Manager and search for "Brother DCP-135C". Install the relevant drivers and turn on the printer.

---

### Post by Ron W on 2008-09-09
How do I 'Install the relevant drivers'?

---

### Post by Ron W on 2008-09-09
To answer my question above I did the following:-

**Installing Brother DCP-135C**

1) Making sure that the printer was turned off, I booted up the computer to Ubuntu 8.04

2) Opened &#8211; System->Administration->Synaptic Package Manager

2a) Entered my 'Administration' password

3) Did a search in the Synaptic Package Manager using &#8220;Brother DCP-135C&#8221; (nb. without the speech marks)

4) Clicked on the software required
	(in this instance there was two packages showing, but when I 'marked' of them, the other also became marked)

5) When the software was installed, I turned off the computer

6) I turned on the printer before rebooting the computer

7) Opened &#8211; System->Administration->Printing

8) Clicked &#8220;New Printer&#8221; button

9) Clicked &#8220;Brother DCP-135C USB # 1&#8221;

10) Clicked &#8220;Forward&#8221; and followed the instructions

11) When I finished 10) I clicked on the &#8220;Test&#8221; button to get a test print out

12) Made the Brother DCP-135C the default printer

13) Tested a print out using a document through Open Office


I hope this is of some use.

---

### Post by Myglaren on 2009-02-07
> **growingneeds said:**
> There is a better way to install the DCP-135C. Before connecting the printer, fire up Synaptic Package Manager and search for "Brother DCP-135C". Install the relevant drivers and turn on the printer.

Excellent info, took all of three minutes start to printed test page.
Thanks.

---

### Post by growingneeds on 2009-08-05
An update. This will be cleaner, clearer and fresher. Follow this sequentially. :D

[LIST=1]
[*]**Download the LPR driver.** This may be found at [http://solutions.brother.com/linux/en_us/download_prn.html](http://solutions.brother.com/linux/en_us/download_prn.html). Obtain the Debian package. My file was named dcp135clpr-1.0.1-1.i386.deb.
[*]**Install the LPR driver.** ```
sudo mkdir /var/spool/lpd/
sudo mkdir /var/spool/lpd/dcp135c
```
Double-click on dcp135clpr-1.0.1-1.i386.deb. Or, ```
sudo dpkg -i dcp135clpr-1.0.1-1.i386.deb
``` Note that for this Debian package to install properly via terminal, it has to be placed in the Home Folder.
[*]**Download the CUPSWRAPPER driver.** This, again, may be found at [http://solutions.brother.com/linux/en_us/download_prn.html](http://solutions.brother.com/linux/en_us/download_prn.html). My file was named dcp135ccupswrapper-1.0.1-1.i386.deb.
[*]**Install the CUPSWRAPPER driver.** ```
sudo mkdir /usr/share/cups/model
```
Double-click on dcp135ccupswrapper-1.0.1-1.i386.deb. Or, ```
sudo dpkg -i dcp135ccupswrapper-1.0.1-1.i386.deb
```
[/LIST]

The Brother printer DCP-135C is now installed. Just make sure that it is set as the default printer. I had tried to use the drivers provided by ubuntu in the repositories: "brother-lpr-drivers-extra" and "brother-cups-wrapper-extra". But the printouts were all displaced upwards, truncating my documents at the top and leaving lots of white space at the bottom. This was just unacceptable. So, I went back to the drivers kindly provided by Brother. This is an install on Jaunty Jackalope (ubuntu 9.04).

---

### Post by KlaymenDK on 2012-02-02
> **growingneeds said:**
> I recently performed a fresh install of Hardy Heron on my Dell Inspiron 640m. Hence, I had to re-install my printer. Coming from a Microsoft Windows background, this setup took me quite a while to figure out. The [Brother: Linux Driver Homepage]("http://solutions.brother.com/linux/en_us/index.html") did not help much in terms of the procedure. Their FAQ was confusing. But, they did provide the drivers that would actually work. Hardy Heron auto-detected the printer but the default driver could not print.
[LIST=1]
[*]From the [Brother Linux Driver Homepage]("http://solutions.brother.com/linux/en_us/index.html"), download the appropriate [LPR Printer Driver]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html") and [CUPS Printer Driver]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html"). Note that you should get the Debian package. These turned out to be [dcp135clpr-1.0.1-1.i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp135clpr-1.0.1-1.i386.deb") and [dcp135ccupswrapper-1.0.1-1.i386.deb]("http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/dcp135ccupswrapper-1.0.1-1.i386.deb") respectively.
[*]In a terminal, type the following ```
sudo mkdir /usr/share/cups/model
sudo mkdir /var/spool/lpd/
sudo mkdir /var/spool/lpd/dcp135c
```These should be performed sequentially. (For some reason, the mkdir command can't seem to create nested directories.)
[*]Install the debian driver package for LPR Printer Driver.
[*]Install the debian driver package for CUPS Printer Driver.
[/LIST]
The Brother printer is now installed. The required ppd file will be installed in /usr/share/cups/model. For some odd reason, the /var/spool/lpd/dcp135c directory cannot be viewed. It claims that I am not the owner. The owner is "lp" and the group is "lp". I presume this to be  an issue with access rights.

I just registered to say that this (ancient, sorry for grave digging) post works flawlessly on Linux Mint 11 LXDE. An hour ago I was almost convinced this 135C was a paperweight.

---

### Post by anthony2010 on 2013-03-04
Hi all.

Well Ive done all the above and have a printer that prints. However the positioning is all wrong. I'm trying to print business cards on decadry sheets but the print out is all over the place.

Can it be adjusted? Im in the UK and we use A4 sheets - which the printer is set up for but none the less its not printing things the way they are set out on the screen. Including text in Libre office (It crops the top line)

Thanks in advance for any and all advice!

Anthony

Ubuntu 12:10

---

### Post by QIII on 2013-03-04
Hello.

Everyone's questions and answers are valuable.

However, this is a very old thread.  If there has been no activity in a thread for a year or so, it is best to start a new one.

Please feel free to reference this thread in any new one you start.

Thanks!

---

