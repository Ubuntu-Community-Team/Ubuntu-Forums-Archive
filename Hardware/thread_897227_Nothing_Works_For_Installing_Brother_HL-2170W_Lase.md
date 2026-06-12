---
title: "Nothing Works For Installing Brother HL-2170W Laser Printer!!"
date: 2008-08-21
forum: Hardware
---

### Post by cbarnes48 on 2008-08-21
Sorry, can't wade through 408 pages this late at night. My problem is getting Ubuntu 8.04.1 to recognize and install my Brother HL-2170W Laser Printer which IS on the compatibility list!! :confused::mad:

When I look at the Documentation material on the official "Documentation for Unbuntu 8.04.1 LTS" page for the procedure to install my Brother printer, it doesn't work. Under "Printing" I click on "Local Printer," since this is the only printer or standalone one I have connected to my Acer Desktop PC via an **_Ethernet_** instead of USB cable.

With my printer plugged in and powered on, it is NOT automatically detected! NO printer icon appears in the Notification Area (where is this??). Then, I attempt to follow the remaining directions, which are:  

   1. Obtain the model name of your printer.
   2. Ensure the printer is turned on.
   3. Choose System &#8594; Administration &#8594; Printing
   4. Now choose New Printer.
   5. Your printer should be automatically detected. If so, simply click
      Forward and then Apply.
   6. Finally, you can enter in a description and location for your 
      printer.

If your printer was not automatically detected, you can try to select the port and printer driver manually - where and how do I do this, since the above procedure doesn't work?? Some printers need further setup. Search the databases at LinuxPrinting.org or check the Ubuntu Wiki's Printer page for possible information on your printer. When I click on the LinuxPrinting.org link I am redirected to a page with the following URL:  [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting). I click on the "Printers" button on the left-hand side of the page and fill in three fields from left to right that say:  "Show" the "Brother" and finally "HL-2170W" which my laser printer make and model ARE. :confused:

I am then sent to yet another page that says: "Brother HL-2170W
BW laser printer, max. 2400x600 dpi, works Mostly 	
Recommended driver: pxlmono (Home page, view PPD, download PPD)
Generic instructions for: CUPS, LPD, LPRng, PPR, PDQ, no spooler." At this point, I just give up and have no idea what to choose or do any more.

Can anybody help me or do I just uninstall Ubuntu, completely clean my one hard disk drive (160 GB SATA) and don't believe all the glowing praise and reports about/for Ubuntu's advantages??

Craig B.

---

### Post by Striker_XF35 on 2008-08-25
I just installed mine, heres how.
The file that you need to download is the .ppd (Postscript Printer Description) file. 
I got it from this page [http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W") 
Press the download PPD button.

Now that you have the file open the printing section and click "New printer"
Select the HL-2170W printer on the left and hit forward.
In the lower section it says "Provide PPD File" check that and browse to the file you just downloaded. Hit Forward.
Name the printer, and if you want you can add a few optional descriptions.

Click "Apply"

To test the install click on the printer name, make sure that it is set as the default printer, and print a test page.

If you run into problems, just post 'em here and I will see what I can do.
Striker_XF35 (PM's might get a faster response, idk)

---

### Post by thexaspect on 2008-08-26
cbarnes48:
From your description it sounds like you might have the printer directly connected to the pc with an ethernet cable, as you would with a standard usb printer. if this is the case, it could be a lot of your issue. With a network printer, you need a network, and something that can issue I.P. addresses like a router. I was actually just having a similar problem, since for some reason I can't get the same printer to print from windows at the moment, but my Hardy laptop works like a charm now. Go figure. 

As well, please don't confuse "Ubuntu's advantages and glowing praise" with a lack of proper driver support by hardware manufacturers. Ubuntu(and linux as a whole) works very well as an operating system, and even better than Windows with many things. But with certain uncommon hardware types, or new or bleeding edge pieces, it takes a bit for someone(generally much smarter than I) to figure out how to make it work with the least amount of hassles for those of us trolling the Ubuntu forums for howto's on everything, which is generally what I end up doing. Good luck with the printer =D

---

### Post by SebMKd on 2008-09-20
This thread is a life saver. Thanks Guys. Got my printer connected in less than 2 min!!!

1. Brother HL-2170W printer was already setup via my router using Windows
2. Went to [http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W) and downloaded the file. Saved it on Desktop
3. Went to System/Preference/Printer. Added one. Search for it and found it immediately. Pressed next.
4. Asked for a PPD file. Just browsed for it. Then the set-up took a few seconds and that's it.

I'm already printing as we speak! :guitar:

---

### Post by Dougo007 on 2008-10-17
I tried the PPD file and the pages that I print says "PCL XL error"

Error: IllegalTag
Operator:Oxel
Position:88818

I am using a USB cable

---

### Post by Striker_XF35 on 2008-11-01
I have not set up the printer using USB, but I can give you the best site I have at this point [http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2170W]("http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2170W")
If you are able to get anything out of that then please try, if not shoot me a PM and once I reinstall GRUB I will try and set it up using USB

---

### Post by pyromanic123boom on 2008-11-01
Follow the Brother Printer Guide here - [http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c](http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c). Although it says Brother MFC210C, just find the right cups and lpr drivers from the brother website. It explains everything in detail and gives you the link to the brother drivers.

---

### Post by alucard1589 on 2008-11-20
i have a problem with the same printer, but mines didn't be recognized by the wireless router and i cant print wirelessly; altought few days ago i can i do not whats wrong with the printer any help?

---

### Post by Striker_XF35 on 2008-11-20
While I don't know what is wrong with the printer from what you just said, I can tell you probably the easiest way to fix it.
[LIST=1]
[*]Reset the Printer- you can use the quoted instructions
[*]Setup the printer using the original instructions
[*]Have working printer, or post here with more details of your trouble
[/LIST]
[QUOTE=Brother Support Website]If you wish to reset the print server back to its default factory settings (resetting all information such as the password and IP address information), please follow these steps:

   1.
      Turn off the printer.
   2.
      Make sure that the front cover is closed and the power cord is plugged in.
   3.
      Hold down the Go button as you turn on the power switch. Keep the Go button pressed down until the Toner, Drum and Error LEDs light up. Release the Go button. Make sure that the Toner, Drum and Error LEDs are off.
   4.
      Press the Go button seven times. Make sure that all the LEDs light up to indicate the print server has been reset to its default factory setting.[/QUOTE]
This was found at [http://welcome.solutions.brother.com/BSC/public/us/us/en/faq/faq/000000/000100/000005/faq000105_012.html?reg=us&c=us&lang=en&prod=hl2170w_all]("http://welcome.solutions.brother.com/BSC/public/us/us/en/faq/faq/000000/000100/000005/faq000105_012.html?reg=us&c=us&lang=en&prod=hl2170w_all")

---

### Post by SeePU on 2008-11-21
Hello, sorry to interrupt the thread but I am looking for a laser printer, preferably a (built-in) network version.  It could be wireless.

I am wondering if you would recommend this printer.

I read some 'how-to's on how to set this particular printer up.  I agree, the OpenPrinting website and Brother's site (i.e. Brother Solutions Center) are steps in the right direction.

It seems quite a few procedures are needed to set up this printer for Ubuntu/Linux.

I was wondering if a Samsung or Lexmark laser would be easier.  However, I found the same model of Brother available for cheaper than the other two, although, it seems to need a bit of work to set up.  

If you already have this printer and have been using it for a while in Ubuntu, does it keep working?   Are the drivers decent?  Any issues?   Would you recommend it to others?  

Thanks.

---

### Post by Striker_XF35 on 2008-11-22
First, I would recommend this printer.
That said, I have no experience with the other options, both network printers in the household are Brother brand.
After talking with my older brother who is a systems administrator for a local ISP, I would recommend that if you are looking for a network printer Brother works well.
While there are a number of setup steps, most of them you will have to go through whatever network printer you decide to buy.
I am including the link to the page for the PPD file again for easy access, also the page includes fairly detailed instructions on how to setup the printer in most configuration's.
[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W]("http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2170W")
One thing to throw out there is that while when this thread was created I had the printer set up through a wireless router, now it goes through a Ethernet hub first with about the same level of ease.
Striker_XF35
(If you found this helpful, you can click the "Thanks" button - I like being thanked)
EDIT: I do also need to mention that I dual-boot with Crapdoze XP as primary OS due to the amount I game, therefore there may be issues with this printer in ubuntu that I have not seen.
Also,  be aware that almost any network printer will require about the same amount of setup, they just have a program on CD that helps ease setup in windows.

---

### Post by flymw on 2008-12-04
> **SeePU said:**
> Hello, sorry to interrupt the thread but I am looking for a laser printer, preferably a (built-in) network version.  It could be wireless.

I am wondering if you would recommend this printer.

I read some 'how-to's on how to set this particular printer up.  I agree, the OpenPrinting website and Brother's site (i.e. Brother Solutions Center) are steps in the right direction.

It seems quite a few procedures are needed to set up this printer for Ubuntu/Linux.

I was wondering if a Samsung or Lexmark laser would be easier.  However, I found the same model of Brother available for cheaper than the other two, although, it seems to need a bit of work to set up.  

If you already have this printer and have been using it for a while in Ubuntu, does it keep working?   Are the drivers decent?  Any issues?   Would you recommend it to others?  

Thanks.

Hello SeePU,

**I do also recommend this printer** for many reasons:

I have been using a few Brother Printers over the last 7 years and always been very satisfied. Never had ANY problem whatsoever! I did try out a Samsung with similar specefications but did not like it as much as the brother. At work I also have to deal with a Samsung and it is not as nice to work with under Ubuntu as the HL2170W.

**Setup** was very easy for me under Ubuntu Hardy and has become even easier under Intrepid because the driver is already included in the database and works fine. I have to admit I used one trick for the initial setup - when I connected the printer to my router via LAN cable the router would not find it (don't ask me why) since I have a very rarely used windows partition on my desktop I just simply booted into windows and used the included windows setup CD, configured everything and then the printer had its own IP adress (also via WLAN) and I easily installed it under Ubuntu. With this slightly dirty trick everything was very easy - probably it would not have been too difficult one a pure Linux system but I was just too lazy to search for the answer.

I do also like the very flawless Linux support by Brother even if it includes a bit of command line - the steps are simple even for beginners and work straightforward. Unlike the brother the Samsung printer at work (SCX-6345N - try searching for that printer on the Samsung website, due to their poorly created website you will have a hard time navigating and I did not find the printer and associated driver for hours and needed some tricks for finding the driver download) even offers an install script including support for Ubuntu. Well, with me the system crashed from the install script (and the printer was not correctly installed) - again with a lot of hassle I managed to get a halfway functioning manual installation of the Samsung but the Brother was just so much faster and more straightforward!

**Conclusion:** I have long good experience with Brother printers and since I have changed to Ubuntu 6 months ago never had any problem (none on Windows the years before either). Installation was straightforward with me, even as a new Ubuntu user.

I hope this will help your decision.

---

### Post by flymw on 2008-12-04
Here a little wiki of how I installed the printer on my Ubuntu 8.04 Hardy, in case this might help anybody. I tried to keep it simple:

1. Pairing with wlan router (should only be required the first time use - maybe you can omit this step? But it helped me):

install via Windows and the accompanying CD
(use installation via LAN cable according to the printer manual)
note MAC (e.g. 00:1E:F1:4F:F9:5A) , IP (e.g. 192.168.0.5) and NODENAME (e.g. BRW001FE14FF85A) (not really necessary but it can't hurt to know them)

2. installing under Ubuntu

*note: under Ubuntu 8.10 Intrepid I could just install the printer easily via the Printers GUI: System-System administration- Printers-search for new printers and the HL-2170W will show up in the list and the drivers are already included.*

(see [http://solutions.brother.com/linux/en_us/before.html](http://solutions.brother.com/linux/en_us/before.html) for other distributions)

(1)
```
    1.  sudo aa-complain cupsd
    2.  sudo mkdir /usr/share/cups/model
    3.  sudo mkdir /var/spool/lpd
```	(command is required if the folder does not exist)

(2)
   download lpd and cups drivers:
```
wget http://solutions.brother.com/Library/sol/printer/linux/dlf/brhl2170wlpr-2.0.2-1.i386.deb
wget http://solutions.brother.com/Library/sol/printer/linux/dlf/cupswrapperHL2170W-2.0.2-1.i386.deb
```

If this doesn't work or you are not using Ubuntu or any other Debian system download the drivers from [http://solutions.brother.com/linux/en_us/download_prn.html#HL-2170W](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2170W) (deb version for Ubuntu)

(3)
  1.  ONLY if you downloaded the drivers manually go to directory in which you downloaded the files (e.g. cd /Desktop), if you used my wget commands unchanged you should already be in the correct directory as the files were downloaded to the current directory

then install the drivers:
```
sudo dpkg  -i  --force-all  --force-architecture  brhl2170wlpr-2.0.2-1.i386.deb
sudo dpkg  -i  --force-all  --force-architecture  cupswrapperHL2170W-2.0.2-1.i386.deb
```
You might have to replace the driver filenamed in case you downloaded them manually and the filename is different, if you are unsure, just copy and paste my commands.
(4)
  ```
ping 192.168.0.5
``` (***replace this with your IP adress you noted before!!!*** -to make sure printer is installed correctly... stop with CTRL+C)

(4)
  1. in web browser open [http://localhost:631/printers](http://localhost:631/printers)
  2. Click "Modify Printer"
  3. when promted enter the following:
  	LPD/LPR Host or Printer			Device
  	lpd://(192.168.0.5)/binary_p1	Device URI (***replace this with your IP adress you noted before!!!***)
  	confirm with Linux username and password

DONE!

to access the printer settings: [http://192.168.0.5](http://192.168.0.5) 
	username: admin
	password:  access
		or
		username: user
		password:

---

### Post by Bupkus on 2008-12-12
I followed the directions by Strker's original post and it worked like a charm. \\:D/
I believe I selected the "LPD/LPR Host or Printer" option when it appeared.
I also think I had to provide the ip, but I got that by viewing the attached hardware in my router. 
Note: this printer was being used by my XP partition before I installed Ubuntu 8.10. Hence, I knew it was working.

---

### Post by SeePU on 2008-12-14
Is the Brother HL-2040 just as easy to set up?  It can be set up on a Network, too, I assume.  Using a router/ip address?

The HL-2170W is over double the price, unforunately.

---

### Post by vinay427 on 2009-04-11
On 9.04 when I click on the printer on the left it just searches for new drivers and installs it automatically.  i didn't have to download anything.  The test page came out fine.  I'm using Ethernet for both the computer and the printer.

---

### Post by zacktu on 2009-04-11
I recommend this printer very highly.  If you want a laser printer that prints just black on white, this is a good one.  It's also just about the most economical that you'll ever find.

The initial installation with Windows was a pain.  The nuisance part is to get the router to assign the printer an ip address.  Once that's done, any additional installations go fast.

The linux installation was easy  because it came after the Windows installation. I got the linux driver for my HL-2170W by installing foomatic-db from synaptic, selected "Add Printer", found the Brother printer, and then selected the driver from the list that was shown.

By the way, I have since reinstalled Windows.  This time around the printer was easy to install.  It already had an ip address, so installation under Windows was just as easy as the linux installation had been.

Some reviews of the printer were highly critical of the short lifetime for the laser cartridge.  You can bring up a webpage at the printer's ip address (user name and password are in the user manual) and set the default for printing to draft (don't remember the exact term).  I think that I've gotten very good service at that setting.

In short, I think it's a good printer.  I think that the first installation under any OS will be a pain, however.

---

### Post by vinay427 on 2009-06-06
I said two posts up that it printed a test page fine.  It still does, but I just found out that it can't print any other file (.pdf, OpenOffice files, etc.).  Only a test page works.

---

### Post by j0eb0b on 2009-07-08
Same problem, my HL 2170W is connected wireless to a router and works using both wireless and ethernet accessfrom 3 MS OS systems.  When I install the printer under 9.04, Ubuntu found and correctly identified the printer when I submitted the IP address assigned to the printer by the router.  Out came a test page.  Now nothing else will print and when I put the mouse over the printer icon it says "not connected"

Ideas?

---

### Post by malibusurfer2 on 2009-07-09
What is the script needed to send a command in a Terminal window to set the Sleep Time for a Brother HL-2170W printer? 

??? Sleep=1minute ???

---

### Post by vegmunky on 2009-08-14
I did nothing special.  I downloaded nothing special.  The only precondition was that I already had the printer installed on my network and have been using it from other computers for months.  Here was my entire process for installing it wirelessly on my laptop:

1. Install Ubuntu 8.04 on a new computer
2. Upgrade to Ubuntu 8.10
3. Click System -> Administration -> Printing -> New
4. Highlight "Other"
5. Enter "ipp://BRW001E4C9145F7" (I got device name by looking at my DHCP routing table)
6. Click Forward
7. Under "Makes" select "Brother"
8. Click Forward
9. Under "Models" select "HL-2170W"
10. Click Forward
11. Click Apply

Then I printed a document from Google Documents.  No problems whatsoever.

---

### Post by vegmunky on 2009-08-17
> **vegmunky said:**
> I did nothing special.

I lied. I did something special: I turned off my brain. If you turn on the printer BEFORE you let the Add Printer tool search for it, it just finds it. Then click Forward, Forward, Forward, and you're done. I'm an idiot. My apologies. :(

---

### Post by anunn2001 on 2009-08-17
This won't help your problems but I have this printer and it works via wireless from two different Ubuntu 9.04 machines and all I did was discover it using the native printer installer of Ubuntu. Nothing else was required.

The only anomaly I have seen is problems printing selected pages of the Full circle Magazine PDF magazine. All other PDF files work just fine so i think it must be something peculiar to the Full Circle Magazine PDF files.

---

### Post by neilevan814 on 2009-10-15
I read a review on amazon about the short life span of the cartridge and all he did to fix it was tape a peice of opaque tape to one of the ends of the cylinder.  The cylinders a transparent and the printer is reading the level of toner this way.

---

### Post by jlanawalt on 2009-12-02
Mostly stumble-free in Ubuntu 9.10 (Karmic) for an Ethernet connected HL-2170W. 

[LIST=1]
[*]gksudo system-config-printer [0]
[*]Click New
[*]Expand Network Printer
[*]Choose Brother HL-2170W (nnn.nnn.nnn.nnn) instead of (BRN001SERIAL) [1]
[*]Expand Connection at the bottom of the right half of the window if it didn't pick the method you want.
[*]Choose LPD or AppSocket/JetDirect network printer via DNS-SD [2]
[*]Forward
[*]Print test page. Done.
[/LIST]

[0] I don't remember if this system is a fresh install or an upgrade, but I seem to be affected by [bug 387970]("https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/387970").
[1] I didn't try the (BRN001BA*) one that was going to use BINARY_P1 queue.
[2] I wanted to use the IPP option and tried it first but no dice. The other two options worked so I stuck with LPD network printer via DNS-SD.

It was nice to have avahi/zeroconf going to see the printer's address and then browse it's web interface and to have the setup work so easily without needing to fire up an MS Windows system first or change anything in the web interface.

---

### Post by xi_Slick_ix on 2009-12-09
> **flymw said:**
> Here a little wiki of how I installed the printer on my Ubuntu 8.04 Hardy, in case this might help anybody. I tried to keep it simple:

1. Pairing with wlan router (should only be required the first time use - maybe you can omit this step? But it helped me):

install via Windows and the accompanying CD
(use installation via LAN cable according to the printer manual)
note MAC (e.g. 00:1E:F1:4F:F9:5A) , IP (e.g. 192.168.0.5) and NODENAME (e.g. BRW001FE14FF85A) (not really necessary but it can't hurt to know them)

2. installing under Ubuntu

*note: under Ubuntu 8.10 Intrepid I could just install the printer easily via the Printers GUI: System-System administration- Printers-search for new printers and the HL-2170W will show up in the list and the drivers are already included.*

(see [http://solutions.brother.com/linux/en_us/before.html](http://solutions.brother.com/linux/en_us/before.html) for other distributions)

(1)
```
    1.  sudo aa-complain cupsd
    2.  sudo mkdir /usr/share/cups/model
    3.  sudo mkdir /var/spool/lpd
```	(command is required if the folder does not exist)

(2)
   download lpd and cups drivers:
```
wget http://solutions.brother.com/Library/sol/printer/linux/dlf/brhl2170wlpr-2.0.2-1.i386.deb
wget http://solutions.brother.com/Library/sol/printer/linux/dlf/cupswrapperHL2170W-2.0.2-1.i386.deb
```

If this doesn't work or you are not using Ubuntu or any other Debian system download the drivers from [http://solutions.brother.com/linux/en_us/download_prn.html#HL-2170W](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2170W) (deb version for Ubuntu)

(3)
  1.  ONLY if you downloaded the drivers manually go to directory in which you downloaded the files (e.g. cd /Desktop), if you used my wget commands unchanged you should already be in the correct directory as the files were downloaded to the current directory

then install the drivers:
```
sudo dpkg  -i  --force-all  --force-architecture  brhl2170wlpr-2.0.2-1.i386.deb
sudo dpkg  -i  --force-all  --force-architecture  cupswrapperHL2170W-2.0.2-1.i386.deb
```
You might have to replace the driver filenamed in case you downloaded them manually and the filename is different, if you are unsure, just copy and paste my commands.
(4)
  ```
ping 192.168.0.5
``` (***replace this with your IP adress you noted before!!!*** -to make sure printer is installed correctly... stop with CTRL+C)

(4)
  1. in web browser open [http://localhost:631/printers](http://localhost:631/printers)
  2. Click "Modify Printer"
  3. when promted enter the following:
  	LPD/LPR Host or Printer			Device
  	lpd://(192.168.0.5)/binary_p1	Device URI (***replace this with your IP adress you noted before!!!***)
  	confirm with Linux username and password

DONE!

to access the printer settings: [http://192.168.0.5](http://192.168.0.5) 
	username: admin
	password:  access
		or
		username: user
		password:

Is the Device URI listed in **step 4** actually literally Device URI or am I just being extremely small minded here?  

I got everything else up until this step.  The printer was set up under windows, wireless, fixed IP address.  It is showing up properly in the 631 port url as well.

---

### Post by Maximus_ARNP on 2010-03-26
[Click Here to get the guide ]("http://welcome.solutions.brother.com/bsc/public_s/id/pdf_pub/faq/faq002519/wireless_wcable_hl2170w.pdf")to reset printer to factory configuration and setup printer on your wireless network.

Now, do as follows to setup printer on Ubuntu 9.10 to work via wireless mode.


=============================================

System >>> Administration >>> Printer
New >> Printer
....wait...
Network Printer >>> Find Network Printer

In the **_host_**, enter the IP address (for me, it is 192.168.1.7) of your Brother HL 2170w and then press "Find". Find produced two results for me: (1) Brother HL-2170w (2) 192.169.1.7

I tried to setup using 1st choice, it did not work.

I selected 2nd choice (192.169.1.7). Nothing changed in "Queue" or "Connection".

Press "Forward"

Next screen "Apply".

Print a test page.

Finish.

====================
Enjoy.

---

### Post by Jon424 on 2010-08-11
**Setup** was very easy for me under Ubuntu Hardy and has become even easier under Intrepid because the driver is already included in the database and works fine. I have to admit I used one trick for the initial setup - when I connected the printer to my router via LAN cable the router would not find it (don't ask me why) since I have a very rarely used windows partition on my desktop I just simply booted into windows and used the included windows setup CD, configured everything and then the printer had its own IP adress (also via WLAN) and I easily installed it under Ubuntu. With this slightly dirty trick everything was very easy - probably it would not have been too difficult one a pure Linux system but I was just too lazy to search for the answer.

I do also like the very flawless Linux support by Brother even if it includes a bit of command line - the steps are simple even for beginners and work straightforward. Unlike the brother the Samsung printer at work (SCX-6345N - try searching for that printer on the Samsung website, due to their poorly created website you will have a hard time navigating and I did not find the printer and associated driver for hours and needed some tricks for finding the driver download) even offers an install script including support for Ubuntu. Well, with me the system crashed from the install script (and the printer was not correctly installed) - again with a lot of hassle I managed to get a halfway functioning manual installation of the Samsung but the Brother was just so much faster and more straightforward!

[/QUOTE]

I dont even know if I will get an answer, but I truly wish I do...
im trying to connect the samsung printer you are talking about in ur answer... [B]SCX-6345N 
but I need the drivers, whom are nowwhere to be found
im an average user, but I didnt set up the network, and im a little confused.
using ubuntu 10.04 on a wlan
anyone an help? :S
[/B]

---

### Post by jason_m on 2010-08-19
Did something change between 9.10 and 10.04?  I no longer am prompted for a PPD file when setting up the printer (Brother 2170w).

Previously (9.10) I followed Striker's instructions and my printer worked very well.  Now (10.04) going to System->Printers, then Server->New->Printer, my printer shows up under Network Printers.  I select it and press Forward.  From there I am taken to the final screen where I can modify the name/description of the printer.  But nowhere did I provide the PPD file.

A test page prints out fine, but anything else seems to get stuck spooling for a very long time.  I had a 6 page document spooling for 30 minutes before I canceled it.  It was 49% done spooling at the time.  I have seen a handful of other similar complaints, but no solution.

Am I missing something?  Or does anyone have updated instructions for 10.04?

Thanks,

---

### Post by Johansen on 2010-10-07
something is very wrong here*

same problem, although it never worked under 9.10 for me so i dunno.

it took *an hour* to print out some directions off google, i was uploading 25kb/s to the printer the whole time

defaults, 10.04 discovers it fine and downloads a driver *somewhere*, but if you disconnect the printer and dhcp assigns it a new ip address, ubuntu wont find it again, even though it should be able to, so you will have to go back, delete the printer and discover it again.

* i cannot reply to this thread in firefox, but can in chrome.. did they *update* that too? -must be a noscript problem.

---

### Post by Kittykathy on 2010-11-26
See my reply here for installing Brother HL-2170W Laser Printer.

[http://ubuntuforums.org/showthread.php?p=10161743#post10161743](http://ubuntuforums.org/showthread.php?p=10161743#post10161743)  

Scroll down to kittykathy.

---

### Post by Maximus_ARNP on 2010-11-28
Check out my following post to setup your printer.

[http://ubuntuforums.org/showthread.php?p=10174567#post10174567](http://ubuntuforums.org/showthread.php?p=10174567#post10174567)

Enjoy.

---

