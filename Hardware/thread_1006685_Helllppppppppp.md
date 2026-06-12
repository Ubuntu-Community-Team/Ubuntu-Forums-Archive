---
title: "Helllppppppppp"
date: 2008-12-09
forum: Hardware
---

### Post by AB109 on 2008-12-09
I can't get my wireless internet, web cam and the sound card to work..........
I have a toshiba satellite M305D- S4830............



Helpppppp

---

### Post by AB109 on 2008-12-09
I can't get my wireless internet, web cam and the sound card to work..........
I have a toshiba satellite M305D- S4830............


Hepllllllllllllllllllllllllllllllllll

---

### Post by albinootje on 2008-12-09
Please show us the output of :
lspci
lsusb

---

### Post by binbash on 2008-12-09
for wireless : 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by AB109 on 2008-12-09
> **albinootje said:**
> Please show us the output of :
lspci
lsusb here is the output the second file is the gzip because of the out load image

---

### Post by RussellHill on 2009-01-03
Hi to everybody! I have the same toshiba satellite M305D- S4830 and same problems:( but now I know solution about wi-fi. First My OS is UBUNTU 8.10 32 bit. 
So:

Check you have the atheros card that Acers use.
Code:

lspci -v

It should return

Code:

Ethernet controller : Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter

somewhere near the end.

If it does copy and paste the following commands into your terminal with a wired connection.

Download the latest madwifi snapshot.

Code:

wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

Unzip it
Code:

tar -xvf madwifi-hal-0.10.5.6-current.tar.gz


navigate to the extracted file

Code:

cd madwifi-hal-0.10.5.6-r3861-20080903

If you`ve not got the tools necessary for compiling get them

Code:

sudo apt-get install build-essential linux-headers-$(uname -r)

Then compile it
Code:

sudo make

Code:

sudo make install

load the module

Code:

sudo modprobe ath_pci

make it load every time you boot

Code:

gksudo gedit /etc/modules

then copy and paste this to the bottom of that file
Code:

ath_pci

save
exit
reboot

---

### Post by Ruyuk on 2009-01-03
When your writing a thread make sure your more specific in what you need Helllppppppppp in. :P

---

### Post by RussellHill on 2009-01-05
Ok I'll try. But please don't kill me if I'll make mistakes because english is not my native language. sorry :D

1. My sound card is Conexant High Definition SmartAudio 221(Conexant Cx20561) in terminal after lspci I can see:
Audio device: ATI Technologies Inc SBx00 Azalia
So my built in microphone doesn't work.

2. As far as I know when laptop's charger is disconnected in tray suppose to be special battery icon with information about discharge, but I dont have it. Looks like I don't have battery :confused:

3. When I try to shutdown it don't want to do that instead laptop restart! :confused:

All this problems makes me crazy!

---

