---
title: "Undo recent changes I did in teminal"
date: 2011-04-11
forum: Hardware
---

### Post by p1atypusx on 2011-04-11
I have a Sony laptop with built-in webcam.  Today I installed the Prey security software.  Better than nothing I guess.  When it used my webcam to take a picture the picture comes out upside down.  I decided to see if I could fix this.  I looked up several fixes for it and copy/pasted some "fixes."  Now the pictures on Prey don't come out at all or have green static lines through them.  On Cheese it still looks normal.  

Any suggestions.  How do I roll back any changes I made.  Is there a way?  Is there a way to just reinstall the r5u870 driver?

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks in advance.

---

### Post by Cheesehead on 2011-04-11
You haven't told us what you did, in order.
If we don't know what you did, it will be difficult for us to tell you how to undo it.

---

### Post by p1atypusx on 2011-04-11
I do remember following these directions.

> sudo add-apt-repository ppa:libv4l/ppa
Update your software list
sudo aptitude update
Install libv4l
sudo aptitude install libv4l-0

 I know I also followed these steps...

> In order to know if your webcam is UVC capable you just need to open your shell and run:
Code:
lsusb

you will get something like this:
Quote:
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID xxxx:yyyy "Your_Webcam_Model"
Bus 001 Device 001: ID 0000:0000
Then type:
Code:
sudo lsusb -d xxxx:yyyy -v | grep "14 Video"

If you get something like the following, your webcam is UVC capable:
Quote:
bFunctionClass 14 Video
bInterfaceClass 14 Video
bInterfaceClass 14 Video
bInterfaceClass 14 Video

If your webcam passes this test, you can go on reading. Otherwise, your camera needs to use propertary driver, because it doesn't use standard protocol/command.

Well,
now you need to donwload the UVCVIDEO driver sources, but they are on a SVN repository, so you need to install the SVN client:
Code:
sudo apt-get install subversion

and got these results...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


the next step was..

> svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk


and the results were..

> 
svn: No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'


So that probably didn't do anything.  

I then check Prey to see if the picture was upright and the pictures weren't only upside down, there was green static and I could barely see anything.  I have it updating every ten minutes and sometimes there is not pic (maybe connection prob) but teh green monster of a picture isnt because the pic was fine before (except for the upside down part.)

I then uninstalled the "firmware loader for cameras based on Ricoh r5u78x chipsets" and reinstalled it.  

I also installed guvcview to see if there were setting that I could adjust but it did not fix the issue.    

What can I do to resolve this?

---

### Post by Cheesehead on 2011-05-05
If the camera works fine in Cheese, then why do you think the camera is the problem?

---

