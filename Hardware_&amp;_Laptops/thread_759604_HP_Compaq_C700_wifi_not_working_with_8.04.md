---
title: "HP Compaq C700 wifi not working with 8.04"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by eliaspoveda on 2008-04-19
I trying Hardy Heron Release Candidate using a Live session, I haven´t install it. My laptop is an HP Compaq C700.

The problem is that the wifi is not working, the first thing Ubuntu has made automatically is install privative drivers for the wireless card. But it seems they dont work.

i've searched 2 hours in the internet for solutions, most of them are for Gusty Gibbon, anyway i try them but it doesn't work.

I really want to use Ubuntu on my laptop...

Any idea? Thanks!

---

### Post by eliaspoveda on 2008-04-19
AAARRgggG!!:mad: i hate windows and im starting to hate ubuntu!!! Why is so ****** difficult to connect to the internet?? this should be the first thing canonical should fix!!!

---

### Post by eliaspoveda on 2008-04-19
OK i have just read that Atheros is NOT compatible with Ubuntu. ****.:frown:

I was waiting for this release since i got my laptop 2 months ago and now i cant use...

---

### Post by stevejesus on 2008-05-02
I just bought a c700 for my wife a few days ago.  All works great except for the wireless.  I have an Acer laptop with an Atheros chipset, and it works with hardy no problem.  I am curious why its not working on the c700.

In the restricted drivers app in Hardy on her c700 it shows the Atheros driver as being "active", however, when I run iwconfig I get;

```
jillian@jillian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

```

Right now I am using an abssurdly oversized Hawking USB G adapter in her laptop.

---

### Post by cloudstrife87 on 2008-05-22
Try the following procedures that i have found from [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html").
It works with my Compaq c700 wireless:


For i386 Users:

First go to System–>Administration–>Hardware Drivers” and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then Reboot your system.

Preparing your system

sudo apt-get install build-essential

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci

sudo reboot

That’s it now your wireless should work without any problem.




For AMD64 Users:

If you are using 64 bit version following this procedure

Blacklist the default driver

echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

Download the 64 bit driver

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

Extract driver using the following command

tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz

Ensure you have your kernel headers and the build essential package.

sudo aptitude update

sudo aptitude install linux-headers-$(uname -r) build-essential

Install ndisgtk

sudo apt-get install ndisgtk

Either use ndisgtk to install the driver or

sudo ndiswrapper -i net5211.inf

Load up ndiswrapper every time Linux is loaded

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system using the following command

sudo reboot

Your card should have been detected and it should show available networks but if it does not, try

sudo iwlist scan

---

