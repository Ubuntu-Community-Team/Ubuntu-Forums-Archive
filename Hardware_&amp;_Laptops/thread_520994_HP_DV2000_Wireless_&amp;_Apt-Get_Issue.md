---
title: "HP DV2000 Wireless &amp; Apt-Get Issue"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by kmfdmk on 2007-08-08
I Just installed a fresh install of 7.04 Ubuntu.  The default wifi drivers wouldn't work on my Broadcom Dell Wireless 1390 WLAN Mini-PCI card.

*01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01*

I attempted to follow the directions here *before* noting that they were directions for the 1490 instead of the 1390.  [http://ubuntuforums.org/showthread.php?t=434946]("http://ubuntuforums.org/showthread.php?t=434946")

Regardless of the differences between the 1390 & the 1490 the 1490 steps didn't work for me.

Now I currently have an issue where every time I try to run apt-get, ie. apt-get install build-essential I receive the following error.


[I]build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--21:17:41--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:17:42 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/I]

After realizing I had installed the wrong drivers I tried to follow the steps here:  [http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Wireless+1390]("http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Wireless+1390")


However I wasn't able to get past step three **sudo apt-get remove ndiswrapper-utils** because I receive the same error as posted above.

I continued past the error to Step 4 and received the following:

[I]hack@mobile:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
hack@mobile:~$ sudo ndiswraper -l
sudo: ndiswraper: command not found
hack@mobile:~$ 
[/I]

So I pretty much get a message saying that the driver is installed but nothing about detecting  the hardware.  And yes the hard switch that turns the wifi on/off is turned on.


Secondly my sound **was** working when I did the fresh install.  After installing the updates to Ubuntu my sound no longer works.


*00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)*
Audio Adapter - HDA Intel - HDA nVidia
Supposed to be a MCP51 High Definition Audio

The audio device is a Conexant chipset, and I'm baffled as to why it would work initially and not now.

The Device Manager lists the following on it.

*info.linux.driver - HDA Intel*


Any help would be greatly appreciated.  I've had a bit of experience in the past with building, making and installing packages, however I'm still pretty new to linux.  I've successfully installed drivers for my Buffalo wifi card, and wardriving software in the past on my other laptop.

---

### Post by kmfdmk on 2007-08-10
*bump*

---

### Post by kmfdmk on 2007-08-13
bump

---

### Post by kmfdmk on 2007-08-25
*bump*

The wireless "fixed itself" after a reboot or two. Still having issues with the sound and Apt-Get failing on me.

---

### Post by kmfdmk on 2007-08-25
Looks like I was able to figure it out on my own.

I noticed in the one error message I was getting was:

Sub-Process /usr/bin/dpkg returned an errror

So I browsed to that folder and noticed it was where the programs/packages get installed to.

Then I though well if that program (which wasn't able to be found to be downloaded) is causing the problem I'll just "uninstall " the program SO:::


sudo apt-get remove bcm43xx-fwcutter 

fixed the problem for me.

Now I just need to get my fscking sound working again (updated Ubuntu broke it for me) and get the whole Aircrack-ng suite installed and running and I'll be happy.

---

### Post by Ayuthia on 2007-08-25
The bcm43xx-fwcutter problem is occurring because /usr/share/install_bcm43xx_firmware.sh has a bad link.  The easiest way to fix it is to go edit /usr/share/install_bcm43xx_firmware.sh and replace the URL with the following:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
This link is the updated version of bcm43xx-fwcutter.

Once you complete that, you should just be able to run:
sudo apt-get install bcm43xx-fwcutter
and it should download the file and clear up this issue.

As for your ndiswrapper -l issue, it looks like you missed a p in ndiswrapper so nothing was listed.  However, if you have not blacklisted bcm43xx, the bcm43xx-fwcutter should get your wireless up and running.  You might have to reboot to get the wireless running.

Oops!  Not fast enough!  Glad you got it fixed.

---

### Post by Acglaphotis on 2007-08-27
This will fix the audio:
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

---

