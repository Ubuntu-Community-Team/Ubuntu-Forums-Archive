---
title: "Asus 1215n network problems"
date: 2010-08-14
forum: Hardware
---

### Post by ger3d on 2010-08-14
Hello

I just got a new Asus 1215N netbook. when I boot with a USB flash drive with ubuntu 10.04 I do not get any network connection. no wifi or wired. The USB flash drive boots fine on other PC's. Should I do an install or is there a problem with that computer. Windows workes so the hardware i fine. 

Could anyone help I realy would like to get rid of windows

Thank's Gerhard

---

### Post by Rusna on 2010-08-19
Hi,

I'm interested as well. I'm struggling whether to buy 1201N or this one. As far as I know Eee 1201N is pretty well compatible with Ubuntu, but lets see if these issues with 1215N can be solved?

---

### Post by dabidovich on 2010-08-19
Asus 1215N may also have an issue with ubuntu and nvidia optimus (this technology is not supported by nvidia in linux)

Did you manage to switch graphics cards using BIOS settings=

---

### Post by ger3d on 2010-08-19
From what I have gathered it's a driver issue with 10.04. I'll give it a try by installing a newer kerner in the weekend. Nvidia optimus is not supported in Linux and Nvidia has no plans at the moment to implement that.

---

### Post by Rusna on 2010-08-19
Ger3d: Could you boot again from live usb and see what "dmesg" gives you in console? 

Copy paste it to a file and paste here from Windows. Maybe we could start solving things, ethernet and wifi for starters. 

Any news about Optimus support so far?

---

### Post by Rusna on 2010-08-19
Alirght, I did some googling and as mentioned by Ger3d, sadly enough nvidia has no interest to support Optimus.

---

### Post by ubun_two on 2010-08-19
> **ger3d said:**
> Hello

I just got a new Asus 1215N netbook. when I boot with a USB flash drive with ubuntu 10.04 I do not get any network connection. no wifi or wired. The USB flash drive boots fine on other PC's. Should I do an install or is there a problem with that computer. Windows workes so the hardware i fine. 

Could anyone help I realy would like to get rid of windows

Thank's Gerhard

I had a similar issue with wired or wireless network not working at all on another laptop.  I went online on another PC and installed the new kernel to get the wired network working.  It might be worth a try.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

---

### Post by Rusna on 2010-08-19
Just an idea, how about 1215N with Maverick? It sure does have a newer kernel?

Anyone able to test? I just ordered mine, so maybe next week time for some testing!

---

### Post by lkarmaz2 on 2010-08-19
Furst, how did you get a 1215n? Here in the US we are still waiting on it. 

Second, does your version have USB 3.0?

Third, I am working on sn Optimus alternative by altering the Nvidia driver itself, but I am waiting to test on an actual 1215n before I make a public release. I have been using an Ion nettop to make my beta, and I am getting 70% to 80% the efficiency of Optimus by switching the normal driver for my underclocked one using a script.

---

### Post by Rusna on 2010-08-20
> **lkarmaz2 said:**
> Furst, how did you get a 1215n? Here in the US we are still waiting on it. 

Second, does your version have USB 3.0?

Third, I am working on sn Optimus alternative by altering the Nvidia driver itself, but I am waiting to test on an actual 1215n before I make a public release. I have been using an Ion nettop to make my beta, and I am getting 70% to 80% the efficiency of Optimus by switching the normal driver for my underclocked one using a script.

I'm in Finland, Europe, it has been shipping here for weeks.

No USB3.0

Alright, great news that the community takes on where Nvidia dithed us! I'll be happy to help you to debug etc.

---

### Post by Rusna on 2010-08-20
I know this is a long shot, but ultimate goal would be integrating the script of yours to work with [VGA-Switchero]("http://ubuntuforums.org/showthread.php?p=9667591") :)

Let's now just take small steps first.

---

### Post by comaide on 2010-08-20
For resume :

-Ubuntu like other linux distros, run on the netbook !

-For recognize the network hardware(wifi & wired), Ubuntu need a new kernel ? 

-The graphics cards works but auto-switch is not supported ?


That's it ?

---

### Post by lkarmaz2 on 2010-08-20
I do have one question I need 12015N owners to answer. What are the applications for which you need more graphics power?

I could theoretically get more efficiency by tailoring settings for certain applications. I actually am currently using WINE output for Windows Games (actually pretty good for a first beta), but my knowledge of Linux applications is a little lacking. What graphics levels are required for what programs? 

P.S. If anyone has a US release date for it, I can tell you when I will have a beta ready. I am planning on getting it ASAP.

---

### Post by masaz on 2010-08-21
I tested Asus 1215n with Maverick Alpha. The newer kernel has direct
support for Atheros AR8152 Ethernet and also Maverick repos
have the closed binary required for Broadcom BCM4313 wireless; suggests
automatically when installed. So, with quick test, both wired/wireless work
with Maverick.

masaz

---

### Post by ikkup on 2010-08-22
Hi!

Installed Ubuntu 10.04 and networking was dead. Found the driver for LAN. This is how you get it working.

Here you find the driver: 
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

Linux Driver: 
AR81Family-Linux-v1.0.1.9.tar.gz


Download the driver and unpack and install the tarball.

tar -xvzf AR81Family-Linux-v1.0.1.9.tar.gz
make
sudo make install
cd scr
insmod atl1e.ko


Thats it! LAN is now working. 

Now install wifi restricted drivers 

System->Hardware Drivers->Broadcom STA wireless drivers

Click Activate and wait until it finds you wireless network.

Do not activate Nvidia driver. That's how you get problems. 

I got everything working. Even compiz is running. Did'nt make any changes to graphics drivers. Just enabled Extra Visual Effects.


-ikkup

---

### Post by Jupp3 on 2010-08-22
> **ikkup said:**
> 
Do not activate Nvidia driver. That's how you get problems. 


Do you mean the nvidia graphics drivers? I mean, isn't the nvidia ion graphics kind of **the point** of this netbook?

So what kind of issues there are?

(In the recent past, I have had way too many problems with GMA chipset in my Acer Aspire One, while my desktop Ion system has been totally fine. That's why I wanted to upgrade to Ion netbook aswell)

---

### Post by ikkup on 2010-08-22
> **Jupp3 said:**
> Do you mean the nvidia graphics drivers? I mean, isn't the nvidia ion graphics kind of **the point** of this netbook?

So what kind of issues there are?



Hold you horses bro. I believe the driver is not quite ready yet. I tried also with ION driver found in Nvidia website and got the same results. After boot I only got a black screen and no way out.

Tried to boot it with vesa driver aswell but same black screen happend. Had to reinstall Ubuntu.

What I'm going to do is to just wait for a while to get the proper ION driver.

---

### Post by lkarmaz2 on 2010-08-22
Wow. Thanks for bringing this to my attention. The bios supports easy switching, and Intel drivers are readily available. It should take me all of 10 minutes to get this working as soon as I get my 1215N. I am stopping work on my script. This guy already did what I am doing, but he did it 10x better.

Basically, assume that I will post a beta here or in a new thread within 24 hours of the US release.

> **Rusna said:**
> I know this is a long shot, but ultimate goal would be integrating the script of yours to work with [VGA-Switchero]("http://ubuntuforums.org/showthread.php?p=9667591") :)

Let's now just take small steps first.

---

### Post by Rusna on 2010-08-24
> **lkarmaz2 said:**
> It should take me all of 10 minutes to get this working as soon as I get my 1215N. 

Basically, assume that I will post a beta here or in a new thread within 24 hours of the US release.

Alright, just give us heads up then :)

---

### Post by Jupp3 on 2010-09-06
> **ikkup said:**
> Hold you horses bro. I believe the driver is not quite ready yet. I tried also with ION driver found in Nvidia website and got the same results. After boot I only got a black screen and no way out.

Tried to boot it with vesa driver aswell but same black screen happend. Had to reinstall Ubuntu.
I could get around this by booting in recovery mode, in "low graphics" mode. If this doesn't work for you, you could probably boot to console-only mode, and then remove nvidia-related packages from there.

Both cable and wireless work, but connection seems to be rather unstabile...

NOTE: This is on 10.10 (which I know is not ready etc.) but I think recovery mode should help with older versions aswell.

---

### Post by Rusna on 2010-09-07
> **Jupp3 said:**
> Both cable and wireless work, but connection seems to be rather unstabile...

Wireless is unstable? 

How did you manage to install Ubuntu on this baby? I made USB stick with unetbootin and even the latest daily build is giving me a shell of busybox with error of bootarg missing? So I cannot even get to live-mode.

lkarmaz2: You've got your 1215N yet? Waiting for the GPU fix :)


//Edit: Alright, of course I could pop in external USB CD-drive but I'd rather do it with the stick.

---

### Post by Jupp3 on 2010-09-07
> **Rusna said:**
> Wireless is unstable?
Well at least for me. Usually goes fast for a while (when f.ex. copying data from nfs mount) and then the transfer rates just drop to 0. After I re-connect, nfs eventually picks up, but it's rather annoying... (and obviously would be much more problematic when downloading f.ex. install cd over the net, if the page doesn't happen to support resume)

Although it just might have to do something with my router... It was acting weird a few times (like it seemed that other connected computers couldn't use network for a while) and finally on sunday, it made itself into some error state, which prevented it from going online at all (local network worked just fine). Got a replacement yesterday, let's see how that works.
> How did you manage to install Ubuntu on this baby? I made USB stick with unetbootin and even the latest daily build is giving me a shell of busybox with error of bootarg missing? So I cannot even get to live-mode.
Actually I just used external DVD drive :-) (didn't have any eraseable USB thumb stick at hand)

---

### Post by Rusna on 2010-09-07
OK, I wonder if Broadcom STA drivers are gonna be updated before Maverick's release... I'm not that familiar with closed drivers. But let's hope the issue is with your router only rather than with the driver, but sounds odd.. Driverlikish problem?

Maybe I'll give the newest daily build a spin in my external DVD drive.

How's everyone else doing with this laptop, wireless issues? Anything else worth mentioning?

We should propably set up a new support thread for this netbook in general, but oh well.

---

### Post by emoguitarist06 on 2010-09-14
Does anyone know how someone in the US can order a 1215N w/USB 3.0? 
even if it requires international shipping?

---

### Post by Phelerox on 2010-09-14
> **Rusna said:**
> Wireless is unstable? 

How did you manage to install Ubuntu on this baby? I made USB stick with unetbootin and even the latest daily build is giving me a shell of busybox with error of bootarg missing? So I cannot even get to live-mode.

lkarmaz2: You've got your 1215N yet? Waiting for the GPU fix :)


//Edit: Alright, of course I could pop in external USB CD-drive but I'd rather do it with the stick.
I'm having the same problem, trying to install Maverick but with no success - refuses to boot! Used unetbootin and USB-Creator (gives a different error though) several times.

---

### Post by FreeTheBee on 2010-09-15
Strange, I had no problems installing maverick from a boot usb stick, which I created with the 'Create a USB startup disk' tool in Lucid. After installing the Broadcom drivers wireless worked fine as well. I have not noticed any instability yet.
I haven't installed the nvidia drivers, since I had no time to play around with it in the case of problems.

---

### Post by Rusna on 2010-09-20
I was testing Maverick a few days ago, pretty much everything seemed to work, even the hotkeys, brightness, WLAN on/off etc.

The only thing why I'm now having second thoughts about putting Ubuntu on this machine is the lousy Flash performance... Watching youtube with resolutions from last decade really isn't my thing. If there's HD available, I'm sure to want it.

---

### Post by Jupp3 on 2010-09-20
> **Rusna said:**
> I was testing Maverick a few days ago, pretty much everything seemed to work, even the hotkeys, brightness, WLAN on/off etc.

The only thing why I'm now having second thoughts about putting Ubuntu on this machine is the lousy Flash performance... Watching youtube with resolutions from last decade really isn't my thing. If there's HD available, I'm sure to want it.
Just download the videos with f.ex. [Video DownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/3006/"), I can't see any reason to watch videos using the crappy flash interface on ANY platform, when I can just download the video, and watch it with f.ex. mplayer.

In case of youtube, you can activate [html5 video support]("http://www.youtube.com/html5"), it's always better than flash video (but not available for all videos, sadly)

Back on topic, the wlan feels a bit weird... On some boots it seems to work without any problems, sometimes it just stops working randomly, and on one boot it didn't even work at all (didn't see any wlan networks available)

Haven't had too much time to debug it yet, but wasn't broadcom drivers open sourced just recently? Does it cover this chipset aswell? If yes, then there's hope for improvements :-)

---

### Post by Rusna on 2010-09-20
> **Jupp3 said:**
> Just download the videos with f.ex. [Video DownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/3006/"), 

Does that plugin work with Chrome as well? Supposedly? [FlashVideoReplacer]("http://flvideoreplacer-extension.blogspot.com/") also seems interesting...

> **Jupp3 said:**
> 
Haven't had too much time to debug it yet, but wasn't broadcom drivers open sourced just recently? Does it cover this chipset aswell? If yes, then there's hope for improvements :-)

Yes, Broadcom did open-source their drivers and yes, this BCM4313 chipset was included. So yep, when it comes to wireless, I'd say there're surely improvements ahead :)

Sorry for OT by the way.

---

### Post by Lianatyk-PL on 2010-09-28
I've found that 64-bit version of the newest Mint 9 Isadora has Wifi driver for 1215N included (Broadcom ?BCM4313). Strangely, the 32-bit version doesn't have it.  BTW: I don't know why but I didn't manage to install system from 4GB stick (installation task stuck in 3rd step), but it run perfectly from 2GB. Both were formatted and prepared by unetbootin.

---

### Post by Rusna on 2010-10-06
I believe this netbook is already out in the US?

lkarmaz2 and everyone else: How's the vga-switcheroo support coming?

I've been following [this]("https://launchpad.net/~hybrid-graphics-linux") project and I even created a acpidump DSDT file to help the project (pasted to the project's [mailing list]("https://lists.launchpad.net/hybrid-graphics-linux/msg00218.html")) but now I don't know what else to do to help.

---

### Post by Jupp3 on 2010-10-07
> **Rusna said:**
> How's the vga-switcheroo support coming?

More important than that, does ion2 support work at all? Would be much nicer to at least have Ion2 "always on"

Last time I tried, the system wouldn't boot to graphical environment (except in "restricted graphics" mode) and after getting that sorted out, I decided to wait a bit longer.

Regarding the network issues, it seems my system is dropping connection even with ethernet cable. And if I reconnect the wireless a few times (after network traffic stops), my cable modem goes to state, where network doesn't work on any of the connected devices (power cycle cures that)

Knowing that Broadcom drivers are rather bad, they still shouldn't be able to mess a cable modem. Maybe I have just bad combination, and broadcom and cable modem don't like each other :-P

(of course there's hope that all issues will be fixed, now that the drivers are open source)

Also, I have used network on windows enough to conclude that the same doesn't happen there.

---

### Post by Rusna on 2010-10-08
Regarding the wireless issues, I noticed that when I was testing Maverick in live-usb mode, that wireless was constantly 1 Mbps only with wl driver. That's quite a drop since it's N-based device :p

During the testing (roughly 3 hours) it didn't drop completely, but also never got quicker either. Let's just hope that the guys could make the broadcom drivers better. :)

---

### Post by Krakken on 2010-10-09
Hi everybody,
I've just got my 1215N in Italy. Everything seems to work OOTB. I installed the atheros driver following your instruction and after the broiadcom drive. Everything worked fine. Now every time I rebbot the wifi is working but not the cable and I need to repeat the procedure.
Where did I got this wrong?? There is a way to keep the new modules installed without need to repeat the procedure.
I'm running ubuntu 10.04 LTS sisnce the pc is to work out the office. I should have a 6 cell battery but the actual time is 3 hours and 45 minute...not very long. The wifi is always on..
Does anyone can help me??
Many thanks

Krakken

---

### Post by Rusna on 2010-10-12
There has been success in turning off the Ion chip, read more [here]("https://lists.launchpad.net/hybrid-graphics-linux/msg00254.html").

So it IS possible to turn off/on the nvidia ion chip, now the only thing that we could wish for is the possibility hot switch graphics.

---

### Post by Jupp3 on 2010-10-12
> **Rusna said:**
> There has been success in turning off the Ion chip, read more [here]("https://lists.launchpad.net/hybrid-graphics-linux/msg00254.html").
Thanks for the info, will try when I have time

> So it IS possible to turn off/on the nvidia ion chip, now the only thing that we could wish for is the possibility hot switch graphics.
Does vga-switcheroo actually allow that? I thought it still needs X restart for changing the chipset...

---

### Post by Tryfon on 2010-10-19
Hello everybody!
I've been reading this topic about the 1215N because I am interested in buying it. I would like a nice summary about what is the state of its hardware support in the newest Ubuntu 10.10 From what I've understood it is the networking and the nVidia graphics that have problems. I'll post some simple questions and I would like to ask for simple and clear answers:

1. Does networking work well now? Are there any drawbacks?

2. Does the nVidia chipset work?

3. I understand that it is possible to switch the graphics card under use through BIOS to the integrated Intel chipset which works well. Does it support 3D acceleration?

3.1 When you do switch to Intel graphics does the Ion chip continue to be used consuming power unnecessarily? 

4. What does turning off the Ion chip mean? Has it got to do only with power consumption?

Forgive my ignorance, I'm just trying to understand if it is worth buying or not.

---

### Post by Rusna on 2010-10-19
As a bottom line, if you haven't yet bought a netbook and you plan to use linux on your netbook, avoid ion2/optimus-based netbooks. Period.

There is no option in bios to choose between integrated & ion chipset, there's no way yet to make this nvidia chipset work under linux, and at least for me, even the two-finger scrolling doesn't work without hacking a bit. Plus then again, for me the wifi only works at 1Mbps, so one might think twice before putting linux on this machine, keep in mind that this is N-draft capable wifi chipset.

You want eee with 12"? Get the older brother, 1201N, that should work without problems.

---

### Post by jimmy.77 on 2010-10-19
> **Rusna said:**
> You want eee with 12"? Get the older brother, 1201N, that should work without problems.

GOSH! Glad to hear this... I threw away about 500€ (me too in Italy) for this machine! 
I think soon or late something have to move. ION2 and Optimus are great technologies, but probably too "young" yet. 
Still waiting for a better future...

Bye all, 

J.

---

### Post by emoguitarist06 on 2010-10-19
> **jimmy.77 said:**
> GOSH! Glad to hear this... I threw away about 500€ (me too in Italy) for this machine! 
I think soon or late something have to move. ION2 and Optimus are great technologies, but probably too "young" yet. 
Still waiting for a better future...

Bye all, 

J.

You looking to sell your 1215N? Does it have USB 3.0?

---

### Post by steventh on 2010-10-20
Belgium here, I have 1215N since a week now. (USB 2.0)

First of all, I'm very happy with this new release in asus' EEE series! Relatively fast for a netbook, nice graphics, stylish design, very quiet and yet good ventilation (it doesn't heat up very much). 

Installed Ubuntu 10.10 netbook remix on it, in dualboot with windows 7, now works fine.

When using a bootable USB to install linux, keep in mind that this BIOS has a Booster-function enabled. At start-up, immediately hit F2 to enter BIOS and change the Boot device priority to boot from USB.

Ubuntu: WLAN is not working from the beginning, but LAN does. So with your internet cable plugged in, you can download the WLAN driver provided. Then most of the time, the internet connection works fine for me.

Do not install the Nvidia driver provided, nor the one available on the Nvidia's website. After reboot, X-system configuration was messed up and could not start Gnome. I needed to reinstall ubuntu completely. The graphics are fine without the Nvidia driver, so I'll just wait untill the driver is stable.

---

### Post by jimmy.77 on 2010-10-27
> **emoguitarist06 said:**
> You looking to sell your 1215N? Does it have USB 3.0?

This model got USB 2.0 (I read somewhere that all EU models should had USB 2.0), and sorry no, at the moment I don't want to sell! :D

J.

---

### Post by jimmy.77 on 2010-10-27
> **steventh said:**
> Belgium here, I have 1215N since a week now. (USB 2.0)
[...]
The graphics are fine without the Nvidia driver, so I'll just wait untill the driver is stable.

Exactly the same for me. I've done same steps :)
If I'll found something new, I'll post here.

Bye, J.

---

### Post by Fabio166 on 2010-10-28
I've got the asus 1215n with Ubuntu 10.10 installed on it.
I had some problems with the wired internet connection but I fixed it by upgrading the kernel to the 2.6.36 version.
I tried to install the proprietary Nvidia driver (from "additional drivers") but it is still not working, even with this new kernel version: it just starts a non-graphic terminal and I have to reboot it in recovery mode and uninstall the driver.
Waiting for a solution....

Fabio

---

### Post by gnagnibu on 2010-11-16
Hello everybody, good news from Italy ;) 

Here LAN & WLAN work great on Ubuntu 10.10.

Here the passages:

- basic installation of Ubuntu 10.10 , LAN works out of the box.
- safe-upgrade of all the packages
- reboot caused of upgraded kernel
- installation of Broadcom driver
- modified /etc/udev/rules.d/70-persistent-net.rules deleting rows about creation of WLAN device (for my pc eth1, so the ones with NAME="eth1" at the end...)
- reboot 

Unfortunately nVidia ION2 doesn't work at the moment, so don't install nVidia drivers!!!
If you have already installed, purge all the packages nvidia-* and remove /etc/X11/xorg.conf then reboot.

Hope this can help!

Giovanni

---

### Post by lokutus25 on 2010-11-27
> **gnagnibu said:**
> Hello everybody, good news from Italy ;) 

- installation of Broadcom driver

Giovanni

I'm lazy...can you post the link of the broadcom driver for WLAN?
Thx ;)

---

### Post by Tryfon on 2010-11-27
The Broadcom driver is automatically discovered by Ubuntu (and then you can easily activate it) as long as you have an internet connection. Obviously you will ask "And how am I supposed to have an internet connection without my wireless card operating?" and the answer is: Get an ethernet cable and connect through wire. The wired network card works perfectly out of the box. Then hit "System->Adminstration->Hardware Drivers" activate the broadcom driver and reboot. After this you won't need the ethernet cable anymore.

---

### Post by lokutus25 on 2010-11-28
Thanks Tryfon. I just installed the 10.10 x64. And found them! ;)
Thx!

---

### Post by ch3rryc0ke on 2010-12-06
I'm a first time Linux user, ended up buying the 1215 just to run Ubuntu.

Installed from the Windows installer-- Wireless and all that worked, but then I activated the NVidia driver and could not recover from it (kept getting a black screen) as others have mentioned here. Recovery mode wasn't giving me a full console, only initramfs and I couldn't figure out how to remove the driver packages from there.

I decided to repave and am installing Ubuntu again. I did not try installing the nvidia driver from their website, I simply activated the one that was detected by Ubuntu.

**Has anyone had success getting the Nvidia driver working yet?**

---

### Post by LtPitt on 2011-01-03
Hi everybody!

I've had a lot of troubles with 10.04 to get broadcom working "the easy way" enabling restricted drivers so I've downloaded from broadcom site the driver, compiled it and used it: no problems.

But now, everytime I reboot I have to digit:

sudo modprobe lib80211
sudo insmod wl.ko

I thought: why not using a script?!

So I've created a script, called it wifilan and saved it in /usr/bin:

#!/bin/bash
sudo modprobe lib80211
sudo insmod wl.ko

I did a
sudo chmod +x wifilan
then added it to startup applications and, finishing touch, with sudo visudo I've added:

myusername ALL=(ALL) NOPASSWD: /usr/bin/wifilan

The little bastard won't work because it keeps on asking the sudo password when loaded...
Any hints?

All the rest is perfect, thanks to your hints...
I'm just waiting for good news about the video adapters :D

---

### Post by lokutus25 on 2011-01-04
> **LtPitt said:**
> 

But now, everytime I reboot I have to digit:

sudo modprobe lib80211
sudo insmod wl.ko



If you add the module names in /etc/modules, aren't they loaded at boot? You can copy the wl.ko in the same dir of lib80211.ko and than run a depmod -a. Add them to the end of /etc/modules and reboot.
To check if they are loaded use lsmod from bash :)

---

### Post by LtPitt on 2011-01-04
Hey! :D

Thanks!

The lib80211 module worked great but I couldn't achieve the same result with the wi.ko...
I have it in my home folder and specified the full path in /etc/modules
maybe I should copy it elsewhere?
I did a sudo modprobe -a in that folder, anyway.

Thank you, my friend, once again :)

---

### Post by LtPitt on 2011-01-05
For everybody who has my same problem:

I've solved it adding

modprobe lib80211
insmod wl.ko

(without sudo)

to /etc/rc.local

which is used, as far as I've understood, to run commands at startup with root privileges.

It may be not the best solution but it's for my personal netbook and it works :D

---

### Post by thelaw on 2011-02-03
I was having problems with Meerkat (Kubuntu) and LAN and WLAN.  For eth0, I was disconnecting after a few mins with rebooting the (seemingly) only way.  After reading around, I decided to go with the new kernel - 1.6.37rc2 for Meerkat.

I went to the ubuntu kernel-ppa and grabbed 3 files:

linux-headers-2.6.37rc2...all.deb
linux-headers-2.6-37rc2-generic...i386.deb
linux-image-2.6.37.rc2-generic...i386.deb

ran them all and then did a sudo update-grub, rebooted, selected that kernal and...voila...LAN is now solid.

Doing this, I noticed a message that said something about doing "meta" or something if I wanted updates...but...well....shame on me for just blowing through it :)

What this did not resolve was the problem I'm having with WLAN.  Granted, this is KDE so...this may not be the best place...but...I am unable to see or connect to all wireless networks.  I can see and connect to some but not my rooted droid's Wireless Tether.  

My win7 partition can see this being broadcast and can connect no problem, however, when I flip to the Kubuntu side of things, I do not see that SSID being broadcast.  Going into network manager, I can manually add it and select it, however, it will never connect.

I have this same problem at some client networks....suggestions?

---

