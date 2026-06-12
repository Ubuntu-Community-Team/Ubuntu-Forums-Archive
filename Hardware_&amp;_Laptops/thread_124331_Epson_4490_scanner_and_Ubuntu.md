---
title: "Epson 4490 scanner and Ubuntu?"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by ulugeyik on 2006-02-01
I am using Ubuntu Linux (Breezy Badger). I can not get my Epson 4490 to work.

I have tried the following:

1) Downloaded the .rpm iscan-1.18.0-1.c2.i386.rpm
file.
2) Converted into a .deb file "alien iscan-1.18.0-1.c2.i386.rpm".
3) dpkg-i iscan_1.18.0-1.c2.i386.rpm
4) At this point "sane-find-scanner" finds something : found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:004:005
5)chmod 0666 /proc/bus/usb/004/005
6) "scanimage -L " does not find anything.

7) So, I tried fixing this problem by removing iscan, doing
apt-get install libsane libsane-extras
8) Trying to reinstall iscan gave an error. So I removed libsane-extras
9) "scanimage -L" still does not work.
10) I followed someone's advice and
edited /etc/sane.d/epkowa.conf and added:
usb 0x04b8 0x0119
11) now scanimage -L says
"device `epkowa:libusb:004:005' is a Epson flatbed scanner"
12) but iscan says "could not send command to scanner, check scanner's status".
13) I tried commenting out epson on /etc/sane.d/dll.conf and putting epkowa there. same result.

Any help is greatly appreciated.

Thanks

Ulugeyik

---

### Post by ulugeyik on 2006-02-03
Any suggestions? Please ":)

---

### Post by ganatronic on 2006-02-09
I'm going to buy this scanner soon. But I'm probably going to reformat my laptop and dual boot to windows. I just don't want to have to hassle with the ubuntu scanner issues -- plus it will be over my head, and my tolerance for spending days working on problems has run low. And I'd like to use the software they provide. Maybe some day it will be hassle-free on Ubuntu. But until then my scanning is more important than my choice of os.

Sorry I can't help!

---

### Post by ulugeyik on 2006-02-09
Hello,

Well, my first attempt at a temporary solution was to install qemu and windows 2000 but could not get the scanner working like that. So instead, I converted my qemu windows image to "vmdk" and used the free vmplayer. The scanner works like a charm and I do not need to have solutions like dual-booting.

Although, I still would like to get it working under Ubuntu directly. Second best would be to use it with Qemu instead of Vmplayer.

Anyway, I also suggest that you take that approach instead of dual-booting. I can provide instructions ifnecessary. 

ugdc

---

### Post by ganatronic on 2006-02-21
I got the scanner yesterday. At first I tried following [this thread]("http://ubuntuforums.org/showthread.php?t=108256") (though I was doing that because I was tired and misreading "4390" as "4490" - go me!). It didn't seem to do anything - I'm guessing because there's no entry for the 4490 in the libsane.rules files.

sane-find-scanner finds the usb scanner. but scanimage -L doesn't. 

So now I'm giving the iscan 1.18 a shot. But when I dpkg the deb I get:

```
dpkg: error processing /home/gratzer/iscan_1.18.0.1-3_i386.deb (--install):
 trying to overwrite `/usr/lib/sane/libsane-epkowa.la', which is also in package libsane-extras
```

I'm not sure why it can't overwrite. If you have any suggestions, that would be helpful.

If I get iscan installed but it still doesn't work (which I'm guessing will be likely), then I'll give qemu a try. I installed it (I live deep in the mountains, and I can't get my intel 537 dial-up modem to work, so I have to make the most out of cafe internet whenever I'm in town), but so far it looks a bit boggling. So I'll probably ask for a bit of help.

---

### Post by ganatronic on 2006-02-21
Putting iscan on hold for a moment, I've made a little progress with xsane. I basically followed all your steps from the first post (and also, I should note, did the stuff from the thread that I linked to in my last reply), but instead of trying to run iscan on step 12, I ran xsane. And it found the device. It hadn't ever done that before.

So xsane opens up, but if I try to scan or acquire preview I receive an error message saying:

*Failed to start scanner: Invalid Argument*

Perhaps I need to load settings, or something. 
"File > Info" shows the device, but not all the information is there. The "Model" line is blank. "Device" just says "002".

I browse around and look for more info on how to work xsane. I was so excited for a moment there when xsane actually started. Hopefully this will end up working.

---

### Post by ulugeyik on 2006-02-22
Hi,

Yes, I get the same from Xsane. I do not yet have a  solution. Iscan forums are not heavily populated enough to get anything out of them it seems. Although, there *is* a person who reported that it works with iscan.

---

### Post by ganatronic on 2006-02-23
Yeah, after a bit more tinkering I just concluded that until [this page]("http://www.sane-project.org/sane-backends.html") shows the 4490 under the "supported" section, it's safe to assume I won't get it working. 

I'll give qemu and vmware a try. Should I just go to [that big vmware how-to]("http://ubuntuforums.org/showthread.php?t=84275"), and follow it until I get it working? Or any other recommendations for qemu?

---

### Post by ulugeyik on 2006-02-23
I essentially followed this web-site:
[http://www.cri.ch/linux/docs/sk0020.html](http://www.cri.ch/linux/docs/sk0020.html)

I did not get qemu to work well with USB. IT seems to have problems. So I went the vmplayer way.

good luck.

---

### Post by LordBug on 2006-02-23
I had all kinds of grief getting my 3170 to work.  Epson scanners are a tad annoying.  I installed SANE, libsane-extras, and iscan.  This requires a bit of a hack, since there's a file conflict with a manpage (use apt-get and dpkg to see which one, I can't remember).  I found that just deleting it solves the issue and both libsane-extras and iscan will co-exist.  Uninstalling later might prove interesting, but I'll deal with that if I have to.

My 3170 also had a second iscan RPM file, a driver as best I can tell.  Does yours?  Install that too if so.  Beyond this, I can't remember all of the details I went through, but I did have to do some config file editting (/etc/sane.d/epkowa.conf, snapscan.conf, and epson.conf all were tinkered with.  Maybe others).  Somehow I got the thing to work.  I think the goat sacrifice finally did it.

---

### Post by rbmorse on 2007-02-02
> **ganatronic said:**
> Yeah, after a bit more tinkering I just concluded that until [this page]("http://www.sane-project.org/sane-backends.html") shows the 4490 under the "supported" section, it's safe to assume I won't get it working. 

I'll give qemu and vmware a try. Should I just go to [that big vmware how-to]("http://ubuntuforums.org/showthread.php?t=84275"), and follow it until I get it working? Or any other recommendations for qemu?

It's been a year, but I got my Epson 4490 working under Feisty Herd 3

step 1.  Install sane and related packages (libsane, libsane-extras, sane, sane-utils, xsane, xsane-common) All of these certainly are not required, but I do not know which ones are and which are not. That is just a list of what I have installed. 

step two. Connect and power up the scanner.

step three: make sure the scanner is detected. In a terminal windows run

sane-find-scanner

it should report :

    found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:001:006

The address at the end of the line will probably be different for you, depending on where you connect. If sane-find-scanner can't find a scanner at all, stop. You have to solve that problem first. Otherwise, 

step four - Get the 4490 linux driver package -- there are two files you need from

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

Answer their questionnaire. Select Perfection 4490 Photo. I told them I was using Debian and selected "other" in the version dialog. Clicking on the "next" button will take you to a download page 

step five: The source file will not build on Feisty, so take the two .rpm files (you need both of them) from the appropriate GCC version section for your distro. For Feisty, the GCC 3.4 files work.  

step six: If you haven't already done so, install alien so you can convert the .rpm files to .deb. (sudo apt-get install alien). 

step seven: convert the .rpm files. In a terminal window change to the directory where the two downloaded driver files are stored then: 

sudo alien iscan_2.5.0-1_i386.rpm
sudo alien iscan-plugin-gt-x750_1.0.0-2_i386.rpm

This should produce the two .deb packages:

iscan_2.5.0-1_i386.deb
iscan-plugin-gt-x750_1.0.0-2_i386.deb

there may be errors, ignore them. 

step eight: Install the two packages from a terminal window with dpkg, doing the main iscan package first.

sudo dpkg i- scan_2.5.0-1_i386.deb
sudo dpkg -i iscan-plugin-gt-x750_1.0.0-2_i386.deb

Step eight(a):

If the main iscan package will not install cleanly because it reports file conflicts with certain sane-related packages previously installed, just go ahead and force dpkg to overwrite the problem files:

sudo dpkg i- --force-overwrite iscan_2.5.0-1_i386.deb

The plugin should not have a conflict.

This completes the installation.  To test things out make sure the scanner is powered up and connected and then type 

iscan

from a terminal, It should start and identify the scanner.  Note the 4490 takes awhile to warm up, so don't do thing too quickly and don't be surprised if things just sit there for a few moments before anything starts to happen.  

Once iscan is installed, the xsane and quiteinsane front-ends also should find and control the scanner. I prefer quiteinsane to the other two, but you can try them and decide what best meets your needs.

---

### Post by weemikey on 2007-04-13
rbmorse, you're a sweetie.
I had tried just the first d/l from 'avasys', but on your advice added the second d/l.  I'm using Hamrick Software's scanner recognition program (I know, I had to pay for it, but it was worth not having the linux hassles) and now I have the Hamrick AND the iscan software to play with.
Pity we can't use all the other goodies on the installation discs: the dust clean up, the red-eye removal, oh well.  It seems like a good scanner for the  money.
Many thanks again.

---

### Post by Payteer on 2008-01-31
Hello,

I can't get the iscan_2.10.0-2_i386.deb to load, even with force overwrite, can you help on this?

---

### Post by luca.mg on 2008-02-23
try with xsane [http://ubuntuforums.org/showthread.php?p=4389626#post4389626](http://ubuntuforums.org/showthread.php?p=4389626#post4389626) 

ciao luca

---

