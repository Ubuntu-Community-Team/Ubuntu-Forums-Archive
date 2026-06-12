---
title: "Belkin N Wireless Adapter Installation guide for 9.10"
date: 2009-11-29
forum: Hardware
---

### Post by Justin2240 on 2009-11-29
Hi all,

This is my first guide that involves a Linux Operation system but I have noticed that after searching on Ubuntu Forums and Google for 7 hours that a lot of people have had the same problem that I had with the Belkin N Wireless Adapter model number F5D8053 V.6 on Ubuntu 9.10. So I thought I would try to help everyone out with this guide so please send some positive feed back if I did a good job, Thanks.

First, to start off. We need to insert the Linux Ubuntu 9.10 disk into the drive bay. Once the icon for your disk pops up onto the desktop double click on it and navigate to

**>ubuntu/pool/main/n/ndiswrapper**

Once in this file click on and install

**>ndiswrapper-common_1.54-2ubuntu1_all.deb**

After that installs go back to your disk and click on and install the file that says

**>nidswrapper-utils-1.9_1.54-2ubuntu1_i386.deb**

After you get done with installing both files eject the disk from the drive bay and then insert your drivers disk for you Belkin Wireless Adapter. Once the icon is mounted on the desktop double click on it and navigate to

**>InstallationFiles/Driver/**

Depending on weather or not you have the 64x or 32x version of Ubuntu will determine the file you choose to open on that disk. Once you open the appropriate file copy the files inside and then navigate to 

[B]>system/homefolder/
[/B]
and then create a new folder and name it < insdir > and paste the files that you copied to that folder. Once done open < Terminal > and then type in

**cd /home/username/insdir/**

_*Note: Don't for get that "username" is what your login name is whenever you boot up your system.*_

After you enter the directory of the new folder you created, type in 

**sudo ndiswrapper -i net8192su.inf**

After you have done this < Terminal > should give you a message verifying that it is installing the necessary hardware driver for your Wireless adapter. Ok now, that was the hard part. Now to get into talking about how to pick up your wireless router with your card and how to turn on your card through < Terminal >.   

Whew.... I know that seems like a hassle but its worth it honestly. Now that you have installed the driver stay in < Terminal > and type in the following command.

**sudo modprobe ndiswrapper**

If you did everything correctly you should see a blue light flashing on your wireless adapter. Congrats!! You have just installed the hardware driver for your Belkin N Wireless Adapter. 

Now for finding your router with your card you can use your system network manager or you can use my personal favorite **Knetworkmanager. **

If you choose to use Knetworkmanager then this is how your are going to have to install it. Open up < Terminal > Once again and type in the following command.

**sudo apt-get install plasma-widget-networkmanagement** 

After you do this it will automatically install the program through < Terminal >. Once it's done go into < Applications > and then < System Tool > and there it is. Once you open it configure your settings according to your router and if all should go well you will now be connected to your router and have internet  access.

---

### Post by Justin2240 on 2009-12-01
I forgot to mention.... Sorry to inform all of you who are reading this guide. This card will only work for some routers apparently. I don't know the whole extent of which routers it works with on Linux but I know for sure sense I'm sitting up at Starbucks right now and they are using a AT&T router that it definitely works with AT&T routers..... Sorry for the bad news.

---

### Post by bthirnrayan on 2009-12-09
Hi,
 
Does the process remains the same for the Belkin "G" wireless adaptor ?
 
-bthirnrayan

---

