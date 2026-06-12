---
title: "Current quality of ATI Linux drivers?"
date: 2008-11-11
forum: Hardware
---

### Post by Drooling Iguana on 2008-11-11
I'm thinking of upgrading my video card soon. Up to this point I've stuck with NVidia cards since their Linux drivers, while closed-source, are fairly high quality and allow the card to work just as well in Linux as it does in Windows. I know that for a long time ATI's Linux drivers were pretty awful and only gave a fraction of their Windows performance, but I've heard that they've recently been open-sourced. Has this led to any improvements in the driver's quality yet or should I stick with NVidia?

---

### Post by Lord Xeb on 2008-11-11
My ATI drives are really good. I have good performance on it too. They have become better that what they once were. Then again I really have never had a problem with them :D

---

### Post by croddy on 2009-08-03
The current ATI drivers on Linux are still **absolute junk**, full of crash bugs, display bugs, and all kinds of nasty problems. You would not buy an ATI card intending to put it in a Linux box and use FGLRX. You would have to be ignorant or stupid or masochistic to do that.

FGLRX is more of a proof of concept that an ATI card can work on Linux under certain limited conditions. It's really not something you would choose for Linux; it's something you're stuck with and you might want to try to get it working. For example, you want to plug two monitors in? LOL, forget about it. You want to play back video smoothly? LOL, forget about it.

I've wasted enough time trying to support ATI's useless !@#$%&* garbage driver at work that we've decided to stop buying ATI. The Linux boxes here only account for about 2% of the total desktops, but because Nvidia's stuff is supportable both on Windows and Linux, and we like to keep everything the same so they're interchangeable, ATI just lost tens of thousands of dollars in card sales for Windows boxes because of the junk quality of their Linux driver. 

I really would like to see ATI make FGLRX something that I can install and configure in under four hours, every time, without repeatedly apologizing to the user who's going to suffer it. But ATI just don't seem to be capable of shipping a Linux driver that's not a worthless piece of utter ****.

---

### Post by Dave_Connor on 2009-08-03
Yeah same here; It was 2 distro updates before ATI FINALLY had support for my Radeon Xpress 200M on my Gateway laptop with 3-D support, etc. Works great now but for now Nvidia is MUCH more supported and stable then ATI cards, even more so with fglrx update that dumped support for a ton of cards that pissed alot of users off.

---

### Post by HavocXphere on 2009-08-03
Go with nvidia. ATI is trying, but on the whole ATI users seem to run into more problems on ubuntu *at the moment*.

Still trying to fix a flashing black box issue on my ati. :(

---

### Post by NormanFLinux on 2009-08-03
Your only choice is open source drivers. ATI will no longer write new drivers for legacy cards. That's about the best that can be done to support ATI graphics in Ubuntu.

---

### Post by MButterman on 2009-08-09
Reverting to 8.10 was my only option to support ATI but as a consequence my wireless card has issues. If I had educated myself a little more in purchasing hardware I would've avoided ATI. 

Currently I am looking into the Coreboot Project and a ASUS M2V-MX SE.  This should provide the compatability to a wide range of OS choices. 

I like Nvidia as well and I can relate to the frustration of ATI configuration as opposed to the simplicity of an Nvidia one.

The lesson learned is to understand the hardware you intend to use and how it will interact with the OS. I seen so many people grab just any hardware and expect it to work. In the Windows world that might be valid but you have to give some thought to LInux to see the best results

---

### Post by ~dr,j on 2009-08-10
hey all~
i agree w/most of the people posting in this thread. while the new ATI driver has made forward progress, it's performance is still lacking in many areas (my worse is trying a video heavy app like say Google Earth while using the ATI graphic driver....it's all choppy till i drop down to the none proprietary [generic] driver then it works smooth.)

as much as i love amd (who own's ATI) i'd say stick w/nVidia if possible (sadly for me, my laptop has an ati radeon hd card....but everything else runs schweet in the best os available :P)
~j

---

### Post by MButterman on 2009-08-10
As for the ATI chipsets, they don't seem as affected but the graphics ones seem the most severely affected. That's is an oddity especially if you have integrated graphics. Logically you would figure it would effect everything across the board. 

I am at loss to explain how a severe glitch would escape the eye of the testers  or why it was released under these conditions?  Certainly a bug of this magnitude could have delayed the release until at least a work around or warning issued.

I have learned my lesson, I am going to stick to the more stable LTS until the next one comes around.

---

### Post by w00die on 2009-08-10
Hi,
Are you guys talking about the 23-7-09 released 9.7 catalyst driver?
Does that one suck too? I downloaded it, haven't tried it yet.

---

### Post by tomsa on 2009-08-10
Right now I say it's crappy.  I'm running 9.04 on a Gateway T-1625 laptop with the Radeon x1200 graphincs card.  ATI has declared (after only two years) my card a "legacy" card.  On top of that, FGLRX will completely bork my system, from what I've read.  Under intrepid, I could watch stuff from my laptop on my lovely plasma tv using that handy HDMI output I have.  Under jaunty, using the open source drivers, I get no  output from the HDMI past the bootsplash- and it screws up the laptop's screen as well.  ATI drivers suck.  Actually, as this laptop has gotten older, I am having more, not less problems with linux in general- which is something I did not expect.

---

### Post by doas777 on 2009-08-10
better but still a major pain. get nvidia if at all possible.

---

### Post by Ryazanov on 2009-08-11
I have HP laptop with ATI graphics. Ubuntu correctly detects resolution and refresh rate, but image quality is a bit crappy...

---

### Post by tony987456 on 2009-08-11
Well i have an ATI Radeon 7000 and it will not work with Ubuntu. Do you or anyone know what video card WILL work. PCI . My board is old and does not have PCIe.

---

### Post by carlinuxlearner on 2009-08-11
So basically what you're all saying here is: New or old, high-end or low-end, ATI drivers stink, and there are not any cards that "just work" with Ubuntu,they all have problems, so stay away from ATI.

--
c@rlewatkins

---

### Post by doas777 on 2009-08-11
pretty much. 
heck I have 3x the problems in windows with ati than I do with nvidia.

---

### Post by ~dr,j on 2009-08-11
hey all~
tony: i'd say just about any newer pci nVidia card (or any nVidia variant)would work ok...

and don't get me wrong, like someone else said....my card was deceted from the get go....it's just wne i use the 'restricted' (ati's) driver i can't do some things like launch google earth and see it properly....so yeah ati sucks in ubuntu compared to nVidia...but it's still useable, especially if your not after any fancy stuff (compiz) 
~j

---

### Post by Ozsmoka on 2009-08-13
I totally agree here with other users views.

I had issues with a mid range ATI x1950 years ago, and now I have issues with a high end 4870x2. When I get some time I'm going to swap back to my older more reliable Nvidia 768mb XFX 8800 Ultra. I have to prize it out of my wifes machine first...

Its ridiculous that such a 'high performance' [for Windows] card can not use drivers other than the open source ones in Linux. Its a credit to the open source developers that I can get the quality that I can. I'd stick with the open source drivers, but fan speed/noise and a few other minor issues are annoying me. Besides, for the money I paid for this card, I should be able to extract better performance from it.

I'll probably try to sell my ATI card to a Windows user and move to Nvidia. I don't particularly like the way Nvidia run their business, and I'm not totally enamored of their hardware, but I must give them credit where its due. I've never had any issues with Nvidia cards on Linux, but I've had many, many issues with cards that work very well in Windows causing hours of misery in Linux on ATI hardware. It just shouldn't be this way! I'm kicking myself now, for believing that ATI could possibly overcome this issue when I bought my existing card. They wont get another cent out of me!

Save yourself the trouble and go with Nvidia. If you want to buy a second hand ATI card, though, let me know lol.

Good luck with which ever you choose. The main thing is that you are using Linux ;)

Cheers

oz

---

### Post by markbuntu on 2009-08-13
I'll take that card off your hands.

The 4870x2 will work fine with the latest ati driver.

Most people who have trouble with the proprietary drivers and a lot of other stuff run into problems because they do not read the release notes or installer instructions. How is that the manufacturers fault?

People also buy the latest greatest stuff and expect it to instantly work on linux with drivers that were written before their hardware was manufactured, are they being reasonable?

That said, there are some legitimate gripes about the open source drivers for the rv500 cards that were released with Jaunty and have not been updated by the package maintainers for 6 months. But is that ATI's fault also?

I just got three monitors on 2 gpus working without any CLI work except installing the latest proprietary driver by running the installer and aticonfig --initial. I did all the setup in the Catalyst Control Center. It was easy.Progress has been good.

Ati could close their doors tomorrow and we would still get driver improvements. There is something to say for that.

---

### Post by ssri on 2009-08-13
> **markbuntu said:**
> Ati could close their doors tomorrow and we would still get driver improvements. There is something to say for that.

If they really do close their doors tomorrow would you be happy when karmic comes around, where AFAIK the current proprietary blobs do not support kernels >2.6.28?  Would you be happy with the opensource drivers for your >R500 card, as they are currently?

---

### Post by markbuntu on 2009-08-14
> **ssri said:**
> If they really do close their doors tomorrow would you be happy when karmic comes around, where AFAIK the current proprietary blobs do not support kernels >2.6.28?  Would you be happy with the opensource drivers for your >R500 card, as they are currently?

Well, I am a patient person.

I have used the open source radeonhd driver with my HD3xxx cards and it works pretty well as is except for 3D which I don't really use anyway. The reason I use the proprietary driver is because RandR1.2 does not currently support multiple gpus. That is not really a driver problem but a X server issue. RandR1.4 which will be out sooner or later will have this support which was originally slated for RandR1.3.

Unlike the proprietary drivers which replace parts of the X server to suit their needs the open source driver writers are constrained to using X as it is so many improvements to the open source drivers are dependent on X server advances. For example they cannot replace RandR which both nvidia and ati do to enanble use of multiple gpus. They also cannot rewrite the OpenGL stack or GEM or TTM like the proprietary blobs do.

By the time Karmic comes out I suspect that the open source drivers will have full 3D support for my cards since they have got basic 3D working already. If randr1.4 makes it I will not need any proprietary driver at all and that will be the end for me and fglrx.

Anyway, there are patches some gentoo folks came up with that will allow the current fglrx to run on the newer kernels. I could use those.

---

### Post by MButterman on 2009-08-14
Certainly patience is a virtue but ATI's history in linux drivers is spotty at best. I could accept the occasional glitch but in my experience ATI is very slow to correct them as opposed to nvidia response. I have one machine and it has to work or else I don't get my work done. I would favor nvidia because its overall track record in the linux community.

---

### Post by Ozsmoka on 2009-08-15
markbuntu,

I have been scanning the forums on various sites for the past two weeks and all the reports I have come across state drivers for the 4870x2 fail to operate correctly. If you have a link or can supply information to the contrary I would appreciate it, as I'm sure others would also. I tried installing the restricted drivers through the gui, and this did not work for me.

I spent alot of time, some versions of Ubuntu ago, getting dual monitors working with an x1950. While Nvidia had this enabled from the gui, it took myself and others alot of trial and error to get that set up going. I don't have anywhere near the time to do that these days.

I wouldn't say I'm a complete n00b. I have managed to compile drivers for my HVR 2200 DVB T card, but I'm no Linux veteran either. To be fair, I did credit the open source drivers, which have enabled me to watch and record HD TV without issue. 

If you can point me to a post where the 4870x2 works without issue, that would be great.

TIA.

oz
-edit-- lol here we go again, installed 9.7 drivers from ati, everything looked good, until starting Kaffeine. DVB T TV crashes x server...haven't even tested anything else out yet. . GPU fan is quieter, but there is a marked increase in CPU temp on my E8400. Not very impressive from my point of view. Pathetic really.

---

### Post by Yellow Pasque on 2009-08-15
The open-source ati/radeon drivers found in the stable Ubuntu's are usually somewhat  out-of-date. The open-source "radeonhd" driver is usually woefully out-of-date
I'd recommend trying .deb's from this PPA to see what the current drivers are like: [https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)

Personally, I prefer to build the radeonhd driver myself from git source. I whipped up a little guide for that: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) 

Mode-setting and 2D acceleration work very well for me with radeonhd. 3D support is advancing rapidly now that the infrastructure to support it is falling into place. We may see decent open-source 3D in Ubuntu 9.10, but it probably won't be truly end-user ready until Ubuntu 10.04: [http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)

---

### Post by ssri on 2009-08-17
> **markbuntu said:**
> By the time Karmic comes out I suspect that the open source drivers will have full 3D support for my cards since they have got basic 3D working already. If randr1.4 makes it I will not need any proprietary driver at all and that will be the end for me and fglrx.

Nope.  Full 3D includes OpenGL 2.0 support 9+(GLSL, shaders, etc), which will not be featured until after Gallium3D is fully stable, which will be by next summer (at the earliest).

[http://www.phoronix.com/forums/showthread.php?t=17887](http://www.phoronix.com/forums/showthread.php?t=17887)
[http://www.phoronix.com/forums/showthread.php?t=18292](http://www.phoronix.com/forums/showthread.php?t=18292)

> **markbuntu said:**
> Anyway, there are patches some gentoo folks came up with that will allow the current fglrx to run on the newer kernels. I could use those.

Last I read, those patches caused huge CPU usage spikes.  As much as I want fglrx to work in newer kernels for my card, I am not ready to sacrifice my CPU for it.  I am stuck with Catalyst 9.3 on my Jaunty install until I am happy with the opensource drivers.

I hope I do not sound like I am arguing with you, but I do not want other ATI sufferers like myself to feel that the solution is just around the corner.  We've been kicked around too much for our liking lately.

---

### Post by MButterman on 2009-08-18
> **ssri said:**
> Nope.  Full 3D includes OpenGL 2.0 support 9+(GLSL, shaders, etc), which will not be featured until after Gallium3D is fully stable, which will be by next summer (at the earliest).

[http://www.phoronix.com/forums/showthread.php?t=17887](http://www.phoronix.com/forums/showthread.php?t=17887)
[http://www.phoronix.com/forums/showthread.php?t=18292](http://www.phoronix.com/forums/showthread.php?t=18292)



Last I read, those patches caused huge CPU usage spikes.  As much as I want fglrx to work in newer kernels for my card, I am not ready to sacrifice my CPU for it.  I am stuck with Catalyst 9.3 on my Jaunty install until I am happy with the opensource drivers.

I hope I do not sound like I am arguing with you, but I do not want other ATI sufferers like myself to feel that the solution is just around the corner.  We've been kicked around too much for our liking lately.

Nothing more I would like is ATI to work but I am a realist before I am an optimist and ATI hasn't deliver the goods. I am not going to dream of a day when ATI has a stable driver when I have an Nvidia card that works today. No dreaming required for installation.

---

### Post by MButterman on 2009-08-31
I've gave 9.05 another try and was pleasantly surprised. Here is what I did with A7GM-S 2.0

1. The Foxconn BIOS issue seems to be solved. Use Foxconn's Global website and grab the recent bios and install. Since I had no floppy, I use a different method which I will write a how to shortly.

2. I loaded Super O/S 9.05 so it would have all multimedia packages installed by default

3. Up date system using "Update Manager" Ignore restricted drivers dialog and hit cancel for right now. Do system updates first.

4. Download most recent driver from ATI. After unsuccessfully using envyNG and Restricted Drivers applet, I decided it was important to manually install driver.

5 System has been extremely stable and linux compatable

---

### Post by Rhemat on 2010-01-25
I have a MSI RX2400Pro (ATi 2400HD chipset), and when I was using 9.04, they worked good.  
Quake 3 - 90FPS
(1152x864 (I think) Anamorphic Widescreen, Max Settings)
QuakeLive - 120FPS
(1280x720, Max Settings)
Doom 3 - 45-60FPS (end 15-30)
(800x600 Anamorphic Widescreen, Shadows, Bump-Mapping, High-Quality Textures)
Quake 4 - 15-45
(800x600 Anamorphic Widescreen, Shadows, Bump-Mapping, Low-Quality Textures)

However, since using openSuSE 11.4, and then switching to Ubuntu 9.10, the ATi drivers do worse.
Quake 3 - 55-80FPS
(Same Settings)
QuakeLive - 35-80FPS
(If I try to play in 1280x720, only the middle third of the screen is used, so I have to play in 1600x900)

I haven't tried Doom 3 or Quake 4 yet, but I'm pretty sure that it won't be an improvement.
If nVidia is as good as a lot of people are saying, I might buy one when I have the money.  However, trying to install the graphics drivers on my server machine, with a 6200LE Ge-Force AGP 8x card, and they don't install.
I have to say, Graphics cards have always been a pain, haven't they?

---

