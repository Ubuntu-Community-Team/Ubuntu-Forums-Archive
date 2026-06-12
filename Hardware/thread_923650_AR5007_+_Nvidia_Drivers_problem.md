---
title: "AR5007 + Nvidia Drivers problem"
date: 2008-09-18
forum: Hardware
---

### Post by Matticus on 2008-09-18
I am using 8.04 64bit ubuntu, and I got the madwifi drivers working fine, but whenever I install the nvidia drivers, either from nvidia's site or from ubuntu's restricted drivers the wireless stops working.

I can see all of the wireless networks it just will not connect.

I used the following to install the wireless drivers:

Disabled: HAL and support for Atheros Card


sudo aptitude update

sudo aptitude install linux-headers-$(matt -r) build-essential

sudo apt-get install ndisgtk

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz

echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

Loaded inf into ndiswrapper

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Then rebooted.


Then to get it working everytime I start I used


#! bin/bash
modprobe -r ndiswrapper
cp /etc/modprobe.d/blacklist .
sed ’s/#blacklist ath_pci/blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist
ndiswrapper -ma && sudo ndiswrapper -mi
modprobe ndiswrapper
sed ’s/blacklist ath_pci/#blacklist ath_pci/g’ /etc/modprobe.d/blacklist>blacklist3
mv blacklist3 /etc/modprobe.d/blacklist


saved as subirwifi

sudo cp subirwifi /etc/init.d

chmod +x subirwifi

sudo ln -s /etc/init.d/subirwifi S09subirwifi


The rebooted and it was perfect.

But now with nvidia drivers running its broken again.

I have read a bunch of threads and none seem to help my situation, mainly because I don't know what sort of solution I am looking for, so searching isn't easy.

Thanks in advance for any help.

---

### Post by Matticus on 2008-09-18
Scratch that, it seems to be randomly working again now. I wonder how long this will last

---

