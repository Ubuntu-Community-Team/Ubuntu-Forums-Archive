---
title: "getting V200 scanner to work on UbuntuStudio 14.04"
date: 2014-06-08
forum: Hardware
---

### Post by Nosphky on 2014-06-08
Gradually moving from Windows 7 to UbuntuStudio (and new to linux), today's task is to get the Epsom Perfection V200 Photo to work on linux.  I've been through a lot of similar threads in this hardware forum and this is where I'm at now.

Initially, SimpleScan told me there was no scanner.   Now, it looks like it will work; Simplescan preferences shows the scanner correctly as an Epsom Perfection V200  but when I try to scan, I get a 'Failed to Scan - unable to connect to the scanner'

lsusb shows the scanner : 

Bus 003 Device 004: ID 04b8:012e Seiko Epson Corp. GT-F670 [Perfection V200 Photo]

sane-find-scanner shows :

found USB scanner (vendor=0x04b8 [EPSON], product=0x012e [EPSON Scanner]) at libusb:003:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


A search on the sane web site shows that this model on usb is unsupported but gives a link to the Epson (epkowa) site where I downloaded the relevant drivers as deb files :

iscan-data_1.28.0-2_all.deb
iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb
iscan-plugin-gt-f670_2.1.2-1_amd64.deb

which I installed in that order using Ubuntu Software Centre.    I checked that libltdl7 is installed.


scanimage -L shows :

device `epkowa:interpreter:003:004' is a Epson Perfection V200 flatbed scanner


I have added my login name to the 'scanner' group.   What other step or steps do I still need to do to get SimpleScan to connect to the scanner  ?  

Thank you.

---

### Post by pdc on 2014-06-08
you have done really well Nosphky; as you say these devices seem to use the epkowa backend; 

there seem 2 different ways to drive the scanner: 

1) SANE open-source
2) Epson's iscan drivers that you have carefully installed

to use 1) if you open and *just have a read first* at the file /etc/sane.d/dll.conf with the text editor gedit with the command > [COLOR="#FF0000"]gedit /etc/sane.d/dll.conf[/COLOR] and if it says

> #epson
epson2

then you need to change it to 

> #epson
#epson2
epkowa          so that SANE uses the epkowa (ie Simple Scan)       .and you look in the directory sane.d to see that there is an epkowa.conf file            (it would need the ID of your scanner in it ........)

to change the dll.conf file, close gedit and then issue the command > [COLOR="#FF0000"]gksudo gedit /etc/sane.d/dll.conf[/COLOR]     ......you will need your sudo password; proof-read; check; SAVE; close; 

___________________________________________________

does the separate Epson iscan work .............ie > [COLOR="#FF0000"]iscan[/COLOR]     in a terminal opens Imagescan ............it is likely a menu item in your system too ..........

---

### Post by Nosphky on 2014-06-09
Hi pdc and thanks for your input.   

 /etc/sane.d/dll.conf    - I edited this file as you suggested (commented out the line epson2 and added the line epkowa)  

I found the file :  /etc/sane.d/epkowa.conf     

It had no mention of my scanner so I put in a line :     usb 0x048 0x012e   

although the language in the conf file itself was discouraging : 

# For any USB scanner not known to the backend (yet), you may, at your 
# own peril(!!), force the backend to recognise and use it via libusb. 
# You can do so by the following configuration command: 
#
Then I tried Simple Scan  (under 'Publishing' in UbuntuStudio) and I got a page to scan successfully  so I thought the job was done.  

I tried iscan in the terminal but didn't see anything happening and I didn't know what to expect - the terminal seemed to be waiting for a response. 

 I found Image Scan!  - it was under 'Graphic Design' in UbuntuStudio.  I don't know whether it was there yesterday.  Because I found SimpleScan under publishing, I thought all the scanning apps would be there.   

Anyways, clicking on Image Scan! gave an error dialog : 

 Scan Selector Dialogue Epson (unknown model) [epkowa:usb:003:004]

     when I clicked ok, it gave way to an Iscan dialogue - "could not connect to scanner"  

lsusb :  gives   

Bus 003 Device 004: ID 04b8:012e Seiko Epson Corp. GT-F670 [Perfection V200 Photo]  

which shows correct vendor ID and product ID and product description, as it did yesterday. 


 sane-find-scanner also correctly finds the scanner as it did yesterday.  


scanimage -L, on the other hand, no longer finds the scanner - giving this result :  

desktop:~$ scanimage -L 
device `epkowa:usb:003:004' is a Epson (unknown model) flatbed scanner device
 `epkowa:interpreter:003:004' is a Epson (unknown model) flatbed scanner 

 I have tried editing the epkowa.conf  file back to its original state but the result is the same.

  I have tried re-booting several times (years of experience with Windows) but I can't get the scanner to work again.    Apart from that single page scan, it has never worked again.


The epkowa.conf file has the following line near the beginning : 

# See sane-epkowa(5), sane-usb(5) and sane-scsi(5) for details.

  I don't understand these references - surely some documentation ?   What is the (5) bit and where would I find them ?

---

### Post by pdc on 2014-06-09
phew; you have done well; and still not working

> The epkowa.conf file has the following line near the beginning :

# See sane-epkowa(5), sane-usb(5) and sane-scsi(5) for details.

I don't understand these references - surely some documentation ? What is the (5) bit and where would I find them ? 

in a terminal, you can read the manual for these things; the terminal uses [COLOR="#EE82EE"]man[/COLOR] as a shortcut for manual so for sane-epkowa it would be > [COLOR="#FF0000"]man sane-epkowa[/COLOR] and thereafter

_______________________________

there is an iscan configuration file and it is in /etc/sane.d/dll.d so to read it the command is > [COLOR="#FF0000"]gedit /etc/sane.d/dll.d/iscan[/COLOR] and edit it the command is > gksudo gedit /etc/sane.d/dll.d/iscan  I wonder if the iscan had the ID of your device as you did in the epkowa.conf file if that would help iscan; as you say you can always remove these references as you wish

_______________________

I guess if one keeps in one's mind the idea that:

1) SANE is the open-source and it has its chain of command
2) Epson supplies iscan and it has its own chain; also with epkowa; 

___________________________________________

scanimage is the command we have used; it is part of the open-source sane arena and it has its own manual; and quite a bit of detail about the command "scanimage -L" > [COLOR="#FF0000"]man scanimage[/COLOR]

they say 

> The -L or --list-devices option requests a (partial)  list  of  devices that are available.  The list is not complete since some devices may be available, but are not listed in any of the configuration files  (which are typically stored in directory[COLOR="#EE82EE"] /usr/local/etc/sane.d[/COLOR]).

so it would seem reasonable to update entries there too: > [COLOR="#FF0000"]cd /usr/local/etc/sane.d[/COLOR] gets you into that directoryl; and if you wish to see what is there > [COLOR="#FF0000"]ls[/COLOR] lists the contents 

and then with > [COLOR="#FF0000"]gksudo gedit dll.conf[/COLOR] you can edit it as you did the other file to add epkowa and comment out epson2

one could only hope after that; (and a reboot!) that scanimage -L might find the device (there is bound to be a command somewhere to restart the services that oversee sane: so you don't have to reboot: I don't have it to hand............eg with printing you restart cups)

_____________________________

the other interesting feature about scanimage is it will do a direct scan from the terminal and some find they can awaken their scanner with > [COLOR="#FF0000"]scanimage >image.pnm[/COLOR] and if I could find it, an additional command to send the image to a file to save

---

### Post by Nosphky on 2014-06-09
Hi pdc :

thanks for the hints on manuals.  I'll get some reading in - not tonight though.

I found the iscan file[COLOR=#FF0000]  ( /etc/sane.d/dll.d/iscan[/COLOR])  but its function seems to be just to tell sane which backend to use and  it specifies 'epkowa'.  I did however try and add a reference to the  scanner ID but it didn't help so I put the file back to its original  state.

Curiously, there seems to be a degree of variability in results from the  series of commands I've been using over the past couple of days.   For  example, scanimage -L  doesn't return a value at all now even if I wait  for ten minutes.  The cursor just sits on the next line and stays there.   If I want to close the terminal it takes a ctrl-c to get control back.

And when I do lsusb :  now it is giving me 

Bus 003 Device 005: ID 04b8:012e Seiko Epson Corp. GT-F670 [Perfection V200 Photo]

This shows the scanner as device 5 on bus 3.  Yesterday and earlier this  evening, it was device 4 on bus 3.  I haven't plugged in or out any  other usb device today and no device 4 is listed.   Is this a normal  behaviour for a linux system ?   It seems to be changing its 'address'.

sane-find-scanner tells the same story.  Yesterday and earlier this  evening, the scanner was found as bus 003, device 004 - now this evening  it says :

found USB scanner (vendor=0x04b8 [EPSON], product=0x012e [EPSON Scanner]) at libusb:003:005


/usr/local/etc/  is empty - no files at all stored there.  In fact, there is almost nothing in /usr/local/directories at all.

Well -it's 1am so I'm closing down for the night.  I'll see what  tomorrow brings.  (If I can get this posy to go - seems like the 'token  has expired' whatever that means.)

---

### Post by pdc on 2014-06-09
> Is this a normal  behaviour for a linux system ?   It seems to be changing its 'address'.

yes;

---

### Post by davidvandoren on 2014-06-10
What motherboard are you using?
Do you have usb 2 or usb 3?

---

### Post by Nosphky on 2014-06-11
Hi davidvandoren ;      After a pc failure, I have just installed a new Gigabyte motherboard :  GA-H97M-D3H   It has support for usb 3 but the V200 scanner dates from around 2008 so is not usb 3,  probably usb 2 ?       The scanner is plugged into a usb 3 port on on the rear of the pc box.   (cannot seem to get the paragraphing / linefeeds to stick : hope this second edit works better)

---

### Post by davidvandoren on 2014-06-11
Restart your pc and go into your bios.
Enable advanced settings and look for usb settings.
Change the [FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]USB 3.0 from XHCI enabled to disabled.[/COLOR][/FONT]
[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]And if available the usb 2 settings EHCI settings from enabled to disabled or vise verse.[/COLOR][/FONT]

---

### Post by Nosphky on 2014-06-11
I set xHCI to disabled (it was on the default of Smart Auto.)  

SimpleScan  still doesn't work but after it has been 'turning' a few minutes, its  preferences do show a choice between 'unknown epson scanner' and 'Epson  Perfection V200' (initially, nothing is shown in the preferences 'scan  source').  I select the correct source and wait and wait - but nothing  further happens.   If I leave it turning long enough, the application closes down.

Between attempts, SimpleScan doesn't remember the correct choice and each time it takes a few minutes to show the choices..

On  one occasion I thought it was going to start a scan because I heard the  sort of noise it generally makes when it is preparing to start up.  But  it didn't continue.

Trying the other scanning application option  'Image scan!' immediately produces a 'Scan selector dialog' offering a  choice between :

-Epson (unknown model) [epkowa:usb:001:004]
-Epson (unknown model) [epkowa:interpreter:001:004]

That  is the same choice as I had before changing the BIOS settings.  The  first option  immediately provokes an Iscan message that it cannot send a  command to the scanner.

But now when I select the second option -  that is [epkowa:interpreter:001:004], I got a good scan.  So that is  some real progress.    I don't understand on what basis I chose between  'usb' and 'interpreter'  and the Image Scan application doesn't seem to  have any gui settings to enable it to remember that choice.

This  is not 100% repeatable.  In 5 tries, I've had 3 success and two failures  with 'unable to send a command to the scanner'.   And sometimes the  succesful attempt takes a long few seconds to come up with the choice of  scanner.  So communications with the scanner are not perfect.

Doesn't  linux (Ubuntu) handle xHCI ?   My BIOS also has an 'XHCI Hand-off'   which by default is set to enabled.  This should have permitted hand-off  from xhci to ehci for those os which don't support xHCI.    The  motherboard doc also claims that the usb3 ports on the back panel can  handle usb3.0/2.0/1.1 specs  and the 2.0 ports can handle 2.0 and 1.1 so  neither the BIOS nor the hardware should have provided an impediment.

---

### Post by davidvandoren on 2014-06-12
Did you change the [FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]usb 2 settings EHCI settings from enabled to disabled or vise verse?[/COLOR][/FONT]
[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]If so either reverse it or set it to the other value. [/COLOR][/FONT]

[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]Another thing you could try out is VueScan which supports many scanner with it's own drivers.[/COLOR][/FONT]
[http://www.hamrick.com/vuescan/epson_perfection_v200.html](http://www.hamrick.com/vuescan/epson_perfection_v200.html)

[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333]Download the try version and see if it works. Sometimes after initiating an Epson scanner with vuesacan the linux free application will work and recognize the scanner till you reboot. You'll have to start the scanner then each time by starting vuescan first or buy the full version. [/COLOR][/FONT]

---

