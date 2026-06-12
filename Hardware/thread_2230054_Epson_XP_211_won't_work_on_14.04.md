---
title: "Epson XP 211 won't work on 14.04"
date: 2014-06-17
forum: Hardware
---

### Post by subfer1 on 2014-06-17
Hey, everyone! I just managed to get rid of Windows 8 from my laptop and now I have issues with installing my xp211 on Ubuntu 14.04. I searched for the printer on my wi-fi network, found it but it gets stuck on "installing"
 It's been like this for over an hour and I doubt that it's downloading any drivers (I had downloaded and installed the deb package for 64 bit sistem before searching for the printer).

[ATTACH=CONFIG]254008[/ATTACH]

Any thoughts?

---

### Post by pdc on 2014-06-17
which interface are you using? Is that a mint cinnamon?

so you have installed the Epson driver? > (I had downloaded and installed the deb package for 64 bit sistem before searching for the printer).

I would get the Epson driver from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=22525&DSCCHK=90be2902d77de22e8474d6a3e989b2a7daa642ac](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=22525&DSCCHK=90be2902d77de22e8474d6a3e989b2a7daa642ac) and download epson-inkjet-printer-201304w_1.0.0-1lsb3.2_amd64.deb and that is what you did?

___________________________

I understand Epson expects you to connect the printer to the router; either through the keypad on your device; if it has one; 

I am not sure what country you are in;

the US website has a guide for the XP 200 [http://www.epson.com/cgi-bin/Store/support/supAdvice.jsp?BV_UseBVCookie=yes&noteoid=231739&type=highlights](http://www.epson.com/cgi-bin/Store/support/supAdvice.jsp?BV_UseBVCookie=yes&noteoid=231739&type=highlights)

______________________

the UK website doesn't seem to have video tutorials; they have pdf files [http://www.epson.co.uk/gb/en/viewcon/corporatesite/products/mainunits/support/12298?searchKey=xp-212](http://www.epson.co.uk/gb/en/viewcon/corporatesite/products/mainunits/support/12298?searchKey=xp-212)

---

### Post by subfer1 on 2014-06-17
I believe I got that package, but I got it from here: [http://www.openprinting.org/printer/Epson/Epson-XP-211_214_216_Series](http://www.openprinting.org/printer/Epson/Epson-XP-211_214_216_Series)

But I will try with the links you've given me and see if they work. I am in Costa Rica, so support here is pretty limited (mostly we get thrown in the latin american site and that is not that precise).

Thanks!

---

### Post by subfer1 on 2014-06-17
THANKS! I don't know why, because the drivers were exactly the same ones, but after I reinstalled them, my laptop detected the printer immediately and it's working now. Thanks a bunch! :)

---

### Post by pdc on 2014-06-17
great! enjoy

---

### Post by Tacuabe on 2015-01-15
Hello there!

I've just bought an Epson XP-211 printer, downloaded the drivers from the Epson official page and my printer is working when connected with cable via USB port.

However, I'm unable to print wireless. I'm using Lubuntu 14.04 with LXDE.

When using System Tools/Printers and trying to locate a Wireless Printer I get up to a point and then the systems seems to enter an endless loop. Cancelling the operation clears the loop but further intents repeat the behavior and refuse to continue.

I am attaching four screen captures that show the steps I went through. Capture_002 shows the printer is indeed located and also shows the SMB Browser output. Capture_003 is the error I get when using the Verify... key. Capture_004 shows a different error I'm getting now when using that same key.

[ATTACH=CONFIG]259273[/ATTACH][ATTACH=CONFIG]259274[/ATTACH][ATTACH=CONFIG]259275[/ATTACH][ATTACH=CONFIG]259276[/ATTACH]

The Epson manual (found in the Web) is much more explicit than the Quick Setup enclosed in the box. However, there are some obscure points:

a) To activate WiFi one has to press the corresponding key for 3 seconds. The manual does not say what is supposed to happen. Actually two lights, one green the other orange blink alternatively for several minutes. After some time the orange light goes steady and the green light is off. Pressing the WiFi key clears (turns off light) and you can press the button again for 3 secs...

b) The printer must be connected via USB until detected by the system as wireless. Then a message will request to remove the cable. I suppose this refers to the Windows and OSX software included in the CD. Linux is not mentioned anywhere and I've never seen the message.

c) Scanning does not work via cable. Tried with Simple Scan and XSane to no avail. Anyhow, I suppose this is a different issue which must be attacked after WiFi is working.

Any help will be much appreciated.

Thank you guys!

---

### Post by Mike_Walsh on 2015-01-15
Hello, Tacuabe.

The reason, most probably, why your scanner section won't work is that printer and scanner/data packages need to be installed separately in Linux (even for all-in-ones).

Go to the Epson download site:-

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

And enter 'XP-211', and 'Linux'. Hit search, and the next page will take you to a list of packages for your machine. You will want the scanner driver (core data & data package);hit Download.

On the next page, scroll down to the bottom of that very long list, and click on 'Accept'. The page will extend, giving you a list of packages. Depending on whether you are running 32- or 64-bit, you will want the 'iscan_2.30.0-1~0.1.ltdl7_(and either i386 OR amd64).deb. You will also require the 'iscan-data_1.33.0-1_all.deb' data package.

You need the .deb packages for the very simple reason that Ubuntu is based on _Deb_ian (hence, .deb.)

When installing these, this is VERY IMPORTANT; you MUST install the DATA package first.....the scanner package requires this to be installed, in order to read this data while it is installing. When you have done all this, and the installation is complete, go to the Dash, and search for 'Image Scan for Linux!'; this is your Epson scanner app. You should find that Simple Scan will now also detect your scanner and work, too. I can't comment on whether XSane will work as I have never used it.....but it's fairly good odds that it will.

When you first open the app, it will say, 'Can't find scanner', or something similar. This is perfectly normal; close the app, switch your XP-211 off, wait about 10 seconds, switch it back on, then open the app again; it will now detect the scanner, and SHOULD be ready to use.

Hope that helps. Wish I could help with the wireless issues, too, but I don't know the first thing about them; my SX218 works solely by good old USB.


Regards,

Mike. ;)

BTW; When you say you're trying to print 'wireless', are you actually referring to 'network' printing? Because the IP address for your printer needs to be configured JUST right; this is the point that proves to be a stumbling block for so many people...

Does your scanner work via wireless, without following the steps I've outlined above? I'd be surprised if it did; whether by USB, OR wireless, it STILL needs those packages to be installed..!

---

### Post by pdc on 2015-01-15
Hi Tacuabe;

Mike has given you pointers for the drivers; 

I understood the printer printed for you via usb; 

and it is the wireless that is defeating you currently;

this link [http://www.manualslib.com/manual/604626/Epson-Xp-211.html?page=3#manual](http://www.manualslib.com/manual/604626/Epson-Xp-211.html?page=3#manual) has the manual for your XP211

____________________

As I understand, the printer needs to have gained access to your wireless router; before you can send a print page; from your computer; to the printer;

.........the manual seems only to talk of using the WPS method; 

......... you seem to have found that step unclear; all I can repeat here is what the Epson manual says:

> 1. To connect your XP211 to your WPS-enabled router, **[SIZE=4]press the WPS button on your router or access point[/SIZE]**.

2. [COLOR="#008000"]Then go to your XP211 and press and hold down the Wi-Fi button on your product for 3 seconds[/COLOR].

Note: Be sure to press and hold the Wi-Fi button on your product within 2 minutes of pressing the WPS button on your router or access poin

Epson thinks it is as simple as that

___________________________

they also supply this video for you to watch [http://www.epson.com/cgi-bin/Store/support/supAdvice.jsp?BV_UseBVCookie=yes&noteoid=231740&type=highlights](http://www.epson.com/cgi-bin/Store/support/supAdvice.jsp?BV_UseBVCookie=yes&noteoid=231740&type=highlights)

is it of any help to you?

---

### Post by steelsoul on 2015-01-16
> **Mike_Walsh said:**
> Hello, Tacuabe.

The reason, most probably, why your scanner section won't work is that printer and scanner/data packages need to be installed separately in Linux (even for all-in-ones).

Go to the Epson download site:-

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

And enter 'XP-211', and 'Linux'. Hit search, and the next page will take you to a list of packages for your machine. You will want the scanner driver (core data & data package);hit Download.

On the next page, scroll down to the bottom of that very long list, and click on 'Accept'. The page will extend, giving you a list of packages. Depending on whether you are running 32- or 64-bit, you will want the 'iscan_2.30.0-1~0.1.ltdl7_(and either i386 OR amd64).deb. You will also require the 'iscan-data_1.33.0-1_all.deb' data package.

You need the .deb packages for the very simple reason that Ubuntu is based on _Deb_ian (hence, .deb.)

When installing these, this is VERY IMPORTANT; you MUST install the DATA package first.....the scanner package requires this to be installed, in order to read this data while it is installing. When you have done all this, and the installation is complete, go to the Dash, and search for 'Image Scan for Linux!'; this is your Epson scanner app. You should find that Simple Scan will now also detect your scanner and work, too. I can't comment on whether XSane will work as I have never used it.....but it's fairly good odds that it will.

When you first open the app, it will say, 'Can't find scanner', or something similar. This is perfectly normal; close the app, switch your XP-211 off, wait about 10 seconds, switch it back on, then open the app again; it will now detect the scanner, and SHOULD be ready to use.

Hope that helps. Wish I could help with the wireless issues, too, but I don't know the first thing about them; my SX218 works solely by good old USB.


Regards,

Mike. ;)

BTW; When you say you're trying to print 'wireless', are you actually referring to 'network' printing? Because the IP address for your printer needs to be configured JUST right; this is the point that proves to be a stumbling block for so many people...

Does your scanner work via wireless, without following the steps I've outlined above? I'd be surprised if it did; whether by USB, OR wireless, it STILL needs those packages to be installed..!

First of all thanks Mike for your detailed explanation.
But in my case scanner for Epson L210 still do not work. 
I have built the scanner drivers, but no luck, I always get 'Can't find scanner'.
Could you help me with L210?, I'm using Ubuntu 14.04, 64 bit.

---

### Post by Mike_Walsh on 2015-01-16
> **steelsoul said:**
> First of all thanks Mike for your detailed explanation.
But in my case scanner for Epson L210 still do not work. 
I have built the scanner drivers, but no luck, I always get 'Can't find scanner'.
Could you help me with L210?, I'm using Ubuntu 14.04, 64 bit.

Hallo, steelsoul.

Hm. well, I don't consider myself an 'expert' by ANY means, but....we can but try.

First of all, three things:-

1) Did you download both scanner AND data packages? And did you get the correct ones for your system (i386 for 32-bit, amd64 for 64-bit)? You'll now want the 'iscan-1.3[COLOR=#ff0000]**4**[/COLOR].0-1_all.deb' data package, by the way; looks like there's been an update in the last 24 hours.

2) Did you make sure to install the data package first, BEFORE the scanner package? This part is MOST important, since it won't work otherwise. The scanner driver will look for data which is included in this package to be able to install itself.

3) And finally (and this is the part that's confusing me a wee bit, I must admit); what precisely do you mean, when you say you have 'built' the scanner drivers? There SHOULDN'T be any 'building' involved. Epsons, fortunately, are one of the easier printer brands to get up-and-running in Linux, so long as you follow the steps in the correct order (there are quite a few), and just be methodical in your approach to the task.

Epson have quite a number of printer drivers available, but relatively few scanner drivers, to cover virtually EVERY scanner module they've ever produced over at least the last decade. And according to the listings, your scanner should use exactly the same driver/data packages that mine uses.

Let me have the info requested, please, and we'll see where to go from there.


Regards,

Mike. ;)

BTW: Do you have the printer itself working yet?

---

### Post by Tacuabe on 2015-01-18
Hello Mike,

A BIG THANKS for your directions on making the Epson XP-211 scanner work. It was a real piece of cake! BTW, I downloaded iscan-1.34.0... since it was the only one available. I note now that you are helping steelsoul and already updated the version.

FYI both Simple Scan and Xsane are also working flawlessly. Simple Scan appears to be very slow compared with Image Scan or Xsane. 

I am now trying to make the wireless work following directions issued by pdc.

Thanks again for you invaluable help.

---

### Post by Tacuabe on 2015-01-19
Hello pdc!

Thanks for writing. I had already located and read the Epson manual. The video only mentions and describes the procedures for Windows and OSx. Not very useful for Linux!

Here is my network configuration:

The service provider (Antel, in Uruguay) connects the fiber optic cable to a ZTE Terminal (Model ZXA 10 F 660) and though there is a WPS button users are banned from using it. The range of this terminal is somewhat reduced, therefore most users add a router to gain access from everywhere in the house.

In my case the router is a TP-LINK WR340G which does NOT have a WPS button. I logged in to TP-LINK web page and did some investigation without any success. I will appreciate if you can provide additional help in this connection.

Thanks

---

### Post by steelsoul on 2015-01-20
Hi Mike, 
Thanks for your response. Please, see my responses below.

1) I downloaded both data and scanner packages, all in deb format. It looks like that I slept update;

2) At first I have installed data package and then driver package, I used synaptics GUI program manager for that;

3) I've built scanner driver and data package using provided *.tar.gz files, using usual chain of commands: configure, make, make install (las command with sudo). 
Moreower in my case the iscan works only if it is built from the sources. When scanner packages were installed first time (through synaptics) the isane didn't work at all, the program hangs down the terminal, but not the entire system, I was able to quit via Ctrl-C. 

The scanner works on the Win 7. 

I will look forward for the changes in the driver's package.

---

### Post by pdc on 2015-01-20
Hi Tacuabe;

so I went here [http://esupport.epson-europe.com/FileDetails.aspx?lng=en-GB&data=VkjUmbBFNN0El7r+C9hfLmD87ZF6SU002F602JyZtpvjBE0U003D&id=376828](http://esupport.epson-europe.com/FileDetails.aspx?lng=en-GB&data=VkjUmbBFNN0El7r+C9hfLmD87ZF6SU002F602JyZtpvjBE0U003D&id=376828)

and downloaded what Epson said was the manual for the XP-212 which must be similar to the XP-211

_____________

the attached thumbnail has a screenshot of page 78 where there is a wifi setup guide;

can you find that in the menu? You need to know the name of your wireless network; your password; and you should be able to enter it into the screen on the printer; and then the printer can talk to the router;

---

### Post by Mike_Walsh on 2015-01-20
> **Tacuabe said:**
> Hello Mike,

A BIG THANKS for your directions on making the Epson XP-211 scanner work. It was a real piece of cake! BTW, I downloaded iscan-1.34.0... since it was the only one available. I note now that you are helping steelsoul and already updated the version.

FYI both Simple Scan and Xsane are also working flawlessly. Simple Scan appears to be very slow compared with Image Scan or Xsane. 

I am now trying to make the wireless work following directions issued by pdc.

Thanks again for you invaluable help.

Glad to be able to help. Hopefully, between us, pdc & I will get you COMPLETELY working.....but I can't take ALL the credit, by a long shot. pdc appears to know a LOT more about the general workings of these things than I believe I EVER will!

In over 30 years with these gadgets, I've ALWAYS used Epsons; never really had any experience with other makes. Having found the very first one to be so reliable and trouble-free, I've tended to stick with them.

My very first Epson printer was this 1983 FX-80, which I purchased, second-hand, in 1988. It was already 5 years old at that point.....and went on to serve me faithfully for the next 16 years!

[ATTACH=CONFIG]259380[/ATTACH]

Notice the pin 'tractor' feed holes at the sides of the continuous paper feed stack; that was how they used to feed the paper through. But it was the most reliable printer I'd ever had; I only gave it up in 2004 because it was no longer possible to get ink for it...


BTW, I agree with you about Simple Scan. I, too, have found it to be slower than Epson's own program; but then Simple Scan, I believe, dates back some years, and (so I understand) was really intended to be used with PPD packages.


Regards,

Mike. :)

---

### Post by steelsoul on 2015-01-20
> **steelsoul said:**
> Hi Mike, 
Thanks for your response. Please, see my responses below.

1) I downloaded both data and scanner packages, all in deb format. It looks like that I slept update;

2) At first I have installed data package and then driver package, I used synaptics GUI program manager for that;

3) I've built scanner driver and data package using provided *.tar.gz files, using usual chain of commands: configure, make, make install (las command with sudo). 
Moreower in my case the iscan works only if it is built from the sources. When scanner packages were installed first time (through synaptics) the isane didn't work at all, the program hangs down the terminal, but not the entire system, I was able to quit via Ctrl-C. 

The scanner works on the Win 7. 

I will look forward for the changes in the driver's package.

Hello again, 
It seems it was a bug in the previous version of the epson scanner driver. 
The next pair: 
iscan-data_1.34.0-1_all
iscan_2.30.1-1~usb0.1.ltdl7_amd64 is working perfectly. 

Best regards, 
steel.

---

### Post by Tacuabe on 2015-01-20
Hello pdc,

Thanks for the reply. Unfortunately the information in the manual refers to printers with a display which the XP-211 has not. And it still requires activating WPS at the router which I failed to detect if available and how its' done.

Any additional suggestions/ideas?

Thanks a lot.

---

### Post by Mike_Walsh on 2015-01-20
> **steelsoul said:**
> Hello again, 
It seems it was a bug in the previous version of the epson scanner driver. 
The next pair: 
iscan-data_1.34.0-1_all
iscan_2.30.1-1~usb0.1.ltdl7_amd64 is working perfectly. 

Best regards, 
steel.

Glad to hear it! Enjoy...

Regards,

Mike. :)

BTW: And all this is possible, despite one of Epson's customer reps INSISTING to me , about 8 months ago, that 'we don't DO Linux drivers....'!

Go figure.

---

### Post by Tacuabe on 2015-01-28
Hello pdc,

Don't know if you've seen my reply one week ago. I'm still with no clue as to how to configure the Epson XP-211 for network printing. Can you or someone provide help with this issue?

Many thanks

---

### Post by pdc on 2015-01-29
Have a read at post #14 above: have you entered the name of your network; and the password; into the printer; so that the printer can talk to the router? .......that is step 1

step 2...........then one needs to install the Epson drivers; ............ have you done that?

step 3............then one tells the printing admin to use the Epson drivers; that were installed in step 2; as interpreters to talk to the printer; that is allowed to be part of the wireless network; if you have completed step 1

---

### Post by Tacuabe on 2015-01-29
Hello pdc,

Thanks for writing back. 

I have read your post #14 and carefully gone over the manual pages and the captures you uploaded in said post.

Unfortunately, the XP-211 does NOT have display, therefore I know no way of entering the necessary data.

I downloaded the Epson drivers and the printer, when connected with an USB cable, works flawlessly.

I hope there is a workaround to get this fine printer working in my network.

---

### Post by Tacuabe on 2015-01-29
Further to my recent post, I should have added that my Internet provider does NOT allow WPS to be activated. Therefore, this becomes an additional hurdle on the wireless printing issue.

---

### Post by jcleonl on 2015-08-18
After following the steps suggested by Mike, I was able to use the scanner wireless by doing this:


[LIST=1]
[*]Installing the epson scanner driver network plugin package available here: [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule) 
[*]Setting the network plug-in by adding the line *net 192.168.0.7 1865* as stated on page 40 of the iscan user's guide (Image Scan for Linux): [http://ftp.uni-stuttgart.de/gentoo-distfiles/distfiles/userg_revQ_e.pdf](http://ftp.uni-stuttgart.de/gentoo-distfiles/distfiles/userg_revQ_e.pdf). 
[/LIST]

I got the ip address with the line scanimage --list-devices in the terminal which gave me: 
  device `epson2:net:192.168.0.7' is a Epson PID 08AE flatbed scanner 
  device `epkowa:usb:003:009' is a Epson XP-211/212/215 flatbed scanner

Now i'm printing and scanning both, with usb cable and wireless.

---

