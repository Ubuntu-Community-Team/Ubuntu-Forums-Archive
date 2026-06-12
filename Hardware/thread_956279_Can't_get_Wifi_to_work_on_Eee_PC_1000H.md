---
title: "Can't get Wifi to work on Eee PC 1000H"
date: 2008-10-23
forum: Hardware
---

### Post by arwate on 2008-10-23
Hi all,

I got an Eee PC 1000H last week and have been trying to get to work various Ubuntu variations on it. A critical feature for me is Wifi, but so far I was not able to get it to work at all (or even find out what's missing on the way to get it work).

I don't really want to trust a "distribution" that tells users to do a fresh restall for a minor upgrade, so my enthusiasm for Ubuntu eee was over as soon as I found that comment there. Wifi didn't work there for me anyway.

But neither did it with eeeXubuntu (7.10), nor did it with a Xubuntu 8.04.1 in combination with the Kernel from Array.org.

After reading that Torvalds himself pressed for better Wifi support in this hardware which should be included in the 2.6.27 kernel, I decided to get the 8.10 Xubuntu beta.
But still, I have no success, and the posts on eeepc forums or various ubuntu forums don't help me, and neither do the few blog entries I found around this issue.

Last thing I did was to follow the descriptions of [http://stadt-bremerhaven.de/2008/10/17/asus-eee-1000h-ubuntu-und-das-wlan/](http://stadt-bremerhaven.de/2008/10/17/asus-eee-1000h-ubuntu-und-das-wlan/)
which gave me a module named rt2680sta (opposed to rt2680a in the article), which I can load, but then what?

It feels like I'm missing some general information about getting Wifi to work. Where can I see the hardware? I couldn't find anything wifi-ish in /proc. How should I recognize a driver module that matches my wifi hardware? Whenever I type 'iwconfig' it tells me that none of the devices has wifi support.
For that matter, how is that awkward wifi configuration dialog meant to work? Enter a SID and WAP password and that's it? Enter a Mac address - the one of the router or mine? How is a connection I configure with this dialog attached to a device? What device anyway?

Confused,
arwate

---

### Post by aurelieng on 2008-10-23
I also have a 1000H, and the wifi works perfectly with Adam's kernel @ array.org. Is the wireless controller activated in the BIOS ?

---

### Post by arwate on 2008-10-23
Ok, ..
Can you tell my just how do you notice that wifi works? Do you see a connection in your network manager?

Which Ubuntu do you use as base?

---

### Post by surfed on 2008-10-23
I have Ubuntu-eee 8.04.1 working perfectly on my 1000h.
I installed ubuntu-eee from usb stick, added both hardy and hardy-proposed repos from array.org, turned on proposed and backports in updates, installed the eeepc kernel (with wired net), upgraded all packages (make sure eeepc-config is installed, not sure if it is by default, there is also a ubuntu-eee meta package) and that was it for me i believe. Now everything works, exept 801.11n, i can only get g speeds, all the function keys work, toggle wireless, bluetooth etc
Fn + F2 toggels wireless. I also replaced networkmanager with wicd, it works much better and faster on the eee, wireless is up at the same time my desktop comes up, while with network-manager it took up to 30 seconds to get a connection.

---

### Post by arwate on 2008-10-24
Thanks for your answers. 

It seems that the kernel drivers from array.org don't include the wifi module for Intrepid. I got rt2860sta from [http://forum.eeeuser.com/viewtopic.php?id=43998](http://forum.eeeuser.com/viewtopic.php?id=43998). The other parts I needed where the kernel drivers from array.org and (important for me since I'm not using Ubuntu eee) eeepc-config.

---

### Post by lostinquestions on 2008-10-25
The Wireless should work by default on Intrepid. Check in your BIOS @ startup to see if it is Enabled at that level; for some reason, it occasionally disables itself.

Bobby

Edit: Sorry. Can't tell by the last post if you solve it or not, but anyway, I was wrong. Apparently, because "ath5k in 2.6.27 is very unstable" it no longer comes built in to the kernel. So, to install the driver, simply type this command in the terminal:

sudo apt-get install linux-backports-modules-intrepid

Note that this seems to be working for most people.. but not for me. :( Oh well.
And then reboot. Wah lah!

Bobby

---

### Post by edders on 2008-10-26
This too is driving me up the wall. I installed Ubuntu on my EEEPC 900 with absolutely no problems whatsoever. I have no installed both Ubuntu 8.04 and 8.10 on two 1000h EEEs and the same result. It basically said I had no network hardware. 

I managed to install the linux-ubuntu-modules-2.6.24-21-eeepc_2.6.24-21.30eeepc5_i386.deb and linux-image-2.6.24-21-eeepc_2.6.24-21.39eeepc1_i386.deb and now it seems my wired controller is recognized but still no wi-fi. I tried to install the rt2860 package mentioned here but get an error about it being a DKMS package. So I have no idea where to go from here. 

Also, what is the main reason Ubuntu is doing this on the 1000h? 

thanks. ed

---

### Post by arwate on 2008-10-27
edders, to get the rt2860sta module to work, you'll have to install the package dkms. I don't remember exactly how it is called but if you search for "dkms" in the package list, it should come up. 

As far as I see it, the Eee pcs come with a different wifi hardware since the 901. So, any tutorial or description that worked from 700 to 900 does not apply to the 901, 1000 and 1000H.

---

### Post by arwate on 2008-10-27
Oh, and I forgot.. you also need the eeepc-config package. After that it should work.

Greetz, arwate

---

### Post by antoni2 on 2008-11-23
Hi this is how I activated Wifi in Xubuntu 8.10 in an Asus Eee PC 1000H.

Download the Adams debian package (just the Wifi package worked for me):

[http://www.mediafire.com/?jfrgzemgnjz](http://www.mediafire.com/?jfrgzemgnjz)
The package is called "rt2860sta-dkms_1.8LK_all.deb"

Then just right click on the file, and choose "Open with GDebi Package Installer". It instals in a breeze and the Wifi is working perfectly right away. I see the applet "NetworkManager Applett" (installs in menu bar from the original Xubuntu 8.10 install - there must be something similar in Ubuntu) that indicates there is a Wireless connexion. You click on it and displays the list of all wifi networks available - you choose yours, and done !

Apparently it works also in the Eee PC 901.

thanks to Adams for the nice debian package, and to Roc Boronat, from the Ubuntu Catalan Team. He has a nice tutorial on this issue at

[http://piposerver.com/joomla157/](http://piposerver.com/joomla157/)

Note: Given the limited storage space in the Asus Eee PC line of computers, the Xubuntu distribution seems specially fit for them. I cannot but recommend it; to me, everything worked out of the box, just the wireless didn't.

---

### Post by Coombabah on 2008-11-25
> **arwate said:**
> Hi all,

I got an Eee PC 1000H last week and have been trying to get to work various Ubuntu variations on it. A critical feature for me is Wifi, but so far I was not able to get it to work at all (or even find out what's missing on the way to get it work)...


I also have a 1000h with wireless issues.

It's OK with the home wireless but haven't been able to get WPA enterprise with TKIP to work at the University.

Edit: Just tried a different laptop and found that WPA enterprise with TKIP works with Ubuntu 8.04.1 but not with 8.10

It looks like my 1000h wireless issues are really Intrepid wireless issues.

I found it easy to get wireless working on the 1000H at home with Intrepid but Intrepid wont work on WPA Enterprise with TKIP.

---

