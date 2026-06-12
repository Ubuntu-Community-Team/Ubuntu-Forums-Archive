---
title: "Need help installing HP Officejet 6500"
date: 2009-06-09
forum: Hardware
---

### Post by Prince Valiant on 2009-06-09
Hello,

I'm trying to install a HP Officejet 6500 e709n on an IBM R51 Thinkpad, under Ubuntu 8.10 (I had problems with Jaunty).  I have the driver disk, but don't know how to get a PPD file off of it; the list of 'default' drivers doesn't include the Officejet 6500.  

How can I install both the printer *and *the scanner?  

Thanks in advance!

-Val

---

### Post by Prince Valiant on 2009-06-12
Anyone?

---

### Post by briguy47 on 2009-06-12
> **Prince Valiant said:**
> Hello,

I'm trying to install a HP Officejet 6500 e709n on an IBM R51 Thinkpad, under Ubuntu 8.10 (I had problems with Jaunty).  I have the driver disk, but don't know how to get a PPD file off of it; the list of 'default' drivers doesn't include the Officejet 6500.  

How can I install both the printer *and *the scanner?  

Thanks in advance!

-Val

I wasn't able to locate a ppd file by itself, for that specific printer.  But it looks like that model is supported under HPLIP.  Here is the download link: [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

I went ahead and downloaded the tarball and extracted the attached ppd files.  One of them was listed under HPIJS and the other under HPCups-->HPIJS.  You might want to give them a try.

I hope that helps!  :D

---

### Post by Prince Valiant on 2009-06-15
Thanks a whole lot, briguy!  I'll try this as soon as I can!

---

### Post by briguy47 on 2009-06-15
My pleasure.  Just let me know how it goes and if you need any more help with it.  :D

---

### Post by Prince Valiant on 2009-06-17
Briguy,

I followed the link you gave and downloaded HPLIP; followed the instructions to install and configure, and now the printer works like a charm!

I'm not sure how to scan, though-- any ideas?

Thanks a whole lot!

-Val

P.S.  Since I configured the printer with the USB cable attached, I've now got four printers installed...wireless and USB Officejet 6500's, and wireless and USB Officejet Faxes.  How can I place a document in the scanner, and output a digital copy to my computer? Thanks!

---

### Post by varun.net on 2009-06-27
Hi Val,

Please let me know if you were able to install the scanner successfully.
I am planning to buy this printer.

Also if you can please tell me how is the printer/scanner working? and is the wireless feature accessible in linux?

Thanks

---

### Post by Prince Valiant on 2009-06-28
Hey Varun.net,

Yes, I was able to successfully install this printer *and* the scanner. :D  Since I wasn't originally sure what to do with the downloads that Briguy provided, I went ahead and downloaded the HPLIP from it's website.  From there, I followed it's installation instructions and installed the printer flawlessly.  The wireless works great; but be warned-- just like in Windows, you'll have to connect via USB once for setup before the wireless can be used.  

The scaning also works wirelessly.  If you go to Applications--> Acessories--> HP Device Manager, then you'll see pretty easily how to send faxes, scan wirelessly, etc.

The printer works great, and I really like it!  Hope this helps!

-Val

---

### Post by varun.net on 2009-06-28
Thanks Val,

I hope you are not from HP.

I will go ahead and purchase the printer.

-Varun

---

### Post by 0pul3nce on 2009-06-28
lol be wary he works for Hp and this is a marketing plot.

---

### Post by Prince Valiant on 2009-06-28
Don't worry- I'm not.  :)

-Val

---

### Post by LinuxBob on 2009-08-17
Do you have to download & install HPLIP on every ubuntu machine you want to access this printer over the LAN?

---

### Post by rolleander on 2009-09-04
> **LinuxBob said:**
> Do you have to download & install HPLIP on every ubuntu machine you want to access this printer over the LAN?

That's a good question - I just bought this printer tonight after my cruddy lexmark died - I just installed mine by downloading the .run file off of hp's hplip website -
then opened a terminal and typed 

./hplip-3.9.8.run

everything installed automatically - just had to follow a few prompts, but everything worked - fax, scanner, printer - now I'm about to try to share the printer on my network and let you know if there's a need to install hplip on the other machine

---

### Post by rolleander on 2009-09-04
Weird - I went to go and try to install the printer on my fiance's netbook after making sure to click sharing and then to my surprise it was already set to use the printer - i didn't even play with the settings at all, but then I realized that the EEEpc already has hplip on it - so I don't know if that's the reason, but I have no other machine to test on...

---

### Post by heatherm on 2009-10-01
I bought the hp officejet 6500 wireless and can print/scan w/ usb connected but not wirelessly... I used the Tools on the printer to connect to the router but still no luck.
Also if I hit scan on the printer I get, on the printer, Scan Menu  (and below that) Select Computer >
Ideas???

Thank you!!

---

### Post by blue-box on 2009-10-20
I just purchased the HP Officeject 6500 and installed it using the installer from HP's website:

[http://hplipopensource.com/hplip-web/models/officejet/officejet_6500_e709n.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_6500_e709n.html)

I simply followed the instructions and was able to print and scan right off the bat.  

Because I plugged this into the network, I did have to use the "setup" button on the printer which allowed me to navigate to a screen for printing out the "HP Network Configuration Page".  This gave me the IP address to use with HP's setup application.

I have ubuntu 9.04.

Hope this helps someone...

---

### Post by rmetzger on 2009-12-26
I've been able to install the printer and get all the functions to work via the USB cable but the wireless doesn't seem to be functioning.  I run the wireless setup and it goes through the steps without error and lists that it is working correctly but I'm never able to print without the USB cable plugged in.  Is there a step I'm missing?

---

### Post by rmetzger on 2009-12-26
nevermind - I had to establish the connection via the printer setup menu first then go through administration printers to finish the connection

---

### Post by dshimer on 2010-01-21
One more ditto on the success. 9.04 and E709a (wired network)
[LIST=1]
[*]Put the printer together, plugged in the ethernet and restart the printer.
[*]Use the HBLIP install wizard to build the driver [http://hplipopensource.com/hplip-web/install_wizard/index.html]("http://hplipopensource.com/hplip-web/install_wizard/index.html")
[*]Download and run according to instructions.
[*]It asked to restart the computer, OK.
[*]Use Applications > Accessories > HP Device Manager to finish the process.
[*]Printer works great, scanner works great via Xsane and GIMP.
[/LIST]
I just followed the directions, and never needed to enter any settings manually or use a usb cable which is probably required to set up the wireless on that model.

I also went through the exact same procedure on 9.10 Karmic and had the identical results. The only difference was that this computer is a laptop with a slow wireless card and after the restart when I ran the HP Device Manager and it prompted me to "setup devices" I had to bump up the timeout on the device discovery process to 10 seconds. Though this might have also been because the device was idle. In any event after it tried discovery and said "No Devices Found", I hit "Back", opened the "Advanced" settings, bumped up the timeout, and tried again. Success.

---

### Post by mlsmith on 2010-03-12
Thanks, worked like a charm. Had a problem with Ubuntu Koala finding the printer, this fixed it after a reboot of the server.

---

### Post by paranoidp on 2010-04-13
Another tip that may help: I was able to configure all the wireless settings from the LCD touchscreen on the printer. I got it to work without ever plugging in via USB or Ethernet... a little tedious typing in the wireless network passphrase, but it did work.

---

### Post by taquito on 2010-08-07
Also, for those having trouble scanning:

I'm also having the issue where, if I press the "scan" button on the printer itself, I just get the "select computer" prompt, and haven't quite figured out a way to progress from there.

*However,* if I start XSane Image Scanner on my computer and start the scan from there, I can scan no problem.

---

### Post by teeleef on 2010-11-15
Taquito,  did you ever get the scanning function to work wirelessly?

I've just set up my friends OfficeJet 6500 and I cannot get it to scan via the printer at all?



Teeleef

---

### Post by sanitair on 2010-12-07
I just finished to install office jet 6500 Wireless. This is done on Ubuntu 10.04.

All I needed to do is to install HPLIP Toolbox,  HPCUPS and HPIJS from Ubuntu software center. I then connected the printer to the computer using the USB and it is automatically detected by the software.
From (System/Preferences/HPLIP Toolbox) menu you will see a dialog with two icons on the left one for the fax and another one for the printer. If you select the printer you will see scan as one of the options. Also you can use any other scanner software available on the software center like XSan Image scanner. 

If you have also a Home network using a wireless router you will be able to connect the printer to the network and if you are connected your computer to the network even wirelessl, you will be able to print, scan, and send fax to any number. 

All you need to do is to add the printer as a network printer from (System/Administration/Print) menu. from there you will be able to select add button and from the dialog selct network printer. in the host field put the IP address which was assigned automatically to the printer (you get it from the print page test from network settings on the printer product itself). Then the rest is easy and now you are connected to the printer / scanner through the network. I loved this device. .. and BTW am not working for HP, I am working for IBM ;)

Ahmed

---

### Post by Coley Gross on 2010-12-19
I f you have your usb cord plugged into your printer and ***puter you should have little to no problem installing on a "current versiou n" of ubuntu or other variant like 10.10 or 10.4

Also press setup on your printer then 8 and use the <OK> right arrow to cycle through dsl routers wifi transmission of their SSID (name) and log on. If you have say WPA2 personal setup your hp6500 will ask you to enter the key or phrase, do it with the keyboard just like you do with a cell phone.

(Make sure your ***puter is logged into your router (and you can laod any pg on u browser) Now load your printer drivers add option, click ADD PRINTER it will scan your IP address say 192.168.10.1 then it will lock on to your printer as a rather long name like Oficejet 6500 e709n (tick the one ending in n you may see its ip address say 192.168.10.10 if u r given 2 option for drivers hpijs, 3.10.2 pick it I've not used CUPS yet (but I love CUPS) with this printer you can skip hpcups3.10.2 highlight hpijs then tick FORWARD You'll see it and a blank for like "LIVING ROOM" Depending on your version of linux based on ubuntu debian you may have to select HP then scrool way down to Officejet 6500 and select it again (don't ask me why) Note your printer is usually on port 9100 if your asked for a port. A simple program I downloaded  YLMF (made to look as much like Windows XP (but based on Ubuntu-debian) makes it so easy. YOU NEVER HAVE TO PROVIDE A PPD file! Worst case you might need to type in a) the printers IP address (you can find its address in your router pages)  or B) the name you gave your printer like hp-6500 (this makes it so much easier to look at ink levels or scan via network rather then trying to always remember the ip address) or worst case click AppSocket/HP/JetDirect and it will download all drivers I suppose HP ever made, at least it takes a long time but the correct driver is avaiable Forward or finish and your done. Remember the Lite or Move or run from cd don't hold the setttings. PS I loved the 6500 so much I bought a second (built like a Sherman tank you dont see that kind of quality these days, heavy as heck!) HP6500 named hp-6500-2 When I add the next 6500 it appears right after I click add printer then under network printer I CLICK aPPsOCKET/hp jETdIRECT AND Bingo the 2nd printer is there all I give it is a name (glossy paper printer) I am a sloppy writer but I hopoe this might have helkped.

> **teeleef said:**
> Taquito,  did you ever get the scanning function to work wirelessly?

I've just set up my friends OfficeJet 6500 and I cannot get it to scan via the printer at all?



Teeleef

---

### Post by Coley Gross on 2010-12-19
I answered the wrong question LOOK AT THE BOTTOM FOR HOW TO SCAN.
> **Coley Gross said:**
> I f you have your usb cord plugged into your printer and ***puter you should have little to no problem installing on a "current versiou n" of ubuntu or other variant like 10.10 or 10.4

Also press setup on your printer then 8 and use the <OK> right arrow to cycle through dsl routers wifi transmission of their SSID (name) and log on. If you have say WPA2 personal setup your hp6500 will ask you to enter the key or phrase, do it with the keyboard just like you do with a cell phone.

(Make sure your ***puter is logged into your router (and you can laod any pg on u browser) Now load your printer drivers add option, click ADD PRINTER it will scan your IP address say 192.168.10.1 then it will lock on to your printer as a rather long name like Oficejet 6500 e709n (tick the one ending in n you may see its ip address say 192.168.10.10 if u r given 2 option for drivers hpijs, 3.10.2 pick it I've not used CUPS yet (but I love CUPS) with this printer you can skip hpcups3.10.2 highlight hpijs then tick FORWARD You'll see it and a blank for like "LIVING ROOM" Depending on your version of linux based on ubuntu debian you may have to select HP then scrool way down to Officejet 6500 and select it again (don't ask me why) Note your printer is usually on port 9100 if your asked for a port. A simple program I downloaded  YLMF (made to look as much like Windows XP (but based on Ubuntu-debian) makes it so easy. YOU NEVER HAVE TO PROVIDE A PPD file! Worst case you might need to type in a) the printers IP address (you can find its address in your router pages)  or B) the name you gave your printer like hp-6500 (this makes it so much easier to look at ink levels or scan via network rather then trying to always remember the ip address) or worst case click AppSocket/HP/JetDirect and it will download all drivers I suppose HP ever made, at least it takes a long time but the correct driver is avaiable Forward or finish and your done. Remember the Lite or Move or run from cd don't hold the setttings. PS I loved the 6500 so much I bought a second (built like a Sherman tank you dont see that kind of quality these days, heavy as heck!) HP6500 named hp-6500-2 When I add the next 6500 it appears right after I click add printer then under network printer I CLICK aPPsOCKET/hp jETdIRECT AND Bingo the 2nd printer is there all I give it is a name (glossy paper printer) I am a sloppy writer but I hopoe this might have helkped.

OK After you have the printer logged into the router (some routers require addition measures so the printer obtains the same ip address EVERY time . There is a little dns server in the printer so if you forget the ip address as long as you gave the printer a rememberable easy short name like hp-6500 you can type it into any ***puter that is logged into the same router be it wired via lan port or wireless via wifi You must know the password to enter the scanner section (because you could scan whatever someone forgot and left on the glass if not) after your in you will see.  Use ADMIN lower case i think and your password) then once your in click preview after youve selected color picture, drawing,BW pic or Txt and doc size then click scan. Now the following is the way "I" do it but there may be a better way. After you click "Preview" or SCAN you see the image SCAN provides the highest dpi then you can right click on the image and click save and or open with ??? It as easy as pie this way but Im sure there is another way. Im lazy and it worked so I stick with it. If you find the correct way please advise me.

Note: you can't refill the inks despite there is no head in them. You must buy and solder a "tiny" resistor on each color (then you loose the ability to see levels, thats fine with me) If your lazy buy some generic refills, youll save about 15-20$ youll see a litttle drop of black epoxy between the 4 gold contacts. You can drill a hole on top and save save. Remember NEVER let these heads in printer sit without power to them. They cycle everyday to keep the head wet, If turned of with a power strip they dont cycle and will dry out. Its not a ig deal to remove the printhead (pops out via 2 purple arms) you can clean some clogs with simple water, OK Im getting carried away.
Coley

---

### Post by fofo412 on 2011-05-19
Best printer / thread / install EVER!!

This is my first printer use with linux (started with Ubuntu 4.10 Warty Warthog) and following the link in the first few posts ( [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html) ) I installed the script, followed the instructions, and everything worked great!!

Running 11.04 x86. . .

---

### Post by Yellow Pasque on 2011-05-19
If only someone would mark it SOLVED...

---

### Post by Prince Valiant on 2011-05-20
> **Temüjin said:**
> If only someone would mark it SOLVED...

Done.  :-D

-Val

---

### Post by meyhus2 on 2012-05-27
The model number **HP Officejet 6500**.

**Method 1:**
You may refer to the below links and use the troubleshooters. Check if it lists and helps resolve any issues: Open the Printer troubleshooter:
[http://h10025.www1.hp.com/ewfrf/wc/product?product=3795314&lc=en&cc=us&dlc=en&task=&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=3795314&lc=en&cc=us&dlc=en&task=&lang=en&cc=us)

**Method 2:**
You may check if you have the latest drivers installed for the device. You may refer to the below link for getting the latest drivers and check –
[HP Officejet 6500 Driver]("http://www.hpdriver.net/hp-officejet-6500-driver/")

Good Luck. 

(Alternative)

---

