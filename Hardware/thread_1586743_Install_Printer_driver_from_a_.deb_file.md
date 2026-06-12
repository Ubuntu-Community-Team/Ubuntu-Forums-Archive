---
title: "Install Printer driver from a .deb file"
date: 2010-10-02
forum: Hardware
---

### Post by Ed_Ziffel on 2010-10-02
Hi all,

first, am I in the right forum?

I need to be able to install a printer driver that is not in the Ubuntu printers list but does have a driver listed both as a .rpm and a .deb (but no ppd) file on the printer website.  

There are some instructions on how to do this, but following these using the terminal failed.  

I'm not sure about cups, lpr, or doing the rpm or deb install.  Is there someone who has expertise with such things and I am in the right forum? I will gladly provide specifics, ie file names, error messages, system etc.

Thanks

Ed

---

### Post by roger_1960 on 2010-10-02
Hi

Normally you can download the .deb file to your PC and then double click on it and a GUI deb installer will start up.

---

### Post by Ed_Ziffel on 2010-10-02
Thanks for the reply.  

here are my choices for the file to download
 

HL-3040CN
Download	      Format	Version	Size	Release Date
lpr driver 	        rpm 	1.1.1-4 	623 KB 	2009.Sep.24
cupswrapper driver 	rpm 	1.1.1-4 	14 KB 	2009.Sep.24
lpr driver 	        deb 	1.1.1-4 	617 KB 	2009.Sep.24
cupswrapper driver 	deb 	1.1.1-4 	12 KB 	2009.Sep.24

# Install Instruction : lpr driver | cupswrapper driver | 

Which one should I use? And how/where should I unzip it?

It is for a brother HL 3040CN.  Ubuntu recognizes the printer on the network

Thanks.

---

### Post by IcarusR on 2010-10-02
You need to install the .deb files.

'lpr driver' is a depandancy of 'cupswrapper driver' so I'd install both by simply double clicking on them, lpr first. 
This will launch gdebi which will install them.
Then you should be able to go to System > Administration > Printing > Add & get your printer to work.

---

### Post by Ed_Ziffel on 2010-10-02
Okay I have tried that.  I get an error message that either I don't have permissions or that the file is corrupt.  So naturally I re-downloaded the files from the brother site and tried again with the same results.  
Should I do a Skudo in the terminal window first or how would I attempt to open it with root permissions.

---

### Post by Ed_Ziffel on 2010-10-03
Hi again,

First let me thank the people who have answered my post. 

I'm still trying to get my Brother HL-3040 network laser printer to work with Ubuntu.  Using system>adminstration>printing>add>select devices>Network Printer I am able to the printer but there is no ppd file on the linux Brother driver page.  

it does have an lpr driver and cupswrapper driver.  both in deb format. 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN)


 I have downloaded them, but double clicking them results in following error message:

[COLOR="Red"]Could not open 'hl3040cncupswrapper-1.1.1.1-4.i386.deb'

The package might be corrupted or your are not allowed to open the file.  Check the permissions of the file.
[/COLOR]

I checked the permission: for my user I have Read and Write.  I added execute to to the lpr file:

-rwxr--r-- 1 betty2 betty2 617464 2010-10-02 10:04 hl3040cnlpr-1.1.1-4.i386.deb
  
But still get the same error.  

To me it is not unbelievable that a Brother driver is bad but in the instructions is also:

# Pre-required Procedure (10)
    Related distributions
    Ubuntu8.04, 8.10
    Related products/drivers
    P-touch/QL-Printer drivers
    Requirement
    1. "sudo aa-complain cupsd" command is required before the installation.
    2. "sudo mkdir /usr/share/cups/model" command is required before the installation. 

So I did this as well which turns off the security and makes the new directory but still no help.

Is there something else I should try?  

This is not the end of the world as I at least dual boot or triple boot my machines with XP and Ubuntu or with XP,7 and Ubuntu all with a shared storage logical drive.  I prefer using Ubuntu and only use windows when like this I have no choice which is why the need for this printer to work.

thanks

---

### Post by nc_jed on 2010-10-03
> **Ed_Ziffel said:**
> 

-rwxr--r-- 1 betty2 betty2 617464 2010-10-02 10:04 hl3040cnlpr-1.1.1-4.i386.deb



Fo fun, can you chmod it to 777 (full access) and see what you get?  sudo chmod 777 hl3040cnlpr-1.1.1-4.i386.deb 

and then (from the terminal), run: sudo dpkg -i hl3040*.deb

-Jed

---

### Post by Ed_Ziffel on 2010-10-03
Great idea!  Tried it but no go.  Put an email into Brother.  They say they will get back to me in one business day.  Oh Yeah!  U bet cha!  On the other hand, who knows?  I asked if it would be a lot of trouble just to get a ppd file.  We'll see and thanks for the useful multi useful tip.

---

### Post by wojox on 2010-10-03
This is how I installed mine. [Install manually]("http://ubuntuforums.org/showpost.php?p=9100367&postcount=14") 

Just swap lpr and cupswrapper number for yours.

---

### Post by sampon on 2010-10-06
Hi!
I've already posted that question on an other forum. I hope that somebody might help me
 
We have a small office with 3 macs, 2 (fresh) ubuntu 10.04 PCs and 2 Windows PC-s. 
Some are behind a router or 2 switches. we also have a several Voip lines.
the printer goes like this: modem-router-switch-switch-printer
 
The driver given with the 3040 is great for windows and macs. They print all very well. 
 
For the Ubuntu machines I downloaded the driver from the Brother site. And tried to do what they say. 
 
I just can't get the printer to work with ubuntu. after installing the driver - CUPS. 
 
In the printer setting the network sees the brother. but it still say the printer is inactive. 
 
I succeeded to get an ubuntu print page test... but I don't know how.  after it did not print at all - saying the printer is inactive. 
one of the Ubuntu PC is connected to the network throuhg WIFI. (The macs also-and thye work)  
 
I also tried to have only one switch before the printer.

I'm not really familiar to linux systems/language yet- 
 
Does anybody has a clue ?

Thanks a lot!

Sampon

---

