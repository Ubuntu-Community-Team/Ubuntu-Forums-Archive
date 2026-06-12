---
title: "AMD 780G Is Here!"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by ikt on 2008-03-05
[http://www.theinquirer.net/gb/inquirer/news/2008/03/05/daily-wibble-05mar2008](http://www.theinquirer.net/gb/inquirer/news/2008/03/05/daily-wibble-05mar2008)
[http://www.theinquirer.net/gb/inquirer/news/2008/03/04/amd-pwns-day](http://www.theinquirer.net/gb/inquirer/news/2008/03/04/amd-pwns-day)

This is quite huge! I plan on getting myself a motherboard with 780G chipset the moment I can get my hands on one  =o

However.. of course.. how well can I expect it to work with ubuntu? will it work at all? :confused:

---

### Post by Azgard on 2008-03-06
I just found out about the 780G chipset today and was also wondering if it'll work properly with Ubuntu..

Time for an upgrade and the motherboards with 780G are looking great :)

Someone buy one and test please :)

---

### Post by ikt on 2008-03-07
> **Azgard said:**
> I just found out about the 780G chipset today and was also wondering if it'll work properly with Ubuntu..

Time for an upgrade and the motherboards with 780G are looking great :)

Someone buy one and test please :)

I should have one in a week or so to test, I was also waiting for the 4850 but it seams to be delayed or something.

I hope it works ok :D

---

### Post by Azgard on 2008-03-08
Great stuff :)

They're not even in my country yet unforuntately, but the suppliers tell me soon :)

---

### Post by gkrules on 2008-03-08
yea i heard they were awesome and had really low power consumption
its 55nm too =D

---

### Post by unsub_dk on 2008-03-15
i just bought the Gigabyte GA-MA78GM-S2H 780G board + AMD athlon X2 BE-2400 low power CPU.

I got everything working on Ubuntu 8.04 Aplha 6, even the onboard HD3200 gfx card works with the suggested ristricted driver :popcorn:

---

### Post by Azgard on 2008-03-16
That's great :D

How's the onboard graphics going..? Have you tested it with anything that uses a reasonable amount of graphics? Everyone seems to tell me it won't be able to do anything good :/

Just a bit off topic, how is 8.04 Alpha 6? I've though about installing it, but haven't tried yet.
Should it work just as well with 7.10?

---

### Post by ikt on 2008-03-16
> **Azgard said:**
>  Everyone seems to tell me it won't be able to do anything good :/

It's the equivalent of an entry level graphics card onboard, so expect to be able to play wow on low settings, and most other games on low settings. The fact you can even play games is crazy for an onboard solution which typically is horrible!

See this flash promo from AMD:

[http://download.amd.com/Desktop%20Launches/chipset1.swf](http://download.amd.com/Desktop%20Launches/chipset1.swf)

Obviously it's biased but the Intel Onboard 5FPS is pretty accurate, I'm not sure how accurate the AMD performance is..

> **Azgard said:**
> 
Just a bit off topic, how is 8.04 Alpha 6? I've though about installing it, but haven't tried yet.
Should it work just as well with 7.10?

I hope it works on 7.10, that's what I'll be installing tomorrow.

Hope it goes well. *Fingers crossed*

---

### Post by Azgard on 2008-03-16
Hmm, wow on low settings? :-O

That sounds pretty useless to me..

I've actually just bought WoW, will be playing it on my laptop, but would be nice to know my desktop is capable.. WoW doesn't use much graphics does it? I mean my laptop has a Radeon Mobility x700 built in and it plays fine with high graphics (from what I remember).

---

### Post by unsub_dk on 2008-03-16
i got WOW running quite well in 1024x768 with high detail :), but at 1280x1024 it's a bit laggy. :(

Had some problems with some graphic missing, but used the config.wtf file from this howto [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=654681]("http://ubuntuforums.org/showthread.php?t=654681")[/COLOR] 

and used the "regedit" tweak from[COLOR="Blue"] [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")[/COLOR]

i haven't had any problem with ubuntu 8.04 alpha 6 so far, seems quite stable.

---

### Post by ikt on 2008-03-16
> **Azgard said:**
> Hmm, wow on low settings? :-O

That sounds pretty useless to me..

Why else would you buy a graphics card? :?

Won't boot on 7.10, problem with x.org.

---

### Post by ikt on 2008-03-17
> **ikt said:**
> Why else would you buy a graphics card? :?

Won't boot on 7.10, problem with x.org.

Update:

Won't boot on 8.04 alpha 6, grub error 18.

Fantastic start. I have submitted a bug.

---

### Post by Azgard on 2008-03-17
Hmm true, I shouldn't be expecting so much from a IGP after all.. :)

That doesn't sound good at all.. :(

---

### Post by ikt on 2008-03-17
> **Azgard said:**
> Hmm true, I shouldn't be expecting so much from a IGP after all.. :)

That doesn't sound good at all.. :(

Fixed it!

Problem was the motherboard was running in some acpi mode? I set the hard drives to be recognised as 'Native IDE' in the BIOS and at the end of the installation I told the bootloader to be installed on the main hard drive, and it's booting up XD

Now just need to wait for 8.04 to be released -_-

---

### Post by madgenius on 2008-03-17
Got myself a Gigabyte 780G GA-MA78GM-S2H with an AMD X2 4000+ setup.

Could install the catalyst 8.3 drivers without any problems (followed the instructions here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide))

installed compiz, but when i enable desktop effects, I get a message saying "Desktop effects could not be enabled"

has anyone had better luck?/

oh! i'm running gutsy.

---

### Post by ikt on 2008-03-17
> **madgenius said:**
> oh! i'm running gutsy.

I'm surprised, gutsy stops loading for me :/

try 8.04, it's pretty stable, I was having a ton of fun with it yesterday.

---

### Post by madgenius on 2008-03-18
i'm new to ubuntu, so please bear with me.

i'll have to uninstall the catalyst drivers, update to 8.04 and re-install catlayst right?

thanks

---

### Post by unsub_dk on 2008-03-19
use the restricted driver ubuntu 8.04 suggests, works fine for me

---

### Post by Azgard on 2008-03-19
Where would I find Ubuntu 8.04 to download?

Thanks :)

---

### Post by Kamilion on 2008-03-21
Run
```

update-manager -d
```

---

### Post by maynoth on 2008-03-24
Can anyone here confirm that the 780g/700SB chipset itself runs under 7.10?  I have a geforce 8600GTS so I wouldn't be using the onboard video.    I don't want to buy it and then not be able to use it till Hardy is out

---

### Post by ikt on 2008-03-25
> **maynoth said:**
> Can anyone here confirm that the 780g/700SB chipset itself runs under 7.10?  I have a geforce 8600GTS so I wouldn't be using the onboard video.    I don't want to buy it and then not be able to use it till Hardy is out

I can't confirm it works because it didn't work for me, however 8.04 did and is 30 days away so I suggest loading it :D

---

### Post by Kamilion on 2008-03-28
Yes, it works with gutsy. You need to install gutsy in order to actually run update-manager -d to get to hardy, or grab the hardy iso from [https://wiki.ubuntu.com/HardyHeron](https://wiki.ubuntu.com/HardyHeron) or [http://releases.ubuntu.com/releases/8.04](http://releases.ubuntu.com/releases/8.04)

---

### Post by madgenius on 2008-03-28
works with Kubuntu Gutsy. i had quite a few crashes running hardy on my machine, so went to a more 'stable' solution.

installed the catalyst 8.3 drivers, and can get compiz running. havent tested it with any 3D games or such as yet.

suprisingly, i cant seem to get any sound output. Made a separate thread here

[http://ubuntuforums.org/showthread.php?p=4604414#post4604414]("http://ubuntuforums.org/showthread.php?p=4604414#post4604414")

---

### Post by pHr34kY on 2008-03-29
I got one!

It all works fairly well. At one stage I even had dual-monitors running BigDesktop with Compiz.

Then I discovered there was no XV video acceleration, so I attempted to fix it by manually installing catalyst. Somehow amdcccle broke my entire setup without modifying xorg.conf, now I'm down to 1 screen at 1024x768. I'm steering clear of amdcccle now.

And yes, this chipset rocks.

The only other problem I've had is with it occasionally hanging at GRUB with AHCI enabled, but I think that's a BIOS issue.

Overall, a very good board, considering how cheap it is!

---

### Post by msebast on 2008-04-01
I was able to get textured video working on Hardy AMD64 using the restricted (fglrx) driver.
I have:
Gigabyte 780G GA-MA78GM-S2H motherboard
Athlon64 x2 5000

I got this info from several forums but I seem to have lost the bookmarks.

In /etc/X11/xorg.conf Device Section add the following lines:

        Option      "Textured2D" "on"
        Option      "TexturedXrender" "on"
        Option      "UseFastTLS" "1"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "off"
        Option      "TexturedVideo" "on"
        Option      "TexturedVideoSync" "on"

At the end of the file add these:

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Enable"
        Option      "XVideo" "Enable"
        Option      "RENDER" "1"
        Option      "DAMAGE" "Enable"
EndSection

After saving your changes run this :
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

And restart the x server (ctrl-alt-backspace)

Then run xvinfo to verify that xv is working.

Seems to get composite mostly working as well. But I don't use composite because it doesn't play nice with mythtv.

video playback is pretty good.
The fglrx driver is buggy.
mythfrontend and aptitude have crashed several times.
The stacktraces always point to fglrx as the culprit.

The computer is usable in this configuration.
But I will be trying the radeon radeonHD open source drivers to see if they are more stable.
up-to-date builds of the open source drivers here:
[https://launchpad.net/~tormodvolden/+archive](https://launchpad.net/~tormodvolden/+archive)
[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)
[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)
[http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

Hope someone finds this helpful.

---

### Post by madgenius on 2008-04-03
Is anyone else having problems with the sound? It started working for me after some time - don't ask me how. Thing is, the sound volume is half of that in windows. This when I have every channel on alsamixer at 100%

---

### Post by msebast on 2008-04-03
> **madgenius said:**
> Is anyone else having problems with the sound?

Under hardy sound has been perfect.
I don't have windows on this machine but volume levels are similar to what I got with my old motherboard.
I'm only using the stereo front speaker analog outputs.
I haven't tried the optical out, sound over hdmi, or other analog in/out.

---

### Post by msebast on 2008-04-03
> **pHr34kY said:**
> ...it occasionally hanging at GRUB with AHCI enabled, but I think that's a BIOS issue.

I have the same issue and it's beginning to drive me nuts.

The grub menu comes up, I hit the enter key (or wait for the 10 second count down).
Then I get a black screen with a cursor in the upper left corner.
And after that nothing happens.

Only 1 out of 3 boots actually start loading the kernel.

My board came with the F2 bios.
I upgraded to F3 and the problem remains.

---

### Post by snirpyor on 2008-04-14
(new to ubuntu)

Got it set up with first kubuntu then with ubuntu 8.04 (hardy). Both with latest catalyst drivers.

In both occasions I ran into the same strange issue. All seems to be working fine, until I use a 3d application. After a few seconds or sometimes directly I start loosing the window running the 3d application. 
[LIST]
[*]In Blender I see right through the window, as if it wasn't there. Moving the mouse brings the window back, but only very briefly. The application still shows on the panel.
[*]In Lincity-NG the window blackens still showing the pointer in lincity style. Again moving the mouse sporadically brings back picture
[/LIST]

No such issues arise with 2d applications (playing a dvd, lincity normal, desktop use). I believe playing a dvd to be more demanding to both CPU and GPU than showing the blank start screen of blender, so I rule out a temperature issue.

Can anyone pinpoint this? Drivers, Hardy, motherboard, bios settings? I believe I have nothing out of the ordinary going on here....

---

### Post by crispy_chunks on 2008-04-16
Is the h.264 hardware decoding working with vlc, kaffeine or anything?

---

### Post by purewater08 on 2008-04-16
Using XV output will reduce CPU usage while playing movies but H.264 hardware decoding seems not supported by AMD's driver.

---

### Post by msebast on 2008-04-16
As far as I know h.264 hardware decoding does not work at all on linux.
Dosen't matter which hardware you have. No linux/xorg drivers support this feature.
On some hardware with some drivers you can get XVMC to accelerate MPEG decoding.
I got it working on my old MB with nvidia 6150. But it wasn't worth the trouble.

See here for more info:
[http://www.phoronix.com/scan.php?page=news_item&px=NjM1Ng](http://www.phoronix.com/scan.php?page=news_item&px=NjM1Ng)

But if you've got a fast processor you don't really need hardware acceleration beyond whatever xv/TexturedVideo does.
I've got mythtv playing 720P and 1080i scaling it to 768x1368 for my lcd tv.
It works pretty well. 
I have an Athalon X2 5000 and get about 20-40% CPU usage playing 1080i.

One advantage of using the CPU for decoding is better control over deinterlacing methods.

---

### Post by bretticus on 2008-04-19
> **msebast said:**
> I have the same issue and it's beginning to drive me nuts.

The grub menu comes up, I hit the enter key (or wait for the 10 second count down).
Then I get a black screen with a cursor in the upper left corner.
And after that nothing happens.

Only 1 out of 3 boots actually start loading the kernel.

My board came with the F2 bios.
I upgraded to F3 and the problem remains.

I can't even seem to install it (Heron.) Harddrive light is solid red. Cursor blinked for a long while. Now I have "Buffer I/O error on device hdb." errors. In addition, I have a SQUASHFS error "failed reading block." Will not got intop setup. Live boot attempt failed as well.

This is RC1 disk. I have F3 bios and Native IDE on SATA harddrive. Athlon X2 5400. 

Anyone else have this issue?

---

### Post by bretticus on 2008-04-19
Downloading the amd 64 bit iso. Maybe I'll have better luck. :)

---

### Post by bretticus on 2008-04-19
> **bretticus said:**
> Downloading the amd 64 bit iso. Maybe I'll have better luck. :)

Well, i think it had  something to do with one of my cdrom/dvd drives. However, I did get it installed via the amd64 version.  I keep getting "exception Emask..." and "status: { DRDT ERR}" messages for one of my cdrom/dvd drives (as mentioned.) Performance seems sluggish compared to Vista. I wonder if all the device drivers are up to scratch for this board (Gigabyte MA78GM-S2H)  I do realize the board is pretty new and this is the 64 bit version of the OS. Not the speed demon in Ubuntu I envisioned :)

---

### Post by msebast on 2008-04-19
Ubuntu should not be sluggish next to vista. I find it is very snappy and responsive. (Well, I haven't tried vista but it's not likely to be faster when they are both setup correctly.)

There is probably something wrong with your install or configuration.

I think for AMD780G Ubuntu defaults to using the very crappy vesa video drivers.
You will get better performance if you enable the fglrx propritary driver.
See "System > Administration > Hardware Drivers"
Check that xv is enabled by running "xvinfo" at the command prompt.
Check that fglrx is enabled with "fglrxinfo".

Try running "glxgears" I get about 2000FPS.
If you get something a lot worse there is probably something wrong.

Some other things to try:
Disconnect your questionable cdrom drive.
Upgrade the firmware for your motherboard. 

Let me know if you're still having trouble.
If you think the problem is related to video drivers could you post /var/log/Xorg.0.log and /etc/X11/xorg.conf ?

Best of luck,
Mike

---

### Post by bretticus on 2008-04-19
> **msebast said:**
> Ubuntu should not be sluggish next to vista. I find it is very snappy and responsive. (Well, I haven't tried vista but it's not likely to be faster when they are both setup correctly.)

There is probably something wrong with your install or configuration.

I think for AMD780G Ubuntu defaults to using the very crappy vesa video drivers.
You will get better performance if you enable the fglrx propritary driver.
See "System > Administration > Hardware Drivers"
Check that xv is enabled by running "xvinfo" at the command prompt.
Check that fglrx is enabled with "fglrxinfo".

Try running "glxgears" I get about 2000FPS.
If you get something a lot worse there is probably something wrong.

Some other things to try:
Disconnect your questionable cdrom drive.
Upgrade the firmware for your motherboard. 

Let me know if you're still having trouble.
If you think the problem is related to video drivers could you post /var/log/Xorg.0.log and /etc/X11/xorg.conf ?

Best of luck,
Mike

Thanks Mike. I've been at this all day and I finally figured out what was wrong (thanks to this forum and folks like you.) My hard drive performance was terrible. [See my other post]("http://ubuntuforums.org/showthread.php?t=760121")

I loaded pata_atiixp and blacklisted ata_generic and Ubuntu is now very fast (of course!)

Wonder why this bug exists still (the post I got my info from goes all the way back to January) aster so much time.

By the way, I  upgraded my fw to F3 on the day I put them computer together. I do get about 2000 fps with glxgears. xvinfo shows no adapter:

```
$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```

And fglrxinfo seems fine:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7412 Release
```

---

### Post by bretticus on 2008-04-19
Added:

```
Option 		"TexturedVideo" "on"
```

to /etc/X11/xorg.conf under the Device section for my video card. Now when I run "xvinfo" I get lots of output. It did create some "funky" artifacts that quickly went away as I was logging in. I can live with that (was very fast!)

Thanks for your help.

---

### Post by Covarrubias on 2008-04-23
I can´t install Hardy RC with SATA AHCI mode enabled, the LiveCD boots and after partitioning and installing with no problems at first reboot grub fails with "error 18", someone tried this?

---

### Post by msebast on 2008-04-23
Covarrubias, see posts 12 and 14 in this thread. Using IDE mode got it working for that poster. On other forums I've seen people have similar problems with Windows. ([http://www.avsforum.com/avs-vb/showthread.php?t=992503](http://www.avsforum.com/avs-vb/showthread.php?t=992503)) 

I was able to install and intermitently boot with AHCI mode but it works much better under IDE mode. Maybe it partially worked for me since I only have one SATA hard drive and my one optical drive is on IDE? I'm curious what SATA devices you are using?

Be sure to update the firmware. The firmware shipped on early boards isn't very good.

Please let us know if you get it working and what you did to fix it.

---

### Post by Kamilion on 2008-04-24
Absolutely update the BIOS to F3.

Dig out a USB flash drive, FAT32, any size, drop the bios file on it, and hit END to fire up Qflash from the current BIOS. It's just so easy. Don't even need windows or DOS anymore...

The F1 and F2 versions have some serious problems with memory timings -- I stuck 8GB of Mushkin DDR 667 in mine, and for some reason the earlier BIOS would try to run it at 720Mhz! (Needless to say, it didn't work out too well!)

I had to yank out all but one stick to even get to the BIOS, changed to DDR533 and dumped the rest of the ram back in. Ran like a champ.

F3 solved the problem and the memory is now running nicely at 667Mhz, autodetected.

Keep in mind, the board has six SATA ports -- the one on the back panel and the sideways one labeled 4 on the GA-MA78GM-S2H will ALWAYS run in Native IDE mode unless you set the BIOS option "OnChip SATA Port 4/5 Type" to "As SATA Type". Ports 0-3 can run in AHCI, RAID, or Native IDE mode, and so far I've not noticed much of a performance difference between them with 2X 250GB Maxtors.

AHCI will get you Hot-plug and NCQ, and not much else, and NCQ still seems to work in Native IDE mode, thanks to Linux's driver support, but I haven't actually tested it.

I'd recommend keeping your /boot on SATA port 5 if you want to play with AHCI.

Personally, I picked up a CF to SATA adapter:
[http://www.addonics.com/products/flash_memory_reader/adsacf.asp](http://www.addonics.com/products/flash_memory_reader/adsacf.asp)

and a nice fast Sandisk Extreme IV 4GB card (~40MB/sec) for my core system to run from, and use the Maxtors for data storage. Most of the time, the Maxtors are spun down and the system runs direct from the CF.

Man, it works sweet with hardy!

-- Kamilion
"Never feel stupid for asking questions, feel stupid for ignoring answers."

---

### Post by jhfry on 2008-04-29
I am considering buying a Gigabyte 780G GA-MA78GM-S2H, or similar 780G mobo for my desperately needed HD frontend (probably diskless).  I have a few questions however.

1. Now that there are more 780G mobo's out, is there a better one?
2. Now that you guys have been using them for a while, do you still highly recommend them?
3. Anybody successfully tested the spdif output (optical/coaxial)
4. Does everything truly work out of the box (with minor tweaks and binary driver installs)
5. Anybody successfully pass SPDIF over HDMI?

I guess, what I am asking is, if you wanted to build a cheap, simple, reliable, 1080p HD-capable frontend would you buy one of these or something else.  Do you have any regrets?

I think that using this or a similar board I can build a sub $400 HD ready frontend that will last for a good long time and likely improve over time as ATI drivers continue to get better.  Should I do it, or look elsewhere?

---

### Post by JoeySantos29 on 2008-05-02
Also planning to setup a new PC.

Would an AMD 780G chipset be advisable?

---

### Post by mike farad on 2008-05-04
I've been working at this for weeks, and being a newbie at most of this stuff, it hasn't been easy.  Then I found this link.
 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

Following it, the fglrx drivers installed perfectly for my Asus M3A78-EMH HDMI MoBo. (I loaded Hardy a few days ago, so I don't know how this would have worked on 7.10).

I then went onto Compiz and other goodies with no troubles.

I hope this link helps others who are still pulling out their hair.

Mike:)

---

### Post by jhfry on 2008-05-04
> **mike farad said:**
> I've been working at this for weeks, and being a newbie at most of this stuff, it hasn't been easy.  Then I found this link.
 
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

Following it, the fglrx drivers installed perfectly for my Asus M3A78-EMH HDMI MoBo. (I loaded Hardy a few days ago, so I don't know how this would have worked on 7.10).

I then went onto Compiz and other goodies with no troubles.

I hope this link helps others who are still pulling out their hair.

Mike:)

I'm glad to hear your video is working... but I still would love to know:

1. is the hdmi output working?
2. is the digital audio output working?
3. is everything else working?
4. will it drive a 1080i display?
5. is it stable?

---

### Post by mike farad on 2008-05-04
Yes the HDMI is working.  I only have an Old School 51" 16x9 Sony rear screen CRT, (love the picture..blows away most LCDs). Anyway, it only does 720p.  It will take 1080i, but not 1080p, and even then it displays it as 720p.  So I configured he monitor setting for 1280x720@60Hz.  Displays nicely.  I could try 1080i, but I didn't see the point.  Besides, I'm not sure how to set up 1080i as opposed to 1080p.  Somewhere in the Video Preference I would have had to set interlaced.  Don't know where that is.

The Digital audio via the HDMI cable doesn't appear to be working, or the old Sony set doesn't accept it, I don't know which.  Booting XP, I get the same result, but XP will output via the separate SPDIF out, (while ouputing to the analogue ports at the same time).  In Ubuntu, I dont hear any digi coming out of the SPDIF, the analogue outs work.

In XP, the HDMI HD content streams perfectly.  Better than in Ubuntu.  XP must be taking advantage of the 780G chip better than Ubuntu.  I only have an AMD Athlon Dual core 4200 on the mobo.  If I had spent more than $79, a faster cpu probably would have given me better results.  Ubuntu is a little laggy at 720p, whereas under XP, the HD has no indication of lagging.

I've only had this machine configured with the flgrx drivers for a day or so, not enough time to say that it is stable.  Everything seems to be working.

Thanks to everyone who helped me work thru my setup.

Mark

---

### Post by nstamoul on 2008-05-04
And how is compiz working?Everything allright?Using stock hardy drivers (i mean the ones from administration->Hardware Drivers).

---

### Post by mike farad on 2008-05-04
I instaled compiz fusion by using this link:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

I also followed his set up instructions and it worked out fairly well. I set up the "cube" but mine doesn't seem to work as I've seen on the various 'You Tube' demos.  Mine kinda scrolls the 4 desktop pages in a 2d kinda flip.  On the youtube videos, the cube is sort of floating on the desktop.  Mine takes up the whole vertical space, and I don't see the top and bottom face of the cube.  I'm sure there's a setting I missed.  The Windows key-Tab works great.  The wobble works...kinda of stupid effecct IMHO.

I badsically wanted to try compiz just because I could. When my flgrx drivers wouldn't load prpperly, it just made me want he compiz stuff that much more.  I sudpec I'll play with the stuff a little nore, and then go back to he basic Ubuntu set up.

Mike

---

### Post by PhatKat on 2008-05-11
Hmm i am a real buntu newbie but i plan to upgrade to buntu 8.04LTS (using Gutsy for past 2 weeks)Can someone compile a sort of 'idioit's guide' to get 780G mobos running buntu 8.04 out of the box?

---

### Post by mboisson on 2008-05-11
hello,
can you give instruction on how you installed everything ? I can't get the graphic drivers installed and I can't get the audio to work properly.


I used ubuntu 8.04 lts server amd64 version.

thank you

---

### Post by hms_gbg on 2008-05-12
I have a GA-MA78GM-S2H with a 4850e CPU, 2GB of memory and a SATA 2.5" hard drive.

When I try to install 8.04 LTS the installation runs for less than a minute before it reboots. I have tried both the desktop and alternate CD with the same result. I have tried to change the SATA settings to native-IDE, raid, and achi, as well as adding acpi=off when booting. I also disconnected the hard drive, but the system still reboots after the "scanning CD" progress bar when using the alternate CD. I doubt that there is a hardware error, since I'm able to boot with an old 2006.1 Gentoo live-CD.

Anyone with suggestions of what more I can try?

---

### Post by prince_niceguy on 2008-05-14
am having gigabyte GA-MA78GM-S2H, amd 4400+, 1 GB Gskill, 80GB sata, and everything is working great out of the box with 8.04 AMD 64. Would recommend using 780G to anyone who is interested in HTPC... it is cheap and great... i got everything under 300$.

---

### Post by bwooster0 on 2008-05-14
I could not get the integrated ATI chipset to put out a perfect 1080i video signal to my 60 inch Sony tv. I think 1280 x 720 did work properly.

After many tries at tweaking the driver setting I threw an NVidia video card into the box and it worked perfectly.

I want to see if I can tweak the Mythbuntu settings so that 720p material goes to the tv as 720p and 1080i material goes out as 1080i (my series 3 tivo does this).

---

### Post by prince_niceguy on 2008-05-14
> **hms_gbg said:**
> I have a GA-MA78GM-S2H with a 4850e CPU, 2GB of memory and a SATA 2.5" hard drive.

When I try to install 8.04 LTS the installation runs for less than a minute before it reboots. I have tried both the desktop and alternate CD with the same result. I have tried to change the SATA settings to native-IDE, raid, and achi, as well as adding acpi=off when booting. I also disconnected the hard drive, but the system still reboots after the "scanning CD" progress bar when using the alternate CD. I doubt that there is a hardware error, since I'm able to boot with an old 2006.1 Gentoo live-CD.

Anyone with suggestions of what more I can try?

did you do a check sum of the ISO before burning it? it might be a coincidence that both the cd didnt work.

---

### Post by iduriduridur on 2008-05-15
I don't if this will make sense but choose the first ubuntu (desktop and install) option when booting the do not choose install. I could not get my asus m3a78 hdmi to work correctly for the "install" only option but the going to the desktop and click the install option worked for me.

---

### Post by nstamoul on 2008-05-23
Has anybody tried out the new 8.5 catalyst drivers yet??

Any improvment with the onboard graphics card?

---

### Post by Azmo on 2008-06-10
Tried the 8.5, but just got a black screen. Did not bother trying to figure out why. It was difficult enough to uninstall the drivers, since the dpkg did not fully do so because of some diversion of some file or whatever. Anyway, once I got back the drivers from the repo it graphics did still not work. Probably because of some configuration in the /etc/ati (which I didn't even know existed) which was not removed because the other drivers could not be fully removed..    very messy. Anyway, the older repo drivers are working now, and i'm not testing the 8.5 again. There must obviously be a reason that it is not even in intrepid yet.

---

### Post by Springveldt on 2008-06-10
Hi all, brand new to Ubuntu and Linux. I've got this board (Gigabyte) and I'm having all sorts of problems with the HDMI and sound. Basically through HDMI, I get up to the splash screen then nothing, the signal cuts off. I've tried setting the resolution but I can't even set 1280x720 as it's not available. I've tried setting the resolution to 1024x768 which is my plasma screens native resolution but still no joy. D-Sub and DVI work fine though.

The ATI driver is installed according fglrxinfo...

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7412 Release

So, my question is has anyone got the HDMI out, working to a plasma? My plasma is a Panasonic TH-42PB60X.

---

### Post by Springveldt on 2008-06-13
Well I finally gave up and installed Vista. Everything worked on Vista as soon as I installed the 8.5 Catalyst drivers. There were just too many things not working in Ubuntu for me to continue trying to get to grips with it. Apart from HDMI not working, I found MKV and h.264 playback pretty poor and my wireless keyboard and mouse had a range of around 5 or 6 feet with Ubuntu but with Vista it is the stated 10 metres.
So it looks like I'm coughing up another £60 to M$ just to have a simple HTPC sitting in the living room, what a pity as Ubuntu did have some things that looked really cool.
Maybe the next release will have better ATI support.

---

### Post by dust79 on 2008-06-19
I got my system up and running on this hardware more or less directly out of the box with Ubuntu 8.04:

motherboard: ASUS M3A78-EHM HDMI
cpu: Athlon64 X2 Dual-Core 4850e

The only problem I had was to boot from SATA port 5 & 6.

It is now running stable with 6 SATA drives since a month.

What I have not tested so far is HDMI output. But I will update my post when its done.

If you have problems getting this motherboard to work I will do my best to help you.

---

### Post by vph on 2008-06-20
Hi,
I just bought the Gigabyte GA-MA78GM-S2H with a Athlon X2-5000+ and one SATA HD. I installed Ubuntu 8.04. After reboot it ends with a GRUB loading error 18.
I saw a bug report ([https://bugs.launchpad.net/ubuntu/+bug/220599](https://bugs.launchpad.net/ubuntu/+bug/220599)) related to the same issue but no fix or workaround.

Did anybody have and fix this problem? Any ideas?

Regards,

vph

---

### Post by Trojanmon on 2008-06-30
> **hms_gbg said:**
> I have a GA-MA78GM-S2H with a 4850e CPU, 2GB of memory and a SATA 2.5" hard drive.

When I try to install 8.04 LTS the installation runs for less than a minute before it reboots. I have tried both the desktop and alternate CD with the same result. I have tried to change the SATA settings to native-IDE, raid, and achi, as well as adding acpi=off when booting. I also disconnected the hard drive, but the system still reboots after the "scanning CD" progress bar when using the alternate CD. I doubt that there is a hardware error, since I'm able to boot with an old 2006.1 Gentoo live-CD.

Anyone with suggestions of what more I can try?

I'm having this exact problem with a GA-MA78G-DS3H motherboard, 4850e processor, 4gb ram + 2 SATA HDs. I tried Native IDE and AHCI and the same thing happens, always a reboot right after the scanning cd step. I even unplugged the drives and tried running the Check CD for Defects option...same deal.

---

### Post by dust79 on 2008-07-01
It looks like it has to do with the GA-MA78GM-S2H motherboard and not the chipset in general. I have an Asus motherboard with same chipset and have more or less the same configuration (4850e CPU, 2GB of memory and a SATA 2.5" drive). And I have no problem with to install 8.04 LTS. My only suggestion is to check if you can find an updated bios and see if it helps.

Maybe you can also try to use an SATA cd-drive and not a PATA or vice versa.

---

### Post by Trojanmon on 2008-07-01
> **dust79 said:**
> It looks like it has to do with the GA-MA78GM-S2H motherboard and not the chipset in general. I have an Asus motherboard with same chipset and have more or less the same configuration (4850e CPU, 2GB of memory and a SATA 2.5" drive). And I have no problem with to install 8.04 LTS. My only suggestion is to check if you can find an updated bios and see if it helps.

Maybe you can also try to use an SATA cd-drive and not a PATA or vice versa.

I have the latest firmware (F4) but no SATA cdrom available. What Asus board do you have exactly? I'm about ready to RMA this thing and get something else.

---

### Post by JEB1517 on 2008-07-19
I have the GA-MA78GM-S2H with a 4850e, 2x1gb ddr2 1066 corsair dominator and a wd250 sataII. I got kubuntu to install just fine but I cant play any videos, haven't tried any games yet. Do I have to install any other drivers or anything? I'm new to this linux thing. When I first loaded it installed a proprietary driver or something but that was it. I also installed all of the available updates. Alot of pictures are also not showing up. I'm using DVI output.

Edit: For instance, at this site [http://na.blackberry.com/eng/services/desktop/](http://na.blackberry.com/eng/services/desktop/) I get the menus at the top and to the left, but the middle is completely blank for me, just white page. I think there's some pictures and drop down menus or something that should be there. I need to download that software for my phone.

---

### Post by GSMD on 2008-07-19
Ok, here's my experience with gigabyte's 780g mobo. I intended it for use as a dev server (amd64 server install) + htpc with mythtv & vdr over hdmi. For the first part - no prob. It's the second that sucks. Installing plain xorg + mythtv was no pain, but fglrx stuff + sound is what sucks. first off, the fglrx driver that comes with ubuntu led to a crippled screen, no matter what xorg options i provided. 8.6 brought the entire system down. what worked out fine was radeonhd compiled from head git revision. this finally brought a perfect 1920 * 1080 60hz pic to my tv. yet no sound no matter what! i finally installed gnome just to mess with gui and eventually hear sound pressing 'test' button but not with mplayer.
moved over to gentoo to see if i can make the damned mobo work. do i need to tell you that under winxp the whole thing worked flawlessly (perfect fullhd hardware-decoded pic and sound) after catalyst 8.6 was installed? and they tell us about how good is linux hardware support. damn it!

---

### Post by mmilburn on 2008-07-21
> **hms_gbg said:**
> I have a GA-MA78GM-S2H with a 4850e CPU, 2GB of memory and a SATA 2.5" hard drive.

When I try to install 8.04 LTS the installation runs for less than a minute before it reboots. I have tried both the desktop and alternate CD with the same result. I have tried to change the SATA settings to native-IDE, raid, and achi, as well as adding acpi=off when booting. I also disconnected the hard drive, but the system still reboots after the "scanning CD" progress bar when using the alternate CD. I doubt that there is a hardware error, since I'm able to boot with an old 2006.1 Gentoo live-CD.

Anyone with suggestions of what more I can try?


The same thing happens to me, indiscriminate of which distribution I use (Fedora 9, Ubuntu, etc).  I am using the same motherboard as you and have modified SATA settings numerous times.  I am going to attempt a firmware update this evening and see what comes of that.

---

