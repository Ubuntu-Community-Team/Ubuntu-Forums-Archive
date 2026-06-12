---
title: "driver for canon pixma mp280 printer"
date: 2010-09-26
forum: Hardware
---

### Post by eMcJagger on 2010-09-26
Hello,

I just got a canon pixma mp280 printer, foolishly forgetting to check whether it was compatible with my ubuntu 10.04/hp pavillion HDX 18 setup.  When I open system > administration > printing, I see drivers available pixma mp220 and pixma mp500, but not mp280.  Does anyone know whether this is available, or if/when it will be, or whether there's another way to get my printer working?

Thanks!

Jeremy.

---

### Post by vicshrike on 2010-09-26
not sure, but maybe this can be of help...
[http://support-nz.canon.co.nz/contents/NZ/EN/0100301402.html](http://support-nz.canon.co.nz/contents/NZ/EN/0100301402.html)

---

### Post by eMcJagger on 2010-09-30
Worked like a charm right out of the box, much thanks!

---

### Post by Andrew Tabs on 2010-11-14
I bought the same printer.  Can't seem to get the scanner function to work.  I get 'no device found' error message from xsane and Gimp.  Did you have this problem or is it just me?

---

### Post by kafkaian on 2010-11-15
I've given up with printing on Ubuntu. I have a Canon Pixma. The colours have always been muddy and dark, and more often than not, it just doesn't print/print properly.

So, I've moved away from Ubuntu - they just can't get printing right IMO.

---

### Post by IcarusR on 2010-11-15
kafkaian

> So, I've moved away from Ubuntu - they just can't get printing right IMO. 

People should stop blaming Ubuntu for everything that does not work quite as well as it does in Windows.
Ubuntu is produced by Canonical, who build this distro from software written by others under the gpl licence.
Canonical do not write drivers for hardware. If the manufacturers do not produce linux drivers or release the specs of their hardware, then it is down to someone to reverse engineer the windows driver & create some sort of linux driver.
Linux is written by people with an interest in it for people with an interest & understanding to use.
Linux is a FREE os, Windows is not.

This article may help you understand things better....

[http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by pierre5933 on 2010-12-08
> **eMcJagger said:**
> Worked like a charm right out of the box, much thanks!

I would buy this machine (pixma mp280) ,

 Before I HAVE MADE SOME TRIALS WITH  IT , and the machine did not start , especialy the scaner was not recognize , perphaps I Made a mistake , can eMcJagger confirm that it runs correctly as printer or saner without anything more done than the 4 deb package (2 for scaner and 2 for printer) 

Thanks

Pierre

---

### Post by dhayfule on 2010-12-09
The driver is officially released by cannon

Printer driver : [http://support-in.canon-asia.com/contents/IN/EN/0100301402.html](http://support-in.canon-asia.com/contents/IN/EN/0100301402.html)
extract the archive and find the dep packages in the extracted folder... install the deb file that has "common" word in the name first, then the mp280 deb file

similarly download and install the scanner package

[http://support-in.canon-asia.com/contents/IN/EN/0100302702.html](http://support-in.canon-asia.com/contents/IN/EN/0100302702.html)

the same concept

Download the scanner instructions from here: [http://support-in.canon-asia.com/contents/IN/EN/0300410501.html](http://support-in.canon-asia.com/contents/IN/EN/0300410501.html)

---

### Post by pierre5933 on 2010-12-10
> **dhayfule said:**
> The driver is officially released by cannon

Printer driver : [http://support-in.canon-asia.com/contents/IN/EN/0100301402.html](http://support-in.canon-asia.com/contents/IN/EN/0100301402.html)
extract the archive and find the dep packages in the extracted folder... install the deb file that has "common" word in the name first, then the mp280 deb file

similarly download and install the scanner package

[http://support-in.canon-asia.com/contents/IN/EN/0100302702.html](http://support-in.canon-asia.com/contents/IN/EN/0100302702.html)

the same concept

Download the scanner instructions from here: [http://support-in.canon-asia.com/contents/IN/EN/0300410501.html](http://support-in.canon-asia.com/contents/IN/EN/0300410501.html)

   My question is not how to do it, BUT

        Is it realy ok or not twice printing and scaning??

Thanks

---

### Post by phl4tpw on 2011-01-03
Just used the above links for Printer drivers and ScanGear for MP280. Installed .debs and both printing and scanning work perfectly, colours are bright and the scanning is sharp. Took less than 10 minutes!

Thank you guys!

---

### Post by jcanini on 2011-02-07
I can confirm that both the printer and scanner driver work,
.... but SANE doesn't detect the scanner while GIMP does.

All in all quite easy to install and get to work.
I have just installed it so will post back if there are any issues.

Cheers J

---

### Post by dhayfule on 2011-02-17
Thanks... that rewards my post :)

---

### Post by dhayfule on 2011-02-17
> **pierre5933 said:**
> My question is not how to do it, BUT

        Is it realy ok or not twice printing and scaning??

Thanks

What r u referring to when u say twice printing and scanning?

Does ur printer prints twice even when you fire a single pint command?

---

### Post by sladden on 2011-03-18
> **jcanini said:**
> I can confirm that both the printer and scanner driver work,
.... but SANE doesn't detect the scanner while GIMP does.

All in all quite easy to install and get to work.
I have just installed it so will post back if there are any issues.

Cheers J

I have been through 4 different entries to download the drivers 4 different times. 
And, reinstall 4 different times.
I have tried installing with the MP280 connected.
I have tried installing with the MP260 dis-connected.
I have tried booting with MP280 connected.
I have tried booting with MP280 dis-connected and then plugged in.

I get the same result every time.

It does NOT tell me that it has found a scanner.

If I open 'Simple Scan'. It gives me the message :-

No scanners detected.
Please check your scanner is connected and powered on.

It works as a printer. So, why not as a scanner?

ALL the printer drivers work fine..

The scanner drivers DON'T work.

---

### Post by Free_Future on 2011-03-18
At my work i have recently the same MFC: Canon Pixma MP280
The scanner works, the printing i don't know because i don't use that

I've downloaded the DEBs from Canon, the files are the following:
> cnijfilter-common_3.40-1_i386.deb
cnijfilter-mp280series_3.40-1_i386.deb
scangearmp-common_1.60-1_i386.deb
scangearmp-mp280series_1.60-1_i386.deb

when you are done installing, you can see the scanner at GIMP (don't work in other scanning software), at my spanish setup says:
"GIMP menu: Archivo > Crear > ScanGear MP..."

i've still missed xsane because i don't know how to do "batch scanning" and i need it for my job.

Hope it helps someone, bye!

---

### Post by dakota34 on 2011-05-14
thanks everyone, accessing mp280 via samba share, and wouldn't work until I installed the Canon supplied driver in the printer setup on my buntu desktop, now works perfectly!

---

### Post by busit on 2011-05-18
Any luck with Xsane?

I found the following on Xsane Project

[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

apparently no support for MP280 but 270 is available

---

### Post by jdavila27 on 2011-06-02
Thanks for the links guys, just bought this printer and drivers work perfect for me, I'm printing and scanning.

I'm using Lucid (10.04) on a Compaq Presario CQ40 Laptop.

---

### Post by helaman on 2011-06-04
I followed everyones instructions to download the drivers from the links

 [http://support-in.canon-asia.com/con...100301402.html]("http://support-in.canon-asia.com/contents/IN/EN/0100301402.html")


[http://support-in.canon-asia.com/con...100302702.html]("http://support-in.canon-asia.com/contents/IN/EN/0100302702.html")


I installed the cnijfilter-common_3.40-1_i386.deb file and the scanner one. It says it installed. Now what?

i tried going to the printing folder. I have my printer attached to my laptop via usb. in the printing folder I say ADD. A window opens which shows that it see the device " Canon MP280". I then click forward it says "searching for drivers" then goes to a a  new window. It gives me radio button options:


[LIST]
[*]select printer from database
[/LIST]

[LIST]
[*]Provide PPD file
[*]Search for printer driver to download
[/LIST]
the first option doesn't have the database for the MP280 only the MP220 and MP500 is closest. but that doesn't help.

the 2nd option allows me to locate the directory where the drivers are found. I don't know where they are at? I tried searching for PPD files, and found them for our HP-laserjet computer but don't see them for the mp280. the hp laserjet is found in  file system/etc/cups/ppd directory.

Can someone help me!

---

### Post by helaman on 2011-06-04
you seem to know what your talking about. I just posted to get help.i installed the drivers, but what do i do next?

---

### Post by demonipuch on 2011-06-05
> **helaman said:**
> 

the 2nd option allows me to locate the directory where the drivers are found. I don't know where they are at? I tried searching for PPD files, and found them for our HP-laserjet computer but don't see them for the mp280. the hp laserjet is found in  file system/etc/cups/ppd directory.

Can someone help me!

The .ppd file you're looking for should be located in /usr/share/ppd

---

### Post by exusborquez on 2011-06-29
look i had the same problem and i downloaded from canon page the pakage for linux and i unziped them and y went to pakages and install the "cnijfilter-common_3.40-1_i386.deb" and then "cnijfilter-mp280series_3.40-1_i386.deb".
after that i went to install the printer from samba and i selected choose a ppd file and went to usr/ppd/ and here i found de canon mp280

hope this will be hellpful

---

### Post by Flutter Finch on 2011-07-07
Thank you thank you thank you!  

I am super green with all things Linux, and have had a lot of trouble getting the various drivers in my laptop to "play nice" with Ubuntu (11.04).  I felt accomplished in successfully searching the forums to get my machine in operating condition, but was struck with a slight sense of dread (mixed with a little excitement at a new challenge) when we got a new printer...  

Your post and info. was easy to follow, and it worked perfectly!  Thanks again!

---

### Post by lunaalunaa on 2011-07-24
thanks for the links. it works

---

### Post by joneshenrys on 2011-07-25
This is a free operating system X driver that allows Mac-PC interface with the Canon Pixma MP280 Photo All-in-one device inkjet printer. PIXMA MP280 Photo Inkjet All-In-One is a compact, stylish and high quality that fits almost every house. It has a maximum of 4800 x 1200 dpi color in combination with Canon's patented hybrid ink.

---

### Post by eherna2000 on 2011-08-04
Thank you printing worked like a charm. Great help :-)

---

### Post by KirkS on 2011-08-08
I have read these posts, and they seem to help the original poster, but I'm still not getting the drivers installed on my Ubuntu 10.10 laptop.  I have downloaded the drivers indicated in prior posts for this printer/scanner, and I have tried to install, but all the Terminal fires back at me is "An error occurred. The package management system cannot be identified.".  I'm obviously doing it incorrectly, as I have installed numerous other applications, and drivers with the Terminal with no problems.  I guess I need someone to hold my hand, and lead me through this.  Can anyone help?  :confused:

---

### Post by demonipuch on 2011-08-08
> **KirkS said:**
> I have read these posts, and they seem to help the original poster, but I'm still not getting the drivers installed on my Ubuntu 10.10 laptop.  I have downloaded the drivers indicated in prior posts for this printer/scanner, and I have tried to install, but all the Terminal fires back at me is "An error occurred. The package management system cannot be identified.".  I'm obviously doing it incorrectly, as I have installed numerous other applications, and drivers with the Terminal with no problems.  I guess I need someone to hold my hand, and lead me through this.  Can anyone help?  :confused:

Try this :
```
sudo dpkg -P alien rpm
```Then launch the installation script again.

---

### Post by KirkS on 2011-08-08
> **demonipuch said:**
> Try this :
```
sudo dpkg -P alien rpm
```Then launch the installation script again.

OK, I did what you recommended, and it appeared to be installing the drivers, but then it wanted to register the printer by detecting it from my network.  It couldn't.  It's funny, because Ubuntu can locate the printer on the network, but it doesn't have the correct drivers for it, but the installation of the correct drivers can't locate the printer.  That's a weird one. ](*,)  Here is what I get in the Terminal installation process:

Command executed = sudo dpkg -iG /home/mandoman/cnijfilter-mp280series-3.40-1-deb/packages/cnijfilter-common_3.40-1_amd64.deb
(Reading database ... 249142 files and directories currently installed.)
Preparing to replace cnijfilter-common 3.40-1 (using .../cnijfilter-common_3.40-1_amd64.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (3.40-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Command executed = sudo dpkg -iG /home/mandoman/cnijfilter-mp280series-3.40-1-deb/packages/cnijfilter-mp280series_3.40-1_amd64.deb
(Reading database ... 249142 files and directories currently installed.)
Preparing to replace cnijfilter-mp280series 3.40-1 (using .../cnijfilter-mp280series_3.40-1_amd64.deb) ...
Unpacking replacement cnijfilter-mp280series ...
Setting up cnijfilter-mp280series (3.40-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------
Currently selected:[0] Update
Enter the value. [0] Update
Enter the value. [0]

Any suggestions?  :-k

---

### Post by demonipuch on 2011-08-08
Turn off your printer.

Launch the script again and turn on your printer when you get the message "Register Printer". Then press Enter to search for your printer on the network.

---

### Post by KirkS on 2011-08-09
That did it.  Thanks very much.  :guitar:  :)

---

### Post by tbdunamis on 2011-08-12
I attempted to install the driver and it is asking me for an authentication code.  Do anyone know what it is, or where I can get one?

---

### Post by KirkS on 2011-08-13
> **tbdunamis said:**
> I attempted to install the driver and it is asking me for an authentication code.  Do anyone know what it is, or where I can get one?

Did you register your printer with Canon?  If so, the code is on the box in which your printer came.  That's the only authentication code I can think of.

---

### Post by trungvkvk on 2011-08-13
can I  join the topic?.
 I am a newbie so do not know what is involved to learn.
 thanks

---

### Post by MyR on 2011-08-31
I posted a guide here: [http://linuxdeal.com/how-to-install-canon-mp280-on-linux](http://linuxdeal.com/how-to-install-canon-mp280-on-linux)

Let me know if I missed any steps.

Also please review the printer if you would be so kind: [http://linuxdeal.com/add-printer.php](http://linuxdeal.com/add-printer.php)

Thanks everyone!

---

### Post by lcross on 2011-08-31
So after i got the drivers from the cannon website, i copied and pasted the drivers into the terminal and i got "command was not found". Did i input correctly?

---

### Post by tbdunamis on 2011-09-13
Well.  I found out that the authentication code is my password for logging in to Ubuntu.  However, despite downloading the drivers, and installing them according to the directions on this thread, it isn't working.  I turn the printer on, and and Ubuntu says that it ain't there.  Any ideas?

---

### Post by demonipuch on 2011-09-13
> **tbdunamis said:**
> Well.  I found out that the authentication code is my password for logging in to Ubuntu.  However, despite downloading the drivers, and installing them according to the directions on this thread, it isn't working.  I turn the printer on, and and Ubuntu says that it ain't there.  Any ideas?

Check if the packages provided by Canon are installed
```
dpkg -l cnijfilter*
```
The output of this command should look like :
```
ii  cnijfilter-common                         3.20-1                               IJ Printer Driver for Linux.
ii  cnijfilter-mp280series                    3.20-1                               IJ Printer Driver for Linux.
```

---

### Post by tbdunamis on 2011-09-13
This is the result:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status, Err: uppercase=bad)
||/ Name                        Version                    Description
+++-===============-===============-=================
ii       cnijfilter-com           3.40-1                     IJ Printer Driver for Linux

It looks like it's telling me I need to re-install both of the drivers, if not just the scanner driver.  I don't mind doing that, if that's what it takes.  However, I have already installed both of them twice.

---

### Post by demonipuch on 2011-09-13
It says that only cnijfilter-common is installed. You also need to install cnijfilter-mp280series.deb

---

### Post by tbdunamis on 2011-09-13
IT WORKS!  Thank you so much.

---

### Post by MisterBark on 2011-11-19
[http://support-in.canon-asia.com/contents/IN/EN/0100302702.html](http://support-in.canon-asia.com/contents/IN/EN/0100302702.html)

The host name **support-in.canon-asia.com** currently has no ip address !
I tried with dig by asking directly to their 4 dns servers.
 
Anyone has a mirror somewhere ?
(I'm looking for the scanner drivers)
 
THANKS !

---

### Post by demonipuch on 2011-11-19
Hi 

[http://software.canon-europe.com/](http://software.canon-europe.com/)

---

### Post by MisterBark on 2011-11-19
> **demonipuch said:**
> Hi 

[http://software.canon-europe.com/](http://software.canon-europe.com/)

thanks but the mp280 is not in the list!
[I] 
(and my country Canada neither lol)[/I]

---

### Post by demonipuch on 2011-11-19
here is a link to your printer drivers : [http://www.canon.fr/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1](http://www.canon.fr/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1)

---

### Post by MisterBark on 2011-11-19
> **demonipuch said:**
> here is a link to your printer drivers : [http://www.canon.fr/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1](http://www.canon.fr/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1)

ah ! :)
thanks a lot! everything works fine!

---

### Post by demonipuch on 2011-11-19
you're welcome

---

### Post by nemark on 2012-02-13
Thanks to all !!! the answer to my problem lied somewhere in between your comments :D so i wanted to add my path to the solution witch as i said is steps taken form different comments:
1, i downloaded the drivers from  [http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1](http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP280.aspx?type=download&page=1)  (all 4 of them)
2.  extracted all of the folders (cnijfilter-source-3.40-1; MP280series_printer_driver; MP280series_scanner_driver; scangearmp-source-1.60-1)
3.  extracted cnijfilter-mp280series-3.40-1-deb.tar.gz  in the  MP280series_printer_driver folder
4. then in the folder cnijfilter-mp280series-3.40-1-deb/packages i installed: cnijfilter-common_3.40-1_i386.deb and  cnijfilter-mp280series_3.40-1_i386.deb 
5. extracted scangearmp-mp280series-1.60-1-deb.tar.gz in the MP280series_scanner_driver folder
6. then in the folder scangearmp-mp280series-1.60-1-deb/packages i installed : scangearmp-common_1.60-1_i386.deb and scangearmp-mp280series_1.60-1_i386.deb 
7.Printing worked fine from the start like i see for most people :D
Scanning didn't work i tired GIMP and XSane , but i found a post on a another forum [http://forums.fedoraforum.org/showthread.php?t=257004](http://forums.fedoraforum.org/showthread.php?t=257004) the name of the user is [pythagorean]("http://forums.fedoraforum.org/member.php?u=173731"). 
8.His advice worked: alt+ F2 then type scan and run scangearmp and scan :D !!!!
I don't know what is the difference between normal menu approach and alt +F2 but in the normal approach typing "scan" didn't amount to anything :p
Sorry if somethings aren't clear i am a new Ubuntu user ( it has been a week now) that  went cold turkey from Windows, and English isn't my first language.

---

### Post by ginoe on 2012-02-16
w00t!

i followed your steps & it worked perfectly - thank you nemark!

i was looking for a original replacement toner for my hplj1100a - amazon has them on sale for $36. they have 'compatible' toners out there for $15 but they all have 1-star negative reviews. original toner from hp is $80!!! :(

i found this printer in walmart for $29 (yeah, it's no laser printer but it's brand new & color for less then the price of a replacement toner).

---

### Post by networker4 on 2012-04-09
> **MyR said:**
> I posted a guide here: [http://linuxdeal.com/how-to-install-canon-mp280-on-linux](http://linuxdeal.com/how-to-install-canon-mp280-on-linux)

Let me know if I missed any steps.

Also please review the printer if you would be so kind: [http://linuxdeal.com/add-printer.php](http://linuxdeal.com/add-printer.php)

Thanks everyone!

Thanks. I had some issues that it didn't detect the printer. After turning it off and on 3 or 4 times, deleting the printer from settings, then another round of on and off, it miraculously detected the printer. Test page worked!!!

---

### Post by syagdiran on 2012-04-14
Ubuntu 12.04 LTS printer, scanner ubuntu does not work. Do you have information on this subject?

---

### Post by Bandit on 2012-04-29
> **syagdiran said:**
> Ubuntu 12.04 LTS printer, scanner ubuntu does not work. Do you have information on this subject?

The Printer works fine with 12.04, the scanner on the other hand is being less then cooperative. All worked under Fedora 16 last week and then I upgraded to Precise. I installed the two 64bit debs manually and without issues since the normal ./install.sh file doesnt recongize the package system for some reason. But the scangearmp software still reports that the scanner is not connected. This leads me to believe it may not be seeing the scanner *duh* for some reason, but may not be directly related to the canon drivers. LSUSB list this:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0607 Genesys Logic, Inc. Logitech G110 Hub
Bus 001 Device 010: ID 04a9:1746 Canon, Inc. 
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
Bus 003 Device 003: ID 046d:c069 Logitech, Inc. 
Bus 001 Device 006: ID 046d:c22b Logitech, Inc. 
Bus 001 Device 007: ID 046d:c22a Logitech, Inc.
```

Although the Canon, Inc is listed. It may only be seeing the printer part which is working. Not sure of the inner working around the USB inside the printer though. I may be wrong but I thought at one time it would list two items under LSUSB one for Printer and one for Scanner???

---

### Post by OostAchterhoek on 2012-04-30
Use new updated driver for scangear. (version 1.80) and scanning for Canon MP280 will work.

see this link:
[https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

good  luck !!

---

### Post by standingfire on 2012-05-07
Thanks also, I found these stumbling through and I can use this wretched printer.

---

### Post by emmdarakis on 2012-05-12
> **OostAchterhoek said:**
> Use new updated driver for scangear. (version 1.80) and scanning for Canon MP280 will work.

see this link:
[https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

good  luck !!


I can confirm that (only) this works in Precise.

I downloaded and installed the latest version of the 4 deb files from the link provided ([http://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](http://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)). 

Both scanner and printer now works in 12.04!!!

Thanks a lot!

---

### Post by dguerre on 2012-05-14
> **OostAchterhoek said:**
> Use new updated driver for scangear. (version 1.80) and scanning for Canon MP280 will work.

see this link:
[https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

good  luck !!
This works, Thank you.

---

### Post by mrpurple on 2012-06-23
how do you install those packages ?

---

### Post by MalinBrown on 2012-07-30
Hi!

I have to say that the new drivers for the scanner aren't working for me. I installed the one from the Canon official site, 1.60, and then updated with the 1.80 and is still not working. I'm very disappointed with Ubuntu right now. I thought that things that worked before would still be working with 12.04, and this is feeling like a slap on my face. I don't know what to do... because 1.80 seems to work for everyone...

I've been using Ubuntu 12.04 just for 3 days and I was really happy until today.

I installed Gimp 2.6. File -> Create -> ScanGear MP.. and.. disaster!!! Not available scanner... all the time... arggg

I downloaded this: scangearmp-mp280series_1.80-0~11~precise1_amd64

---

### Post by MalinBrown on 2012-08-05
Hi!
I'm unable to put to work the scanner with 12.04. At the end I virtualized ubuntu 10.04 and that's what I'm using. And from today the printer just prints half page... I googled and I think that's some problem with cups... so I guess I'll be using Lucid frequently...

Maybe I did something wrong when I installed the drivers.

My steps.
1. I installed both source and mp280 for the printer and the scanner
2. I updated both of them with the new drivers.
3. Nothing works.

Ideas?

---

### Post by pdc on 2012-08-11
> Nothing works............

I wondered what you did to get your Canon scanner to work:

Canon provide the programme scangear and sadly there is not a GUI interface for it, so you initially issue the command

> scangearmp

in a terminal;

If you do this, do you get the programme scangear loading...

this post

[http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop](http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop)

talks about how to create a launcher so that you can load scangear more easily in the future;

---

### Post by MalinBrown on 2012-08-19
> **pdc said:**
> 


in a terminal;

If you do this, do you get the programme scangear loading...



If I write scangearamp in a terminal I get the same message than with Gimp. Scanner not found.

What I did to install the drivers is in my previous post.

---

### Post by thomasphillpotts on 2012-08-20
I installed the drivers from the Canon website as listed above and everything is working fine for me, printing and scanning.
Running Ubuntu 11.10.

Does it cause problems if the printer is on and connected via USB when installing the drivers? Initially it wasn't working but after trying the install again today everything is good. Does rebooting affect the driver install?

Scanning works well, accessing it through GIMP.

---

### Post by LK_gandalf_ on 2012-08-28
Kubuntu 12.04 64bit, printer works well after having installed the Canon drivers (.deb). Scanner works only after having installed the drivers version 1.80, precisely these two files:

- [URL="https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+build/2890941/+files/scangearmp-common_1.80-0%7E11%7Eprecise1_amd64.deb"]https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+build/2890941/+files/scangearmp-common_1.80-0%7E11%7Eprecise1_amd64.deb
[/URL]
- [https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+build/2890941/+files/scangearmp-mp280series_1.80-0%7E11%7Eprecise1_amd64.deb]("https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+build/2890941/+files/scangearmp-mp280series_1.80-0%7E11%7Eprecise1_amd64.deb") 

User-friendliness: zero 0.

How to scan? Ksane and other program don't detect any scanner. Terminal > snagearmp ? This is not possible at all to do every day, for many users can be a single good reason to abandon Ubuntu.

(bracket on)
Ok, we cannot blame Ubuntu because Canon releases the drivers (this is always the official story), but I ask myself why I spent half a day and my free time just to install a damned printer (and why I spent this time for the webcam, mouse, and so on).
If Linux wants to keep users (I have plenty of patience and support Linux since years, but I'm almost done now. Cannot imagine the reaction of someone who can't wait to have an excuse to go back to windows..) they MUST talk/lobby with the major companies and be sure that there will be an easy .deb package on their websites which will install drivers and some graphical-decent software!

How can I never install Ubuntu on my newbies parents' pc? No way...Ubuntu/linux is far better than 10 years ago, but instead of renovating the graphical interface every 6 months, they should start to do some serious lobbying.
(bracket off)

---

### Post by pdc on 2012-08-28
sorry to hear you are so frustrated about the installation; you sound very fed up and brassed off with things;

as part of your frustration and irritation you say

> terminal > scagearmp ? This is not possible at all to do every day, f

to help that sort of reaction, in my post (#62) I gave a link as to how to install a launcher; I see you use kubuntu 64bit

I post it again

[http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop](http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop)

I am sorry your experience of installation was so frustrating; I recently installed a Canon MG2160 and then on another computer the MG3160; both were very quick and straightforward; I created a launcher for scangearmp and I have been very pleased with both; 

You have obviously been a big supporter of linux and everyone would hope you stay part of the linux community and can help and support others;

best wishes

---

### Post by aikishugyo on 2012-08-28
> **LK_gandalf_ said:**
> Kubuntu 12.04 64bit, printer works well after having installed the Canon drivers (.deb). Scanner works only after having installed the drivers version 1.80 /../
How to scan? Ksane and other program don't detect any scanner. Terminal > snagearmp ? This is not possible at all to do every day, for many users can be a single good reason to abandon Ubuntu.

Hi, my 2 cents worth.

I've been involved on the Canon side with both the SANE project (scanner support) and the gutenprint project (inkjet printer support); on the latter I am currently the maintainer of the Canon backend, and as far as the former goes, I am always happy to work on adding more support for new Canon scanners.

1) SANE should support the MP280 (it is marked in the code as untested), so if you would try it with SANE and giove feedback, we could ensure built-in support on linux platforms. Scanner support is generally fairly straightforward to add.

2) Gutenprint also supports to MP280, although the Canon backend is not perfect: photo printing may be less than ideal, and there may be issues with calibration of the colors, depending on the media and resolution chosen. However, feedback is welcome.

Regards,
Gernot Hassenpflug

---

### Post by pdc on 2012-08-28
thanks for this post aikishugyo; pleased to help if I can with the MG2100 and the MG3100

lsusb for the 2100 gives 

> 04a9:1751

and sane-find-scanner gives

> found USB scanner (vendor=0x04a9 [Canon], product=0x1751 [MG2100 series]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

however both 

> scanimage -L

and 

> sudo scanimage -L

report

> No scanners were identified.

the files from here

[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

all seem to be loaded

xsane reports no scanner;

pleased to receive guidance on how to get things going

---

### Post by LK_gandalf_ on 2012-09-08
> **aikishugyo said:**
> 
1) SANE should support the MP280 (it is marked in the code as untested), so if you would try it with SANE and giove feedback, we could ensure built-in support on linux platforms. Scanner support is generally fairly straightforward to add.

Hi and thank you all for the replies. I will be happy to help with a feedback, just need more info on what to do :)

---

### Post by aikishugyo on 2012-09-10
> **pdc said:**
> thanks for this post aikishugyo; pleased to help if I can with the MG2100 and the MG3100. /../
pleased to receive guidance on how to get things going

1) What is the SANE version.
2) If you run xsane as root and first set the debug level for the pixma backend, then we can discover if the version of SANE used on your system recognizes the MP280 or not. Here is how (man sane-pixma for mor info):

export SANE_DEBUG_PIXMA=3
xsane

If the MP280 is not registered in your version of SANE, you'll need to download a new version from CVS repository and compile it to get support. It's not hard, I can explain as needed.

If the MP280 is recognized by SANE (specifically the pixma backend), then I'll have to work on correcting bugs---but for that probably we'll need some USB sniffs from Windows.

Let's try the debug first.
Regards,
Gernot Hassenpflug

---

### Post by aikishugyo on 2012-09-10
> **LK_gandalf_ said:**
> Hi and thank you all for the replies. I will be happy to help with a feedback, just need more info on what to do :)

Please see my answer to pdc's post on how to check that your SANE version actually has supposed support for the MP280 in it.

Regards,
Gernot Hassenpflug

---

### Post by pdc on 2012-09-10
Hi Gernot;

is it okay to use this thread for investigating the scanning of the **MG2160** and the **MG3160**?

1.0.14-9 is the version of sane that I have installed

so I coped into a terminal

> export SANE_DEBUG_PIXMA=3

and then following your advice to run xsane as root typed

> sudo xsane

and received the suitably dire warning enclosed as screenshot!

so I tried 

> xsane

and sane could not detect any devices and plucking up all my courage I reverted to root with 

> sudo xsane

it was the same: no devices detected

.. sounds like I may need this??

> you'll need to download a new version from CVS repository and compile it to get support. It's not hard, I can explain as needed.


---

### Post by aikishugyo on 2012-09-10
> **pdc said:**
> Hi Gernot;

is it okay to use this thread for investigating the scanning of the **MG2160** and the **MG3160**?
1.0.14-9 is the version of sane that I have installed

Ah, different thread would be best, but in the interestes of the other readers, here the instructions to get and compile SANE from CVS. Yes, you probably need CVS SANE from git to get support for the newer scanners.

When you run sudo xsane (and accept the risk of running as root) then the console should show pixma module output, including the fact that it could not match the USB ID with any scanner model.

To get the CVS code, you need git installed. Then you can do inside a source direcftory (I usually use ~/src):

```
mkdir ~/src
cd ~/src
git clone git://git.debian.org/sane/sane-backends.git
```

Reference: [http://www.sane-project.org/cvs.html]("http://www.sane-project.org/cvs.html")

Go to sane-backends, and try to compile:
```
cd sane-backends
BACKENDS="pixma" ./configure
make
sudo make install
```

I don't know if you will need some dependencies first (like gcc, some parsers maybe, etc.)

SANE is installed into /usr/local, so it does not overwrite the system SANE. But you may need to always run xsane as sudo to be sure that you access the new pixma libraries.

Regards,
Gernot Hassenpflug

---

### Post by pdc on 2012-09-10
thanks

> Go to sane-backends, and try to compile:

........please spell out what I am to do........

> To get the CVS code, you need git installed. Then you can do inside a source directory (I usually use ~/src):

......pasted your git command into a terminal and it is happening

........please spell out what "Then you can do inside a source directory (I usually use ~/src)"involves:

---

### Post by aikishugyo on 2012-09-10
> **pdc said:**
> thanks
........please spell out what I am to do........

I edited my original post. I hope that is sufficient, else please ask more.

---

### Post by pdc on 2012-09-11
so I followed your instructions;

before make, it advised installed libusb-dev; which I did;

sudo xsane after the above still produced no devices recognised;

if you can guide me on what is needed to furnish more information for you

---

### Post by aikishugyo on 2012-09-11
> **pdc said:**
> so I followed your instructions;

before make, it advised installed libusb-dev; which I did;

sudo xsane after the above still produced no devices recognised;

if you can guide me on what is needed to furnish more information for you

Did the pixma debug output show that it did not find any matching USB ID, or did it find a matching USB ID but was unable to initialize the device?

In the former case, you need to install the new code. In the latter case, we need to fix the code for this scanner. For that, one needs to snoop the USB traffic of test scans using a USB sniffer:

[http://www.pcausa.com/Utilities/UsbSnoop/default.htm](http://www.pcausa.com/Utilities/UsbSnoop/default.htm)

What you do is install it on a Windows XP (not Vista, not 7) system where your Scanner is installed,

1) start the sniffing,
2) then use the "replug" function of the software to make the USB initialization occur again (packets will restart at 0 also). You can check this in the log file of the software. Then start up the Canon ScanGear software (or it could be open already) and used the advanced settings:
3) take the smallest scan (I guess Canon software limits to about 4mm x 4mm) at the lowest resolution (75 dpi for flatbed), in color.
4) stop the sniffing, and save the log file to something relevant,
5) use the "delete" function in the software to empty the logfile.

Then repeat steps 1 to 5 doing a 75 dpi scan in grayscale and monochrome (black and white).

These three logs should then be compressed with gzip and sent to me by mail (aikishugyo at gmail dot com). Note that if you take a large scan area you won't be able to make the files small enough to attach to email....

Once these files are understood by me (i.e., we have demonstrated that the above process works to create logs files I can interpret on my side) then we can repeat the above at the higher optical resolutions, which will be multiples of 75: 150, 300, 600, 1200 dpi for this canner.

The MP280 already works, apparently, up to 600 dpi, so I suppose I only need 1200 dpi scans. However, you need to learn how to use this software first, and we need to prepare a special scan material for the 1200dpi scan (the letters R, G,B written consecutively in their respective colors and scanned), so let's start with 75 dpi.

---

### Post by twipley on 2012-09-12
> **emmdarakis said:**
> I can confirm that (only) this works in Precise.

I downloaded and installed the latest version of the 4 deb files from the link provided ([http://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](http://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)). 

Both scanner and printer now works in 12.04!!!

Thanks a lot!
Should one download both "common" and "mp280series" files? What about both "cnijfilter" and "scangearamp" variants?

I personally have installed all 4 deb files and rebooted, although scanning has not gotten to work through Simple Scan -- no perceivable change.

---

### Post by Corvair on 2012-09-20
Great information.
I just downloaded the drivers from Canon for the printer and the scanner.
The printer already prints but the scanner does not work yet as I do not know how to install the drivers. Please I need someone to walk me through this.

Thank you in advance.

---

### Post by aikishugyo on 2012-09-20
SANE has support for the MP280, so if you install the latest SANE from git you should be able to scan.

---

### Post by Corvair on 2012-09-21
Hello aikishugyo and everyone else,

I am getting closer.
I deleted the printer and scanner drivers I got from Canon and loaded the files from the launchpad Micheal Cruz instead.
Then I typed in a Terminal "scangearmp" and to my surprise the Canon ScanGear window opened.
I previewed a document to see if it worked and I got a preview.
Then I tried a scan and could not get a scan.

After typing a name for the folder I got: Invalid path
In save folder: Cannot select a folder. After several tries I was able to enter a name and automatically was able to save a document to the TMP folder.
I tried to repeat and I cannot get to enter a name again.

Something not configured right??? I don't know.
Any sugestions?

---

### Post by Corvair on 2012-09-22
OK,
Thanks to everyone. Finally figured out how to operate ScanGear.

You have to preview first and then select where you want the document to go and then hit the scan.

But , still I cannot get Simple Scan to recognise the scanner.
Not perfect but I can use the MP280 Scanner.

---

### Post by twipley on 2012-10-05
> **Corvair said:**
> OK,
Thanks to everyone. Finally figured out how to operate ScanGear.

You have to preview first and then select where you want the document to go and then hit the scan.

But , still I cannot get Simple Scan to recognise the scanner.
Not perfect but I can use the MP280 Scanner.

OK -- thanks for the feedback.

So, if I understand correctly, the answer lies over at [https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages), then launching "scangearmp" from terminal.

A couple of questions (the computer of the person I am trying to help is so slow and underpowered that any external help or insight would be greatly appreciated):

1) are both "scangearmp-common-1.80" and "cnijfilter-common-3.70" needed?

2) what will happen when quantal (or any other new version) comes out -- will scanning work no more every six months? (I am thinking of locking this person to precise for them to stop needing me helping them, although this would only be if necessary.)

---

### Post by twipley on 2012-10-05
The biggest question might be: why are not such scanners supported out of the box? Everything seems to work so nice in companionship with HPs...

---

### Post by aikishugyo on 2012-10-05
> **twipley said:**
> The biggest question might be: why are not such scanners supported out of the box? Everything seems to work so nice in companionship with HPs...

Well, that is easy (as seen by this thread): because people who have the scanners seem to prefer to use the Canon software instead of helping with "out of the box" development (which would be SANE, and gutenprint).

---

### Post by pdc on 2012-10-05
> what will happen when quantal (or any other new version) comes out

the 12.04 version of Ubuntu is called the LTS version;

LTS= long-term support

have a read at this wiki

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

so 12.04 will be supported till 2017; so ideally suited to stay as the installed distro

__________________________________________________________

..............**[COLOR="Red"]_How to run scangear_[/COLOR]**.........

>  then launching "scangearmp" from terminal.

......that is right........and a "launcher" ......is very helpful to automate the process for repeated use............

.....and the thread below......

[http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop](http://linuxhelp.host.org/index.php?page=news&type=view&id=linux-help_2%2Fhow-to-create-desktop)

.......tells you how to do it;

__________________________________________________

I have created a launcher for scangear

I enclose a thumbnail below of what it looks like.....

........you can call it what you like......

......the command must say

> scangearmp

......to launch the programme

---

### Post by twipley on 2012-10-05
> **aikishugyo said:**
> SANE has support for the MP280, so if you install the latest SANE from git you should be able to scan.

> **aikishugyo said:**
> Well, that is easy (as seen by this thread): because people who have the scanners seem to prefer to use the Canon software instead of helping with "out of the box" development (which would be SANE, and gutenprint).

Well, you are right. I had skipped that post, because a quick Google search returned incompatibilities, although I am now browsing [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html) and perceiving the MP280, like you said, indeed is supported by the latest stable version.

It is a shame both precise and quantal do not provide access to v1.0.23 from their respective USCs, me being unable to do anything with downloaded-from-sites SANE packages.

Furthermore, as I understand it, Simple Scan is a frontend for the SANE backend, is not it? Therefore, would not there be a method for that backend to be included in the next versions of Ubuntu? (Perhaps I should wait to see if the scanner function gets, in an automatic manner, supported in quantal.)

---

### Post by twipley on 2012-10-05
I do not know what that means, but:

[https://launchpad.net/ubuntu/quantal/i386/simple-scan/](https://launchpad.net/ubuntu/quantal/i386/simple-scan/)
[https://launchpad.net/ubuntu/quantal/i386/libsane](https://launchpad.net/ubuntu/quantal/i386/libsane)

it is written simple-scan depends on the libsane package -- which seems to point that ("i386 build of sane-backends 1.0.23-0ubuntu1 in ubuntu quantal RELEASE") mp280 is compatible out of the box with quantal.

If anyone finds out, please post here so we can stop talking and start scanning! ;)

---

### Post by aikishugyo on 2012-10-05
> **twipley said:**
> It is a shame both precise and quantal do not provide access to v1.0.23 from their respective USCs, me being unable to do anything with downloaded-from-sites SANE packages.

Do you mean you don't know how to compile SANE from source? I am pretty sure I gave a step-by-step instruction in this thread earlier though. It is dead simple, and does not overwrite the  system SANE.

> **twipley said:**
> Furthermore, as I understand it, Simple Scan is a frontend for the SANE backend, is not it? Therefore, would not there be a method for that backend to be included in the next versions of Ubuntu? (Perhaps I should wait to see if the scanner function gets, in an automatic manner, supported in quantal.)

You would have to check how each Ubuntu version handles upstream packages. For example, since 1.0.23 was released in August, it is included in Quantal since September 20th (according to the Ubuntu pacakges page for sane-backends), and there the MP280 is supported---up to 600dpi. For 1200dpi I would need someone to sniff under Windows XP.

---

### Post by twipley on 2012-10-06
> **aikishugyo said:**
> I've been involved on the Canon side with the SANE project (scanner support); [...] I am always happy to work on adding more support for new Canon scanners.

SANE should support the MP280 (it is marked in the code as untested), so if you would try it with SANE and give feedback, we could ensure built-in support on linux platforms. Scanner support is generally fairly straightforward to add.

> **aikishugyo said:**
> Do you mean you don't know how to compile SANE from source? I am pretty sure I gave a step-by-step instruction in this thread earlier though. It is dead simple, and does not overwrite the  system SANE.
This is what I am saying. I am a terrible layman. Here are the instructions, for reference. (No problem though; continue reading below to find out.)

> **aikishugyo said:**
> Here the instructions to get and compile SANE from CVS. Yes, you probably need CVS SANE from git to get support for the newer scanners.

When you run sudo xsane (and accept the risk of running as root) then the console should show pixma module output, including the fact that it could not match the USB ID with any scanner model.

To get the CVS code, you need git installed. Then you can do inside a source direcftory (I usually use ~/src):

```
mkdir ~/src
cd ~/src
git clone git://git.debian.org/sane/sane-backends.git
```

Reference: [http://www.sane-project.org/cvs.html]("http://www.sane-project.org/cvs.html")

Go to sane-backends, and try to compile:
```
cd sane-backends
BACKENDS="pixma" ./configure
make
sudo make install
```

I don't know if you will need some dependencies first (like gcc, some parsers maybe, etc.)

SANE is installed into /usr/local, so it does not overwrite the system SANE. But you may need to always run xsane as sudo to be sure that you access the new pixma libraries.


> **aikishugyo said:**
> Since 1.0.23 was released in August, it is included in Quantal since September 20th (according to the Ubuntu pacakges page for sane-backends), and there the MP280 is supported--up to 600 dpi.
This is great news -- that means no more fiddling with anything, and that everything is compatible out of the box more and more. :guitar:

Thanks for the help; it is greatly appreciated!

---

### Post by aikishugyo on 2012-10-06
> **twipley said:**
> This is what I am saying. I am a terrible layman. Here are the instructions, for reference.

Hi,
Yes, those instructions are fine, please feel free to try them, or use Quantal.
Knowing for myself that the scanner is really working under SANE will be a great relief (although it is already known apparently, not "untested").

What would be even more welcome on top of that, would be if you have access to WinXP and could install the Canon driver and then do some USB sniffing (instructions as neded at that time) at 1200dpi so that we can get the scanner working completely.

Cheers,
Gernot Hassenpflug

---

### Post by twipley on 2012-10-06
> **aikishugyo said:**
> What would be even more welcome on top of that, would be if you have access to WinXP and could install the Canon driver and then do some USB sniffing (instructions as neded at that time) at 1200dpi so that we can get the scanner working completely.
Well, I guess I could contribute to that. At least, if the person would not mind lending me their scanner for a week or two.

I am quite busy with stuff at the moment, but perhaps between the 20th and the 31th of October I will have some time to fiddle with that. I already have Windows XP x86 installed through the latest VirtualBox.

The driver I will download is: [http://gdlp01.c-wss.com/gds/5/0100002905/02/mp280swin101ejs.exe](http://gdlp01.c-wss.com/gds/5/0100002905/02/mp280swin101ejs.exe)
```

**Details - MP280 series MP Driver Ver. 1.01 (Windows 7/7 x64/Vista/Vista64/XP/XP x64)**

ID: 0100290502_EN_2

This product is a driver for Canon IJ multifunction printers.
```
Source: [http://usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mp_series/pixma_mp280](http://usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mp_series/pixma_mp280)

I will post back in the two following weeks to either output that I cannot do this, or that I can and want the instructions to perform some (much-needed) USB sniffing.

---

### Post by aikishugyo on 2012-10-06
> **twipley said:**
> Well, I guess I could contribute to that. At least, if the person would not mind lending me their scanner for a week or two./../
I will post back in the two following weeks to either output that I cannot do this, or that I can and want the instructions to perform some (much-needed) USB sniffing.

OK, if that will be possible then wonderful. Note that Scangear under Windows has some quirks, you need to go to the advanced settings selection in order to choose resolution settings, and possibly you may even have to enter the number (1200) yourself, if it is not available in the drop-down selection.

For a scan, prepare a small area (top left on a sheet of white paper), perhaps 2cm high and 6cm wide, and write in block leters the letters RGB, each in their respective colors, as neatly as possible (these will be used to collate the colors in the scan data, under 400x or 800x magnification to figure out needed values of de-striping or other kinds of data manipulation).

I will then need color (most important), grayscale and monochrome scans of this, each sniffed with SniffUSB v2.0, the program you can find here:

SniffUSB v2.0, for x86 and x86-64 architectures, and complete instructions for use:
[http://www.pcausa.com/Utilities/UsbSnoop/default.htm](http://www.pcausa.com/Utilities/UsbSnoop/default.htm)

A generic look at the development of the sniffer program, for interest:
[http://linuxtv.org/wiki/index.php/Usbsnoop](http://linuxtv.org/wiki/index.php/Usbsnoop)

Note: you can use v1.8 as well, although the buttons are a bit different, but please do not use Snoppy Pro or any other newer derivative. Not only are they more confusing to use, but the log format cannot be parsed by our current tools, making it much more difficult (WIP).

Please read the above page for clear instructions with screenshots. Below my interpretation for posterity...

The installation is simply to copy the SniffUSB.exe program to the Windows Desktop, and execute it. It puts a library into the system folder, and then displays a list of known USB devices, and under the display screen is a series of control buttons. When you attach a new USB device, and press "refresh", it should appear in the list.

You select the device in the list with the mouse, and press the "install" button (in the Filter Control column on the right).

It is crucial usually to "replug" the scanner from inside the program after attaching it to the program (obviously it has already initialized itself on connection to the OS and therefore sniffusb can see it and select it for sniffing.... so now a "replug" action reinitializes the scanner and the sniffer can record the initialization packets). Feel free to replug as many times as you need (a look at the log file should show that the USB packet count gets reset to 1).

Now, on to the log file (leftmost column of buttons). By default, a log is already in progress. This is usually fine, so go ahead with a scan.

After each scan, stop the recording with "pause log", write remaining buffer information to the logfile with "close log", then copy (not move!) the logfile to the Desktop (rename it to something meaningful like mp280-color-1200dpi.log), and then re-initialize the log file to zero with "delete log", and start logging again with "resume log".

Now, before doing another scan, do a "replug" to initialize the scanner again and reset the USB packet count to 1. Then perform the scan of interest, "pause log", "close log", copy the actual log file to the Desktop and rename it, and then "delete log", "resume log", "replug", and then scan again.... do you follow the sequence?

Hope that helps anyone that wants to do some USB sniffing for the SANE project.

Note: Canon scanners generally start at 150dpi for flatbed, and have physical resolutions in multiples after this: 300, 600, 1200, 2400, 4800, 9600. There is no need to try in-between values (which Windows offers in the selection I believe).

Cheers,
Gernot Hassenpflug

---

### Post by twipley on 2012-10-06
Okay. So I would install the driver, reboot, then follow the instructions you have just posted, scanning using Scangear?

Furthermore, the sheet of white paper does not need to have anything written on it, besides the three letters?

In the same line of thought, do the letters need to be written thick, for example using felt-tip (marker) pens?

Finally, I will need to manually select either 400x or 800x magnification in the Scangear program, right?


twipley

---

### Post by aikishugyo on 2012-10-06
> **twipley said:**
> Okay. So I would install the driver, reboot, then follow the instructions you have just posted, scanning using Scangear?

Yes, you use the Canon scan program. I did not check where you will get this from, usually it is sufficient to simply access the nearest Canon website and download the software driver for the device from there. I prefer the USA site as it is easiest to navigate and most sensibly organized for me.

> **twipley said:**
> Furthermore, the sheet of white paper does not need to have anything written on it, besides the three letters?

In the same line of thought, do the letters need to be written thick, for example using felt-tip (marker) pens?

Thick is good, that is what block leters is suposed to signify. I use colored penciels, but feel free to use whatever you have, as long as the paper does not become soggy :-)

> **twipley said:**
> Finally, I will need to manually select either 400x or 800x magnification in the Scangear program, right?

No nagnification needed (you can look at your pre-scan at whatever magnification you like of course). That is my job when looking at the re-asembled data under SANE.

Cheers,
Gernot Hassenpflug

---

### Post by twipley on 2012-10-07
Having no marker pens at all around, would not it just be easier for us to create a PDF file with RGB letters on the upper-left corner, that I could then real-size laser-print at school?

I believe their color reproduction might be adequate, and on top the PDF file could be printed back by anyone to help the SANE project USB-sniffing relevant data.

---

### Post by aikishugyo on 2012-10-07
> **twipley said:**
> Having no marker pens at all around, would not it just be easier for us to create a PDF file with RGB letters on the upper-left corner, that I could then real-size laser-print at school?

I believe their color reproduction might be adequate, and on top the PDF file could be printed back by anyone to help the SANE project USB-sniffing relevant data.

Yes, you can do tha. As long as the red, green and blue are separated and recognizable shapes you can have anything you want.

---

### Post by twipley on 2012-10-07
> **aikishugyo said:**
> Yes, you can do that. As long as the red, green and blue are separated and recognizable shapes you can have anything you want.

Okay. I will be printing the attached document in the center of the sheet, at a low scaling value, so as not to waste too much ink.

source: [http://www.flickr.com/photos/s2art/325135760/](http://www.flickr.com/photos/s2art/325135760/)

By the way, I will have access to the printer in about a week or two -- I will repost here then.

---

### Post by aikishugyo on 2012-10-07
> **twipley said:**
> Okay. I will be printing the attached document in the center of the sheet, at a low scaling value, so as not to waste too much ink.

source: [http://www.flickr.com/photos/s2art/325135760/](http://www.flickr.com/photos/s2art/325135760/)

By the way, I will have access to the printer in about a week or two -- I will repost here then.


Please keep the colors separate and on one line, not joined in two dimensions like in your example. R G B will be best if it is least confusing to understand.

---

### Post by twipley on 2012-10-07
What about the below attachment? Should be more viable.

---

### Post by aikishugyo on 2012-10-07
> **twipley said:**
> What about the below attachment? Should be more viable.

If you are making blocks, I don't need big blocks, they can be just thin horizontal lines for the same result. Instead, I need shapes like letters so it is possible to see things at different angles.

---

### Post by twipley on 2012-10-07
> **aikishugyo said:**
> As long as the red, green and blue are separated and recognizable shapes you can have anything you want.
It is my last try at it. If it is still not correct, then you will have to create a viable file yourself for me to work with.

(Although I believe it should now be okay.)

See you in the near future, level-15 Tokyo man.

---

### Post by aikishugyo on 2012-10-07
> **twipley said:**
> It is my last try at it. If it is still not correct, then you will have to create a viable file yourself for me to work with.

(Although I believe it should now be okay.)

See you in the near future, level-15 Tokyo man.

Looks fine to me! Maybe the shade of green is too light though.... kidding!!!

---

### Post by twipley on 2012-10-07
The green is too green? ::facepalm:: #-o

---

### Post by twipley on 2012-10-18
I'm sorry. I cannot understand where to download scangear. I installed the driver, but there is no scangear. I am pushing the scan button on the scanner, but nothing seems to get sniffed. I am approaching mid-semester, and I cannot afford spending more time on this.

---

### Post by aikishugyo on 2012-10-18
> **twipley said:**
> I'm sorry. I cannot understand where to download scangear. I installed the driver, but there is no scangear. I am pushing the scan button on the scanner, but nothing seems to get sniffed. I am approaching mid-semester, and I cannot afford spending more time on this.

I have no idea why this is difficult, have you looked at the MP280 on Canon's website? I recommend the US site for its easy browsing functionality. Takes no time at all to find what you need.
[http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mp_series/pixma_mp280#DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mp_series/pixma_mp280#DriversAndSoftware)

1) The driver is the MP driver, currently version 1.01, it includes the TWAIN scanner driver. Any scanner program should then be able to connect to the scanner.

2) The program Canon gives you for scanning is called MP Navigator, it is version 4.02 at this time.

3) There are several USB connections to a multi-purpose machine, you need to select the one for the scanner in order to sniff scans. If you select the wrong one you won't be recording anything.

Hope that helps,
Gernot

---

### Post by pdc on 2012-10-19
twipley:
aikishugyo is the real expert on scanning and sane;

I am much more of a plodder.......

If I give you some very direct pointers to help you find scangear?

go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html)

and click the big red [COLOR="Red"]DOWNLOAD NOW[/COLOR] button to get the 

[COLOR="SeaGreen"]MP280 series ScanGear MP Ver. 1.60 for Linux (debian Packagearchive)[/COLOR]

it comes down as a .tar.gz file

[COLOR="Blue"]scangearmp-mp280series-1.60-1-deb.tar.gz[/COLOR]

the terminal commands would be

> [COLOR="Red"]cd Downloads[/COLOR] .hit enter for each command..

> [COLOR="Red"]tar -zxvf scangearmp-mp280series-1.60-1-deb.tar.gz[/COLOR] 

> [COLOR="Red"]cd scangearmp-mp280series-1.60-1-deb[/COLOR]

> [COLOR="Red"]./install.sh[/COLOR]

.......and you should see things happening on your terminal

.....once done to get it to run

> scangearmp

and the programme should open.........

.....how did that go?

---

### Post by aikishugyo on 2012-10-19
Hi pdc,
I'm also a plodder, so I only know the track I plodded along, a real "one-trick pony", that's me! For more, one needs a project :-) Hence, I'm an active member of the gutenprint project, and help out on the SANE project as time permits.

The instructions you give are fine, for using Canon's scangear software under linux. In contrast, what I am helping with is how to get USB snoop data from Windows using Canon's software for the MP280. I don't know the circumstances, but instead of scangear, there is MP Navigator for the MP280. 

Note: From cursory inspection, I surmise Scangear is only provided for high-end devices on Windows, such as the CanoScan 8800F (which I own), iR series and so on.

---

### Post by twipley on 2012-10-19
```
MP Navigator EX
```

This is the information I needed.

I will give it one more shot later on this morning.

---

### Post by twipley on 2012-10-19
Alright. Here are the instructions I followed, for the sake of preservation. Note that I retained the most-important information. Best I could layman-side. ;)

> **aikishugyo said:**
> 1) The driver is the MP driver, currently version 1.01, it includes the TWAIN scanner driver. Any scanner program should then be able to connect to the scanner.

2) The program Canon gives you for scanning is called MP Navigator, it is version 4.02 at this time.

3) There are several USB connections to a multi-purpose machine, you need to select the one for the scanner in order to sniff scans. If you select the wrong one you won't be recording anything.

> **aikishugyo said:**
> I will then need color (most important), grayscale and monochrome scans of this, each sniffed with SniffUSB v2.0, the program you can find here:

SniffUSB v2.0, for x86 and x86-64 architectures, and complete instructions for use: [http://www.pcausa.com/Utilities/UsbSnoop/default.htm](http://www.pcausa.com/Utilities/UsbSnoop/default.htm)
You select the device in the list with the mouse, and press the "install" button (in the Filter Control column on the right).

Note: Canon scanners generally start at 150dpi for flatbed, and have physical resolutions in multiples after this: 300, 600, 1200, 2400, 4800, 9600. There is no need to try in-between values (which Windows offers in the selection I believe).

It is crucial usually to "replug" the scanner from inside the program after attaching it to the program (obviously it has already initialized itself on connection to the OS and therefore sniffusb can see it and select it for sniffing.... so now a "replug" action reinitializes the scanner and the sniffer can record the initialization packets).

After each scan, stop the recording with "pause log", write remaining buffer information to the logfile with "close log", then copy (not move!) the logfile to the Desktop (rename it to something meaningful like mp280-color-1200dpi.log), and then re-initialize the log file to zero with "delete log", and start logging again with "resume log".

Now, before doing another scan, do a "replug" to initialize the scanner again and reset the USB packet count to 1. Then perform the scan of interest, "pause log", "close log", copy the actual log file to the Desktop and rename it, and then "delete log", "resume log", "replug", and then scan again.... do you follow the sequence?

Hope that helps anyone that wants to do some USB sniffing for the SANE project.

Furthermore, this is the picture that has to be scanned. [http://ubuntuforums.org/attachment.php?attachmentid=225238](http://ubuntuforums.org/attachment.php?attachmentid=225238) It should be printed using adequate settings.

Wow, I had never realized current-generation scanners were *that* powerful! On the picture, one can see detailed hairs, and if I had been bleeding, one could almost see the DNA structure! (Not *that* close, but *close enough*.) :)

At least for the needs. I had more problems. From inside "Canon MP Navigator EX," resolutions over 600 dpi could not be chosen. However, just below this setting is a "use the scanner driver" box, which, once ticked, permits the opening of ScanGear from within, which permits using the 1200 dpi.

Next post should feature picture and log links!

---

### Post by twipley on 2012-10-19
I've ran into another problem which resulted in scan being unable to be performed, as resolution exceeded 10001*10001 pixels, told the message. although I have fixed it through reducing (through pre-scan tweaking) the scanning area to the upper-left corner of the page, all the while maintaining a resolution of 1200 dpi.

Furthermore, I had to tweak the default settings to disable any kind of post-processing that would have influenced the image output, although that might not have affected the log file (or would it have?).

I have compressed using 7-Zip, which, through normal settings, gave a compression ratio of 6%, which brought the archive down from 380 to 26 MB.

The resulting file is available over at [http://www.2shared.com/file/cuZSf91q/logs.html](http://www.2shared.com/file/cuZSf91q/logs.html)

Did I do a good-enough job? If you tell fast enough, I might have time to correct things before returning the machine. :)

---

### Post by aikishugyo on 2012-10-19
Hello Twipley,
Thanks for the effort, it finally paid off: the logs look fine, they correctly include the initialization of the scanner, and I could parse them. Now need to reconstruct images from them and submit patches to the SANE pixma backend maintainer.
I'll post here again on the weekend after I have done this. If you have already compiled SANE from source, I can send you the patches file you will need, and you can test if it works.
Regards,
Gernot

---

### Post by aikishugyo on 2012-10-19
Twipley,
I would really appreciate it if you could send me also a color scan at 75dpi and 600dpi for comparison.

---

### Post by aikishugyo on 2012-10-19
Hello Twipley,

Update:
1)I have constructed a PNM image from the 1200dpi color log you sent me, and it looks fine as it is, no artifacts that need to be taken care of in the code.
2) I won't need any other scans.

So, you should try the latest SANE, either 1.0.23 or the git source code, and see if you can scan at 1200dpi correctly.

Regards,
Gernot

---

### Post by twipley on 2012-10-19
> **aikishugyo said:**
> Thanks for the effort, it finally paid off.
Okay, great to hear! You're welcome. :)

> **aikishugyo said:**
> So, you should try the latest SANE, either 1.0.23 or the git source code, and see if you can scan at 1200dpi correctly.
I have lost possession of the scanner, but if anyone else wants to try it, they should note that selecting 1200-dpi scan in the options is not enough, as, for example Simple Scan, tries to pass off 600 dpi for 1200 dpi. What is needed is to really, as far as I am aware of, check that the 1200-dpi scan contains twice as much pixels in each axis, in comparison with the 600-dpi one.

I also cannot remember which driver quantal recommended by default. I think it was something beginning with the letter "g," but cannot ascertain that it was gutenprint. At any rate, I don't remember seeing anything relating to SANE. Recommended driver topped at 600 dpi for the actual scanning resolution, too, through the Simple-Scan frontend.

Cheers!
twipley

:popcorn:

---

### Post by aikishugyo on 2012-10-19
> **twipley said:**
> I have lost possession of the scanner, but if anyone else wants to try it, they should note that selecting 1200-dpi scan in the options is not enough, as, for example Simple Scan, tries to pass off 600 dpi for 1200 dpi. What is needed is to really, as far as I am aware of, check that the 1200-dpi scan contains twice as much pixels in each axis, in comparison with the 600-dpi one.

There is no limitation in the SANE library, it is simply stated in the SANE support webpage that 1200dpi does not work yet. This is clearly outdated, since it should work perfectly fine as no data manipulation is needed to compensate for this scanner.

What SimpleScan does I do not know, certainly in SANE there is no such thing as "passing off 600dpi as 1200", you simply cannot select higher resolutions than what is avaible on that device.

To be sure, you should use scanimage from the command line, or Xsane, to check whether you can get a 1200dpi scan. If you work from the commandline, even with Xsane (starting with xsane command) with the pixma debug variable enabled (man sane-pixma) you can send me the output (I know you don't have the scanner now) where I can check that the scanner received a command to scan at 1200dpi.

> **twipley said:**
> I also cannot remember which driver quantal recommended by default. I think it was something beginning with the letter "g," but cannot ascertain that it was gutenprint. At any rate, I don't remember seeing anything relating to SANE. Recommended driver topped at 600 dpi for the actual scanning resolution, too, through the Simple-Scan frontend.

I don't think there is any other driver than SANE, unless it is a proprietary one from Canon or some VueScan. You might be talking about the front-end.

---

### Post by twipley on 2012-10-25
Just for the info, I am installing that printer to where it belongs right now, and default (recommended) driver indeed is the "Canon PIXMA MP280 - CUPS+Gutenprint v5.2.9 [en]."

---

### Post by aikishugyo on 2012-10-25
> **twipley said:**
> Just for the info, I am installing that printer to where it belongs right now, and default (recommended) driver indeed is the "Canon PIXMA MP280 - CUPS+Gutenprint v5.2.9 [en]."

Great! Now, for the scanning. I am pretty sure there can still be a probem with SANE (either 1.0.23 or the CVS source). So I would appreciate if you could scan at 600 and 1200 dpi in SANE and let me know what happens: I suggest using scanimage from the commandline for now, but you may use xsane as well if you prefer.

---

### Post by freacert on 2012-11-01
> **aikishugyo said:**
> here the instructions to get and compile SANE from CVS. Yes, you probably need CVS SANE from git to get support for the newer scanners.

When you run sudo xsane (and accept the risk of running as root) then the console should show pixma module output, including the fact that it could not match the USB ID with any scanner model.

To get the CVS code, you need git installed. Then you can do inside a source direcftory (I usually use ~/src):

```
mkdir ~/src
cd ~/src
git clone git://git.debian.org/sane/sane-backends.git
```Reference: [http://www.sane-project.org/cvs.html](http://www.sane-project.org/cvs.html)

Go to sane-backends, and try to compile:
```
cd sane-backends
BACKENDS="pixma" ./configure
make
sudo make install
```I don't know if you will need some dependencies first (like gcc, some parsers maybe, etc.)

SANE is installed into /usr/local, so it does not overwrite the system SANE. But you may need to always run xsane as sudo to be sure that you access the new pixma libraries.

Regards,
Gernot Hassenpflug


Thanks  **aikishugyo, **Gernot, scan people for your time and effort!

two days working on 12.04 and now scanner issues. 
yes, i want XSane to work!! (stupid me)
Canon pixma mp280. 
Followed your steps, which made the canon scan under 10.04 a few months ago. Now I get this

```
:~/src/sane-backends$ xsane
[sanei_debug] Setting debug level of pixma to 3.
[pixma] pixma is compiled with pthread support.
[pixma] pixma version 0.16.2
[pixma] sanei_bjnp_find_devices:
[pixma] eth0 is IPv4 capable, sending broadcast..
[pixma] eth0 is IPv4 capable, sending broadcast..
[pixma] eth0 is IPv4 capable, sending broadcast..
[pixma] eth0 is IPv4 capable, sending broadcast..
[pixma] eth0 is IPv4 capable, sending broadcast..
[pixma] pixma_find_scanners() found 0 devices
xxx@xdx:~/src/sane-backends$ 

```no devices...  scanner turned on. 

uname -a 
```
3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux

```

---

### Post by aikishugyo on 2012-11-01
Hi,
It means the MP280 was not found by the network backend, apprently. Since the pixma driver is separate from the network backend, please connect directly via USB first, to deal with the actual driver.
After that, any problems with the network backend (special rules needed, perhaps) can be handled.
Regards,
Gernot

---

### Post by freacert on 2012-11-02
hello!
yes, eth0, strange, because the canon pixma MP280 is not a network printer, can only be connected by usb!

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 002 Device 002: ID 04a9:1746 Canon, Inc. 

```

---

### Post by aikishugyo on 2012-11-02
Hi,
Interesting :-) OK, so neither the network backend (the information is not relevant, it appears) nor the pixma backend found anything.
Hence I'm pretty sure you have done something wrong. I had a closer look at the current source code, and the pixma backend there is version 0.17.0, not 0.16.2 as in your case! So you are not using the source pixma backend... That means the MP280 is still declared as experimental in your current backend and will not be activated unless you choose the experimental debug option. I don't remember what that is, since it does not exist in the source code anymore (I could try to search the archives on the SANE ML, and you could find out by doing "man sane-pixma" on your system, but it is more productive to use the newer code).

Your best bet is to actually do what you copied/pasted in the instructions for getting and compiling/installing the source code, and making sure that your pixma backend is updated to version 0.17.0. Then the MP280 will be found.

As I don't know what you actually did in getting and installing the source code, please let me know if you had trouble compiling the code---I assumed from your previous post that you had done that without trouble.

Regards,
Gernot

---

### Post by freacert on 2012-11-02
> **aikishugyo said:**
> Hi,
I had a closer look at the current source code, and the pixma backend there is version 0.17.0, not 0.16.2 as in your case! 



yes, I see the same. Maybe because of the old 10.04 install i still had the sane-backends in the home folder (not in the src folder as you suggested)

> 
As I don't know what you actually did in getting and installing the source code, please let me know if you had trouble compiling the code---I assumed from your previous post that you had done that without trouble.

no faults, worked fine. 

have to go now. will try again in 12 hours. I hope. Were to get the 0.17 files?

thanks!

---

### Post by aikishugyo on 2012-11-02
"where to get the 0.17 files?"

In the source repository of course! that is what CVS means. Did you just copy and paste the instructions into the post, or did you actually execute them? If you can't compile the source code you can't use the new code. So prove that you downloaded, compiled and installed the source code please as per the instructions.

---

### Post by freacert on 2012-11-02
off course i did. 
did it again, because how to proof it?

some code 
```
-> Installation directories:
Configuration: /usr/local/etc
Libraries:     /usr/local/lib
Binaries:      /usr/local/bin and /usr/local/sbin
Manpages:      /usr/local/share/man
Documentation: /usr/local/doc/sane-1.0.24git
Lockfiles:     Feature is disabled!
-> Network parameters:
Build saned:   yes
IPv6 support:  yes
Avahi support: no
SNMP support:  no
CUPS support:  no
-> The following backends will be built:
pixma 
```


found something in the make file 

```
NOT overwriting pixma.conf in /usr/local/etc/sane.d...
NOT overwriting saned.conf in /usr/local/etc/sane.d...
NOT overwriting dll.conf in /usr/local/etc/sane.d...

```

can be that this is the cause of the problem. because i had an older version installed. Now i really have to go...

---

### Post by aikishugyo on 2012-11-02
I see the output of configure.
Did you do "make clean", "make", "make install" without problems?
If so, then you should be able to see the pixma version when you set debug environment variables and use sane-find-scanner, xsane or scanimage.
Since the installation goes into /usr/local, it will be chosen over any built-in system SANE version which may be older.

Take your time and send me the proofs of the proper installation without errors. You can email me at [email]aikishugyo@gmail.com[/email] if you need to.

---

### Post by LK_gandalf_ on 2012-11-03
Hi, I gave up using sane and other software, so I am trying to figure out if it is possible to use this scan with ubuntu for working purpose, or if it is necessary to reboot on windows.
I am using kubuntu 12.04 64bit, installed drivers from canon websites.
With Scangear, I have two problems and I wonder if you have the same:

a) colour: If i scan setting COLOUR or GREYSCALE I always get a page with a grey background, even if I scan a perfectly white page.
I got a white paper only if I scan black&white.

b) size:
for example, a document scanned with colour setting, A4 at 200dpi, weight  6 MB as pdf. It seems too much for me, especially because using the software from windows it weights much less.

If scanned in Black&white it weights only 50kb, but the quality is not suitable to scan working documents (CV, applications and other important documents). The result looks like a declassified file. If I scan it at 1200 (900kb) )it looks better, but still not like greyscale and not suitable for job applications, for example.

---

### Post by yusronhilmy on 2012-11-23
> **OostAchterhoek said:**
> Use new updated driver for scangear. (version 1.80) and scanning for Canon MP280 will work.

see this link:
[https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

good  luck !!
It works very well for Me.

Thank you !

---

### Post by LK_gandalf_ on 2012-12-04
I'm maybe very unlucky, but another serious issue I have is that I can only print with colours. Even if I manually choose the option "greyscale", it comes with colours. 
Do any of you have the same problem? 
I installed the drivers from the canon website, and tried to update them from the PPA linked above. I am desperate with this printer, I have to reboot on windows for every operation :mad:

---

### Post by pdc on 2012-12-04
can you copy and paste this command

> [COLOR="Red"]sudo dpkg -l | grep cnijfilter[/COLOR]

and copy and paste back the results .....it checks to see what driver you have installed...........

---

### Post by LK_gandalf_ on 2012-12-05
Thanks for helping. Here the output of the command:

```
ii  cnijfilter-common                               3.70.1-0~23~precise1                    IJ Printer Driver for Linux.

ii  cnijfilter-mp280series                          3.70.1-0~23~precise1                    IJ Printer Driver for Linux.
```

---

### Post by pdc on 2012-12-05
that's fine: so you have right drivers installed ......

so the ink etc must all be fine because it works in windows.....I don't know...........

.....and you have never edited the .ppd file?

for my MG3100 it is in etc/cups/ppd ............

---

### Post by freacert on 2012-12-05
> **LK_gandalf_ said:**
> I'm maybe very unlucky, but another serious issue I have is that I can only print with colours. Even if I manually choose the option "greyscale", it comes with colours. 
Do any of you have the same problem? 


Yes, I do have. 
I just started to install the printer, and noticed that any change in dpp or turning RGB colors to greyscale, does not print anything. Never had that problem before. 

Something to do with the new cups i saw flying by?

```
sudo dpkg -l | grep cnijfilter
ii  cnijfilter-common                             3.70.1-0~23~precise1                    IJ Printer Driver for Linux.
ii  cnijfilter-mp280series                        3.70.1-0~23~precise1                    IJ Printer Driver for Linux.

```

```
3.2.0-34-generic-pae #53-Ubuntu SMP Thu Nov 15 11:11:12 UTC 2012 i686 athlon i386 GNU/Linux
```


edit, extra information

With terminal -> system-config-printer no success either. 

Adding lines as described in [https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/](https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/)
printing in grayscale simply doesnot exist. Returning to the 3.40 drivers and editing like explained in this blog, is for me, untill now, the only way to print in grayscale.

---

### Post by LK_gandalf_ on 2012-12-07
I have never been able to print grayscale...even with previous drivers.

When printing, I can choose the option colour/greyscale available, but nothing changes.

---

### Post by freacert on 2012-12-07
LK_gandalf_
you will be able to print in grayscale if you follow the links in my previous post.

---

### Post by Marjinalist on 2013-01-22
I both installed scanner and printer driver shown above. I use Ubuntu 12.04 LTS Precise Pangolin.When I open Simple Scan utility appears "There is no Device for scanning or is not connected.Please check your device"...Please help me about that.Is there anybody to explain step-by step how to install all these and how to use that Scanner&Printer in ubuntu 12.04.I am getting mad now.It has to work in next 2 hours.If not I will be kicked from my work :) Pleaseeeee :):):):)

---

### Post by pdc on 2013-01-22
..can we check if you have scangearmp installed? It is the programme Canon supply to run your scanner ..

if you copy and paste 

> [COLOR="Red"]sudo dpkg -l | grep scangear[/COLOR] into a terminal (use the Menu/Edit option to paste)

and if it shows something like 

> [COLOR="Blue"]scangearmp-common                             1.80-1                                  ScanGear MP for Linux.
ii  scangearmp-mp280series                       1.80-1                                  ScanGear MP for Linux.[/COLOR]


....... you have scangearmp installed 

..........as in post #4 here

[http://ubuntuforums.org/showthread.php?t=2106604](http://ubuntuforums.org/showthread.php?t=2106604)

if you copy and paste 

> [COLOR="Red"]scangearmp[/COLOR]

into a terminal, and hit the ENTER key ......scangear should load;

......if you don't have it installed, I recommend you do and again; post #4 tells how

....... you can create a launcher ......to launch it each time: also see post #4 as to how to do this

---

### Post by LK_gandalf_ on 2013-01-23
I still cannot print in black&white or modify any setting, and the scanner creates files which are too big in size. To use the printer I switch on my netbook with windows7, where I have a lot of setting with Canon's software. It is quite sad, I must say.

---

### Post by pdc on 2013-01-24
Canon provide a utility to edit the printer settings ..it is called cngpij

if you type this into a terminal

> cngpij P MP280

I enclose a screenshot for my MG entitled grayscale

.......... you comment

> the scanner creates files which are too big in size

.....does the size change in scangear help?

---

### Post by LK_gandalf_ on 2013-01-25
Hi pdc and thank you for assistance.
Unfortunately the utility to change print setting doesn't work, I selected grayscale but nothing changed.

Yes the expected size change in scangear, but the problem is that I find it is much bigger than the windows version.
A grayscale document at 100 takes 600 kb in .pdf, but the quality is so low that it is not readable.
At 200 it jumps to 2,2 mb which is clearly too much. 

On windows I got 2mb for 3 pages coloured in .pdf, at a very good quality.

---

### Post by kouni on 2013-02-11
Hi,

My Canon mp280 isn't working properly: it does print, but the scanner isn't recognized, no matter what I do.

I've installed (and reinstalled)

scangearmp-common                             2.00-23~precise1                                ScanGear MP for Linux.
scangearmp-mp280series                        2.00-23~precise1                                ScanGear MP for Linux.

(i386)

and I've been trying to scan using Scangear/xSane/Simple Scan...

The scanner is simply not recognized. Scangear and xsane don't even launch, stating they can't find any scanner turned on.
Simple scan does launch, but says "no scanner", same message.

I've read this thread and I think I've done everything that is mentioned, but it is just not working.

Can anyone help me to solve this? Should I downgrade to scangear 1.80?

Thanks,

nic

---

### Post by pdc on 2013-02-11
hi kouni: welcome to the ubuntu forums.........

.........If you have installed scangearmp...... well done..

(and you can check the installation is good by copying and pasting the command below into a terminal)

> [COLOR="Red"]sudo dpkg -l | grep scangearmp[/COLOR]

.........then you launch Canon's programme to run your scanner...

.......which is called [COLOR="Blue"]**ScanGearMP**[/COLOR] .......

by firstly typing

> scangearmp

into a terminal and the programme should open ...

.....to run it in the future, one can create a launcher ..to launch it ..

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

the commands are

> [COLOR="Red"]sudo apt-get install gnome-panel[/COLOR]

and then 

> [COLOR="Red"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

..I enclose an image of the launcher in the thumbnail below ..

NAME: whateveryouwish_it_tobecalled

COMMAND: [COLOR="Red"]scangearmp[/COLOR]

.....in the future you are often best to start a new thread .........

---

### Post by kouni on 2013-02-12
Thanks for your reply pdc.

Scan Gear is properly installed and the launcher was automatically generated when I installed the program.

The point is, it keeps saying there is no available scanner connected to my computer, which is wrong.

Here is a screenshot (in French):
"Impossible to find any available scanner"
"Cable might be unplugged or your scanner might be switched off."
"Check it out and try again."

Then Scangear immediately shuts down once I click "OK": I have no access to any menu/option/setting whatsoever.

I thought it'd be better to use this thread, as this matter has previously been discussed with others.

So, I'd be grateful for any clue: should I downgrade to scangearmp 1.80? should I erase some hidden file in my system to make it work?

Thanks again,

nic

---

### Post by pdc on 2013-02-12
thanks for all this; you seem very fluent in what you are doing;

if you check what

> [COLOR="Red"]sane-find-scanner[/COLOR]

and 

> [COLOR="Red"]scanimage -L[/COLOR]

show and if you repeat these commands with [COLOR="Red"]sudo[/COLOR] before them.......

there have been several posts recently where scanners are not recognised; some where they were working well before; one does wonder if some recent software change has triggered some of this .....I have a Canon MG printer and scangear is fine with it ..

---

### Post by kouni on 2013-02-22
Thanks for these commands, pdc.

So, here is what I get:
To sane-find-scanner:
> # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x1746 [MP280 series]) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
To scanimage -L:
> No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).I get the same results with sudo.

I don't quite get it: could it possibly be a usb port access issue? Should I set some kind of permission?

Thanks for any help!

nic

---

### Post by aikishugyo on 2013-02-22
> **kouni said:**
> Thanks for these commands, pdc.
To sane-find-scanner:
To scanimage -L:

Hmmm, if you installed the Canon software, why are you using sane-find-scanner and scanimage to try and find it?!? For that to work, you would have to install the SANE drivers (which I am still trying to find someone for, so we can finally fix the 1200dpi issue).

As pdc wrote, scangearmp is what you need to run.

---

### Post by kouni on 2013-02-22
Hi aikishugyo,

I'm trying other softwares because I can't rely on scangear.
Actually, scangear is properly installed but won't start.

As mentioned in a previous message (a screenshot was included), each time I launch it, scangear says it sees no scanner connected and shuts down when I click "OK".

What's strange is, the terminal says it does see the scanner... So how come no software is able to see it?

---

### Post by aikishugyo on 2013-02-22
> **kouni said:**
> Hi aikishugyo,

I'm trying other softwares because I can't rely on scangear.
Actually, scangear is properly installed but won't start.

As mentioned in a previous message (a screenshot was included), each time I launch it, scangear says it sees no scanner connected and shuts down when I click "OK".

What's strange is, the terminal says it does see the scanner... So how come no software is able to see it?

Sorry, I'm not able to say anything about Canon software. I hope others can help. I just wanted to clarify that SANE-related programs will not detect the scanner for you if you don't have a SANE driver (probably the latest CVS) for the MP280.

---

### Post by kouni on 2013-02-22
Alright, the problem seems not to be linked with these software anyway.

I've found out that many people have the same terminal answer with various brands.

It is probably a libusb permission issue, it's more complicated than I thought. Got to find some threads on the matter...

---

### Post by LancerNZ on 2013-03-13
I've been using the canon MP drivers. Printer works, but the scanner says not found. However, if I run scangear_mp as root, there is no problem. For me, I think it's a permissions issue.

---

### Post by pdc on 2013-03-13
there are various topics on the issue

[http://www.tuxradar.com/answers/412](http://www.tuxradar.com/answers/412)

is this helpful?

---

### Post by LancerNZ on 2013-03-13
pdc thanks. That page didn't really match my Ubuntu system (files it asks me to list don't exist), nevertheless performing:
```
sudo gpasswd -a lancer lp
```
...then logging out & back in, did fix the issue and I can now scan as well as print as user "lancer".

---

### Post by pdc on 2013-03-14
that's great; you need to be a member of the lp group and now you are ....so the command did that for you;

---

### Post by kouni on 2013-03-14
So, I just tried again to launch scangear prior to trying this new command... and it worked.
I haven't done anything since I last tried to launch it (a couple of weeks ago, I think), but there has been an update or two, so I guess the issue has been fixed, great news!
Thanks for helping out anyway :)

---

### Post by pdc on 2013-03-14
sometimes computers have minds of their own; and perhaps your computer has entered a more mellow phase; enjoy

---

### Post by LK_gandalf_ on 2013-03-15
I still cannot print in black and white/greyscale, this happens from two different laptop with kubuntu 12.04 64bit. Anyone has the same issue?

---

### Post by pdc on 2013-03-15
Go back to post #133 and do what freart told you to do;

I enclose a thumbnail of the box one edits

---

### Post by LK_gandalf_ on 2013-03-16
Yes I did it time ago but unfortunately nothing changed. I could try to clean up everything and try again. I use drivers 3.40-1. Thanks!

---

### Post by jz77f on 2013-04-26
Ubuntu 12.04 64-bit, running on Asus 1225b.
Installed (via Ubuntu Software Center):
   cnijfilter-common-64 3.90-63~precise1
   cnijfilter-mp280series-64 3.90-63~precise1 (... seems to be a newer version than what is available on Canon website)
Tried:
   ScanGear - says "Cannot find available scanners" :(
   XSane 0.998 - says "no devices available" :(
   Simple Scan - says "No scanners detected" :(
   Gimp - says "Cannot find available scanners" :(

Note the printer works fine.
Help appreciated!

---

### Post by pdc on 2013-04-26
Hi there jz77f

> ScanGear - says "Cannot find available scanners" 

.............. so I'm wondering if you installed ScanGearMP?

You can get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html)

and when installed, you run it by

> [COLOR="#FF0000"]scangearmp[/COLOR] from a terminal, and for repeated use, you create a launcher ...........google to find how to do it

.........if you don't have ScanGear installed ............ it comes down as [COLOR="#008000"]scangearmp-mp280series-1.60-1-deb.tar.gz[/COLOR] .....let me know and I can give you the commands if you need them

---

