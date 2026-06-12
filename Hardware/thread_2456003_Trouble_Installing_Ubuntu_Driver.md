---
title: "Trouble Installing Ubuntu Driver"
date: 2021-01-02
forum: Hardware
---

### Post by nbmota on 2021-01-02
I have just installed the latest Ubuntu Linux distribution on  my computer. I did so, because I was unable to install the drivers for  the scanner component of my Canon PIXMA TR8520 office printer, scanner,  copier and fax machine desktop combo device on my computer when I was  running Zorin OS; a Ubuntu-based Linux operating system. At the time  that I had Zorin OS installed, I posted my concern in the Canon  Community Support forum; to see if anyone could help me to install the  scanner driver for my multifunction Canon PIXMA TR8520 office device on  my computer; and I was told that Canon unfortunately did not offer any  support for installing the Linux drivers that it provides onto Zorin OS  regardless of the fact that Zorin OS is a Ubuntu based Linux  distribution. In fact, they only offer support for installing these  drivers onto either Ubuntu Linux or Fedora Linux. So, I installed Ubuntu  Linux in place of Zorin OS, using the partition that Zorin OS occupied  in my system.

 
Then, I went to the support page for my  Canon multi-function device and downloaded the manual for installing the  ScanGear MP driver for the scanner component of my device on Ubuntu  Linux. That manual is called "ScanGear MP for Linux (Operation guide)"  and is available at the following URLs as a compressed file with the  .TAR.GZ file extension:


[LIST]
[*][https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-multifunction/tr-s...]("https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-multifunction/tr-series-inkjet/pixma-tr8520-wireless-office-all-in-one-printer?tab=manuals%20") 
[*][https://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDMwMDAyOTE5NTAx&cmp=ABR&lang=EN](https://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDMwMDAyOTE5NTAx&cmp=ABR&lang=EN) 
[/LIST]
Then,  I proceeded to follow the instructions that the manual provided as  closely as possible, for installing this driver onto my computer. I  started by downloading the Debian package of the driver; which is the [scangearmp2-3.50-1-deb.tar.gz]("https://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwOTExMTAx&cmp=ABR&lang=EN") archive file; from the following URLs: 

[LIST]
[*][https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-multifunction/tr-s...]("https://www.usa.canon.com/internet/portal/us/home/support/details/printers/inkjet-multifunction/tr-series-inkjet/pixma-tr8520-wireless-office-all-in-one-printer?tab=drivers_downloads") 
[*][https://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwOTExMTAx&cmp=ABR&lang=EN](https://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwOTExMTAx&cmp=ABR&lang=EN) 
[/LIST]
I  downloaded the archived file to my Downloads folders in Ubuntu. Then,  continuing to follow the instructions to install this printer's driver  for its scanner component, I openned a Linux terminal. I made sure that  my Canon Printer and Scanner device was turned off and connected it to  my laptop computer using a USB wire and the USB port. Then, I got to my  Downloads folder, to where I had downloaded the driver for installation,  by typing the following into the Linux terminal, then pressing the  Enter (or Return) key:

[LIST]
[*]**cd Downloads** 
[/LIST]
Then, I unarchived the scangearmp2-3.50-1-deb.tar.gz by typing the following command, then pressing Enter again:

[LIST]
[*]**tar zxvf **[**scangearmp2-3.50-1-deb.tar.gz**]("https://pdisp01.c-wss.com/gdl/WWUFORedirectTarget.do?id=MDEwMDAwOTExMTAx&cmp=ABR&lang=EN") 
[/LIST]
Then,  I openned the the scangearmp2-3.50-1-deb archive by typing the  following command into the terminal, then pressing Enter again:

[LIST]
[*]**cd scangearmp2-3.50-1-deb** 
[/LIST]
Then,  I finished installing the scan driver by typing the following command,  pressing Enter, then typing in the same password that I used to login to  my Ubuntu account at the prompt that followed:

[LIST]
[*]**sudo ./install.sh** 
[/LIST]
Once  this driver was installed, I tested it to see if it was working by  attempting to scan an image. I began by turning on my Canon PIXMA TR9520  multifunction printer and scanner device, then typing the following  command in the terminal, followed by a press of the Enter key, in order  to open Scan Gear MP:

[LIST]
[*]**scangearmp2** 
[/LIST]
Then,  in the "Select Scanner" window panel and prompt that opened up, a  message appeared saying that no scanner was found connected to my  device. The exact message of this alert was *"No scanners detected."*  To attempt to see if I could get this driver to work even though it did  not seem to want to do that, I clicked on the button that said "Update  Scanner List." Then, another window openned that said *"Searching for scanners."* Then, a message popped-up on top of my screen saying *"Scan Gear is ready."* Then, another warning came up in a different window that said *"Cannot  find available scanners. Cable may be disconnected or scanner may be  turned off. Check the scanner status then try again."*
 
So,  I double checked to make sure that my Canon PIXMA TR8520 printer and  scanner device was on and properly connect to my laptop using the USB  cable and the USB port; and it was. Then, I unplugged the USB cord from  my USB drive, plugged it back in and tried clicking the the button  called *"Update Scanner List"* again, yet to no avail. Once again, another window openned that said *"Searching for scanners."*  Then, a message popped-up on top of my screen saying "Scan Gear is  ready." Then, another warning came up in a different window that said *"Cannot  find available scanners. Cable may be disconnected or scanner may be  turned off. Check the scanner status then try again."*
 
So,  I tried uninstalling the scanner driver and attempting to install it  using the second method outlined in the manual for installing this  driver onto the Ubuntu Linux Operating System. To begin this process, I  closed out of Scan Gear by clicking the *X* button on the  right-hand corner of its window. Then, I exited the directories that I  had gotten into by entering the following command into the terminal,  followed by a press of the Enter key, to go back down the directory  tree:


[LIST]
[*]**cd ..** 
[/LIST]
Then, I entered the following command again and pressed Enter again:

[LIST]
[*]**cd ..** 
[/LIST]
Then,  I proceeded to enter the following commands in the terminal to  uninstall the Scan Gear driver, press the Enter key once more, and then  type-in my password at the prompt the followed:

[LIST]
[*]**sudo scangearmp2-pkgconfig.sh --uninstall** 
[/LIST]
Once it was done uninstalling, I attempted to install Scan Gear again; only to do so by *specifying the package*  this time around. So, I turned off my Canon PIXMA 8520 device, while  leaving the USB cable connecting it to my computer. Then, I typed the  following command in the terminal, followed by a press of the Enter key:

[LIST]
[*]**cd Downloads/scangearmp2-3.50-1-deb/packages** 
[/LIST]
This got me to the packages directory inside of the scangearmp2-3.50-1-deb  folder, within my Downloads folder from the terminal. Then, I typed the  following command at the terminal to finish this process of installing  this driver for a 64 bit computer, followed by typing my password at the  prompt once again:

[LIST]
[*]**sudo dpkg -iG scangearmp2_3.50-1_amd64.deb** 
[/LIST]
Then,  I tried testing my installation once again, to see if it worked this  time. I did so by typing the following command in the Linux termina, in order to open Scan Gear MP, followed by pressing the Enter key:

[LIST]
[*]
[LIST]
[*]**scangearmp2** 
[/LIST]
   
[/LIST]
Then,  in the Select Scanner window panel and prompt that opened up again, a  message appeared once more saying that no scanner was found connected to  my device. The exact message of this alert was *"No scanners detected"*  again. To attempt to see if I could get this driver to work another  time, even though it had just failed to do so once more, I clicked on  the button that said "Update Scanner List" again. Then, another window opened that said *"Searching for scanners"* once again. Then, a  message popped-up on top of my screen saying "Scan Gear is ready" again.  Then, once again, another warning came up in a different window that  said *"Cannot find available scanners. Cable may be disconnected or  scanner may be turned off. Check the scanner status then try again."*

 
So,  I double checked to make sure that my Canon PIXMA TR8520 printer and  scanner device was on and properly connect to my laptop using the USB  cable and the USB port once again; and, again, it was. Then, I unplugged  the USB cord from my USB drive, once again, plugged it back in again.  Then, I tried clicking the the button called *"Update Scanner List"* again, yet to no avail. Once again, another window opened that said *"Searching for scanners."* Then, a message popped-up on top of my screen saying *"Scan Gear is ready."* Then, another warning came up in a different window that said *"Cannot  find available scanners. Cable may be disconnected or scanner may be  turned off. Check the scanner status then try again."*

 
So,  installing the driver for my Canon PIXMA TR8520 in my official Ubuntu  distribution of the Linux Operating System failed using both  installation methods outlined in the manual for "ScanGear MP  installation for Linux," like it did when I previously tried to install  this driver onto Zorin OS. Could anyone help me to fix this problem so  that I can get my Canon PIXMA TR8520 multi-function device's scanner  component to work with my Ubuntu Linux Operating System?

 
I would really appreciate it!
 
 
Sincerely,
 
Nataly Mota

---

### Post by TheFu on 2021-01-02
You've provided a ton of details, but not the most important information.  What version of Ubuntu and which DE?  **lsb_release -a** will provide the version.

Try:
[LIST]
[*]different USB port
[*]different USB cable
[*]Working with Canon for their support
[/LIST]

If you have MS-Windows, can you verify that the printer works there correctly?  It would be good to rule out some printer hardware issue, yes?

I learned long ago to be very selective about the hardware I choose for myself when Linux support is needed. Based on a bad interaction with a Canon printer around 2011 on a Linux system, I'd not purchase a printer from that manufacturer.

---

### Post by nbmota on 2021-01-05
Althouth the command **lsb_release -a **does not work in my terminal, I am running version 20.04 of Ubuntu Linux with GNOME. I have just recently tested my Canon PRIMA TR8520 multi-function printer, scanner, copier and fax device on a Windows computer and it works perfectly fine. So, there is nothing wrong with the actual hardware. I have tried switching the USB cord to every available port that I have in my laptop and still could not get my computer to detect the scanner component of my Canon multi-function device.

Canon provided two device drivers for my multi-function device: one for printing and one for scanning. I installed both device drivers and the device driver that exclusively works for printing works fine. So, I am able to send documents to this printer of mine from my computer through the USB cord that connects to my Canon multi-function device. So, there is nothing wrong with the USB cord that I am using either, otherwise I would be unable to send documents to the printer while using it. However, the device only comes with one USB wire, as well as only one USB port to connect to it to my computer; and it has to work for both printing and scanning. It does that just fine on my Windows computer, but on my Linux computer, it is not working for the purposes of printing,

It is actually not a bad Canon multi-function device either! It prints in full color, its printing quality is crisp, it is good for printing documents as well as pictures. When using with Windows, the scanner also scans in high definition. Yet, I feel like the manufacturer provided driver should work for both printing and scanning with it; and it is not working for me at all.

Are you able to help me to get my multi-function Canon device setup to scan like it prints?

I would really appreciate your assistance.


Sincerely,

Nataly Mota

---

