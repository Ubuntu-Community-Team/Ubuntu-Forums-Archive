---
title: "ASUS EEE Box"
date: 2008-08-04
forum: Hardware
---

### Post by Saiing on 2008-08-04
So the ASUS EEE Box is available, and looks like a reasonable spec machine with a nice footprint and low power consumption.  I need a small form factor server fairly urgently.  As you're probably aware, ASUS has rather disappointed the Linux community by releasing a Windows only version of the box first (with a Linux version to follow later).  However, due to the pressing commitments of a project, I don't really have the time to wait for the Linux box to arrive, so I'm probably going to buy the launch model and put Linux on it myself.

My question essentially is: Is there anything about the basic spec of the EEE Box that might cause me problems when trying to install Ubuntu?  I'm not too concerned about small details (e.g. if the card reader didn't function it wouldn't be an issue because it's going to be a small dev server).

FYI to save you the trouble of looking stuff up, the rough spec is as below (some parts I don't know the specific make/model):

Processor: Intel Atom N270 (1.6 GHz, FSB 533) 

Memory: DDRII-400 512 MB / 1 GB

Storage: Seagate 2.5" 80 GB Low power HD

Chipset: 945GSE + ICH7M

VGA: On-board Intel GMA 950

Networking: 10/100/1000 Mbps LAN, 802.11n WLAN

SD/MMC/MS slot: SD, SDHC, Mini SD, (Micro SD through adapter) ; MMC, MMC plus, MMC4.x, RS MMC, RSMMC4.x (MMC mobile through adapter);MS,MS PRO

Audio: Azalia ALC888 Audio Chip

Front Ports:
USB x 2
Card Reader x 1
Headphone-out jack (WO/SPDIF) x 1
MIC x 1

Rear Ports:
USB 2.0 x 2
Gigabit LAN x 1
DVI out x 1
Line-Out (L/R) with S/PDIF x 1
WiFi antenna

---

### Post by indiekid97 on 2008-08-04
I know it's not much help, but I can verify that Ubuntu recognizes the integrated graphics. I have the same chipset on a budget box. This probably doesn't help much for what your using it for, but I thought I'd let you know anyway.

---

### Post by Saiing on 2008-08-04
No really, thanks - that's exactly the kind of comment I'm looking for.  While it doesn't guarantee trouble free installation, it at least helps to identify whether or not the key components are supported.

---

### Post by RedPandaFox on 2008-08-05
Oh heck yes! I have been waiting for the Eee Box for months, I'm going to sell one of my 2 eeepcs for it. Anyone want a 2gb eeepc surf? :P
It shouldn't have any problems with Ubuntu from what I see, Hell, I got Ubuntu working on a G3 mac so I don't see why that will stop it? :)

---

### Post by anontrol on 2008-08-10
I've been working with an Intel D945GCLF board trying to get a general feeling for how well Ubuntu works with it.  I'm running 2GB of RAM and 32GB transcend SSD with an Aterhos based PCI wireless card (not using the wireless for general network access).

My initial assesment was that Ubuntu + firefox = unusable.  I would get grey "I'm busy go away" screens that seemed to be associated with disk writes.  I went through the standard disk activity minimization tweeks with no improvment.  In addition the wireless card was not recognized.  I moved to Opera to continue my assesment, but still ran in to frequent grey screens because of disk activity.

On a whim, I decided to upgrade the BIOS (looks like Intel has gotten smart and is distributing their BIOS upgrade as bootable .iso images... nice).  Anyway, that help a little (boot up was faster and certain types of disk access no longer produce grey screens) and my wireless hardware was finally recognized; however, I still get occassional grey screens every couple of minutes when there seems to be a huge block of disk activity (file system journaling?).  Firefox is still pretty much unusable.

My recomendation would be to first upgrade the BIOS, then try some disk access tweeks:  [http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/](http://www.kaobear.com/2008/07/30/reduce-disk-activity-in-ubuntu/) .  If that doesn't get the system usable, then I'd recomend looking at moving away from a journaling filesystem (but I haven't tried that yet as my system is now relatively usable under Opera).

You'd think Intel/Ubuntu would get more involved, but it's obvious that they're not particularly serious about making sure their lower end stuff is super usable.  In 12 to 18 months, these Atom based systems are going to be everywhere...

---

### Post by Saiing on 2008-08-11
Well, I managed to find a supplier that would sell me the Box only, minus the bundled copy of Windows for 50 bucks less, so I ordered one.  Should arrive in the next couple of days.

If I discover anything useful I'll report back.

---

### Post by RedPandaFox on 2008-08-11
Where did you find the supplier and for how much? My supplier can only get them for $500 AUD with Windows and no peripherals. He gets his stuff from multiple suppliers but that's the best he can do. What happened to the announcement of $200-300 eeeBox? :(

---

### Post by Saiing on 2008-08-12
I got it from ebay from a supplier in Taiwan called e-bagel.  Price was US$300.  When I ordered he obviously had a few because he asked me if I wanted a black or white one.  Delivery was prompt.

OK - Progress so far on my Ubuntu Install (copied from a forum post I made on another forum):

Downloaded the standard 8.04.1 iso because I heard that the .1 update has better Intel Atom support to see if it would install 'out of the box' so to speak.

Decided on an external USB CD install since I had a spare drive lying around.  Put CD in drive.  Started EEE Box.  Splashtop came up.  Chose the exit to OS option.  Ubuntu main install menu came up.  Chose install.  My Apple Mac Pro keyboard was detected fine.  It tried to start the graphical installer, failed, black screen.  Finished.

Kicked myself and downloaded the alternate iso with the text based installer.

Ubuntu installed without any issues, ejected the CD, restarted.

Ubuntu startup screen came up with the progress bar, got to 100%, screen went black.  Nothing further.

Rebooted, pulled up the grub boot menu.  Dropped into root shell.  Tried 'startx' - X server wasn't starting properly (which presumably was the reason the graphical installer failed before).

Tried reconfiguring with dpkg-reconfigure xserver-xorg.  Didn't give me many options - just keyboard config really.  No help.

Manually edited xorg.conf - changed the driver setting to vesa.  Tried starting the X server again.  Success!

Shut down the x server, rebooted, Ubuntu started up, login window appeared, logged in, network is running, resolution set automatically at 1600x1200.  Currently downloading system updates.

---

### Post by RedPandaFox on 2008-08-12
Yeah, something I noticed with my eeepc, it may be a coincidence but X always has problems, could it be coincidental or maybe because of such cheep parts?

---

### Post by Saiing on 2008-08-12
Things are working pretty well now.  Set up the standard LAMP configuration, SSH server etc.  I'm running it as a headless server, so I configured the remote desktop and it's working absolutely fine.  Very fast response when I open a VNC window from my Mac.

---

### Post by tuxxy on 2008-08-12
Whcih model is it?

---

### Post by Saiing on 2008-08-12
1 Gig / 80 Gig HD

---

### Post by frankgobbo on 2008-08-14
Thanks for trying this out. I've just bought an eeeBox B202 (black) and although I didn't get any discounts for lack of XP the shop was pretty cheap anyway (in Australia).

I've just downloaded the server CD, alternate so I'm about to have a crack at installing it now (windows on it will never even see teh light of day)

---

### Post by frankgobbo on 2008-08-14
Is there anything special you did to get it boot off USB?

I'm trying with a USB drive (Sandisk Cruzer) and I've tried creating the bootable USB device several different ways with no luck. I've taken the HD out of the boot menu options so it only tries the USB device and still no luck.. so I suspect there's something wrong with my USB, just wondering if there's a trick.

Thanks!

PS, is there a way to PXE boot the eee box? It'd be just as easy for me to kickstart a network install.. if not easier.

---

### Post by sandlidl on 2008-08-14
I just got mine yesterday and I'm going to try out billix. From what I've read, (in Linux Journal) it's a nice pendrive utility loaded with NetInstall for Ubuntu (among others). Pop in the pendrive, boot up and it initiates a netinstall.

sourceforge.net/projects/billix

Any other ideas?

---

### Post by RedPandaFox on 2008-08-14
> **frankgobbo said:**
> Is there anything special you did to get it boot off USB?

I'm trying with a USB drive (Sandisk Cruzer) and I've tried creating the bootable USB device several different ways with no luck. I've taken the HD out of the boot menu options so it only tries the USB device and still no luck.. so I suspect there's something wrong with my USB, just wondering if there's a trick.

Thanks!

PS, is there a way to PXE boot the eee box? It'd be just as easy for me to kickstart a network install.. if not easier.

On the EeePC's you had to press Esc to choose bootable media such as, internal, card reader or external drive. Try Esc when first booting, failing that, mash keypad to get it to work? :P

Also you said you got it in Aus? Where from and what did it cost you? I'm looking at one near me, but I suspect the dealer is not giving me the best deal.

---

### Post by frankgobbo on 2008-08-14
I couldn't be bothered toying with the bootable USB anymore, and I remembered I have an old external HD/USB enclosure thing with an IDE port.. 2 minutes later, I had an external USB cdrom drive. Worked a treat, I've now got Ubuntu Server 8.04.1 (alternate) installed and running like a charm. Worked straight out of the box.

It's pretty nippy, too. 

I don't remember the name of the shop I got it from, I'm in Melbourne, it's next door to Digiworld in La Trobe St. I paid $449 but if you look at shopbot.com.au and search for b202 you can find cheaper.

Also, [www.pccasegear.com](www.pccasegear.com) has it available for $10 shipping (courier, Melbourne wide or I think $12 interstate or store pickup from Oakleigh) and I think $419 but I'm *really* impatient and I wanted it immediately ;)

---

### Post by RedPandaFox on 2008-08-14
I'm not overly familiar with Melbourne, I'm a country bumpkin from Albury Wodonda area :P
I know MSI and that 'bout it in Melbourne, isn't that in the area you are referring to?

---

### Post by eric_octopus on 2008-08-16
Hey guys,

I've installed 8.04.1 on my Eee Box, and after some pain I have successfully got my wireless working, but I cannot for the life of me figure out how to get the video to work correctly. The only way I get X to boot is by editing xorg.conf to use the VESA driver, but when I do this there does not seem to be any way to use a resolution higher than 1280 x 1024, and no widescreen resolutions (I'm trying to get 1600 x 1050). 

The chipset is Intel 950 supposedly, but I've tried looking up everything and I can't figure out why it isn't working. I've been playing around with xorg.conf driver settings to see if I can have any luck, but nothing but VESA displays anything at all. I'd really appreciate any ideas, especially if other people have gotten this to work. I bet I'm not the only person who has come up against this problem.

Thanks!

---

### Post by sandlidl on 2008-08-17
Yes, I'm having the same problems. I can't figure out anything about the wireless (is it an RT** driver???) and google hasn't helped me out a lot this time.

As for Vesa, I set the display to be larger, but the best I can get is 1024x768.

---

### Post by xadder on 2008-08-18
Hi everyone,

Just curious, some people are installing ubuntu instead of the xandros on these Asus boxes. I have no experience with Xandros, but it is a debian system, and hence upgradable/changable.  Apart from the fun of it, why go to the trouble of installing Ubuntu?

(I have Ubuntu on all machines I work with, and love it,  but I also have a busy life so wouldn't mind just keeping a pre-installed as long as I can do dist-upgrade in future.)

---

### Post by eric_octopus on 2008-08-18
> **xadder said:**
> Hi everyone,

Just curious, some people are installing ubuntu instead of the xandros on these Asus boxes. I have no experience with Xandros, but it is a debian system, and hence upgradable/changable.  Apart from the fun of it, why go to the trouble of installing Ubuntu?

(I have Ubuntu on all machines I work with, and love it,  but I also have a busy life so wouldn't mind just keeping a pre-installed as long as I can do dist-upgrade in future.)

Unlike Eee PC's, the Eee Box comes with XP only, no version of Xandros.

---

### Post by xadder on 2008-08-18
Ah, I assumed the word "Box" was being used loosely. It is the Eee PCs I am interested in, probably the 901 when it gets here (Sweden).

---

### Post by Saiing on 2008-08-18
> **eric_octopus said:**
> Hey guys,

I've installed 8.04.1 on my Eee Box, and after some pain I have successfully got my wireless working, but I cannot for the life of me figure out how to get the video to work correctly. The only way I get X to boot is by editing xorg.conf to use the VESA driver, but when I do this there does not seem to be any way to use a resolution higher than 1280 x 1024, and no widescreen resolutions (I'm trying to get 1600 x 1050). 

The chipset is Intel 950 supposedly, but I've tried looking up everything and I can't figure out why it isn't working. I've been playing around with xorg.conf driver settings to see if I can have any luck, but nothing but VESA displays anything at all. I'd really appreciate any ideas, especially if other people have gotten this to work. I bet I'm not the only person who has come up against this problem.

Thanks!

Have you tried adding the following in the Device section of xorg.conf?:

Option          "NoDDCValue"    "True"

This will cause it to bypass monitor detection, and you can define your own refresh rates and resolution in the same file.  I admit to not being much of an expert on this, but if you google around you might find a little more guidance on this.  Although I've never seen it happen, I've read numerous warnings over the years saying that running wrong refresh rates can damage your hardware, so be wary.

---

### Post by eric_octopus on 2008-08-19
> **Saiing said:**
> Have you tried adding the following in the Device section of xorg.conf?:

Option          "NoDDCValue"    "True"

This will cause it to bypass monitor detection, and you can define your own refresh rates and resolution in the same file.  I admit to not being much of an expert on this, but if you google around you might find a little more guidance on this.  Although I've never seen it happen, I've read numerous warnings over the years saying that running wrong refresh rates can damage your hardware, so be wary.

Still no luck, though I appreciate the help. I still get the same options in the Screen Resolution applet. And any attempt to use the intel graphics driver causes my monitor to detect no input and go to sleep. Is it possible my monitor is the problem? I have an HP w2207h.

Has anyone gotten their Eee Box set up successfully? Right now it's usable but I really wish I could get everything working perfectly.

---

### Post by ulinuxgeek777 on 2008-08-20
> **eric_octopus said:**
> Still no luck, though I appreciate the help. I still get the same options in the Screen Resolution applet. And any attempt to use the intel graphics driver causes my monitor to detect no input and go to sleep. Is it possible my monitor is the problem? I have an HP w2207h.

Has anyone gotten their Eee Box set up successfully? Right now it's usable but I really wish I could get everything working perfectly.
I think this will help you:

[http://forum.eeeuser.com/viewtopic.php?pid=348575#p348575]("http://forum.eeeuser.com/viewtopic.php?pid=348575#p348575")

Your Welcome

---

### Post by Paul_K on 2008-08-25
I got the wireless in my 901 working (as well as most everything else) here:

[http://www.ubuntu-eee.com/index.php5?title=EeePC_901](http://www.ubuntu-eee.com/index.php5?title=EeePC_901)

Here is a good link to how to boot off thumbdrive:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Worked for me.  I hope this helps.

-PaulK

---

### Post by motang on 2008-08-26
> **sandlidl said:**
> I just got mine yesterday and I'm going to try out billix. From what I've read, (in Linux Journal) it's a nice pendrive utility loaded with NetInstall for Ubuntu (among others). Pop in the pendrive, boot up and it initiates a netinstall.

sourceforge.net/projects/billix

Any other ideas?
Try this [article]("http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/") it very good and worked for me Ubuntu and Kubuntu. So I will installing Kubuntu 8.10 on my new Eee Box when I get in (ordered it yesterday, can't wait).

---

### Post by Caysho on 2008-08-28
> **eric_octopus said:**
> Hey guys,

I've installed 8.04.1 on my Eee Box, and after some pain I have successfully got my wireless working, but I cannot for the life of me figure out how to get the video to work correctly. The only way I get X to boot is by editing xorg.conf to use the VESA driver, but when I do this there does not seem to be any way to use a resolution higher than 1280 x 1024, and no widescreen resolutions (I'm trying to get 1600 x 1050). 

The chipset is Intel 950 supposedly, but I've tried looking up everything and I can't figure out why it isn't working. I've been playing around with xorg.conf driver settings to see if I can have any luck, but nothing but VESA displays anything at all. I'd really appreciate any ideas, especially if other people have gotten this to work. I bet I'm not the only person who has come up against this problem.

Thanks!

There is a [display issue with dual pipeline usage](http://forum.eeeuser.com/viewtopic.php?id=39698) - one pipe is for the nonexistant laptop LCD screen, the other is for the DVI out.
I have it working for SXGA (1280x1024) on a Philips LCD monitor using the intel driver:
```

(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so

```

I had no problem with the screen going into standby for the default install.  I figure that once you use the intel driver you should be able to use higher resolutions and/or widescreen, video memory permitting.

```

(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output TMDS-1 using initial mode 1280x1024
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.

```

An aside: [1680x1050 hack](http://forum.eeeuser.com/viewtopic.php?pid=356440).
Looks like 3-4 steps of tweaking needed.

---

### Post by vmsgman on 2008-10-10
I cannot get the sound to work properly. I am new to Ubuntu. Have installed 8.10 alpha 6. Anyone have any suggestions. Am I in the right thread?

---

### Post by frankgobbo on 2008-10-14
> **Paul_K said:**
> 
Here is a good link to how to boot off thumbdrive:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Worked for me.  I hope this helps.

-PaulK

This was the part I had by far the most difficulty with. In the end I had to use a USB CDROM drive.

Thanks for the info, it'll definitely help next time I have to rebuild it!

---

### Post by nolihc on 2008-10-18
I have problems with playing movies on the eee box after a couple of minutes the screen gets black but the sound is still there. 

ctrl-alt-backspace opens login screen which remains black. It happens with all movie players. vlc, mediaplayer, xbmc, boxee, miro.

An activated screensaver makes the screen go white instead of black.

Anyone?

---

### Post by trapperjohn on 2008-12-24
Old thread but matches best:

My tipps for Eee Box B202 and Ubuntu 8.10:

The "netinstall" version provided by UNetBootin (for creating the USB stick) did not work for me, grub and/or kernel installation failed and the installed system didn't boot.

8.10 Desktop version installed flawlessly from USB (also created by UNetbootin).

My Eee Box didn't power-down at the end of the shutdown sequence. I had to add ```
acpi=force lapic
``` to the "defoptions" in /boot/grub/menu.lst

WLAN works very good using ndiswrapper, Windows drivers are on the CD. I didn't try the native drivers.

Some seconds after starting a video, the screen turns black and cannot be reactivated. After some googling I could fix this problem by adding the following line to the "device" section of xorg.conf:
```
Option "FramebufferCompression" "off"
```

The Intel video driver hast two "adapters", one for "texturing" and one for "overlay". By default, the first is used for everything - this results in ["screen tearing"](http://en.wikipedia.org/wiki/Page_tearing) when watching videos which looks really bad. 
Using "xvinfo" you can detect the port of the overlay adapter ("port base"). My Eee box says, the overlay's port base is at 91.
For example mplayer can use the overlay adapter:
```
mplayer -vo xv:port=91 videofile.mpg
```
-> no tearing!

Most h264-encoded 720p videos are too much for the Eee-out-of-the-box, it's laggy, choppy, slow, whatever ...
But it is possible to use the famous Windows-only "CoreAVC" codecs with mplayer:
[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)
Note: Before building mplayer, I had to upgrade the x264 package to a current development snapshot!

I tried this using a CoreAVC trial version and I'm amazed how smooth h264 videos now run on the Eee box (of course without anything else running in the background ...). The 15$ for CoreAVC are a really good investment!

Merry Christmas!

Florian

---

### Post by trapperjohn on 2009-05-04
Okay, I made an update to Jaunty and had a lot of video problems. 

After hours of recompiling mplayer, recompiling dshowserver (for core avc), upgrading intel driver, downgrading intel driver and so on and so on ... I finally found this:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

The mentioned "MTRR" bugfix solved the problems for me. Now smooth video is back :guitar:

By the way: Did someone already try 2.6.30 with KMS and a new Intel driver? Phoronix benchmarks look as if it will bring a good performance boost ...

---

### Post by usbargains on 2009-08-21
I have wrote an article to summarize what I did to convert Windows-based EEE BOX to Ubuntu server. It is fantastic to have this ubuntu server. Follow the link to find details.

[http://www.sunfinedata.com/handson/install-ubuntu-server-to-eee-box/](http://www.sunfinedata.com/handson/install-ubuntu-server-to-eee-box/)

For some reason, you can recover your Windows OS late on your EEE BOX, follow the link to read detail

[http://www.sunfinedata.com/handson/restore-windows-on-eee-box-without-cddvd-drive-boot-from-usb-falsh-drive/](http://www.sunfinedata.com/handson/restore-windows-on-eee-box-without-cddvd-drive-boot-from-usb-falsh-drive/)

---

### Post by PhilMize on 2009-09-17
> Brand  	ASUS
Series 	Eee Box
Model 	EB1006-B-111-5002
Recommended Usage 	Home / Home Office
Colors 	Black
Processor 	Intel Atom N270(1.6GHz)
Cache Per Processor 	512KB L2 Cache
Memory 	1GB DDR2
Hard Drive 	160GB 5400rpm
Graphics 	ATI Radeon HD 4530, 256MB DDRII
Audio 	Sound card - Integrated
Ethernet 	10/100/1000 Mbps
Wireless Card 	802.11 b/g/n Wireless LAN
Power Supply 	36W
Keyboard 	Wireless KeyBoard
Mouse 	Wireless Mouse
Operating System 	Windows XP Home
Special Features 	Energy Star: 5.0 Compliant

Source: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883220014](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220014)

I'm looking at purchasing one of these to use as a boxee media center pc. My only concern is the ATI card on it. I know ati is not very linux friendly. So has anyone else had experience with theses? Pros cons? I'll prob be using UNR on it with boxee installed.

---

### Post by carnedv on 2009-10-15
> **PhilMize said:**
> Source: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883220014](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220014)

I'm looking at purchasing one of these to use as a boxee media center pc. My only concern is the ATI card on it. I know ati is not very linux friendly. So has anyone else had experience with theses? Pros cons? I'll prob be using UNR on it with boxee installed.

I bought this model to replace the previous model (with the integrated Intel video) of the EEE Box that I lost in a power failure this last weekend. Last night I installed 9.04 Live Descktop via USB key and was pleasantly surprised that it picked up and configured the ATI @ full 1920 x 1080 automatically. I was sure it was going to be a fight. On the whole this install was a lot easier than the previous model when it came to video. I had to do a lot of extra configuring to get the full resolution out of the previous one.

This new model is a screamer compared to my old one, and the HDMI is gorgeous on the 52" tv. Intsalling HULU desktop tonight to give video a whirl.

---

### Post by PhilMize on 2009-11-03
sweet i just bought one from newegg thanx!

---

