---
title: "Webcam install for Xubuntu 15.04."
date: 2015-04-27
forum: Hardware
---

### Post by bob120 on 2015-04-27
Just learning Linux, completed printer install yesterday with very good clear instruction help.  

I'm testing 3 webcams, first is a Logitech. I don't recall witch ones worked in XP, 2 of 3 did, one by disc, other by download.
Followed a similar topic in Hardware, failed to bookmark, this fails my twilighting memory bank.
So the instruction had 2 Terminal entries, first was (I think) "lsusb", this recognized a Logitech device.
Next entry started with "sudo", worked, found drivers, then completed. I done a screen shot, but I don't know how to send that if requested.

Were do I find this program? Camera button does not activate an indicator light, its possible this one did not work. I believe I had restarted comp after install.

---

### Post by AllenGG on 2015-04-27
First off, did you install "Cheese" ?    It really helps.  Now in Ubuntu software Center.

---

### Post by bob120 on 2015-04-27
Yes, Cheese shows as installed.

---

### Post by AllenGG on 2015-04-27
OK. does it work on any cam ?  next, check the dependencies in Synaptic.   Notice that it depends on  gnome-video-effects,  which in turn depends on  " gstreamer1.0-plugins-good"

For some unknown reason the gstreamer plugins do not always get installed. 
Going through all of the dependencies helps, sometimes you may have to include the "Suggests" items.

---

### Post by bob120 on 2015-04-28
None of the 3 webcams are recognized by plugging in. 

Maybe the correct question is were to find instructions on how to do all things in Xubuntu 15.04, an index. Seem to spend hours following Google hits, always missing the correct info because it was targeting a different version of Linux or Ubuntu or...

I search in the box from the top lefthand corner , no results, how does one find Synaptic?  I've seen this before, same as gstreamer.

---

### Post by Elfy on 2015-04-28
You probably don't have synaptic installed. Certainly not by default.

It might help if you said what webcams you have.

I know for fact that Logitech C270 just works. 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

check this wiki page - see if the webcam is listed there [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by bob120 on 2015-04-28
Like I already stated Cheese is installed. "Cheese webcam booth", 3.14.1-2ubuntu4. Were do I find the settings?

None of the 3 webcams get a popup box after plugging in. 

I will check that ubuntu webcam link, I have read a few, thats why I'm posting, the help info is not obvious.

I did not install C270, I used the instruction (as a guide) to get a plugged in Logitech to download its drivers in the Terminal. I did not enter "logitech" or "c270" anywhere.  None of the cams have a model number, yet the Logicam downloaded its drivers, so I don't think it is needed.


Synaptic does not show as installed (the 2nd column) in the"Software centre", nor does it show in software (the first column), how do I get this and were does it end up after install? Is it background, no settings to consider?

---

### Post by Elfy on 2015-04-28
ok 

Open a terminal - Ctrl+Alt+T 

run this command

```
lsusb
```

copy and paste the whole output here, let's see what camera you have :)

---

### Post by bob120 on 2015-04-28
Ok, I just went to the webcam link, second one posted by Elfy administrator, Same instructions I followed to download. The next line states open Cheese, thats were I am stuck, how to open?

Elfy, I just seem your recent post, I have screenshots but don't know how to post them. I don't have copy and paste buttons since I ungraded to Xubuntu 15.04, I'll try to find them.

---

### Post by Elfy on 2015-04-28
I have no idea about cheese.

Please post the output so that we know what webcam(s) you are actually talking about.

Once we've got more idea of what they are we can help more.

---

### Post by bob120 on 2015-04-28
Just to top of visiting Elfy links, the Skype link says that the list may be different to those in Ubuntu, follow this later if needed.

I enter lsusb in the terminal, get a result listing Logitech and other items. I left click, lists paste, copy is not activate. I have saved it but cannot determine how to post it.

I search "how to post screenshot"  the search box at the top right of this page, zero hits. Probably the wrong question / words to search for. Elusive.

I rechecked the cord label of the Logitech, M/N V-UD4.

As usual the wrong approach, after highlighting then copy does work Keep trying until it works or the keys wear out!

tosomebody@somebody-C51-MCP51:~$ lsusb
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
somebody@somebody-C51-MCP51:~$

The 2nd webcam, no labels or brand.

somebody@somebody-C51-MCP51:~$ lsusb
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0c45:6029 Microdia Triplex i-mini PC Camera
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
somebody@somebody-C51-MCP51:~$

3rd webcam, a disc came with this purchase, has audio and camera light (LED).

somebody@somebody-C51-MCP51:~$ lsusb
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 009: ID 1e4e:0102 Cubeternet GL-UPC822 UVC WebCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
somebody@somebody-C51-MCP51:~$ 

Done posting, until instructed, thanks for everyone's patients.

I was looking for Synaptic, found "gksu synaptic", hopefully this installs it.  

somebody@somebody-C51-MCP51:~$ gksu synaptic
The program 'gksu' is currently not installed. You can install it by typing:
sudo apt-get install gksu
somebody@somebody-C51-MCP51:~$ sudo apt-get install gksu
[sudo] password for somebody: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgksu2-0 libgtop2-10 libgtop2-common
The following NEW packages will be installed:
  gksu libgksu2-0 libgtop2-10 libgtop2-common
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 173 kB of archives.
After this operation, 1,274 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) vivid/main libgtop2-common all 2.30.0.is.2.30.0-0ubuntu1 [9,540 B]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) vivid/main libgtop2-10 i386 2.30.0.is.2.30.0-0ubuntu1 [37.0 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) vivid/universe libgksu2-0 i386 2.0.13~pre1-6ubuntu7 [74.8 kB]
Get:4 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) vivid/universe gksu i386 2.0.2-9ubuntu1 [51.6 kB]
Fetched 173 kB in 3s (49.3 kB/s)
Selecting previously unselected package libgtop2-common.
(Reading database ... 186383 files and directories currently installed.)
Preparing to unpack .../libgtop2-common_2.30.0.is.2.30.0-0ubuntu1_all.deb ...
Unpacking libgtop2-common (2.30.0.is.2.30.0-0ubuntu1) ...
Selecting previously unselected package libgtop2-10.
Preparing to unpack .../libgtop2-10_2.30.0.is.2.30.0-0ubuntu1_i386.deb ...
Unpacking libgtop2-10 (2.30.0.is.2.30.0-0ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu7_i386.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu7) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-9ubuntu1_i386.deb ...
Unpacking gksu (2.0.2-9ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Setting up libgtop2-common (2.30.0.is.2.30.0-0ubuntu1) ...
Setting up libgtop2-10 (2.30.0.is.2.30.0-0ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu7) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Setting up gksu (2.0.2-9ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
somebody@somebody-C51-MCP51:~$

---

### Post by AllenGG on 2015-04-28
Try installing synaptic, like this....
$ sudo apt-get install synaptic
[sudo] password ...........
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic *is already the newest version.*
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

---

### Post by bob120 on 2015-04-28
I did that, got the synaptic active, needs administrator rights, says it will run.

Does anyone know where I can find webcam instructions for Xubuntu 15.04?

Perhaps the webcam solution is Microsoft.

I like Linux but finding "how to" is very expensive time wise.

---

### Post by Elfy on 2015-04-30
> **bob120 said:**
> Does anyone know where I can find webcam instructions for Xubuntu 15.04?

Perhaps the webcam solution is Microsoft.

I like Linux but finding "how to" is very expensive time wise.

Sorry - missed the new posts.

Looking at the camera's you've got - the *quickcam* should work.

I know for fact that Logitech C270 will plugin and work. 

Got one to replace another last week.

As far as Xubuntu instructions go - the majority of an *buntu instruction will do - Xubuntu is Ubuntu with Xfce instead of Unity basically. 

In generla it's only when you start looking at xfce parts that instructions differ.

---

### Post by bob120 on 2015-04-30
Elfy. Thanks for your help. I'm marking this as solved. Solution is replace this copy of Xubuntu 15.04 with a new copy without all the crap I installed from advice in this thread and others I found. None of it works, so something is messed up.

I followed multiple Ubuntu advice threads including a webcam page, none of the commands worked, I assume because it's for the wrong OS. 

I value contributors advice and especially their time, I will waste no more.

I thank everyone for considering my issue and attempts to help.

I have different appearances from this new install, better that the ungrading method to Xubuntu 15.10. I downloaded 15.10 yesterday, burned to disc and installed today.  It is likely a setting issue on my part, thankfully its gone bye. A little slow but that will change as the upgrades happen.

A fresh install of Xubuntu 15.10 from a homemade disc (above post). I installed cheese the same way as the first time, tried all 3 cameras, 2 worked. 

The problem may have been my settings (?), or upgrading from Xubuntu (14.latest) to 15.10 omitted items.

Problem is solved by fresh install.

---

