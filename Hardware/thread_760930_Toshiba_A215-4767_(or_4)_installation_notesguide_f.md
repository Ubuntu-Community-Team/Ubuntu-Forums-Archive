---
title: "Toshiba A215-4767 (or 4****) installation notes/guide for Ubuntu 8.04 Hardy Heron"
date: 2008-04-20
forum: Hardware
---

### Post by AndrewTheArt on 2008-04-20
[size=5]Toshiba A215-4767 (and 4***) Specific Installation Notes for Ubuntu 8.04 Hardy Heron[/size]

Installing Ubuntu 8.04 on the Toshiba A215-4767 is a fairly simple process. There are only two components that take any real configuration - the wireless and sound setup. Everything else is either automatic or self explanatory.

Short description of what is done in this guide - 

* For the wireless, you need to blacklist the ath_pci module and install the XP drivers with ndiswrapper, and modprobe ndiswrapper. 
* For the sound, you need to get the latest version of Alsa (I achieve this through enabling backport packages in Hardy) and edit a config file.

Be sure to attach an Etherent wired connection to your laptop before the install or directly after it. You need to do this because you need to install ndiswrapper/ndiswrapper-utils to get wireless access, and the simplest way to get it is from the online repositories. (You can install ndiswrapper/ndiswrapper-utils from the installer CD, but I have been unable to determine how to set that up properly, even after messing around in the Software Sources area).

**[size=4](1) Wireless setup[/size]** (per [this](http://drewwithers.com/2007/12/ubuntu-linux-710-gutsy-on-toshiba.html) site)

Instructions for Atheros wireless card:

Download drivers:

[XP 32-bit](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)
[XP 64-bit](http://www.atheros.cz/download.php?atheros=AR5006EG&system=2)

*(small note - once you click Download, you might have to wait a bit for the download to initiate*

Extract the drivers and take note of where you extracted them.
Open a terminal a type in the following -

```
sudo -i
echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
rmmod ath_pci
apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
cd <location where you extracted the drivers>
ndiswrapper -i net5211.inf
```

For confirmation's sake, type in - 

```
ndiswrapper -l
```

and ensure that something like this is returned:

```
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)
```

Finally, execute the following commands - 

```
modprobe ndiswrapper
echo "ndiswrapper" >> /etc/modules
```

After a reboot wireless should work. You should see available wireless networks in the network manager (left click on the network icon in the system tray). Note: every few bootups, Ubuntu doesn't get the MAC Address for the wireless card correctly. *(Andrew's note - haven't noticed this problem yet)* So far it looks like the easiest way to correct this is to go into /etc/ndiswrapper/net5211 and look for the file with a symbolic link. Edit it and replace the line that says

```
mac_address|XX:XX:XX:XX:XX:XX
```

and replace the X's with your MAC address.

**[size=4](2) Sound setup[/size]** (per [this](http://ubuntuforums.org/showpost.php?p=4220157&postcount=5) site)

After the inital boot and some updates, but you notice that the sound stops working after a reboot.

To fix this issue, you need to upgrade to the cutting edge version of Alsa. The easiest way to do this is to just use the backports modules.

1) Enable backports in software sources (System Menu> Administration> Software Sources--> Updates--> check "Enable Backports")

2) Then open a terminal and type in

```
uname -r
```

(this will tell you what kernel you're running (eg 386 or generic)

3) In a terminal, type -

```
sudo aptitude install linux-backports-modules-hardy-generic
```

OR

```
sudo aptitude install linux-backports-modules-hardy-386
```

depending on what kernel you have.

**NOTE!!!:** You can instead simply install *linux-backports-modules-hardy*, which is a meta package that depends on the latest generic backports package. (in theory at least, I haven't personally tried this)

4) In a terminal

```
sudo gedit /etc/modprobe.d/alsa-base
```

This will open a file in gedit (the text editor). Scroll down the page and add this as the last line

```
options snd-hda-intel model=toshiba
```

5) Reboot. This will upgrade your alsa to the 1.0.15RC3 and your sound will be fixed.

---

