---
title: "Lexmark X1150 Printer"
date: 2010-03-25
forum: Hardware
---

### Post by WarKirby on 2010-03-25
Hi folks. Running Ubuntu 9.10 Karmic

I'm trying to setup my printer, which is a Lexmark x1150, It predates my Ubuntu install, I didn't buy it for linux. Ubuntu doesn't find drivers for it automatically, I tried picking the closest one which I think is x1050 or somesuch, but that's not working.

The Lexmark site has no linux drivers for the X11xx series

A bit of googling found me an archived thread on this forum where someone apparently got it working, but couldn't print because they were out of ink. Said they were running out to get ink and would report on functionality shortly. That post was over 2 years ago, and he didn't post again after it.

I also found this: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

But it references a very old Ubuntu version, and the first relevant link to the Lexmark section on a gentoo wiki, is dead. So I'm unsure about proceeding farther in that direction.

Can anyone provide any help/advice on getting this setup ? Is it going to be possible ?

---

### Post by Crimsonjester on 2010-03-25
Kirby I am here with you in an exact situation. I have the newest Ubuntu with the Exact printer... Thank you for this thread.. I will be watching for any info and bring it back here....

---

### Post by anglican on 2010-03-26
> **WarKirby said:**
> Hi folks. Running Ubuntu 9.10 Karmic

I'm trying to setup my printer, which is a Lexmark x1150, It predates my Ubuntu install, I didn't buy it for linux. Ubuntu doesn't find drivers for it automatically, I tried picking the closest one which I think is x1050 or somesuch, but that's not working.

The Lexmark site has no linux drivers for the X11xx series

A bit of googling found me an archived thread on this forum where someone apparently got it working, but couldn't print because they were out of ink. Said they were running out to get ink and would report on functionality shortly. That post was over 2 years ago, and he didn't post again after it.

I also found this: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

But it references a very old Ubuntu version, and the first relevant link to the Lexmark section on a gentoo wiki, is dead. So I'm unsure about proceeding farther in that direction.

Can anyone provide any help/advice on getting this setup ? Is it going to be possible ?

This printer works fine (as a printer - not the scanner part). To install it try:

$ sudo apt-get install alien
$ mkdir lexmark
$ wget http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
$ tar -xvzf install.tar.gz
$ alien -t z600cups-1.0-1.i386.rpm
$ alien -t z600llpddk-2.0-1.i386.rpm
$ sudo tar xvzf  z600llpddk-2.0.tgz -C /
$ sudo tar xvzf z600cups-1.0.tgz -C /
$ sudo ldconfig 
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

I have one of these printing fine from karmic - and before that jaunty.

H

---

### Post by Crimsonjester on 2010-03-26
I am a noob and I don't understand the sudo install stuff. I have no idea how to do that and I would'nt even know where to go to do stuff like that. Is there a simpler way???

---

### Post by ubunterooster on 2010-03-27
Hi Crimson! I'll try to break it down better. First start the terminal (it's under accessories) in it type (or copy and paste):
1 ```
 sudo apt-get install alien 
``` (here we are telling the computer we are telling the computer to get packages for .rpm installing) press enter and give your password to the terminal. 

Or get the package called alien via synaptic

2 ```
 mkdir lexmark 
``` (here we make the directory for the driver)

3 ```
 wget [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz) 
``` (here we download the driver) [or just click the link]

4 ```
 tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz 
``` (unpaking the tar file)
5 ```
 tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz 
``` (here we begin installation)
6 ```
 tar -xvzf install.tar.gz 
``` (continuing install...)
7 ```
 alien -t z600cups-1.0-1.i386.rpm 
```
8 ```
 alien -t z600llpddk-2.0-1.i386.rpm 
```
9 ```
 sudo tar xvzf z600llpddk-2.0.tgz -C / 
```
10 ```
 sudo tar xvzf z600cups-1.0.tgz -C / 
``` (install itself finished, we still need to...)
11 ```
 sudo ldconfig 
``` (doing configuration)
12 ```
 cd /usr/share/cups/model 
``` (moving to a different folder to finish configuration)
13 ```
 sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz 
``` (completing configuration, hopefully)

---

### Post by Crimsonjester on 2010-03-27
Stopped at line 3 

tnt@tnt-desktop:~$ wget [http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.gz)
--2010-03-27 20:35:53--  [http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.gz)
Resolving [www.downloaddelivery.com](www.downloaddelivery.com)... 12.120.30.110
Connecting to [www.downloaddelivery.com|12.120.30.110|:80](www.downloaddelivery.com|12.120.30.110|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-27 20:35:53 ERROR 404: Not Found.

thats how far i got.... HELP !!!!

---

### Post by ubunterooster on 2010-03-27
It appears link is invalid. Try clicking the link and saving it to your home [not downloads] folder.

---

### Post by Crimsonjester on 2010-03-27
ok the package that I downloaded, I right clicked it and opened it then dragged it into the home file ..   /home/tnt/CJLZ600LE-CUPS-1.0-1(3).TAR

now what the heck do I do with it.....I changed my location and soon my sig....

---

### Post by ubunterooster on 2010-03-28
Go to step 4 unless you extracted it already, if you did extract it already go to 5

[BTW, It does not look that way, but I first really started using the terminal only two months ago]

---

### Post by Crimsonjester on 2010-03-28
ok now i have extracted it and have 2 items 


/home/tnt/CJLZ600LE-CUPS-1.0-1.TAR.gz


/home/tnt/CJLZ600LE-CUPS-1.0-1.TAR

wow what a p i t a   ... you fill in the blanks..... Do I need any special program for this nome or something??????????

---

### Post by Crimsonjester on 2010-03-28
dude this is horrible.. Why the heck is linux such a pain,,, now its saying alien isnt the root????? Thinkin bout buying a windows op system right now would be a lot easier

---

### Post by Crimsonjester on 2010-03-28
Roo you did good , I really appreciate you ... Thank you soooo much for your help.
You should check into being a mod, you are so smart and helpful.

it came up with an error bug log report thing... don't know man...

Stopped because the scheduler could not execute a filter...

Printer 'Lexmark" X1100-Series':'cups-insecure-filter'

I tried to debug it it just made the report and I saved it. Can I send it somewhere can i post it .. The company I am doing this for needs the printer to work.

---

### Post by ubunterooster on 2010-03-29
No offense, but I literally fell asleep at the "computer" Saturday night.

anglican did most of the work, I am just trying to get it to be simplified. I should PM him...

As for filing a bug report to launchpad (that's who you send it to), I do not think they will get it done anytime soon as likely they will not see it as important (due to the small number of users of that printer)
I am still looking for a workaround...

---

### Post by anglican on 2010-03-29
> **ubunterooster said:**
> No offense, but I literally fell asleep at the "computer" Saturday night.

anglican did most of the work, I am just trying to get it to be simplified. I should PM him...

As for filing a bug report to launchpad (that's who you sed it to), I do not think they will get it done anytime soon as likely they will not see it as important (due to the small number of users of that printer)
I am still looking for a workaround...

OK, I've fixed my original message so the link for the driver doesn't get mangled by the forum software, it can now be cut and pasted (but no-longer clicked on, you can't have it both ways :icon_frown:).

The error the installed filter is giving is due to incorrect ownership of the filter, the following commands should get rid of that:

sudo chown -R root.root /usr/lib/cups/filter
sudo chown -R root.root /usr/lib/cups/backend

H

---

### Post by ubunterooster on 2010-03-29
&#8251;Never mind this post&#8251;

---

### Post by anglican on 2010-03-30
[B]One more thing...

[/B]I seem to recall that the Z600 filter also requires the libstdc++5 library to run. This isn't available for Karmic (I guess that Canonical have dropped this as it's only needed for fairly old and out-of-date software) but you can install the Jaunty version which seems to work OK with Karmic. Download from:

[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

H

---

### Post by Crimsonjester on 2010-03-31
LOL I fixed it...... I Just formated the hard drive and installed windows... Now the Transcription program and the printer works, finished it in under 2 hours... Thanks for all your help guys...
<3 Crimson

---

### Post by ubunterooster on 2010-03-31
At least you got it working. 

[It's 1:00AM in your area! Get some sleep]

---

### Post by Crimsonjester on 2010-03-31
I did and it rained bonus..... Thanks Roo

---

### Post by anglican on 2010-05-18
> **anglican said:**
> [B]One more thing...

[/B]I seem to recall that the Z600 filter also requires the libstdc++5 library to run. This isn't available for Karmic (I guess that Canonical have dropped this as it's only needed for fairly old and out-of-date software) but you can install the Jaunty version which seems to work OK with Karmic. Download from:

[http://packages.ubuntu.com/jaunty/i386/libstdc++5/download](http://packages.ubuntu.com/jaunty/i386/libstdc++5/download)

H
Just a note for anyone stumbling upon this thread. OK, I finally got around to seeing what happens myself with my Lexmark x1150 . In Lucid (and also later Karmic kernels) there is a problem caused by usbfs no-longer being included in the kernel; usbfs was already deprecated and found to cause some problems with udev. Old drivers like z600, however, require it and will silently fail! There is a way to get the printer working, not IMO a terribly good way, but it works. You will need to give the following commands:
   
     ```
sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices 
```You can test that the printer driver is correctly installed with the command:
     
     ```
/usr/lib/cups/backend/z600 
```Which should give output something like:
     
                                                 > direct z600:/dev/usb/lp0 "Lexmark Lexmark X1150 Series" "Lexmark Printer"Once you've finished printing you might want to undo the above as it may well break other things, so type:
     
     ```
sudo umount /proc/bus 
```Hope this helps.

H

---

### Post by am.clark on 2010-09-02
Hi All,

I've got the same problem that the lexmark x1150 won't print. I've followed all the steps above and the computer "thinks" it has printed successfully, in that the print job is completed, but no printing is done on the printer.  I'm using Ubuntu 10.04.

Any help would be appreciated.

Cheers, Alan

---

### Post by anglican on 2010-09-10
> **am.clark said:**
> Hi All,

I've got the same problem that the lexmark x1150 won't print. I've followed all the steps above and the computer "thinks" it has printed successfully, in that the print job is completed, but no printing is done on the printer.  I'm using Ubuntu 10.04.

Any help would be appreciated.

Cheers, AlanWhich steps have you followed exactly... and what is the output of the command:

```
/usr/lib/cups/backend/z600
```
H

---

### Post by meka4996 on 2013-02-09
Hi, just to confirm with you all that I've just successfully got Lexmark X1150 to work in Ubuntu 12.10 Quantal Quetzal 64 bit by installing i386 AND amd64 versions of libstdc++5, and lexmark.z600-0.4.deb according to
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters) That's IT!!
Thanks & Enjoy!! =)

---

