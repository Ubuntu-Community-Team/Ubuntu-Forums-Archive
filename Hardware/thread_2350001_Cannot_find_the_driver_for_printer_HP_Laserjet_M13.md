---
title: "Cannot find the driver for printer HP Laserjet M130NW"
date: 2017-01-20
forum: Hardware
---

### Post by jimmi on 2017-01-20
In Ubuntu 16.10 I wanted to install the printer HP Laserjet M130NW connected via wifi.

The printer is correctly detected but in the list of drivers I cannot find the correct driver, which should be "HP LaserJet MFP m129-m134" shown in [this]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_mfp_m129-m134.html") page of hplip project.

Hplip is correctly installed, so I expecetd to see the driver among the others, but it isn't. How may I add it?

---

### Post by Autodave on 2017-01-20
Did you go into the "All Settings" and see if Linux sees the printer? Make sure printer is turned on, of course.

If it doesn't see it, go to the drop down menu and look for something close: that will usually work. (It has always worked for me.)

---

### Post by pdc on 2017-01-20
I had seen many HP supporters trumpet the support that HP provides for printers in linux: I thought hplip covered all their devices; however when I go to [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

and try my very best to find the HP LaserJet Pro MFP M130nw listed, under supported devices, I cannot see it; when I search on the product page, [http://support.hp.com/my-en/drivers/selfservice/hp-laserjet-pro-mfp-m130-series/9365370/model/9365372#Z7_3054ICK0K8UDA0AQC11TA930O2](http://support.hp.com/my-en/drivers/selfservice/hp-laserjet-pro-mfp-m130-series/9365370/model/9365372#Z7_3054ICK0K8UDA0AQC11TA930O2) then HP would only seem to say that mac and windows are supported; 

however it does not appear on the unsupported page [http://hplipopensource.com/hplip-web/supported_devices/unsupported.html](http://hplipopensource.com/hplip-web/supported_devices/unsupported.html) which till now, I did not know existed

---

### Post by ajgreeny on 2017-01-20
The nearest I can find is LaserJet Pro MFP m132nw, not the m130nw, but that may not matter.
[https://ubuntuforums.org/showthread.php?t=2350001&p=13596976#post13596976](https://ubuntuforums.org/showthread.php?t=2350001&p=13596976#post13596976)

I do note, however, that the minimum version of hplip needed for that printer is 3.16.11 which is newer that the version in Ubuntu 16.10, I think, so you may need to get the latest version direct from the site [http://prdownloads.sourceforge.net/hplip/hplip-3.16.11.run](http://prdownloads.sourceforge.net/hplip/hplip-3.16.11.run)

The install instructions for the hplip-3.16.11.run file you now have at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by pdc on 2017-01-20
"The nearest I can find is LaserJet Pro MFP m132nw, not the m130nw, but that may not matter." ........ indeed..... 

Interestingly, when I open the HP website for the HP LaserJet Pro MFP M132nw

I get this [http://support.hp.com/us-en/drivers/selfservice/HP-LaserJet-MFP-M129-M134-series/9365375/model/9365377](http://support.hp.com/us-en/drivers/selfservice/HP-LaserJet-MFP-M129-M134-series/9365375/model/9365377) ...... and it picks linux on this computer and offers that .......... whereas the M130 site only offered mac/win

and this aussie site [http://support.hp.com/au-en/document/c05228191](http://support.hp.com/au-en/document/c05228191) says linux compatible for the 132 as well ........... whereas the 130; on the aussie page; says no linux

---

### Post by ajgreeny on 2017-01-21
Don't go to the HP site itself; that will only have Windows and Mac files and is useless for your Linux OS.
Go to the second site I linked, download the hplip-3.16.11.run file and then install in the manner shown in the third link in my post.

---

### Post by efflandt on 2017-01-21
HP's PCL (printer control language) is usually backwards and forwards compatible, so all you usually need is something that is close for a printer driver. For example when at work we had something like a 1200 dpi HP LaserJet 2200 DTN I was able to print to it from WordPerfect 5.1 in MS DOS (on its parallel port) using an HP LaserJet III DOS driver which is an old 300 dpi printer. And when our HP printer failed, I temporarily used a cheap Lexmark X204n laser all-in-one in its place which emulated HP PCL (besides postscript) and we had no trouble printing to that without switching from HP drivers on PC's and remote HP-UX computer at our factory (by simply giving the Lexmark printer the same IP address that our HP printer had). The Lexmark was not capable of duplex, but the remote HP-UX computer did not use that anyway. Your printer does PCLmS, URF, PWG printer languages, so I would think that any HP driver with similar features would work.

Similarly when I first got a Lexmark C543dn color duplex laser before Ubuntu had a driver for it, that printer worked fine with a C534 Linux driver.

---

### Post by jimmi on 2017-01-22
Thanks everybody for your answer. I believe my question was not that clear. My obsesrvations were:
1. The printer is correctly identified when I want to add a new one
2. The wizard ask me to choose a driver among a list, but I cannot see any driver compatible. The list of Laserjet MFP ends with MFP M128
3. If I go to the [hplip site ]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_mfp_m129-m134.html") I can see a driver which has the same name of the driver in window: MFP M129-m134, therefore I suppose it is the correct one

Then I cannot understand why thhis driver is not include in the list offered by gnome inteface, despite the last hplip package is installed. Moreover I would like to understand how to add the driver present in hplip site to my list.

---

### Post by ajgreeny on 2017-01-22
You could try using hplip-gui which gives you a HP Toolbox which allows you to install the printer using the hplip itself, ratyher than the system Printing utility.

I am still not sure if you have the printer working in your Ubuntu installation, or if that is still your difficulty.
Have you installed that most recent version of hplip yet as it is needed for that printer model; the version of hplip you get from the repos in 16.04 is too old.

---

### Post by Autodave on 2017-01-22
Try closest one like I suggested before. At worst, it doesn't work and you delete it.

---

### Post by jimmi on 2017-01-23
Thanks  **ajgreeny** and **Autodave** for pointing that. Reading the release notes of hplip I can see tat the support for M129-M134 was added in the last revision 3.16.11, present in the next release 17.04. I will try to understand how to get it working in the present release.

---

### Post by leunam12 on 2017-01-23
Go to hplip download page, download hplip-3.16.11.run and run it from terminal.
```
chmod +x hplip-3.16.11.run
./hplip-3.16.11.run
```

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by ajgreeny on 2017-01-23
See my post #4 again for all details and links to the pages to download the hplip-3.16.11.run file and then install it.
It takes a few minutes to install but it is all done for you by the system and is just about foolproof.

Make sure you read the terminal output at each step as it guides you through while it installs it for you.

---

### Post by jimmi on 2017-01-24
Thanks again, hplip 3.16.11 installed and working for printing and fax. 

A further step is necessary in order to get the scanner working: from terminal send the command "hp-plugin", after that also Xsane works like a charm :)

---

### Post by ajgreeny on 2017-01-24
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

