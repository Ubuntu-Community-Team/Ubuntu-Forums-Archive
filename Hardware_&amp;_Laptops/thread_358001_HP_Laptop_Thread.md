---
title: "HP Laptop Thread"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by #Reistlehr- on 2007-02-10
Hey everyone, i just wanted to see if i could get some input for your HP Notebook. I was wondering where everyone stood with working hardware and steps taken. If ya don't mind, think you can copy the format im gonna use?

Model: Dv9000z
Ubuntu: Edgy Eft
CPU: AMD Turion64
Video: nVidia Go 7600
Memory: 2GB
Wireless: Broadcom 4310
Sound: HD-Nvidia Generic (MCP51)

Video working by adding noapic to boot line. Otherwise xserver would crash.
Broadcom 4310, ndiswrapper, fwcutter, didnt work. tried windows drivers provided, and multiple sources. Bought a ZEW2500p, and now have wireless.
Sound not working. Compiled new alsa 1.0.13 drivers, and non of them worked
Need to boot with noapic and acpi=off.

where does everyone else stand?

---

### Post by Chenzo on 2007-02-10
Model: Dv2000z
Ubuntu: Edgy Eft
CPU: AMD Turion64
Video: nVidia Go 6100
Memory: 1GB
Wireless: Broadcom 4310
Sound: HD-Nvidia Generic (MCP51)

I got everything working in about a day except my headphone jack.  Wireless was the only major issue, and this website solved my problems; it also has a list of many other compatability issues and fixes. A great resource for anyone with an HP or compaq. Scroll down until you see "Broadcom BCM4311 (pain, all pain)" and it will show you how to get wireless working (don't worry, it's not as bad as it sounds).

[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A](http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A)

I'm in the process of getting the headphone jack working. My roomate has the same computer as I do, and after a little effort he has everything, even headphone jack, working perfectly, so it's not impossible. Also keep in mind that both my roomate and I are very new to linux, i've been running ubuntu for only about 4 months. If I can get it running, anyone can.

---

### Post by feed_sparky on 2007-02-10
Model: dv5215us
Ubuntu: Feisty 7.04
CPU: AMD Turion64
Video: ATI Radeon Xpress 200m 128mb sideport
Memory: 1GB
Wireless: Broadcom 4318
Sound: ATI IXP AC97

I used ndiswrapper to get the Broadcom 4318 wireless card to work. Everything is working even the FGLRX driver.

---

### Post by teaker1s on 2007-02-10
**edgy** was an unstable nightmare it wouldn't boot,shutdown, crashed randomly,Nvidia drivers killed ndiswrapper
**Feisty** all seems better and stable,just crashes logging out

---

### Post by #Reistlehr- on 2007-02-10
do all of you have to use noapic and acpi=off in the bootline? if not, what do you use

---

### Post by teaker1s on 2007-02-10
noapic and acpi=off no effect on my dv6116eu with feisty. when I updated phoenix bios to F.27 it went mental.
feisty boots perfectly with latest updates and I haven't altered anything, crashes on logout and I think it's a display driver issue

---

### Post by ikariwths on 2007-02-11
hp 500 (rq260aa) it is an intel centrino notebook
everything work's at ubuntu 6.10 but touchpad it seem's to be a kernel bug or something like that

---

### Post by housam on 2007-02-11
My hp compaq nx7400 is working just fine either with Dapper or Edgy.
Specs : Intel core duo ( 2.0 G Hz - 2 Mb cash ) 1 Gb RAM - 100 GB sata - intel 950 GMA card. dial-up modem working fine - LAN working fine.

---

### Post by drpaul on 2007-02-11
Model: dv6150us
Ubuntu: Edgy Eft
CPU: Intel Core 2 Duo 1.66 GHz
Video: Intel 945
Memory: 2GB
Wireless: Intel
Sound: Intel HDA

Video working at 1280 x 800 by adding 915resolution. Otherwise stuck at 1024 x 768.
Wireless worked right away.
Sound works from the speakers if I don't try to improve it.  Built in microphone doesn't work. Followed lots of the threads, but all I can seem to do is kill the sound from the speakers.
Haven't tried the built in web cam yet.

Paul

---

### Post by mikewhatever on 2007-02-11
HP Pavilion 5000, core2duo, nvidia 7400 go.
Four things did not work:
1. Wireless Intel3945. Had to install linux restricted modules.
2. Microphone. Had to install the newer alsa driver.
3. Direct rendering. Had to reinstall nvidia driver.
4. An error is displayed on boot, but no idea what is it related to.
> [17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2

---

### Post by pveith on 2007-02-11
TC1100, HPs older TablettPC is working like a charm (even though the nvidia card is no longer supported in newest driver). Hardware basically working, just no suspend to ram and no suspend to disk...

---

### Post by gapplewagen on 2007-02-11
HP Compaq nx7000
Intel Pentium 4-M 1.6Ghz
1GB RAM
ATI Mobility 9200

I originally installed Dapper on this laptop and it worked great right away.  All hardware was properly detected and worked with no tweaking.  The only thing that didn't work was putting the laptop into suspend mode.  This was resolved as soon as I upgraded to Edgy.

A client of mine gave me a HP nw8240 to work on and I decided to see how Edgy would run on it.  I think the laptop itself has hardware issues because it would just turn itself off at random while running WinXP.  I had similar problems while trying to install Ubuntu.  However, after turned off ACPI support I was able to get it to boot and install.  Wireless was working but I didn't get any notifications of signal strength.  No battery levels, etc (makes sense, ACPI handles this)

---

### Post by comfurtn on 2007-02-11
HP Pavilion dv6102od
Intel Centrino Mobile 1.8 GHz
Intel 3945abg wireless chipset
Intel 945 Onboard Video Chipset

Using Ubuntu Edgy standard install, everything works normally.. installing 915resolution fixes the widescreen resolutions.  Compiling the newest ALSA driver solves issues with the front headphone/microphone jacks.  The media card reader works if you enable the driver... see [the wiki page]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu") for more info.

---

### Post by serag on 2007-02-11
Model: Dv9010ca
Ubuntu: Edgy 6.10 64 bit
CPU: AMD Turion64 x2
Video: nVidia 6150 Go
Memory: 2GB
Wireless: Broadcom 4311
Sound: HD-Nvidia Generic (MCP51)

Video only works with vesa or nv, crashes whenever set to nvidia
Need to boot with acpi=noirq
Sound works but skips, is slow
Broadcom wireless doesn't work at all, have to use netgear MA111 usb.

---

### Post by ziphead on 2007-02-11
dv2125nr, running Dapper

wifi:
Broadcom 4311 works with ndiswrapper compiled from source.

video:
Still struggling with Nvidia driver: crashes with a "no usable screens found" message  
Also, widescreen resolution does not work under any driver.
nv driver will not give resolution better than 640 by 480.
Using vesa driver @ 1024x768

Headset output does not work.

If I had known how agonizing this was going to be, I would not have bought this POS HP.
But I'm stuck with it.  :mad:

---

### Post by zaazu48 on 2007-02-12
> **ikariwths said:**
> hp 500 (rq260aa) it is an intel centrino notebook
everything work's at ubuntu 6.10 but touchpad it seem's to be a kernel bug or something like that

I have the same problem.... I saw some instructions on how to overcome it but it is still not working

[http://ubuntuforums.org/showthread.php?t=295863&highlight=ksynaptic](http://ubuntuforums.org/showthread.php?t=295863&highlight=ksynaptic)

can any one please help.....

---

### Post by drpaul on 2007-02-12
Installing the .13-rc3 version of the Alsa driver enabled my sound capture and put sound out on the earphone jack.
However, plugging in the earphone does not cutoff the speaker sound.

Anyone have a clue how to do that?

Also, I have had zero success in getting Ubuntu to see the builtin webcam.  All ideas are welcome.

Working on a dv6150us.

TIA

Paul

---

### Post by Bertha on 2007-02-22
Got the DV6119eu with the nvidia mcp51 sound. Got the headphones working after compiling the newest alsa driver. But I can't get the microphone working, for skype and ekiga. Anyone got this working? 

Almost got the broadcom working. When I try to connect to a wirleless network, the machine comletely hangs up. And I need to hold the power button to turn it off. Idea? :)

---

### Post by wv25m on 2007-02-22
HP DV9030 running Kubuntu 6.10 (dual boot with XP on first HDD and Linux on second HDD)

Works somewhat... 

Out of the gate with some minor updating... wireless no issues, video (Nvidia) seems to work fine, sound out of laptop speakers works, ipod mounts fine...

Issues: microphone inop, built-in webcam is detected as USB2 cam but I have no idea how to get it working or how to access it (Skype does not detect), headphone jack inop and laptop speakers do not shut off when something is plugged in, my Canon all-in-one printer does not seem to be supported... still have to try my A630 and see if it is detected.

I have read something about getting an update to ALSA since my version is out of date, but I don't know how to do that properly... tried but so far unsuccessful.  

Any help is appreciated...

So far I absolutely love Linux/Ubuntu but I need to get everything working before I can deep six XP... but so far so good and I am as happy as can be even with reduced functionality.


Thanks

---

### Post by drpaul on 2007-02-23
HP dv6125us

Installing uvccapture-0.4 got webcam running with ekiga. Have not got any other service to use it yet.

Progress!

Paul

---

### Post by pixeldotz on 2007-02-25
compaq c500
display - mobile intel 945GM (worked with 915resolution)
optiarc - dvd-rw ad-7530 ata device (works out of the box, haven't tried writing yet)
broadcom 802.11b/g WLAN (4311) (doesn't work. i need to compile ndiswrapper from source)
realtek - RTL8139/810x family fast ethernet nic (works out of the box)
altec lansing - conexant high definition audio (kind of works out of the box. compiled ALSA 1.14-RC2 driver from source and now the headphones and volume work much better. MIC still not working)
modem - hdaudio soft data fax modem with smartcp (i have no idea, i'll never use it)
generic pnp monitor (works fine at 1280x800 with 915resolution installed)


ubuntu 6.10 with all updates installed.  wireless doesn't work ofcourse even after following countless threads. i can't find the 'pain, all pain' thread to try it out.

the audio works 'ok' except of course for the mic which is what i'd originally planned to use this laptop for. the audio at 100% seems like maybe it's at 75%

everything else aside from MIC and Wireless seem to work fine.

---

### Post by DizzyTech on 2007-02-26
Compaq Presario V5204NR

Mobile Intel 945GM.  Widescreen resolution 1280*800, worked with 915resolution.
TSSTcorp CD-RW/DVD TS-L462C.  Worked out of box.  (Haven't tried writing yet).
Broadcom 4311 Wireless LAN.  Worked compiling NDISWrapper from source, though you have to press the wireless button twice (off, back on) to get it to start connecting to my home network.
Intel PRO/100 VE Ethernet Connection, worked out of box w/ NetworkManager
Synaptics Touchpad.  Worked mostly out of box, installing QSynaptics (w/ option "SHMConfig") caused mouse to skip around a times.
HDAudio Soft Data Fax Modem.  Don't know, I loathe dialup.
Conexant High-Definition Audio.  Worked much better quality-wise with ALSA 1.14-RC2 driver.
Intel Celeron M CPU @ 1.46 GhZ.  Worked out-of-box (duh).
Built-in LCD screen.
Dual-boot with Windows XP (OEM).  Boots into GRUB from NTLDR, really smooth!

I love my Compaq-buntu!
 :guitar:

---

### Post by Tom Tiger on 2007-02-26
Model: 6000
Ubuntu: Edgy Eft
CPU: Intel P3 800mhz
Video: ATI
Memory: 256mB
Wireless: none
Sound: generic
Network: intel pro100

Model: 6100
Ubuntu: Edgy Eft
CPU: Intel P3 1000mhz
Video: ATI
Memory: 512mB
Wireless: none
Sound: generic
Network: intel pro100

Both worked straight out of the box, no problems found, even the soundbuttons on the side worked. Okay... so they're a bit dated...:)

---

### Post by darklitany on 2007-02-27
Aside from having to wrap the broadcom wireless adapter, everything has worked very well. I am running Edgy on a Pentium 4 and an X300 ATI card. I have a random board bridge down though. It may be causing some performance issues. The mouse is touchy as sin, but the amazing thing to be was the power management. Windows couldn't tell me anything about my battery problems. Come to find out, my battery is half dead, I'll try and resync it but who knows.

Much happier with Ubuntu on this thing then I am with Windows, though I remain to dual boot.

---

### Post by gus sett on 2007-03-07
**return visit**
2nd week of May.  Staples bumps the pace with a *64-bit celery*, 1.6 Ghz M520
and a bundled printer, no DVD writing for $50 more.  A separate 19" flat panel widescreen
with leading specs is available too for $30 less than most other places.
**option to donate savings on battery upgrade/replacement to ubuntuforums.org**
got back from another thread about parts purchase, but it was about desktops. when
I doubled+ my battery capacity TitanNotebook.com sent a general discount code FBJUSV07 
good till June 30 for 20% **more** off.  Just got a great part & delivery today so see 
what you think. (donate is on the forum homepage, under forum help)

**THIS ROUND**
Ok.  I have reason to believe that the 2 DVD system recovery discs I made with this
drive instead of 6 or more CDs can help in a bind, should the counterpart reinstall 
utilities on the *hard drive* used here pan out.  I reloaded just the Muvee 
software; it and the drive were bystanders :) because...

Running a Vista session in safe mode then restarting the system restores most
if not all DVD read capabilities, if your Media Player window hangs.  A clue that
the disc isn't read right is that Vista can calculate and report the available disk space
for a read-only disc containing file(s), until you run safe mode and reboot to 
correct the information it displays.  The smaller read errors remaining were
addressed by uninstalling a 3rd party application I tried along with Muvee when
WMP 11 couldn't proceed.  One of its tags still appeared in a Vista header
alongside a burner icon.  Found the application entry in Control Panel/Programs and
Features.  Though uninstall said the app was already gone, the subsequent
reboot removed all traces, so perhaps Muvee overwrote it previously.  
Nonetheless, this pup's now housebroken...the coast is cleared. ):P


**AFTER**
was raised on unix in a former life, so glad that *google* made this Vista match
to a Linux camp based on HP notebook; had already done a half dozen searches because 
a number of prior results weren't in Arabic (alphabet text) format.
"Good" news for any others in similar circumstance. The problem appears to be
that tags to connect to help keys by way of the system register(s/y) may have
been concatenated instead of cleared, as different DVD writing applications
were tried after Media Player 11 couldn't proceed.  HP Total Care provided
instruction to clear most notably the LowerFilters value/text using regedit.  If you
encounter similar difficulties, seek comparable help, and remember to translate from
XP dialect to Vista phrasing.  Solution includes "simple" editing and reinstalling steps.

This 8X drive through Vista writes to Philips 16X DVD format to the satisfaction of 
Media Player 10 on XP, so confidence is high that shorter follow up with HP Total Care
will permit the drive to read its own output completely; as of this writing Vista
recognizes simply available free and total space of disc.


**BEFORE**
compaq c509NR with Celeron 440 came to me as follows:
broadcom 802.11b/g WLAN works good on Texas coast
altec lansing audio sounds acceptable, only medium volume--but my tv tuner
   software flags it as malfunctioning
microphone jack supports my Logitech mike for Skype internet telephone
   use, effectively enabling speakerphone operation
optiarc DVD RW AD-7530A ata driver wrote(?) the recovery discs to 16x 4.7GB DVD,
   but the driver 6.0.6000.16386 is yellow-flagged by the system, suggested as
   missing or corrupted.  Windows Media Player 11 and Muvee software included
   with Vista Home Basic **cannot write to the DVD+R's**.
HP support has suggested good first steps for remedy, but am seeking specific/narrow
   patch approach rather than a broadbrush subsystem update/reinstall.

**other subsystems seem fine**, haven't tried modem, faxing, or cable networking.
internal cooling fan works well with a 2-fan, 4 USB port scissor-style laptop base
  I encourage the aftermarket to keep making, because it folds small enough
  so that it isn't left behind after other accessories are packed with unit in a
  standard carrying case.



> **pixeldotz said:**
> compaq c500
display - mobile intel 945GM (worked with 915resolution)
optiarc - dvd-rw ad-7530 ata device (works out of the box, haven't tried writing yet)
broadcom 802.11b/g WLAN (4311) (doesn't work. i need to compile ndiswrapper from source)
realtek - RTL8139/810x family fast ethernet nic (works out of the box)
altec lansing - conexant high definition audio (kind of works out of the box. compiled ALSA 1.14-RC2 driver from source and now the headphones and volume work much better. MIC still not working)
modem - hdaudio soft data fax modem with smartcp (i have no idea, i'll never use it)
generic pnp monitor (works fine at 1280x800 with 915resolution installed)


ubuntu 6.10 with all updates installed.  wireless doesn't work ofcourse even after following countless threads. i can't find the 'pain, all pain' thread to try it out.

the audio works 'ok' except of course for the mic which is what i'd originally planned to use this laptop for. the audio at 100% seems like maybe it's at 75%

everything else aside from MIC and Wireless seem to work fine.

---

### Post by gus sett on 2007-03-07
**return visit**
Amazing.  this thread has about 7000 additional hits since my 1st post in March.
For mid July:   Best Buy now offers the c571NR with dual core T2080 for $450
the optional conexant patch MS released 4/03/07 applied on its 3rd attempt
on my system. no change in sound quality or volume but pinnacle software
still flags it as a device malfunction.

compaq c509NR with Celeron 440 came to me as follows:
broadcom 802.11b/g WLAN works good on Texas coast
altec lansing audio sounds acceptable, only medium volume--but my tv tuner
   software flags it as malfunctioning
microphone jack supports my Logitech mike for Skype internet telephone
   use, effectively enabling speakerphone operation
optiarc DVD RW AD-7530A ata driver wrote(?) the recovery discs to 16x 4.7GB DVD,
   but the driver 6.0.6000.16386 is yellow-flagged by the system, suggested as
   missing or corrupted.  Windows Media Player 11 and Muvee software included
   with Vista Home Basic **cannot write to the DVD+R's**.
HP support has suggested good first steps for remedy, but am seeking specific/narrow
   patch approach rather than a broadbrush subsystem update/reinstall.

**other subsystems seem fine**, haven't tried modem, faxing, or cable networking.
internal cooling fan works well with a 2-fan, 4 USB port scissor-style laptop base
  I encourage the aftermarket to keep making, because it folds small enough
  so that it isn't left behind after other accessories are packed with unit in a
  standard carrying case.



> **pixeldotz said:**
> compaq c500
display - mobile intel 945GM (worked with 915resolution)
optiarc - dvd-rw ad-7530 ata device (works out of the box, haven't tried writing yet)
broadcom 802.11b/g WLAN (4311) (doesn't work. i need to compile ndiswrapper from source)
realtek - RTL8139/810x family fast ethernet nic (works out of the box)
altec lansing - conexant high definition audio (kind of works out of the box. compiled ALSA 1.14-RC2 driver from source and now the headphones and volume work much better. MIC still not working)
modem - hdaudio soft data fax modem with smartcp (i have no idea, i'll never use it)
generic pnp monitor (works fine at 1280x800 with 915resolution installed)


ubuntu 6.10 with all updates installed.  wireless doesn't work ofcourse even after following countless threads. i can't find the 'pain, all pain' thread to try it out.

the audio works 'ok' except of course for the mic which is what i'd originally planned to use this laptop for. the audio at 100% seems like maybe it's at 75%

everything else aside from MIC and Wireless seem to work fine.

---

### Post by soul814 on 2007-03-11
Model: L2000
Ubuntu: Edgy
CPU: AMD Turion64
Video: ATI 200m
Memory: 1.5GB
Wireless: Broadcom 4318

Installs fine, sound works without a problem, wireless needs a little tweaking, follow this link, takes a few seconds and it works

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

umm beryl works on it, used 2 different links/articles to get it to work and used a fix for the white screen bug, but it works

---

### Post by lamalex on 2007-03-11
hp dv5139us, works great. 0 complaints about getting things working. I wish it didn't have ATi graphics but, what are you going to do. I was debating seeing if it had a discreet chip I could pull out and replace but it wasn't worth the trouble.

---

### Post by Snyper64 on 2007-03-12
Model: HP zv5000z
Ubunto: Edgy eft

Both internal and my external(Turtle Beach Audio Advantage Amigo) work perfectly fine(my laptop speakers actually sound better than they did in XP thanks to the Alsa drivers), touchpad works fine also but my MX310 doesn't want to use the auto scroll(I'll have to look this one up for a fix). Over all everyone of my onboard components work, my only real complaint is I can't get my second monitor to work.

Edit: Nevermind, my built in card reader doesn't work, but I have gotten my second monitor to work(sort of) and my auto scroll works now that i checked use autoscroll in Firefox. Also I have yet to test my WiFi card so i do not know if that works.

---

### Post by amanjsingh on 2007-03-13
> **mikewhatever said:**
> HP Pavilion 5000, core2duo, nvidia 7400 go.
Four things did not work:
1. Wireless Intel3945. Had to install linux restricted modules.
2. Microphone. Had to install the newer alsa driver.
3. Direct rendering. Had to reinstall nvidia driver.
4. An error is displayed on boot, but no idea what is it related to.


[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2


On my machine, this error comes right after it says Loading Kernel.......

Also, Live CD works fine, (though shows this error) but when I install Ubuntu on HDD, it directly goes to Shell (command prompt) and never boots to GUI. X11 seems missing EVERYTIME.

I am tired of this. I have the same HP laptop...DV5118TX. Please help. I tried Gentoo also but same errors with that linux distro.

Thanks
AJ

---

### Post by Ender Black on 2007-03-23
Laptop: dv9000
Proc: Intel Centrino Duo 1.66Ghz
Mem: 2 GB
Video: Nvidia GeForce Go 7600 (256Mb)
OS: Ubuntu 6.10 (Edgy Eft)

Microphone and Sound - Working after manually compiling and installing alsa 1.0.13
Touchpad:  Working
Video:  I wish I can remember which fix fixed it, but I have the up to date propiertary graphics driver from nvidia and it works
Webcam: not working
Wireless: Working

The only thing keeping XP on my laptop is Zune Software requires MS XP.... they made such a good media player why did they have to lock it down wose than Apple?

Oh, and my Ubuntu is playing Eve Online with all the bells and whistles

---

### Post by dustrho on 2007-04-11
**_COMPUTER_**
Processor: Intel(R) Pentium(R) 4 CPU 2.80GHz
Memory:	515MB (154MB used)
Operating System: Ubuntu 6.10
Date/Time	04/11/07 / 10:14

**_DISPLAY_**
Resolution: 1440x900 pixels
OpenGL Renderer: Mesa GLX Indirect
X11 Vendor: The X.Org Foundation

**_PCI DEVICES_**
VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600]
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller

I was able to get everything working out of the box except the wireless networking and the built-in memory card reader. I used [these instructions]("http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306") to get the wireless working without a hitch, but now I'm still having problems getting the built-in memory card reader working. I'd really like to get that working for the two digital cameras I have at the moment. Otherwise it wasn't too much effort getting Linux running on this old laptop of mine.

---

### Post by hgordon on 2007-04-12
Compaq Presario C508US -
7.04 Feisty

Everything works except 802.11.  
Screen resolution limited to 1024x768, and it's a bit fuzzy
$450 after rebate from Circuit City (worth every penny if I can get wireless going)

=================
update - got screen resolution running 1280x800 using "sudo apt-get install 915resolution"  -  nice !!!

wireless works now - the correct driver is bcmwl5, as bcmwl6 is a Vista driver, and it doesn't work with ndiswrapper

also, found out how to control the Synaptics touchpad's behavior by adding 
   Option "VertScrollDelta" "0"
   Option "HorizScrollDelta" "0"
   Option "MaxTapTime" "0"
to the Synaptics section of /etc/X11/xorg.conf

---

### Post by jml on 2007-04-12
HP Compaq nx6110
Celeron m processor
768 megs RAM
40 gig HD
Broadcom 4310 wireless
Intel "accelerated" graphics using shared memory

Except for wireless, everything worked out of the box, including accelerated graphics (planet penguin racer worked just fine!)  Initially could not get the Broadcom wireless card to work, so I used an Atheros based PCMCIA card with good results.  Finally got the Broadcom card to work with Debian Etch plus bcm43xx-fwcutter.  Since the 6110 is my "serious work" laptop at home, the more conservative nature of Debian Etch is a better fit for that box.  I still use Ubuntu 6.10 on my Darter and it works well.

Joe

---

### Post by tuxGeek on 2007-04-20
Hey guys, I was looking at Ubuntu as a possible distro for my laptop. I really have the need to use linux on it, but the last distro I tried, Fedora Core 6, did not work with the wireless card at all. I was wondering if anyone here, uses the same or similiar laptop and can get the wireless card working. Here is my system:

HP Pavilion ZE5732QV
Mobile Intel Pentium 4 processor 2.3GHz 533MHz
ATI MOBILITY RADEON 4X AGP and 3D architecture (more specifically, Radeon 345m, or something to that effect)
54g Integrated 802.11 b/g Capable Wireless LAN: Broadcom 43xx (don't recall the exact model at the moment)

Pretty much the only thing that is keeping linux off of it is the wireless card. I tried numerous things when I tried with FC6, but it never worked. If anyone has this, or similar, it would be a great help. I'm not sure if other distros would act the same way, but I'm going to give Ubuntu a shot and see.

Thanks!!

---

### Post by zub on 2007-04-20
As recently written in a recent post: 

Feisty amd64 Desktop
hp pavilion dv6156eu
AMD rution 64 x2
1 Gig RAM
120 Gig HD
nvidia GeForce go 7200, 256 mb memory cache
integrated webcam 1,3 megapixels (Ricoh)
Broadcom WLAN (bcm43xx)
soudcard: SnD-HDA-NVIDIA

* mode live cd: I remain stuck at login brown screen without seeing the login window, with same short sequence of sound being repeated;
* mode live cd: unable to load broadcom driver.

Experienced the laptop with Mepis 6.5, and got the broadcom driver working; sound was ok and all this in live cd mode which let me enter the system to test it.

yours
zub

---

### Post by FrancoNero on 2007-04-20
Feisty
hp nx7400, core2duo, 1gb ram

everything seems to work fine.
the most and major annoyance is that i dont have keyboard or touchpad upon return from suspend/hibernate. seems to be a very common problem/annoyance. i hope they release a fix, else i will have to stop using feisty right away, as i rely on that heavily. can't be that this isn't working....
also, lots of things just look worse in ubuntu than on windows, for example Facebook toolbar for Firefox, fonts, etc

also, desktop effects not working out of the box....

---

### Post by constantine on 2007-04-21
Hp dv2028ea 
Nvidia 
Chipset Model	C51 PCI Express Bridge
NVIDIA GeForce Go 6150
AMD turion64 x2
Conexant High Definition Audio
Broadcom 4310 

wi-fi card work after long work with Ndiswrapper 
soundcard not working , though it was working from live cd and after installation :confused: 
which is the first time it happened with Ubuntu !!
Any suggestions 
thanks

---

### Post by dustrho on 2007-04-21
Well, I decided to wipe my laptop clean (HP Pavilion zd7020) and start with a fresh install of Feisty, and now the wireless doesn't and the screen resolution is 1280x800. I've done all the tricks I previously did to get it to work in Edgy to no avail. I spent almost two hours trying to get these working, and not a damn thing wanted to work for me. Really irks me. :mad:

---

### Post by kitts_82 on 2007-04-21
Model: v3149au
CPU: AMD Turion X2 TL-52
Video: nVidia Go 6150
Memory: 1GB
Wireless: broadcom 4310

Everything worked except wireless. blacklisting the bcm43xx was important or the system would often hang. Wireless works with ndiswrapper > 1.30

Model: tx1003au
CPU: AMD Turion X2 TL-52
Video: nVidia Go 6150
Memory: 1GB
Wireless: broadcom 4310
Touchscreen: eGalax

Live cd will not boot because of bcm43xx. Had to enter single user mode, unload the bcm43xx module and continue booting. Wireless works with ndiswrapper. Touchscreen works but is grossly miscalculated.

Sound does not work. The mute button glows in red. system thinks sound works but there is no audio output except for the system bell in konsole. :(

---

### Post by teh.element on 2007-04-30
MODEL:       HP DV9000t
CPU:           1.83GHz Core 2 Duo
RAM:           2Gb RAM
VIDEO:        NVIDIA 7600 Go
INPUT:        Synaptics Touchpad
AUDIO:       Conexant High Definition Audio
NETWORK: Wireless/Gigabit
OTHER:      Webcam
                   Microphones
OS:             Ubuntu 7.04 Feisty/Windows XP/Windows XP Embedded (For playing DVDs only)

Probably one of the most compatible laptops, everything but microphone and webcam worked out-of-the-box. I have heard stories of getting them working. There is an awesome Synaptics touchpad driver that you can d/l through repos. The newest NVIDIA Driver has almost the same functionality that WinXP has and when I wined Steam, CS1.6 worked without the slightest problems.

Headphones now auto-detect heaphone input switching to headphone jack when they are inserted and muting audio from the speakers!

---

### Post by A. J. Rimmer on 2007-05-01
HP Pavilion dv5220us with T2050 Core Duo.  

Most everything works with the usual exceptions:

Had to install 915Resolution to get 1280x800.

Sound out works OK but not very loud; mic in does not work unless I boot into Windows XP first then do a Restart (not shutdown and then start).  By the way, I use my laptop to run several sound-card based Amateur Radio programs (FLDIGI in particular), so I just bought an external USB sound card, which works fine.

Intel WiFi adapter works perfectly.

Touchpad is OK, just had to "detune" the sensitivity a bit.

I did install the 686 kernel which I believe improved performance.

Edit: Oh, yeah, the TI card reader does not work, as reported by many others.

Edit Edit.  Oops, forgot to mention the internal modem not working, also.  Since I only have dial-up Internet access, I use a Bluetooth modem and USB-to-Bluetooth adapter.

---

### Post by neuromancer on 2007-05-02
Model: Pavilion ZE4453EA
Ubuntu: Feisty Fawn
CPU: AMD Athlon-XP 2500+
Video: ATI Radeon IGP 320m
Memory: 512MB
Wireless: Intersil Prism 2.5 Wavelan
Sound: ALi M5451

Everything works except that damn (win)modem.

I blacklisted orinoco, orinoco_pci and prism2_pci in order to use the hostap_pci driver, but I think wireless works with orinoco or wlan-ng (prism2_pci) drivers too.

---

### Post by aubre on 2007-05-02
> **jml said:**
> HP Compaq nx6110
Celeron m processor
768 megs RAM
40 gig HD
Broadcom 4310 wireless
Intel "accelerated" graphics using shared memory

Except for wireless, everything worked out of the box, including accelerated graphics (planet penguin racer worked just fine!)  Initially could not get the Broadcom wireless card to work, so I used an Atheros based PCMCIA card with good results.  Finally got the Broadcom card to work with Debian Etch plus bcm43xx-fwcutter.  Since the 6110 is my "serious work" laptop at home, the more conservative nature of Debian Etch is a better fit for that box.  I still use Ubuntu 6.10 on my Darter and it works well.

Joe

I have this same laptop but with 2GB RAM. Feisty works great, all I had to do to get the wireless working was to install bcm43xx-fwcutter. Boom - it just works. I've tried it with an unsecured and a WPA-TPIK setup and both worked fine. I am very happy! Ubuntu is so much snappier on this than XP ever was.

---

### Post by sagui on 2007-05-02
DV6275us


Everything I tested (everything but modem and multicard reader) works under Feisty (not so in Edgy) including the nvidia driver, headphones, wireless networking and webcam.  

There is only one exception:  the Expresscard slot.  Have any of you guys get it working yet?

---

### Post by linux_author on 2007-05-02
HP L2000 (Lance Armstrong edition)... AMD Turion64 running Edgy...

memory card reader slots (MMC driver) do not work... ATI 200 was enabled by Envy, but graphics are SLLLLLOOOOOOOOWWWW (but still better than the previously dismal 2D performance)...

but WHY OH WHY doesn't Ubuntu include ndiswrapper-utils on the desktop iso??? WHY WHY WHY??!!!

life would have be *so* much easier during an install for use Broadcom-hobbled notebook users!

:-(

p.s. don't get me wrong:  i'm VERY happy with 6.10 on my notebook... VERY pleased... (thanks to all the developers; let me know where to send the case of virtual beer)...

---

### Post by theonlykman on 2007-05-03
Model: Presario v3000t
Ubuntu: Feisty
CPU: Core Duo 1.6 Ghz w/ embedded graphics
Memory: 1GB
Wireless: IPW 3945
Sound: Intel 82801G (ICH7 Family) HD

Did anybody else get burned with that Vongo installer fiasco? I actually thank HP for it since it was a factor that helped push me to finally install a linux distro, and thus expose me to ubuntu.

Only one hiccup with my system...I have terrible sound quality through headphones. At the same volume settings (maxed out) I can plug in a pair of desktop speakers and they sound great, but if I use headphones its complete static. I know the headphones work in windows. Does anybody else with similar specs have a similar issue? I wouldnt mind the static, its just to get clear audible sound, I have to turn the volume down so far to where its almost pointless to use headphones. This is the only problem that has remained persistent through numerous reinstallations of feisty.
Thanks for ideas

---

### Post by reacocard on 2007-05-08
HP dv4000
Pentium M 1.7 Ghz
1GB RAM
Intel 2200 b/g wi-fi
Intel i915 graphics

Works perfectly. Breezy, Dapper, Edgy and Feisty have all run flawlessly without any extra configuration.

---

### Post by renim on 2007-05-08
Model: Compaq Presario V3000Z
Ubuntu 7.04
CPU: AMD Turion64 X2 TL 50
Memory: 2GB
Wireless: Broadcom 4311
Sound: nVidia Corporation MCP51 High Definition Audio (rev a2)

Almost everything other than the wireless and the headphone worked out of the box. [Some people]("http://ubuntuforums.org/showthread.php?t=416234") have had trouble with the audio but atleast for me it works just fine. 
Update: Ok, the sound worked fine for 2 days and now there is no sound...tried upgrading to alsa 1.4 but didn't fix it.

Enabling the wifi with ndiswrapper wasnt too tough either. The wiki[(link)]("http://hpwiki.cactii.net/hpwiki/Presario_V3***") explains what needs to be done and within 10-15 minutes the wireless should be up and running including WPA. :)

---

### Post by Grungydan on 2007-05-08
MODEL: HP DV9000t
CPU: 2.00GHz Core 2 Duo
RAM: 2Gb RAM
VIDEO: NVIDIA 7600 Go
INPUT: Synaptics Touchpad
AUDIO: Conexant High Definition Audio
NETWORK: Wireless/Gigabit
OTHER: Webcam
Microphone
OSs: Ubuntu 7.04 Feisty/Windows XP Professional

Still haven't gotten the webcam working (after spending about 2 hours poking around for drivers, etc).
Haven't tested the microphone, but I don't expect it to work either, so there will be another hunt for that. 
Haven't used headphones since installing Feisty, so I don't know if it auto mutes or not.  (Update:  it automutes and feeds sound correctly, I didn't have to do anything extra.  Wheee!)
The volume control is "loose", when I use the buttons to turn it up and down, the jumps seem very arbitrary, and at the high end it goes from "too quiet" to "full volume" in one or two clicks.  Also, I lose sound at about 1/4 "volume", instead of a gradual reduction in volume.  Hopefully I'll find something that fixes that up.
Also, the battery life monitor seems to get confused easily.  I plan to calbrate the battery soon, hopefully that will fix it.

All in all, loving Ubuntu, but I just haven't gotten much time with my personal machine to do any fixing and poking around.  :(

(Thanks to teh.element for providing a template for the machine. ;))

---

### Post by jxb on 2007-06-14
> **jml said:**
> HP Compaq nx6110
Celeron m processor
768 megs RAM
40 gig HD
Broadcom 4310 wireless
Intel "accelerated" graphics using shared memory

Except for wireless, everything worked out of the box, including accelerated graphics (planet penguin racer worked just fine!)  Initially could not get the Broadcom wireless card to work, so I used an Atheros based PCMCIA card with good results.  Finally got the Broadcom card to work with Debian Etch plus bcm43xx-fwcutter.  Since the 6110 is my "serious work" laptop at home, the more conservative nature of Debian Etch is a better fit for that box.  I still use Ubuntu 6.10 on my Darter and it works well.

Joe

i have the same one, can you tell me what graphic driver you are using?

---

### Post by rajivrajagopal on 2007-07-20
hi kitts_82 which ubuntu u r using ? i am not able 2 install.please help me.

---

### Post by rajivrajagopal on 2007-07-20
i am using tx1003au..

---

### Post by Bablefish on 2007-07-20
My Nc6000 works fine

---

### Post by #Reistlehr- on 2007-07-20
If you have an intel processor, use the normal (i386) image. If you have an AMD processor, (like a turion64 x2), use the AMD64 Alternative image.

---

### Post by lamegaptop on 2007-07-20
Been running 7.04 since 04/07. The laptop worked great on first boot. Been tweaking since then and it cranks. The SMP Kernel made a difference and of course the proprietary nVidia driver. 

No kernel parameters needed here.

Working-
root@rb-laptop:/usr/src# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

Not working is my Audigy 2 ZS Notebook pcmcia sound card. Rats. Thanks Creative.
Wine/Steam/HL2 work great. Awaiting episode two.

---

### Post by buntunub on 2007-07-21
hp dv2415us
amd turionx2
2G ram

What worked out of the box:

Everthing except -

*with some tweaking now works:

-wireless thanks to ndiswrapper. Also, great wireless WPA guide this forum to get that up and running nicely.
-scrollpad
-DVD playback (had to really wrestle with that one as the usual tricks did not work)
-Sound. There is a bug with ALSA for these models where you must do some very strange things to get it to work (load latest drivers, put into hibernate, take back out, then reboot without power chord in). If you boot into a dual-boot windows and try to boot back into ubuntu, you wont have sound anymore btw.

What does not work -- at all -- after following all available guides via google -

Sonix Microdia builtin usb2.0 webcam (0c45:62c0). Contrary to the one or two "hey this works in Ekiga!" reports, this webcam does NOT work in uvc for the vast majority out there. Ive heard however, that if you hold the laptop with your left hand while standing on your head, and bark at the full moon -- it works in linux! The drivers are non-functional due to some freaky internal usb setup change between the dv2000's and the later models.

built-in mic's. See above webcam issues.

Overall, the Buntu's still have worlds to go to catch up to Mepis and PClos when it comes to the newer hardware detection/setups. This laptop runs mostly flawless in those distro's. Sabayon, as always, has no trouble at all on any new hardware ive thrown its way (not the webcam as it cant work in linux yet consistently).

---

### Post by A. J. Rimmer on 2007-07-29
Upgrading from Dapper to Edgy to Feisty on my dv5000-series (Centrino T2050 with Intel motherboard graphics and Intel wireless adapter) fixed a number of issues.

Sound volume out is now very good; previously was very low even at max.

Built-in card reader now works.

Video quality is much improved; previously many video files were too contrasty and no settings could be found that looked right.

The Generic kernel detects the dual processors.  Previously had to install the 686-SMP kernel to get the second core recognized.

Sound input is no longer "deaf," but sounds like heck.  Very tinny and compressed, no matter what settings I try.  Still using an external USB sound card for some applications.

One other VERY weird "problem."  Although all other sound out works fine, the login and logout sounds no longer play, no matter what settings I try.  Can't figure that one out, but it's no great loss. (EDIT: fixed this problem by deleting .asoundrc file and associated config file (both in ~ directory).  Found this solution somewhere on the Fourms -- sorry, I lost the link.)

---

### Post by vincentvee on 2007-08-16
yeah well everything works good with 7.04 on my omnibook xe3......BUT, does anyone know why the laptop speakers still work when i have a headset plugged in to the jack at the front??
if anyone knows, is it possible to fix this, and how would i do it?
tried everything i can think of

---

### Post by dansen926 on 2007-08-16
Model: Dv6500t CTO
Ubuntu: Fiesty Fawn (Kubuntu 7.04)
CPU: Intel Core2 Duo 2.0 GHz T7300
Video: nVidia Geforce 8400 GS
Memory: 2GB
Wireless: Intel PROWireless 3945ABG
Sound: Hewlett-Packard Company HD Audio Controller
Optical Drive: MATSHITA DVD-RAM UJ-851S

GUI install would not work due to video hardware/driver problems. Used alternate, text-based install, selecting VESA drivers as a temporary workaround. Then I installed and ran the envy script which downloads and updates drivers direct from nVidia or ATI. It also updated my xconf for me, which was nice :)

Sound didn't work at first, but I found a workaround thanks to [l-fever]("http://ubuntuforums.org/member.php?u=324798"):
*Note: This involves installing ALSA drivers from source code*
> Basically go to [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and follow the part where it says to download the latest version of alsa-driver, alsa-lib, and alsa-utils.

Go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104") and download realtek10.tar.gz.
Extract to ../alsa-driver-1.0.14/alsa-kernel/pci/hda/

Follow the compile part of [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

Reboot

Edit /etc/modprobe.d/alsa-base and insert "options snd-hda-intel model=toshiba" at the end of the file.

Reboot again. la

It should work at this point. It did for me anyways. Good luck!

The last major problem I've found with the hardware was the DVD-RW Drive. I can't get this thing to mount for anything yet! I've been working on it for awhile, and from what I can tell the DVD Drive is on an IDE Bus and linux loads the IDE Bus but for some reason misses the Drive. Still working on it :mad:

---

### Post by dansen926 on 2007-08-16
I don't know if my fix will work for you, but I suggest opening KMix (if you use Kubuntu) or your Mixer console. On my KMix, there are green...buttons for lack of a better word over the sliders. Notice how both green buttons are lit. I clicked on the headphones button, it went dark, and that's how I isolated my audio to one track.

---

### Post by FuturePilot on 2007-08-16
HP Pavilion dv6500t
Intel Centrino Duo
2GB RAM
Intel HD sound card
Nvidia 8400 GS
160GB hard drive
Yes it works, but it took some effort to get it working. I needed the all_generic_ide kernel parameter to get the live CD to boot or else I got dumped into Busybox with cannot access tty. My Nvidia card wasn't detected by the Restricted Manager so I had to use Envy. No big deal it works now. I didn't have any sound and I had to compile the latest alsa drivers along with a Realtek patch to get the audio working. Suspend doesn't work right, but it seems to be a common thing with laptops. I'm still getting this PCI: Failed to allocate mem resource #6 error at boot up but it doesn't seem to be affecting anything. Haven't tested out the wireless yet, but the Restricted Manager detected it and installed the drivers for it.

@dansen926
I'm not sure what could be wrong with your CD drive. Mine seems to mount CDs fine:confused:

---

### Post by EXCiD3 on 2007-08-16
Has any messed around with Gutsy much yet? I booted into the live CD and found my Intel Pro/Wireless 3945 to be unusable by default. The 3945 drivers are automatically taken care of by the Restricted Drivers Manager in Feisty and Gutsy. It works perfect in Feisty, however, in Gutsy wireless IS enabled, but it cannot find any wireless networks. I tried updating my Feisty kernel to Gutsy's kernel also and it wouldn't work with it either. Anyone else having the same problem?

---

### Post by #Reistlehr- on 2007-08-16
well my Broadcom 4310 still doesn't work by default.

---

### Post by EXCiD3 on 2007-08-16
> **#Reistlehr- said:**
> well my Broadcom 4310 still doesn't work by default.

Yeah, i figured that, but I was wondering if anyone with an Intel 3945 card had tried Gutsy and gotten their Intel 3945 card to work, since it works by default in Feisty, i assumed it would in Gutsy but something broken between kernels apparently...

---

### Post by kitsuneofdoom on 2007-08-17
My touchpad stopped working right (the scrollbar stops working), programs started to crash oddly, especially firefox, the CD-ROM driver got fickle, hald-storage-addon started stealing cycles, and now usb mice stop working randomly and lsusb hangs.

dv5000 with a turion 64 and ATI 200M (using the open source default drivers) and using Feisty 32 bit. The errors only started with Feisty

---

### Post by deridex on 2007-08-17
Hi,

I have a HP/Compaq NX7300 (GB904ET) wich acctualy is working great!
Although the wireless needed some fixing with ndiswrapper..
Using dualboot with Win XP and Im acctualy thinking about getting rid of the Microsoft virus.. ;)

//deridex

---

### Post by A. J. Rimmer on 2007-08-18
"does anyone know why the laptop speakers still work when i have a headset plugged in to the jack at the front??"

Have you checked all the settings in alsamixer?  Mine has several settings that I never expected to find, including things like mike bypass, and there is at least one for which I have never figured out the function.  There might be a speaker bypass that can be enabled, don't know, just guessing.

---

### Post by EXCiD3 on 2007-08-18
> **A. J. Rimmer said:**
> "does anyone know why the laptop speakers still work when i have a headset plugged in to the jack at the front??"

Have you checked all the settings in alsamixer?  Mine has several settings that I never expected to find, including things like mike bypass, and there is at least one for which I have never figured out the function.  There might be a speaker bypass that can be enabled, don't know, just guessing.

I think that this was just a problem of having an older version of ALSA, since the repositories don't always have up-to-date software. You might try that.

---

### Post by dansen926 on 2007-08-18
Simple fix for my DVD-RW drive: add "all_generic_ide" to the end of the kernel parameters in the bootloader :)

---

### Post by vincentvee on 2007-08-19
there's not.....seems to be aproblem with HP only........my xe3 is still doing it and i've been working on this problem for three days
if anyone knows a way to fix it, please email me

> **A. J. Rimmer said:**
> "does anyone know why the laptop speakers still work when i have a headset plugged in to the jack at the front??"

Have you checked all the settings in alsamixer?  Mine has several settings that I never expected to find, including things like mike bypass, and there is at least one for which I have never figured out the function.  There might be a speaker bypass that can be enabled, don't know, just guessing.

---

### Post by Alex Fernandez on 2007-08-19
NX6325 (Turion X2 x86_64 with ATi Radeon XPress 200M)

Works like a charm :)

---

### Post by Jukka-Pekka on 2007-08-19
Model: nc8430
Ubuntu: Feisty Fawn ( trying out Gutsy Gibbon)
CPU: Intel Core2Duo T7200
Video: ATI Mobility Radeon X1600
Memory: 2GB
Wireless: Broadcom 4311

My Feisty experiences with this nice laptop:

Video working somehow, but slow and X-window crashes often. No "advanced desktop effects". Native resolution of 1680x1050 was not recognized before editing xorg.conf etc. Excessively difficult and lengthy setup for a linux n00b like me. Well, i learned a lot of unnecessary stuff (for the future, i hope :) )
WLAN works somehow with ndiswrapper but disconnects often. Setup was excessively difficult.
Sound is working perfectly.
CD/DVD combo is working perfectly both reading and writing both cd's and dvd's.
Bluetooth and USB memory-sticks are working perfectly.
Integrated SD-card reader is working properly.
Terratec Cinergy DT USB XS Diversity TV-tuner is not working at all, have not figured that out yet. Probably needs some drivers etc "tuning".

Power management works only partially, a lot more heat and fan noise (and, therefore, a lot less battery time) than in WinXP. CPU voltage regulation with low loads is perhaps not working properly? The GHz steppings go between 1GHz and 2 GHz which is correct for my processor.

Jukka

---

### Post by mridkash on 2007-08-19
HP Compaq Presario V3000
80 Gb HDD
1.5 Gb RAM
Intel Graphics, onboard
Ubuntu Studio

Everything working fine now. 
Sound didn't work when I first installed ubuntu, but after compiling the new version of ALSA driver, it works and works well. Mic, speaker, headphone, quickplay buttons, usb mouse, sd card, LAN works fine.

---

### Post by vincentvee on 2007-08-19
when you plug in the headphone do the laptop speakers mute??


> **mridkash said:**
> HP Compaq Presario V3000
80 Gb HDD
1.5 Gb RAM
Intel Graphics, onboard
Ubuntu Studio

Everything working fine now. 
Sound didn't work when I first installed ubuntu, but after compiling the new version of ALSA driver, it works and works well. Mic, speaker, headphone, quickplay buttons, usb mouse, sd card, LAN works fine.

---

### Post by FuturePilot on 2007-08-20
The only other small issue I have with my dv6500 is that when you plug in the headphones sound still comes out of the built in speakers and they have to be manually muted. No big deal, the headphone jack at least works.:)

---

### Post by EXCiD3 on 2007-08-20
Hopefully this will be fixed in a new version of ALSA...

---

### Post by ronthedon on 2007-08-20
Hey guys,
got myself a new hp dv2530ee

configs are:
1024MB RAM
Centrino duo 2.0 Ghz
NVIDIA Go 7400M

Everything seems to be working in order, even the remote. The only problem I faced was the NVIDIA graphics driver. No matter what i do, I still get 800 x 600 resolution.  I installed the nvidia-glx driver, No cigar! 

Not only tht, it took me some time to actually boot into ubuntu-live, had to enable the piix module to do that.  Since I hate VISTA so much.. I decided to go with other distros, I tried fedora and suse, both gave me some query about where to find the IDE driver, or something.  Have no idea how to fix this thing, any help would be appreciated

---

### Post by EXCiD3 on 2007-08-20
I recently installed Gutsy and have not been able to get my Intel 3945 drivers to work. Does anyone know how to fix this?

---

### Post by mgont on 2007-08-20
I am new to ubuntu, coming from Vista.  Anyways, I have an HP Pavillion DV9230US laptop and the only thing that doesn't work right off the bat is my video.  Well, it displays at 1024xwhatever, but in vista, it goes to 1440x900.  Can somebody please take a little bit of time and tell me exactly how to get the drivers set up and the commands to get it going?  Thanks.  By the way, it's an nVidia GeForce Go 7600

---

### Post by EXCiD3 on 2007-08-20
> **mgont said:**
> I am new to ubuntu, coming from Vista.  Anyways, I have an HP Pavillion DV9230US laptop and the only thing that doesn't work right off the bat is my video.  Well, it displays at 1024xwhatever, but in vista, it goes to 1440x900.  Can somebody please take a little bit of time and tell me exactly how to get the drivers set up and the commands to get it going?  Thanks.  By the way, it's an nVidia GeForce Go 7600

Its covered in this thread: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by vincentvee on 2007-08-21
damn....i have no way of manually muting mine

> **FuturePilot said:**
> The only other small issue I have with my dv6500 is that when you plug in the headphones sound still comes out of the built in speakers and they have to be manually muted. No big deal, the headphone jack at least works.:)

---

### Post by ronthedon on 2007-08-21
> **vincentvee said:**
> damn....i have no way of manually muting mine
Have u tried downloading Alsamixergui? It worked on my HP dekstop which had the same problem

---

### Post by FuturePilot on 2007-08-21
> **vincentvee said:**
> damn....i have no way of manually muting mine

Have you tried the mixer under Applications>Sound&Video>Volume Control
If it's not there you might have to enable it in the Menu Editor.

---

### Post by Charlied105 on 2007-08-21
Model: dv2415nr
Ubuntu: Feisty 7.04
CPU: AMD Turion64 x2
Video: nvidia Go 6150
Memory: 1GB
Wireless: Broadcom 4311

Cannot successfully get the WLAN adapter to work

---

### Post by A3sthetix on 2007-08-21
Model: dv6402ca
Ubuntu: Feisty 7.04 (Ubuntu Studio)
CPU: AMD Turion64 x2 TK-53
Video: nVidia Go 6150
Memory: 1.5 GB
Wireless: ?? (Broadcom)

I'm still working on the wireless. The initial 3 installs did not work. I finally got it going through Wubi. I had to use special parameters when booting up:
```
nosmp noirqpoll noapic noapci nolapic
```

After that, edited the boot options. Audio and ethernet are working fine. I still need to get my graphic card going along with the WLAN. 

It's quite a battle... ](*,)

---

### Post by EXCiD3 on 2007-08-21
Use envy to install the video card driver, at least that is simple and straightforward.
 
Also try this for installing your broadcom driver: [http://ubuntuforums.org/showpost.php?p=3218583&postcount=7](http://ubuntuforums.org/showpost.php?p=3218583&postcount=7)

---

### Post by vincentvee on 2007-08-22
tried that, muted PCspeakers, but they still worked after i did it........really is quite annoying cause i work at night and need sound, but my wife and kids are sleeping and it wakes them up
anyways......i'll keep working at it

> **ronthedon said:**
> Have u tried downloading Alsamixergui? It worked on my HP dekstop which had the same problem

---

### Post by vincentvee on 2007-08-22
:) got it working doing that, also now running amarok, which i think might have made a difference over rhythmbox but dunno why
thanks heaps for all the input everyone, and in the end it was a simple solution too
i wonder why it didn't work doint the same thing through accessing the volume control through the icon on the panel??

> **FuturePilot said:**
> Have you tried the mixer under Applications>Sound&Video>Volume Control
If it's not there you might have to enable it in the Menu Editor.

---

### Post by agntsmyth on 2007-08-30
Model: dv6000z
Ubuntu: Feisty 7.04 
CPU: 2.0ghz AMD Turion64x2
Video: Nvidia 6*** (idk but it worked on install mostly)
Memory: 2GB
Wireless: Broadcom 4310
Sound: conextant (also worked out of box)

Desktop Effects always blanks my screen out and requires a ctrl+alt+backspace. wireless broadcom worked with install script i found on forums.  DVD player keeps reporting an error reading from the device (I cant find this problem on the forum so far anyone know what is up? so far I've only tried the ubuntu live cd a music cd and two  unencrypted(?) movies in it, both cds worked.)

---

### Post by #Reistlehr- on 2007-08-30
does the wireless start on boot?

think you can grab a link for the wireless script for future reference?

---

### Post by A. J. Rimmer on 2007-08-30
> **mikewhatever said:**
> HP Pavilion 5000, core2duo, nvidia 7400 go.
Four things did not work:
 ...
4. An error is displayed on boot, but no idea what is it related to.

I got the same error messages on my dv5220us while running Dapper, but now that I have upgraded to Feisty they have gone away.  By the way, if you run lspci and compare the output with the error messages you will get some insight into what hardware they are referring to.

Never did get my microphone working with Dapper, but it does work (sort of) under Feisty, except that the recorded audio is very distorted.  I have some applications where I need sound in, so I just went with a 24 bit USB sound card.

[Oops, sorry folks, it appears that I just fell through a time warp and replied to a six-month-old post.  Don't know how I got so lost in the thread.]

---

### Post by rrob100 on 2007-08-30
This laptop works very well under Feisty the only area I haven't tested is using the microphone input for sound recording here are the main details of this machine.
    * Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
    * ATI Technologies Inc M56P [Radeon Mobility X1600]
    * Texas Instruments PCIxx12 Cardbus Controller
    * Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
    * Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    * Texas Instruments PCIxx12 GemCore based SmartCard controller
    * Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express
    * Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

I recommend this website [http://fp.ath.cx/nc8430-linux-howto.html](http://fp.ath.cx/nc8430-linux-howto.html) which provided a straight forward 'how to' for this laptop.

---

### Post by Old *ix Geek on 2007-08-30
HP Pavilion dv6000z:

    * Mobile AMD Sempron(TM) 3500+ (1.80GHz/512KB)
    * 15.4" WXGA BrightView Widescreen (1280x800)
    * NVIDIA(R) GeForce(R) Go 6150 w/Productivity Ports
    * HP Imprint Finish + Microphone
    * 1GB DDR2 System Memory (2 Dimm)
    * 120GB 5400RPM
    * 8X DVD+/-R/RW w/Double Layer Support
    * 802.11b/g WLAN
    * 6 Cell Lithium Ion Battery
    * Network controller: Broadcom Corporation 4311
    * FireWire (IEEE 1394): Ricoh Co Ltd 0832

What works: Everything *I* need: Wireless (even with the dreaded Broadcom 4311...); Samba; printing (local and network); audio; video (including DVDs); USB thumb drives; USB camera connection; Compiz-Fusion (after some tinkering with NVidia); wine (for the few windoze games I play, most notably Roller Coaster Tycoon); etc.

What doesn't work: Nothing that I've tried!  I have not tried using the microphone, so I can't say whether or not it works.

Overall: After some initial tweaking, I love this laptop.  I had some problems getting its wireless to work because of that Broadcom 4311 card, but since I did it's been great.  I recommend this laptop as a relatively low cost, Ubuntu-friendly machine, if one is willing to put a little initial work into getting things up and running.

---

### Post by Offoffoff on 2007-08-31
HP Compaq NC4000  
Everything works fine excluding native irda hp hsdl-3600, modem ALi Corporation M5457 AC'97 Modem Controller. And cannot get direct rendering with my ATI videocard....
Here is my lspci output:
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
00:0b.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:0b.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 USB Controller: NEC Corporation USB (rev 43)
00:12.1 USB Controller: NEC Corporation USB (rev 43)
00:12.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:13.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 03)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

---

### Post by j4ck455 on 2008-03-20
> **deridex said:**
> Hi,

I have a HP/Compaq NX7300 (GB904ET) wich acctualy is working great!
Although the wireless needed some fixing with ndiswrapper..
Using dualboot with Win XP and Im acctualy thinking about getting rid of the Microsoft virus.. ;)

//deridexIs the mic on your nx7300 working in 7.04? - my nx7300's mic is not working in 7.10 :(.

---

### Post by mkarnicki on 2008-03-27
Model: tx1320us
Ubuntu: Hardy Heron (beta)
CPU: AMD Turion64 duo-core
Video: works out of the box (restricted drv)
Memory: 2GB
Wireless: works out of the box
Sound: works out of the box (including headphone jacks)
Touchscreen: seeking solution

---

### Post by rayzoredge on 2008-03-28
Model: zd8000
Ubuntu: Gutsy Gibbon
CPU: Pentium 4
Video: ATI X600 Mobility Radeon
Memory: 2GB
Wireless: Broadcom
Sound: Conexant and SB Live! 24-bit External

On fresh boot, I had to update everything and tweak with xorg.conf to get the proprietary video drivers to work with fglrx and for the wireless to pick up. Bluetooth is working, although right now I'm trying to install my Bluetooth-enabled printer (HP 3210) and it's giving me a "obex://[00:0c:55:f8:d9:f1] not a valid location" error.

---

### Post by blumagic on 2008-03-30
Model: HP Pavillion dv9700t
Dual Boot:
Ubuntu: Gutsy Gibbon
Windows Vista Home Premium
CPU: Intel Core Duo T7250 @ 2.00 GHz
Video: nVidia GeForce 8600 GS 512MB
System Memory: 3GB
Wireless: Broadcom 4965
Sound: Intel HDA
DVD writer/reader
Synaptics Touchpad
fingerprint reader
Integrated webcam: Ricoh
Integrated microphone

For me while I dont use it, the webcam isnt working or detected by Ekiga Sofphone.
I dont think the microphone is working either. The laptop will suspend and/or hibernate,
but it wont recover. Screen stays black and I have to force shutdown with power button.I
still havent tried to get fingerprint reader to work yet.System was very nstable(modprobe
and lsusb commands would hang)until I blacklisted the uvcvideo module.I had to install
backport modules to get sound working.Wireless worked right out of the box after 
configuration of router/wireless network information.So far, I have enjoyed my 
new laptop in both ubuntu and windows. I am also looking forward to upgrading 
to Hardy to see if has more support for the items that are not supported in 
Gutsy.I hope this will be a helpful thread for myself and others.

thanks,
blu.....

---

### Post by #Reistlehr- on 2008-03-30
I got my new dv9700z replacemnet today. Everything with it works flawlessly, minus the fingerprint reader (but they only added it to make me feel better).. and the wireless.. The Atheros 5007eg isn't recognized in HAL, so hpoefully that gets fixed. i want to be able to use it in monitor mode.

---

### Post by kc4mnp on 2008-03-31
run the new version of envy and reboot when prompt also yes to the prompts during the prompt about updating xorg file, works great at 1440x900 on my dv9230us! enjoy!

---

### Post by unMourned on 2008-04-26
Model: zd8000 (zd8230us)
Ubuntu: Hardy Heron
CPU: 3.4 GHz Intel Pentium 4 650 processor 
Video: ATI Radeon X600 
Memory: 2GB
Wireless: Broadcom Corporation BCM4318 [AirForce One 54g] 
Sound: 16-bit Sound Blaster Pro

I have 15 years of Windows experience and about 3 years of UNIX / AIX System Admin experience.  This is my first experience with Ubuntu--set it up as dual boot on my laptop with WinXP.  It seems...okay (Ubuntu, that is), but I'm still trying to get wireless working.  :(

---

### Post by pblanton on 2008-04-26
I have a dv9700t and hardy installed on it like it was made for it. No problems with networking, webcam, special function buttons, bluetooth, ... The installation was easier than any windows installation I ever did.

I posted the details here...

[http://ubuntuforums.org/showthread.php?t=686879](http://ubuntuforums.org/showthread.php?t=686879)

My only real issue was with Skype, which obviously doesn't support 64-bit Linux. Not a Ubuntu problem, but a problem nonetheless.

---

### Post by #Reistlehr- on 2008-04-26
Got a replacement laptop now, dv9700z, this thing is horrible. i hate it. I actually miss the original dv9000z. Almost every distro i put on it creates kernel panics, no matter what options i pass to grub (noapic, acpi=off, pnpbios=off, etc). I tried Debian, Ubuntu (7.04->8.04), Mandriva, SuSe, Fedora, Wolvix, DSL, and LFS as a last resort. I'm really disappointed, and im regretting buying an HP in the first place, if only i never had the motherboard die in the first place.

---

### Post by m61 on 2008-04-27
Model: dv8000 (dv8320ca)
Ubuntu: Hardy Heron
CPU: Intel Centrino Duo (each says 1.6GHz)
Video: Nvidia GeForce Go 7600
Memory: 1GB (i think, can't remember)
Wireless: Intel Pro Wireless (it's a centrino)

had some minor issues with wireless for hardy (gutsy and feisty never had issues) but it's working now.  also my media buttons don't work (haven't worked since gutsy).  when i push the buttons, the on-screen shows the proper event, and the volume control goes up and down or mute (as it should) but it has no effect on the sound, it's almost as if the Master doesn't control the PCM...

---

### Post by pblanton on 2008-04-27
That's a drag and I'm sorry to hear it.  Give HP a call and (yeah I know it will be a painful process) let them know your PC is not working. They support Linux whole-heartedly internally. Maybe they will get you a good fix.

I'd ask for an exchange for an Intel-based one.

It may be time to put Vista or XP on it and dump it on EBay.

---

### Post by #Reistlehr- on 2008-05-12
> **pblanton said:**
> It may be time to put Vista or XP on it and dump it on EBay.

Thats what i think im going to do. Either taht, or buy myself a new one, and pass it on to my father.

---

### Post by freakwillie on 2008-06-14
I have a Pavillion DV6768se here with a 64 bits Hardy. The wifi didn't work out of the box and it was a hard time finding a solution mainly because the Ubuntu 64 bits is poorly supported. 

I still can't seem to make the internal mic work in my Conexant CX20561 Hermosa soundcard. Havent tested the card reader yet. The GeForce Go 8400 gs worked out of the box though.

---

### Post by KemKev on 2008-06-14
Hello All:

I'm having some difficulty getting my integrated webcam working on my DV6000 with Hardy Heron 8.04.   

When I run "lsusb", I get the info below

Bus 002 Device 002: ID 050d:0845 Belkin Components 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

I then got the "r5u870-0.10.0.tgz" and after unpacking and running the "make" command, I get the following:

make -C /lib/modules/2.6.24-18-generic/build M=/home/colin/Desktop/r5u870-0.10.0 V=0 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/colin/Desktop/r5u870-0.10.0/r5u870_md.o

In file included from /home/colin/Desktop/r5u870-0.10.0/r5u870_md.c:55:
/home/colin/Desktop/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory

make[2]: *** [/home/colin/Desktop/r5u870-0.10.0/r5u870_md.o] Error 1

make[1]: *** [_module_/home/colin/Desktop/r5u870-0.10.0] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'

make: *** [all] Error 2

I've downloaded the file form different sources, but all the packages contain the same files, so I'm not sure why I'm getting all the errors. 

I've also tried to run Cheese and a few other apps to see if I could get the cam recognized, but no luck.

Any help would be greatly appreciated.  Thanks much.
[B]
Edited to add...[/B] Results from latest test:

colin@colin-laptop:~$ lsmod | grep videodev
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev

I came across a site that says the Linux headers changed names in Hardy, and so the compilation will only work on kernels up to 2.6.22.  Hardy is 2.6.24 :(  Is there a work around?

---

### Post by KemKev on 2008-06-14
> **unMourned said:**
> Model: zd8000 (zd8230us)
Ubuntu: Hardy Heron
CPU: 3.4 GHz Intel Pentium 4 650 processor 
Video: ATI Radeon X600 
Memory: 2GB
Wireless: Broadcom Corporation BCM4318 [AirForce One 54g] 
Sound: 16-bit Sound Blaster Pro

I have 15 years of Windows experience and about 3 years of UNIX / AIX System Admin experience.  This is my first experience with Ubuntu--set it up as dual boot on my laptop with WinXP.  It seems...okay (Ubuntu, that is), but I'm still trying to get wireless working.  :(
The wireless part was fairly easy.  Are you still having problems with it?

---

### Post by loudnlownoma on 2008-06-14
Model: zd8000 (zd8205us)
Ubuntu: Gutsy
CPU: 2.8 GHz Intel Pentium 4 processor
Video: ATI Radeon X600
Memory: 1GB
Wireless: Broadcom Corporation BCM4318 [AirForce One 54g]
Sound: 16-bit Sound Blaster Pro

Works like a charm with Gutsy - so much so I finally had to make a post a while back in the testimonials section of the site.  Wireless worked flawlessly after enabling the restricted driver in Gutsy.  Runs Compiz like a dream.  I think the only thing I haven't got working on it are some of the media buttons at the top, but mostly because I haven't tried to mess with them to see what they do now or how to configure them.  The volume and mute buttons do work properly though.

Having good luck on my desktop with Hardy, but I do use this pretty regularly and have it running pretty solid at the moment, so I'm not sure if I wanna try the upgrade yet or not...

---

