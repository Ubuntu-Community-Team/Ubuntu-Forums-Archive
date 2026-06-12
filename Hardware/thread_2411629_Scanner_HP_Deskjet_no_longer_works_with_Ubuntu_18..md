---
title: "Scanner HP Deskjet no longer works with Ubuntu 18.04"
date: 2019-02-01
forum: Hardware
---

### Post by andrew_s4 on 2019-02-01
for whatever reason Simple Scan and other scanning programs have stopped recognizing my HP scanner. All I get is: no device found. It used to work just fine. My OS is Ubuntu 18.04. 
I know that there are others here with the same complaint, but I'm really a novice at doing anything with code and would appreciate some help in getting my scanner going again, basic help! My scanner is HP Deskjet 3630. A couple of months ago I downloaded gscan2pdf and it also worked. But as of a month or so nothing scans anymore.
Anyone with patience and help to offer?
Thanks, Andrew

---

### Post by kurt18947 on 2019-02-01
I'm not HP knowledgeable so take this for what it's worth. HP generally works very well with Ubuntu as you may know, HP software is included by default. You may need a later version. This seems like a reasonable place to start:

[https://developers.hp.com/hp-linux-imaging-and-printing](https://developers.hp.com/hp-linux-imaging-and-printing)

There is a list of supported printers as well as the latest version.

---

### Post by andrew_s4 on 2019-02-03
Hi Thanks for your help. So I downloaded the newest HPlip from your link installed and configured etc. and printing is as ever. It works! Scanning still does not. So I'm looking at the HP site for some help as well. Any other thoughts? Perhaps a fresh download of gscan2pdf or Xsane...

---

### Post by andrew_s4 on 2019-02-03
Using my smart phone and Ipad I can scan with the HP app over wifi with success, and to any place I wish. But not with Ubuntu using usb or wifi. So this is looking like a Ubuntu problem.

---

### Post by andrew_s4 on 2019-02-03
[COLOR=#333333][FONT=HPSimplifiedRegular]**[SIZE=4][B]Found this on HP. However I haven't a clue what it means or how to go about installing it... would appreciate some simplified help!**[/SIZE]

Symptoms: [/B][/FONT][/COLOR]
[COLOR=#333333][FONT=HPSimplifiedLight]OpenOffice or xsane cannot see my network connected scanner

[/FONT][/COLOR]
[COLOR=#333333][FONT=HPSimplifiedLight][FONT=HPSimplifiedRegular]**Cause: **[/FONT]
CUPS queue not configured properly


[/FONT][/COLOR]
[COLOR=#333333][FONT=HPSimplifiedLight][FONT=HPSimplifiedRegular]**Solution: **[/FONT]
For network scanning, the "hp:/net/..." URI must be configured in the CUPS queue for auto-discovery by OpenOffice and xsane. You can manually specify the URI with xsane using the following format:
xsane <"hpaio" device uri>
For example:
xsane hpaio:/net/PSC_750?ip=12.25.63.142
[I](Where the CUPS installed device URI is: hp:/net/PSC_750?ip=12.25.63.142, and the hp: was replaced with hpaio:)


[/I]


[/FONT][/COLOR]

---

### Post by oldfred on 2019-02-03
Do you have printer connected with USB connection or trying with Wireless?

I have a HP3520 connect with USB and it works without issue.
Before 18.04 I installed HPLIP directly from HP, but a new clean install of 18.04 just worked with whatever default settings.
There is a change with 18.04 Bionic Beaver:
Driverless printing support is now available. 
PostScript Printer Description (PPD) files are created by vendors to describe the entire set of features and capabilities available for their PostScript printers.

Does printer show in System Settings, Devices, printers?

---

### Post by andrew_s4 on 2019-02-03
My printer is connected via USB and I can use it wireless. The printer works without a problem, but the scanning function doesn't work at all anymore under any software. 
The printer is shown in System Settings both wireless and USB.
Just the scanner refuses to be recognized, since about 1 month.

---

### Post by oldfred on 2019-02-03
I just scanned several documents with Simple Scan.

Is correct device shown in Simple Scan. Upper right corner icon, then preferences?

---

### Post by andrew_s4 on 2019-02-04
in Simple Scan  there is no longer a scanner listed. I get a message saying that '' Additional Software needed. You need to install driver software for your scanner'' I click on the link given for the drivers and it loads and installs. Still no scanner listed and it says I need ''Additional Software... This is the endless circle. But no scanner is listed. Under Devices/Printers  HP is listed and prints. But no scanning...
I'm reduced to using the scanner with the HP app for Ipad and Android. Why the scanner doesn't work under Ubuntu anymore is the puzzle.

---

### Post by oldfred on 2019-02-04
I show these as part of my scan software:
simple-scan, libsane-common, libsane1 and sane-utils 
    
Check what you have installed.
I use snaptic to know details names of applications or drivers.

---

### Post by andrew_s4 on 2019-02-04
scan software 
simple scan, sane-pygtk, Xsane Image and gsscan2pdf. None of them recognize my scanner.

I'm not sure what snaptic is or how to go about finding it or using it. I am a very under educated Ubuntu / Linux user, because I don't have the time to go into it at depths. Hence I'm hopeful of your patience!

---

### Post by oldfred on 2019-02-04
I like synaptic as it shows detailed file names and better description of the apps. I can search and then click on heading and see what is already installed.

sudo apt install synaptic

It is a gui program and will ask for your password to run.

---

### Post by andrew_s4 on 2019-02-04
Ok, this is what is listed:
sane utils, simple scan, libsane1,  libsane-dev, libsane-common, libimage-sane-perl, libkf5sane-data, libkf5sane5,  gsscan2pdf, xsane

---

### Post by helicase on 2019-02-04
I've had similar problems with the scan function on a couple of HP printers. Installing via the printer menu works fine for the print function, but scanning doesn't work. I've been able to solve the problem with hplip-gui. If you install it and run it from the terminal it will take you through a few windows to install the printer. Just follow the installation process and both printing and scanning should work. It's probably best to remove the printer from the devices menu first, because otherwise you might end up with two entries for your printer, which can cause more printing trouble (it did for me).

---

### Post by him610 on 2019-02-06
Check with HP support to see if they provide Linux scanner drivers for you machine.

---

### Post by kurt18947 on 2019-02-12
Here's something to check though it may not be applicable to HP scanners. Brother has a similar problem, a new install will print fine but will not scan. The problem in Brother's case is that some files are installed in the wrong location. Here is an example of Brother's recommended fix:

> [B]Example 
command(For brscan3 Users):[/B] 

**cp /usr/lib64/libbrscandec3.so.1.0.0         /usr/lib**
**cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane**
**cp /usr/lib64/sane/libsane-brother3.so.1     /usr/lib/sane**
**cp /usr/lib64/sane/libsane-brother3.so       /usr/lib/sane**
**cp /usr/lib64/libbrscandec3.so               /usr/lib**
**cp /usr/lib64/libbrscandec3.so.1             /usr/lib**

You could look in /usr/lib64/sane and see if there are any likely HPish files that might belong in /usr/lib/sane. Only thought I have. I've also seen a recommendation to create a link rather than copying. I'm not sure what the functional difference would be.

---

### Post by andrew_s4 on 2019-02-13
This is getting all far too complicated for me! The more I delve into this issue, the more I see it has been a problem for a very long time for a lot of people and there doesn't seem to be any solution. HP doesn't offer any help other than being able to ask the question. An answer doesn't seem to be important enough. 

At present printing works via USB although the HP Device Manager says Unable to open device hp:/usb/DeskJet_3630_series?serial=CN7734N25W067P.
Also HPLIP-3.19.1 version is installed. But on boot up I get a error message from the HPLIP Status Service saying 
''No system tray detected on this system.
Unable to start, exiting.''

What bothers me, is that the scanner will work under iOS and Android with the HP app. The scanner also used to work for me under Ubuntu 18, but no longer. So where does the issue lie: Ubuntu or HP? 
I'm not any where near computer competent enough to solve this problem and certainly don't have the time either. I've already spent too many hours looking around. Such issues just shouldn't exist anymore.
Thanks for any help offered, I would like to see it working again!

---

### Post by him610 on 2019-02-13
Oftentimes in the past, the addresses of devices connected by USB  would wander between shutdowns and startups. It used to happen with Windows also. The bus and device ID would not remain consistent between shutdown/startup.  I don't know if that is your problem or not, and I don't know of a permanent fix.  Ever since I first noticed this behavior several years ago, I have always utilized my local area network to connect to my printers and multifunction (print, scan fax) devices.

This HP webpage, [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index]("https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index") describes your HP DeskJet 3630 All-in-one Printer as having both USB and Network connection capabilities.

---

### Post by brian_p on 2019-02-14
You say the device is on wireless. Please provide the outputs of

```
avahi-browse -rt _uscan._tcp
```
```
avahi-browse -rt _scanner._tcp
```

avahi-browse is in the avahi-utils package.

---

### Post by SeijiSensei on 2019-02-14
I have an HP scanner that isn't supported by SANE.  I gave up trying to find open-source solutions and ended up investing in [VueScan]("https://www.hamrick.com/") which works flawlessly.

---

### Post by brian_p on 2019-02-14
> **SeijiSensei said:**
> I have an HP scanner that isn't supported by SANE.  I gave up trying to find open-source solutions and ended up investing in [VueScan]("https://www.hamrick.com/") which works flawlessly.

Yours is standalone scanner, we assume. The Deskjet 3630 is an AIO. True, the scanner part is not supported by SANE but it is (or should be) supported by HPLIP.

---

### Post by andrew_s4 on 2019-02-14
My device when running on Ubuntu has always been with USB. Although it doesn‘t scan when using it from Ubuntu and wifi either.
But when scanning and printing on iOS and my cell phone with the HP app it works great on wifi.
I‘ll provide the outputs when I get back onto my desktop.

---

### Post by brian_p on 2019-02-14
> **andrew_s4 said:**
> My device when running on Ubuntu has always been with USB. Although it doesn‘t scan when using it from Ubuntu and wifi either.
But when scanning and printing on iOS and my cell phone with the HP app it works great on wifi.


Does either iOS or your cell phone use HPLIP? No? Thought not.

We'll await.

---

### Post by brian_p on 2019-02-15
> **andrew_s4 said:**
> 
I‘ll provide the outputs when I get back onto my desktop.

If the cause is what I think it is, a look at the journal output after trying to scan could provide confirmation.

---

### Post by brian_p on 2019-02-15
oldfred said

> I have a HP3520 connect with USB and it works without issue.

Do we suppose that is the one of the Deskjet 3520 series?

Anyway, for comparison with what andrew_s4 will eventually provide, it would be useful to have your outputs from

```
avahi-browse -rt _uscan._tcp
```

and

```
avahi-browse -rt _scanner._tcp
```

---

### Post by kurt18947 on 2019-02-15
> **SeijiSensei said:**
> I have an HP scanner that isn't supported by SANE.  I gave up trying to find open-source solutions and ended up investing in [VueScan]("https://www.hamrick.com/") which works flawlessly.

ViewScan is a very good suggestion. It can be tried without purchase, a non-purchased install will put a watermark on scanned images. We bought it because even though our Canon scanner is supported, the light in the lid is not and we wanted to scan slides. A useful feature of ViewScan is that it doesn't need to be install to test. I just copied 3 files, the executable and two others. The executable may have to be marked as an executable program. I created a desktop launcher, set the preferences and that was all that was required.

---

### Post by andrew_s4 on 2019-02-16
Brian,
I assume I have done this correctly, here are the outputs:

$ avahi-browse -rt _uscan._tcp
+ wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
+ wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
= wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "ty=DeskJet 3630 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
= wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "ty=DeskJet 3630 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
sav@sav-desktop:~$ avahi-browse -rt _scanner._tcp
+ wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _scanner._tcp        local
+ wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _scanner._tcp        local
= wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _scanner._tcp        local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["flatbed=T" "button=T" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "mdl=DeskJet 3630 series" "mfg=HP" "ty=DeskJet 3630 series" "txtvers=1"]
= wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _scanner._tcp        local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["flatbed=T" "button=T" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "mdl=DeskJet 3630 series" "mfg=HP" "ty=DeskJet 3630 series" "txtvers=1"]


I have also downloaded VueScan and it works. At first it didn't find the scanner and after restarting the scanner and software, like magic it worked. Would still like to understand or at least fix the problem of no other scanner programs being able to find the scanning function, either on USB or wifi.

---

### Post by brian_p on 2019-02-17
> I assume I have done this correctly, here are the outputs:

Spot on. Thanks. The problem arises from

[LIST]
[*]ty=DeskJet 3630 series
[/LIST]
You have been hit by [https://bugs.launchpad.net/hplip/+bug/1797501]("https://bugs.launchpad.net/hplip/+bug/1797501").

Edit /usr/share/hplip/data/models/models.dat to change [deskJet_3630_series] to [kJet_3630_series].

---

### Post by brian_p on 2019-02-18
> Edit /usr/share/hplip/data/models/models.dat to change [deskJet_3630_series] to [kJet_3630_series].

I had high hopes of seeing "SOLVED" in the suject line for this,

---

### Post by andrew_s4 on 2019-02-19
Hi Brian, as soon as I can get back to my desktop I&#8216;ll get to your very promising solution! I just don&#8216;t have the necessary time. The one thing that does worry me a little bit is, what do I do exactly with your line. As I am not very Terminal proficient...I am very grateful for your help and patience!

---

### Post by andrew_s4 on 2019-02-20
Ok, so I'm not literate enough to understand what it is I'm supposed to do with 
Edit /usr/share/hplip/data/models/models.dat to change [deskJet_3630_series] to [kJet_3630_series].
Andrew

---

### Post by brian_p on 2019-02-20
**Before** models.dat is edited, execute this command:

```
xsane -d hpaio:/net/deskJet_3630_series?ip=192.168.223.1
```

and report on the outcome. 192.168.223.1 is what you gave earlier for the IP address of the printer/scanner.

> Edit /usr/share/hplip/data/models/models.dat to change [deskJet_3630_series] to [kJet_3630_series].

I do not know which editor you would nornally use, so I'll show you with mine.

Open the file:

```
sudo nano /usr/share/hplip/data/models/models.dat
```

[list]Access the search facility with CTRL+W. Press the CTRL key; keep it down and then press "W". Release both keys, enter "deskjet_3630" in the search box and press the ENTER key.[/list]
[list]The cursor will now be on [deskJet_3630_series] . Change this to [kJet_3630_series][/list]
[list]Exit nano with CTRL+X (see above). You will asked whether to save the file. Make it so.[/list]
[list]Try scanning.[/list]

---

### Post by andrew_s4 on 2019-02-20
>  
 	Code:
 	xsane -d hpaio:/net/deskJet_3630_series?ip=192.168.223.1 
and report on the outcome. 192.168.223.1 is what you gave earlier for the IP address of the printer/scanner.

 	 		 			   
Here is the outcome:
sav@sav-desktop:~$ xsane -d hpaio:/net/deskJet_3630_series?ip=192.168.223.1
Gtk-Message: 13:52:27.555: Failed to load module "overlay-scrollbar"
Gtk-Message: 13:52:27.566: Failed to load module "canberra-gtk-module"
more to come...

---

### Post by andrew_s4 on 2019-02-20
>   	Code:
 	sudo nano /usr/share/hplip/data/models/models.dat 

[LIST]
[*]Access the search facility with CTRL+W. Press the  CTRL key; keep it down and then press "W". Release both keys, enter  "deskjet_3630" in the search box and press the ENTER key.
[/LIST]
  

Done... and this was the response:
[ "deskjet_3630" not found ]

---

### Post by brian_p on 2019-02-20
> Done... and this was the response:
[ "deskjet_3630" not found ] 

Then search for 3630. Your device has been supported since HPLIP 3.15.6 	.

---

### Post by brian_p on 2019-02-20
You can get a brand new version of models.dat with

```
apt-get --reinstall install libsane-hpaio
```

---

### Post by andrew_s4 on 2019-02-23
Hi, so back to it. After >  [COLOR=#000000]You can get a brand new version of models.dat with[/COLOR]

[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=&quot]apt-get --reinstall install libsane-hpaio[/FONT][/COLOR]  
I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kinit kio libhfstospell9 libkf5attica5 libkf5completion-data
  libkf5completion5 libkf5doctools5 libkf5globalaccel-bin
  libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5sane-data libkf5sane5 libkf5solid5 libkf5solid5-data
  libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5
  libllvm6.0 libvoikko1 sonnet-plugins
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/246 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 203684 files and directories currently installed.)
Preparing to unpack .../libsane-hpaio_3.17.10+repack0-5_amd64.deb ...
Unpacking libsane-hpaio:amd64 (3.17.10+repack0-5) over (3.17.10+repack0-5) ...
dpkg: error processing archive /var/cache/apt/archives/libsane-hpaio_3.17.10+repack0-5_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/hplip/data/models/models.dat', which is different from other instances of package libsane-hpaio:amd64
Preparing to unpack .../libsane-hpaio_3.17.10+repack0-5_i386.deb ...
Unpacking libsane-hpaio:i386 (3.17.10+repack0-5) over (3.17.10+repack0-5) ...
dpkg: error processing archive /var/cache/apt/archives/libsane-hpaio_3.17.10+repack0-5_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/hplip/data/models/models.dat', which is different from other instances of package libsane-hpaio:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libsane-hpaio_3.17.10+repack0-5_amd64.deb
 /var/cache/apt/archives/libsane-hpaio_3.17.10+repack0-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

According to HP Device Manager I already have HPLIP-3.19.1 version is installed


But on every bootup I get an error message from 

HPLIP Status Service :
No system tray detected on this system.
Unable to start, exiting.

I assume this is causing some problems?

---

### Post by andrew_s4 on 2019-02-23
Still no scanning possible... other than Vuescan. and the now constant error message at bootup from HPLIP...

---

### Post by brian_p on 2019-02-23
> Errors were encountered while processing:
/var/cache/apt/archives/libsane-hpaio_3.17.10+repack0-5_amd64.deb
/var/cache/apt/archives/libsane-hpaio_3.17.10+repack0-5_i386.deb

An amd64 system I suppose, but the package manager wants to install something for an i386 system. This is doomed to failure. You have a broken system.

> According to HP Device Manager I already have HPLIP-3.19.1 version is installed

You have altered the system. Return it to its 18.04 state. You do not need HPLIP-3.19.1.

> But on every bootup I get an error message from

HPLIP Status Service :
No system tray detected on this system.
Unable to start, exiting.

I assume this is causing some problems? 

Highly unlikely.

---

### Post by brian_p on 2019-02-23
> Done... and this was the response:
[ "deskjet_3630" not found ]

I know for a fact from the HPLIP source file  and the Debian packages that this entry is in models.dat and the HPLIP-3.19.1 package. You have a broken system. Why? Pass.

---

### Post by brian_p on 2019-02-23
> **andrew_s4 said:**
> Still no scanning possible... other than Vuescan. and the now constant error message at bootup from HPLIP...

You need a major operation to return your system to a semblance of normality.

---

### Post by andrew_s4 on 2019-02-23
>   [COLOR=#000000]You have a broken system.[/COLOR]  
What part of the system is broken? Ubuntu? HP? 
With the exception of scanning with HP everything works fine. I have done nothing other than letting things update themselves as the requests came. Somewhere in those updates something happened and it has screwed up my scanner.

---

### Post by oldfred on 2019-02-23
Are you getting a system tray issue?

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by brian_p on 2019-02-23
> **andrew_s4 said:**
> What part of the system is broken? Ubuntu? HP? 
With the exception of scanning with HP everything works fine. I have done nothing other than letting things update themselves as the requests came. Somewhere in those updates something happened and it has screwed up my scanner.

Trying to install an i386 package on an AMD64 system (or vice versa) would be a system problem. You could try to cure that by looking at /etc/apt/sources.list or with

```
apt update
```
```
apt upgrade
```

Not having the string 3630 in models .dat is an HPLIP issue but you have brought the problem on yourself in some way.

Not convinced about the 3630?

Download the 18.04 libsane-hpaio package:
```
wget http://nl.archive.ubuntu.com/ubuntu/pool/main/h/hplip/libsane-hpaio_3.17.10+repack0-5_amd64.deb
```
Unarchive the .deb.
```
ar -x libsane-hpaio_3.17.10+repack0-5_amd64.deb
```
Uncompress data.tar.xz.
```
unxz data.tar.xz
```
Extract files from data.tar.
```
tar -xf data.tar
```
Look at models.dat and search for 3630.
```
less usr/share/hplip/data/models/models.dat
```

Note that the path does not begin with "/".

You have been informed of the reason why you cannot scan. Rectifying it is easy - but not on a broken system.

---

### Post by brian_p on 2019-02-24
Restoring Network Scanning Functionality
=========================

The assumptions are made that the system's packaging services are working correctly and that the AIO has Bonjour broadcasting operative.

Remove all traces of any HPLIP installations:
[list]```
apt purge hplip hplip-data libsane-hpaio printer-driver-hpcups libhpmud0
```[/list]
[list]```
apt --purge autoremove
```[/list]
[list]```
rm -r /usr/share/hplip/
```[/list]
[list]```
rm -r /var/lib/hp
```[/list]

Install scanning functionality only:
```
apt install libsane-hpaio --no-install-recommends
```

Test for scanning availabilty (there will be a negative output):
```
scanimage -L
```
and read [https://bugs.launchpad.net/hplip/+bug/1817214/comments/1](https://bugs.launchpad.net/hplip/+bug/1817214/comments/1) 

Edit models.dat (as described previously) if it is desired to use xsane etc without a URI.

Restoring Network Printing Functionality
========================

[https://wiki.debian.org/QuickPrintQueuesCUPS#IPP_Printers](https://wiki.debian.org/QuickPrintQueuesCUPS#IPP_Printers)

---

### Post by andrew_s4 on 2019-02-25
Thank you Brian. Scanning now works after executing the codes in your last post. However, printing does not! Only using wifi and within Libre Office can I print. 
I have no idea what it is that this has done, other than the results. Is it now possible to somehow get my printer back!
Andrew

---

### Post by andrew_s4 on 2019-02-25
Sorry spoke too soon. After rebooting there is no longer a recognition of a scanner. Printer works on a driverless basis.

---

### Post by brian_p on 2019-02-25
> **andrew_s4 said:**
> Sorry spoke too soon. After rebooting there is no longer a recognition of a scanner. Printer works on a driverless basis.

Printing is ok. It uses nothing from models.dat, but scanning does consult models.dat. Check that there is a

[LIST]
[*][deskjet_3630_series]
[/LIST]
header and section in the file.

The URI for the scanner has to be

```
hpaio:/net/deskjet_3630_series?ip=<IP_address>
```
because it is the only URI format libsane-hpaio and libhpmud0 recognise. Are you saying that

```
xsane hpaio:/net/deskjet_3630_series?ip=<IP_address>
```
```
simple-scan hpaio:/net/deskjet_3630_series?ip=<IP_address>
```
do not work? The IP address has to be correct and "<" and ">" are not typed.

---

### Post by andrew_s4 on 2019-02-26
i don't know why I can't find the IP address of my printer. It's not listed on my router's home page under Connected devices. The printer is on and connected via wifi, but nowhere can I find it's ip address. Any other suggestions?

---

### Post by oldfred on 2019-02-26
My Deskjet 3520 has a tiny screen and in its menu under settings, wireless settings, advanced settings, ip summary is ip addresses.

---

### Post by brian_p on 2019-02-26
The output of
```
avahi-browse -rt _uscan._tcp
```

should show it. avahi-browse is in the avahi-utils package.

I am interested in what the command gives. Please post the output.

---

### Post by #&amp;thj^% on 2019-02-26
To get an overview lpinfo

Example
```

$ lpinfo -v | grep -P '://'
network dnssd://HP%20LaserJet%201022n._pdl-datastream._tcp.local/
network dnssd://TOSHIBA%20e-STUDIO2540C-07279076._printer._tcp.local/
network socket://192.168.20.201
network socket://192.168.20.203
network socket://192.168.20.204
network socket://192.168.20.205
network socket://192.168.20.206
network socket://192.168.20.207
network socket://192.168.20.43
```
Or even try:
```
lpstat -pPRINTER -l
```
Check through the printer information, as the IP address may be listed there, depending on your system.

---

### Post by andrew_s4 on 2019-02-26
Thank you Fred! Found it...

>  [COLOR=#000000]The URI for the scanner has to be[/COLOR]

[COLOR=#000000]Code:
hpaio:/net/deskjet_3630_series?ip=<IP_address>[/COLOR]
[COLOR=#000000]because it is the only URI format libsane-hpaio and libhpmud0 recognise. Are you saying that[/COLOR]

[COLOR=#000000]Code:
xsane hpaio:/net/deskjet_3630_series?ip=<IP_address>[/COLOR]
[COLOR=#000000]Code:
simple-scan hpaio:/net/deskjet_3630_series?ip=<IP_address>[/COLOR]
[COLOR=#000000]do not work?[/COLOR]  
Both worked when approached in this way. When I use Simple scan's icon to open it up, it can't find the scanner. Same for xsane.

---

### Post by andrew_s4 on 2019-02-26
Brian,

avahi-browse -rt _uscan._tcp
+ wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
= wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "ty=DeskJet 3630 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
+ wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
= wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "ty=DeskJet 3630 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]

---

### Post by brian_p on 2019-02-26
> **1fallen said:**
> To get an overview lpinfo

Example
```

$ lpinfo -v | grep -P '://'
network dnssd://HP%20LaserJet%201022n._pdl-datastream._tcp.local/
network dnssd://TOSHIBA%20e-STUDIO2540C-07279076._printer._tcp.local/
network socket://192.168.20.201
network socket://192.168.20.203
network socket://192.168.20.204
network socket://192.168.20.205
network socket://192.168.20.206
network socket://192.168.20.207
network socket://192.168.20.43
```
Or even try:
```
lpstat -pPRINTER -l
```
Check through the printer information, as the IP address may be listed there, depending on your system.

```
lpinfo -v
```

shows the IP for a socket URI in your example. Andrew isn't using a socket connection.

The -p option in the second command shows enabled printers. This isn't quite what is wanted.

---

### Post by brian_p on 2019-02-26
> 
Both worked when approached in this way. When I use Simple scan's icon to open it up, it can't find the scanner. Same for xsane.

```
xsane hpaio:/net/deskjet_3630_series?ip=192.168.223.1
```

There you are - you are now scanning. It was something you were not doing before. Objective achieved.

---

### Post by brian_p on 2019-02-26
> **andrew_s4 said:**
> Brian,

avahi-browse -rt _uscan._tcp
+ wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
= wlp58s0 IPv4 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "ty=DeskJet 3630 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]
+ wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
= wlp58s0 IPv6 HP DeskJet 3630 series [6779B6]               _uscan._tcp          local
   hostname = [HPF430B96779B6.local]
   address = [192.168.223.1]
   port = [8080]
   txt = ["duplex=F" "is=platen" "cs=binary,color,grayscale" "rs=eSCL" "representation=images/printer.png" "UUID=1c852a4d-b800-1f08-abcd-f430b96779b6" "note=" "adminurl=http://HPF430B96779B6.local." "ty=DeskJet 3630 series" "pdl=application/octet-stream,application/pdf,image/jpeg" "vers=2.5" "txtvers=1"]

Thanks.

[LIST]
[*]ty=DeskJet 3630 series
[/LIST]
is at the root of your issue.

---

### Post by andrew_s4 on 2019-02-26
> **brian_p said:**
> ```
xsane hpaio:/net/deskjet_3630_series?ip=192.168.223.1
```

There you are - you are now scanning. It was something you were not doing before. Objective achieved.

Yes, that‘s true! Thank you! However, do I have to use such a long winded way of getting a simple scan done? 
It must still be possible to use the scanning software with a simple click of the icon?


Andrew

---

### Post by brian_p on 2019-02-27
> **andrew_s4 said:**
> Yes, that‘s true! Thank you! However, do I have to use such a long winded way of getting a simple scan done? 
It must still be possible to use the scanning software with a simple click of the icon?
Andrew

You have done well to have got this far and to have stuck with it; many would have given up. It was unfortunate you met this bug in HPLIP.

I haven't any immediate ideas (or the incentive to find out) how to adjust the icon so that it does what you want, but would suggest you do a new post on what is required to determine the command the icon executes.

---

