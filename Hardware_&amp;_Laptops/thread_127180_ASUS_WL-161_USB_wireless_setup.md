---
title: "ASUS WL-161 USB wireless setup?"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by jingo811 on 2006-02-08
Hi I've searched like mad for a long time now making Ubuntu find my Wireless USB and be able to connect to Internet.  Which I can do without problem in Win XP.

So the closest solution was to go to ASUS website and download their wireless driver:
**ASUS WL-161 USB pen type adapter Linux driver (Kernel 2.4.5)**
[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)
But I don't understand the installation procedures in their readme file:
[http://web.telia.com/~u87415110/Symbios/TEXT%20POR.DOC](http://web.telia.com/~u87415110/Symbios/TEXT%20POR.DOC)
I'm guessing that section 3 and 4 are the most relevant to me?

Since I'm a newbie I've never installed stuff before on Linux but from browsing this tutorial:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
I couldn't understand or implement the source installation steps.  It's to much technical talk for me to follow.
Need simple directions as to what I should do to install those ASUS drivers for Ubuntu?

---

### Post by az on 2006-02-08
[QUOTE=jingo811]Hi I've searched like mad for a long time now making Ubuntu find my Wireless USB and be able to connect to Internet.  Which I can do without problem in Win XP.

So the closest solution was to go to ASUS website and download their wireless driver:
ASUS WL-161 USB pen type adapter Linux driver (Kernel 2.4.5)[QUOTE]


The ubuntu kernel is 2.6.12, 2.5.6 is years old.  This driver will not work.

Perhaps you can use ndiswrapper?  It should work fine.

install ndiswrapper-utils

Find the windows driver for your card (there is an .inf file)

cd to that directory

cd /home/me/Deskto/driver
sudo ndiswrapper -i xxxxx.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper
PLug in your device and have fun.  If it does not work, try downloading the newest version of the windows driver.  To get ndiswrapper to load at boot time, add the word "ndiswrapper" to the end of the list in /etc/modules

sudo gedit /etc/modules

---

### Post by jingo811 on 2006-02-09
Ahoy, sorry t' be a pain in the *** Gar. :KS But I couldn't even install the program without errors.

I went to Sourceforge and downloaded the latest ndiswrapper-1.9.tar.gz for Hoary and I managed to unpack it as the ndiswrappers Wiki instructed.
But when it comes to installing the files I'm in no mans land.  So I followed the readme and Install text files from the ndiswrapper.tar.gz.
[http://web.telia.com/~u87415110/Symbios/ndis_install_readme.doc](http://web.telia.com/~u87415110/Symbios/ndis_install_readme.doc)
where I highlighted the parts that I had trouble with.  Mainly the **prerequisite part** I don't get that part at all, and the **make uninstall** parts printed out ERROR messages which I have documented at here:
[http://web.telia.com/~u87415110/Symbios/ndis_install_prob_01.doc](http://web.telia.com/~u87415110/Symbios/ndis_install_prob_01.doc)

Is it because I didn't do the **prerequisite** part that I get these ERRORS?
What should I do from here, I really don't follow the procedures in prerequisite?

---

### Post by az on 2006-02-09
A perfectly fine version of ndiswrapper is already included with ubuntu.  You don't need to compile a newer one!

See my last post.  If that does not work, get the latest driver (INF file) for your card.  If that still does not work, then try getting anewer version of ndiswrapper.  This is usually not what you have to do!

---

### Post by jingo811 on 2006-02-10
Sorry but I'm kind of having trouble reading between the lines from your instructions so I've been following the Ndiswrapper Wiki parallell to your responses:
[https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=HowToSetUpNdiswrapper](https://wiki.ubuntu.com/WifiDocs/Ndiswrapper?action=show&redirect=HowToSetUpNdiswrapper)
Section:
**2.1. Install necessary packages - 2.1.3. With no internet access**
I finally managed to install the ndiswrapper-utils from my Ubuntu CD.
But I'm having trouble in section:
**2.2. Set up and install drivers**
Understanding how I can find that **.inf **file?  Is it in Ubuntu OS, Ubuntu CD or Win XP CD, if so where can I find it because I'm also having trouble finding a search option in Ubuntu when it comes to looking for specific files?  And also the so called chipset **List link** in the Wiki I found this about my wireless:> 

Card: Asus WL-161, 11mbps

    * Chipset: Sis162u USB
    * usbid: 2821:0161
    * Driver: CDRom, WinXP driver. (sis162u.inf, original at [www.sys.com](www.sys.com))
    * Other: Use "ndiswrapper -d 2821:0161 sis162u"... to get Hardware present. It works perfect on 11 mbps! 
I surfed to that [www.sys.com](www.sys.com) but I didn't know where to look? :-k or maybe I did some more investigating could you confirm if this is the correct files to download and use?
[http://www.sis.com/download/download_step2.php?id=155863&agree=1&country=Sweden&Image7911.x=51&Image7911.y=11](http://www.sis.com/download/download_step2.php?id=155863&agree=1&country=Sweden&Image7911.x=51&Image7911.y=11)

---

