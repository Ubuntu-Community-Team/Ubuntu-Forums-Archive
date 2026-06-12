---
title: "Canon PIXMA MX340"
date: 2010-07-31
forum: Hardware
---

### Post by rbski69 on 2010-07-31
Need drivers for PIXMA MX340 Canon Printer. Ubuntu 10.4 LTS Operating System.

---

### Post by utilitytrack on 2010-08-02
Hello, look up here. 


drivers: [http://support-au.canon.com.au/P/search?model=PIXMA+MX340&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MX340&menu=download&filter=0&tagname=g_os&g_os=Linux) 
manuals: [http://support-au.canon.com.au/P/search?model=PIXMA%20MX340&filter=0&menu=Manual](http://support-au.canon.com.au/P/search?model=PIXMA%20MX340&filter=0&menu=Manual)


[]("http://support-au.canon.com.au/P/search?model=PIXMA%20MX340&filter=0&menu=Manual")good luck!

---

### Post by rbski69 on 2010-08-02
How do you install the driver downloads.

---

### Post by utilitytrack on 2010-08-02
All right, step by step. Special for you :) 
make sure that you plug a USB cable and turn on the device :D


1) download tarball with printer driver (**cnijfilter-mx340series-3.30-1-i386-deb.tar.gz**) and save it in your favorite directory (for example /home/Desktop/downloads/)


2) open your favorite terminal (e.g. roxterm or gnome terminal)


3) change your working directory: 

```
cd ./Desktop/downloads/
```
4) next, extract files from tarball:
```
tar -xvf ./cnijfilter-mx340series-3.30-1-i386-deb.tar.gz
```(don't forget use TAB key for autocompletion filenames)

5) look at this:
```
ls *
```
it will show something like
```
cnijfilter-mx340series-3.30-1-i386-deb/  cnijfilter-mx340series-3.30-1-i386-deb.tar.gz
```
6) again change working directory:
```
cd ./cnijfilter-mx340series-3.30-1-i386-deb/
```
7) look at this
```
ls *
```
will show 
```
install.sh*  packages/  resources/
```
8) ok, time for launch installer:
```
sudo ./install.sh
```
Give your password here. Ok, next all as in the manual:
```
Register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
>
```
Next, press Enter and choose how to connect with device. I strongly recommend USB.
For to register device, select your printer (as [FONT=Courier New]/dev/usb/lp0[/FONT])
After enter some simple printer name, you will set printer as default.

Check status (run this command as a non-root user)
```
cngpijmonmx340 [printer_name]
```

ENJOY




PS
I give here explanations for printer driver only. 


PPS
And finally, don't forget before reply about problems take manual (it's in the file **guidemx340series-pd-3.30-1_en.tar.gz**) and carefully read them.

---

### Post by utilitytrack on 2010-08-02
Also please mark this thread as solved

---

### Post by jd50i on 2010-09-13
I tried this but I could not get it to work, I got the message;

==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.30-1_i386.deb
dpkg: error processing ./packages/cnijfilter-common_3.30-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 ./packages/cnijfilter-common_3.30-1_i386.deb

---

### Post by CasPol on 2010-09-26
Hi everyone.

I also have a canon mx340. I have this file sitting in downloads,
can anyone explain to me what to do now ?

I do not know what this file is, and how to install it,

cnijfilter-mx340series-3.30-1-i386-deb.tar.gz

---

### Post by Shaggin Shea on 2010-11-21
> **CasPol said:**
> Hi everyone.

I also have a canon mx340. I have this file sitting in downloads,
can anyone explain to me what to do now ?

I do not know what this file is, and how to install it,

cnijfilter-mx340series-3.30-1-i386-deb.tar.gz

Go to applications > Accessories > Terminal

Terminal will open up and then you can pretty much start copy and paste the code from steps 3 to 8 into the terminal 1 at a time. To paste in the terminal hold ctrl + **** + v

Step 3 depends where you downloaded the file to. your code for step three if it is in your Downloads forlder as you say would be.

```
cd ./Downloads
``` you can copy and paste that instead of step three and then continue on with step four.

---

### Post by CasPol on 2010-11-21
Thanks guys, that got it working like a dream ....

---

### Post by underpope on 2011-01-02
Unfortunately, I'm getting the following error message when I attempt to install the driver:

An error occurred. The package management system cannot be identified.

I'm not sure how to proceed.

---

### Post by sKRiBEL on 2011-01-19
This works like a dream, Oh and posting here so I can find this thread for future reference.

---

### Post by riskbreaker927 on 2011-02-04
> **jd50i said:**
> I tried this but I could not get it to work, I got the message;

==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.30-1_i386.deb
dpkg: error processing ./packages/cnijfilter-common_3.30-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 ./packages/cnijfilter-common_3.30-1_i386.deb

Same issue for me, Ubuntu 10.10 amd64.

---

### Post by anfractuosities on 2011-03-05
I have a strange issue with the pixma mx430. When I send a job over wifi from ubuntu, it sits in my print queue for about 5 mins, and then it will print, but only about a 16th of the page and spits it out. 

The queue stills says processing, then it prints another page, this time printing a little more.

It eventually prints the entire page, and then the job disappears from the queue.

Any suggestions on where to start with this one? It is not the printer, because this is the second one.

thNka!

---

### Post by scda1234 on 2011-05-29
Works wifi and all on Ubuntu 11.04

---

### Post by rue1341 on 2012-02-28
For Ubuntu 11.10 64bit

Have a look at thread below  pages 1 and 5 which sorted me out.

[http://ubuntuforums.org/showthread.php?t=1518425](http://ubuntuforums.org/showthread.php?t=1518425)

It worked for me after many trying hours

Good luck

---

### Post by konradst on 2012-02-28
```
Register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
>
```
my computer does not detect the printer so at this point i have got only useless drivers installed which don't work even if I installed them later directly to cups (canon pixma mp250, ubuntu 11.10 32-bit, mp250 driver ofc)

---

