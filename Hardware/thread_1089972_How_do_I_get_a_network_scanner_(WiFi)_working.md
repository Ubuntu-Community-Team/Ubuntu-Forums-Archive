---
title: "How do I get a network scanner (WiFi) working?"
date: 2009-03-07
forum: Hardware
---

### Post by robenroute on 2009-03-07
Hi there all,

I've just bought myself an Epson BX600FW (same as SX600FW but with additional software) and I would like to get the scanner functionality available through the network. Printing via the network works, no problems there.

I've both tried XSane and the Epson utility Image Scan! on Ibex (8.10), but XSane tells me there are no devices available and the Epson software insists on "Could not send command to scanner." and "Check the scanner's status."

Funny thing is, when I try iscan, the scanner makes this typical scanner starting sound, but then it stops and the error message is displayed. Running iscan from the terminal yields "[epson2] Cannot send this command to a networked scanner"

Anyone out there who has got a network scanner working? I'm not 100% sure, but I suppose there's a difference between a scanner attached to a server and a network-enabled scanner with it's own IP address...

Thanks in advance.

Rob

---

### Post by robenroute on 2009-03-08
I've been mucking about a bit more, but to no avails. I can't seem to get the daemon (saned) to recognize a network-connected device. USB works, but that's not what I want...

Anyone any hints/links/remarks directing me in the right direction? (or perhaps a statement like "this is not supported"? I just want to know what's on)

Thanks

---

### Post by robenroute on 2009-03-08
I found more info here: [click]("http://manpages.ubuntu.com/manpages/intrepid/man5/sane-net.5.html"). Seems that sane-net could do the trick. Only thing is, my networking knowledge is very limited (rather the fish and bicycle story...)

Anybody out there that could give me a little push? Thanks in advance.

Rob

---

### Post by breaky9973 on 2009-03-10
I am trying to connect to a HP Laserjet 3055, a multifunctional with scanner.

The Laserjet 3055 is directly connected to the network..not through a computer.

The printer works fine...but i really would love to use the scanner on my laptop with Ubuntu 8.10 (connected using WiFi)

The scanner works fine on Windows XP clients with HP software installed.

I really have no clue where to begin. Just one question...what is this iscan software? I only see XSane here.

---

### Post by Flag on 2009-03-10
Don't know if it's any help but ... Using a HP PSC through D-Link, printer can be installed as usual, for scanning I use the webrowser to get access to the setup page there I can choose the scanner part of it and actually use it.

---

### Post by breaky9973 on 2009-03-10
Ok i found it already.

My printer is supported through the HPLIP Drivers. Also the scanning is supported these drivers.

Since I use XSane the only thing i needed to do was:

xsane hpaio:/net/HP_LaserJet_3055?ip=192.168.0.118

And then XSane could use my scanner.

Unfortunately I don't think it is so easy for Epson scanners....

---

### Post by terpdan on 2009-03-10
for the hp use this

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by robenroute on 2009-03-12
> **breaky9973 said:**
> 
Unfortunately I don't think it is so easy for Epson scanners....

Indeed, it seems a lot more difficult for the Epson. However, I'm not giving up [-o<

Rob

---

### Post by SteRiley on 2009-04-29
Did you get any luck with this robenroute?

I've just purchased a Epson SX600FW and I've ran into the same problem, can print right away with no problems on 9.04, but would like to be able to make the most of wireless scanning now also.

Fingers crossed its possible!

---

### Post by baltho on 2009-08-12
Woohoo, folks! Took a while, but I found it (on a gentoo forum, love the irony!).

I've got a Brother MFC-885CW, and had no joy with ethernet on the blighter until I stumbled across this command:

[FONT="Courier New"]brsaneconfig2 -a name=MFC885CW model=MFC-885CW nodename=brother_mfc
[/FONT]

Fired up xsane, and it "just worked"! :)

You can swap the nodename=<hostname> for ip=10.1.2.3, evidently, and it works just the same. Scan on dudes!!

---

### Post by mkonc on 2009-09-10
I also have epson sx600fw. Any solution yet?

---

### Post by ogromano on 2009-10-29
> **baltho said:**
> Woohoo, folks! Took a while, but I found it (on a gentoo forum, love the irony!).

I've got a Brother MFC-885CW, and had no joy with ethernet on the blighter until I stumbled across this command:

[FONT=Courier New]brsaneconfig2 -a name=MFC885CW model=MFC-885CW nodename=brother_mfc
[/FONT]

Fired up xsane, and it "just worked"! :)

You can swap the nodename=<hostname> for ip=10.1.2.3, evidently, and it works just the same. Scan on dudes!!

Hey baltho... a little more info for the linux-impaired would be appreciated.

I also have access to MFC-885CW. I'm trying to get it to work but I'm not even sure which driver I need from the Brother website. I have 8.04 Hardy and it recognizes it, wirelessly, when I want to add it as a new printer, but after that, it is not listed in the printer drivers from Brother, there are other MFCs up to 8840D and others (see image). 

Downloaded both the debs that were on the Brother webpage (see attached image)  but the cupswrapper when double clicked stated that it didn't meet all the dependencies and the cwlpr met all the dependencies, but I have no idea what it did since I see no change. 

Also tried the brsaneconfig2 command you stated on a terminal, on its own to see what it did and it didn't recognize it. I can't find anything about "brsane" on the man page of xsane... so basically I have no clue as to how to get this to work. 
I'd love to paste some code for you or someone to look at to tell me what I need to do, but being a Linux noob, I need some guidance. 

Thanks in advance for taking the time to read my post and for maybe helping to get this going.

---

### Post by ogromano on 2009-12-28
bump

---

### Post by NightSniper on 2010-01-02
> **robenroute said:**
> Hi there all,

I've just bought myself an Epson BX600FW (same as SX600FW but with additional software) and I would like to get the scanner functionality available through the network. Printing via the network works, no problems there.

I've both tried XSane and the Epson utility Image Scan! on Ibex (8.10), but XSane tells me there are no devices available and the Epson software insists on "Could not send command to scanner." and "Check the scanner's status."

Funny thing is, when I try iscan, the scanner makes this typical scanner starting sound, but then it stops and the error message is displayed. Running iscan from the terminal yields "[epson2] Cannot send this command to a networked scanner"

Anyone out there who has got a network scanner working? I'm not 100% sure, but I suppose there's a difference between a scanner attached to a server and a network-enabled scanner with it's own IP address...

Thanks in advance.

Rob
I've got the exactly same problems as above. But I'm running Ubuntu 9.10 and got Epson Stylus SX610FW.
Using WLAN to connect printer/scanner to the network.

Since so many users are having the same problem with Epson scanners/printers, perhaps someone might be able to create a install-guide. 

I'm not familliar with where to find the config-files since I'm newable to Linux.

---

### Post by focwiz on 2010-01-02
> **ogromano said:**
> bump

The brother Linux site...
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html")

has a ton of info...885CW specific linux driver are available.  Note that the 885CW is a "brscan2" model.  Follow the guides, download the debian packages for printing, scanning, faxing, etc.  But do keep the previous posters command in mind.  after you get through the brother install steps, that command will make it all work.

Mine is a brscan3 model, so ...

brsaneconfig2 -a name=MFC885CW model=MFC-885CW nodename=brother_mfc

Becomes....for my machine....

brsaneconfig3 -a name=MFC9320CW model=MFC-9320CW ip=192.168.1.006

also...notice the IP address is what worked, but I set up the MFC with a static IP address on my network.

Good Luck

---

### Post by olivers on 2010-02-24
I have an Epson Office TX610FW and have scanning and printing working over the network using Ubuntu 9.10. Mine is connected to the router by ethernet cable, not WiFi, but I hope these steps will help

Steps were:

1) Plug printer/scanner into router, turn on and follow set-up instructions provided to set language, date, time etc and install ink

2) Make sure device has a static IP address (set this up in your router settings) - for example 192.168.0.5

3) Printing works with no extra packages installed using the CUPS+Guttenprint driver for Epson Office TX600FW. An alternate driver (and PPD file) is supplied at the address below, but I didn't need it (in fact Epson's printer driver wouldn't install for me on Ubuntu 9.10)

4) To get network scanning working you need to download and install **two** packages, available by clicking through from: [http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)

scanner program and backend (install this first): iscan_2.24.0-4.ltdl7_i386.deb
network plugin for backend: iscan-network-nt_1.1.0-2_i386.deb
There is also a manual (including these instructions): userg_revK_e.pdf

5) Once both packages are installed, edit the following configuration file: /etc/sane.d/epkowa.conf
Add the following line to the end (substitute your printer's IP address): net 192.168.0.5

To do this in one command, cut-and-paste the following into a terminal (substitute your printer's IP address):
```
sudo sh -c "echo net 192.168.0.5 >> /etc/sane.d/epkowa.conf"
```

That's it! You can use the epson-supplied program iscan, or use other programs like xsane - just make sure you select the [epkowa:net:] driver and not the [epson2:] driver

---

### Post by John_T on 2010-05-09
Thank you olivers!

I can confirm that this works with an Epson TX710W Multifunction Device.

Ubuntu 9.10, 64 bit version.

---

### Post by chideock on 2010-11-10
This is how I got my Epson Artisan 810 scanner, which is connected on my home network via WIFI as a network scanner, working. You most probably can adapt these instructions for your Epson scanner.
 I am using Lucid (10.04.01)
 

 For the drivers and scanning program go to:
 [http://avasys.jp/eng/](http://avasys.jp/eng/)
 

 Then choose &#8220;Download&#8221;
 Then choose &#8220;All in One Multifunction printers&#8221;
 You will now be on a page that starts with &#8220;All-in-Ones (Multifunction Inkjet Printers)&#8221;
 In the first info box titled &#8220;Information&#8221; do not select &#8220;model name&#8221; but do select &#8220;here&#8221; in the line below.  
 

 This will take you to the scanner section. OR you could just page down to the scanner section which starts in the box titled &#8220;Product Information&#8221;.
 Page down past &#8220;License agreement&#8221; down to the box titled &#8220;Form for download&#8221;.
 Now choose your scanner, in my case Artisan 810
 Continue to page down until the OS Questionnaire appears.
 Now answer the OS questions and then select next.
 The next page that comes up starts with &#8220;Printer Driver&#8221; since we want the scanner drivers page down until that info shows up.
 The drivers are shown in order of &#8220;plugin package&#8221;, &#8220;data package&#8221; and then &#8220;core package&#8221;.
 I do not know if the order of install is crucial or not.
 

 I installed the core package first which was the deb 32bit package [libtldl7] (for Ubuntu 8.10 or later)
 

 Select the file (left click) which opens the download window then I selected &#8220;open with Gdebi Package Installer (default). This opened the package installer. You might have to also select &#8220;Install package&#8221; in the upper right corner if not greyed out.
 

 Ignore error messages at this time.
 

 Then I installed the plugin using the same method above.
 I installed the data package last using the same method above.
 Ignore any error messages if they come up.
 

 Now I proceeded to edit some files in terminal window.
 
Edit /etc/sane.d/epkowa.conf (which was added on installation of the above packages) to include only the line &#8220;net 192.168.10.102&#8221; the ip address being that of the printer. Ensure all other lines are commented out (my scanner is a network scanner thus the net line). You could read all the other comments as they may be of interest to you.
 

 Edit /etc/sane.d/dll.conf to exclude, by commenting out, any or all scanner references except &#8220;net&#8221;. At the very least the &#8220;epson2&#8221; line must be commented out. (my scanner is a network scanner so I need only the &#8220;net&#8221; line.
 

 Reboot for good measure.
 

 Now select Applications-Graphics-Image Scan! For Linux
 

 Mine worked with this program only which is all I wanted.

---

### Post by dafranca on 2010-11-16
> **ogromano said:**
> Hey baltho... a little more info for the linux-impaired would be appreciated.

I also have access to MFC-885CW. I'm trying to get it to work but I'm not even sure which driver I need from the Brother website. I have 8.04 Hardy and it recognizes it, wirelessly, when I want to add it as a new printer, but after that, it is not listed in the printer drivers from Brother, there are other MFCs up to 8840D and others (see image). 

Downloaded both the debs that were on the Brother webpage (see attached image)  but the cupswrapper when double clicked stated that it didn't meet all the dependencies and the cwlpr met all the dependencies, but I have no idea what it did since I see no change. 

Also tried the brsaneconfig2 command you stated on a terminal, on its own to see what it did and it didn't recognize it. I can't find anything about "brsane" on the man page of xsane... so basically I have no clue as to how to get this to work. 
I'd love to paste some code for you or someone to look at to tell me what I need to do, but being a Linux noob, I need some guidance. 

Thanks in advance for taking the time to read my post and for maybe helping to get this going.

I got it working with this script:
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

I could not get the scanner working yet.

---

### Post by Braveheart1980 on 2010-11-18
> **olivers said:**
> I have an Epson Office TX610FW and have scanning and printing working over the network using Ubuntu 9.10. Mine is connected to the router by ethernet cable, not WiFi, but I hope these steps will help

Steps were:

1) Plug printer/scanner into router, turn on and follow set-up instructions provided to set language, date, time etc and install ink

2) Make sure device has a static IP address (set this up in your router settings) - for example 192.168.0.5

3) Printing works with no extra packages installed using the CUPS+Guttenprint driver for Epson Office TX600FW. An alternate driver (and PPD file) is supplied at the address below, but I didn't need it (in fact Epson's printer driver wouldn't install for me on Ubuntu 9.10)

4) To get network scanning working you need to download and install **two** packages, available by clicking through from: [http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)

scanner program and backend (install this first): iscan_2.24.0-4.ltdl7_i386.deb
network plugin for backend: iscan-network-nt_1.1.0-2_i386.deb
There is also a manual (including these instructions): userg_revK_e.pdf

5) Once both packages are installed, edit the following configuration file: /etc/sane.d/epkowa.conf
Add the following line to the end (substitute your printer's IP address): net 192.168.0.5

To do this in one command, cut-and-paste the following into a terminal (substitute your printer's IP address):
```
sudo sh -c "echo net 192.168.0.5 >> /etc/sane.d/epkowa.conf"
```

That's it! You can use the epson-supplied program iscan, or use other programs like xsane - just make sure you select the [epkowa:net:] driver and not the [epson2:] driver

Thanks m8 !

I just did that on 10.10 for my epson sx425w and it worked great!

nice job!!!!:popcorn::popcorn::P:P:P:P:P:P

---

### Post by SammyBoy247 on 2010-12-11
Wireless g WPA2 - Ubuntu 10.10 and the SX600FW I'd managed to get the scanner working in the past without doing much but I could only scan at one low DPI, the doc feeder didn't work and the printer would spontaneously crash.

Followed this thread though and I now have a fully functioning printer scanner.

Thank-you, thank-you etc. etc....

---

### Post by gsimpson on 2011-01-07
> **ogromano said:**
> Hey baltho... a little more info for the linux-impaired would be appreciated.

I also have access to MFC-885CW. I'm trying to get it to work but I'm not even sure which driver I need from the Brother website. I have 8.04 Hardy and it recognizes it, wirelessly, when I want to add it as a new printer, but after that, it is not listed in the printer drivers from Brother, there are other MFCs up to 8840D and others (see image). 

Downloaded both the debs that were on the Brother webpage (see attached image)  but the cupswrapper when double clicked stated that it didn't meet all the dependencies and the cwlpr met all the dependencies, but I have no idea what it did since I see no change. 

Also tried the brsaneconfig2 command you stated on a terminal, on its own to see what it did and it didn't recognize it. I can't find anything about "brsane" on the man page of xsane... so basically I have no clue as to how to get this to work. 
I'd love to paste some code for you or someone to look at to tell me what I need to do, but being a Linux noob, I need some guidance. 

Thanks in advance for taking the time to read my post and for maybe helping to get this going.

Go to this page on Brother site to install scanner drivers.

Read instructions as brsaneconfig2 may become brsaneconfig3 depending on your scanner (as in my case as I have MFC-990CW)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

Follow instruction steps. Illustrated examples given too. Brother should be commended for making a good effort to support Linux.

---

### Post by bpevrancken on 2011-07-17
Thanks, Olivers, this works greatly, using Epson Stylus Photo PX270WD!

---

### Post by beermotor on 2011-08-30
> **baltho said:**
> Woohoo, folks! Took a while, but I found it (on a gentoo forum, love the irony!).

I've got a Brother MFC-885CW, and had no joy with ethernet on the blighter until I stumbled across this command:

[FONT="Courier New"]brsaneconfig2 -a name=MFC885CW model=MFC-885CW nodename=brother_mfc
[/FONT]

Fired up xsane, and it "just worked"! :)

You can swap the nodename=<hostname> for ip=10.1.2.3, evidently, and it works just the same. Scan on dudes!!


For those of you with a Brother MFC-7460DN, the brscanconfig4 command with the associated -a <blah blah> will allow a network machine to find the scanner over the network. Brother's website isn't much help on that point, sadly.

---

### Post by desconocido on 2012-03-22
> **olivers said:**
> I have an Epson Office TX610FW and have scanning and printing working over the network using Ubuntu 9.10....

Thanks for this. I now have an Epson Stylus SX420W scanning and printing over WiFi, using Ubuntu 9.10.

---

