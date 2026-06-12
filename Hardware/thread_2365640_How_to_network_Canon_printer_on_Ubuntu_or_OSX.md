---
title: "How to network Canon printer on Ubuntu or OSX"
date: 2017-07-08
forum: Hardware
---

### Post by L0key on 2017-07-08
I have a new Canon Pixma IP8720 photo printer connected with USB cable to ASUS RT AC66R wireless router that my Ubuntu 16.10 laptop connects to. I have no problem connecting to internet, my NAS, or a wirelessly connected Brother multi function B/W printer. The Canon does connect to my Win10 machine via the router with no apparent problems.

Logging into the Router I see the Canon 8729 as 'enabled' under the USB applications. I've spent considerable time online with Canon support  and other websites with no joy about connecting this Canon to OSx or Linux. Does anyone out their know how to access the settings in the printer (non display on this model) to check what it's setting s are? Canon talks about a kludgey piece of their software 'IJ Network' tools, but that doesn't seem to work on OSX and they provide no support on Linux.

Any Linux tools or commands that can let me connect directly to the printer controller via my router or the USB connection from the printer? The printer does install and seems to work when installed as a local Linux printer, but I really need to share this hardware for it to be useful.

---

### Post by yancek on 2017-07-08
The process is explained at the link below.  If you have problems post again with specifics on what you tried and results.

 [https://askubuntu.com/questions/513713/how-to-configure-a-network-printer-in-ubuntu-14-04](https://askubuntu.com/questions/513713/how-to-configure-a-network-printer-in-ubuntu-14-04)

---

### Post by pdc on 2017-07-09
Hi there LOkey; seems like you have been using Ubuntu since 2010 but haven't needed to post too many times? 

I am going to take a different tack and would suggest it is a real good idea to install the drivers that Canon supply for this printer so if you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100586102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100586102.html) and click to download and SAVE, you will be saving [COLOR="#008000"]cnijfilter-ip8700series-4.10-1-deb.tar.gz[/COLOR] to your Downloads directory;

you need to open a terminal: are you all good with that? ..... and you need to paste commands into the terminal: to paste commands, right-click at the text prompt in the terminal; look for PASTE in the menu that appears ............ all good to go? (After each paste, hit the ENTER key ......)

```
cd Downloads
```

```
tar -zxvf cnijfilter-ip8700series-4.10-1-deb.tar.gz
```

```
cd cnijfilter-ip8700series-4.10-1-deb
```

now we are ready to run the install script: watch the action carefully; ........... a chance it needs **[COLOR="#0000FF"]libtiff4[/COLOR]** and it will stop the install ...... if it does, get it from here [https://packages.debian.org/wheezy/libtiff4](https://packages.debian.org/wheezy/libtiff4) ... scroll down the page to find the amd64 version you need .. if you have 64bit ubuntu ..

so let's launch the install script 

```
./install.sh
```

that should do the driver install; find the printer and its address; and we hope set it up to print ... let us know how it goes ................

---

