---
title: "Viliv s5"
date: 2009-04-23
forum: Hardware
---

### Post by slick666 on 2009-04-23
Has anyone seen the viliv s5? It looks like a great UMPC and probably a great platform for Ubuntu Mobile,

Here is a good vid showing it
[http://www.youtube.com/watch?v=J35AOdit0Xw&feature=channel_page]("http://www.youtube.com/watch?v=J35AOdit0Xw&feature=channel_page")

---

### Post by psychoticdream on 2009-04-23
i'm actually thinking of getting it but problem is that the number of machines is so limited  i think it was said less than 500 machines were gonna be put on sale so its gonna be  sold out really fast   still i'd like to see linux on it :D

---

### Post by blauhung on 2009-05-30
I just got one, the thing is wonderful.... but currently having issues.  I just made a live image of Ubuntu-MID found here
[https://wiki.ubuntu.com/MobileTeam/Mobile?action=show&redirect=MobileAndEmbedded](https://wiki.ubuntu.com/MobileTeam/Mobile?action=show&redirect=MobileAndEmbedded)

and it doesn't seem to want to boot.  The first time I started it up, it went into the normal ubuntu loading screen and then crashed out with an error that I vaguely remember saying something to the effect of ".... please update your kernal...." but when i went to copy the error down to search for a solution, my arm hit enter on the keyboard and then the error was gone and replaced with an(initramfs) prompt.

Now each time I boot it dropping out to the prompt without any error.  Any help would be welcome.

---

### Post by blauhung on 2009-05-31
Tried netbook-remix now.  The system installs without a hitch, but looks like no touch screen drivers, and when switching between menu items the system takes about 4-5 seconds to clear the icons from the last menu off the screen.

back to win7 for me.

---

### Post by rado3105 on 2009-05-31
it should run normally with linux, it is atom based and intel has good linux support. I want to buy also this thing, maybe Umid M1, but the linux must be able to run on it without problems. There is no way to use ms windows for me.

Maybe you could try to install there linux for netbooks.

---

### Post by blauhung on 2009-06-02
> **rado3105 said:**
> it should run normally with linux, it is atom based and intel has good linux support. I want to buy also this thing, maybe Umid M1, but the linux must be able to run on it without problems. There is no way to use ms windows for me.

Maybe you could try to install there linux for netbooks.

doesn't look like the touchscreen is recognized.  I'm a bit clueless on how to go about tracking down drivers for it

also, in windows viliv has some software that enables and disables the bluetooth and wifi radios.  it looks like by default on any boot they are disabled and unless the software tells them to turn on they stay hidden to the OS.  so to get them to work someone would have to enable the radios first.

---

### Post by mexisme on 2009-06-09
> **blauhung said:**
> doesn't look like the touchscreen is recognized.  I'm a bit clueless on how to go about tracking down drivers for it

also, in windows viliv has some software that enables and disables the bluetooth and wifi radios.  it looks like by default on any boot they are disabled and unless the software tells them to turn on they stay hidden to the OS.  so to get them to work someone would have to enable the radios first.

I had the same problem with my Samsung Q1U years ago.  The problem there was though the Kernel recognised the driver, X.org couldn't understand the protocol.  Fortunately, someone had written a driver:

[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)

---

### Post by Sudrien on 2009-06-27
From what I've read, win7 resisters it as a ps2 driver.

Also see comments in, [http://philwiltux.blogspot.com/2009/06/viliv-s5-and-linux-not-good.html](http://philwiltux.blogspot.com/2009/06/viliv-s5-and-linux-not-good.html)

The x70 is likely to have a similar interface, and is said to have linux available pre-installed; hopefully it will have a similar hardware spec.

---

### Post by JaseP on 2009-06-28
I'm the one who made the comments on Phil's site... 

Check the latest one about 3D support on the Viliv S5. Netbook-launcher runs passably well in Jaunty once 3D is up and running (you'll know its working when your glxgears reports frame rates at 200+). The joystick in arrow key mode is actually damn fast as a selection tool in Netbook-launcher... push for direction, push down the plunger to TAB, and OK to select. Compiz is a bust for some reason. I've placed a link there to the PPA repositories.

The one app, onboard, can provide an on screen keyboard. Use of it can be had by using the joystick in mouse mode (press and hold the MENU key a few seconds).

---

### Post by btbluesky on 2009-06-29
Keep this alive!! I want to boot it to any distro... so bad. Got a SLC USB driver just for this purpose.
They should just release the damn spec anyway, it's not like anyone else would do another S5/X70, cuz it's such a niche market.

But Garmin mobile PC is "super nice" w/ the GPS chip. beat a $400 gps unit.

---

### Post by JaseP on 2009-06-29
As for Specs... Here you go...

Viliv S5:

CPU: Atom 1.33 (Siverthorne)
System Chipset: SCH US15W (Poulsbo),... Incl Intel GMA 500 Graphics, USB host controller, SDIO Host controller.
RAM: 1 GB
HD: Samsung SATA 60GB
Wifi/Bluetooth/GPS: Marvell SD8686 via SDIO / SiRF STAR III
Touchscreen: AMI EC controller, (4 wire?!?) resistive touchscreen with "Haptic Feedback" connected as an internal ps/2 port device.

I have recently found information that may make either powering up the Marvell SD8686 and/or installing Ubuntu 8.04 a possibility. Ubuntu 8.04 with a 2.6.24 Kernel is apparently the best supported for the chpset for the device... but not its HD.

The problem with Ubuntu 8.04 is that the SATA HD does not recognize... but there may be a solution. If one launches the Install ISO with the generic ide option, it may recognize the drive... Alternatively, turning on RAID support may do this as well... but would forstall booting into Windoze, for those so inclined (if Hardy installs on this thing with full 3D, Wifi, BT, touch Screen and GPS,... WHY, would anyone want Windoze on it?!?!?). Lastly, I am looking into updating the BIOS to see if they have added more SDIO options because of the bugs that have surfaced in Windoze. I don't want to brick my unit though,... because wiping the Windoze partition probably voided my warranty.

The problem with waking the chipsets in Jaunty is that the Video in Jaunty is proving to be pretty unstable, and leads to lock-ups every hour or so... And still there is no joy as far as touchscreen or Wifi/Bluetooth.

So re-installing using Hardy with all the netbook remix stuff, seems like the best bet. I'm just a little upset that I'll have to wipe the HD again since I have the /home partition formatted with EXT4. I'll keep everyone informed and hopefully I will have an easy to follow solution... If anyoine else knows more about these things than I do,... please step up. Some of it is over my head.

By the way... Although I might just be paranoid,... I smell the stench of M$ in the fact that this device is a #$%#@# to set up. I believe they hijacked the Viliv S5, making YuKyung an offer they couldn't refuse to alter the device so that installing Linux would be an uphill battle. I think they altered the AMI Bios in such a way as to make Linux installation a real problem. Part of the issue is that the SDIO does not see the Marvel chipset on boot, apparently due to it being powered down. M$ is running scared against Linux in the embeded market,... and showcasing a machine that easily runs Windoze 7 and for which there is no out of box Linux solution is good PR for their FUD machine. The device originally was demonstrated with a version of Asianux Linux. So,... there WERE drivers available for the thing. I would really like to kow how much YuKyung is paying for their Windoze licenses... I bet it's under $20 per unit,... and closer to $0, with some M$ re-engineering "advice" thrown in...

---

### Post by JaseP on 2009-07-02
OK,...

Using the Ubuntu 8.04.1 Mobile IMG file, you get a very extremely basic 2D acceleration from the Poulsbo chipset... The Moblin version of that release is very lacking in even the most basic system tools, and touchscreen setup does not work. Neither does the system identify the Wifi/Bluetooth/GPS adapter.

It looks like going to Jaunty is the best bet right now... Jaunty is the best supported for getting the 3D running, even if in an unstable mode. It is also getting the most developer attention... So there is no point in retrograding to the older release for chipset support. Using a Dell 8.04.1 install disk is a bust too (there was some talk of them having proprietary 3D drivers working).

Efforts should focus on getting Jaunty running with full accelerated 3D graphics, and working on the other devices from there... The most critical ones are the touchscreen and the Wifi, in that order. I have more identification of the chipsets used in the device taken from a Korean site (too bad I don't speak and write Hangul)....

The radio chipset is the W2CBW003, which consists of a Marvell SD8686, either a Freescale i.MX21 or 31, or a Samsung SC2443, 2412 BT radio, plus likely the SiRF Star III GPS.

The AMI Bios resides on a SST 49LF008A Memory Flash chip, which is compatible with the Intel 82802 Firmware Hub Component (FWH).

All are Linux compatible. So,... It stands to reason that the devices were turned off in the bios by YuKyung (likely at the behest of M$). If we cold find a way to turn them on, I suspect the problems in getting Jaunty running in all its glory would be over.

---

### Post by JaseP on 2009-07-09
Status,...

Attempted an eGalax touchscreen driver (only one that suports the internal ps2 port as the connection) in Jaunty, but so far it's a bust... There is trouble in calibration. Serio_raw fails to connect... I'm looking to do a bug hunt and use some info gained from the MP3Car forums... the fan following for building in-car multimedia PCs. They tend to use the Atom based motherborads for in-car user installations... or MIDs stipped out of their cases and mounted inside the dash. An eGalax driver looks like the way to go...

There is some info on getting the the UMID M1 netbook working in Linux. It is a very similar device, electronically, but features a clamshell design and keyboard. But it features the same CPU, System on a chip (Intel SCH US15W, incl. the Poulsbo GMA 500 graphics adapter), and the same SDIO connected Marvell SD8686 based chipset for Wifi (I think the same W2CBW003 multiradio chip).

On a positive note, 3D acceleration is working fairly well, with framerates on glxgears of around 114 FPS on a full-screen glxgears running from the netbook-launcher App/window (sub)manager... Some tweaks to power mgmt are needed for stability using the gnome configuration editor (the regular GUI tools don't give enough options)... No Compiz,... at least yet... Compiz fails to load, even after tweaking the xorg.config file to include compositing support... No idea if this is bad conf file entries, lack of proper dependencies or the dri driver causing problems...

Cellwriter is the superior on-screen keyboard. It features a mode that is keyboard only and also supports inking, similar to the Palm or Nokia N8x0 series inputs. Once the touchscreen is working, using cellwriter would be the best bet.

Also recommended is passwordless logins and disabling password screen locks (especially at hibernation)... No keyboard after all... I haven't found a way to call any on-screen keyboard during logins. Regular password entry prompts can be set to function like regular windows, so the use of the on-screen keyboard works.

---

### Post by JaseP on 2009-07-13
Update,...

Attempting on Ubuntu 8.10 hoping to see more indpendant driver support for the older release...

Have working: accelerated graphics (2D & 3D), Compiz (can be accomplished on Jaunty as well, with minor edits of various configuration files)...

Currently looking for eGalax touchscreen driver for Ubuntu 8.10 allowing for driver to be configured against the ps/2 port via the serio_raw driver module.

One thing for sure... you need to lock your kernel version (Linux generic 2.6.24.7.11???) after installing the Poulsbo 2D/3D drivers, as they will break if you update your kernel & headers. I've currently nerfed my Synaptic configuration to the point of near un-usability trying to do this ... Glxgears is not responding nearly as well to the 3D drivers under 8.10 as it did under 9.04... However Compiz responds beautifully. All features are available, and even improve system performance, taking the computing load off the CPU...

PS - I've read about Foxconn's sabotage of the bios on some of their motherboards,... making me think something similar was done as far as the power managment and SDIO support of the viliv s5. It is, at least, an avenue to approach... I may even contact Viliv for tech support as to how to turn on the multi-radio chipset.

---

### Post by JaseP on 2009-07-16
Further update...

Using eGalax drivers on the touchscreen seem to be a bust... conflicts with evdev and work-arounds tend to either yield failed results or non-working usb mice and keyboards, including the mouse function of the pointer stick (not exactly what you want here).

A solution more likely to yield positive results would be to use /dev/psaux and psmouse and various settings in the xorg.config files to take the touchscreen's raw data and translate that. There was early work in this area when the mouse and keyboard input was first transported into kernel space in the early kernel 2.6 incarnations... Some of the workarounds developed then but rarely used now might yield better results...

Another possible temporary work around for people who use both this and a bluetooth enabled Palm (e.g.: t3, Tx, Lifedrive, etc.)is to use a Palm app called Remote Commander to emulate a bluetooth mouse and keyboard. Used in conjunction with a bluetooth dongle on the Viliv, it would yield you a touchscreen and keyboard,... even if they aren't right there on the device, and you have to lug around another unit... But,... it gives you a reason to dig your Palm out of the drawer.

The Wifi and bluetooth seem similar to units used on the later Palms... So I am going to investigate the possibility of taking the changes made to the Linux kernel that has been ported to the Palm TX, by the folks at Hack&Dev, to see if it might yield us some good results... or at least a start. So, interstingly enough Wifi, and Bluettoth might be a faster fix than the touchscren... although there has been some progress on a similar device, the fijitsu u820, in getting its touchscreen working without (I think...) eGalax drivers. The same people also have had some success in talking to the GPS chips on the fujitsu u820which also use the SiRF Star III chipset.

To sum it up:
Working; Graphics (2D, 3D, and Compiz support) with minor hacks from the people at the Launchpad PPAs, and some tweaks to config files.

Not working: Touchscreen, wifi, bluetooth, and GPS.

Blame game:
Blame M$ and Yukyung (Viliv) for putting together a device which intentionally cripples the ability to install a 100% working Linux. (Crippled BIOS, choice of unsupported Hard Drive in earlier Linux kernels, turning off the power of embeded units with no easy way to turn them on, using a Ps/2 connected touchscreen instead of a usb connected touchscreen, and use of a graphics chipset with closed source portions of the drivers).

Blame the Linux Kernel Developers for moving mouse function into the kernel space making use of older drivers for touchscreens a real pain in the back-side.

---

### Post by kozian on 2009-12-26
2JaseP: first of all thanks for your posts.
Any more news? What about 9.10 on s5?

---

### Post by santana on 2010-01-03
any new developments?

---

### Post by thingmaker on 2010-01-06
Just lending my voice to the desire for info. My Sony UX is dieing and I am looking at the s5 as a replacement.  I am quite interested to know the status of the s5 and 9.10.  Any progress with wireless? Also, I have heard conflicting reports of the headphone jack actually being a mic/headphone jack, can anyone with one of these confirm this?

Thanks

---

### Post by JaseP on 2010-01-09
So far...

I have had Jaunty running on the S5 for some time now but with no support for the touch screen, Wifi, bluetooth or the GPS chipset. A few tweaks to the GUI makes it usable, and you can use a USB Wifi adapter to get Wifi Access. Same for bluetooth.

Yukyung has released information related to how to activate the devices connected to the SDIO bus, but only one guy who claims to have been working on it has done anything with it, and hasn't released what he has done to anyone else (a month or so after he claims to have the touchscreen working and devices activated).

PSB drivers are available for the poulsbo video chipset on the Launchpad PPA... (Karmic and Jaunty both appear to be supported). I might give Karmic another try. It might have more support for the SDIO bus...

---

### Post by JaseP on 2010-01-09
> **thingmaker said:**
> I have heard conflicting reports of the headphone jack actually being a mic/headphone jack, can anyone with one of these confirm this?

Thanks

The headphone jack ***IS*** an iPhone compatible headset jack. An iPhone headset with a built-in mic ***SHOULD*** work,... but maybe with mixed results in terms of quality.

---

### Post by JaseP on 2010-01-21
If you check out the pocketables.com forums, you will see that the application to activate the devices has now been released. Our thanks to an Intel employee, who was involved in writing an app, and was kind enough to release the application to us...

Bluetooth is working, the GMA500 graphics are working, Wifi is *somewhat *working (trouble with WPA & WPA2), the touchscreen recognizes events, but I have yet to get the drivers for it working. The GPS,... well, I am not sure how it is connected, but once someone figures that out, it *SHOULD *be able to work through the gpsd daemon.

---

### Post by clmaxwell on 2010-02-08
that, sir, is fantastic. I will definitely be coming back to write a guide on this once all drivers are available. I have an s5 I'd be glad to help test on, as well.

---

### Post by yeejr on 2010-02-23
anything?

Thinking of buying an S5

---

### Post by deadhp1 on 2010-02-26
What touch screen controller is inside the viliv s5?
If it's connected over ps/2 there is another option you might not of tried.
[http://www.ideacom.com.tw/DR_UTS6680.htm](http://www.ideacom.com.tw/DR_UTS6680.htm)
This controller comes in USB or PS2 versions.
I have a ClarionMind and the internal touch screen is connected to ps2 via the uts6680 controller.  Other devices that use this driver/controller are the t91(ps2), Dell Latitude 2100(usb?), Gigabyte M528(?)

There is also a liveusb for the Clarion Mind with the touch drivers installed and the poulso drivers installed and mplayer-vaapi.  The resolution is however set to 800x480.  It's just ubuntu 9.04 with some modifications to enable a few things.
[http://mindbuntu.blogspot.com]("http://mindbuntu.blogspot.com/")(It's getting renamed on the next release).
If it booted and worked for you,  you would have to at least change the xorg.conf file to your resolution.  
You would probably need to do the things from this post:
[http://http://forum.pocketables.net/showpost.php?p=35888&postcount=154]("http://http//forum.pocketables.net/showpost.php?p=35888&postcount=154")

I'm interested to see if the Viliv touch screen will work with the Ideacom uts6680 drivers.  Good luck.

---

### Post by lara.layaa on 2010-02-26
Nice information
Thanks

---

### Post by JaseP on 2010-03-02
Update,...

The ideacom drivers are a no-go,... unless I am doing something wrong...

I am trying the eGalax drivers again, but think they will be a bust too...

The touchscreen is apparently an EZEX touchscreen,... but I do not know whether that is a re-branding or not... I am having trouble compliing the drivers we were given... (no target errors), and the eGalax drivers seem to detect the touchscreen, but then not work. I really wish I could get this thing going... I have a sales conference in less then a week and I would like to use the Viliv to take notes... Much more convenient than a touchscreen laptop/netbook.

Complicating matters is that I believe the GPS unit wants to come in as ttys0, and so does the internal ps2 port that the touchscreen connects on...

Not activating the GPS at startup makes the "joystick" unresponsive as a pointer...

---

### Post by deadhp1 on 2010-03-11
Sorry bout that,  I didn't know what kind of touchscreen it used.  The evtouch driver might work for you.
I found a thread that might help you.

[http://forum.pocketables.net/showthread.php?t=4952](http://forum.pocketables.net/showthread.php?t=4952)

If I had a viliv s5 I would be able to build a proper livecd for it. 
I have no way to test my livecd without the hardware,  otherwise I could just make some modifications to it.
If you do decide to use my iso as a starting point, you may want to rewrite /usr/bin/dexconf as well as the current xorg.conf.
It's been modified to write an xorg.conf with the options for both the GMA 500 driver and the ideacom UTS6680 driver(on PS2 port).  So you'd want to rewrite these,  at least if you want to rebuild the livecd with Remastersys.
If you just want to use it to instal you could just rewrite the xorg.conf,  but if X generates a new xorg.conf it will go back to thee original.
Sorry I couldn't be of much help.

Did the wireless at least work?
What about playing back h.264 movies with mplayer-vaapi or SMplayer(also using vaapi)?
On the clarionmind we have the UL11L chipset, and it can only decode SD h.264 with hardware decoding.  The US15 chipsets should be able to pull of HD decoding.

---

### Post by JaseP on 2010-03-13
The evtouch driver won't work unless it's been updated to include the EZEX's chipset... What we have are sources for a specific eGalax driver version, but I have not been able to compile them... A patch for the SD8686 wifi is needed, but the same thing applies...

---

### Post by Snow Keld on 2010-03-19
hello everyone, i'm interested in buying one of these, but i wont even consider it unless there is a way to keep a current version of ubuntu running on it without problems.

i dont really care how much work it takes to make it work, as long as it works once tweaked correctly.

that being said, i'd like to thank all of you for working on this device, and i hope more people gain interest in it.


so dont give up! please!

---

### Post by JaseP on 2010-03-21
The big problem with getting a current version of Ubuntu running on it will be kernel updates... The kernel requires a bit of patching to get running with all the devices. If you don't mind updating the patch process every time there is a kernel update, or locking the kernel version instead, you should be fine...

That said, I still haven't gotten everything working, myself...

---

### Post by ibgeorgeb on 2010-03-21
Great work JaseP and all of you contributors. I too am looking at the s5 but I'll only buy one if Linux can be installed and functioning properly. Best wishes, i2bgB

---

### Post by JaseP on 2010-03-28
Right now, the following is the status:

[LIST]
[COLOR="Navy"][*]Graphics working 100%
[*]Bluetooth working 100%[/COLOR]
[COLOR="DarkRed"][*]Wireless about 75% (no WPA or WPA2,... & Using Gnome's Network Manager locks the system)
[*]Touchscreen about 33% (touches are registered, but drivers are not correctly translating the coordinates, and calibration is not yet possible).
[*]GPS about 25% (device turns on.... that's about it... The device is likely attached to the /dev/ttys0 port, but so far no response from any apps that use gpsd to interface to it,... admittedly not much work being done there...)[/COLOR]
[/LIST]

Anyone who knows how to patch kernel modules is welcome to give us a hand,... What we really need is to apply the patches that exist "out there" to the psmouse driver to make it stop trying to report the PS/2 port to /dev/mice, or at least force it to do so with absolute coordinates...

---

### Post by fanum on 2011-02-12
> **JaseP said:**
> Right now, the following is the status:

[LIST]
[COLOR="Navy"][*]Graphics working 100%
[*]Bluetooth working 100%[/COLOR]
[COLOR="DarkRed"][*]Wireless about 75% (no WPA or WPA2,... & Using Gnome's Network Manager locks the system)
[*]Touchscreen about 33% (touches are registered, but drivers are not correctly translating the coordinates, and calibration is not yet possible).
[*]GPS about 25% (device turns on.... that's about it... The device is likely attached to the /dev/ttys0 port, but so far no response from any apps that use gpsd to interface to it,... admittedly not much work being done there...)[/COLOR]
[/LIST]

Anyone who knows how to patch kernel modules is welcome to give us a hand,... What we really need is to apply the patches that exist "out there" to the psmouse driver to make it stop trying to report the PS/2 port to /dev/mice, or at least force it to do so with absolute coordinates...

I own a Viliv s7 with the same wifi chipset, and was never able to make it work with network manager (and even wicd), but for some reason I found one version of natty daily image that it works on (after alpha 1, right before alpha 2). I now have it working (full wpa2 and everything), but if I update, it breaks again. Not sure who to alert, and what information to provide so that this can be resolved, if you have any ideas, let me know

---

### Post by fanum on 2011-02-12
I also should add that even tho my Viliv s7 has a different touchscreen (also not working out the box), I did find a nice app called xinput_calibrator that works for configuring my touchscreen, so it may be of help to you guys. Here is the ppa:

[https://launchpad.net/~tias/+archive/xinput-calibrator-ppa](https://launchpad.net/~tias/+archive/xinput-calibrator-ppa)

---

