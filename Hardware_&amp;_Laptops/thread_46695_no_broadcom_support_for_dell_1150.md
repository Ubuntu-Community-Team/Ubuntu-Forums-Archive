---
title: "no broadcom support for dell 1150?"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by pedwards on 2005-07-05
I recently installed 5.04 on my dell 1150 and now i cant connect to the internet at all.  I am brand new to linux and im probibally making some stupid noob mistake but a little help would be nice.  I have 5.04 set up as a duel boot next to winxp(iece) and all my devices work in windows.  
-thanks

---

### Post by apollo2011 on 2005-07-05
No, it sounds like you are doing ok with Linux.  Broadcom (which makes almost all the Dell Ethernet and WiFi cards doesn't make Linux drivers.  In order to use your WiFi cards and Ethernet cards, you will have to load the Windows driver through [Ndiswrapper](http://ndiswrapper.sourceforge.net).

---

### Post by Steve1961 on 2005-09-05
Broadcom cards can be tricky, but you need to first go to the sourceforge ndiswrapper website to see if your card's listed and how to get the .inf and .sys windows drivers. Download these and put both of them in a directory in your home directory - I created a directory called windriv.  You then need to install ndiswrapper.  You can install ndiswrapper from your installation cd, but I've never managed to get this to work. Better to download the source file for version 1.2 from [http://sourceforge.net/project/show...group_id=93482](http://sourceforge.net/project/show...group_id=93482). You will obviously need to go online for this, but just download the file from a pc that is online. Once you have this use the synaptic package manager to install essential packages from the CD by typing the following into a shell:

sudo apt-get install debhelper build-essential fakeroot linux-headers-$(uname -r)

Then untar the file and install it:

cd /home/username/
sudo tar xvzf ndiswrapper-1.2.tar.gz
cd /home/username/ndiswrapper-1.2.tar.gz
sudo make
sudo make install

You then need to cd to the directory (windriv in my case) where you've store the windows drivers for your card and type:

sudo ndiswrapper -i <insert name of .inf file - from memory its called something like bcmwl5a.inf>

Then type the following to make sure the driver's installed:

ndiswrapper -l

Hopefully this will show the driver installed. From here you need to type:

sudo modprobe nidswrapper
sudo iwlist wlan0 scan 

If you can see your network type: ndiswrapper -m followed by sudo gedit /etc/modules. Add ndiswrapper to the end of this file.

From here you should be able to set your essid and encryption from the system/administration/network interface in the gui. Just click on your wlan card and then select properties. When you've finished press activate. You should now be online.

If you have problems with ndiswrapper try different versions. Hope this helps.

---

### Post by acejones on 2005-09-22
[QUOTE=Steve1961]Broadcom cards can be tricky, but you need to first go to the sourceforge ndiswrapper website to see if your card's listed and how to get the .inf and .sys windows drivers. Download these and put both of them in a directory in your home directory - I created a directory called windriv.  You then need to install ndiswrapper.  You can install ndiswrapper from your installation cd, but I've never managed to get this to work. Better to download the source file for version 1.2 from [http://sourceforge.net/project/show...group_id=93482](http://sourceforge.net/project/show...group_id=93482). You will obviously need to go online for this, but just download the file from a pc that is online. Once you have this use the synaptic package manager to install essential packages from the CD by typing the following into a shell:

sudo apt-get install debhelper build-essential fakeroot linux-headers-$(uname -r)

Then untar the file and install it:

cd /home/username/
sudo tar xvzf ndiswrapper-1.2.tar.gz
cd /home/username/ndiswrapper-1.2.tar.gz
sudo make
sudo make install

You then need to cd to the directory (windriv in my case) where you've store the windows drivers for your card and type:

sudo ndiswrapper -i <insert name of .inf file - from memory its called something like bcmwl5a.inf>

Then type the following to make sure the driver's installed:

ndiswrapper -l

Hopefully this will show the driver installed. From here you need to type:

sudo modprobe nidswrapper
sudo iwlist wlan0 scan 

If you can see your network type: ndiswrapper -m followed by sudo gedit /etc/modules. Add ndiswrapper to the end of this file.

From here you should be able to set your essid and encryption from the system/administration/network interface in the gui. Just click on your wlan card and then select properties. When you've finished press activate. You should now be online.

If you have problems with ndiswrapper try different versions. Hope this helps.[/QUOTE]
thanks!!!  after working on my Netgear MA521 card for three days, i stumbled upon this thread trying to install a Linksys WPC11 card.  But your instructions were easy to follow and i ended up getting the netgear card to install after all!  thanks again!!!

---

### Post by Steve1961 on 2005-09-23
Glad to have been of help.  I struggled with ndiswrapper myself to start off with, but this method always seems to work for me.

---

