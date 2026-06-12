---
title: "HP 2300c Scanner &amp; SANE problems"
date: 2008-10-24
forum: General Help
---

### Post by ThaddeusW on 2008-10-24
*UPDATED* *FIXED!!!* Read on below

Ok I found my problem. Apparently I need to be root to scan. I suppose I have to figure out how to allow a non root user to scan now. I used the following command to make the scanner work:

```
sudo scanimage -d genesys:libusb:002:003 --format pnf > scan.pnf
```

Hello everyone, 

Ok I have an HP Scanjet 2300c USB scanner connected to my Ubuntu 8.04 box. My problem is even though it is detected, I cannot select it under the xsane or xscanimage. I also have a Hauppauge BT878 multi-input video card that is detected using the V4L driver. The video capture card is detected and works under xsane and I an use it to aquire images for both the Gimp and Openoffice. The scanner on the other hand is not detected at all by xsane :(  

When I run lsusb I see the scanner in the USB device list. I also ran sane-find-scanner and it detects the scanner but does not show the capture card. Here is the output:
```

found USB scanner (vendor=0x03f0, product=0x0901, chip=GL646_HP?) at libusb:002:003
```


 Then I ran scanimage -L and it only reports v4l:/dev/video0 which is my video capture card. 

```
device `v4l:/dev/video0' is a Noname BT878 video (Hauppauge (bt878)) virtual device
```

I was reading the SANE doc's and it said I should see a /dev/scanner in my /dev directory but no such scanner device exists in /dev. Maybe Debian/Ubuntu handles it different.

I cant figure out this problem for the life of me. Usually I can solve most problems on my own but this has me stumped. :confused:

---

### Post by pdwerryhouse on 2008-10-24
Not sure if this will help you, but I have almost exactly the same setup here (although under Debian, not Ubuntu):

* HP Scanjet 2200c USB scanner
* Hauppauge BT878 tv card

My setup works perfectly, though.

When I run scanimage -L, I get:

```
device `v4l:/dev/video0' is a Noname BT878 video (Hauppauge (bt878)) virtual device
device `plustek:libusb:005:002' is a Hewlett-Packard Scanjet 2200c flatbed scanner
```

I don't have a /dev/scanner device, either.

---

### Post by ThaddeusW on 2008-10-24
*Updated*

Ok I found that running scanimage -L as root shows my scanner and the backend. Now why it isnt working might be a problem of permissions?

Thanks for the reply. Hmmm I guess Debian doesent put the scanner right in the /dev directory. scanimage -L only shows the BT878 card, no scanner. I think it might have something to do with the backend for the 2300c which is genesys, your 2200 uses the plustek backend.      

Can you do me a favor and give me the output for sane-find-scanner? I want to see if it lists the backend before the USB address. Mine just shows the USB address: libusb:002:003. Your scanimage -L shows the backend as a prefix to the address. Maybe this is my problem, my backend isnt configured (that doesn't sound right lol.) Now my problem is the genesys doc links are broken on the sane site. Arrgh this is a pain.

---

### Post by pdwerryhouse on 2008-10-24
Sure thing:

```
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0605 [HP ScanJet 2200C], chip=LM9832/3) at libusb:005:002
found USB scanner (vendor=0x046d, product=0x0870) at libusb:004:003

```

The second device that it is finding there is a Logitech Quickcam, which is connected to this PC.

---

### Post by mgmiller on 2008-10-24
I had a similar problem with scangearamp instead of scanimage, but I think it's the same concept.

When scangearmp works successfully under root and not as user, it normally means that you have a permissions problem. The default permission rules for udev currently set scanners to belong to the root group and not to the scanner group. The most elegant method to solve this is to write a custom permissions rule and place it into /etc/udev/rules.d. This is achieved as follows:

Udev processes the rules files in /etc/udev/rules.d in lexical order, so your local settings should be stored in a file lexically ahead of the default 50-udev.rules so that they are processed first. The name of your new file must end in .rules, otherwise udev will ignore it.

create a new entry:
```
gksudo gedit /etc/udev/rules.d/10-udev.rules
```enter the following in the new file:
```
# scanner devices
KERNEL=="sg0", GROUP="scanner"
```Save the file.

Assuming hotplug is installed and working, simply unplug/replug in your scanner so that udev updates your permissions. Users in the scanner group can now use scangearmp.

---

### Post by pdwerryhouse on 2008-10-24
Ah, to get your scanner working for non-root users, add the usernames to the scanner group (and then log out, and back in again).

---

### Post by ThaddeusW on 2008-10-27
Thanks for the tips but still no dice. I added my user name to the scanner group and created the custom permissions rule 10-udev.rules in /etc/udev/rules.d. I even restarted the machine between the updates to be sure. I thought for sure it would work but it didn't. As for hotplug, not sure if it is installed or not and it doesn't appear to be an actual package name. I am not running a normal Ubuntu install, bare bones install and built up from there using Fluxbox as my wm.  

Even if I try to run xsane or kooka as root they crash when trying to scan color or have trouble operating the scanner properly. When scanning from the command line by default its greyscale and works fine. But if use the Color argument it scans and the scanner head tries to scan past the physical size of the bed and keeps crashing the head. I have to kill scamimage and unplug the scanner to reset it. Kooka doesn't control the scanner properly and Xsane warns against running as root and crashed when doing color. 

Very frustrating that such a simple process has become so complex. Why should a scanner by default belong only to root? Its just an input device not storage or something critical. I would hate to have to hook this think back to a windows box just to scan. The HP software alone make me homicidal when it comes to installing 300+MB of junk just to scan. But I will remain determined to fix this.

---

### Post by mgmiller on 2008-10-27
Some googling around revealed that your model scanner should have complete support in Linux (as do most HP devices).  Here is a link to the sane page on your scanner with links to the online manual.  Hopefully you can find something there about libraries you need to install.  

Since you did a bare bones OS, it's possible you're missing something.  

The instructions I gave above were what I used to get a "semi-supported" Canon scanner working for my son.  I needed to get drivers from canon Australia, for example as well as using the Australian canoscan linux software as xsane would not work.  

I also own an Epson 3200 scanner that was totally plug and play for every feature in the scanner.   Turn it on and xsane fires up and away you go.  I believe your HP scanner should also "just work" if you have all the libraries installed.

[http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=2300c&bus=usb&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=2300c&bus=usb&v=&p=)

One final thought.  Have you tried booting off an Ubuntu live CD and trying the scanner from that environment?  I suspect it will work normally.

Good luck.

---

### Post by ThaddeusW on 2008-10-28
mgmiller, 	
Thanks for the reply. You got me thinking and I realized I had no auto mounter installed for mounting external disks. I normally mount them as root and use sudo to copy to them. The same darn problem with the scanner, I need to be root! I did a quick Google for "ubuntu automounter" and found another post on this forum related to auto mounting USB disks and thier permissions. It mentioned two packages one was pmount, the other was gnome-volume-manager. I said the heck with it and installed them both. Rebooted and wouldn't you know it the darn scanner is now usable by non root users! WOO-HOO! 

BUT color still wont work. The scanner kind of spazes out, scans about 1/4 the bed length, stops spazes some more then returns. I do get a partial color image but with abnormal colors. Either something is wrong with the scanner or the sane backend is having trouble properly controlling the scanner. Greyscale works like a champ but still isn't what I need. Looks like I have to hook it back to the crusty P3 1ghz windowz box to test it. Darn.

---

### Post by mgmiller on 2008-10-28
> Looks like I have to hook it back to the crusty P3 1ghz windowz box to test it. Darn.

I still think you could test it by booting off a live CD.  If it's a supported scanner, it should just work.  xsane would be the interface.  Applications > Graphics > Xsane Image Scanner.  Run that with the scanner turned on and it should auto detect and be ready to go.

---

### Post by r2ramos on 2009-06-05
Hello ThaddeusW, did you ever got the HP scnajet 2300c color scanning working?
 
if you did please tell me how. I didnt´t have the "root issue" since i installed the scanner under jaunty and apparently did´n´t have that problem, but i can´t get the color scanning working, and i cant find in google or in this forum anyone else but you with this problem. 
 
By the way, gray scanning is flawless, but color scanning sucks...

---

