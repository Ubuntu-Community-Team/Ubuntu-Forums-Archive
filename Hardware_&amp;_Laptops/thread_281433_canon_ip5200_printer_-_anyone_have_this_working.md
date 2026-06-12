---
title: "canon ip5200 printer - anyone have this working"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by cfm_fr_59 on 2006-10-21
Hi all,

Can someone tell me how to install canon pixma ip5200 printer ?

Thank in advance,
Cfm.

---

### Post by sixteensix on 2006-10-25
Cfm, there are no native drivers for the Canon IP5200. The only way to get the printer to work is to buy turboprint from turboprint.de

Sorry to be the bearer of bad news.

Sixteensix

---

### Post by cfm_fr_59 on 2006-10-28
Hi,

I found this but can't have this working, if someone can help :

[http://www.3dbuzz.com/vbforum/showthread.php?t=137351]("http://www.3dbuzz.com/vbforum/showthread.php?t=137351")

Cfm.

---

### Post by a2d2 on 2006-10-29
...really a post with a lot of details to IP5200

will try to install next day, maybe for pixus7500 or ip4200.

just tested turboprint demo - excellent, but too expensive.

installed Edgy 6.10 and IP4000 driver, using Gutenprint 5.0.0 - prints just natural text(b&w), but errors with bold and coloured text and pictures.

installed a new cups printer, as shown in ubuntuusers-wiki [here]("http://wiki.ubuntuusers.de/Canon_Pixma_IP4000?highlight=%28pixma%29")
there&#347; a .ppd file, but need more knowledge to change sections or params  ](*,) 

...overseas greets

---

### Post by sixteensix on 2006-10-31
Cfm, I will try that out once I have my internet connection back up. The Joys of moving home!!!

Good searching!!!

Sixteensix

---

### Post by a2d2 on 2006-11-19
...not really working until now, but a new hint for ink tuning sets.

it&#347; coming up beginning next month - **GEHA Tuning Kit for CLI-8 **(34.79 €), single cartridge about 6.99 - 7.49 €, including an adapter for ink-level control !!! (the 1st working clone on market):p 
follow this link [here]("http://www.hardware-versandhandel.de/modules.php?warp=artikel&group=1_7&seite=1&id=1288&kid=42b4f358296a161c43bf1b45c36cac2e") (just in german)

---

### Post by Robert Leithe on 2006-11-27
Being a happy and somewhat frequent photographer I also like to print my pictures. Being so, I purchased a PiXMA iP5200. As I recently switched to Linux (Ubuntu 6.10) I was a bit puzzled when it came to printer support - although I have found posts in several forums telling me "it's getting along"

Now, I came by this post, and to summarize shortly what I did on my PC:

I went to [ftp://download.canon.jp/pub/driver/bj/linux](ftp://download.canon.jp/pub/driver/bj/linux) and downloaded the following files:

cnijfilter-common-2.60-1.i386.rpm
cnijfilter-ip4200-2.60-1.i386.rpm
cnijfilter-ip4200-lprng-2.60-1.i386.rpm

I downloaded and installed Alien
sudo apt-get install alien

I converted the .rpms to .debs
sudo alien cnijfilter-common-2.60-1.i386.rpm
sudo alien cnijfilter-ip4200-2.60-1.i386.rpm
sudo alien cnijfilter-ip4200-lprng-2.60-1.i386.rpm

I then installed the newly converted .deb-files
sudo dpkg -i cnijfilter-common_2.60-2_i386.deb
sudo dpkg -i cnijfilter-ip4200_2.60-2_i386.deb
sudo dpkg -i cnijfilter-ip4200-lprng_2.60-2_i386.deb

Under System>Administration>Printing
New Printer>Forward>Install Driver...>point to /usr/share/cups/model/canonip4200.ppd>Open>Pick iP4200 Ver.2.60 in the list>Forward>Apply

I now have a printer called iP4200 Ver.2.60 and its status is Ready.

I opened a picture (both in gThumb Imageviewer and GIMP) and did a print.
The status of the printer changed to "Printing 1 jobs" for a few seconds before changing back to Ready. But there is no response on the printer itself.

Can anyone see if I did something wrong, or left something out in my procedure?

Sincerely

---

### Post by jmontelius on 2007-01-03
Switched to Ubuntu over teh weekend so I'm a newbee but hers my experience with the IP5200.  I have it up and running with teh IP4200 drivers from Canon Europe [http://software.canon-europe.com/software/0024302.asp](http://software.canon-europe.com/software/0024302.asp) , tried the IP7500 from japan but as reported the colors are not aligned. The .rpm files unpack with alien etc. 

 I previously had severe problems with a freezing Ubuntu everytime i tried to print anything but as described in the setup guide, also from Canon Europe (same site), one has to:
----
Run the gdmsetup command.

Select the [Security] tab and uncheck the [Always disallow TCP connections to X server (disables all remote connections)] check box
----

Now, all I have left to to is to tweek the /usr/shares/cups/model/canonip4200.ppd to allow more than 600dpi. 

 jm

---

### Post by jmontelius on 2007-01-04
:confused:  Well, nothing good that lasts forever. I'm having problems with what I think is a cups issue. The printing can freeze halfway through the page, sometimes Ubuntu crashes :-|  I'm still uinsg the cups 1.2.4 relese but I'm considering moving to 1.2.7 or 1.3 anyone else tried this?

 jm

---

### Post by Nvening on 2007-01-04
Ok

Here is the PPU file for the ip4200, am i correct in thinking that this is all one needs to install the driver?:

[http://upload2.net/page/download/T5j6r09gCAPMMOZ/canonip4200.ppd.html](http://upload2.net/page/download/T5j6r09gCAPMMOZ/canonip4200.ppd.html)

You can select to install that when you setup your printer.

After its setup the file can be deleted.

However, i am getting the same problem as reported earlier. 

When I try to print something it simply says ready for printer status and the job status is stopped.

Also there is no action coming from the printer.

Any ideas?

---

### Post by budgie9 on 2007-01-04
Some of these files need some additional lib files to make them work.
I would suggest you take a look through past posts in these forums and see if there is any mention of them. There are posts I have posted that have links to other web pages where there is some help.
For my i860 under Dapper, I had to install the following lib files perhaps your printers need these or something along those lines.  
libtif3g_3.5.5-7woody2_i386.deb
compat_2004.1.25-10_i386

Note. I am NOT saying these will work for you, but the readme on the Canon site mentions other files being required by some printers. These files are not in English but others have  converted those files.

---

### Post by Nvening on 2007-01-04
Ok, i have done a bit more looking

This wiki page says that you need this:

[http://gentoo-wiki.com/Canon_Pixma_Series](http://gentoo-wiki.com/Canon_Pixma_Series)

[http://bugs.gentoo.org/show_bug.cgi?id=130645](http://bugs.gentoo.org/show_bug.cgi?id=130645)

However i am not sure what to do with that, and it may just be for gentoo?

EDIT:

Just found this, ill give it a go!

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

---

### Post by Nvening on 2007-01-04
Yep! Works just fien on an IP5200, ive updated the WIKI too!

---

### Post by HilliBilly on 2007-02-01
do you believe this does work for the network model (IP5200**R**) as well? (because my ip5200r isn't physically connected to my laptop)

---

### Post by oldnat on 2007-05-26
Hi, still a problem: the site says "This does not work for AMD64".

But I (un)fortunately am sitting before an AMD64 box... 

I did not dare to do this all for I am quite new to Linus so I am afreid to screw up my box - any infos appreciated.

Thanks, Nat

---

### Post by oldnat on 2007-05-30
Well I searched quite a lot but still nothing useful.

There are several stubs which I tried out all one by one and also together, no use.

Even the alien stuff put together (from gentoo) which seems quite logical does not work for me (it states also that this does not work for 64 bit) for I have 64-bit (ith throws up with "invalid architecture" in alien).

So is there a method to get a canon iP5200 print under Ubuntu64?

Thanks

Nathalie

---

### Post by AndrewRodaway on 2008-07-03
A bit late, but I have just successfully printed via WLAN to my Canon Pixma iP5200r. I just installed it first as a USB printer using the CUPS+Gutenprint v 5.0.2 driver and did a test print OK. Then made a copy of the printer and changed the device URI in the settings dialog to socket://192.168.1.101 which I know to be the IP address of the wireless interface and it just worked... (yes, I did pull out the USB cable first...)

a.

---

### Post by oldnat on 2008-07-04
Well, since a time this prnter works well as a defult with Ubuntu, the problem is, that the Gutenprint drivers still have a max resolution of 600 dpi and the printer is just usable as a printer, not as a photo printer! There is still no possibility to print good photos with it like under Windows... there are no possibilities to set the settings you can set under windows :-( So I still have to maintain an XP only for printing :-(

Nat

---

