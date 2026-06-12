---
title: "Dell Studio XPS 13"
date: 2009-05-26
forum: Hardware
---

### Post by Knowle on 2009-05-26
I was thinking about getting this laptop but I was comparing it against the same model that comes with Windows pre-installed. Think I would have any problems getting the one with Windows then install Ubuntu(jaunty, this one comes with 8.10) over it and use the Vista product key in virtualbox? The only difference/problem I see in hardware is the wireless card. Any opinions on the battery life and how much noise it makes or any heat issues?
[http://www.dell.com/content/products/productdetails.aspx/laptop-studio-xps-13?c=us&cs=19&l=en&s=dhs&~ck=mn](http://www.dell.com/content/products/productdetails.aspx/laptop-studio-xps-13?c=us&cs=19&l=en&s=dhs&~ck=mn)

Windows pre-installed
Dell Wireless 1510 802.11n Half Mini-Card

Ubuntu pre-installed
Dell Wireless 1397 802.11a/g Half Mini-Card

It comes with the 13.3" HD WXGA LCD, what's the difference in screen quality if I upgrade it to the 13.3" HD WXGA Slim WLED LCD? Any opinion on doing this same setup on a Studio 15? Sorry I've never had a laptop and the desktop I have is 6 years old. >_>

---

### Post by Knowle on 2009-05-27
bump  :[

---

### Post by SQuark on 2009-05-29
The Studio XPS 13 tends to get quite hot. Be sure to do a BIOS upgrade, as this does help a bit. But it's still hotter than say the XPS M1330.

The WLED screen is brighter, slimmer, weighs less and consumes less energy, so it's definitely an upgrade you'll want to consider.

Where I live, Dell doesn't give the choice of a pre-installed Ubuntu, so I got the 1510 802.11n Half Mini-Card. All I can tell you so far is that it doesn't work out of the box on a fresh Jaunty install. And 'Hardware Drivers' finds nothing. In fact, searching for that is how I stumbled upon your post. :)
Since Dell chose the 1397 802.11a/g Half Mini-Card for the version with Ubuntu pre-installed, it may be easier to get that one to work. (Just speculating here, no guarantees.)

I got the NVIDIA® GeForce® 9500M and had to install a beta driver from the Nvidia site, because the older drivers that were suggested by 'Hardware Drivers' had some irritating bugs. (Here's a good How To for that: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400))
But maybe the NVIDIA® GeForce® 9400M G does not have these issues.

Note that, as far as I know, you can't profit from the battery saving Hybrid SLI technology in Linux (yet?).


Some cons you should be aware of before buying:
[LIST]
[*]as I said, it can get relatively hot
[*]it's a magnet for fingerprints
[*]I have a tiny speck of dust in my screen and --browsing the Dell forums-- I'm not the only one
[/LIST]

If you can live with minor issues like that, it's definitely a commendable laptop.

---

### Post by SQuark on 2009-05-29
All right, forget what I said about the wireless card. It does work out of the box on Ubuntu. It's just that the hardware switch only toggles bluetooth. So I had to boot into Vista to turn on my wireless and then boot back into Ubuntu and now everything's working fine. :)

---

### Post by Knowle on 2009-05-30
Yeah, I started reading the comments/customer ratings for it. I'm real scared about having any heat issues. I don't want it to cook itself. :[ Most people said as you also suggested, a BIOS update. It looks like besides that, the main issue is the design itself as from what I was reading if you tilt the screen past a 90 degree angle it will block the vent in the back which of course leads to more heat issues. >:/


The Inspiron 15n looks pretty cool, but the specs on it are lower. >_>

[http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-1545?c=us&l=en&s=dhs&cs=19&~oid=us~en~29~linux_2~~](http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-1545?c=us&l=en&s=dhs&cs=19&~oid=us~en~29~linux_2~~)

---

### Post by ozzyprv on 2009-06-08
My Studio XPS 1340 is working fine so far.
Not as hot as I thought from reading all the comments/reviews. Maybe it gets hotter when running Vista?

I got it with the WLED screen, it is nice.

O.

---

### Post by lessfield on 2009-06-08
I've had this for ~a week. Works nice, not too hot. LED screen and solid-state drive are good upgrades. Got vista pre-installed 
with the BroadComm N card and nVidia 9500 GPU. 

BroadComm has worked out of the box w/ 9.04 64bit, 
Deleted the Dell recovery partition and shrunk vista down to a 40 gigs

nVidia 9500 GPU works OK with the current nVidia pre-release 185.18.14. Dual monitors work fine in TwinView mode. I can't drop to a root console w/o seeing flashing black and white vertical bars. **[Correction: I can drop to tty2 ctrl+alt+f2]** Also, sometimes the lappy's screen dims unexpectedly and need to be brought back w/ the hard-coded brightness key. (Does this in windows too). 


Overall I'm happy with this my purchase  and as the driver development continues to progress (fingers crossed) it should become rock solid.

Has anybody used the display port connector on this laptop yet?

---

### Post by ozzyprv on 2009-06-08
> **lessfield said:**
> 
Has anybody used the display port connector on this laptop yet?

No, not yet.

Did you nVidia driver installed ok? If so it must be the fact that I installed the server kernel why I had to do some extra work.

---

### Post by lessfield on 2009-06-09
> 
Did you nVidia driver installed ok? 

the install was smooth. No problems. with most recent pre-release

---

### Post by matrio on 2009-06-10
Someone has managed to do a bios upgrade of the 1340 under ubuntu?

---

### Post by ozzyprv on 2009-06-11
Has anybody tried the integrated webcam? If so, how (program)?

---

### Post by ozzyprv on 2009-06-11
In case you are having problems with the Network Manager, I removed and installed Wicd. Much better.

---

### Post by SQuark on 2009-06-12
> **ozzyprv said:**
> Has anybody tried the integrated webcam? If so, how (program)?

Works out of the box with Cheese, Skype and aMSN.

---

### Post by Demoraliser on 2009-06-13
> **matrio said:**
> Someone has managed to do a bios upgrade of the 1340 under ubuntu?

i just got my M1340 a few days ago. It had the A02 bios, i upgraded the to the A07 version available on the dell site. Before the upgrade the bios would not pick up the HDD at boot, i would have to Ctrl-Alt-Del to before the drive was picked up. The bios upgrade fixed this.

Running Win7 and Jaunty... both are pretty smooth.

---

### Post by ozzyprv on 2009-06-13
Was I the only one with problem with Network Manager (wired network not being managed)?

Now, Wicd is not reconnecting automatically.

---

### Post by SQuark on 2009-06-22
I just wanted to mention that with the new kernel version the wireless/bluetooth switch now works correctly!

---

### Post by ozzyprv on 2009-06-24
Could somebody post the audio setting to get Skype to work properly?

I am kind of confused with all the available options:
>Volume control at panel > Preferences
>Volume control at panel > Open Volume Control> Device
>System > Sounds

Thank you.

---

### Post by lessfield on 2009-06-25
> Could somebody post the audio setting to get Skype to work properly?


Sound In: HDA Nvidia (hw:NVidia,0)
Sound Out: HDA Nvidia (hw:NVidia,0)
Ringing: HDA Nvidia (hw:NVidia,0)


wrt the volume control Digital Input Source in the options tab is selected for the Mic you are using. Digitial Mic 1 For the built-in mic, and Analog Input if you are using a headset.

Also, w/ the built-in mic Mic Mixer and Capture have to be turned up rather high, and the built-in mic only works on one channel.

---

### Post by ozzyprv on 2009-06-27
> **lessfield said:**
> Sound In: HDA Nvidia (hw:NVidia,0)
Sound Out: HDA Nvidia (hw:NVidia,0)
Ringing: HDA Nvidia (hw:NVidia,0)


wrt the volume control Digital Input Source in the options tab is selected for the Mic you are using. Digitial Mic 1 For the built-in mic, and Analog Input if you are using a headset.

Also, w/ the built-in mic Mic Mixer and Capture have to be turned up rather high, and the built-in mic only works on one channel.


Thank you. It worked, it is just a bit slow (audio).

---

### Post by PhilMize on 2009-07-04
I just bought one from Dell with ubuntu 8.10 preinstalled... comes in on the 20th, should be interesting!

---

### Post by ozzyprv on 2009-07-06
> **PhilMize said:**
> I just bought one from Dell with ubuntu 8.10 preinstalled... comes in on the 20th, should be interesting!

Let us know how it goes!

Cheers.

---

### Post by HarrisonNapper on 2009-07-14
Is there anyone else here who has constant crashing? I'm on a 1340, running x386 Jaunty and I've installed the proprietary nVidia driver, so I'm not sure what's going on. Aside from crashing about once an hour (I'm not even kidding), if I can manage to put it in to hibernate or sleep, it won't come back on. Also, it crashes a lot during shutdown and restart.

---

### Post by ozzyprv on 2009-07-14
> **HarrisonNapper said:**
> Is there anyone else here who has constant crashing? I'm on a 1340, running x386 Jaunty and I've installed the proprietary nVidia driver, so I'm not sure what's going on. Aside from crashing about once an hour (I'm not even kidding), if I can manage to put it in to hibernate or sleep, it won't come back on. Also, it crashes a lot during shutdown and restart.

Please define crashing.

Does the laptop just restarts itself?

---

### Post by HarrisonNapper on 2009-07-14
> **ozzyprv said:**
> Please define crashing.
 
Does the laptop just restarts itself?
 
Negative, ghost rider. The screen goes blank (the monitor's still on) and it just sits there forever. No mouse, no nothing. The caps lock key doesn't light up when pressed. I've managed to get a dump on it before and gotten some different error messages like: CPU#1 stuck for 61s, failed to initialize btusb, and another one I can't remember. The second message is when it crashes on the way back from a sleep or hibernate session, whereas the first was, if I recall, a problem with X initializing, but I fixed that.
 
I'm doing a new install (I'm dual booting again--I was 100% ubuntu before) of Ubuntu Studio 9.04 amd64 with the ethernet plugged in, so if it stops crashing, I'll definitely post that.

---

### Post by HarrisonNapper on 2009-07-14
Actually, I should correct that; it usually just freezes, so if it happens to be blank, it stays blank. Usually, though, it's not blank.
 
Just re-installed and I'm getting the same issue.

---

### Post by ozzyprv on 2009-07-14
> **HarrisonNapper said:**
> Actually, I should correct that; it usually just freezes, so if it happens to be blank, it stays blank. Usually, though, it's not blank.
 
Just re-installed and I'm getting the same issue.

I know that probably what you want are answers instead of more questions, but...

Why are you installing amd64 version? I did a fresh install of 9.04 server version. I installed the server version to get the full 4 GB of RAM recognised. Besides the nVidia driver, everything (including stability) was/is excellent.

Have you tried pressing ctrl+Alt+F1 when it freezes? You will probably get some more info by doing that. It was useful to me when troubleshooting some issues I have had.

---

### Post by HarrisonNapper on 2009-07-15
Yeah, it won't let me switch to any tty, as the keyboard locks up. After this memtest, I'll install Jaunty server and just do the studio upgrade. Did you install 64 bit server? I don't know how x386 server compares with amd64 for multimedia type stuff.

---

### Post by lessfield on 2009-07-15
Why are you installing the server version? 64bit desktop should work just fine wrt to the >4gigs ram

---

### Post by ozzyprv on 2009-07-16
> **HarrisonNapper said:**
> Did you install 64 bit server? I don't know how x386 server compares with amd64 for multimedia type stuff.

I installed the x386 server version. I needed to. I use a Citrix application that does not like amd64 versions.
Same as Harri said, I then installed the desktop portion.

Hope this method works well for you.

---

### Post by HarrisonNapper on 2009-07-16
Okay, I got everything pretty much working. I have to run synaptic through the terminal, my add/remove app doesn't work (it closes right after it loads) and there's tons of other stuff going on, BUT my wireless works and it's not crashing every two seconds. So, on the whole, I would consider it a victory. Also, I read that the computer not being able to wake from hibernate was a known issue (the bios and the GPU don't get along 100%).
 
I just use Faildoze for day-to-day stuff and then Ubuntu Studio for production, anyway.
 
Another win for Monoposoft.

---

### Post by HarrisonNapper on 2009-07-16
> **HarrisonNapper said:**
> So, on the whole, I would consider it a victory.
 
Fragment. Consider Revising.

---

### Post by ozzyprv on 2009-07-16
> **HarrisonNapper said:**
> 
 
Another win for Monoposoft.

Disappointing.

All I can say is that if you and me have the same laptop (initially it looks like) there is a way to get the server version installed and runing with no problems.
I am neither an Ubuntu nor Linux expert. If I can get it to work, anybody can.

Let me know if you want me to tell you what I did, step by step.

---

### Post by HarrisonNapper on 2009-07-17
> **ozzyprv said:**
> Disappointing.

All I can say is that if you and me have the same laptop (initially it looks like) there is a way to get the server version installed and runing with no problems.
I am neither an Ubuntu nor Linux expert. If I can get it to work, anybody can.

Let me know if you want me to tell you what I did, step by step.

Yeah, running server is a good idea. I may still do that, but since I have a decent desktop version going, I'll stick with that for awhile. Thanks for the offer, though; I'll pm you if I am given cause to follow up.

---

### Post by calle#52 on 2009-07-28
If anyone is interested... :)
Tried this iso from Dell with my new Studio XPS 13: [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)

Seems to work fine. Only tested for 1 day ;)  

Known issues:
- The laptop gets hot at times (need to upgrade BIOS according to other posts)
- The wireless card doesn't accept DHCP. Need to asign static IP. Haven't tried suggested fix ([http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441))
- Not able to configure my norwegian keyboard correctly (some keys are not according to layout)

Specs on my Studio XPS 13:
- Core 2 Duo P9600
- 4 GB RAM, 1067 MHz DDR3
- 13.3 WXGA white LED
- HDD: 500 GB 7200rpm
- Dell wireless 1515 Half mini card
- Dell bluetooth 370 card

---

### Post by ozzyprv on 2009-07-29
Keep us posted.
My wireless card worked fine with dynamic DHCP.

But I think we have different cards.

```
me@mybox:~$ lspci | grep Wireless
06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```

---

### Post by jezjones on 2009-07-31
Hi All,

I was looking at this thread to see if there is any progress on the hybrid sli graphics as to be honest this laptop is wasted with such basic graphics.

But, i have now found that i have only got 2gb of my 4gb of RAM being picked up.

This seems like a major problem to me. Does desktop editions of linux not recognise 4 gb of ram... is it still 1998? 

I love linux and have been working with Debian for a number of years, and ubuntu was originally Debian without the headaches, but this laptop is fairly crippled with a default install.

Here is my list of bugs;-

1) Wifi - poor signal strength i.e. need to be on top of an access point for access.
2) hardware keys only work intermittently i.e. volume, cd eject etc.
3) Over heating, my laptop gets VERY hot (just downloading the bios update now).
4) Battery life, without hybrid SLI i just about get 2 hours, and this laptop is brand new.
5) Only 2 gb of ram being recognised.
6) Sound needed to be reconfigured to get it to work.

Honestly i am considering ditching this laptop, putting it on ebay and getting something that will run linux properly.
Graphics are important these days and if you take a look at Vista, win7, OSX (leopard) then you see a clean sharp interface... this high spec dell studio 13 looks pretty poor with ubuntu's brown and no 3d acceleration.

I am not going to put the 64bit version on here as there is little 64 support in the desktop linux world (my last laptop was 64bit and i ended up running so much in a chroot env that it seemed pointless to have 64bit).

So... we'll see how i get my other 2 gb of ram going... :confused:

---

### Post by lessfield on 2009-08-01
> 1) Wifi - poor signal strength i.e. need to be on top of an access point for access.
Yep, but only in  WPA mode. I have broadcom 4322 card which is not fully supported by linux-wireless and the broadcom driver is still crap. When I need to connected to WPA I use a  usb wireless dongle. 

> 2) hardware keys only work intermittently i.e. volume, cd eject etc.

When that happens to me the way i get it to work is to briefly(seconds) put the lappy into suspend. This re-initialize the hardware buttons and then everything works again. 

> 3) Over heating, my laptop gets VERY hot (just downloading the bios update now).
Bios update help, but I've noticed achpi goes resource hungry when the touch buttons aren't picked correctly. Again a quick suspend always solves this problem for me. 

> 4) Battery life, without hybrid SLI i just about get 2 hours, and this laptop is brand new.
This lappy isn't a netbook. I'd say even with a fully supported hybrid SLI ~2 hours is going to be par for the course with the standard battery.

> 5) Only 2 gb of ram being recognize.
6) Sound needed to be reconfigured to get it to work.

You should go 64bit; unless you have a specific app-concern. 
Sound works out of the box w/ 9.04. 
Also, no problems with the ram (i've got 4 gigs  doing work right now).  
I use 64 bit as my daily driver, and haven't run into any roadblock. Flash 10, skype, matlab, sun-java all work fine. In fact, matlab runs so much better on 64bit it blows my mind.:smile: 
I also run an intensive Compiz setup w/ no problems. Compiz benchmark under load only drops to ~ 70 frames/sec, and idles ~ 260 frames/sec

---

### Post by SQuark on 2009-08-02
Install the packages linux-headers-server, linux-image-server and linux-server, reboot, and your extra RAM will be picked up.

---

### Post by jezjones on 2009-08-17
> 
This lappy isn't a netbook. I'd say even with a fully supported hybrid SLI ~2 hours is going to be par for the course with the standard battery.

You should go 64bit; unless you have a specific app-concern. 
Sound works out of the box w/ 9.04. 
Also, no problems with the ram (i've got 4 gigs  doing work right now).  
I use 64 bit as my daily driver, and haven't run into any roadblock. 

I know its not a netbook, but my last machine ran on a standard battery for approx 4 hours from new, as does any thinkpad T60+ 

I have upgraded the BIOS and it runs slightly cooler, but still not cool enough to use on your lap.. table only if you dont want sweaty legs!

Also 64bit, nope, i had too much of a hassle when i was trying to run that previously on a HP laptop... i had to put firefox in a sandbox, flash took about 2 years to become available for 64 bit, so don't hold your breath for any new version anytime soon.
I have no specific app concern, but it is just not as well supported and there was always a 64 bit issue with some stuff like video.

Its interesting that you mention compiz as that does not appear to work on this machine in any way. It complains about unsupported graphics cards due to the SLI stuff (has two but cant pin down which one to use).

I appreciate linux is always playing catch up, but i am not particularly impressed with this machine, it is likely to be my last Dell at any rate.

Also i have upgraded to server version to get my extra ram and Picassa no longer can import from my camera - it sees it as a device and recognises it, but then does not see any pictures (and it is on the supported list).

No, high end machines like this are not an area that linux has really got into yet, sadly.

---

### Post by ozzyprv on 2009-08-17
> **jezjones said:**
> 
Its interesting that you mention compiz as that does not appear to work on this machine in any way. It complains about unsupported graphics cards due to the SLI stuff (has two but cant pin down which one to use).


I have Compiz working with no problem in this machine. Let me know if you need to know what I did. Nothing complicated.

O.

---

### Post by balud on 2009-08-18
hi
I just got my dell xps studio 13, read this thread, installed jaunty x86 (dualboot with vista), then installed server kernel on top, everything seems to be working fine. compiz, bluetooth, wireless, 4gb of memory recognised, could play extreme tux racer without loading on cpu (as was with dell precision m60+ubuntu 8.04).
Just one issue! the desktop hangs once in a while. no patterns. keyboard stuck so can't jump to terminal. strangely mouse works and hard disk is alive/working (since i was copying files from remote machine and it didn't stop)!
I don't like to hard reboot, of course! any ideas?

---

### Post by HangLoose on 2009-08-19
I am thinking in buying this laptop and would like to get some input from you guys (since you are using it for quite some time).

This is the configuration I want:
> Studio XPS 13 : Intel Core 2 Duo Processor P8600 (2.40GHz,1066MHz,3MB)
Display : Black Leather 13.3in WXGA (1280x800) CCFL Display with TrueLife
Camera : Integrated 2.0 Mega Pixel Camera with Facial 
Memory : 4096MB (2x2048) 1067MHz DDR3 Dual Channel
Hard Drive: 320GB Free Fall Sensor (7200RPM)
Graphics : 256MB nVidia 9500m graphics card
Wireless Label (Dell Wireless Cards)- Core 2 Duo
Wireless : Europe Dell Bluetooth 370 Card
Wireless : Dell Wireless 1397 (802.11 b/g) Mini Card European
Dell Dock 1.0
1Yr Premium Warranty Support


I am also thinking about the Dell Studio 15.

I will use the machine mainly to develop so I am kinda afraid it being very small. I saw some people saying something about buying a second monitor (which is a good idea) but if I am on a train I will look weird carrying it around. :P

Should I take the 2.60Ghz with 6mb of cache? Or increase RAM? Or warranty? 

Are there any problems related to it? Incompatibility with 64bit or incorrect drivers for camera, bluetooth and so on?

Thanks a lot

---

### Post by balud on 2009-08-20
i think you can go for that config! everything works for me - bluetooth, webcam, mic, sound, wireless. as said in this thread earlier, you will need to install server kernel to see the full memory. i would go for 3 years warranty. go for the wled screen. and yes the screen size is small particularly when i was used to 1900x1440 in my earlier precision m60. got to scroll down a lot to see all my folders in thunderbird. but as for the performance i would say this one is pretty good.
after one more day of usage, i think it is the graphics config which is causing the desktop to hang. when the battery reached 6% some compiz configs (cube) got disabled by itself and threw all the windows from different workspaces into one. i just let it be and went on and it didn't hang so far.
let's see how it goes!

---

### Post by HangLoose on 2009-08-20
Thanks for the help. 

I was already thinking about bumping up the warranty (since its a pricey machine) and also updating the screen...

But the thing that I am worried the most is this heating issues.
[http://en.community.dell.com/forums/p/19261589/19440603.aspx](http://en.community.dell.com/forums/p/19261589/19440603.aspx)

It seems that a LOT of people had this problem. Some people even in their 3 laptops and issues about hanging and freezing still happening. 

Anyone with the same issues either in linux or windows?

---

### Post by balud on 2009-08-21
My bios version is A07 well it heats up, true but not to the extent to call it overheating.

---

### Post by HangLoose on 2009-08-21
I see.. 

How hot can it get while doing some heavy work (like running tomcat, eclipse, browser, db) and also just normal usage like running firefox and pidgin? 

I am so concerned cos I still want to have kids you know? :P

Is it possible to use gkrellm and i8kutils to control the fans?

---

### Post by ozzyprv on 2009-08-24
As balud said, go for it. It is the first Dell I own, and so far I am happy. I did not get the extended warranty, I never do for any electronic....an old habit.

The heating issue has not been a problem for me at all. It is cooler than my previous laptop (HP dv9005). 

The screen size is a bit small, same as balud, my desktop has a 1400x900 res. But it is the price I paid for a light powerful machine.

O.

---

### Post by balud on 2009-08-25
i didn't see any major difference in heating while playing urban terror+thunderbird+firefox+few terminals as against using regular thunderbird+firefox+pidgin+few terminals.

---

### Post by balud on 2009-08-25
sorry, i haven't checked about gkrellm and i8kutils so far. may be someone else more knowledgeable can say!
but to continue on my earlier issue of desktop hanging, i figured out it was compiz segfaulting.
[ 6902.609970] NVRM: Xid (0003:00): 13, 0003 00000000 00008397 000015e0 00000000 00000040
[ 6919.480135] compiz.real[3573]: segfault at 1c ip b72fe674 sp bf855bf4 error 6 in libGLcore.so.180.44[b6be0000+d1a000]
so i am running without 'advanced desktop effects' for a day now and faced no issues either with AC power on or on battery!

---

### Post by SQuark on 2009-08-25
@balud: What version of the Nvidia drivers are you using?

You may want to try installing the (stable) 185.18 drivers following the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1125400).

---

### Post by ozzyprv on 2009-08-25
> **SQuark said:**
> @balud: What version of the Nvidia drivers are you using?

You may want to try installing the (stable) 185.18 drivers following the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1125400).

That is the same I am using, 185.18.14. It has caused no problem so far.
I got it installed and semi-smooth updates for the server kernel using this thread: [http://ubuntuforums.org/showthread.php?p=7507616#post7507616](http://ubuntuforums.org/showthread.php?p=7507616#post7507616)

Enjoy.

---

### Post by hellforgedheart on 2009-08-26
I haven't had many problems running this machine with 9.04 64-bit (minor wireless woes because of kernel driver) or Fedora 11 64-bit (there are some acpi quirks that delays power source detection) and I've run the latest nVidia drivers on both setups.

---

### Post by balud on 2009-08-28
> **SQuark said:**
> @balud: What version of the Nvidia drivers are you using?

You may want to try installing the (stable) 185.18 drivers following the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=1125400).
thanks for that. will try and post back. my graphics card model is 'GeForce 9200M GS' and the driver 'NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009' from sysinfo.

---

### Post by lessfield on 2009-10-07
Just wanted to report that with  alsa 1.0.21 the built-in microphone works much better. 
I used soundcheck's alsa updating script 

[http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")

also had to add 

```
options snd-hda-intel model=dell-m6
```
to the tail of /etc/modprobe.d/alsa-base.conf

---

### Post by arslano on 2009-10-25
Hello

I've installed Ubuntu 9.04 as a secondary operating system to my xps 1340. I am able to select Vista or Ubuntu by GRUB boot loader.

The problem is: in Vista there is no overheating or fan problem. But in Ubuntu the fans always runs, it doesnt stop and the keyboard area is extremely hot.

I'm sure that the fan speed is at the up level. it's too loud and fast.

any suggestions?
thanks

---

### Post by thiefy on 2009-11-26
> **SQuark said:**
> All right, forget what I said about the wireless card. It does work out of the box on Ubuntu. It's just that the hardware switch only toggles bluetooth. So I had to boot into Vista to turn on my wireless and then boot back into Ubuntu and now everything's working fine. :)

   you can usually tweak that annoyance in the bios.

---

### Post by jtsmith73 on 2009-11-28
The only minor annoyance I have with the hardware on my XPS 13 (m1340) is with Cheese!.  Takes snaps just fine, but the app crashes when I attempt to make a movie clip.  Don't know what to do about that.  I'm running karmic and Kubuntu and this machine only heats up when it's doing tasks.  Otherwise, it's only sipping resources (and staying cool).  I too have the 1510 wireless card and it works fine with the default wireless manager and the latest broadcom-sta driver (I think wireless supplicant is also included).
 
What I haven't tried are the DVI and HDMI out ports.  Has anyone tested these in *ubuntu?
 
Cheers,
 
Jimbo

---

### Post by Kai69 on 2009-12-10
Just read this thread you were saying about heat problems on the xps i have a dell xps m1330 i had heat problems and updated the bios it was A14 new bios is A15 this has cured heat and display hang problems .
Just keep checking the dell drivers website. Hope this helps.

---

### Post by underminded000 on 2009-12-22
Has any one had any burning problems with the M1340? Currently using the Ubuntu 9.10 amd64 flavor and i keep experiencing slow burning problems in Braesero (Like 100/kbs) with Dvd's and Cd's. Ive tried k3b as well and i keep getting Underflow Error / Check your disc speed error. Other than that, everything works perfect.

---

### Post by Dr. Funkenstein on 2010-01-11
I Just recently got a Dell Studio XPS 1340 on December 30, 2009..... and I will be returning this laptop for a full refund.


Why?


Mostly because of the NVIDIA G 210M card..... it's not even used by the Linux NVIDIA drivers, and adding the BusId does not work..... so what I'm left with is the integrated 9400M G motherboard card instead of 512MB of dedicated GDDR3 graphics.


I wouldn't even care about the hybrid switching or boost if I could just configure it to use the NVIDIA G 210M on AC power and the lowest setting of the 9400G M on battery.


What really sucks is that NVIDIA has no plans for Hybrid SLI support for their Linux drivers..... which is terrible because all of their new cards use it..... so I guess I'll have to find a new laptop with ATI instead.

Here are some bug reports and threads:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756?comments=all)
[http://www.nvnews.net/vbulletin/showthread.php?t=110920](http://www.nvnews.net/vbulletin/showthread.php?t=110920)
[http://www.nvnews.net/vbulletin/showthread.php?t=143337](http://www.nvnews.net/vbulletin/showthread.php?t=143337)



As for the rest of the computer I really liked it:

Intel P9600 at 2.66GHz and 6Mb cache
4GB DDR3 1066MHz RAM
NVIDIA G 210M 512MB dedicated (when it actually did work for those moments on windows 7)
Slim LED screen with 1.3mp cam (nice and bright)
Backlit Keyboard
128GB Samsung SSD drive that I aligned my ext2 partitions with "fdisk -H 224 -S 56 /dev/sda"

(I had planned on reformatting it to ext4 with no journaling, or even fuse-zfs, but don't need to now.... I also was going to add a FreeBSD install using ZFS but again, no need to do it now)  



This computer never ran super hot when in Windows 7, but it did crash/freeze ALL THE TIME on simple programs like Google Earth and the Windows Experience Index test. I've never had to hard-restart/reboot a computer so many times before, it was constantly freezing where the only option left was to use the power button.


I also downloaded some video game demos from the NVIDIA site and I had a terrible time running them.


One race care game couldn't even make it past the intro video and player set up, while the other video game demo (street fighter) started alright, but when I ran the benchmark demo it would crash and the driver would fail and have to restart again..... which totally sucks. Other than that, the FPS average was 30.75..... and even though it looked nice I still saw video tearing (also on google earth).



Other things that sucked were the headphone plugs, the crackling speakers with bad sound, and only having 2 usb.


I really wish that the NVIDIA G 210M had worked better, I would have not cared about the speakers/headphones and would have just got some bluetooth ones or something.


Overall the Dell Studio XPS 1340 is a very nice laptop, it's the NVIDIA cards that I'm having issues with and their lack of caring to bring the same support features to their Linux users..... (and maybe if I allowed their Dell support guy to come and change my motherboard, then maybe I would have had better results with Windows 7..... but I still would have missed using Linux..... so I figured I can return this now and get a full refund and have a better knowledge of what I want in a computer)

---

### Post by DodgeV83 on 2010-01-17
> **Dr. Funkenstein said:**
> I Just recently got a Dell Studio XPS 1340 on December 30, 2009..... and I will be returning this laptop for a full refund.


Why?


Mostly because of the NVIDIA G 210M card..... it's not even used by the Linux NVIDIA drivers, and adding the BusId does not work..... so what I'm left with is the integrated 9400M G motherboard card instead of 512MB of dedicated GDDR3 graphics.


I wouldn't even care about the hybrid switching or boost if I could just configure it to use the NVIDIA G 210M on AC power and the lowest setting of the 9400G M on battery.


What really sucks is that NVIDIA has no plans for Hybrid SLI support for their Linux drivers..... which is terrible because all of their new cards use it..... so I guess I'll have to find a new laptop with ATI instead.

Here are some bug reports and threads:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756?comments=all)
[http://www.nvnews.net/vbulletin/showthread.php?t=110920](http://www.nvnews.net/vbulletin/showthread.php?t=110920)
[http://www.nvnews.net/vbulletin/showthread.php?t=143337](http://www.nvnews.net/vbulletin/showthread.php?t=143337)



As for the rest of the computer I really liked it:

Intel P9600 at 2.66GHz and 6Mb cache
4GB DDR3 1066MHz RAM
NVIDIA G 210M 512MB dedicated (when it actually did work for those moments on windows 7)
Slim LED screen with 1.3mp cam (nice and bright)
Backlit Keyboard
128GB Samsung SSD drive that I aligned my ext2 partitions with "fdisk -H 224 -S 56 /dev/sda"

(I had planned on reformatting it to ext4 with no journaling, or even fuse-zfs, but don't need to now.... I also was going to add a FreeBSD install using ZFS but again, no need to do it now)  



This computer never ran super hot when in Windows 7, but it did crash/freeze ALL THE TIME on simple programs like Google Earth and the Windows Experience Index test. I've never had to hard-restart/reboot a computer so many times before, it was constantly freezing where the only option left was to use the power button.


I also downloaded some video game demos from the NVIDIA site and I had a terrible time running them.


One race care game couldn't even make it past the intro video and player set up, while the other video game demo (street fighter) started alright, but when I ran the benchmark demo it would crash and the driver would fail and have to restart again..... which totally sucks. Other than that, the FPS average was 30.75..... and even though it looked nice I still saw video tearing (also on google earth).



Other things that sucked were the headphone plugs, the crackling speakers with bad sound, and only having 2 usb.


I really wish that the NVIDIA G 210M had worked better, I would have not cared about the speakers/headphones and would have just got some bluetooth ones or something.


Overall the Dell Studio XPS 1340 is a very nice laptop, it's the NVIDIA cards that I'm having issues with and their lack of caring to bring the same support features to their Linux users..... (and maybe if I allowed their Dell support guy to come and change my motherboard, then maybe I would have had better results with Windows 7..... but I still would have missed using Linux..... so I figured I can return this now and get a full refund and have a better knowledge of what I want in a computer)

For what it's worth, I just got the Dell Studio XPS 13 (1340) and experienced multiple crashes, bluescreens (related to the video card.  ...etc in Windows 7.  Well, the first thing I did when I got the machine is go to [www.nvidia.com](www.nvidia.com) and download the newest drivers.  After going back to the official Dell drivers the laptop came with (downloaded from their site) I have had nothing but joy from this machine. :)

Since I know the Linux drivers don't support Hybrid SLI, I've decided to run Windows 7 as a "backend" if you will, with Ubuntu running in Virtualbox.  I removed all unnecessary services and startup items (though I kept the Dell facial recognition to login ;)).  I have found this to be better than running Ubuntu and occasionally running Windows in Virtualbox for a few reasons:

[LIST]
[*]All drivers work perfectly (Hybrid SLI is great)
[*]Ubuntu is very light on resources, easily running in Virtualbox
[*]For those times you need a Windows box, it is already running natively
[*]Less Ubuntu bugs (Whenever I close my laptop lid on my Dell m1330 the screen always comes back on after a few minutes, networking issues...etc)
[*]No worrying about using Wine or having to reboot for gaming
[*]I have yet to come across an Ubuntu application which doesn't run well in Virtualbox, while many of my Windows applications do not run well in Virtualbox.
[/LIST]

All in all, I am extremely satisfied with this laptop.

Edit: Posted in both threads to help other's who are having trouble with this laptop.

---

### Post by Dr. Funkenstein on 2010-01-20
Yeah, I really did like that laptop..... except for the nvidia G 210M  issues.


As for drivers:

I first used the original ones  that were installed from the factory. Those would freeze.

Then  after I did a clean install of Windows-7 (with the provided disk) I  installed all of the newest drivers from the Dell Driver Download page  for the SXPS 1340 64-bit Windows-7 (instead of using the old drivers on  the Dell driver disk), and those nvidia drivers froze. 

I even  tried the newest Windows-7 driver from the official NVIDIA site (195.26  maybe?) and they lowered my graphics score from a 5.9 to a 4.8 score,  plus they made Google Earth start to show a strange new tearing of the  graphics..... and nvidia would still freeze.


So Dell received  my laptop today and they sent me a gmail that said that they would  credit the card within 30 business days..... so I'm searching for a new  laptop.


I can't find any laptops that have a SSD drive (other  than the macbook pro/air, sony cw or sony x series, and a few HP  laptops). And I really want a backlit keyboard so the HP notebooks are  out.


Now I sort of regret sending that laptop back, but I  have been looking at the Dell Studio 14z with an Intel P8700, 5GB DDR3, 8  cell battery, NVIDIA 9400M G (I figure this will work decently in  Linux), and of course it has the nice backlit keyboard (and a 900p  screen). I could buy it right now for $1184 with those stats above, and  then maybe replace the 320GB 7200rpm HDD with a 80GB Intel SSD..... but  I'm not sure how much that would cost me, I guess I could wait a while  for the SSD prices to drop.


And I was hoping that Dell would  make a new Studio 14z with the Intel i5-540M processor, but so far there  is only that Best Buy "blue label" Studio 15(z?)..... it is a very cool  color, and the 13.3 inch Sony blue label also looked good, but again,  no SSD option in any of these i5-430M blue label series.

---

### Post by DodgeV83 on 2010-01-22
> **Dr. Funkenstein said:**
> Yeah, I really did like that laptop..... except for the nvidia G 210M  issues.


As for drivers:

I first used the original ones  that were installed from the factory. Those would freeze.

Then  after I did a clean install of Windows-7 (with the provided disk) I  installed all of the newest drivers from the Dell Driver Download page  for the SXPS 1340 64-bit Windows-7 (instead of using the old drivers on  the Dell driver disk), and those nvidia drivers froze. 

I even  tried the newest Windows-7 driver from the official NVIDIA site (195.26  maybe?) and they lowered my graphics score from a 5.9 to a 4.8 score,  plus they made Google Earth start to show a strange new tearing of the  graphics..... and nvidia would still freeze.


So Dell received  my laptop today and they sent me a gmail that said that they would  credit the card within 30 business days..... so I'm searching for a new  laptop.


I can't find any laptops that have a SSD drive (other  than the macbook pro/air, sony cw or sony x series, and a few HP  laptops). And I really want a backlit keyboard so the HP notebooks are  out.


Now I sort of regret sending that laptop back, but I  have been looking at the Dell Studio 14z with an Intel P8700, 5GB DDR3, 8  cell battery, NVIDIA 9400M G (I figure this will work decently in  Linux), and of course it has the nice backlit keyboard (and a 900p  screen). I could buy it right now for $1184 with those stats above, and  then maybe replace the 320GB 7200rpm HDD with a 80GB Intel SSD..... but  I'm not sure how much that would cost me, I guess I could wait a while  for the SSD prices to drop.


And I was hoping that Dell would  make a new Studio 14z with the Intel i5-540M processor, but so far there  is only that Best Buy "blue label" Studio 15(z?)..... it is a very cool  color, and the 13.3 inch Sony blue label also looked good, but again,  no SSD option in any of these i5-430M blue label series.

For what it's worth, I have the Nvidia 9500M (9400 + 9200 Hybrid SLI) card.  I haven't tried running Ubuntu natively yet, as running it in Virtualbox has been the best of both worlds for me.  It's unfortunate, but this is literally the best Ubuntu experience I've ever had.  Everything still works perfectly, even video editing and encoding in the Virtualbox.  Thanks to the low-power graphics card, I've yet to have an overheating problem even with everything running.  I have yet to see how it reacts to a long WoW session, however.

When something comes up that usually doesn't work well in Linux (Hulu Full-Screen Flash anyone), I am no longer embarrassed with the bad-performance I get when hooking it up to the flatscreen. I'd also forgotten how good it feels to plugin an external monitor (or projector) and have your computer automatically recognize the monitor, set the correct resolution...etc

Anyway, that's another topic for another thread.  Maybe it's not too late to take Dell up on their motherboard exchange offer?  The fact that it was running so poorly for you in Windows tells me something was amiss.  Or you could always get the same laptop with the Nvidia 9500 card, would safe you some money as well.

---

### Post by Dr. Funkenstein on 2010-01-22
> **DodgeV83 said:**
> Or you could always get the same laptop with the  Nvidia 9500 card, would safe you some money as well.


Yeah, I've been looking at the Studio XPS 13 again (with the  9400G M and no discrete card). It's one of the few laptops out there  that includes a SSD flash hard drive option.


The XPS that  I've been looking at only has the Intel P8800 instead of the P9600  processor that I returned, but it should be similar since they have the  same clock speeds of 2.66GHz, the only difference between the P9600 and  the P8800 is that the P9600 has 6MB cache while the P8800 has a 3MB  cache. I'm not sure what sort of difference that would make..... I doubt  that I would even notice.


I've also been looking at the  brand new Studio 14 with the i5-520M processor, and I keep hoping that  it will give a SSD hard drive option but they haven't added it yet.  (though it is mentioned on the "Design" page, as well as blue ray  option, a 900p screen, and the i7 processors with 1333MHz DDR3 RAM..... plus it already comes with a 9 cell battery, 3 usb slots, and I personally like the place they put the heat vent better than the blocked one on the XPS 13) 


And  I've also been thinking about buying the old Studio 14z (the thin one  with the external CD/DVD drive) that comes with the Intel P8700 and the  NVIDIA 9400M G (again I wouldn't have to worry about the discrete card  running and wasting battery power without actually being used). I also  thought that I could buy a OCZ or and Intel SSD and put it in myself.


I'm  not too sure what I'm going to do. I know that the new i3/i5/i7 and the  on-board GMA HD might not work with Linux yet:  [http://www.phoronix.com/scan.php?page=news_item&px=NzkwOA](http://www.phoronix.com/scan.php?page=news_item&px=NzkwOA)


And  at the same time I don't really want to spend $1500 dollars on older  processors and older graphics cards that seem like they're on there way out.

---

### Post by Dr. Funkenstein on 2010-02-05
> **sarashah said:**
> Seems very nice and balanced for specs. I like the 9500m but I would have thought they would go with the 1xx series GPU.

They have an upgrade option to "NVIDIA G 210M" of the 2XX series GPU.

They had 3 different options:

9400M G
9500M G
G 210M

---

### Post by Kareeser on 2010-02-18
Hello everybody, I've been following the posts here, and ended up buying the Studio XPS 1340 - great so far! Resized the Windows partition, and installed Ubuntu on the rest of the space. Everything seems to work so far (proprietary nvidia driver was a cinch, no errors, and I think all I have to do is change the BusID to use the G210M.)

So far so good. :)

The full laptop test is here: [https://wiki.ubuntu.com/LaptopTestingTeam/DellStudioXPS1340](https://wiki.ubuntu.com/LaptopTestingTeam/DellStudioXPS1340)

---

### Post by Kareeser on 2010-03-03
For those wondering whether Ubuntu will support the 1340's hybrid graphics system:
[http://www.phoronix.com/scan.php?page=news_item&px=ODAyMg](http://www.phoronix.com/scan.php?page=news_item&px=ODAyMg)

The answer is: *pretty much yes, in Lucid*

---

### Post by spotdog14 on 2010-03-10
Alright, I figure I would post here. I have had the 1340 for a year now and love it. I dual book Ubuntu 9.10 and Win 7. The only problem I am really having in Ubuntu is my wifi. I use synergy at work and I get constant drop outs with the network. This does not happen when using ethernet. I also notice it by its self when using deluge or downloading anything on any AP. 

I have the Dell 1515 card, anyone else experiencing network drop outs?

---

### Post by rstuart on 2010-04-28
I have been experiencing wireless dropouts as well. Not sure what the cause is, all I know is that I don't see the issue on Windows 7.

Given 10.04 is just around the corner I am going to hold off on doing anything drastic to see if the new release improves the situation.

---

### Post by ozzyprv on 2010-05-13
I was experiencing some of those drop-outs last year but I blamed my old router. I do not not remember having problems after upgrading my router to a WRT54G (running DD-WRT).

---

### Post by emdee on 2010-05-16
I also own the 1340 about a year now and I experienced drop outs at a high rate using jaunty. After upgrading (actually I reinstalled because I don´ t really trust the upgrade process) to lucid now it seems to be better - there are still drop outs but the reconnect is much faster.
I can also confirm that drop outs do NOT happen with my WRT54G (also on DD-WRT).
Besides I can recommend to upgrade to lucid anyway as it seems to run overally smoother on this nice piece of technology.

---

### Post by ozzyprv on 2010-05-16
> **emdee said:**
> 
Besides I can recommend to upgrade to lucid anyway as it seems to run overally smoother on this nice piece of technology.

I am considering this very point these days. What tweaks did you have to do (if any)?

Thanks.

---

### Post by gshmaritz on 2010-05-21
Installed Lucid.
I see that Nvidia 9400m G is enabled. The PC is running on average 15 degrees celcius warmer than it does on Win7. 
Had to go back to win7. No point having a laptop you can't put on your lap. And yes all the BIOS updates have been done and newest drivers are installed. I'm guessing it would run cooler if I could disable 9400m G and enable 9200m GS?

Nvidia please address this issue...
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)

---

### Post by HarrisonNapper on 2010-05-22
> **gshmaritz said:**
> Installed Lucid.
I see that Nvidia 9400m G is enabled. The PC is running on average 15 degrees celcius warmer than it does on Win7. 
Had to go back to win7. No point having a laptop you can't put on your lap. And yes all the BIOS updates have been done and newest drivers are installed. I'm guessing it would run cooler if I could disable 9400m G and enable 9200m GS?

Nvidia please address this issue...
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)

Possibly but doubtful since for me the warmth of the PC was the CPU. Have you tried setting the cpu governor to conservative? That made it run much cooler for me and for a lot of others. The cpu applet in gnome will only let you set it for one session, so you have to edit a config file to make it permanent. Since the 1340 has a dual core, you'll need two cpu applets and in the preferences for the applet, set one to cpu 0 and the other to cpu 1.

Hope that helps.

---

### Post by gshmaritz on 2010-05-22
> **HarrisonNapper said:**
> Possibly but doubtful since for me the warmth of the PC was the CPU. Have you tried setting the cpu governor to conservative? That made it run much cooler for me and for a lot of others. The cpu applet in gnome will only let you set it for one session, so you have to edit a config file to make it permanent. Since the 1340 has a dual core, you'll need two cpu applets and in the preferences for the applet, set one to cpu 0 and the other to cpu 1.

Hope that helps.


But it's the GPU's temp that is through the roof?

---

### Post by emdee on 2010-05-24
> **ozzyprv said:**
> I am considering this very point these days. What tweaks did you have to do (if any)?

Thanks.

the only thing that did not work right after install, was the skype video chat - it did not show my counterpart, yet transmitted my video stream to him. easy fix: when i start skype with: 'export XLIB_SKIP_ARGB_VISUALS=1 && skype' it works fine.

everything else works fine too - I must admit that battery life with all the compiz stuff turned on is of course not that good as with windows, but you can always turn it of or get the bigger battery, which also elevates the laptop a bit, so it doesn´t get to hot either.

i use the nvidia drivers from the repository and they work fine - there is also a thermal monitor included in the nvidia settings (on my xps it is always in the green area, about 51 °C) and you can set the power usage to adaptive, that should also take away some heat - additionally to scaling down your cpus.

---

### Post by HarrisonNapper on 2010-05-24
> **gshmaritz said:**
> But it's the GPU's temp that is through the roof?

What is leading you to suspect the GPU? Also, have you tried disabling compiz and using metacity? Do you use a lot of 3d desktop effects. It's possible that it's a Gnome thing, too, as ever since I switched to KDE and set the default cpu governor to conservative, temperature hasn't been a problem.

---

### Post by gshmaritz on 2010-05-24
> **HarrisonNapper said:**
> What is leading you to suspect the GPU? Also, have you tried disabling compiz and using metacity? Do you use a lot of 3d desktop effects. It's possible that it's a Gnome thing, too, as ever since I switched to KDE and set the default cpu governor to conservative, temperature hasn't been a problem.

Mainly because I think Nvidia drivers aren't up to standard. I mean in Win there is hybrid sli. But in ubuntu that card is running all the time... the heat also seems to come from where the GPU is situated. But I'm not sure anymore. I will try your tips and report back...

---

### Post by HarrisonNapper on 2010-05-24
> **gshmaritz said:**
> Mainly because I think Nvidia drivers aren't up to standard. I mean in Win there is hybrid sli. But in ubuntu that card is running all the time... the heat also seems to come from where the GPU is situated. But I'm not sure anymore. I will try your tips and report back...

[http://www.bradtrupp.com/ubuntu-cpu-temperature.html](http://www.bradtrupp.com/ubuntu-cpu-temperature.html)

Once you get lm-sensors installed, you can get xsensors or you can just type sensors into a terminal.  In any case, look at one of those when it's hot and it will tell you what cpu temp is.

---

### Post by gshmaritz on 2010-05-24
> **HarrisonNapper said:**
> [http://www.bradtrupp.com/ubuntu-cpu-temperature.html](http://www.bradtrupp.com/ubuntu-cpu-temperature.html)

Once you get lm-sensors installed, you can get xsensors or you can just type sensors into a terminal.  In any case, look at one of those when it's hot and it will tell you what cpu temp is.


Thank you for the reply... Didn't even know of lm-sensors. 
Under normal conditions (after a reboot) - chrome, music, IM
Cores temp are between 50 - 52 degrees celcius. while according to the nvidia app the gpu is at 60-63.
While skipping through a avi movie the temps of the cpu cores go up to 57 degrees while nvidia reports a temperature of 68.

Any ideas?

---

### Post by pulz on 2010-06-05
How are your battery time on linux compared to windows for you other users? 

The battery seems radicaly worse in ubuntu vs windows, i suspected the sli gpu to be blamed for this.

But it would be fun to hear what other users get on "normal" usage.

---

### Post by HarrisonNapper on 2010-06-05
> **pulz said:**
> How are your battery time on linux compared to windows for you other users? 

The battery seems radicaly worse in ubuntu vs windows, i suspected the sli gpu to be blamed for this.

But it would be fun to hear what other users get on "normal" usage.

Mine is terrible, as well. I believe earlier in the thread someone pointed something out about this, but don't recall what it was. I think it was that there is a Windows-only driver that controls the sleep state on one or more of the components, making whichever peripheral run constantly. I'm sure with LXDE and after running powertop, one could squeeze several hours out of it.

I get a little under 2 if I'm using KDE with Kwin compositing suspended.

---

### Post by yossell on 2010-06-06
My experience in battery life on ubuntu seems to be atypical in that I'm squeezing more out of it than I get on my typical window session. 

I have the m1330, dreaded 8400MGS model. It's 2 1/2 years old with the original nine cell battery. Running powertop and on an openbox session, I can still get between five and five and a half hour use from it. This is a little more than I get when I'm running windows.

This is also on 10.04, with an incredibly large number of wakeups (over a hundred), partly caused by the load balancing tick problem of the current kernel. Could get it down to around 10 wakeups in 9.04 - but it doesn't seem to be having any adverse affect on battery life.

---

### Post by ozzyprv on 2010-06-07
> **yossell said:**
> 
This is also on 10.04, with an incredibly large number of wakeups (over a hundred), partly caused by the load balancing tick problem of the current kernel. Could get it down to around 10 wakeups in 9.04 - but it doesn't seem to be having any adverse affect on battery life.

I know it is kind of off topic, but I gotta ask.
What are "wakups" in this context?

Thanks.

Now, on topic:
I got a bit less than 2 hours like others. I cannot compare with Windows, I deleted that partition as soon as I got my laptop...a bit more than a year ago.

---

### Post by yossell on 2010-06-07
I think the program powertop was instrumental in helping me squeeze 5+ hours from my battery as opposed to the 2.5 I was getting when I first installed Ubuntu and ran Gnome.

Here's what I thought I knew: 

One thing that drains battery is the cpu idling in a high power state; power management down clocks the chip when it's not doing anything. However, a lot of background processes are often bothering the cpu, wanting things done, and this WAKES UP the chip from its idle state for a short period of time, to do its business. Powertop reports on these wake ups and makes suggestions for changing them. It's a good programme which worked well for me on 9,04, and I suggest giving it a go. 

I'm not sure how effective it is on 10.04, and I'm wondering whether wakeups was so important or is so important in 10.04, given that I'm here getting great battery life, even with many of these wake ups. But, with powertop on an openbox session, I'm getting 5+ hours life on an old battery, which is great.

---

### Post by rockstar__ on 2010-06-07
hello.. i just installed ubuntu 10.04 LTS on my M1340.. this is my first time trying ubuntu.. but my wireless is not working.. and i can only use 2.2GB memory out of 4GB.. can anyone help? thanks a lot..

---

### Post by ozzyprv on 2010-06-07
> **rockstar__ said:**
> hello.. i just installed ubuntu 10.04 LTS on my M1340.. this is my first time trying ubuntu.. but my wireless is not working.. and i can only use 2.2GB memory out of 4GB.. can anyone help? thanks a lot..

2.2 vs 4 GB of RAM.
Las time I checked (9.04), I had to install the server edition (and later the desktop portion) to "see" the full 4GB of RAM.
I am using 10.04 now and same as you, I only "see" 2.2 GB of RAM. 
I guess I am been lazy. I installed the desktop version of 10.04 to tried it and got used to it. I now what to do....reinstall (fresh) 10.04 server edition and then the desktop portion.

Hopefully somebody else knows a better solution.

Wireless
Connect to internet via ethernet cable. Then proceed to update you system (System>Administration>Update Manager).
Once this is completed go to System>Administration>Hardware Drivers. Enable/install the driver for the wireless card.

I hope I helped!

---

