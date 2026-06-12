---
title: "Jaunty Jackalope upgrade + ATI X1650 Driver?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Imoen on 2009-04-23
> This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 9.04. Do you want to continue?

If I do this update then will my video card not work? Anyone else with this video card already updated? If so please advise me on any issues to expect.

---

### Post by BubuXP on 2009-04-23
I've installed Jaunty some minutes ago on a motherboard with integrated ATI HD 3200.

I installed the fglrx drivers and at the reboot the login screen was impossible to see and unusable.

In another forum someone suggest to run this command right after the installation and before the reboot:

sudo aticonfig --initial -f

but I think that if you boot with a safemode kernel with your unusable machine it should work.
If the command doesn't work in safeboot, at least one can remove the driver, restore the video configuration and then reinstall the driver and run the command.
But I haven't tried this yet, don't know if this really works.

---

### Post by kshane on 2009-04-23
> **Imoen said:**
> If I do this update then will my video card not work? Anyone else with this video card already updated? If so please advise me on any issues to expect.

Just did the upgrade myself.  I have the same card (X1650Pro).  I am unable to use Jaunty, at this point.  My system slows to a crawl and is unusable.

So, in a nut shell, I'd wait for the new ATI driver.

Kevin

---

### Post by plysovej_kaktus on 2009-04-23
I've tried that few days ago on X1600 Mobility. No it won't. And in addition, xserver freezes with broken graphics, alt+F1 2 3 .. is not working and only i can is pushing the power button. Then it shuts smoothly, but i can't do anything despite of killing gdm while loading to try fixing that. I tried 9.1 9.2 9.3 and 9.4. When you will be trying, before restart, try to load module fglrx. If there will be message "can't somethhing memory bla bla", do not shut down xserver before uninstall. Now, I'm running ATI driver, but it has only GL 1.2 :/

---

### Post by plysovej_kaktus on 2009-04-23
> **BubuXP said:**
> 

sudo aticonfig --initial -f



no way, i've tried.

---

### Post by BubuXP on 2009-04-23
:(
I found a related discussion, maybe can help:
[http://ubuntuforums.org/showthread.php?p=6927575](http://ubuntuforums.org/showthread.php?p=6927575)

---

### Post by plysovej_kaktus on 2009-04-23
> **BubuXP said:**
> :(
I found a related discussion, maybe can help:
[http://ubuntuforums.org/showthread.php?p=6927575](http://ubuntuforums.org/showthread.php?p=6927575)

I've tried almost everything, what google offered. Only approach was to NOT install restricted fglrx driver automatically. Now, I've installed new clean and shiny jaunty. So let's try it again.

---

### Post by plysovej_kaktus on 2009-04-23
9-1: better way, fglrx module loaded, but now, I'm running in low graphics mode.


Xorg.0.log:
```
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: miInitVisualsProc
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(EE) module ABI major version (1) doesn't match the server's version (2)
(II) UnloadModule: "dri"
(II) Unloading /usr/lib/xorg/modules/extensions//libdri.so
(EE) Failed to load module "dri" (module requirement mismatch, 0)
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "vesa"

```

---

### Post by plysovej_kaktus on 2009-04-23
for the first problem ( undefined symbol: miInitVisualsProc )

this is an solution for fedora:

[http://www.nabble.com/-Bug-47121--NEW%3A-Loading-GLX-module-fails-due-to-undefined-symbol-miInitVisualsProc-to21531374.html#a21531713](http://www.nabble.com/-Bug-47121--NEW%3A-Loading-GLX-module-fails-due-to-undefined-symbol-miInitVisualsProc-to21531374.html#a21531713)

but
```

update-alternatives --display gl_conf

```
gives me no alternative.

---

### Post by BubuXP on 2009-04-23
Reinstalled a clean copy of Jaunty.
After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-voodoo

After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
Next step, opened a terminal and typed:
sudo aticonfig --initial -f
Finally, I crossed my fingers and reboot. And I'm still here :-D

Compiz works fine and also Google Earth 5 from Medibuntu repository runs smooth (but with compiz or minimal effects enabled the earth start to flash and is unusuable).

Remember that I have an integrated HD 3200 VGA.
Hope will work with someone else.

---

### Post by plysovej_kaktus on 2009-04-23
ATI X1600 mobility: 

   9-1: glx ABI fglrx errors, aticonfig --initial -f works
        modprobe fglrx doesn't work ( permission denied, while root ?!? )
        after reboot, fails into lowgraphics
   9-2: glx fglrx errors, aticonfig --initial -f works
        modprobe fglrx works
        after reboot, fails into lowgraphics
   9-3: (8.593) glx fglrx errors, aticonfig --initial -f works
        after reboot, fails into lowgraphics
   9-4: (8.602) aticonfig --initial -f says no supported addapter
        after reboot, broken graphics, keyboard not responding
   ???: (8.600) aticonfig --initial -f says no supported addapter
        after reboot, broken graphics, keyboard not responding

  .. maybe this is a reason, why automatic installing restricted drivers was disaster for my computer ... X1600 seems to be no longer supported since 9-4

---

### Post by Imoen on 2009-04-23
> **kshane said:**
> Just did the upgrade myself.  I have the same card (X1650Pro).  I am unable to use Jaunty, at this point.  My system slows to a crawl and is unusable.

So, in a nut shell, I'd wait for the new ATI driver.

Kevin

Thanks, I think I will do just this. I'm kind of new to Ubuntu/Linux so how to fix an issue is something I'm still learning and I'm not confident to try fixing these big problems just yet. :)

---

### Post by plysovej_kaktus on 2009-04-23
> **BubuXP said:**
> Reinstalled a clean copy of Jaunty.
After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-voodoo

After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
Next step, opened a terminal and typed:
sudo aticonfig --initial -f
Finally, I crossed my fingers and reboot. And I'm still here :-D

Compiz works fine and also Google Earth 5 from Medibuntu repository runs smooth (but with compiz or minimal effects enabled the earth start to flash and is unusuable).

Remember that I have an integrated HD 3200 VGA.
Hope will work with someone else.

Have you any errors/warnings in logs?

please attach output of 

```

 dpkg --list | grep glx

```

---

### Post by BubuXP on 2009-04-23
your problem is that your VGA is supported until version 9.3 of fglrx.
Version 9.4 won't work with your VGA.

Then, in Jaunty, there is the new X.Org server 1.6 that is compatible only with fglrx from version 9.4+.
So, older version of fglrx will not work on jaunty.

Your only chanche is to install some open source driver. My only reference to these drivers is Wikipedia:
[http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS#ATI.2FAMD](http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS#ATI.2FAMD)
but some expert user can tell you more.

---

### Post by BubuXP on 2009-04-23
> **plysovej_kaktus said:**
> Have you any errors/warnings in logs?
no errors, I followed the packages installation from the Synaptic terminal window and nothing was wrong.

here's the output:

dpkg --list | grep glx

ii  libgl1-mesa-glx                            7.4-0ubuntu3                      A free implementation of the OpenGL API -- G
ii  libglitz-glx1                              0.5.6-1                           Glitz OpenGL library GLX backend
ii  rss-glx                                    0.8.2-1ubuntu3                    Really Slick Screensavers GLX Port

---

### Post by plysovej_kaktus on 2009-04-23
> **BubuXP said:**
> your problem is that your VGA is supported until version 9.3 of fglrx.
Version 9.4 won't work with your VGA.

Then, in Jaunty, there is the new X.Org server 1.6 that is compatible only with fglrx from version 9.4+.
So, older version of fglrx will not work on jaunty.

Your only chanche is to install some open source driver. My only reference to these drivers is Wikipedia:
[http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS#ATI.2FAMD](http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS#ATI.2FAMD)
but some expert user can tell you more.

ughhg... my only dream about opengl3 has gone with my old computer. It seems only solution is stay with ibex, open source drivers doesn't support gl2, which i'm developing in. ... it's time for new computer.

---

### Post by BubuXP on 2009-04-23
> **BubuXP said:**
> Reinstalled a clean copy of Jaunty.
After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-voodoo

After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
Next step, opened a terminal and typed:
sudo aticonfig --initial -f
Finally, I crossed my fingers and reboot. And I'm still here :-D

Compiz works fine and also Google Earth 5 from Medibuntu repository runs smooth (but with compiz or minimal effects enabled the earth start to flash and is unusuable).

Remember that I have an integrated HD 3200 VGA.
Hope will work with someone else.

While I'm at it, I'm trying the 64 bit version of Jaunty.
Repeated the same as above and it works well also on 64 bit.


The aticonfig command could help someone:

sudo aticonfig --initial=check
will check if the configuration file have the fglrx section.
Running this command right after the driver installation tells me that the section is absent.

sudo aticonfig --initial -f
will write the fglrx section on the configuration file. The -f option needs to force the writing

if you need the full list of option:
aticonfig > /eventualpath/textfile.txt
and read the text file created, because the list is bigger than the terminal buffer.
P.S.: the boot time on the 64bit version is even smaller than 32bit :)

---

### Post by sansa dude on 2009-04-23
ho well is my x1650 pro card in desktop computer supported in jaunty? right now im just using the defaults

---

### Post by darojasp on 2009-04-24
Ok guys, just surfing through the web I found this [link in the ATI web page]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English"). The problem, according to this [article]("http://www.linuxpromagazine.com/online/news/proprietary_driver_for_ubuntu_9_04_fglrx_for_x_server_1_6?category=13413"), is that the driver 9.3 from AMD is not compatible with X.org 1.6. ATI offers support for this version of X.org but only to newest hardware (you can see the list of no longer supported hardware in the first link).

As I see it know, we have to either create a new driver, or conform with the slow and "open" ati driver or not update at all.

---

### Post by StuartN on 2009-04-24
> **sansa dude said:**
> ho well is my x1650 pro card in desktop computer supported in jaunty? right now im just using the defaults

X series cards are not supported in Catalyst 9.4, according to the ATI documentation at [http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx) (nor is the Xpress 200m in my Dell Inspiron 1501).

---

### Post by HAL5000 on 2009-04-24
Unfortunately I experience the same issue... 

It would be nice if I could (painlessly :confused:) downgrade to 8.10 which worked fine for me.

---

### Post by StuartN on 2009-04-24
> **HAL5000 said:**
> Unfortunately I experience the same issue... 

It would be nice if I could (painlessly :confused:) downgrade to 8.10 which worked fine for me.

I'm sticking with 8.10 or upgrading to Debian Lenny.

---

### Post by s3lekta on 2009-04-24
another user tried this and worked -->

[http://ubuntuforums.org/showthread.php?t=1133931&page=2](http://ubuntuforums.org/showthread.php?t=1133931&page=2)

---

### Post by Dave in Tempe on 2009-04-24
Well, all I have to say is this guy with a 200m xpress card laptop\ will be going with nVidia for my next purchase.

---

### Post by Redsunz on 2009-04-24
I have a 4870 X 2 and it also won't work on Jaunty Jackalope.
Its not just the old hardware.
I'm definitely going with Nvidia for my next video card!!
I tried the ATI terminal install and when I reboot the screen is unreadable. Same thing with using restricted drivers from the Hardware Drivers menu.
8.10 worked fine may be I should go back to that one?

---

### Post by anonymousT on 2009-04-25
does turning off your desktop effects stop the flickering?

I used to use the fglrx driver which has some bug that makes video playback and certain applications to flicker that it becomes unusable if the desktop effects is turned on.

Now, I'm using the default xorg driver that comes with a fresh jaunty install, and so far it looks like video playback is normal with desktop effects on. So, in a way it's better than the fglrx driver.

My only worry is that it doesn't have the powerplay (the ati power saving feature) when before I could use aticonfig --set-powerstate to engage the powerplay. But I did read somewhere that the xorg driver has its own powersaving features.

---

### Post by cutterjohn on 2009-04-25
Actually I read the other day that ATI relented with the catalyst X11 drivers and did release a version of 9.04 for them(no Xserver 1.6 support though from what I recall), but I didn't really pay much attention to it. (Mobility Radeon 4850HD -- installing Ubuntu 8.10 was fun though as I had to take a trip to the past and use the alternate text mode install CD and have loads'o'fun manually configuring things to get enough of a build environment to install catalyst drivers(9.1).)

--> So my $0.02 is: if you're serious about your gfx go nVidia, as they just get it, OSS fanboi BS aside...  (Also nVidia seems to have devs who know WTH they're doing... last ATI card for me ever.)

---

### Post by mendieta on 2009-04-28
I agree with the general sentiment. I bought a new system with an ATI HD 3200 on board and it broke in Jaunty. There is no way to file a bug report or contact ATI. 

On the other hand, they are promoting Open Source drivers, which I love. So, what I will do is:

* Wait for one more Catalyst release ((should be around in about three weeks)

* If that doesn't work, get an affordable NVidia card to get going.

* Use that card for the next year or so, and see if the ATI open source drivers get competitive 3D acceleration. If they do, my next upgrade will be ATI. Otherwise, I'll stick to NVIDIA (I never had issues with them).

At least, with the radeon driver I can do Hulu in High Def with no issues whatsoever. But games, forget about it.

---

### Post by emarkay on 2009-05-01
Yes, here is the thread for this issue: 

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by salehram on 2009-05-12
sorry for replying on the old topic.. but

about this thing...
i have installed the 9.04 ubuntu on a laptop with ATI HD3200
so.. all what i have to do is removing these unused packages and install the fglrx driver and that's it???

i've been trying this since one week and each time i destroy my xorg server and screw the whole thing...

---

### Post by flang3r on 2010-03-24
Here is some guide to make it work. I haven't tried it yet but I will!

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

