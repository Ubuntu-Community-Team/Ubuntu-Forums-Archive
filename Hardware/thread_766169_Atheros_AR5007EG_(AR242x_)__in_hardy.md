---
title: "Atheros AR5007EG (AR242x )  in hardy"
date: 2008-04-25
forum: Hardware
---

### Post by formol on 2008-04-25
hi, 

this post is for people who may have the same problem as i had.

i've a Toshiba a201 with Atheros AR5007EG (named AR5006EG in gusty) now name AR242x in hardy.

anyway, to make it work:

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz")

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work

i hope this help.

---

### Post by FredB on 2008-04-25
For 32 bits, you can use and install madwifi and a patch. See [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Your solution is only the good one for 64 bits hardy.

---

### Post by formol on 2008-04-25
hello,

i tryed madwifi with the patch before, maybe i did something wrong but it didn't work.  then, i tryed with ndiswrapper and it works, with the 32 bits version of hardy.

---

### Post by williamson389 on 2008-05-10
i tried the steps given by formol in the first step and the wireless connection still wont show up in System-administration-network. When i typed sudo ndisgtk the network showed u but it still doesnt work.  i dont know if i made a mistake at the first step with the restricted drivers.  i unchecked atheros support and 802.11 lan card.

---

### Post by formol on 2008-05-10
> **williamson389 said:**
> ...i typed sudo ndisgtk the network showed ...

ndisgtk is the graphical interface of ndiswrapper, where you have to set the .inf file. (using the graphical interface equal to type : ndiswrapper -i filename.inf) and the .sys files must be in the folder.

---

### Post by Alfred_McGee on 2008-05-12
The Madwifi fix worked for me, thanks to Tom-X. The problem, though is that my computer no longer suspends. Instead, once the lid has been closed, the screen fills with code, and the machine has to be restarted. Anybody know a fix for this?

EDIT: use the 3366 madwifi driver instead of the old 2756, and the suspend problem goes away

---

### Post by fissionmailed on 2008-05-12
I have to connect via command line.  I have a AR5070EG with 7.10 and have always had to connect via command line.  I tried the 32-bit patch on a 32-bit OS and it didn't work too. I wish madwifi work get a working 64-bit version out though.

---

### Post by formol on 2008-05-12
for this card in 32bit gusty, look at the last post on this page [http://ubuntuforums.org/showthread.php?t=527619&page=4]("http://ubuntuforums.org/showthread.php?t=527619&page=4")

---

### Post by fissionmailed on 2008-05-12
> **formol said:**
> for this card in 32bit gusty, look at the last post on this page [http://ubuntuforums.org/showthread.php?t=527619&page=4]("http://ubuntuforums.org/showthread.php?t=527619&page=4")

That's what I had to do, although I went about another way around it.

---

### Post by allspamme on 2008-05-18
forgive me I am a newbie but I am not even able to install ndiswrapper.
in my add/remove i get this 
---
Windows Wireless Drivers
Windows Wireless Drivers cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.
----
Please help

---

### Post by nicedude on 2008-05-18
I have writen a complete step by step guide for installing the aircrack patched madwifi drivers for proper operation of the AR5007 chipset in 32bit Hardy 8.04 . Also in the posts at the thread below I have posted 2 scripts to both launch a kismet server and to return to managed mode for regular internet use that I wrote for myself and decided to share. You might check it out if your using a Atheros card with patched madwifi drivers or want to be.

Link to my guide
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

My kismet scripts are at post #13

If you do use my guide or scripts please post a comment on that thread to report your experience.

While there are other guides around mine is the most complete I know of. And I have had a bunch of people tell me it was the only thing that worked for them.

Anyone that needs furthur help feel free to PM me and I will try to help you out :-)

---

### Post by lusis89 on 2008-06-05
Using the latest version of MadWifi from [http://madwifi.org](http://madwifi.org) worked for me.

1) Disable restricted drivers (HAL & Atheros from System->Restricted manager)

2) ```
wget http://sourceforge.net/project/downloading.php?groupname=madwifi&filename=madwifi-0.9.4.tar.gz&use_mirror=surfnet
```

3) extract the downloaded tarball and run
```
make
```
and
```
sudo make install
```

4) then unload old modules
```
sudo madwifi-unload
```

5) Insert the new module
```
sudo modprobe -i ath_pci
```

And should work.

---

### Post by Meggeler on 2008-06-06
Thnk you for the explicit instruction.  My eeepc wifi quit after the latest update and I was lost :-).  Having a broken right arm make a lot of hit and miss debug difficult and painful.

---

### Post by jazee on 2008-06-22
I have tried both solutions (1st ndiswrapper, 2nd new madwifi drivers build) neather seem to have solved my problem.

I have a new HP dv6812 with Hardy 64bit edition installed. Any other idea that I may look into trying to get this to work.

---

### Post by retrow on 2008-06-26
I had not disabled the Hardware Drivers earlier. They need to be disabled in order for the new drivers to kick in.

Thanks a lot for the OP.

---

### Post by rsandu on 2008-07-21
Hello,

I am trying to set the wireless on a Fujitsu-Siemens Esprimo Mobile V5535 (64 bit machine), using Ubuntu 8.04 x86_64.

I've read and followed the howto's given above (including disabling proprietary driver), but I was unable to get it working.


The full hardware data about this machine is here:

[https://bugzilla.redhat.com/show_bug.cgi?id=456041](https://bugzilla.redhat.com/show_bug.cgi?id=456041)

I've used the ndiswrapper method + Windows drivers, but no luck. The Windows is reported as loaded, but „unattached”. The Windows drivers are those that already work on Windows...

I really don't want to install 32bit Hardy just for the sake of wireless...


Could you please help ?


Regards,
R&#259;zvan

---

### Post by rsandu on 2008-07-21
Hello again,

Regarding what I've said above about the Fujitsu-Siemens Esprimo Mobile V5535, my only idea is that:

If one looks on Fujitsu's site, looking for Windows drivers, he/she will note that Windows 64bit Edition is not supported.

[http://support.fujitsu-siemens.com/com/support/downloads.html](http://support.fujitsu-siemens.com/com/support/downloads.html)

So probably the Windows drivers available on this site are *32 bit* drivers. Many people said here I have to use 64bit drivers...

Can you please point me to some x86_64 Windows drivers, if any - to use with ndiswrapper ?

Regards,
R&#259;zvan

---

### Post by stranger22 on 2008-08-06
I couldn't thank you enough mate. Sometimes when I boot, it doesn't connect automatically. Then I got to left click on it and choose *Connect to Other Wireless Network*. That I can do.
Thanks a lot, again.

---

### Post by apche93 on 2008-08-06
Here is another method of installing ur driver:

First download the driver from here:


[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz")

Then complete these steps:
1. Remove any ath_pci driver from the RESTRICTED DRIVERS MANAGER
2. Make sure that you have ```
build-essential
``` package installed, if not, fire up a terminal and type in ```
sudo apt-get install build-essential
```
3. Navigate your way in Terminal to the directory where you downloaded the archive for the driver
4. Type these to decompress the archive ```
tar xfz madwifi-ng-r2756+ar5007.tar.gz
``` and ```
cd madwifi-ng-r2756+ar5007
```
5. Type ```
make
``` to compile
6. Type ```
sudo make install
``` to install the driver
7. Type ```
sudo modprobe ath_pci
``` to insert the driver as a kernel module
8. Restart by typing ```
sudo reboot
```
9. If all goes well, after you restarted, you will find wireless networks in your Network Manager


OR,

u can just visit this topic where i kinda stole the information from:
[http://ubuntuforums.org/showthread.php?t=662877]("http://ubuntuforums.org/showthread.php?t=662877")


Hope that helps!

---

### Post by ftabor on 2008-08-07
> **formol said:**
> hi, 

this post is for people who may have the same problem as i had.

i've a Toshiba a201 with Atheros AR5007EG (named AR5006EG in gusty) now name AR242x in hardy.

anyway, to make it work:

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz")

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work

i hope this help.
Thanks, this worked perfectly for a HP Pavillion dv6000.

---

### Post by blitzer on 2008-08-27
> **formol said:**
> hi, 

this post is for people who may have the same problem as i had.

i've a Toshiba a201 with Atheros AR5007EG (named AR5006EG in gusty) now name AR242x in hardy.

anyway, to make it work:

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz")

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work

i hope this help.

Thank you for the post this helped me set up my wireless.

My system is an Acer Aspire 5520 64 bit Hardy.

---

### Post by d38as3r on 2008-12-27
This worked flawlessly for me...
Did exactly as he suggested (im on 32bit also)
Rebooted and had my wireless back.
Thanks Much!

---

### Post by clevefan on 2009-01-31
I did everything you said. my wireless card light is not on. is it suppose to be lit up after dpoing all this?

---

### Post by persev on 2009-02-02
> **FredB said:**
> For 32 bits, you can use and install madwifi and a patch. See [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Your solution is only the good one for 64 bits hardy.

Not Found

The requested URL /ticket/1679 was not found on this server.

---

### Post by elwin_windleaf on 2009-02-07
Just wanted to mention that this worked flawlessly on Linux Mint 6 (Felicia), so I imagine it should work alright under most versions of Ubuntu 8.10 Intrepid.

The machine I installed it on was a Emachines E520 laptop.

---

### Post by Crafty Kisses on 2009-02-18
This has worked on a couple of laptops, but you can install the backports package, and it will resolve the issue as well from my understanding.

---

### Post by [.root/fail] on 2009-02-24
Hello, I have a Compqaq CQ60-211DX. It is a 64-bit machine. But it came with Windows Vista Basic (32-bit). I am running Ubuntu 8.10 (64-bit). I cannot get my wireless to work. I am working through ethernet just fine though. 

I am really hoping for help, and I need to take care of this as soon as possible.

I am a complete Linux newbie, bear that in mind too.

Anyways, here is the manufacterer's site: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&lang=en&product=3866423](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&lang=en&product=3866423)

Here is the information I got from lsusb:

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Here is the information I got from lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


I followed the instructions in the first post in the following link, but still no luck.

[http://ubuntuforums.org/showthread.php?t=76616](http://ubuntuforums.org/showthread.php?t=76616)

---

### Post by fuzzyworbles on 2009-03-07
i don't know why you want to mess with ndiswrapper. i know that madwifi 0.9.4 works with atheros 5007 variants, but really the best and easiest way to get this card working is to install the ath5k module. do this by getting the the correct source here [http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download") and compiling. you'll need your kernel headers and build-essential. check the included README to see what you need to compile.

in my experience the ath5k module provides a stronger signal than madwifi. for example, madwifi caps the card under the fcc regulation whereas ath5k meets the limit.

---

### Post by the diz on 2009-03-09
I'm really glad I found this thread, I've found quite a few other solutions but this one was the easiest to set up and actually worked for me. I was ready to give up if I didn't get my Wi-Fi up and running today.

> **formol said:**
> hi, 

this post is for people who may have the same problem as i had.

i've a Toshiba a201 with Atheros AR5007EG (named AR5006EG in gusty) now name AR242x in hardy.

anyway, to make it work:

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz")

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work

i hope this help.

For future reference and just a tip for fellow noobs with the same notebook or wireless gear I have ( Compaq Presario CQ60-211DX ), formol's advice here worked perfectly fine for me (Thanks a lot formol!). The physical button on my laptop doesn't indicate the wireless is working, but it is in fact connected without any problems so far (few hours). I'll report back should I come across any hiccups.

---

### Post by Azaria on 2009-04-08
Thank you so much! I've been trying to figure out this for days. I'm new to Linux and your quick guide was so easy to follow and understand. Took me only a few minutes to get it up and running.

:KS <---Gold Star

---

### Post by radagast1155 on 2009-04-12
> **formol said:**
> hi, 

this post is for people who may have the same problem as i had.

i've a Toshiba a201 with Atheros AR5007EG (named AR5006EG in gusty) now name AR242x in hardy.

anyway, to make it work:

- disable both restricted drivers in System > Adminstration > Hardware drivers

- install ndiswrapper in the add/remove window

- download the .inf from the XP driver at : [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz")

- open a terminal and type this command : sudo ndisgtk

- select the net5211.inf file and "enter"

- it should now work

i hope this help.

after two days of fighting with the computer it finally works! Thank you

---

### Post by subtorn on 2009-04-15
Some progress to report with my Toshiba LT and upgrading to JJ (9.04)...

After upgrading from Hardy to JJ, my AR5007EG is working and allowing me to post this message...unbelievable...and totally awesome!!!

Gotta give it 3: :guitar::guitar::guitar: for it working without ndiswrapper.



Edit/Update:  Installed aircrack-ng and madwifitools through the SPM and got the AR5007EG into Monitor Mode.

---

### Post by screwballl on 2009-05-06
> **subtorn said:**
> Some progress to report with my Toshiba LT and upgrading to JJ (9.04)...

After upgrading from Hardy to JJ, my AR5007EG is working and allowing me to post this message...unbelievable...and totally awesome!!!

Gotta give it 3: :guitar::guitar::guitar: for it working without ndiswrapper.



Edit/Update:  Installed aircrack-ng and madwifitools through the SPM and got the AR5007EG into Monitor Mode.

That is what I suggest for people using previous versions of Ubuntu... worked for me as well... I did have it working for a few hours in 8.10 but then it stopped working for some odd reason...

---

### Post by Chris Hallquist on 2009-05-25
This fix worked for me when I did it last fall, but I had computer troubles and had to reinstall my OS. Now when I try to do it, the website linked in the OP seems to be gone. Does anyone have the file / know where I can get it? If you have the file and are willing to send it to me, say so and I will PM you my e-mail address.

---

### Post by djobbito on 2009-05-29
There is a very good solution. Working perfectly for me and trust me, I got full speed with the ath5k modules and no more suspend on the network.

Go to [http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/) for instructions.

But I would advice to install the 2.6.30r*{last one} (I have the 2.6.30r4) from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) which work very good on my laptop with that chipset.


Let me know.

Ps: Info about kernel 2.6.30 [http://www.h-online.com/open/Kernel-Log-What-s-coming-in-2-6-30-Network-New-Wi-Fi-drivers-and-other-network-novelties--/news/113090](http://www.h-online.com/open/Kernel-Log-What-s-coming-in-2-6-30-Network-New-Wi-Fi-drivers-and-other-network-novelties--/news/113090)

---

### Post by SaintHairBall on 2009-07-13
This referenced link is 404d.  Any replacement?

 [http://blakecmartin.googlepages.com/...-32-0.2.tar.gz](http://blakecmartin.googlepages.com/...-32-0.2.tar.gz)

---

### Post by J_dillinger on 2009-08-22
Upgrading ubuntu 8.10 with madwifi-hal-0.10.5.6-r3942-20090205 to ubuntu 9.04

I was using the madwifi-hal driver with my 8.04 - 8.10 ubuntu install, but when I upgraded to 9.04 the driver failed to function.  More importantly the Ath5k fails to allow running in promiscuous mode and packet injection.  The wifi works, but I am unable to use kismet and aircrack-ng with the new driver.  In answer to the previous question I edited kismet.conf with the following devices activated:

source=madwifi_ag,wifi0,Atheros

The real problem maybe that I just need the source for the ath5k driver.

---

### Post by J_dillinger on 2009-08-22
so I tried the following...

sudo modprobe ath5k

then...

modeprobe -l 

to check  if it worked.  I then edited /etc/kismet/kismet.conf with the following source...

source=ath5k,wlan0,atheros

and kismet worked perfectly, I will have to work on aircrack-ng next because my wife does not see the importance of the achievment and wants me to weed the yard.

---

