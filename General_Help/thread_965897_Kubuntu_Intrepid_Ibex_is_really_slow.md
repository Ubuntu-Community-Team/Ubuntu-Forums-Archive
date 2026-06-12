---
title: "Kubuntu Intrepid Ibex is really slow"
date: 2008-10-31
forum: General Help
---

### Post by JSHW on 2008-10-31
My new kubuntu install is really slow! Flash videos skip, resizing is laggy and it's all around slow, even when web surfing and word processing.

Granted, I have a 4 year old laptop with a 1.6ghz processor and intel 910i video card, but I've run compiz way back when without any trouble.

Does anyone know a quick fix? I turned off desktop effects, and that fixed most of my problems. It'll be nice to have some of that eye candy, though.

BTW, the new KDE4 is pure awesome, I don't want to switch to Ubuntu (not that there's anything wrong with it)

---

### Post by Yezinki on 2008-10-31
I agree its feels like a hogger like Vista.

---

### Post by Asham on 2008-10-31
If you bring up the system activity monitor, do you see processes using high values for cpu? How much memory do you have? 

I agree, KDE4 looks great! :D

---

### Post by JSHW on 2008-11-01
> **Asham said:**
> If you bring up the system activity monitor, do you see processes using high values for cpu? How much memory do you have? 

I agree, KDE4 looks great! :D

krunner - 11%
xorg - 9 
firefox - depends, usually around 10-20

I have 1 gig of RAM. Mplayer doesn't play well with firefox either. It can barely play a video. I think it might be a video card problem.

---

### Post by frioux on 2008-11-03
I agree, but how can it be a video card problem?  It's not just the video that lags, it's EVERYTHING.  Like, just typing right now on firefox sometimes I get input lag like I used to on my old 233Mhz 32 meg computer.  

Top says that  ksoftirqd/0 is taking up 65% of the CPU.

Maybe we should turn that off?

-fREW

---

### Post by jasomsef on 2008-11-05
I have slow Interpid to. My problem is with frequency scaling, because it always run on 900MHz but I have 1900MHz Thurion. If I change power scheme to performance frequecy doesn't change.

I have HP 6715s with 64bits Turion and 4GB RAM

---

### Post by JohnnyVW on 2008-11-09
I'm having this same issue.  I decided to install Kubuntu 8.10 on my work laptop (Thinkpad R51, 1.6GHz Pentium M, 1.2GB RAM) after trying out the live version.  I haven't played with KDE since Mandriva was still called Mandrake.  ;)

Anyway...  I really dig KDE 4.1's interface (mostly eye-candy).  I need to re-acquaint myself with KDE; I've been using Gnome since Ubuntu 5.04.  I sure would like to use Kubuntu on this laptop, but the jerky video and slow window wipes are pushing me back to Ubuntu...

---

### Post by aged hippy on 2008-11-09
To be fair, KDE 4.2x is a desktop still in development. :)

Give it a chance, please....

---

### Post by PacShady on 2008-11-09
I have to say, it's the same story for me. I tried running Intrepid Kubuntu on my laptop, 1.6GHz dual core, 3GB RAM, and nVidia 8600m GS 512MB graphics card, and I have to say KDE 4 is currently unusable for me. I so much as HOVER over a desktop icon and the entire system hangs for about 10 seconds, and that's with desktop effects turned off, removed from apt-get and effects turned off in xorg.conf!

I have no idea as to why it's so horrifically slow, and to be honest I don't think I'll find out because it seems most people don't have a problem (what ungodly machines are these people RUNNING?!?). This thread is the first evidence I've found of others having the same issues. I'm afraid, until something is done to unbloat KDE 4, I'll have to make the decision to either stick with Hardy, or switch to vanilla Ubuntu.

I got the impression when I first heard about KDE 4, that it was like the KDE user's Vista, with the fancy eye candy and the widgets and all that funky stuff. Seems it turned out to be too MUCH like Vista, with the bloat and the bugginess and the utter unusability and the fact you need a machine powered by Satan to run the damn thing!

'Shady

---

### Post by aged hippy on 2008-11-10
[quote=PacShady]what ungodly machines are these people RUNNING?!?[/quote]

In my case - nothing special, it's a cobbled-together machine with an ASUS K8-VMX motherboard, ATI Radeon 9800 Pro graphics card, and 768Mb of Ram, no fancy effects turned on. :)

Intrepid is fast enough for me, and responsive, but to be honest, i much prefer Hardy with KDE 3.5 :D

---

### Post by prankst3r on 2008-11-10
I have a Intel Core 2 Duo (6600) 2.4Ghz w/ 2Gb of Ram, Nvidia 8600GT w/512Mb of Ram and KDE 4.12 Intrepid runs like ***. I also installed it on my laptop (Dell 1420N Core 2 Duo 1.66Ghz w/ 4Gb RAM, Nvidia 8400GS) and it is also unbearable on that laptop. Both of these computers have visual effects set to None and still laggy everywhere.

Is this a video driver problem or something with KDE?

I wanted to give KDE a chance - I really did, but it looks like I'll be sticking with Gnome.

---

### Post by wpiter on 2008-11-10
I don't have a fancy laptop, but with compiz fusion activated (read: full eye-candy) I don't notice any delay in day to day work. However what I do notice is that when playing flash based games, there is lots of lag. Also on kubuntu 8.04 I had no problems playing tremulous, now it locks up with only 8 or 9 fps. Dissabling all eye-candy results in absolutely no improvement. I'm willing to wait another month for updates/upgrades (currently I'm noticing a lot of updates) so I hope this problem gets resolved soon. Otherwise I'm going ubuntu 8.04

---

### Post by aged hippy on 2008-11-10
> **prankst3r said:**
> I have a Intel Core 2 Duo (6600) 2.4Ghz w/ 2Gb of Ram, Nvidia 8600GT w/512Mb of Ram and KDE 4.12 Intrepid runs like ***. I also installed it on my laptop (Dell 1420N Core 2 Duo 1.66Ghz w/ 4Gb RAM, Nvidia 8400GS) and it is also unbearable on that laptop. Both of these computers have visual effects set to None and still laggy everywhere.

Is this a video driver problem or something with KDE?

I wanted to give KDE a chance - I really did, but it looks like I'll be sticking with Gnome.

It should run like a hungry lurcher on your machine. :D

I don't wish to advertise another Forum, but there have been several video-related problems raised at the Kubuntu Forums, maybe someone there could help you...?

---

### Post by PacShady on 2008-11-11
Just to test at theory, what graphics cards are you all using? I have a distinct feeling maybe ATI cards have no problems with KDE 4 whereas nVidia cards are useless. Can anyone verify/disprove this for me?

'Shady

---

### Post by aged hippy on 2008-11-11
I'm using an ATI Radeon 9800 Pro, but i had to install the drivers manually, as the installed ones insisted on a desktop ~900 x something.

---

### Post by _Azrael_ on 2008-11-12
I must agree with the general consensus on this thread. I have yet to experience the latest KDE as it should be on my Dell Vostro 1400 (Core2 T7250 @2GHz, 2GB RAM and the nefarious [and useless] Intel GMA 965).

Man it looks good though! Ibex too looks better than the vanilla KDE...

---

### Post by Anusiya on 2008-11-20
I noticed that firefox hogs CPU usage but left to itself Intrepid is fine. I am guessing X rendering with firefox has got something to do with it as htop shows 90% CPU usage for X when firefox is running. SOmething to do with drivers? Can someone run top or htop when firefox is running and confirm?

---

### Post by prankst3r on 2008-11-20
> **aged hippy said:**
> It should run like a hungry lurcher on your machine. :D

I don't wish to advertise another Forum, but there have been several video-related problems raised at the Kubuntu Forums, maybe someone there could help you...?

Well I've pretty much given up on Kubuntu 8.10 - the ISO CD is just another drink coaster for now. 

Maybe I'll give Kubuntu another shot when next April rolls around. I just want something that works and Vanilla Ubuntu (Gnome) has always seemed to be a reliable companion.

---

### Post by Yezinki on 2008-11-20
Smart Choice!

---

### Post by PacShady on 2008-11-22
I found some info on how to make an nVidia card run better under Linux, might be useful to make Kubuntu Intrepid work. Seems the problem isn't so much with KDE 4, but with nVidia's dodgy work on Linux drivers.

[http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916)

It's certainly sped things up a helluva lot on my Hardy lappy, anyone using Intrepid and has an nVidia card wanna give it a try and see if it helps at all?

Next time I buy a new graphics card, I'll be going ATI, nowadays they work MUCH better with Linux than nVidia thanks to AMD.

'Shady

---

### Post by Changturkey on 2008-11-29
Why don't you try KDE 4 on Debian or Arch?

---

### Post by dewert on 2008-12-07
I seem to be having the same problem - I have an ATI card though.  I'm currently using the ope source driver, but I've been switching back and forth in gnome - each seems to have advantages and disadvantages.  Proprietary one is stable for standard type of graphics - compiz, openoffice, firefox... except when I try to watch a video or do something 3-D accelerated.  Then it is jerky, and stops in the middle of things.  The open source driver works in these cases, but will randomly cause things to crash... less so if 3d effects are turned off.

Anyone know if there's an equally easy way to switch under kde4?  Sigh... I think ubuntu is ruining me with its GUI's.

I have turned off the KWin effects, and it seems better, but still kind of slow.  I have kde 4.1 on my laptop with intel 945GM, i believe, and it works quite well.  However, that was a manual install onto a hardy base system.  It's very eye-candied - I have either all KWin's effects, or about half of compiz's turned on - no hitch.  I do like desktop cube with KDE... :D

Running top while running only firefox (right now) I get python as my highest cpu user.  WTF?  It's eating ~30%!  Now the question is, what is it running?  Firefox is down at a modest 3%.  something called ld-linux.so.2 is taking up 50% of the memory though, which is not cool.  I don't think.  Let me check... no not cool: [http://ubuntuforums.org/showthread.php?t=754944](http://ubuntuforums.org/showthread.php?t=754944)

So... I'll try installing lsb, since I do have acrobat reader.  Not running actively, but maybe due to firefox...  I'll get back to you guys on that.

---

### Post by garba on 2009-01-17
just installed jaunty aplha3, succesfully installed the nvidia closed source drivers version 180.something straight from the repos (had to use the ignoreabi flag though) and yes kde 4.2 looks great actually it's more like it's something great to look at and that's it, can't do much more besides that ^^ resizing windows makes me seasick, every thing you could possibily do is jerky, slow, unresponsive... totally unusable... bottom line: on this 6yrs old machine (atlhonxp 2.2ghz and 1gig of ram) windows7 beta1 runs smooth as silk... it looks like i'll have to stick with hardy and kde 3.5 for the time being

---

### Post by geoffbeaumont on 2009-01-17
For what it's worth - I briefly tried Kubuntu 8.10 (amd64 build) on my laptop - Thinkpad T61 with Core2 Duo, 2Mb RAM but a fairly humble Intel 810i integrated graphics chip, and performance wise it was fine. I installed it for a quick play before installing Ubuntu, which I switched to a while back because I found nearly all the apps I was using were GNOME anyway, and was so impressed with the slick eye candy that I decided to keep it.

Unfortunately it only took one evenings use for me to realise that it was at best early beta quality - missing *major* functionality (usable package manager, for instance?!!), things crashing left right and centre and terrible integration of anything GNOME based (ugly themeing, more importantly unusable fonts. The latter I'm sure I could have sorted out given time, but it was already obvious that Kubuntu wasn't ready for everyday use, so I wiped it an put Ubuntu on instead. Still struggling to see how Ubuntu allowed Kubuntu 8.10 to be released!

Geoff

---

### Post by PacShady on 2009-01-17
Hey guys, found something that might help you out a lot with how slow KDE 4 is.

[http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916)

Turns out nVidia drivers for Linux aren't so good for 2D rendering as they are for 3D rendering. This link will give you some tweaks you can make to your xorg.conf and such that will greatly improve nVidia's 2D rendering. It's designed for 17* drivers (I'm running 177.82 on my Hardy laptop right now and works great for other 2D rendering problems I've had), but hopefully it might work for 180 drivers too. If not, try removing the 180 drivers and install the 177 drivers instead from nVidia's page and then applying these tweaks.

Hope it helps!

'Shady

---

### Post by PacShady on 2009-01-17
Whoops, didn't realise I've already posted this link in this thread already :p LOL, oh well twice the fun!

---

### Post by Faolan84 on 2009-01-25
Well after trying Kubuntu 8.10 for a week or so I've decided Gnome is the way to go. My system:

- P4 @ 2.26 GHz
- 764 MB DDR RAM
- ATI Radeon 9600SE w/ 128 vRAM
- Cyberdrv CW058D CD-R/RW *
- Samsung DVD-ROM 616-F
- Generic Floppy

Also I would like to not that my CD-R drive hates wodim and cdrecord, but burning with cdrdao works like a charm.

The fact is that Gnome runs so much more smoother than the recent incarnate that is KDE 4.x. I would use 8.04, but it's only supported until Oct 2009 and there is no telling if KDE 4.x will be a solid system by then and the various kinks are extremely irritating. I think KDE 4.x is the only DE I've ever used that has went into a hard freeze where CTRL+ALT+BACKSPACE does nothing.

---

### Post by Pillage Idiot on 2009-04-04
I have an asus m3a board, amd7750, 2gb ddr800, and a cheap nvidia card.
I went straight to 8.10 64 bit from 8.04 32 bit.
Mine runs like a cut cat.
KDE 4.2 is a bit better, and has fixed my full screen flash issue (it wouldn't on 4.1).

I also have the 32 bit version running KDE 4.1 on two old Toshiba TE2100s, and it runs just as well as KDE 3.5. The nvidia drivers won't run on these though.
Apparently the huge tidy up to the KDE base has exposed a lot of serious issues with the nvidia drivers, which seem to be getting fixed quite quickly.

My xorg.conf files on all of these are almost completely empty with no references to video hardware. X is doing fine by itself.

 I have seen some posts of problems with speed, and they mostly seem to be 32 bit on newer platforms. If you can support it give the 64 bit a go, I was amazed at how seemless the 32 bit handling is now. It doesn't even give pause for thought it is so good. The last time that I used 64 bit was ubuntu 6.10, and that was so much hassle that I went straight back to 32 bit.

I am amazed at how far these systems have come just a couple of years.

---

