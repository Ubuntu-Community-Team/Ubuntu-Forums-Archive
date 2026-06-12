---
title: "my Brother mfc 235c printer is driving me crazy!"
date: 2008-07-05
forum: Hardware
---

### Post by pol-kilo on 2008-07-05
I have alredy installed every possible driver for my Brother printer and it seems to be connected, but it still won't not print =(

[[IMG]http://img530.imageshack.us/img530/5536/screenshotik0.th.jpg[/IMG]](http://img530.imageshack.us/my.php?image=screenshotik0.jpg)

any ideas? :cry:

---

### Post by pol-kilo on 2008-07-05
anyone??

---

### Post by TopEnder on 2008-07-06
Hi,

You do not mention what version of Ubuntu/Kubuntu you are using, the following Posts gives a very good description of HowTo at
Ref #1
[http://ubuntuforums.org/showthread.p...other+printers](http://ubuntuforums.org/showthread.p...other+printers)

Ref #2
Also look in System/Adminstration/Synaptic Package manager (Ubuntu). You may find the following packages for your MFC-235C
brother-lpr-drivers-extras
brother-lpr-drivers-commonnon
brother-cups-wrapper-extra
brother-cups-wrapper-common,
check the Repo to make sure the above drivers are for your MFC-235C (highlight and your MFC235C should be shown). If these packages are there, Un-install what you have already installed (trying to get the MFC135C working) and use these packages to get the printer side of the MFC-235C working.
If the packages are not there then follow the posts in Ref #1 Make sure the Printer is diconnected from the power and the USB cable is disconnected for both solutions.
As yet there are no drivers for the Scanner side of the MFC235C, so you need to follow the scanner direction in Ref #1. there is some very goog information within the Post but you will need to read through all the posts in Ref #1 and maybe download (save) for reference, until you are up printing and scanning.

If you still have problems the ask Brother (Help). As you go through installing both Printer & Scanner write down what you did as it could help other members wishing to install other Brother Printers/Scanners.

---

