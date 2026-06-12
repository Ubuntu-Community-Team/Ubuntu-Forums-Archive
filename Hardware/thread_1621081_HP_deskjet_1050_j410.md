---
title: "HP deskjet 1050 j410"
date: 2010-11-13
forum: Hardware
---

### Post by Dark Shinobi on 2010-11-13
Seem to be having problems getting a HP deskjet 1050 j410 to work at all under lucid. The add a printer section just sees it as a 1000c and doest let me print, scan, or anything. Suggestions?

---

### Post by Dark Shinobi on 2010-11-15
Well its actually the 1055 j410 AiO, and I'm still having no luck :( Just got the hplip from the HP website, Ill give it a shot when I get home and see how that goes.

---

### Post by ichchhaankur on 2010-11-16
You will find what you need here:

[http://hplipopensource.com](http://hplipopensource.com)

---

### Post by ichchhaankur on 2010-11-16
Please remember to call HP and ask them to either make their printer CUPS compatible (preferred) or to provide drivers and instructions in the CD.

---

### Post by Dark Shinobi on 2010-11-16
Well the latest version of hplip from their website seems to have done the trick. Still no scanner function, but from what I have read its a very common and well known problem. A reply from HP is "We will be supporting your OS in a future release" which is the same thing I've read on forum after forum. Oh well can't win them all, thank you for your help. I'll keep pushing them to better support the Linux OS, and in particular Ubuntu. I am a college student and can honestly say its popularity is growing.

---

### Post by richlyn9 on 2010-11-28
> **Dark Shinobi said:**
> Well the latest version of hplip from their website seems to have done the trick. Still no scanner function, but from what I have read its a very common and well known problem. 

Can you name the version of lip that you have ...i believe you have Ubuntu Lucid 10.4 right.
 i have the same distro but it does not detect the device. And the official Hplip says that the scan feature is unsupported (such a sad thing)

BTY its good to hear that you like Ubuntu!!:p

---

### Post by Dred on 2010-12-16
> **Dark Shinobi said:**
> Well the latest version of hplip from their website seems to have done the trick. Still no scanner function, but from what I have read its a very common and well known problem. A reply from HP is "We will be supporting your OS in a future release" which is the same thing I've read on forum after forum. Oh well can't win them all, thank you for your help. I'll keep pushing them to better support the Linux OS, and in particular Ubuntu. I am a college student and can honestly say its popularity is growing.Hi,

For the time being as a work around, please do the following steps;

Open /usr/share/hplip/data/models/models.dat file as root. Go to section [deskjet_1050_j410_series] and set "io-mfp-mode=1" and "scan-type=7" and save the file.

Now your scan should work.

---

### Post by Pirschjaeger on 2010-12-23
I just bought the same printer today. Unfortunately no one was able to help me get online at the shops to check out the compatibility with Ubuntu so I decided to just take a chance. As luck would have it, when I connected it to my laptop the printer was detected but not the scanner. But, I couldn't even print out a test page.

I've tried editing the dat file as you've prescribed and I can now at least print. Sadly, the scanner doesn't work. Is it possible you've missed another setting?

To make matters worse, I bought it primarily for the scan function as I need to prepare some work in a hurry.

---

### Post by Dred on 2010-12-23
> **Pirschjaeger said:**
> I just bought the same printer today. Unfortunately no one was able to help me get online at the shops to check out the compatibility with Ubuntu so I decided to just take a chance. As luck would have it, when I connected it to my laptop the printer was detected but not the scanner. But, I couldn't even print out a test page.

I've tried editing the dat file as you've prescribed and I can now at least print. Sadly, the scanner doesn't work. Is it possible you've missed another setting?

To make matters worse, I bought it primarily for the scan function as I need to prepare some work in a hurry.Okay...this is from memory.

1. Download the [hplip-3.10.9.tar.gz from SourceForge]("http://sourceforge.net/projects/hplip/files/hplip/3.10.9/hplip-3.10.9.tar.gz/download") to your desktop.
2. Extract Here, Open the untarred folder and find the models.dat.
3. Go to section [deskjet_1050_j410_series] and set "io-mfp-mode=1" and "scan-type=7" (don't forget to remove the DASH from the -1 on scan-type=-1 default also, it happened to me...lol) and save the file.
4. Open a terminal
5. (if you're not already root) enter ```
sudo -i
```
6. enter root user password (if requested)
7. enter ```
cd hplip-3.10.9/
``` (not sure about the backslash)
8. enter ```
./configure
``` (let it finish)
9. enter ```
make
``` (let it finish)
10. enter ```
make install
``` (let it finish)
11. close terminal and restart Ubuntu (you may not need to but I do it anyway)
12. After reboot, turn on the printer, go to Accessories and click on the HP icon to open the HP Device Manager...you should see Scan under the Actions tab.

---

### Post by Pirschjaeger on 2010-12-25
Hi Dred,

I've already downloaded and installed the file and while I have 'scan' in the HP options, it still fails. I've tried in vain both Simple Scan and Xsane.

The easiest thing to do would be to order a scanner online but there are a few obstacles:

1) I live in China but don't speak Chinese.

2) There are issues with trust when it comes to ordering anything here.

3) The Sane list of in/compatibility is just too long and complex to print out and carry.

4) It's too far and too complicated to run back and forth to a store. I did try checking the net at the shops but everyone uses Windows on dinosaur systems and inadequate net connections. In short, I was unable to access the sites I needed.

I have the worse luck for choosing hardware. I always seem to chose something incompatible with Linux or discontinued. If anyone is worried about making the same mistakes they should first ask what I would by and then stay far away from my recommendations. :)

I've needed to build a new rig for sometime now but have been putting it off for the reasons mentioned above. It would be a great service for people if there were a site when you could pick and choose hardware and get instant feedback on compatibility. Alas we live not in a perfect world.

I've infected/installed one of my rigs with Windows/Linux dual-boot so I can at least use the scanner on that.

Thanks for the help.

---

### Post by Dred on 2010-12-26
> **Pirschjaeger said:**
> Hi Dred,

I've already downloaded and installed the file and while I have 'scan' in the HP options, it still fails. I've tried in vain both Simple Scan and Xsane.

The easiest thing to do would be to order a scanner online but there are a few obstacles:

1) I live in China but don't speak Chinese.

2) There are issues with trust when it comes to ordering anything here.

3) The Sane list of in/compatibility is just too long and complex to print out and carry.

4) It's too far and too complicated to run back and forth to a store. I did try checking the net at the shops but everyone uses Windows on dinosaur systems and inadequate net connections. In short, I was unable to access the sites I needed.

I have the worse luck for choosing hardware. I always seem to chose something incompatible with Linux or discontinued. If anyone is worried about making the same mistakes they should first ask what I would by and then stay far away from my recommendations. :)

I've needed to build a new rig for sometime now but have been putting it off for the reasons mentioned above. It would be a great service for people if there were a site when you could pick and choose hardware and get instant feedback on compatibility. Alas we live not in a perfect world.

I've infected/installed one of my rigs with Windows/Linux dual-boot so I can at least use the scanner on that.

Thanks for the help.For a new rig try Newegg.com and get a combo package. My 3.1 GB PC cost me all of 253 dollars (of course I had to put it together myself) and I used the HDD from my old PC instead of buying a new one and thus saved myself the cost of that.
Just a suggestion.

---

### Post by Biosd on 2010-12-26
> **Dred said:**
> Okay...this is from memory.

1. Download the [hplip-3.10.9.tar.gz from SourceForge]("http://sourceforge.net/projects/hplip/files/hplip/3.10.9/hplip-3.10.9.tar.gz/download") to your desktop.
2. Extract Here, Open the untarred folder and find the models.dat.
3. Go to section [deskjet_1050_j410_series] and set "io-mfp-mode=1" and "scan-type=7" (don't forget to remove the DASH from the -1 on scan-type=-1 default also, it happened to me...lol) and save the file.
4. Open a terminal
5. (if you're not already root) enter ```
sudo -i
```6. enter root user password (if requested)
7. enter ```
cd hplip-3.10.9/
``` (not sure about the backslash)
8. enter ```
./configure
``` (let it finish)
9. enter ```
make
``` (let it finish)
10. enter ```
make install
``` (let it finish)
11. close terminal and restart Ubuntu (you may not need to but I do it anyway)
12. After reboot, turn on the printer, go to Accessories and click on the HP icon to open the HP Device Manager...you should see Scan under the Actions tab.

Following this guide, I have come upon an error, here is the output: [http://pastebin.com/3rWWUiag](http://pastebin.com/3rWWUiag)

configure: error: cannot find net-snmp support (or --disable-network-build)

---

### Post by Dred on 2010-12-26
> **Biosd said:**
> Following this guide, I have come upon an error, here is the output: [http://pastebin.com/3rWWUiag](http://pastebin.com/3rWWUiag)

configure: error: cannot find net-snmp support (or --disable-network-build)Then for step 8 use ```
./configure --disable-network-build
```

---

### Post by Biosd on 2010-12-26
> **Dred said:**
> Then for step 8 use ```
./configure --disable-network-build
```

...And that gives me a new problem "configure: error: cannot find libcups support"

Libcups2 is already installed. So... I'm guessing its not looking in the right place? I'm building it from the desktop if thats a problem.

---

### Post by Dred on 2010-12-26
> **Biosd said:**
> ...And that gives me a new problem "configure: error: cannot find libcups support"

Libcups2 is already installed. So... I'm guessing its not looking in the right place? I'm building it from the desktop if thats a problem.Maybe try a re-install of libcups? I don't know because I didn't get any install errors during my install.

---

### Post by Biosd on 2010-12-26
> **Dred said:**
> Maybe try a re-install of libcups? I don't know because I didn't get any install errors during my install.

Nopes. I tried reinstalling all the libcups2 stuff, I even rebooted. Still same error. One other theory is that its looking for libcups 1. But thats a stretch. 

I'm going to have to probably return the printer for another... unless someone else can find a solution.

---

### Post by du@dde on 2010-12-29
> **Biosd said:**
> Nopes. I tried reinstalling all the libcups2 stuff, I even rebooted. Still same error. One other theory is that its looking for libcups 1. But thats a stretch. 

I'm going to have to probably return the printer for another... unless someone else can find a solution.

I guess it is the dev-package (libcups2-dev) that is needed at configure time.

---

### Post by chrisbailey on 2010-12-29
Having bought this same printer last week (I thought HP was supposed to be Linux friendly!) I have exactly the same problem as Biosd, so have been following this closely. Thanks for this latest advice du@dde - it does move things forward, but doesn't quite get there. The new error is "error: cannot find libusb support".

Any idea how to get this?

---

### Post by du@dde on 2010-12-31
@chrisbailey: Pretty much the same issue. When you're building code that uses libusb you need the libusb-dev package which contains headers and some other stuff. If you normally don't build a lot of code on your machine you will need to install several dev-packages to get through the configuration of this driver.

Even when the configuration was done some headers were missing and I got compilation errors. I installed the remaining libcups-dev packages and it resolved the issue.

---

### Post by dwhitney67 on 2011-01-13
> **chrisbailey said:**
> Having bought this same printer last week (I thought HP was supposed to be Linux friendly!) I have exactly the same problem as Biosd, so have been following this closely. Thanks for this latest advice du@dde - it does move things forward, but doesn't quite get there. The new error is "error: cannot find libusb support".

Any idea how to get this?

I just bought this printer too; apparently the HPLIP package available with Ubuntu 10.04 is not up to date.

But you can follow these [instructions]("http://winunixmac.com/tips-and-tricks/74-how-to-configure-a-hp-deskjet-1050-on-ubuntu") to get a later version; just skip to step 2.

Anyhow, I setup my printer using the USB cable, and it works.  Then I proceeded to connect my USB cable to my iogear networked device.  When I went through CUPS (localhost:631), to my surprise the appropriate PPD driver was now listed.

In summary, for $40, I'm happy.

---

### Post by Professor Ducky on 2011-01-19
I wrote this as a quick fix to automate the fixes shown on this thread. Since you helped me, I thought I could at least share what I have used.

#!/bin/bash

LINE=$(grep deskjet_1050_j410_series /usr/share/hplip/data/models/models.dat -n -A 60 | grep "io-mfp-mode=" | cut -d "-" -f 1)
sed -i.bak "$LINE s/io-mfp-mode=.*/io-mfp-mode=1/" /usr/share/hplip/data/models/models.dat
LINE=$(grep deskjet_1050_j410_series /usr/share/hplip/data/models/models.dat -n -A 60 | grep "scan-type=" | cut -d "-" -f 1)
sed -i.bak "$LINE s/scan-type=.*/scan-type=7/" /usr/share/hplip/data/models/models.dat

---

### Post by Professor Ducky on 2011-01-19
I wrote this as a quick fix to automate the fixes shown on this thread. Since you helped me, I thought I could at least share what I have used.

#!/bin/bash

LINE=$(grep deskjet_1050_j410_series /usr/share/hplip/data/models/models.dat -n -A 60 | grep "io-mfp-mode=" | cut -d "-" -f 1)
sed -i.bak "$LINE s/io-mfp-mode=.*/io-mfp-mode=1/" /usr/share/hplip/data/models/models.dat
LINE=$(grep deskjet_1050_j410_series /usr/share/hplip/data/models/models.dat -n -A 60 | grep "scan-type=" | cut -d "-" -f 1)
sed -i.bak "$LINE s/scan-type=.*/scan-type=7/" /usr/share/hplip/data/models/models.dat

---

### Post by Professor Ducky on 2011-02-01
If you were not aware the HPLIP 3.11.1 driver should fix this problem now.

---

### Post by dwhitney67 on 2011-02-01
> **Professor Ducky said:**
> If you were not aware the HPLIP 3.11.1 driver should fix this problem now.

I'm not sure who you are addressing, but I discovered that with HPLIP 3.10.9 that the printer worked fine.  See my earlier [post]("http://ubuntuforums.org/showpost.php?p=10353905&postcount=20").

---

### Post by Shobuz99 on 2012-02-12
Since the thread has not been "closed", I thought it would be ok to ask a related question. 
It is now over a year later, and I had the same problem getting the HP 1050 j410 to work with Ubuntu 10.04 LTS. 
Professor Ducky is correct that the HPLIP 3.11.1 driver corrected my problem. It is now working fine on an AMD 64 machine.

My question is, is it possible to make this printer a 'network'  printer by using a direct connection to a Linksys WRT54GS router?
Since the HP 1050 j410 has a USB connection; I thought I could use a USB to CAT5 converter connector and go directly into the router. 
This has not worked so far. Is it possible to make the HP 1050 j410 a network printer? If so, how? Thanks for any ideas or help.
Shobuz99

---

### Post by dwhitney67 on 2012-02-13
> **Shobuz99 said:**
> Since the thread has not been "closed", I thought it would be ok to ask a related question. 
It is now over a year later, and I had the same problem getting the HP 1050 j410 to work with Ubuntu 10.04 LTS. 
Professor Ducky is correct that the HPLIP 3.11.1 driver corrected my problem. It is now working fine on an AMD 64 machine.

My question is, is it possible to make this printer a 'network'  printer by using a direct connection to a Linksys WRT54GS router?
Since the HP 1050 j410 has a USB connection; I thought I could use a USB to CAT5 converter connector and go directly into the router. 
This has not worked so far. Is it possible to make the HP 1050 j410 a network printer? If so, how? Thanks for any ideas or help.
Shobuz99

There are two ways:  a) use a USB-to-CAT device (I personally use one made by IOGear), or b) hook the printer directly to the computer and make it shareable.

The caveat with option b is that the particular computer (print server) must always be powered on for other systems to use it.

Anyhow, for option a, my IOGear device is configured with a fixed-IP address, and I plug it onto my router.  When setting up the printer, choose "lpd" type of printer connection (e.g.  lpd://192.168.1.50/hp1050).  You can easily set this up using CUPS via the HTTP interface pages it provides; simply goto [http://localhost:631](http://localhost:631).

P.S.  Attached is a screenshot of my printer's configuration (where iogear, which is used in the lpd URL, is defined in my /etc/hosts file).

---

### Post by vidyadhara on 2012-02-14
I got hplip from the hplip website as suggested. And it worked fabulously right away.

I am running ubuntu 10.04.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Never did a printer work so famously on linux before. 
And I have no prior experience with running a scanner on linux.

This is terrific.

It also has a jazzy color histogram makes me feel like flash gordon on his first space flight.

---

### Post by vidyadhara on 2012-02-14
Oh,
And I forgot to add this is hplip 3.12.2

---

### Post by seravb on 2012-08-01
> **ichchhaankur said:**
> You will find what you need here:

[http://hplipopensource.com](http://hplipopensource.com)

Thank you very much! from Spain ;) (Muchas gracias)

---

