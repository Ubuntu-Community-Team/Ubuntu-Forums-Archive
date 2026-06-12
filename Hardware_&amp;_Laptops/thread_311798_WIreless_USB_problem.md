---
title: "WIreless USB problem"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by skii on 2006-12-03
I recently tried to install a Wireless USB stick with a guide I found on ubuntu.com, but when I follow it and go on system | administration | networking it says i should see a wlan0 network connection, but I dont. What can I do, the hardware is confirmed to work with ndiswrapper and im using the right driver. What can I do?

---

### Post by teaker1s on 2006-12-03
install
network-manager-gnome

this should help you configure and switch between wired and wireless easily

---

### Post by skii on 2006-12-04
it doesn't appear on my synaptic package manager and i dont have internet access on that pc. what I cant understand is that I did everytihng right i think.
1) uninstalled old ndiswrapper
2)installed new ndiswrapper
3)installed the tl-wn620g driver
4)assigned the driver to use the hardware using its usb ID 0cf3:0002
5)In the Ndiswrapper GUI interface it's telling me tl-wn620g driver present, hardware present, but when I click on configure network, there is nothing like wlan0, just eth0 and Modem. Can anyone tell me what to do i've been struggling for 2 weeks.

---

### Post by teaker1s on 2006-12-05
does wireless light come on? network-manager-gnome can be installed using alternate install cd and cdrom add. alternatively look at [this]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28broadcom%29#head-1e63934359df5734b0d85f653110de7e4ba224df")

---

### Post by sorairo on 2007-05-09
I'm having the same problem, but I DO have internet access.

I have installed ndiswrapper, and installed the latest drivers (in fact I've done reinstalls of the entire OS and tried older drivers too), and I still don't get a wlan0 or ath0 interface.

When I try ndiswrapper -l it gives:

athfmwdl: driver installed
device (0CF3:0002) present

net5523: driver installed
device (0CF3:0002) present

So the system knows the USB wireless adapter is there, and it knows how to use it, but it doesn't give me an interface to use.
The link light on the device starts flashing when I fire it up with modprobe ndiswrapper, but no amount of ejecting/reinserting/rebooting seems to help.

I'm using ndiswrapper 1.43, and have a fresh install of Ubuntu Fiesty.

I know people have this TL-WN620G device working, but I'm afraid I might be too much of a n00b.
If anyone can give me a hand, I'd be really grateful!

---

### Post by Dino Rastoder on 2007-06-07
[http://ubuntuforums.org/showpost.php?p=2799192&postcount=5](http://ubuntuforums.org/showpost.php?p=2799192&postcount=5)

---

