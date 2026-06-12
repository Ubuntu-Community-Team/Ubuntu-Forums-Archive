---
title: "Lenovo X200 Owner's Thread"
date: 2008-09-02
forum: Hardware
---

### Post by nate_2001 on 2008-09-02
So far, the newest ultraportable offering from Lenovo is very close to being fully compatible with Ubuntu 8.04 amd64 directly out of the box.

These two things need to be done to get it fully functioning:

Wi-fi:  [http://ubuntuforums.org/showpost.php?p=5657450&postcount=16](http://ubuntuforums.org/showpost.php?p=5657450&postcount=16)  (The poster indicates that the instructions don't work for him, but if they're followed closely, they work for the X200).

Intel Video drivers:  [http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/](http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/) 

To install this deb, you have to use apt-get to remove the default driver package, but after that, installation goes well and enables 2d and 3d support.

Suspend to RAM is not working for my configuration.  I'll re-post if I find a solution.  

Trackpoint:

For vertical/horizontal scrolling using the middle mouse button, replace the automatic xorg.conf entry with:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2" 
       Option "YAxisMapping" "4 5"
       Option "XAxisMapping" "6 7"

EndSection
```

Fingerprint reader does not work.

---

### Post by matlabwarrior on 2008-09-05
Thanks for the post. I have ubuntu running on my x200 just fine. I have some minor issue. Did you get the webcam to work? When I try to use the cam in skype the machine just locks up but the light comes on next to the cam.

---

### Post by TheCan on 2008-09-05
Hi,

First of all, thanks for basic information about that the X200 is working fine with Ubuntu 8.04. I would be very interested if any of the external Monitor outputs is working in Ubuntu with the X200. Especially I'd like to know whether the VGA Output is working for connecting the X200 to a beamer and the Displayport Output in the Docking station with an external (preferably high resolution like WUXGA) DVI-connected display.

Thanks a lot in advance.

---

### Post by simon.sigre on 2008-09-06
My new x200 is about 5 days away i cant wait; how do people apply bios/firmware updates here without windowz?

---

### Post by justincwatt on 2008-09-09
I wrote up a post on how to get the [ThinkPad wireless card to work in Ubuntu 8.04 on an X200]("http://justinsomnia.org/2008/09/getting-wireless-to-work-in-ubuntu-on-a-lenovo-thinkpad-x200/"). Figured that might save some folks some time. 

Regarding webcam support, I just installed Cheese, ran it, saw the webcam light flash, then stay on, and Gnome totally froze. Well I could move my mouse but that was about all. Couldn't even Ctrl+Alt+Bksp. Not sure I want to try again.

Update: more info in this thread: [http://bugzilla.gnome.org/show_bug.cgi?id=551463](http://bugzilla.gnome.org/show_bug.cgi?id=551463)

---

### Post by Ub1476 on 2008-09-16
My X200 is running much hotter with Ubuntu than Vista. Fan is actually also on (which it is not with Vista). Also, battery life is worse..

Is this because I use amd64 or is it Ubuntus fault?

---

### Post by simon.sigre on 2008-09-20
Looks like the bug with the blackscreening has been resolved now.. and has been pushed into the ibex stream.. holy!

---

### Post by tlf1138 on 2008-09-22
Hi. I'm a noob here, eh? My X200 should be in my hands within days and I just had a few questions.

1) Will the webcam be supported in Intrepid Ibex? Is there any hack that gets it working with Hardy Heron?

2) Is the 3D acceleration for the X200's Intel X4500 (I believe that's the model anyways) supported in Intrepid Ibex out of the box? Does the method described here to support the X200's integrated graphics support full 3D acceleration?

3) Is there support for the Intel 5300 wireless a/b/g/n option? (I bought this almost on impulse.) If not, will Intrepid Ibex support it? 

4) How about the GPRS/WiMAX modem? Will Intrepid Ibex support that (Mark Shuttleworth has said that there will be support for this type of wireless in general for Intrepid Ibex.)

Thanks in advance! I might be asking the wrong people. If I don't get a response, I'll open a thread in the Intrepid Ibex forum(s.)

---

### Post by nate_2001 on 2008-09-23
I do not have a webcam on my configuration.

I'm getting an external monitor today, so I will let you know if the outputs work.

As for battery life and heat, I've not noticed a significant heat issue.  I'm always below 40 C according to the sensors.  Battery life is lower.  I got about 5.5 hours of normal use on a 9-cell battery.  This is a continuous laptop issue with Ubuntu ... you can search about using Intel Powertop.  I folks have any other suggestions, I'd love to hear them.

---

### Post by henry44 on 2008-09-24
The suspend to ram (hibernation) thing works if you configure it in 
system >> preferences >> power management.

I can close the lid, or use the power button to put my x200 into hibernation mode. This is with the AMD64 OS.

I, too am getting about 5.5 hours from a 9-cell battery that got 7 hours in Vista 64-bit. The fan runs all the time on both AC and battery, just slower on battery. 

I hate Vista and feel that 1.5 hours of battery life is a fair trade to rid myself of that pox on human kind. 



I have a question for you all. How do I change the amount of shared video ram? I have 4 gb and want to send the max to the video card.

Thanks..............

---

### Post by nate_2001 on 2008-09-24
Like most things, the VGA out works and it does not work.  It is not 'hotplug'-able, but it will work when properly configured.  I haven't gotten cloned monitors up yet using xrandr, but I think it will be possible once I further configure the xorg.conf file.  I have not had much trouble getting the external monitor to work without the laptop monitor working.  But it's one or the other, so not useful for giving presentations.

Like I said, I fully expect this to work fully once I learn to configure it better.

---

### Post by TheCan on 2008-09-24
Thanks a lot for the information nate_2001! Did you buy your X200 together with the Ultrabase? My primary interest is whether the Displayport Connector works with an DVI-Adapter to connect an external display with reasonable signal quality.

What kind of Monitor did you attach to the VGA output? And did you notice any signs of a bad signal quality? I am planning to attach the X200 to a 26" TFT with WUXGA (1920x1200) that's why signal quality would be really important for me.

And you are running 8.04, not Intrepid? I wouldnt recommend trying Intrepid right now since the current Alpha might permanently damage your network controller. (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555))

Could you post the output of "randr" once your external monitor is attached? There is a good randr Howto in the German Ubuntuusers.de-Wiki about how to get it to work: [http://wiki.ubuntuusers.de/RandR](http://wiki.ubuntuusers.de/RandR)

It also links to three english articles on this topic, hope that helps you.

---

### Post by nate_2001 on 2008-09-24
I don't have the base, this was through the VGA out on the machine.  I connected it to an acer 22" widescreen LCD.  It seemed like the quality was fine, but I still have to fine tune it.  When I get home tonight, I'll try to find time to work it out and post my xrandr output.

---

### Post by simon.sigre on 2008-09-29
Hey guys; how awsome are these boxes?? Well other than the fact that the HDD accelerator (flash cache) isnt supported, GB-ETH dosent work and finger print reader do-sent seem to be supported by any of the standard packages.

End Rant; hey whats the deal with the usb port on the right hand side? Ibex dosent appear to pick up anything plugged into it.. yet on the left hand side, not probs.. argh!

Have you guys tried compiling the intel video drivers for X from source? they actually work pretty well; other than that.. this laptop is driving me crazy..

---

### Post by arnstein on 2008-10-01
I own a Lenovo X200, and I'm running Intrepid. 

From what I see, there's very little documentation available about this combination, so sharing my little pieces of advice.

1. Intrepid does not recognize that the machine can suspend, so pm-suspend by default etc, does not do anything. Currently this can be overcome by adding creating a file in /etc/pm/config.d/ with the contents
SLEEP_MODULE=kernel 
This bug is not an exclusive X200 bug.

2. Once this is done, the X200 suspends, but does not restore properly. I tried all sorts of quirks with pm-suspend, but nothing works. Finally, I changed my Xorg driver to "vesa", and now suspend works beautifully. (Sigh, I lose compiz though.) I still haven't found any bug report against this, probably because of the confusion caused by the first bug.

Everything else works beautifully, and almost out of the box. (The GigE ethernet is of course currently disabled, if you've been following the news: there's a bug in the e1000e driver which can permanently damage your ethernet card.)

---

### Post by fowlstar on 2008-10-03
In response to an earlier post about the x200 integrated webcam, I too had problems with cheese/luvcview/skype all causing gnome to freeze up after showing a black box and then a full black screen. I couldn't ctrl+alt+backspace to reset X, so I had to hard reset each time. I figured out that the x200 integrated webcam is uvc-friendly (lsmod |grep uvc).

I also ran into the same problem of having to resort to hard resets while viewing videos (.avi files).

After a bit of experimentation, I tried these three sites (in the order listed below; the last site I had previously installed the drivers for, uninstalled them, and then re-installed them again):

[http://ubuntuforums.org/showthread.php?t=593231](http://ubuntuforums.org/showthread.php?t=593231)
[http://ubuntuforums.org/archive/index.php/t-793513.html](http://ubuntuforums.org/archive/index.php/t-793513.html)
[http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/](http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/)

...and must have done a hard-reset one-time too many (I'm new to Ubuntu and Linux), because the next time I booted up, cheese and luvcview worked fine, though skype would just shut itself down as soon as I used the "test" option for the webcam.

As for the video playback, upgrading to the new intel drivers did the trick.

---

### Post by me13221 on 2008-10-05
I don't know what it is I did wrong, but maybe you guys can help me.  Apparently Intrepid is supposed to "just work" on the X200, but for me it's more like "just doesn't work."  I just did a fresh install to disk from the 20081004 daily-live build and have the following issues.  I'd appreciate any help in resolving them:

 - Screen resolution is wrong.  I added a 1280x800 Mode to xorg.conf but it comes up screwy--- the "bottom" gnome panel is offset from the bottom of the screen by about 40 pixels, and the screen appears to run off the right-hand edge of the display by an unknown number of pixels.  This problem is evident both in the gdm login screen and on the gnome desktop.  It *is* a 1280x800 screen, right?  That's what lenovo says...

 - wifi card is not detected. ath5k and ath_pci are loaded but don't do anything.

 - (of course, e1000e is disabled so I'm kinda screwed)

 - VT console font is too large (also probably a screen resolution thing). when I added vga=791 to the grub menu.lst I lost virtual terminals completely.

And forget about the acpi, webcam, etc.  I don't dare to even test those at this point.

I'd appreciate any recommendations.

---

### Post by me13221 on 2008-10-05
A few updates:

>  - Screen resolution is wrong.  I added a 1280x800 Mode to xorg.conf but it comes up screwy--- the "bottom" gnome panel is offset from the bottom of the screen by about 40 pixels, and the screen appears to run off the right-hand edge of the display by an unknown number of pixels.  This problem is evident both in the gdm login screen and on the gnome desktop.  It *is* a 1280x800 screen, right?  That's what lenovo says...

So I took a screenshot from GIMP and the size of the resulting image was 1360x800. wtf?  The image shows the weird floating bottom-panel.

[http://301south.net/wrong-size-desktop.png](http://301south.net/wrong-size-desktop.png)

FWIW, here's my xorg.conf file:

[FONT="Fixedsys"]
Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    SubSection "Display"
        Depth 24
        Modes "1280x800" "1024x768"
    EndSubSection
EndSection
[/FONT]


>  - wifi card is not detected. ath5k and ath_pci are loaded but don't do anything. 

In 'dmesg | grep ath' I get the following:

[[FONT="Fixedsys"]...
[   12.240069] ath_hal: module license 'Proprietary' taints kernel.
[   12.241111] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   12.281171] wlan: 0.9.4
[   12.287699] ath_pci: 0.9.4
[   12.287740] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.287751] ath_pci 0000:03:00.0: setting latency timer to 64
[   12.336429] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   12.336447] ath_pci 0000:03:00.0: PCI INT A disabled
...
[   12.610268] ath5k_pci 0000:03:00.0: enabling device (0000 -> 0002)
[   12.610277] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.610290] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   12.610316] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   12.620339] ath5k phy0: failed to wakeup the MAC Chip
[   12.620360] ath5k_pci 0000:03:00.0: PCI INT A disabled
[   12.620366] ath5k_pci: probe of 0000:03:00.0 failed with error -5
...
[/FONT]

>  - VT console font is too large (also probably a screen resolution thing). when I added vga=791 to the grub menu.lst I lost virtual terminals completely.

I "fixed" this by switching back to vga=normal, and set about trying to select the font with /etc/default/console-setup.  however, I have not found any fonts that give me more than 80 columns, which is disappointing.

---

### Post by arnstein on 2008-10-05
> **me13221 said:**
> I don't know what it is I did wrong, but maybe you guys can help me.  Apparently Intrepid is supposed to "just work" on the X200, but for me it's more like "just doesn't work."  I just did a fresh install to disk from the 20081004 daily-live build and have the following issues.  I'd appreciate any help in resolving them:

 - Screen resolution is wrong.  I added a 1280x800 Mode to xorg.conf but it comes up screwy--- the "bottom" gnome panel is offset from the bottom of the screen by about 40 pixels, and the screen appears to run off the right-hand edge of the display by an unknown number of pixels.  This problem is evident both in the gdm login screen and on the gnome desktop.  It *is* a 1280x800 screen, right?  That's what lenovo says...

Change the driver to "vesa", everything works. However compiz will not work. But you'll need "vesa" for suspend to work without crashing.

If you really want to use compiz, and not care about suspend, then a workaround would be specify 1280x800 in xorg.conf, and then set the resolution as 1280x800 in the gnome screen-resolution applet.

> **me13221 said:**
>  - wifi card is not detected. ath5k and ath_pci are loaded but don't do anything.

Hmm, can't help here, I have the Intel wireless which works out of the box.

> **me13221 said:**
>  - (of course, e1000e is disabled so I'm kinda screwed)

apparently this has been fixed. I might wait a while before trying it :-) 

> **me13221 said:**
> And forget about the acpi, webcam, etc.  I don't dare to even test those at this point.

I'd appreciate any recommendations.

webcam works. You'll notice that your fan always runs at full speed. (The speed increases from 0, but never decreases.) Suspending and resuming brings the fan back to 0, so another reason to use the vesa driver.

---

### Post by cleverselfreferentialname on 2008-10-07
> **henry44 said:**
> The suspend to ram (hibernation) thing works if you configure it in 
system >> preferences >> power management.

I can close the lid, or use the power button to put my x200 into hibernation mode. This is with the AMD64 OS.

I, too am getting about 5.5 hours from a 9-cell battery that got 7 hours in Vista 64-bit. The fan runs all the time on both AC and battery, just slower on battery. 

I hate Vista and feel that 1.5 hours of battery life is a fair trade to rid myself of that pox on human kind.

Heh, see the package laptop-mode-tools and see if anything in there is helpful. Report back for all our benefits.

EDIT: see the output of 'dpkg -L laptop-mode-tools' and start inspecting the tools. Things can be done to reduce heat/increase battery life. hdparm can be used to mess with the frequency with which disk spins up, but I haven't run ubuntu for so long, I don't know if the defaults are sane yet. (I run Debian on a desktop.)

ANOTHER EDIT: If/when SSDs become standard, we won't have to worry about disk stuff.

> I have a question for you all. How do I change the amount of shared video ram? I have 4 gb and want to send the max to the video card.

Thanks..............

IIRC it maxes out at 768 and takes it at will, but I really have no idea for sure. If you're using the vesa driver it's probably not being used much.

---

### Post by ashaw on 2008-10-08
Same problems w. my display after editing Xorg.conf - it's easy enough to drag and drop the bottom panel back in it's proper position, but this too-wide-screen thing is really annoying.

Off to experiment w. the suspend -rm workarounds before switching to Vesa.
[B]
Update:[/B] For the moment, I'm settling for the Vesa driver, which at least provides the capability for 12800x800 resolution and also does a better job supporting some hibernate/suspend activities. With this configuration, the screen resolution applet seems to think the refresh rate is 0 HZ, but it's obviously confused.

Does anybody know if the current intel_drv.so in /usr/lib/xorg/drivers/modules supports the 4500MHD card in the X200? (According to [this thinkwiki post]("http://www.thinkwiki.org/wiki/Installing_Debian_on_an_X200") it should be v2:2.3.2-1)

I upgraded all the Ibex packages and installed the 2.6.27-6 kernel this morning, but I'm not sure if this driver was included or not...

If this driver update can/must be done manually, can someone point me towards a step-by-step how-to for adding experimental packages?

---

### Post by eater on 2008-10-08
Regarding the suspend-to-RAM problem -- have you tried installing the hibernate package (and perhaps tweaking its config file)? That worked like a charm for me in Hardy with a similar problem (different ThinkPad). Just run "hibernate-ram" when you want to suspend (and if that works, map it to the lid sensor).

Regarding the fan problem -- have you played around with the suggestions <a href="http://www.thinkwiki.org/wiki/How_to_control_fan_speed">here</a>? What was the result?

---

### Post by ashaw on 2008-10-08
> **me13221 said:**
> 

 - wifi card is not detected. ath5k and ath_pci are loaded but don't do anything.




For X200 Atheros wifi tips, check out [this thread]("http://ubuntuforums.org/showthread.php?t=905126")

---

### Post by ccc1 on 2008-10-09
> **me13221 said:**
> 
 - Screen resolution is wrong.  I added a 1280x800 Mode to xorg.conf but it comes up screwy--- the "bottom" gnome panel is offset from the bottom of the screen by about 40 pixels, and the screen appears to run off the right-hand edge of the display by an unknown number of pixels.  This problem is evident both in the gdm login screen and on the gnome desktop.  It *is* a 1280x800 screen, right?  That's what lenovo says...


how i fixed the resolution problem:

open system->screenresolution. Untick the box that says "mirror screens". A or i think two "new" monitors appear. disable them (set the resolution to off). now you can set the desired resolution on your primary monitor.

hoped it worked for you as well.

---

### Post by tlf1138 on 2008-10-10
Dear Ubuntuites,

There has been some progress since I downloaded one of the Intrepid Ibex alphas. The beta I just tried worked for the most part. I have tried to report the bugs I have found, only to find that Launchpad does not work (I can't log in.)

I am hoping that:

1) The time zone configuration utility in the installer will work properly. It calculates the local time incorrectly.

2) That the installer will work from the LiveCD. I have had trouble loading it. It also crashes (and I'd love to send some bug reports and maybe poke around with the debugger, but Launchpad doesn't like me.)

3) That the Intel 5300 wireless card will work as advertised. I have had success with it once, but all the other times I have tried it, the two little green blobs appear, but no bars. I am thinking that its maybe the DHCP stuff.

4) Somebody will improve the power management. C'mon people! If we want to beat Windows, we're going to need to be greener than it is.

5) Somebody will make the webcam work out of the box.

6) That the partitioner in the installer work right, and that the graphics be readable. 

Hopefully somebody will see this post and let the people who are working on 8.10 know about the bugs. I'd love to submit a bug and poke about in the beta, but Launchpad doesn't like me :(

---

### Post by ashaw on 2008-10-10
@cc1 - thanks for catching that. i didn't find the "invisible" display detected in the applet. now i can confirm that i've got xorg.conf using the intel driver and am getting 1280x800.

---

### Post by ccc1 on 2008-10-12
-----

---

### Post by Fischli on 2008-10-13
> **arnstein said:**
> ...
Hmm, can't help here, I have the Intel wireless which works out of the box.
...

For me the Intel wireless does not work (see separate post [1]). Which card do you have Intel WifiLink 5100 or 5300?

Are your running 32 or 64 bit version of intrepid?

[1] [http://ubuntuforums.org/showthread.php?t=945270](http://ubuntuforums.org/showthread.php?t=945270)

---

### Post by arnstein on 2008-10-13
> **Fischli said:**
> For me the Intel wireless does not work (see separate post [1]). Which card do you have Intel WifiLink 5100 or 5300?

Are your running 32 or 64 bit version of intrepid?


It does work for me, 64 bit intrepid with 5300 card.

---

### Post by ccc1 on 2008-10-13
anybody else owning the ultrabase for the x200?
is your audio-out on the ultrabase working? mine isn't ...

---

### Post by bluebook on 2008-10-15
ccc1 - mine isn't working either! I have their full support, so I thought it was a busted base. I was going to go check them out, but now you make me think it's not. I have no idea where I would start to look for a fix.


Also -- after today's updates, my Intel 5300 wireless card is busted again. I reinstalled the drivers that got it workign before (from [this post]("http://ubuntuforums.org/showpost.php?p=5754065&postcount=62")) but it's still not working. 

Anyone have any thoughts?

---

### Post by ccc1 on 2008-10-16
> **bluebook said:**
> ccc1 - mine isn't working either! I have their full support, so I thought it was a busted base. I was going to go check them out, but now you make me think it's not. I have no idea where I would start to look for a fix.

i thought at first as well that the base is broken, but then i noticed that the warning sounds are played over the speakers connected to the ultrabase.
guess we should report it on lauchnpad ...

---

### Post by banshee.berlin on 2008-10-16
I'd like to join the discussion.

First of all, I'm running an up-to-date AMD64 8.10 (originally from a recent kubuntu daily build). Wifi works just fine for me.

ccc1's tip helped to deal with the strange toolbar problem. That seems to have something to do with the following xrandr output:

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2560 x 1024
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+   50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI-1 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-2 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
```

The HDMI info is completely wrong, but those are the screens that strangely appear in the Monitor Resolution Settings. I have no idea how to get rid of this. Maybe there is a way to tweak the xorg.conf? Mine is still very close to the default one:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Modes "1280x800"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```


xrandr correctly detects an attached VGA display but I didn't manage to reliably activate it and switch back to LVDS (I'd prefer an xrandr command over any GUI setting). The vesa driver doesn't help me at all. Ideas, anyone?

---

### Post by feeldead on 2008-10-17
Godness! Thanks very much. I was so frustrated by the default driver of ubuntu 8.04 on x200. Everytime I play a video, the machine goes down and has no single response. Now the video is OK. But desktop effects don't work on the new driver. Did anyone have the same problem?

---

### Post by simon.sigre on 2008-10-18
Here in .AU the X200 cost me almost 3000AUD, and thus far im not super super happy with its *nix support.
One thing i was thinking about was. How do you know how your machine is running compared to other x200 Users?

What do people this about a few benchmarks and output to compare against other X200 users so we can compare how our rig is running in the larger scheme of things?

example:

    description: Notebook
    product: 745533M
    vendor: LENOVO
    version: ThinkPad X200


uname -a
//
Linux penfold 2.6.27-7-generic #1 SMP Fri Oct 17 22:24:21 UTC 2008 i686 GNU/Linux
\\


Running 'glxgears -fullscreen -info'
//
GL_RENDERER   = Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 7.2
GL_VENDOR     = Tungsten Graphics, Inc
894 frames in 5.0 seconds = 178.787 FPS
921 frames in 5.0 seconds = 184.191 FPS
\\

Running 'sudo lshw | grep UNCLAIMED'
//
        *-display:0 UNCLAIMED
        *-display:1 UNCLAIMED
        *-communication UNCLAIMED
        *-network UNCLAIMED
           *-memory UNCLAIMED
        *-serial UNCLAIMED

Display = Whats with this? 

Communication = Modem i assume?

Network =  My GB Ethernet Card; dont get me started im assuming that kernel bug screwed all of us?

Memory = Turbo Memory Controller, such a shame this wont work under *nix

Serial = Far Enough, i havent set it up yet
\\

Anybody else have some ideas about benchmark results / ideas?

---

### Post by aceFruchtsaft on 2008-10-19
Hello Ubuntu users!

I think I've found a way to make suspend and hibernate work with the intel driver on my X200 (I am using Gentoo but nonetheless the same procedure might work an ubuntu).

As some of you have noticed, the output of xrandr on the X200 gives something like:
```

timaios richi # cat /tmp/xrandr.txt
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1920 x 1200
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+   50.0
   1024x768       60.0
   800x600        60.3     56.2
   640x480        59.5
HDMI-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*
   800x600        60.3
   640x480        59.5
HDMI-2 disconnected (normal left inverted right x axis y axis)

```

.. but the X200 does not even have a single HDMI port!

Consequently, I disabled both HDMI ports adding this to my xorg.conf:
```

Section "Device"
    
    # ... skip other intel config
    Option  "monitor-HDMI-2" "FakeHDMI-2"
    Option  "monitor-HDMI-1" "FakeHDMI-1"
    Option  "monitor-LVDS"  "Monitor0"
EndSection

# Add 2 fake monitors
Section "Monitor"
    Identifier "FakeHDMI-1"
    Option  "Ignore"    "True"
EndSection                    

Section "Monitor"
    Identifier "FakeHDMI-2"
    Option  "Ignore"    "True"
EndSection    

```

... which results in the following xrandr output:
```

timaios richi # xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1920 x 1200
VGA connected (normal left inverted right x axis y axis)
   1024x768       60.0
   800x600        60.3
   640x480        59.5
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+   50.0
   1024x768       60.0
   800x600        60.3     56.2
   640x480        59.5

```

... and suddenly suspend and hibernate started to work!

If you use s2ram you will have to use the "-f" option to start suspend. If you are using pm-utils (or whatever the package might be called on ubuntu), you will thus have to add
```

S2RAM_OPTS="-f"

```
somewhere into /etc/pm/config.d/...

I hope this works on other systems as well, so could someone please verify this?

BTW: According to Intel developers on the Xorg developer mailinglist, **DisplayPort** is NOT supported in driver version 2.4.0 (xserver: 1.5.x) and probably won't be soon since they have other priorities.

As a reference, here's my complete xorg.conf (I use hal/evdev so I don't have any InputDevice sections in there):
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0     
EndSection                               

Section "Files"
        ModulePath   "/usr/lib64/xorg/modules"
        FontPath     "/usr/share/fonts/misc/" 
        FontPath     "/usr/share/fonts/TTF/"  
        FontPath     "/usr/share/fonts/OTF"   
        FontPath     "/usr/share/fonts/Type1/"
        FontPath     "/usr/share/fonts/100dpi/"
        FontPath     "/usr/share/fonts/75dpi/" 
    FontPath    "/usr/share/fonts/corefonts/"  
    FontPath    "/usr/share/fonts/mathematica-fonts/"
EndSection                                           

Section "Module"
        Load  "dri"
        Load  "extmod"
        Load  "glx"   
        Load  "record"
        Load  "xtrap" 
        Load  "dbe"   
        Load  "freetype"
EndSection              

Section "Monitor"
        Identifier   "Monitor0"             
        VendorName   "LEN"                  
        ModelName    "4010"                 
        Option      "DPMS"                  
    Option  "PreferredMode" "1280x800"      
EndSection                                  


Section "Monitor"
    Identifier "FakeHDMI-1"
    Option  "Ignore"    "True"
EndSection                    

Section "Monitor"
    Identifier "FakeHDMI-2"
    Option  "Ignore"    "True"
EndSection                    

Section "Device"
    Option     "DRI"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Unknown Board"
        BusID       "PCI:0:2:0"
    Option  "monitor-HDMI-2" "FakeHDMI-2"
    Option  "monitor-HDMI-1" "FakeHDMI-1"
    Option  "monitor-LVDS"  "Monitor0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
    DefaultDepth    24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        Modes   "1280x800" "1024x768" "800x600"
        Virtual 1920 1200
        EndSubSection
EndSection

Section "dri"
     Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

### Post by ccc1 on 2008-10-19
> **bluebook said:**
> ccc1 - mine isn't working either! I have their full support, so I thought it was a busted base. I was going to go check them out, but now you make me think it's not. I have no idea where I would start to look for a fix.

i reported the bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/285834](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/285834)

feel free to confirm it. 

ccc1

---

### Post by arnstein on 2008-10-19
> **simon.sigre said:**
> 
Running 'glxgears -fullscreen -info'
//
GL_RENDERER   = Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 7.2
GL_VENDOR     = Tungsten Graphics, Inc
894 frames in 5.0 seconds = 178.787 FPS
921 frames in 5.0 seconds = 184.191 FPS
\\


Same here, so no worries:


glxgears -fullscreen
877 frames in 5.0 seconds = 175.272 FPS
902 frames in 5.0 seconds = 180.339 FPS

---

### Post by arnstein on 2008-10-19
I tried the Intel driver again, without any xorg.conf changes, and many suspends-and-resumes later, everything seems to be working fine. Something got fixed along the way, can others confirm this?

---

### Post by simon.sigre on 2008-10-20
> **arnstein said:**
> Same here, so no worries:


glxgears -fullscreen
877 frames in 5.0 seconds = 175.272 FPS
902 frames in 5.0 seconds = 180.339 FPS




How about the rest? Hows your lshw looking?

---

### Post by vishketan on 2008-10-20
Hi

Can somebody post a link to this statement?

According to Intel developers on the Xorg developer mailinglist, DisplayPort is NOT supported in driver version 2.4.0 (xserver: 1.5.x) and probably won't be soon since they have other priorities. 

A quick Google search did not lead to anything relevant except for the following links:

[http://lists.freedesktop.org/archives/xorg-announce/2008-July/000621.html]("http://lists.freedesktop.org/archives/xorg-announce/2008-July/000621.html")

[URL="http://www.phoronix.com/scan.php?page=news_item&px=NjUzOA"]
http://www.phoronix.com/scan.php?page=news_item&px=NjUzOA
[/URL]

Is there anybody else out there using the ultrabase? Can you post your experiences with Intrepid beta?

vishy

---

### Post by banshee.berlin on 2008-10-20
> **vishketan said:**
> Can somebody post a link to this statement?

According to Intel developers on the Xorg developer mailinglist, DisplayPort is NOT supported in driver version 2.4.0 (xserver: 1.5.x) and probably won't be soon since they have other priorities.

I'm not sure about this statement either. First of all, my intrepid seems to run the driver version 2.4.1, not 2.4.0:
```
dh@spirit:~$ dpkg -l|grep xserver-xorg-video-intel
ii  xserver-xorg-video-intel                  2:2.4.1-1ubuntu9 
```

And have a look at Joel Burton's comment on [this page]("http://justinsomnia.org/2008/09/getting-wireless-to-work-in-ubuntu-on-a-lenovo-thinkpad-x200/"). Seems to work for him. I should be able to verify this as soon as my Ultrabase arrives...

---

### Post by vishketan on 2008-10-20
> **banshee.berlin said:**
> I'm not sure about this statement either. First of all, my intrepid seems to run the driver version 2.4.1, not 2.4.0:
```
dh@spirit:~$ dpkg -l|grep xserver-xorg-video-intel
ii  xserver-xorg-video-intel                  2:2.4.1-1ubuntu9 
```

And have a look at Joel Burton's comment on [this page]("http://justinsomnia.org/2008/09/getting-wireless-to-work-in-ubuntu-on-a-lenovo-thinkpad-x200/"). Seems to work for him. I should be able to verify this as soon as my Ultrabase arrives...

Perhaps this was the message that was referred to?

[http://lists.freedesktop.org/archives/xorg/2008-July/037375.html]("http://lists.freedesktop.org/archives/xorg/2008-July/037375.html")

One strange thing I noticed is that Joel Burtons comment talks about a DVI output but AFAIK the X200 Ultrabase only has a displayport output!

vishy

---

### Post by banshee.berlin on 2008-10-20
> **vishketan said:**
> One strange thing I noticed is that Joel Burtons comment talks about a DVI output but AFAIK the X200 Ultrabase only has a displayport output!

My hope is that he simply has a DisplayPort->DVI converter on his ultrabase. Let's wait and see if he responds to your comment. Last time I tried it took him a while. Maybe we should mail him to the joelburton.com address an hope that it's the right guy? ;-)

---

### Post by ashaw on 2008-10-20
A little piece of my lshw output (below) reveals some interesting bits re: the VGA, display, communications and Ethernet.

According to this, the VGA and display mgr are unclaimed, while it looks like the latest patches to 8.10 have re-activated the e1000e driver for the Intel Gig-e nic (can anyone confirm?)

I'm not in a location where I can test the ethernet at the moment, but will report back in a bit. Meanwhile, anybody got ideas for activating this VGA output? I'd love to be able to get that working with my 22" LCD anytime now...


lshw output:

```
      *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0

        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

        *-communication UNCLAIMED
             description: Communication controller
             product: Mobile 4 Series Chipset MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0

        *-network
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1f:16:09:84:bf
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 latency=0 link=no module=e1000e multicast=yes port=twisted pair

```

---

### Post by scheuri on 2008-10-20
Hi all

I am an owner of a Lenovo Thinkpad x200 (type 7458-AL7) with x4500 graphics and Intel wireless 5300.

While Wireless works out of the box with Ubuntu 8.10 beta (and with Ubuntu 8.04.1 using the firmware and compate-wireless) I just could not wrap my head around the whole graphics issues.

My desktop shows up with 1024x768 where 1280x800 should be possible. However, X11 offers me a generic xorg.conf which does not help me much. I must admit that the whole X11-framework never was my strong point. So I kinda hope I find some help here...

my xrandr
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1360 x 1360
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0 +   50.0  
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
HDMI-1 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  

```

my glxinfo (or at least some of it)
```

display: :0  screen: 0
direct rendering: Yes
GL_RENDERER   = Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 7.2
GL_VENDOR     = Tungsten Graphics, Inc

```

my xserver-xorg-video-intel
```

ii  xserver-xorg-video-intel                  2:2.4.1-1ubuntu9

```

As I mentioned earlier, I just have the generic xorg.conf, nothing much.

Questions:
How I can I determine what driver it uses (vesa, intel)?
How can I force X to use a certain driver (I presume xorg.conf)
How can I force X to use the native resolution?
Does anybody manage to use the intel driver with 3D acceleration and native resolution?
Anyone an idea how my xorg.conf might look in the first place? I might just be able to go from there...

Thanks a lot for your answers and your help...
Cheers
Stefan

---

### Post by anthro398 on 2008-10-21
I received my X200s today and installed Intrepid.  Wireless works well.  I pasted in the xorg file on the previous page and my resolution has been fixed.  I can't enable desktop effects, either.  
glxgears:
3786 frames in 5.0 seconds = 757.019 FPS
3777 frames in 5.0 seconds = 755.364 FPS
3789 frames in 5.0 seconds = 757.749 FPS

xrander:
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1920 x 1200
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1440x900       50.0*+

---

### Post by simon.sigre on 2008-10-21
> **scheuri said:**
> Hi all

I am an owner of a Lenovo Thinkpad x200 (type 7458-AL7) with x4500 graphics and Intel wireless 5300.

While Wireless works out of the box with Ubuntu 8.10 beta (and with Ubuntu 8.04.1 using the firmware and compate-wireless) I just could not wrap my head around the whole graphics issues.

My desktop shows up with 1024x768 where 1280x800 should be possible. However, X11 offers me a generic xorg.conf which does not help me much. I must admit that the whole X11-framework never was my strong point. So I kinda hope I find some help here...

my xrandr
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1360 x 1360
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0 +   50.0  
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
HDMI-1 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  

```

my glxinfo (or at least some of it)
```

display: :0  screen: 0
direct rendering: Yes
GL_RENDERER   = Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
GL_VERSION    = 1.4 Mesa 7.2
GL_VENDOR     = Tungsten Graphics, Inc

```

my xserver-xorg-video-intel
```

ii  xserver-xorg-video-intel                  2:2.4.1-1ubuntu9

```

As I mentioned earlier, I just have the generic xorg.conf, nothing much.

Questions:
How I can I determine what driver it uses (vesa, intel)?
How can I force X to use a certain driver (I presume xorg.conf)
How can I force X to use the native resolution?
Does anybody manage to use the intel driver with 3D acceleration and native resolution?
Anyone an idea how my xorg.conf might look in the first place? I might just be able to go from there...

Thanks a lot for your answers and your help...
Cheers
Stefan


My dodge xorg.conf.. works for me.. any suggestions though?

//Section "Module"
	Load 	"glx"
	Load	"GLcore"
	Load	"i2c"
	Load	"ddc"
	Load	"dri"
	Load	"freetype"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option 		"EmulateWheel" "true"
	Option 		"EmulateWheelButton"
EndSection

Section "Device"
	Identifier	"x200VideoCard"
	Driver		"intel"
	#BusID		"PCI:00:02.0"
EndSection

Section "Monitor"
	Identifier	"x200Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"x200Screen"
	Device		"x200VideoCard"
	Monitor		"x200Monitor"

	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection

EndSection


Section "ServerLayout"
	Identifier	"x200ServerLayout"
	Screen		"x200Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
\\

---

### Post by anthro398 on 2008-10-21
So, I see there aren't configuration sections in xorg for the navigation input device.  (What are the buttons called?)  I'd like to be able to use the middle button for scrolling in combination with the track stick.  Can anyone explain how that's done?

Thanks.

Edit: Ok, [trackpad]("http://en.wikipedia.org/wiki/Pointing_stick")! And, after some updates, it works without intervention.

---

### Post by eater on 2008-10-21
**anthro398**: Oooh, the X200s! How is the battery life, compared to what it's supposed to be? And how are hibernate and suspend working?

---

### Post by scheuri on 2008-10-22
Hi all

Thanks to you, simon.sigre. To my big surprise, your xorg.conf (with some changes for my keyboard layout) worked "as is".

It worked so good, that I am actually suspicious if it really is used...;)

It says direct rendering, xrandr names the correct resolution.

Now, the only "concern" is, that World of Warcraft (my choice of 3d testing) is not working properly....no fonts, graphic glitches.

Now, I have no idea why that is and I guess I will never find out. But at least everything else seems to work out of the box now.

Thanks...
Cheers
Scheuri

---

### Post by anthro398 on 2008-10-22
> **eater said:**
> **anthro398**: Oooh, the X200s! How is the battery life, compared to what it's supposed to be? And how are hibernate and suspend working?

My suspend and hibernate both work perfectly.  In fact, I think it recovers something like twice as fast as my Thinkpad T-60 running Hardy.  It's almost as fast as my wife's MacBook.  If you've seen a MacBook recover from suspend, you'll know it's almost instant.  It's a killer feature that made me consider buying one instead of the X200.  

I suspect the Mac doesn't re-request an IP address when it wakes and instead tries it's last DHCP setting.  I was very happy to see that Intrepid is nearly as fast.

I'm not sure why I can't enable desktop effects, though.

---

### Post by vishketan on 2008-10-22
I looked through the forum posting and want to summarize my understanding of the hardware support for this machine under Intrepid Beta. Can someone who is running Interpid Beta (and preferably also has a Ultrbase) pls confirm?

- Wireless seems to work reliably (with Intel cards)
- The ethernet bug seems to be fixed and it seems to work reliably
- There is a problem with sound from the docking station. 
- X seems to be a touch and go. The Intel drivers seem to be at fault. 
- There is no displayport output from the docking station when using Intel drivers. This is possible by using the Vesa driver but then one loses desktop effects
- Suspend and Resume are flaky when using Intel drivers but seem to be reliable when using Vesa driver
- The fingerprint reader does not work. 

How is the support for the rest of the Hardware, especially the Ultrabase? Do all the extra ports on the Ultrabase work? Does the machine suspend and resume reliably when placed on the Ultrabase? 

I am looking forward to my machine arriving in a few days ...

vishy

---

### Post by anthro398 on 2008-10-23
> **vishketan said:**
> I looked through the forum posting and want to summarize my understanding of the hardware support for this machine under Intrepid Beta. Can someone who is running Interpid Beta (and preferably also has a Ultrbase) pls confirm?

- Wireless seems to work reliably (with Intel cards)
My Intel 5300 works perfectly.
> **vishketan said:**
> - The ethernet bug seems to be fixed and it seems to work reliably
Yes, the Ethernet card using e100e works perfectly.
> **vishketan said:**
> - Suspend and Resume are flaky when using Intel drivers but seem to be reliable when using Vesa driver
No, suspend and resume have never failed for me using the Intel video driver.  In fact, it works much faster than it did in Hardy.

I don't have an ultrabase or fingerprint reader so I can't comment.  However, the fingerprint reader in my T-60 worked, though it took configuration.  In my estimation it wasn't worth the trouble to configure, though.  In Windows, swiping an enrolled finger logs you in.  In Linux, the same swipe only works after you've typed in your user name.  If you're already typing your user name it's easier and faster to type your password than to move your hand and swipe your finger.  It's really just a status symbol thing, I think.  The swipe works with PAM which requires one to identify oneself first.  

I haven't tested the 3 in 1 media reader, bluetooth, or the VGA out.  I can't enable desktop effects under the Intel driver.  Other than that, everything seems to work.  The speakers are muffled since they're on the bottom of the laptop, but are OK.  The screen, I have the backlit LED, is super bright and crisp.  Mine, at 3.4 lbs with the 9 cell battery, is super light.  I love it.

As an aside, sleeves for the MacBook seem to fit the X200 really well.  I bough a [Brenthaven Eclipse Sleeve 1]("http://www.amazon.com/Brenthaven-2169101-Eclipse-Sleeve-Notebook/dp/B0016BH492/ref=sr_1_2?ie=UTF8&s=electronics&qid=1224760541&sr=8-2") yesterday and it's a perfect fit.

---

### Post by vishketan on 2008-10-23
> **anthro398 said:**
> 
No, suspend and resume have never failed for me using the Intel video driver.  In fact, it works much faster than it did in Hardy.



Sorry to be anal. Are you sure you are using the intel drivers? 

Can you please look into your /var/log/Xorg.0.log and verify that it shows 

(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so

thanks

vishy

---

### Post by anthro398 on 2008-10-23
> **vishketan said:**
> Sorry to be anal. Are you sure you are using the intel drivers? 

Can you please look into your /var/log/Xorg.0.log and verify that it shows 

(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so

thanks

vishy

```

(II) Loading /usr/lib64/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "intel"

(II) Loading /usr/lib64/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

```


So, all signs point to yes.  

By the way, I was wondering why scrolling using the middle button worked in Thunderbird but not Firefox.  I found that I hadn't enabled autoscrolling in Edit>Preferences>Advanced>Use autoscrolling.  Select that and use the middle Trackpoint button with the track stick and you get a nice scrolling experience.  

I'm pretty disappointed to discover that Network Manager now respects split tunnels in the server configuration for both OpenVPN and vpnc.  I was enjoying knowing that all my traffic was encrypted on unsecured networks.  Not so much anymore.

---

### Post by Chrigi on 2008-10-25
Today I installed the 8.10 RC on my X200. So far everything has gone pretty well. BUT there are some things I don't understand:

1.) My xorg.conf file is nearly empty. It has just the disclaimer and 2 sections with very very little 'default' stuff. Why? -> Like this I can't change my login screen resolution. But the normal resolution works O.o

2.) Is there already an Intel driver for the 4500MHD? I have some strange issues with the grafics and would like to try the newest intel driver. (e.g. when I change to the DarkRoom theme, the menu bars stay how they were...)

I hope someone can help me...

---

### Post by vishketan on 2008-10-25
Chrigi,

You might need to post your /var/log/Xorg.0.log and your xorg.conf for people to have a look and comment on your problem.

vishy

---

### Post by anthro398 on 2008-10-25
Mine also came basically empty.  Someone said the sparseness of the file had to do with [HAL]("http://en.wikipedia.org/wiki/HAL_(software)").  I don't know anything about it, really.

Here's my xorg:
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0     
EndSection                               

Section "Files"
        ModulePath   "/usr/lib64/xorg/modules"
        FontPath     "/usr/share/fonts/misc/" 
        FontPath     "/usr/share/fonts/TTF/"  
        FontPath     "/usr/share/fonts/OTF"   
        FontPath     "/usr/share/fonts/Type1/"
        FontPath     "/usr/share/fonts/100dpi/"
        FontPath     "/usr/share/fonts/75dpi/" 
    FontPath    "/usr/share/fonts/corefonts/"  
    FontPath    "/usr/share/fonts/mathematica-fonts/"
EndSection                                           

Section "Module"
        Load  "dri"
        Load  "extmod"
        Load  "glx"   
        Load  "record"
        Load  "xtrap" 
        Load  "dbe"   
        Load  "freetype"
EndSection              

Section "Monitor"
        Identifier   "Monitor0"             
        VendorName   "LEN"                  
        ModelName    "4010"                 
        Option      "DPMS"                  
    Option  "PreferredMode" "1280x800"      
EndSection                                  


Section "Monitor"
    Identifier "FakeHDMI-1"
    Option  "Ignore"    "True"
EndSection                    

Section "Monitor"
    Identifier "FakeHDMI-2"
    Option  "Ignore"    "True"
EndSection                    

Section "Device"
    Option     "DRI"
        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "Unknown Board"
        BusID       "PCI:0:2:0"
    Option  "monitor-HDMI-2" "FakeHDMI-2"
    Option  "monitor-HDMI-1" "FakeHDMI-1"
    Option  "monitor-LVDS"  "Monitor0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
    DefaultDepth    24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        Modes   "1280x800" "1024x768" "800x600"
        Virtual 1920 1200
        EndSubSection
EndSection

Section "dri"
     Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

I took the xorg configuration posted earlier in this thread and may have modified it slightly.  I still can't enable compiz, though, due to compiz complaining that the driver, intel, isn't whitelisted, though it is in the whitelist.  [Compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check") tells me it should work:

```

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

I've been thinking about trying to start compiz with skip-check, but am worried it could be problematic.
Edit: I did enable compiz with checking skipped:
```
SKIP_CHECKS=yes compiz
Checking for Xgl: not present.
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 
Starting gtk-window-decorator
```

Seems to work fine.  This can be automated by 
```
mkdir -p ~/.config/compiz; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```
as seen in [this thread]("http://forum.compiz-fusion.org/archive/index.php/t-6038.html").  I have no idea what the dangers of doing this are, but I assume you can delete that directory and restart X if it breaks.

---

### Post by ashaw on 2008-10-25
**Of external VGA's and imaginary HDMI's...**

So following up on my VGA difficulties and the general problems surrounding the display configurations that a number of us have had, I came across [this Debian install notes page]("http://www.thinkwiki.org/wiki/Installing_Debian_on_an_X200") on ThinkWiki and tested out the author's xorg.conf workaround to get rid of the "imaginary displays" that had been wreaking havoc with my screen resolution settings (note: I'm running the x64 version of the Intrepid beta on my machine).

After changing xorg.conf to turn off the HDMI's, *everything* seems to work! I can now get perfect VGA output to a projector; the screen resolution applet detects my monitor and external monitors without any trouble; and I can use the VGA in mirrored or un-mirrored mode.

I've added a step-by-step guide to the [Ubuntu 8.10 install guide on ThinkWiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_%26_8.10_on_an_X200"). If you just want the xorg.conf settings, here they are (please let me know if they work):


```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
    Identifier    "HDMI-1"
    Option        "Ignore" "True"
EndSection

Section "Monitor"
    Identifier    "HDMI-2"
    Option        "Ignore" "True"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth     24
    SubSection "Display"
        Modes "1280x800" "1024x768"
# The following line was an auto-configuration added by an
# external VGA projector; you might leave it out
# and to let the system detect dimensions appropriate for
# whatever display you happen to use.
        Virtual    2432 864
    EndSubSection
EndSection

 Section "Device"
     Identifier    "Configured Video Device"
     Driver        "intel"
     Option        "monitor-HDMI-1" "HDMI-1"
     Option        "monitor-HDMI-2" "HDMI-2"
 EndSection

```

---

### Post by justkeeper on 2008-10-25
Has anyone managed to use hdaps or tp_smapi with his/her X200?I'm running Intrepid on a model 74542GU,and it seems that it's not supported.

---

### Post by Chrigi on 2008-10-26
Sure, sure:

My xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```
Not like it should be right? Can I just copy/paste the fixed file posted a few posts before?

My Xorg.0.log:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux chrigi-ubuntux200 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 26 16:22:44 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf2000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
(--) PCI: (0@0:2:1) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xf2400000/1048576
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Mobile Intel® GM45 Express Chipset
(--) intel(0): Chipset: "Mobile Intel® GM45 Express Chipset"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xF2000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 32704 kB
(II) intel(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): Attempting to determine panel fixed mode.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video1
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): Output HDMI-1 has no monitor section
(II) intel(0): I2C bus "HDMIDDC_B" initialized.
(II) intel(0): HDMI output 1 detected
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output HDMI-2 has no monitor section
(II) intel(0): I2C bus "HDMIDDC_C" initialized.
(II) intel(0): HDMI output 2 detected
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output HDMI-1 connected
(II) intel(0): Output HDMI-2 connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): Output HDMI-1 using initial mode 1024x768
(II) intel(0): Output HDMI-2 using initial mode 1024x768
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 32764 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x61110 (PORT_HOTPLUG_EN) changed from 0x10000120 to 0x38000120
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x10100000 to 0x38500000
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000206 to 0x00000000
(WW) intel(0): PIPEASTAT before: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEASTAT after: status:
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x00000246 to 0x00000206
(WW) intel(0): PIPEBSTAT before: status: VSYNC_INT_STATUS LBLC_EVENT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): Register 0x321b (FBC_FENCE_OFF) changed from 0x08024d00 to 0x7d006c00
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 1248000 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 4991996 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xf2000000
(II) intel(0): [drm] ring buffer = 0xd0000000
(II) intel(0): [drm] mapped front buffer at 0xd0100000, handle = 0xd0100000
(II) intel(0): [drm] mapped back buffer at 0xd2000000, handle = 0xd2000000
(II) intel(0): [drm] mapped depth buffer at 0xd274e000, handle = 0xd274e000
(II) intel(0): [drm] mapped classic textures at 0xd2e9c000, handle = 0xd2e9c000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Disable render standby.
(II) EXA(0): Offscreen pixmap area of 22978560 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01fff000 (pgoffset 8191)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x0274e000 (pgoffset 10062)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x02e9c000 (pgoffset 11932)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00094fff: compressed frame buffer (468 kB, 0x00000000be020000 physical
)
(II) intel(0): 0x00095000-0x0009efff: HW cursors (40 kB)
(II) intel(0): 0x0009f000-0x000a6fff: logical 3D context (32 kB)
(II) intel(0): 0x000a7000-0x000b8fff: exa G965 state buffer (72 kB)
(II) intel(0): 0x000b9000-0x000b9fff: power context (4 kB)
(II) intel(0): 0x00100000-0x0084dfff: front buffer (7480 kB) X tiled
(II) intel(0): 0x0084e000-0x01e37fff: exa offscreen (22440 kB)
(II) intel(0): 0x01fff000:            end of stolen memory
(II) intel(0): 0x01fff000-0x01ffffff: HW status (4 kB)
(II) intel(0): 0x02000000-0x0274dfff: back buffer (7480 kB) X tiled
(II) intel(0): 0x0274e000-0x02e9bfff: depth buffer (7480 kB) Y tiled
(II) intel(0): 0x02e9c000-0x04e9bfff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): using SSC reference clock of 100 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output HDMI-1 is connected to pipe none
(II) intel(0):   Output HDMI-2 is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): using SSC reference clock of 100 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 261 x 163
(II) config/hal: Adding input device ThinkPad Extra Buttons
(EE) No input driver/identifier specified (ignoring)
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device TPPS/2 IBM TrackPoint
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event9"
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "ch"
(**) AT Translated Set 2 keyboard: xkb_layout: "ch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "ch"
(**) Video Bus: xkb_layout: "ch"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "ch"
(**) Video Bus: xkb_layout: "ch"
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
AUDIT: Sun Oct 26 16:22:52 2008: 5289 X: client 4 rejected from local host ( uid=0 gid=0 pid=5504 )
(II) config/hal: Adding input device Microsoft Microsoft? 2.4GHz Transceiver v5.0
(**) Microsoft Microsoft? 2.4GHz Transceiver v5.0: always reports core events
(**) Microsoft Microsoft? 2.4GHz Transceiver v5.0: Device: "/dev/input/event11"
(II) Microsoft Microsoft? 2.4GHz Transceiver v5.0: Found x and y relative axes
(II) Microsoft Microsoft? 2.4GHz Transceiver v5.0: Found 5 mouse buttons
(II) Microsoft Microsoft? 2.4GHz Transceiver v5.0: Configuring as mouse
(II) XINPUT: Adding extended input device "Microsoft Microsoft? 2.4GHz Transceiver v5.0" (type: MOUSE)
(**) Microsoft Microsoft? 2.4GHz Transceiver v5.0: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft? 2.4GHz Transceiver v5.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Sun Oct 26 16:23:11 2008: 5289 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5566 )
AUDIT: Sun Oct 26 16:23:11 2008: 5289 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5567 )
AUDIT: Sun Oct 26 16:23:11 2008: 5289 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5568 )
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): using SSC reference clock of 100 MHz
(II) intel(0): Selecting standard 18 bit TMDS pixel format.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   60.96  1280 1328 1360 1478  800 803 809 825 -hsync -vsync (41.2 kHz)
(II) intel(0): EDID vendor "LEN", prod id 16400
(II) intel(0): I2C device "HDMIDDC_B:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_B:ddc2" removed.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "HDMIDDC_C:ddc2" removed.
```

So is there an Intel driver for the 4500MHD which supports 3D acceleration or is it already installed with my 8.10RC?
Because I can use the moderate effects without any problems.

Oh and regarding my Theme problem, I attached a screenshot.
As you can see, not only are the menu bars strange, I can't read the text on it and my trash can is somewhat displaced...
//Fixed the whole theming stuff! And I just needed some time to find out how to rearrange these icons... I just selected a completely different theme and waited until it updated the panels and then switched to the DarkRoom Theme and voila it worked.

I found in entry on the ThinkWiki install guide regarding the tpfand config. I managed to install the sensors-applet and the tpfand on my 8.10 amd64. My Questions are now:
In tpfand every sensor is just named "Sensor X", do the same sensors have the same numbers on all x200? (So I could use the naming from the ThinkWiki)
I just can't get it to work. I set it to manual and then close it and put the new values in the file but when I launch the GUI again, it reverted to my old settings...

Oh yeah and then I've got just some more questions:
The mute button works to mute but I can only unmute by using the volume up/down button. Is this somehow changeable?
Is it possible to get all the Fn-Keys working?
Is it possible to use the middle mouse button for scrolling just like on windows?
Is it possible to easely disable/enable Bluetooth?

Sorry, I'm an absolute novice on Linux... hopefully someone is willing to answer such beginner questions.

---

### Post by ashaw on 2008-10-27
@Chrigi -

re: the xorg.conf file, I recommend saving a backup somewhere before you change anything. 

other than that, yes, you can replace the uncommented portion of your config file with the code from my earlier post. 

let me know how it goes...

---

### Post by Fischli on 2008-10-28
> **ashaw said:**
> ...I've added a step-by-step guide to the [Ubuntu 8.10 install guide on ThinkWiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_%26_8.10_on_an_X200"). If you just want the xorg.conf settings, here they are (please let me know if they work):


Thanks. Your settings work fine for me too! First suspend to ram was not working but this was because in the file /etc/pm/config.d/00sleep_module the line ```
SLEEP_MODULE="kernel"
``` was commented out! I removed the #, rebooted and afterwards suspend to ram worked!

---

### Post by Ub1476 on 2008-10-28
> Oh yeah and then I've got just some more questions:
The mute button works to mute but I can only unmute by using the volume up/down button. Is this somehow changeable?
Is it possible to get all the Fn-Keys working?
Is it possible to use the middle mouse button for scrolling just like on windows?
Is it possible to easely disable/enable Bluetooth?

Sorry, I'm an absolute novice on Linux... hopefully someone is willing to answer such beginner questions.

Which Fn-keys doesn't work for you? I'm quite sure everyone worked for me in Hardy (didn't do a detailed check though)..

Read [here]("http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html") for fixing the mouse.

I just use the Fn-key for wireless/bluetooth to enable/disable it.

For others information, the atheros chipsets will likely get support a few weeks after Intrepids release.. I'm personally not sure wether I wish to use it anyway because of the poor power-managment support (fan/temp/battery) it has on Thinkpad compared to Vista.. :(

---

### Post by us3r on 2008-10-28
I have un-commented the line from 00sleep_module and suspend works about 50% of the time. It almost seems like every other time it works. Is anyone else experiencing this? This is the same behavior that it had before I edited the file. I'm using ashaw's xorg.conf file, which has worked like a charm.

Just about everything else is working great though.

---

### Post by chuffykow on 2008-10-29
I recently received my X200s with the X200 Ultrabase. Sadly, the Intel Xserver does not seem to support the DisplayPort out. My Xorg log reports that it finds the internal LVDS panel at 1440x900, finds an unattached VGA port and two HDMI ports that it defaults to 1336xwhatever. I currently have the system attached to a Dell 2408WFP, which works rather well in the standard Vista install. If people have specific questions about what is support/what works, i'll answer as best I can.

---

### Post by banshee.berlin on 2008-10-29
> **chuffykow said:**
> I recently received my X200s with the X200 Ultrabase. Sadly, the Intel Xserver does not seem to support the DisplayPort out. My Xorg log reports that it finds the internal LVDS panel at 1440x900, finds an unattached VGA port and two HDMI ports that it defaults to 1336xwhatever. I currently have the system attached to a Dell 2408WFP, which works rather well in the standard Vista install. If people have specific questions about what is support/what works, i'll answer as best I can.

That's unfortunate. Could you try to get the DisplayPort running with the Vesa driver? Thank you.

---

### Post by Chrigi on 2008-10-29
Thank you for all the answers :)
Resolution and display detection works great now.

Fn-Keys:
e.g. the Fn+Space doesn't work. But thanks, now I can disable BT. But whenever I restart, it's enabled again. Is it possible to disable it so that it stays disabled after restart?
oh yeah and the mute button only works to mute but not to unmute...

Scrolling:
I followed the guide and created the file and then restarted ubuntu but it still doesn't work... maybe because the file is marked as text (it is .fdi) instead of xml like the other .fdi in the folder? How could I change that?

tpfand:
I'm kind of lost here... Whenever I edited the config file as explained in the ThinkWiki guide, it rverted back to the initial settings. (I selected 'manual' in the settings)
Then I tried to create a profile by simply putting the values in an existing profile and then rename it to lenovo_XXXXX (I used the ID displayed in the tpfand GUI) but that did not work :/

suspend:
It worked right out of the box (tested after I installed all the updates) but whenever I suspend, it displays two messages about "xxx_usb ... not able to resubmit" but everything works... is that normal?
wow... today I suspended and the errors did not show... strange...

Thank you

---

### Post by anthro398 on 2008-10-30
> **eater said:**
> **anthro398**: Oooh, the X200s! How is the battery life, compared to what it's supposed to be? And how are hibernate and suspend working?

I'm getting 6 hours with the 9 cell battery.  I hope the [tpfand]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script#fanctrld") package helps with that, but I don't see it in the repositories presently.  I think I mentioned that hibernate and suspend are working perfectly and are faster than they were in Hardy.

---

### Post by anthro398 on 2008-10-30
I just realized that I hadn't enabled the repository containing the tpfand packages.  Here is my /etc/apt/sources.list (Duke is just down the street)
```

# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta amd64 (20080930.4)]/ intrepid main restricted
deb-src http://archive.linux.duke.edu/ubuntu/ intrepid restricted main #Added by software-properties

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta amd64 (20080930.4)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.linux.duke.edu/ubuntu/ intrepid restricted main
deb-src http://archive.linux.duke.edu/ubuntu/ intrepid main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.linux.duke.edu/ubuntu/ intrepid-updates restricted main
deb-src http://archive.linux.duke.edu/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.linux.duke.edu/ubuntu/ intrepid universe
deb http://archive.linux.duke.edu/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.linux.duke.edu/ubuntu/ intrepid multiverse
deb http://archive.linux.duke.edu/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.linux.duke.edu/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://archive.linux.duke.edu/ubuntu/ intrepid-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.linux.duke.edu/ubuntu/ intrepid-security restricted main
deb-src http://archive.linux.duke.edu/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://archive.linux.duke.edu/ubuntu/ intrepid-security universe
deb http://archive.linux.duke.edu/ubuntu/ intrepid-security multiverse

## Google repository for Picasa
deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.google.com/linux/deb/ testing non-free

# MediaTomb
deb http://apt.mediatomb.cc/ hardy main

# Miro - The free open-source video platform.
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/

# Virtual Box
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

# Thinkpad Fan control.  See http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control
deb http://ppa.launchpad.net/surban/ubuntu intrepid main

# Mediabuntu
deb http://packages.medibuntu.org/ intrepid free non-free



```

As I read earlier, there isn't yet a profile for the X200.  I'd really like to get the fan under control and to get the Active Protection system working.  I walk around to a lot of meetings and take my laptop on the bus.  It'd be nice to have the disk protection working.

---

### Post by Chrigi on 2008-10-30
I have some quite annoying gfx problems. It seems that it crashes whatever app uses a liiitle bit more enhanced gfx than ubuntu e.g. Nexuiz, Wormux etc. crash on startup or as soon as there are some effects.

---

### Post by chuffykow on 2008-10-31
> **banshee.berlin said:**
> That's unfortunate. Could you try to get the DisplayPort running with the Vesa driver? Thank you.

I had limited success with this. While I was able to get the DisplayPort on the dock to work with the 'vesa' driver, the internal panel was lost by xrandr. Additionally, the output seemed to be limited to 1600x1200. Attempting to set it to 1920x1200 had no effect, and increasing my Virtual size to any value resulted in severe display corruption both in X and on the console. I didn't test video play back speeds or anything of that nature, but general web browsing and remote screen sessions were reasonably snappy with this setup.

---

### Post by Kokopelli on 2008-10-31
I just got a shiny new X200 tablet so of course I had to install Ibex on it to celebrate.  :)  

The WACOM settings from the X60 tablet work out of the box, though touch screen does not work yet.  When I set the virtual resolution to 3200 1280 so I could rotate the panels did weird things.  I might try again later but since I am not too worried about rotating yet I left it be.

I noticed that when I wake the laptop from suspend the wireless drivers (Atheros chipset with the custom compiled madwifi) seem to not be able to connect to my access point.  

For xorg.conf I also increased the virtual resolution to 3200 1200, this way I could put my 24" LCD to the left of the LVDS.  A minor note.  There is no need to log off and back on to add a screen if you do not mind a little bit of command line...

```

xrandr --output VGA --left-of LVDS --mode <resolution>

```

where you put in the resolution for the external.

and to switch back to just LVDS

```

xrandr --output VGA --off

```

I set the two commands up in my .bashrc as follows
```

alias dual='xrandr --output VGA --left-of LVDS --mode $1'
alias single='xrandr --output VGA --off'

```

so I don't have to type the whole command.  i.e. "dual 1920x1200"

The monitor applet may be able to do it live (I did not try) but earlier posts were saying to restart X so it sounds like it does not.  

Overall I have been very happy with the experience so far.  The xorg.conf on this thread made my life a lot easier.

---

### Post by bluebook on 2008-11-03
I'm having some issues with the xorg.conf in this thread. I have an X200 (non-tablet) and after editing my xorg.conf as it was earlier in this thread it looks as quoted below.

My problem is that while my Dell 24" monitor works fine at 1920x1200 resolution (that was never my issue anyway, that always worked), my 12" laptop screen is unreadable. A screenshot of it doesn't show it so I can't attach it here but basically there are lines all over the screen and I can't see much (but the stuff is still there).

What I'd *really* like is to mirror the screens, not so much for when I'm connected to my 24" Dell, but when I do a presentation. I need to have the screens so I can have a presenter view on my laptop and the slides showing on the VGA out. Anyone know how to do that? 

Thanks to Kokopelli btw, those commands do work beautifully (and in "single" mode as aliased above, the laptop looks fine).

[PHP]
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2" 
       Option "YAxisMapping" "4 5"
       Option "XAxisMapping" "6 7"

EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
    Identifier    "HDMI-1"
    Option        "Ignore" "True"
EndSection

Section "Monitor"
    Identifier    "HDMI-2"
    Option        "Ignore" "True"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth     24
    SubSection "Display"
        Modes "1280x800" "1024x768"
# The following line was an auto-configuration added by an
# external VGA projector; you might leave it out
# and to let the system detect dimensions appropriate for
# whatever display you happen to use.
#        Virtual    2432 864
    EndSubSection
EndSection

 Section "Device"
     Identifier    "Configured Video Device"
     Driver        "intel"
     Option        "monitor-HDMI-1" "HDMI-1"
     Option        "monitor-HDMI-2" "HDMI-2"
 EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection[/PHP]

---

### Post by me13221 on 2008-11-06
> **us3r said:**
> I have un-commented the line from 00sleep_module and suspend works about 50% of the time. It almost seems like every other time it works. Is anyone else experiencing this? This is the same behavior that it had before I edited the file. I'm using ashaw's xorg.conf file, which has worked like a charm.

Just about everything else is working great though.

I filed a bug report about resuming from suspend-to-RAM on x200: [[COLOR="Blue"]#292422[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292422")

I would love to hear if other people are having the same problem.  :confused:

---

### Post by petri0 on 2008-11-06
The X200 suspend/resume bug is a generic Intel GM45 bug and it has been discussed for example in the "[Lenovo T400 Suspend / Hibernate / Resume Problems]("http://ubuntuforums.org/showthread.php?t=959712")" thread. It looks like it is a problem only with 32 bit Ubuntu 8.10 (the 64 bit version may have other problems). 

Good news: no need to use the VESA driver, there is a workaround. See [**this**]("http://ubuntuforums.org/showthread.php?t=959712&page=2#12") entry.

Please report if that works on the X200 too. It should.

Petri K

---

### Post by etola on 2008-11-08
**this regards suspend to ram**

Hi all,

I have lenovo x200 with kubuntu 8.10.

I couldn't manage to get intel driver to work with my graphics card so I switched to using vesa instead. I don't care about visual effects so it no problem for me.

My suspend to ram works well with vesa when I do it by clicking on the cpu icon an selecting  the 'suspend to ram' option. However, when I run pm-suspend from the command line, the screen stays black after resume.

I tried it with 'pm-suspend --quirk-dpms-on' but it didn't work either.

incidentally, I also uncommented 'SLEEP_MODULE="kernel"' line in /etc/pm/config.d/00sleep_module file.

I know it works, but I don't know how to do it from the command line. Any ideas ?

---

### Post by vishketan on 2008-11-11
I got fed up with having to run xrandr everytime I docked or undocked my laptop from the ultrabase. So I wrote a little script which listens to the dbus event and does the switch automatically for you. Save somewhere convenient and add it to your gnome startup programs. It is "inspired" by the gnome-docker code as well as the Fn-F7 python script from the thinkwiki site ;)

[PHP]
#!/usr/bin/python

import dbus
from dbus.mainloop.glib import DBusGMainLoop
import gobject
import os
import re

SERVICE   = "org.freedesktop.Hal"
DEV_INTERFACE = "org.freedesktop.Hal.Device"
UDI_DOCK = "/org/freedesktop/Hal/devices/platform_dock_0"
PROPERTY = 'info.docked'

LAPTOP = 'LVDS' 
MONITOR = 'VGA'

# "LVDS connected 1024x768+0+0 (normal left inverted right) 304mm x 228mm"
REGEX_OUTPUT = re.compile(r"""
 	(?x)					# ignore whitespace
 	^					# start of string
 	(?P<output>[A-Za-z0-9\-]*)[ ] 		# LVDS VGA etc
 	(?P<connect>(dis)?connected)[ ]		# dis/connected
 	((					# a group
  	(?P<width>\d+)x 			# either 1024x768+0+0
 	(?P<height>\d+)[+]  
  	(?P<horizontal>\d+)[+]
 	(?P<vertical>\d+)
 	)|[\D])					# or not a digit
 	.*					# ignore rest of line
 	""")

# "Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2624 x 1968"
REGEX_SCREEN = re.compile(r"""
 	(?x) 				# ignore whitespace
 	^				# start of string
 	Screen[ ]			
 	(?P<screen>\d)[: ]+
 	minimum[ ]
 	(?P<minWidth>\d+)[ x]+
 	(?P<minHeight>\d+)[, ]+
 	current[ ]+
 	(?P<curWidth>\d+)[ x]+
 	(?P<curHeight>\d+)[, ]+
 	maximum[ ]+
 	(?P<maxWidth>\d+)[ x]+
 	(?P<maxHeight>\d+)
 	""")	

def switch_screen(docked=True, disp0=LAPTOP, disp1=MONITOR):
    """Use xrandr to read current display state and change state"""
    for line in os.popen('xrandr -q').read().splitlines():
        if line.startswith(disp0,0) :
            d0_state = REGEX_OUTPUT.match(line).groupdict()
        elif line.startswith(disp1,0):
            d1_state = REGEX_OUTPUT.match(line).groupdict()
        elif line.startswith('Screen',0):
            screen_size = REGEX_SCREEN.match(line).groupdict()
        else:
            pass
    for i in ('width','height','horizontal','vertical'):
        try:
            d0_state[i] = int(d0_state[i])
        except TypeError:
            d0_state[i] = 0
        except UnboundLocalError:
            raise DisplayNameError, 'Internal Display: %s not found'% disp0
        try:
            d1_state[i] = int(d1_state[i])
        except TypeError:
            d1_state[i] = 0
        except UnboundLocalError:
            raise DisplayNameError, 'External Display: %s not found'% disp1
    for i in screen_size.keys():
        try:
            screen_size[i] = int(screen_size[i])
        except TypeError:
            screen_size[i] = 0
    xrandr ='xrandr --output '+disp0+' --%s --output '+disp1+' --%s'
    
    # If we are docked and external monitor plugged in 
    if docked and d1_state['connect'] == 'connected':
        print xrandr % ("off", "auto")
        os.popen(xrandr % ("off", "auto"))
        
        # If we are undocked then switch back to laptop 
    if not docked:
        print xrandr % ("auto", "off")
        os.popen(xrandr % ("auto", "off"))
    return


def Responder(num_changes, arr_struct, path=None):
    device_object = dbus_system_bus.get_object(SERVICE, path)
    device_interface = dbus.Interface(device_object, DEV_INTERFACE)
    
    if device_interface.PropertyExists(PROPERTY):
        switch_screen(device_interface.GetProperty(PROPERTY))
        
        
DBusGMainLoop(set_as_default=True)
dbus_system_bus = dbus.SystemBus()

hal_object = dbus_system_bus.get_object(SERVICE, UDI_DOCK)
hal_interface = dbus.Interface(hal_object, DEV_INTERFACE)

# Check if we are already docked on startup 
Responder(1, None, UDI_DOCK)

# Now watch for any other dock/undock events
hal_interface.connect_to_signal("PropertyModified",
                                Responder, path_keyword='path') 

loop = gobject.MainLoop()
loop.run()

[/PHP]
vishy

---

### Post by alexgenaud on 2008-11-12
I've resolved to familiarize myself with Vista and give time for bug fixes before installing 8.10 on my X200. The only things I like  about Vista are the new Start menu and extended file attributes. But I've never heard the fan, appreciate long battery life, and actually use my laptop on my lap, so heat is a concern. Does Ubuntu really tax and drain the hardware so much more than Vista?

---

### Post by Ub1476 on 2008-11-16
> **alexgenaud said:**
> I've resolved to familiarize myself with Vista and give time for bug fixes before installing 8.10 on my X200. The only things I like  about Vista are the new Start menu and extended file attributes. But I've never heard the fan, appreciate long battery life, and actually use my laptop on my lap, so heat is a concern. Does Ubuntu really tax and drain the hardware so much more than Vista?

Ufortunately, yes. While I use Linux on every other system around here, I just can't do it on my X200. Atheros wireless sucks, lots of problems with the graphic controller, and almost worst, battery is cut by two hours, it's warmer and still the fan runs on all the time.

I know there are fixes for much of this, but I'll wait for the "official" stuff. Hopefully much will be fixed in the next Linux kernel.

---

### Post by arnstein on 2008-11-16
Does anybody know what causes the extra battery drainage? I'm using tpfand and my fan is at 15% most of the time now, but I see no significant reduction in power usage.

---

### Post by eater on 2008-11-16
I finally got my **x200s** two days ago and I'm pretty thrilled. Thanks to this thread for the encouragement. No thanks to the Lenovo shipping department for three weeks of anxiety. 

Here are a few notes on my Ubuntu experience so far. I was expecting it to be a lot harder than it was.

[LIST]
[*]I booted up Vista first, shrank its partition as much as it would let me using the Windows tool, then shrank it further (down to 15GB) with the Intrepid installer tool. Seems like it has to be done in that order if you want to keep the possibility of dual-booting. The Intrepid installer wouldn't touch the partition till I shrank it in Vista first.

[*]Lacking a CD drive, I did a net install from a USB key, with no difficulty. 

[*]When asked to select my profile toward the end of the install, I checked Ubuntu Desktop, Ubuntu Mobile, and Xubuntu Desktop, which caused the install to fail with a red screen -- the console told me "rarian-compat conflicts with scrollkeeper". I unchecked Xubuntu Desktop and then it worked.

[*]Why the heck does a fresh install of Gnome start with DevilsPie set to "Force all windows maximized and undecorated"?? Just to frighten newbies?

[*]It took a little while to get my Atheros wireless working -- for some reason it seemed to only work when I modprobed ath5k manually, not when I put it in /etc/modules to load at boot, but after a few reboots that problem stopped happening inexplicably. Sorry if that's unhelpful. Now NetworkManager is behaving very nicely.

[*]I didn't have to touch the xorg.conf file, as all of you seem to have. 

[*]And desktop effects work seamlessly out of the box for me, anthro398 -- I can't imagine why they don't for you.

[*]The Gnome panel, fully expanded, doesn't quite reach across the screen, oddly -- it ends about 100 pixels from the right edge.

[*]I had trouble with a freeze upon resuming from suspend until I installed the little script from here:
[*][http://ubuntuforums.org/showthread.php?t=959712&page=2](http://ubuntuforums.org/showthread.php?t=959712&page=2)

[*]I also had to reformat my swap partition in gparted before hibernation with uswsusp would work.

[*]I installed [this script]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Ubuntu_8.10_using_HAL") to enable trackpoint scrolling.

[*]Battery life seems good -- about 3 hours with the 4-cell battery. I ran Powertop and followed its sage advice. I am not noticing the fan running at all -- if it is running it is very quiet -- and the machine is very much cooler to the touch than my X31.
[/LIST]

---

### Post by NDLunchbox on 2008-11-16
> **eater said:**
> 

[*]The Gnome panel, fully expanded, doesn't quite reach across the screen, oddly -- it ends about 100 pixels from the right edge.


I had this problem too.  It also messed up Compiz/Beryl effects (windows would wig out if you moved them to the wrong spot).  I noticed it was detecting an unknown display in edition to the laptop screen.  I think it is related to the display port on the UltraBase.  I disabled it and now the screen is perfect.


I just got my X200 for work, came with XP-Pro installed.  Ripped it off (filled with trialware) and re-installed.  Lenovo hasn't gotten all their drivers sorted out for Windows yet, it was painful to track down and manually install all the packages the Auto Update tool missed, so I was very pleasantly surprised that so much worked out of the box when I installed Ubuntu 8.10 AMD64.

I just installed, but so far here are my issues:

1) The display was all messed up out of the box, but simply disabling the "unknown" display fixed everything.

2) WiFi seems to work, even with Kismet - but once it enters promiscuous mode it stays there until reboot.  I think this is probably more a Kismet problem.

3) I have a Lenovo bluetooth mouse - I was able to pair it fine (easier than Windows) - but every reboot I must remove the profile and it and re-pair it every time.

---

### Post by banshee.berlin on 2008-11-19
> **NDLunchbox said:**
> 
3) I have a Lenovo bluetooth mouse - I was able to pair it fine (easier than Windows) - but every reboot I must remove the profile and it and re-pair it every time.

Same here - annoying.

---

### Post by anthro398 on 2008-11-22
> **arnstein said:**
> Does anybody know what causes the extra battery drainage? I'm using tpfand and my fan is at 15% most of the time now, but I see no significant reduction in power usage.

No, I don't, but using tpfand, dimming the display to the minimum acceptable brightness given ambient brightness, and using the CPU frequency governor has allowed me more than 5 hours of power.  I used [these instructions]("http://ubuntuforums.org/showpost.php?p=5946956&postcount=2") to set the governor to conservative, which I find more than adequate.  I also turned off unnecessary services and considered power battery life when choosing components.  I chose the 9 cell battery and the LED backlit display.  I considered the flash drive, but just couldn't get over the price/capacity ratio.

At more than 5 hours, I still have longer battery life than my colleagues on other systems.  I'd sure like to see 8 hours out of the battery, but I'll take what I can get.  Vista is alright as far as proprietary, Microsoft-built operating systems go, but until they make bash the shell and incorporate tools like ssh, it's fairly inconvenient for me.

---

### Post by Chrigi on 2008-11-24
I have no clue why I can't get the .fdi script for the scrolling to work. I created the file with the contents but I don't have any scrolling... any suggestions?

Yeah I also have some issues with the 4500MHD gfx. on 3D Stuff like games, it just crashes :/

The one big thing which bothers me even more than the mouse stuff, is the bad power saving. I thought I configured it quite good but in Vista it still has way more juice.

---

### Post by wired98 on 2008-11-29
Concerning the battery drainage on ubuntu. I cannot really confirm this as I never really tried to fully empty the battery with vista (deleted it from my hard disk on the second day I had the X200 and installed Intrepid).

However, I can report that the 6-cell battery gives a decent 4+ hours when running in powersave mode with lcd brightness set to the lowest setting. With the 9-cell I even get more than 6 hours. And this was on my first run without any powertop tweaking. So in total this gives me more than a work day's time independence from the ac adapter. I think this is not to bad at all. 

Also I cannot really report any issues with the fan, even I have not installed any extra fan script magic. So doing so at a later stage might even give more time on battery.

I have only two issues so far:
[LIST]
[*] Sound from the ultrabase docking station is not work. So far I have not clue why. In principle I thought it is just a pass-through of the internal one, but this seems to wrong. Anybody has an answer to the sound issues already?
[*] When running with an external monitor I have problems with my plasma panels (I am on kubuntu). They always go on the external display no matter what I do. However, I think this is a plasma related bug that probably is going to be fixed in kde4.2 where dual monitor integration should be better due support with the kephal library. 
[/LIST]

Otherwise I am very happy with the x200. I still have to try the UMTS modul but at the moment the x200 is simlocked on the card from vodafone that came with it...

Update: I recognized that the integrated stereo speakers of the ultrabase actually work. However, the stereo output plug for external speakers does not work...

---

### Post by stauraum on 2008-11-29
I have some grafic performance issues with intrepid and the x200. With ubuntu 8.04 (unmodified install) I was able to play e.g. urbanterror without any problems and glxgears gave me about 1500 FPS. Now with xubuntu 8.10 glxgears get just up to 730 FPS which is roughly just the half and it's impossible to play ut (5 FPS). Compiz runs fine though. I've played with some options (xorg.conf) followed some recommendations on the net, but without any success.
Any ideas?

Kind regards,
Martin

---

### Post by NDLunchbox on 2008-11-30
This is the first time I've put Linux on a Thinkpad... does anyone know if there is a working implementation of ThinkVantage Active Protection to protect the HDD from bumps?  It's the only IBM / Lenovo tool I miss (well, I dual-boot into XP too...).

---

### Post by anthro398 on 2008-11-30
> **NDLunchbox said:**
> This is the first time I've put Linux on a Thinkpad... does anyone know if there is a working implementation of ThinkVantage Active Protection to protect the HDD from bumps?  It's the only IBM / Lenovo tool I miss (well, I dual-boot into XP too...).

See [http://www.thinkwiki.org/wiki/HDAPS]("http://www.thinkwiki.org/wiki/HDAPS"), [http://www.thinkwiki.org/wiki/Tp_smapi]("http://www.thinkwiki.org/wiki/Tp_smapi"), and [http://www.thinkwiki.org/wiki/Active_Protection_System]("http://www.thinkwiki.org/wiki/Active_Protection_System").

The answer, I take it, is 'sort of'.  It's a little bit too experimental for my comfort level.  I've had this my T-60 for a couple of years without HDAPS and have survived.

---

### Post by Nadge59 on 2008-12-03
Has anyone been able to access the Lenovo R&R partition from grub? I'm in a dual-boot (Vista-Intrepid) config.  I need to do a recovery of vista (for work :?), the best progress I've made for /boot/grub/menu.lst is below (including Intrepid kernels) where the R&R entry is the last one:
> 
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6681f4d5-f052-42c7-b35b-45161d94e6df ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6681f4d5-f052-42c7-b35b-45161d94e6df ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6681f4d5-f052-42c7-b35b-45161d94e6df ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6681f4d5-f052-42c7-b35b-45161d94e6df ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=6681f4d5-f052-42c7-b35b-45161d94e6df ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=6681f4d5-f052-42c7-b35b-45161d94e6df ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
chainloader	+1

title           Thinkvantage Rescue and Recovery
root            (hd0,1)
parttype        (hd0,1) 0x07
savedefault
makeactive
chainloader     +1

Cheers,

---

### Post by Fischli on 2008-12-12
I'm using the vesa driver for my X200 because for me suspend-to-ram does not work with the intel driver.

Now I'd like to use an external monitor but xrandr is not detecting it...

Does anybody have an idea on how to use an external monitor with the vesa driver?

Thanks!

---

### Post by chs32 on 2008-12-16
On my X200s, hibernate works out of the box with the intel driver if triggered via the applet. It fails now and then if triggered via Fn-F12 (black screen, automatic reboot).

---

### Post by wonder202 on 2008-12-17
I wonder if anyone tried to boot from the X200 ExpressCard slot, using a CF card or external drive. X200 BIOS does not recognize my CF card in the expresscard slot, though the Ubuntu 8.10 installation recognized this card but after rebooting it could not start.

I successfully installed Ubuntu 8.10 64-bit on the SD card in my X200. I use SanDisk Extreme III 16GB SD, 30MB/sec Edition, though the speed of the SD card slot is slower, as it is linked to the USB bus. 

The speed of the expresscard slot should be much faster as it is linked to the PCI-E bus. I am using the SanDisk Extreme IV 8GB CF (40MB/sec) with this adapter:

[http://cgi.ebay.com/Boot-up-laptop-or-transfer-large-data-to-CF-at-40MB-sec_W0QQitemZ260319262993QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item260319262993&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A1|293%3A1|294%3A50](http://cgi.ebay.com/Boot-up-laptop-or-transfer-large-data-to-CF-at-40MB-sec_W0QQitemZ260319262993QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item260319262993&_trksid=p3286.c0.m14&_trkparms=72%3A1234|66%3A2|65%3A12|39%3A1|240%3A1318|301%3A1|293%3A1|294%3A50)

The seller says this adapter is Linux bootable, but actually it is not (or it is the X200 limitation).

---

### Post by icco on 2008-12-30
I just got an x200 for christmas and am loving it. I am slowly reading through and I'm having some of the same issues as many of you with the suspend.

for disabling just bluetooth run these commands:

echo "enable" > /proc/acpi/ibm/bluetooth
echo "disable" > /proc/acpi/ibm/bluetooth

I put each one in a script file that I run with sudo to get it to work. 

Thank you though for the links to get the scroll wheel working. Very awesome.

---

### Post by Fischli on 2009-01-06
Does anybody use the DisplayPort on the ultrabase? Does it work and how good is the display quality?

My problem is that when I use my VGA port an a 22" (1680x1050) monitor the image is not sharp. Therefore I'm considering buying the ultrabase then using the DisplayPort (with a DisplayPort-to-DVI converter) to use the monitor. 

And that's why I wanted to ask if anybody is using a setup like that?

Thanks a lot!

---

### Post by wired98 on 2009-01-14
> **chs32 said:**
> On my X200s, hibernate works out of the box with the intel driver if triggered via the applet. It fails now and then if triggered via Fn-F12 (black screen, automatic reboot).

Hi,

did your function keys work out-of-the-box? Or did you tweak ACPI settings? Which version of ubuntu are you running? Because for me all the keys like FN-F2 to -F12 do not doing anything for me (except FN-F5). I am on Kubuntu Intrepid. If you tweaked something could you post your settings? Thanks!

---

### Post by jjhuff on 2009-01-18
I've gotten a couple hangs, anyone else?  The mouse pointer still responds, but nothing else works (capslock, VT switching, Ctrl-Alt-Bkspace) Sadly, every time this has happened, I didn't have network connectivity to come in via SSH.

Also, is there any downside to running 64bit?
thanks!

---

### Post by tjansson on 2009-01-21
In case anybody is interested I have written a small article on my blog on how I made GPS work under Ubuntu 8.10:
[http://www.tjansson.dk/?p=450](http://www.tjansson.dk/?p=450)

---

### Post by Mr.Carramba on 2009-01-22
I'm waiting wor my X200 with SSD with 4GB ram , have few question

Does anyone have managet to get ultrabase to work?
should I disable swap, becouse of the SSD?

---

### Post by anthro398 on 2009-01-26
I was running 64 bit until a couple of weeks ago.  I reinstalled 32 bit on all of my computers out of frustration with a couple of applications.  However, I'm not ware of anything specific to the X200 that would make 64 bit any more or less problematic than it would be on other hardware.

---

### Post by Urban Strata on 2009-01-31
Just a quick note:

I've been running Ibex on my X200 for a couple months and loving it. But last week some updates were pushed out that messed up my wireless configuration and brightness controls. Not a huge deal, as I simply re-did the [wireless config]("http://ubuntuforums.org/showpost.php?p=5692155&postcount=2"), but now I have to reset the brightness every time I log in. It would be nice if this stuff didn't break with system updates.

Is there any way I can "pin" these X200-specific elements of my configuration so they won't break again?

Thanks.

---

### Post by GrouchoMarx on 2009-02-02
Has anyone had any success figuring out why the fan is constantly on? I'm a little reluctant to control it through software ([tpfan discussion]("http://www.nabble.com/tpfand-configuration-for-an-X200s-td20777095.html")). The system is spewing out cold air and it's only consuming about 11 Watts on battery power. The fan should not be on.

---

### Post by castrojo on 2009-02-04
Hi guys, I had 2 guys from the kernel team check out my laptop and try to diagnose it. 

They think it might be something in thinkpad-acpi so they will look into that - I'll keep everyone informed when I get more information.

---

### Post by GrouchoMarx on 2009-02-04
That's great news whiprush! Fingers crossed.

---

### Post by zmanian on 2009-02-06
I have an intel x200 tablet running with the intel video drivers. I'm running Intrepid.

When I rotate the screen 90 degrees using xandr, gnome does not properly redraw the screen. So moving from 1280x 800 moves me to a 800x800 window area.

Any suggestions on debugging?

---

### Post by NDLunchbox on 2009-02-09
FYI, I found an easy solution to the strange bluetooth pairing issues mentioned above - if your mouse is on when the laptop boots it works.

---

### Post by GrouchoMarx on 2009-02-09
Whatever is keeping the fan on seems somehow related to the wireless card. After engaging the wireless kill switch the fan turns off. After turning the wireless back on the fan starts again. This works every time with about a two or three minute delay.

Turning wireless power management on or off via:
```
iwconfig wlan0 power on
```
does not seem to have any effect.

I *think* that I have an Wifi Link 5100 wireless card*. Is anyone with the Atheros card also experiencing this issue (where the fan is always on)?

*The reason I say *think* is that I could have sworn that I bought a Wifi Link 5300. However, lshw -C network reports that it is a Wireless WiFi Link 5100. But then [this person]("http://stompbox.typepad.com/blog/2008/11/lenovo-x200-and-ubuntu-810.html") seems to have had the same experience. Could iwlagn simply be just reporting the product incorrectly?

---

### Post by nxn_swe on 2009-02-14
> **GrouchoMarx said:**
> 
I *think* that I have an Wifi Link 5100 wireless card*. Is anyone with the Atheros card also experiencing this issue (where the fan is always on)?

*The reason I say *think* is that I could have sworn that I bought a Wifi Link 5300. However, lshw -C network reports that it is a Wireless WiFi Link 5100. But then [this person]("http://stompbox.typepad.com/blog/2008/11/lenovo-x200-and-ubuntu-810.html") seems to have had the same experience. Could iwlagn simply be just reporting the product incorrectly?

I can confirm that i have the same problem. I specifically ordered a 5300 card in my x200, but got a 5100. I've contacted both my reseller and Lenovo about this, but i haven't recieved an answer on how they are going to solve this. All i heard so far is that this matter is escalated within Lenovo.

---

### Post by eater on 2009-02-14
I suspect that the machine is misreporting the card model -- I too bought a 5300 and my Ubuntu tells me it's a 5100.

Perhaps one of us could boot into Windows (not I!) and see if that OS recognizes the model differently?

---

### Post by GrouchoMarx on 2009-02-14
> **eater said:**
> I suspect that the machine is misreporting the card model -- I too bought a 5300 and my Ubuntu tells me it's a 5100.

Perhaps one of us could boot into Windows (not I!) and see if that OS recognizes the model differently?

Unfortunately I deleted my Windows partition. Actually this proved to be a big mistake because the Rescue and Recovery partition, which I kept, was borked by Ubuntu when Grub wrote to the master boot record during installation. Now the only way to re-install Windows is to order the Lenovo Rescue and Recovery DVDs, purchase a USB DVD drive, and revert to the factory state. Annoying! They should really make Grub installation reversible. Not that I use Windows very often. But now I have no safe way to update the BIOS, for instance.

---

### Post by whtvr on 2009-02-15
Hi guys,

I got my X200s ([http://www5.pc.ibm.com/ie/products.nsf/$wwwPartNumLookup/_NS45KUK?OpenDocument](http://www5.pc.ibm.com/ie/products.nsf/$wwwPartNumLookup/_NS45KUK?OpenDocument)) few weeks ago and am running 8.10 64bit. I've been following this thread for a while and wanted to share my experience with you.

First of all, out of the box linux compatibility is simply spectacular. I installed both 32bit and 64bit (from USB stick) and practically everything works flawlessly. I was happy with 32bit but wanted to use full 4gb of ram so went with 64bit eventually.

I have no problem with 3d acceleration - compiz works very well. All other things work too: wireless, bluetooth, card reader (with Sony Memory Stick as well) and even Express Card 3G Data Card (I briefly tried one at work once). I don't know about finger print reader - haven't configured it cause I wouldn't use it anyway.

There's a few small annoyances though:

1) Suspending to ram works in about 90% of times. The laptop wakes up almost every single time but sometimes wireless doesn't work after wake up. I don't really use hibernation but tried it few times and it failed once or twice...

2) I only get trackpoint scrolling (both vertical and horizontal) by running the following commands:

```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Button" 8 2
```I made a little script that I run every time when I log in but after waking up from suspend to ram scrolling works only every second time (roughly) and I have to re-run the script or/and put it to sleep and wake up again to get scrolling working.

3) As some one already pointed out there's a bug in controlling brightness. After GDM login is displayed brightness is on very low level and I have to manually adjust it with Fn+Home. Same thing happen after resuming from suspend.

4) I feel like fan is running more often than it needs to. I don't want to control it manually to prevent overheating but it's on about 3600rpm most of the time and it probably doesn't have to be...

5) Battery life is satisfactory for me (about 5-6 hours with 9cell accu) but nowhere near battery life some people are getting on windoze. I didn't really bother to tweak it (like I said, 5 hours is fine for my usage patterns) beyond runnig powertop and applying its suggestions within the program (btw. do I need to re-run powertop and re-apply all the tweaks after each reboot? it sort of feels like it... ) but more battery life would be very nice.

6) Mute button stopped working after one of the updates (don't remember which one) - all other special keys work ok (apart from ThinkVantage one which I didn't bother to configure)

7) GDM theme is not scaled properly to fit screen's resolution and it's only 1280x800 (or so) from upper left corner with black frame along bottom and right edge.

8) There's few others minor bugs (sometimes Gnome applets are not rendered properly upon boot and I need to either delete them and add them again or restart X) but nothing really serious I couldn't live with.

All in all I love this laptop, it's perfect for my needs and while I'm already very happy with the way linux behaves on it I wouldn't mind above mentioned issues to be sorted.

I'd be happy to help troubleshooting these bugs so feel free to ask for more details.

---

### Post by nxn_swe on 2009-02-15
> **eater said:**
> I suspect that the machine is misreporting the card model -- I too bought a 5300 and my Ubuntu tells me it's a 5100.

Perhaps one of us could boot into Windows (not I!) and see if that OS recognizes the model differently?

Well so I booted into Windows. And just as you suspected, it says 5300. So now there's a new question. Why does the card report itself as a 5100 card in Ubuntu.
It really bugs me as I now have some explaining to do. My contact at the reseller and to the guys at Lenovo. I guess i should have checked in Windows first, but to my defense i actually installed it yesterday for some specific work related applications.

---

### Post by eater on 2009-02-16
> After GDM login is displayed brightness is on very low level and I have to manually adjust it with Fn+Home. Same thing happen after resuming from suspend.

My partial solution for this is a script called "00modprobe-video" in /etc/pm/sleep.d that unloads the "video" module before suspend and reloads it after resume:

```
#!/bin/sh

case "$1" in
        hibernate|suspend)
                modprobe -r video
                ;;
        thaw|resume) 
                sleep 1
                modprobe video
                ;;
        *)
                ;;
esac

```

---

### Post by whtvr on 2009-02-17
> **eater said:**
> My partial solution for this is a script called "00modprobe-video" in /etc/pm/sleep.d that unloads the "video" module before suspend and reloads it after resume:


Thanks for info, I tried creating this script and it didn't work... any ideas why?

Thanks

---

### Post by eater on 2009-02-17
Make sure the script's permissions are executable, and perhaps try increasing the sleep number from 1 to 5 or so ... for me it took a bit of trial and error before it worked.

---

### Post by SaintDanBert on 2009-02-18
Nate_2001 wrote that "fingerprint is not working" There is
a larger problem where fingerprint everything and PAM everything have trouble playing well together. So much so that I understand that major changes are in play in the way that fingerprint works all together.

I learned this on my X61 tablet and continue to monitor what is happening, but alas no resolution yet. One symptom involves (1) supply fingerprint, (2) get asked for password, too, (3) failed authentication, (4) supply password, (5) now fingerprint works, (6) sudo doesn't know who to trust, etc ... tangled mess. Individually, the fingerprint hardware and apps work fine for me.

If you are interested you can search for bug reports and issue reports about fingerprint and PAM for both Hardy and Gutsy.

~~~ Saint 0;-D

---

### Post by SaintDanBert on 2009-02-18
Folks,
     I know that this is the X200 thread and it focuses on getting things running on that platform. Please consider a couple of things:

1.  Some of what you say here also applies to X61 too. Yes, there is devil in detailed differences, but one side's fix at least suggests where to dig for the other side.

2.  Consider sharing the what and how about your USE of tablet features.  which applications work well with stylus?
Stylus specific configuration? Special-key and special-button configuration? etc. Both X200 and X61 folks might benefit here too.

Just a thought,
~~~ 0;-D

---

### Post by whtvr on 2009-02-19
tried adjusting that script, couldn't get it to work, oh well - perhaps next update will fix it

oh, and the trick with running the script to enable trackpoint scrolling after resuming from standby doesn't seem to work anymore after last update...

---

### Post by robert1606 on 2009-02-25
Hello guys,

I am an owner of an x200 and I have been following this thread for a while. Everything works more or less fine, there are just a few things that are bugging me. One of them: I use wvdial to connect to the internet with the integrated 3G modem. It works most of the time, but every so often I receive the message
> 
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM1: No such file or directory
--> Cannot open /dev/ttyACM1: No such file or directory
--> Cannot open /dev/ttyACM1: No such file or directory
When I get this message, it takes usually a few reboots until wvdial succeeds to activate the 3G card. Do you have any idea what causes this problem?

I use ubuntu 8.10, 64 bit.

Thanks a lot in advance.

---

### Post by purba on 2009-02-28
> **bluebook said:**
> I'm having some issues with the xorg.conf in this thread. I have an X200 (non-tablet) and after editing my xorg.conf as it was earlier in this thread it looks as quoted below.

My problem is that while my Dell 24" monitor works fine at 1920x1200 resolution (that was never my issue anyway, that always worked), my 12" laptop screen is unreadable. A screenshot of it doesn't show it so I can't attach it here but basically there are lines all over the screen and I can't see much (but the stuff is still there).

What I'd *really* like is to mirror the screens, not so much for when I'm connected to my 24" Dell, but when I do a presentation. I need to have the screens so I can have a presenter view on my laptop and the slides showing on the VGA out. Anyone know how to do that? 

Thanks to Kokopelli btw, those commands do work beautifully (and in "single" mode as aliased above, the laptop looks fine).



bluebook, thx for the xorg.conf configuration. Now my X200 7455 can use 1280x800 in Ubuntu 8.10 64bit and my compiz still working.


Peace

---

### Post by whtvr on 2009-03-04
ok guys, i've sorted out the brightness problem! it was actually MUCH easier than i thought and i can only wonder why didn't i think about it earlier... h'anyway, here it goes:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Brightness_control_broken_-_lowest_level_after_Booting.2FSuspend.2FHibernate.2FScreen-off]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Brightness_control_broken_-_lowest_level_after_Booting.2FSuspend.2FHibernate.2FScreen-off")

i still cannot get scrolling to work after resuming from suspend and it's annoying like hell and essentially prevents me from using suspend at all... can i ask you all to post whatever info you have about this issue to launchpad ([https://bugs.launchpad.net/ubuntu/+bug/289023](https://bugs.launchpad.net/ubuntu/+bug/289023)) - the more people report the problem the greater chance we will have to bring it to the attention of developers and actually fix it

---

### Post by eater on 2009-03-04
Whtvr:

Thanks for the brightness tip!

As for the scrolling, the slightly annoying workaround I use is to just switch to another virtual console (Ctrl-Alt-F2) and then back (Ctrl-Alt-F7) whenever I notice that scrolling isn't working. That fixes it.

---

### Post by alain40 on 2009-03-04
Posted a page that describes how to optimize battery life on the X200. I get 7 to 8 hours of actual use with the changes described in my post. It also solved the always on fan problem.

See: [Extending battery life on the X200]("http://www.thinkwiki.org/wiki/Extending_battery_life_on_X200")

---

### Post by GrouchoMarx on 2009-03-04
> **alain40 said:**
> Posted a page that describes how to optimize battery life on the X200. I get 7 to 8 hours of actual use with the changes described in my post. It also solved the always on fan problem.

See: [Extending battery life on the X200]("http://www.thinkwiki.org/wiki/Extending_battery_life_on_X200")

You say this solved the fan problem. But with Wifi on or off? My machine does not have either the Ericsson 3G modem or Bluetooth. To me the "fan" problem seems more like a Wifi power management problem.

---

### Post by whtvr on 2009-03-05
> **eater said:**
> 
As for the scrolling, the slightly annoying workaround I use is to just switch to another virtual console (Ctrl-Alt-F2) and then back (Ctrl-Alt-F7) whenever I notice that scrolling isn't working. That fixes it.

Hmm... This doesn't seem to work for me... How do you enabled trackpoint scrolling in the first place? Do you use .fdi file or a script like me? I tried creating the .fdi file the other day but it doesn't work for me either (before/after suspend, doesn't work at all)

---

### Post by eater on 2009-03-05
I use an .fdi file copied from here:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Xorg-7.4.2B_using_HAL](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Xorg-7.4.2B_using_HAL)

---

### Post by alain40 on 2009-03-06
> **GrouchoMarx said:**
> You say this solved the fan problem. But with Wifi on or off? My machine does not have either the Ericsson 3G modem or Bluetooth. To me the "fan" problem seems more like a Wifi power management problem.
Yes it did solve the fan noise problem for me WITH wifi on. 

Using my system as I type these lines. Wifi on, connected.

Fan speed hovers around 1900 rpm (barely audible for me) in normal use. Only makes it to 3000 rpm (the max) if I stress the system, quickly goes back to lower speed by itself as I stop whatever was making it consume more power. 

Looking at sensors, nothing goes above 40 Celsius, which is really the reason why this all works.

Checked my wifi power settings, they are set for always on, you are quite right on this point. Wifi power can be improved as you pointed out, I will amend my wiki page to suggest moving to 3,4, or 5 for the power_level setting.

---

### Post by GrouchoMarx on 2009-03-07
> **alain40 said:**
> Yes it did solve the fan noise problem for me WITH wifi on. 

Using my system as I type these lines. Wifi on, connected.

Fan speed hovers around 1900 rpm (barely audible for me) in normal use. Only makes it to 3000 rpm (the max) if I stress the system, quickly goes back to lower speed by itself as I stop whatever was making it consume more power. 

Looking at sensors, nothing goes above 40 Celsius, which is really the reason why this all works.

Checked my wifi power settings, they are set for always on, you are quite right on this point. Wifi power can be improved as you pointed out, I will amend my wiki page to suggest moving to 3,4, or 5 for the power_level setting.

I guess I should ask: which Wifi card do you have (lspci -nn)? I cannot for the life of me get power management to work with the Intel Wifi 5100 [8086:4236]. The temperature hovers around 43-44 C.

---

### Post by whtvr on 2009-03-19
> **eater said:**
> I use an .fdi file copied from here:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Xorg-7.4.2B_using_HAL](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Xorg-7.4.2B_using_HAL)

ok, so i created this file but still cannot get middle-button scrolling to work; is there something i'm doing wrong? should i set some special permissions or anything like that?

i can only get scrolling to work when i issue these commands in the terminal:
```
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Button" 8 2
```
and that works until i suspend/hibernate my laptop...

any ideas guys?

---

### Post by whtvr on 2009-03-19
h'okay, i found a workaround [http://blog.aliencam.net/2008/11/tpmiddlemouse-ubuntu-810/](http://blog.aliencam.net/2008/11/tpmiddlemouse-ubuntu-810/)

i now seem to be able to use scrolling after resuming from suspend (i'm on kubuntu with 2.6.27.14-generic kernel)

---

### Post by Adalgiso on 2009-03-20
I am intending to buy a X200s, now two questions arose:

1.) How do i install Linux from a USB Pendrive, as the notebook does not have a CD drive? Is there an easy-to-follow Wiki? 

2.) Would you rather suggest a screen with 1140x900 or 1280x800 screen resolution?

Thank you in advance for quick answers, best regards.

---

### Post by whtvr on 2009-03-20
> **Adalgiso said:**
> I am intending to buy a X200s, now two questions arose:

1.) How do i install Linux from a USB Pendrive, as the notebook does not have a CD drive? Is there an easy-to-follow Wiki? 


[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

very easy to use piece of software with which you can create bootable "live" usb sticks; you use that kind of stick essentially in the same way you'd use livecd; questions? ask (-:

> **Adalgiso said:**
> 
2.) Would you rather suggest a screen with 1140x900 or 1280x800 screen resolution?

Thank you in advance for quick answers, best regards.
I would (and did) go for 1440x900, it's sharper and brighter but 1280x800 isn't all that bad either from what i've heard

---

### Post by parkerhiggins on 2009-03-25
Hello all!

I recently bought a new x200 (with the Intel 5100 wireless hardware) that came with Windows XP.  I know the wireless worked on XP, but I only used it once.  Immediately thereafter, I booted up the live CD, and had working wireless, and proceeded to install Ubuntu as a single install.

As soon as it installed, the wireless starting having an odd problem: Network Manager would try to connect to my home network, and would get as far as "Requesting a network address," where it hangs for a long time and ultimately fails.  While it's hanging there, I know I have some kind of connection, because it told me that I needed updates.

In trying to remedy this, I've installed all available updates from a wired connection, tried manually installing the firmware for my wireless card into /lib/firmware/, switched from Network Manager to wicd, all to no avail.  I've also tried using the live CD again, and now the wireless doesn't work on that either.

Has anybody had any experience with anything like this?  Thanks in advance, and please let me know if I can provide any more information.

---

### Post by sam.bkh on 2009-04-05
Hi all,
I have a serious battery life issue on my x200. With a 6-cell I'm getting about 2.5 hours with brightness all the way down; reports suggest that on Vista (although I never used it) people get closer to double that. My fan speed is always at 3770-80 rpm, even when I'm running at 800Mhz and both cores are well below 40 degrees; the fan is usually blowing cold air. I've followed all the powertop recommendations and turned off my 3G card with 

```
sudo echo "0" > /sys/devices/platform/thinkpad_acpi/wwan_enable
```

(although, oddly, for this to work I had to put it in a script and run that). I'm usually using wireless but not bluetooth. In case it's of any help, I followed [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/) to get my wireless (atheros) working.

Also, perhaps this is normal (this is my first dual-core computer) but no matter what my clock frequency is (800, 1600, 2270), both cores are running around 50 percent load with just normal computing tasks -- a couple of terminals up (not compiling or anything) ,a text editor or two, firefox with four or five tabs, and pidgin. Can anybody offer any help? I'd rather not run software fan controls, but the fan noise is driving me batty.
Sam

---

### Post by sam.bkh on 2009-04-05
Update: I figured out why my cores were running at a super-high load all the time, so I've fixed that. It didn't fix the fan issue, though.
Sam

---

### Post by me13221 on 2009-04-09
> **parkerhiggins said:**
> Hello all!
...

 As soon as it installed, the wireless starting having an odd problem: Network Manager would try to connect to my home network, and would get as far as "Requesting a network address," where it hangs for a long time and ultimately fails. While it's hanging there, I know I have some kind of connection, because it told me that I needed updates.

...


The wireless seems to be much improved in jaunty.  Try 'update-manager -d' from a wired connection.

---

### Post by halloworld on 2009-04-20
Anyone know the model of the x200 integrated camera (webcam), a v4l or v4l2? cos' i can capture picture using the integrated one but not my gspca camera, i use uvccapture, thank you

---

### Post by GrouchoMarx on 2009-04-20
After installing Jaunty, my wireless card is being properly reported as a Wifi 5300, and not a 5100, as with Intrepid. I guess that solves that mystery.

Unfortunately, the fan issue has not gone away. :(

---

### Post by GrouchoMarx on 2009-04-22
Ok. So after experimenting with Jaunty, it seems that they've made some improvements to the wireless module.

Turning on the wireless power management:

```
sudo iwconfig wlan0 power on
```

finally seems to have an effect. With wireless power management on, the fan only spins up at high transfer rates (>1MB/s). I wonder if anyone else can confirm this.

Note that it takes a while for the fan to actually respond to changes in wireless state, but eventually it spins down, and stays there. Try unplugging the AC if you're impatient.

---

### Post by holistone on 2009-05-09
I've been using my **X200** for almost 6 months with XP and Vista. I just installed 9.04-desktop-amd64 via a pen drive to a separate partition and I can not use or activate the wireless (the antenna light never comes on). I've tried a few of the suggestions earlier in this thread to get wireless working but with no success.

Windows reports that my wireless adapter is a **11 b/g Wireless LAN Mini PCI Express Adapter III **with Atheros driver 7.6.096. I'm not really sure where to start, so I would appreciate any suggestions. I've used linux/unix in the past, but not much in the last few years and not on laptops.

the following subset of dmesg output may be helpful:

[    9.142541] ath_hal: module license 'Proprietary' taints kernel.
[    9.143416] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[    9.150641] wlan: 0.9.4
[    9.154907] ath_pci: 0.9.4
[    9.154947] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.154958] ath_pci 0000:03:00.0: setting latency timer to 64
[    9.203467] pciehp 0000:00:1c.1:pcie02: Card not present on Slot(1)
[    9.203478] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[    9.203488] ath_pci 0000:03:00.0: PCI INT A disabled

Thanks in advance for any suggestions.

---

### Post by Emigallo on 2009-06-23
[FONT=Arial]If you are shopping for a new X200 watch out that the default B/G/N wireless adapter that Lenovo started shipping does not have Linux drivers. The new wireless adapter shows up as a:

[/FONT][FONT=Arial]Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. Device e020

[/FONT]More details can be found here:

[http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II)

I have queried Lenovo customer support to see if they are aware of any workaround. They appeared supportive but I'm not sure what they can do other than taking the unit back to install a new internal wireless adapter.

The bottom line is: order your X200 with one of the optional (and more expensive) Intel wireless adapters which apparently are fully supported in Ubuntu/Linux.

---

### Post by TheCan on 2009-06-23
Hi Emigallo,

thanks for sharing this information with the community. Did you try to use Ndiswrapper with the Windows Drivers for this Wifi-Card? And did you order a CTO-X200? As far as I remember, Lenovo offered various options regarding the wifi-card when ordering the Laptop directly.

---

### Post by Emigallo on 2009-06-24
> **TheCan said:**
> Hi Emigallo,

thanks for sharing this information with the community. Did you try to use Ndiswrapper with the Windows Drivers for this Wifi-Card? And did you order a CTO-X200? As far as I remember, Lenovo offered various options regarding the wifi-card when ordering the Laptop directly.

I did not try to use ndiswrapper because discouraged by this posting:

[http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&thread.id=1195](http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&thread.id=1195)

My X200 is indeed the "CTO" kind, the specific model number is 7458-CTO. Indeed I should have selected one of the supported Intel wireless cards when ordering but didn't because the information I had gathered indicated that the "default" card was the Atheros-based one (which is amply documented to be well supported by Ubuntu/Linux).

---

### Post by Xinef on 2009-06-29
Hello, just here to add my stone about what works, or more precisely what does not.
I use 9.04 updated.
Do not work:
- The power button and sound mute button (nothing under xev)
- The fan control: as many others, the fan speed only goes up, never down
- Reported battery time is half of what the computer actually holds
- fingerprint reader

Out of this all, I do not mind much, except the fan issue that gets on my nerves. The "auto" level is supposed to hand the fan speed control to some kind of hardware controller right? Why would the speed only go up? I do not want to risk overheating by installing third-part utilities, but I really hate wasting battery time and, decibels (not much though) and fan lifetime for nothing.

EDIT: speaker now works. Only 4 things to go.
EDIT2: forgot the fingerprint reader

---

### Post by GrouchoMarx on 2009-06-29
> Out of this all, I do not mind much, except the fan issue that gets on my nerves. The "auto" level is supposed to hand the fan speed control to some kind of hardware controller right? Why would the speed only go up? I do not want to risk overheating by installing third-part utilities, but I really hate wasting battery time and, decibels (not much though) and fan lifetime for nothing.

What type of wireless card do you have? For my Intel Wifi 5300, I was able to turn on wireless power management via:

```
sudo iwconfig wlan0 power on
```

The fan is still slow to respond to changes in wireless state, but after a while, it does eventually spin down on its own. Importantly, now my fan never turns on unless the wireless is under heavy load. I am curious if this works for anyone else.

---

### Post by toasty_ghosty on 2009-06-29
I was planing on ordering a X200 this week at some point. Good thing I noticed this...quick question though, if the power button doesn't work, how do you turn it on?

-Ghosty

---

### Post by Xinef on 2009-06-29
>GrouchoMarx
I will try this as soon as I get home.

>toasty_ghosty
The power button works in hardware, but when linux is up, it won't work in soft... No big deal, you just cannot associate any action to the power button.

---

### Post by toasty_ghosty on 2009-06-29
FYI, when I was looking around for thoughts on this laptop, might have been Arch forums, and there is a bug report regarding the naming of the 5300 wireless card and heres at least a forum post about it...but its only a name issue.

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/intel-5300-thinks-its-a-5100-707520/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/intel-5300-thinks-its-a-5100-707520/)

---

### Post by Xinef on 2009-06-30
> **GrouchoMarx said:**
> What type of wireless card do you have? For my Intel Wifi 5300, I was able to turn on wireless power management via:

```
sudo iwconfig wlan0 power on
```

The fan is still slow to respond to changes in wireless state, but after a while, it does eventually spin down on its own. Importantly, now my fan never turns on unless the wireless is under heavy load. I am curious if this works for anyone else.
I have the same card, I could execute your command and see in iwconfig that power management got activated.
Still the fan is stuck well over 3000 rpms, even when I let the computer sit idle for over 20 minutes, and as before, once it ramped up to a certain speed, won't go back down.
You seem to point the finger at the wlan adapter for the whole speeding fan problem, but does it really generate that much heat?
I think I will try to boot a live fedora 11 image to see if there is any difference...
This is kind of a heart-break to have only a nearly-perfectly running machine :/

---

### Post by GrouchoMarx on 2009-07-02
> I let the computer sit idle for over 20 minutes, and as before, once it ramped up to a certain speed, won't go back down.

Hmm. Yeah, to be perfectly honest I may have jumped the gun about the fan spinning down. I have left it overnight a few times and then found the fan off in the morning, but I have never actually "seen" it go off. That was dumb, I shouldn't have assumed anything. However, between 8.10 and 9.04 there has been a clear and reproducible improvement what regards the fan turning on in the first place. With power management activated in Jaunty the fan rarely turns on unless the wireless is working really hard. Without power management, my fan automatically turns on after about 10 minutes. However, unlike in Jaunty, turning on power management in Intrepid had no effect. The only way to prevent the fan from turning on in Intrepid was to activate the wireless kill switch, which is what led me to suspect the wireless card in the first place. So something changed between 8.10 and 9.04, and as the Intel drivers are open source, and the laptop is fairly popular, I'm hopeful that we will continue to see improvements with each release.

---

### Post by Xinef on 2009-07-03
Well it is really not that bad, I just feel like there is some power wasted in creating useless wind... I mean I do not think the fan needs to be at 4000 rpms when the CPU is at 37~39 degrees, knowing that room temperature is close to 30...
Anyways, I have good hopes for this to improve. A fan overworking is still better than a non-working one.
It appears that there is no documentation for the fingerprint reader and that some reverse-engineering has to be done but is not planned so far... So we'll have to forget about it for probably a year at best before it ends up merged in the kernel.
I have no clue how long it will take for the mute and power buttons to be mapped properly.
Finally I have some problems getting my microsoft bluetooth mouse to work with the jaunty, this has probably something to do with the bluez stack and since I am not alone in that case I expect improvements in a near future.
I could not get to test fedora so far because the usb startup disk creator won't accept fedora images :/ I will try again when I have more time.
Cheers, and if you happen to have solutions for any of those issues, you are welcome to leave a comment and give us hope ;)

---

### Post by Xinef on 2009-07-08
A small update there.
I installed Fedora 11, it works beautifully, so I do not regret Jaunty much.
The problem with the mouse pairing went away, but the rest is still there to stay...
The button mapping and fan control API seem to be an undocumented change on the Lenovo side. If I can find some time, I will try to investigate it, but for now I'll just keep my machine up to date in hope of getting the update that makes it right some time ;)
Cheers

---

### Post by AlesUbu123 on 2009-07-25
Hi all, has anyone tried the undervolting approach to improve the battery life and reduce the fan sound explained on this link: [Extending_battery_life_on_X200]("http://www.thinkwiki.org/wiki/Extending_battery_life_on_X200"). I got stuck at the the step of installing phc modules (i did not have acpi-cpufreq module loaded). Is it worth it?

Also I have tried Fedora, but the fan problem is also present here.

---

### Post by maverickonair on 2009-08-01
> **GrouchoMarx said:**
> 
...
Turning on the wireless power management:
...


Thanks! Works great for me with the WiFi Link 5300 card =)!

---

### Post by Emigallo on 2009-08-01
> **Mr.Carramba said:**
> 
Does anyone have managet to get ultrabase to work?


I've just started using the X200 UltraBase. No issues so far with my 64bit 9.04 installation. As far as I can tell everything works out of the box: DVD+RW, Audio, Video Out, ethernet, USB ports, etc.

---

### Post by lorenz_b on 2009-08-04
Hi everyone!
Is there already a working setup for the fingerprint reader?

cheers,
Lorenz

---

### Post by desmane on 2009-08-04
hello people, 

everything works out of the box here. Thats great. I even got the hdd protection thingy working with smapi. yeah!

But one thing bugs me a lot and I even thought going back to windows because of this (I actually ran it for couple of days but.. well, windows is not a solution :D )

The Intel Power Manager / Battery Tool in Windows is totally awesome, the x200 runs stone cold and I get up to 10h battery life, if idle even up to 12 hours. 

In Linux however, (battery up to 8h, i can life with that) the bottom side at the front (just underneath the mouse bottons) **gets REALLY hot**! I dont understand that, since with powertop / fancontrol it just shouldn`t be. 

would the **undervolting** described [_here_]("http://www.thinkwiki.org/wiki/Extending_battery_life_on_X200#Reducing_CPU_voltage") fix this issue? Did anybody try it because I am really concerned to screw things up and damage my hardware! 

How does intel get the x200 that cold in windows? 

and there is one more question, if I put Option "NoDRI" in the Device section of xorg.conf, suspend and hibernation stops working. Since I prefer battery over everything else, whats the solution?

If someone has the tearing problems while playing videos, a fix is to add the ppa [_here_]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") for installting the intel driver. Works great. 

running ubuntu jaunty, 2.6.28-11-generic, (should i get the 64bit version??)

Thanks for your help!! Hope you have ideas...


update: added screenshots tpfand and powertop for comparison

---

### Post by desmane on 2009-08-07
hey AlesUbu123

those modules are in the kernel in jaunty, so patching not possible anymore. 

go here [https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)

add this ```
deb http://ppa.launchpad.net/linux-phc/ppa/ubuntu jaunty main
``` to your sources.list

key: ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4D950ED1
```

and upgrade to a patched phc kernel

if you have the penryn p8400 core2duo with 2,26GHz check those values: 

[http://vaioubuntu.wordpress.com/2008/09/11/undervolting-your-cpu-for-longer-battery-life/#]("http://vaioubuntu.wordpress.com/2008/09/11/undervolting-your-cpu-for-longer-battery-life/#")

---

### Post by alecwh on 2009-08-17
Hello,

I just ordered my X200, and I cannot get wifi working. I have Ubuntu 9.04 installed. I have followed the directions in previous posts, such as the madwifi fix... but nothing has worked. The light doesn't even come on.

A few posts back, someone mentioned that there are no drivers for this card. Is this really the case?

Is there -any- way to fix this? If I cannot get wifi working, then this laptop will need to be returned. :(

Thanks in advance!

---

### Post by lorenz_b on 2009-08-21
have you tried to press Fn + F5? you have to press it multiple times, because on my X200 it first starts up bluetooth, then BT and WiFi, then WiFi alone, then both off again. Be also sure to have the WiFi switch on when trying this.
hope this helps.
Lorenz

---

### Post by Emigallo on 2009-08-22
> **alecwh said:**
> Hello,

I just ordered my X200, and I cannot get wifi working. I have Ubuntu 9.04 installed. I have followed the directions in previous posts, such as the madwifi fix... but nothing has worked. The light doesn't even come on.

A few posts back, someone mentioned that there are no drivers for this card. Is this really the case?

Is there -any- way to fix this? If I cannot get wifi working, then this laptop will need to be returned. :(

Thanks in advance!
If 'lspci' shows:

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

then it looks like you're just as out of luck as me. Instead of returning the X200 I got myself a wifi Express card on ebay (Dell Wireless 1390) which works fine.

---

### Post by BradNeuman on 2009-08-27
Just got an X200s (non-tablet) and installed 9.04 (x64) on it. Everything is working pretty well except I am having the fan issue and I cannot, for the life of me, get middle mouse button scrolling working. I have tried every approach I found online including the old way of modifying the Xorg.conf file and all of the mouse-wheel.fdi scripts, including switching around the axes, spelling them right and wrong, deleting the cache, restarting countless times, all to no avail.


With my current setup I get:
```
$ xinput -list-props "TPPS/2 IBM TrackPoint"
Device 'TPPS/2 IBM TrackPoint':
	Device Enabled (99):		1
	Evdev Axis Inversion (231):		0, 0
	Evdev Reopen Attempts (232):		10
	Evdev Axis Calibration (233):		
	Evdev Axes Swap (234):		0
	Evdev Middle Button Emulation (235):		1
	Evdev Middle Button Timeout (236):		50
	Evdev Wheel Emulation (237):		1
	Evdev Wheel Emulation Axes (238):		0, 0, 4, 5
	Evdev Wheel Emulation Inertia (239):		10
	Evdev Wheel Emulation Timeout (240):		200
	Evdev Wheel Emulation Button (241):		2
	Evdev Drag Lock Buttons (242):		0

```

I have also been able to get the axes to be something like 6,7,4,5 and that didn't work either. If I launch xev I only get normal mouse-move events when I hold the middle click.

I have no idea what might be causing this problem, any ideas?

Overall I am loving this laptop! but not being able to scroll is a serious issue.

---

### Post by Chrigi on 2009-10-08
I just recently installd the Karmic beta on my X200 and have some strange regressions:

[LIST]
[*]The Bluetooth can not be disabled by pressing Fn+F5. It will either turn off WiFi AND BT or it will eneable them both.
[*]The volume up and down buttons work but the the mute button does not.
[/LIST]
Is there a way to fix/change this?

---

### Post by Xinef on 2009-10-08
Chrigi: for the mute button, you just need to add acpi_osi="Linux" to your kernel line in menu.lst (grub)

---

### Post by Chrigi on 2009-10-08
As I use the Karmic Beta and therefore GRUB2 (1.97beta3) the menu.lst will be ignored (right?) is there another way? Or how would I do that for GRUB2?

// Edit: I foound out howto do it :) thank you

---

### Post by alecwh on 2009-10-10
Hello, I posted earlier about the wifi card that won't work under Ubuntu. I have successfully replaced it with the card recommended above (Dell Wireless 1390) that I got off ebay for like 25 bucks. If anyone has any questions about this procedure, PM me!

Next question: How is Karmic working with the X200? Are there less issues out of the box?

---

### Post by temo's on 2009-10-31
dear All,
i have Lenovo x200 tablet, and i want to install Ubuntu 9.04 on it solely.
i wander if this applicable or not and what are problems i'll face after that.

best regards

---

### Post by SGFHK321 on 2009-11-03
I recently installed 9.10 on a brand new X200.  Middle button scrolling does not work (I have practically tried all solutions posted on the Internet).  

The closest thing I have to a solution is these terminal commands:
> xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Y Axis" 8 4 5
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation X Axis" 8 6 7 

---

### Post by codeFX on 2009-11-15
After auto-upgrade to Karmic Koala my X200 was completely messed up ...
(xorg won't starts the intel driver anymore - starting compiz just resulted in a white screen)

it took me a while until I got it working again - have posted the solution to my [blog]("http://www.codefx.biz/2009/11/karmic-koala-with-i915/").

---

### Post by Emigallo on 2009-12-13
This is to confirm that a working driver has appeared for the Realtek wifi card

$lspci -vv | grep Realtek
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device e020

See:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)


32bit and 64bit versions are available:
[http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz](http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz)
[http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)

I have installed without problems the 64bit version on my X200 freshly upgraded to 9.10. Just make sure you have linux-headers installed and run BOTH "make" and "make install" as root.

---

### Post by davidsinterested on 2009-12-15
hi i installed karmic 9.10, but i don't know how to install hdaps??
i'm a real newbie to this, so if you could explain it for dummies that would be awesome.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_X200](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_X200)

has some details but i don't understand it :(

[I]Nevertheless hdaps seems to work fine with thinkpad_ec. After installing hdapsd edit /etc/default/hdapsd make sure START ihttps://launchpad.net/~flomars set to "yes", DISK to "sda" and adjust SENSITIVITY (50 works ok for most people).

edit: use tp-smapi as in [1] [/I]

make sure START ihttps://launchpad.net/~flomars set to "yes", DISK to "sda" and adjust SENSITIVITY (50 works ok for most people).

I DON"T UNDERSTAND THIS PART...

if someone knows it be awesome if they could post up a simple set of detailed instructions...MANY THANKS! 


oh and also is there anyway of having the fingerprint reader work?

---

### Post by davidsinterested on 2009-12-15
.

---

### Post by maple on 2009-12-25
> **Chrigi said:**
> As I use the Karmic Beta and therefore GRUB2 (1.97beta3) the menu.lst will be ignored (right?) is there another way? Or how would I do that for GRUB2?

// Edit: I foound out howto do it :) thank you

Why don't you make your edit more useful by explaining how you did it instead of just letting us know you did it.

---

### Post by Reboli_NL on 2010-01-12
Hi all,

I recently got myself a Lenovo x200 tablet and most stuff works out of the box:

[LIST]
[*]Video
[*]Pointer
[*]GPS (Ericsson F3507g) ;-)
[*]Webcam
[*]Wifi (intel 5300)
[*]Lock/Sleep/Suspend
[/LIST]
With some work:

[LIST]
[*]Stylus/Multi-Touch
[*]Scroll button
[/LIST]
What doesn't work is:

[LIST]
[*]Soundcard Intel HDA Conexant CX20561 (Hermosa). (Despite the audio gotcha's article)
[*]Fingerprint reader: New unsupported model
[*]Powerbuttons (No reaction)
[/LIST]
lspci for audio:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Device 20f2
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 31
        Region 0: Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```Anything I could have missed with the soundpart? :-(

OS: Xubuntu 9.10 Karmic amd64

---

### Post by GrouchoMarx on 2010-01-14
Since I've owned this laptop I have not been able to get rid of a faint, yet incredibly annoying buzz during audio playback. Does anyone else have this problem? Have they found a solution? It's subtle, but enough to ruin quiet music like Jazz or Classical. Is this just a matter of poorly shielded electronics? I've fiddled with the levels of every possible volume control to make sure that the sound wasn't just being compressed. Any ideas?

---

### Post by Reboli_NL on 2010-01-29
Some updates further on my x200 tablet.... 
Somewhere there must have been a tradeoff I'm not aware of.... Touch and eraser don't work anymore, yet sound is just fine :?
Tried re-installing the drivers [from source]("http://ubuntuforums.org/showthread.php?t=1038949") as I did before to no avail.
Upside is that they are listed in lshal.
I think I'll better wait till the new driver is a version further. :(

---

### Post by Reboli_NL on 2010-02-07
Hi again,

I was wondering if anyone tried more that 4GB in his X200 (tablet)?
The chipset is 8GB capable, yet specs upto this day stay limited to 4GB
Some Lenovo forums I read support the notion the chipset (and laptop) can handle the 8GB.
What are your experiences? Does it run well?
Thanks

---

### Post by Gompa on 2010-02-10
you can get active protection to work by folowing the info in [this link ]("http://www.h-bomb.nl/active-protection-in-ubuntu-9-10")

---

### Post by flomar on 2010-03-09
Has anybody seen some progress on the batterylife and heat problem when using a fresh install of 10.04 that is still in development? If it's to soon to tell, is there plans that could help solve this problem?

---

### Post by flomar on 2010-04-14
Hi,

I just installed the Ubuntu 10.04 Beta on my Thinkpad X200 via Wubi, for those interested here`s my first impressions - I will update from time to time as I encounter issues relevant for X200 owners.

**List of problems with 10.04 Beta on X200:**
[LIST]
[*]Fan problem persists [bugreport](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380303)
[*]Ultranav scrolling doesn't work (except in firefox) [fix](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Configuration_using_Gnome)
[*]Bluetooth permanent ON at startup persists [bugreport](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/280811)
[*]Mute button still not working [bugreport](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281732)
[*]Reactivating Wifi via hardware switch needs reboot
[*]idle screen brightness diming, return to standard level instead of previous level 
[*]Loud noise at shutdown
[*]Panel brightness applet not clickable [bugreport]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/535097")
[/LIST]
More general and not especially X200 related, everyting seems to work out of the box like WLAN, Audio, Graphics etc...

---

### Post by NDLunchbox on 2010-05-04
I upgraded to 10.04 from 9.10.  Had some funkyness, just did a fresh install.  Experiencing the problems listed above, plus I'm getting random flashes of a static bar across the bottom third of the screen difficult to explain, it's like a bar of digital noise.  I have not found a way to reproduce it and it's only happened a few times, but it is strange.

---

### Post by bowsercake on 2010-05-21
Has anyone been able to adjust the trackpoint sensitivity in 10.04?

---

### Post by Russianguy on 2010-06-08
Hi guys, 

I am looking to upgrade my Lenovo X200 with an 500 GB SSD, preferably with a Sandforce controller. Any suggestions which brand to choose?

---

### Post by rearviewmirror on 2010-06-28
How's everyone going with 10.04 on their X200?  I'm interested in ditching XP and running Ubuntu on my work laptop.  

A couple of months ago this was posted,

List of problems with 10.04 Beta on X200:

    * Fan problem persists bugreport
    * Ultranav scrolling doesn't work (except in firefox) fix
    * Bluetooth permanent ON at startup persists bugreport
    * Mute button still not working bugreport
    * Reactivating Wifi via hardware switch needs reboot
    * idle screen brightness diming, return to standard level instead of previous level
    * Loud noise at shutdown
    * Panel brightness applet not clickable bugreport


Are these issues still outstanding?

Thanks.

---

### Post by Jabz.biz on 2010-06-29
I've made a fresh install of the Lynx on my X200s last week. So far everything works great.

* Fan problem persists bugreport -> I have none.
* Ultranav scrolling doesn't work (except in firefox) fix
* Bluetooth permanent ON at startup persists bugreport -> Kool with me, as I have plenty of Bluetooth devices connected.
* Mute button still not working bugreport -> Mine works on the external keyboard, the button the X200s itself does not work.
* Reactivating Wifi via hardware switch needs reboot -> Confirmed.
* idle screen brightness diming, return to standard level instead of previous level
* Loud noise at shutdown -> Nope. Everything is fine here.
* Panel brightness applet not clickable bugreport -> Can't confirm.

---

### Post by lawrencius on 2010-07-08
Hey Every1,

I updated to 10.04 and the built-in webcam doesn't connect anymore. Has anybody had similar problems? 
Any advice would be appreciated.

Best,
Nicholas

---

### Post by rearviewmirror on 2010-07-09
> **lawrencius said:**
> Hey Every1,

I updated to 10.04 and the built-in webcam doesn't connect anymore. Has anybody had similar problems? 
Any advice would be appreciated.

Best,
Nicholas

I did a full install of 10.04 on my X200, the camera works fine in Skype and other apps.

---

### Post by copyhold on 2010-07-11
he||o all
so x200 connects to wireless network with no problem , but then not periodically looses connection and can't even ping to router.
this is not happened with win7 installed on same x200 and same ubuntu but with other router.

this might happen once a minute or once in 5 minutes without any period.

how can i check where is the problem?

Signal strength is always > 60%

---

### Post by lawrencius on 2010-07-15
bump

---

### Post by valbaca on 2010-07-19
I've been away from Ubuntu for a while (using other distros and learning A LOT) but finally came back and am glad I did.
I'm loving 10.04 and am so glad that it's LTS.
I just ordered a OCZ Vertex 2 50GB SSD and am eager to see how it speeds up an already speedy machine.

---

### Post by schmickey on 2010-07-19
Anyone know how to get the "Thinkpad b/g/n" card working in Lucid?  I'm using the AMD64 version.  I think it is actually a RealTek card.

---

### Post by valbaca on 2010-07-20
> **schmickey said:**
> Anyone know how to get the "Thinkpad b/g/n" card working in Lucid? I'm using the AMD64 version. I think it is actually a RealTek card.
 
Try this: [http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II)
 
I can't confirm the above; I have the Intel 5300 (works with any linux kernel after 2.6.28 )

---

### Post by James Paige on 2010-07-29
I recently upgraded from 9.10 to 10.04. The upgrade went smoothly, and I did not notice any problems at the time.

<s>Today, I realized that my touchscreen/stylus has stopped working :(</s>

EDIT: Nevermind, seemed to be a one-time problem. After a reboot it works fine again (even after subsequent hibernate/wakeups) ... I hate fixing problems "the windows way" :P


> **lawrencius said:**
> Hey Every1,

I updated to 10.04 and the built-in webcam doesn't connect anymore. Has anybody had similar problems? 
Any advice would be appreciated.

Best,
Nicholas

What? I was never aware of a webcam in the X200! Did Lenovo make more than one version of the X200? Where is the webcam located?

---

### Post by Jaydon H on 2010-07-29
It's a shame those changes aren't applicable to Ubuntu 10.04. Tablet also works on X200 Tablet. Thinkpad X200s rock!

---

### Post by odd on 2010-08-01
Hi everyone

Does anybody experiencing issues with PressCurve on Lenovo X200 Tablet PC with Ubuntu Lucid I've described here [http://sourceforge.net/tracker/?func=detail&aid=3008864&group_id=69596&atid=525124](http://sourceforge.net/tracker/?func=detail&aid=3008864&group_id=69596&atid=525124) ? Or it's just me? It makes tablet quite annoying while drawing (unable to draw smooth fades from light to intensive lines etc.).

---

### Post by Payteer on 2010-10-03
with the new bios update, I am unable to get my usb drive to install ubuntu, I have also used an external dvd drive with a live dvd, but the computer does not recognise this either.  Can anyone help on this


Update on this issue
I worked out how to do it, you need to change the bios to look to the USB key first before the hard drive, then it will read the new install.  Pain in the neck, but got it to work.

---

### Post by Mr.Carramba on 2010-10-05
had 10.04 everything worked without problems.
Now running 10.10 beta and as no major problems with it. Some times it does hands from suspend. But, hey, its still beta.

---

### Post by gerv on 2010-10-12
I've upgraded to 10:10 (Maverick Meerkat). Has anyone else had trouble with their CD/DVD drives, both reading and burning? 

I'm getting intermittent behaviour, failure to automount, burns producing coasters, all sorts of trouble - both on the drive in my dock, and an external Samsung drive which works fine with my older 9.04 laptop.

Am I alone?

Gerv

---

### Post by midas13 on 2010-10-14
Upgraded to 10.10. And now have troubles with suspending: sometimes (not every time, may be in one of 4-5 cases) after closing notebook cover it doesn't suspend (fan is working and display is on) and crescent led is blinking. In 10.04 suspending worked fine. 
I'v tried to find some relations betweeen this problem and running software but didn't succeed. Also couldn't find any errors in logs.

Does anybody have the same problem? Where should I look at?

---

### Post by gerv on 2010-10-15
Yep, I've been seeing this too. Looking at my syslog, it looked like there was a problem suspending the wifi. I added iwlagn to /etc/modules/acpi-support's blacklist, to see if that helped. But I don't have enough data yet.

Check /var/log/syslog after you reboot after the failed suspend, look for the last thing that happened.

---

### Post by midas13 on 2010-10-15
I have now logs corresponding normal suspend and failed one.

normal:
```
Oct 15 13:15:27 lunatik-x200 kernel: [ 3683.642879] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Oct 15 13:15:27 lunatik-x200 kernel: [ 3683.683432] EXT4-fs (sda7): re-mounted. Opts: commit=0
Oct 15 13:15:28 lunatik-x200 kernel: [ 3684.174573] EXT4-fs (sda6): re-mounted. Opts: commit=0
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> sleep requested (sleeping: no  enabled: yes)
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> sleeping or disabling...
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (eth0): now unmanaged
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (eth0): device state change: 8 -> 1 (reason 37)
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (eth0): deactivating device (reason: 37).
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (eth0): canceled DHCP transaction, DHCP client pid 4340
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (eth0): cleaning up...
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (eth0): taking down device.
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (wlan0): now unmanaged
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (wlan0): device state change: 2 -> 1 (reason 37)
Oct 15 13:15:28 lunatik-x200 NetworkManager[1200]: <info> (eth0): carrier now OFF (device state 1)
Oct 15 13:15:28 lunatik-x200 init: anacron main process (4166) killed by TERM signal
Oct 15 13:15:29 lunatik-x200 kernel: [ 3685.545548] PM: Syncing filesystems ... done.
Oct 15 13:15:29 lunatik-x200 kernel: [ 3685.549788] PM: Preparing system for mem sleep
Oct 15 13:15:52 lunatik-x200 acpid: client 1339[0:0] has disconnected
Oct 15 13:15:52 lunatik-x200 kernel: [ 3685.990414] Freezing user space processes ... (elapsed 0.02 seconds) done.
Oct 15 13:15:52 lunatik-x200 rtkit-daemon[1603]: The canary thread is apparently starving. Taking action.
Oct 15 13:15:52 lunatik-x200 rtkit-daemon[1603]: Demoting known real-time threads.
Oct 15 13:15:52 lunatik-x200 rtkit-daemon[1603]: Successfully demoted thread 2017 of process 1951 (n/a).
Oct 15 13:15:52 lunatik-x200 rtkit-daemon[1603]: Successfully demoted thread 2008 of process 1951 (n/a).
Oct 15 13:15:52 lunatik-x200 rtkit-daemon[1603]: Successfully demoted thread 1951 of process 1951 (n/a).
Oct 15 13:15:52 lunatik-x200 rtkit-daemon[1603]: Demoted 3 threads.
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.011399] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.031391] PM: Entering mem sleep
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.031472] Suspending console(s) (use no_console_suspend to debug)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.071574] sd 1:0:0:0: [sda] Synchronizing SCSI cache
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.071741] sd 1:0:0:0: [sda] Stopping disk
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087708] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087719] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087731] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087737] pciehp 0000:00:1c.3:pcie04: pciehp_suspend ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087742] pciehp 0000:00:1c.2:pcie04: pciehp_suspend ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087752] pciehp 0000:00:1c.0:pcie04: pciehp_suspend ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087781] ehci_hcd 0000:00:1a.7: PCI INT D disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087793] uhci_hcd 0000:00:1a.2: PCI INT C disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.087806] uhci_hcd 0000:00:1a.0: PCI INT A disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.088005] e1000e 0000:00:19.0: PME# enabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.088013] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.090055] uhci_hcd 0000:00:1a.1: PCI INT B disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.101294] pciehp 0000:00:1c.1:pcie04: pciehp_suspend ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.101348] i915 0000:00:02.0: power state changed by ACPI to D3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.120023] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.190353] HDA Intel 0000:00:1b.0: PCI INT B disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.210021] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 122.263 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.400938] PM: suspend of drv:sd dev:1:0:0:0 complete after 329.366 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.400949] PM: suspend of drv:scsi dev:target1:0:0 complete after 329.329 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.400957] PM: suspend of drv:scsi dev:host1 complete after 329.266 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.460027] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 372.337 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.460037] PM: suspend of drv: dev:pci0000:00 complete after 372.010 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.460045] PM: suspend of devices complete after 428.194 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.460047] PM: suspend devices took 0.430 seconds
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.501311] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.521305] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.561305] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.581305] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.651296] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.651424] PM: late suspend of devices complete after 191.373 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3686.751299] ACPI: Preparing to enter system sleep state S3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.131326] PM: Saving platform NVS memory
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.141081] Disabling non-boot CPUs ...
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.290031] CPU 1 is now offline
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.290034] SMP alternatives: switching to UP code
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.296531] Extended CMOS year: 2000
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.296531] Back to C!
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.296531] PM: Restoring platform NVS memory
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.296531] Extended CMOS year: 2000
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.296531] Enabling non-boot CPUs ...
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.296531] SMP alternatives: switching to SMP code
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.302891] Booting Node 0 Processor 1 APIC 0x1
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.580343] CPU1 is up
Oct 15 13:15:52 lunatik-x200 kernel: [ 3687.581309] ACPI: Waking up from system sleep state S3
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.381445] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.381469] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.381481] pci 0000:00:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.491296] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.511304] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.511332] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.531304] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.551304] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.551308] PM: early resume of drv:uhci_hcd dev:0000:00:1a.0 complete after 169.763 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.551339] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.571304] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.591303] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.591331] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.611304] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.631304] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.631342] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.651304] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671304] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671344] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100102)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671384] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc031c021)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671389] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xc010c000)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671394] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0xf0, writing 0x4040)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671405] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671459] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc051c041)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671465] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0xf0, writing 0x5050)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671477] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671530] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x1fff1, writing 0xc071c061)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671544] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.671609] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.691304] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.711304] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.711332] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.731304] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.751303] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.751334] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.751373] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.751418] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.771304] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791304] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791317] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x40000, writing 0x400ff)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791328] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791333] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791338] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791349] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791442] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791573] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791661] pci 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791687] pci 0000:04:00.0: restoring config space at offset 0x6 (was 0x1, writing 0x2001)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791696] pci 0000:04:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf2600000)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791703] pci 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.791712] pci 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.792059] PM: early resume of devices complete after 410.728 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.801313] i915 0000:00:02.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.801348] i915 0000:00:02.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.801353] i915 0000:00:02.0: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.801391] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.801396] e1000e 0000:00:19.0: PME# disabled
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.801469] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803590] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803596] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803621] usb usb4: root hub lost power or was reset
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803705] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803712] HDA Intel 0000:00:1b.0: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803749] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803784] pciehp 0000:00:1c.0:pcie04: pciehp_resume ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803789] pciehp 0000:00:1c.1:pcie04: pciehp_resume ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803794] pciehp 0000:00:1c.2:pcie04: pciehp_resume ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803798] pciehp 0000:00:1c.3:pcie04: pciehp_resume ENTRY
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803839] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803844] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803869] usb usb7: root hub lost power or was reset
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803889] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803894] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803917] usb usb8: root hub lost power or was reset
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803970] pci 0000:00:1e.0: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.803986] ahci 0000:00:1f.2: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.804069] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.804410] sd 1:0:0:0: [sda] Starting disk
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.813949] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814163] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814175] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814184] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814195] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814224] usb usb3: root hub lost power or was reset
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814304] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814425] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814543] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814830] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814892] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814898] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814930] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814934] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814944] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.814979] usb usb5: root hub lost power or was reset
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.815112] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.815166] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.815173] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.815204] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.815209] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.815216] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.815239] usb usb6: root hub lost power or was reset
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.961371] PM: resume of drv:usb dev:usb8 complete after 157.094 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.961394] PM: resume of drv:usb dev:usb7 complete after 157.150 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.961400] PM: resume of drv:hub dev:8-0:1.0 complete after 157.106 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.961412] PM: resume of drv:hub dev:7-0:1.0 complete after 157.151 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980055] PM: resume of drv:usb dev:usb6 complete after 175.839 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980078] PM: resume of drv:usb dev:usb5 complete after 175.891 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980084] PM: resume of drv:hub dev:6-0:1.0 complete after 175.853 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980092] PM: resume of drv:hub dev:5-0:1.0 complete after 175.890 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980099] PM: resume of drv:usb dev:usb3 complete after 175.972 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980104] PM: resume of drv:usb dev:usb2 complete after 176.006 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980111] PM: resume of drv:hub dev:3-0:1.0 complete after 175.970 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.980115] PM: resume of drv:hub dev:2-0:1.0 complete after 176.003 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3688.981447] PM: resume of drv:i915 dev:0000:00:02.0 complete after 180.170 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.071365] PM: resume of drv:usb dev:usb4 complete after 267.210 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.071394] PM: resume of drv:hub dev:4-0:1.0 complete after 267.221 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.091374] usb 2-6: reset high speed USB device using ehci_hcd and address 2
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.151329] ata2: SATA link down (SStatus 0 SControl 300)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252638] PM: resume of drv:usb dev:2-6 complete after 448.331 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252666] PM: resume of drv:usb-storage dev:2-6:1.0 complete after 448.344 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252679] PM: resume of drv: dev:ep_81 complete after 177.849 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252695] PM: resume of drv:scsi dev:host0 complete after 448.359 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252709] PM: resume of drv:scsi dev:target0:0:0 complete after 448.243 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252713] PM: resume of drv:scsi_host dev:host0 complete after 448.361 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252726] PM: resume of drv:sd dev:0:0:0:0 complete after 448.247 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.252754] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 448.261 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.371365] usb 4-1: reset full speed USB device using uhci_hcd and address 2
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.527857] PM: resume of drv:usb dev:4-1 complete after 723.472 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.527883] PM: resume of drv:usb dev:4-1:1.0 complete after 723.484 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3689.527909] PM: resume of drv: dev:ep_81 complete after 275.212 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.531376] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.534471] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.534476] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.534580] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.534584] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.550283] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.550288] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.550396] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.550400] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.553669] ata1.00: configured for UDMA/133
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.585653] ata1.00: configured for UDMA/133
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.585657] ata1: EH complete
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.591894] PM: resume of drv:sd dev:1:0:0:0 complete after 1787.478 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.591907] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 1063.986 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.591923] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 1787.471 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.594566] PM: resume of devices complete after 1802.455 msecs
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.594764] PM: resume devices took 1.800 seconds
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.594792] PM: Finishing wakeup.
Oct 15 13:15:52 lunatik-x200 kernel: [ 3690.594794] Restarting tasks ... done.
```

failed:
```

Oct 15 13:19:14 lunatik-x200 ntpd[5377]: kernel time sync status change 2001
Oct 15 13:34:14 lunatik-x200 ntpd[5377]: synchronized to 193.79.237.14, stratum 1
Oct 15 13:40:33 lunatik-x200 anacron[5589]: Anacron 2.3 started on 2010-10-15
Oct 15 13:40:33 lunatik-x200 anacron[5589]: Normal exit (0 jobs run)
Oct 15 13:40:33 lunatik-x200 kernel: [ 5172.062361] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Oct 15 13:40:34 lunatik-x200 kernel: [ 5172.807088] EXT4-fs (sda7): re-mounted. Opts: commit=0
Oct 15 13:40:34 lunatik-x200 kernel: [ 5172.813851] EXT4-fs (sda6): re-mounted. Opts: commit=0
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> sleep requested (sleeping: no  enabled: yes)
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> sleeping or disabling...
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (eth0): now unmanaged
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (eth0): device state change: 8 -> 1 (reason 37)
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (eth0): deactivating device (reason: 37).
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (eth0): canceled DHCP transaction, DHCP client pid 5254
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (eth0): cleaning up...
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (eth0): taking down device.
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (wlan0): now unmanaged
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (wlan0): device state change: 2 -> 1 (reason 37)
Oct 15 13:40:35 lunatik-x200 NetworkManager[1200]: <info> (eth0): carrier now OFF (device state 1)
Oct 15 13:49:58 lunatik-x200 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Oct 15 13:49:58 lunatik-x200 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1044" x-info="http://www.rsyslog.com"] (re)start
Oct 15 13:49:58 lunatik-x200 rsyslogd: rsyslogd's groupid changed to 102
Oct 15 13:49:58 lunatik-x200 rsyslogd: rsyslogd's userid changed to 101
Oct 15 13:49:58 lunatik-x200 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 15 13:49:58 lunatik-x200 kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 15 13:49:58 lunatik-x200 kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 15 13:49:58 lunatik-x200 kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 (Ubuntu 2.6.35-22.34-generic 2.6.35.4)
Oct 15 13:49:58 lunatik-x200 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=76bd440c-e9cd-4a82-a19f-99f36cdf6673 ro quiet splash
```

It's seems that wifi has nothing to do with suspending problem: i have my wifi module turned off in both variants. In failed case i had to turn off notebook with power button and only beginning of booting process is shown.

---

### Post by imraj on 2010-10-16
I recently installed 10.10; 

but am unable to get PEN working properly. 
I can't scroll up/down.
I can't right-click.
Mouse location is disoriented in Portrait mode.

---

### Post by cpeee on 2010-10-19
I encounter exactly the same issue. I've updated my BIOS to 3.15 (x200 thinkpad) but still no joy. Unable to spot any error in the PM suspend log. Looks like a major show stopper. May consider downgrade to 10.04 if I can't do any workaround. 

> **midas13 said:**
> Upgraded to 10.10. And now have troubles with suspending: sometimes (not every time, may be in one of 4-5 cases) after closing notebook cover it doesn't suspend (fan is working and display is on) and crescent led is blinking. In 10.04 suspending worked fine. 
I'v tried to find some relations betweeen this problem and running software but didn't succeed. Also couldn't find any errors in logs.

Does anybody have the same problem? Where should I look at?

---

### Post by lawrencius on 2010-10-20
Hello everyone,

I recently upgraded to 10.10 and the built-in webcam does not seem to get recognized in cheese/skype. Has anybody experienced something akin to that? 

Any help/tip would be appreciated.
Cheers,
Nicholas

---

### Post by Calorus on 2010-10-25
Are any of you with Intel Mobile 4 Chipsets having any problems with Video Drivers?

I'm having no luck starting Hardware Acceleration or OpenGL.

Which drivers are you using? And which Kernels & versions of OpenGL and Xorg?

Many thanks!

---

### Post by MoCC on 2010-11-03
Hi there, 

I'm also suffering from the suspend/resume bug on my x200 after upgrading from 10.04 to 10.10. 

My x200 gets VERY hot when this bug occurs and I'm quite worried about damaging my hardware. 

Anyone got any news on that? 

Cheers,
MoCC

---

### Post by Calorus on 2010-11-07
Just to ask -- Has anyone with an X200 with Intel Mobile 4 graphics managed to get OpenGL/Graphic Acceleration working with Ubuntu 10.10?

I'm worried that I may be fighting a losing battle...

---

### Post by midas13 on 2010-11-09
> **Calorus said:**
> Just to ask -- Has anyone with an X200 with Intel Mobile 4 graphics managed to get OpenGL/Graphic Acceleration working with Ubuntu 10.10?

I'm worried that I may be fighting a losing battle...

I have Inter Mobile 4 graphics; i am not sure, but it seems it works fine.  I'd like to help if I can. How can I check if Graphic Acceleration works fine? What kind of problems with graphics do you have?

ubuntu 10.10 after upgrade from 10.04, kernel: 2.6.35-22-generic

---

### Post by Calorus on 2010-11-11
> **midas13 said:**
> I have Inter Mobile 4 graphics; i am not sure, but it seems it works fine.  I'd like to help if I can. How can I check if Graphic Acceleration works fine? What kind of problems with graphics do you have?

ubuntu 10.10 after upgrade from 10.04, kernel: 2.6.35-22-generic
Thanks Midas! I can't use Compiz or Run anything that uses OpenGL, like Blender or GLXdock.

Have just tried using the Nomodeset but no avail.

I'm the same version as you .35-22 from 10.04, but I started on 9.10... It might just be that I have to reinstall - but I'm avoiding it, if I can!

Thanks again.

---

### Post by mutetella on 2010-11-29
> **midas13 said:**
> Upgraded to 10.10. And now have troubles with suspending: sometimes (not every time, may be in one of 4-5 cases) after closing notebook cover it doesn't suspend (fan is working and display is on) and crescent led is blinking. In 10.04 suspending worked fine. 
I'v tried to find some relations betweeen this problem and running software but didn't succeed. Also couldn't find any errors in logs.

Does anybody have the same problem? Where should I look at?

Hello midas13,

I had the same problem on my X200. Since I have unload the kernel modul 'tpm_tis' (driver for the Intel TPM-Chip) suspend_on_ram works fine. If you don't need TPM, you can unload this modul for all time. Otherwise you must unload it before suspend an reload after resume. A description you can found on this site (in german!):

[http://wiki.ubuntuusers.de/pm-utils#Module-vor-SUSPEND-entladen-nach-RESUME-wieder-laden](http://wiki.ubuntuusers.de/pm-utils#Module-vor-SUSPEND-entladen-nach-RESUME-wieder-laden)

From kernel 2.6.37 the problem with tpm_tis will fixed. Hopefully... ;)

Regards
mutetella

---

### Post by hermelinen on 2011-03-06
> **cpeee said:**
> I encounter exactly the same issue. I've updated my BIOS to 3.15 (x200 thinkpad) but still no joy. Unable to spot any error in the PM suspend log. Looks like a major show stopper. May consider downgrade to 10.04 if I can't do any workaround.

I had the same problem on my Lenovo x200 but I came across the solution on the Maverick Release Notes:

> When the XHCI module is loaded for USB 3.0 operation the system cannot suspend. Manually unloading XHCI will allow suspend to complete normally. To avoid future suspend problems, the workaround is to add SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module then the system can suspend normally. (522998)

See the Release notes at [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes) for more info.

---

### Post by roperp on 2011-05-29
Just checking in on this thread; I'm looking at putting Ubuntu 11.04 onto my Lenovo X200 laptop and want to make sure there aren't any major outstanding compatibility issues.

---

### Post by Mr.Carramba on 2011-10-20
I have updated to 11.10 and everything seems working just fine :)

---

### Post by ncs_one on 2011-10-30
So is there a way to make the fingerprint reader working on the Oneiric?

---

### Post by Marzata on 2012-05-01
Upgraded Lenovo ThinkPad X200 to Xubuntu 12.04 LTS (Precise Pangolin) and everything seems to be working just fine. :)

---

### Post by jpeg729 on 2012-07-12
Have installed Precise on my new x200 and it works pretty well. However I have been looking into tuning a few things.

The fan often runs much faster than it needs to. This is a known problem with a fairly simple solution.

I have also been looking into undervolting the cpu to save on battery life. Not too hard either, but if you want a lowlatency kernel you are going to have to compile it yourself.

Been looking into more battery friendly charging options as well.

I will write up on all this and post the link.

---

### Post by Marzata on 2012-07-12
> **jpeg729 said:**
> Have installed Precise on my new x200 and it works pretty well. However I have been looking into tuning a few things.

The fan often runs much faster than it needs to. This is a known problem with a fairly simple solution.

I have also been looking into undervolting the cpu to save on battery life. Not too hard either, but if you want a lowlatency kernel you are going to have to compile it yourself.

Been looking into more battery friendly charging options as well.

I will write up on all this and post the link.
How do you do all these things?

---

### Post by jpeg729 on 2012-08-31
Sorry about the delay in repling.

See here for a résumé.

[http://hackmemory.wordpress.com/2012/07/19/lenovo-x200-tuning/](http://hackmemory.wordpress.com/2012/07/19/lenovo-x200-tuning/)

It does involve installing a few extra packages. It is a pity Ubuntu doesn't detect that it is running on a lenovo laptop and install at least some of them.

---

### Post by linrunner on 2012-08-31
For advanced power management and battery functions you want to try [TLP]("http://linrunner.de/tlp") :D.

---

### Post by kto456dog on 2012-09-11
Hey guys,

I just purchased a Lenovo Thinkpad X200 as a backup/home computer for my time at University.

I've got a bit of experience with Ubuntu and i first used it when 6.10 came around, didn't really know what I was doing but it was fun netherless.

Oh wait, just realised that I've gone off one again.

What I mean to say is that I've just bought a X200 for £170 from a popular auction site, it has these specs.

Processor:- Intel Core 2 Duo L9300 (1.8GHz?)
RAM:- 3GB DDR3 RAM

How does it fair when running Ubuntu?

Will it give me a better performance than Windows? It'll mainly be used for LibreOffice and Web-Browsing when I'm on the can.

Thanks

---

### Post by jpeg729 on 2012-09-11
Mine's got a P8400 cpu, a bit more powerful. Quite frankly I start windows XP once in a blue moon. I am really happy with linux.

---

### Post by Marzata on 2012-09-11
> **kto456dog said:**
> 
Processor:- Intel Core 2 Duo L9300 (1.8GHz?)
RAM:- 3GB DDR3 RAM


It is more than enough. And I would install Xubuntu, [http://xubuntu.org/](http://xubuntu.org/), instead of Ubuntu. It is a Canonical official distro, faster, more stable and more stylish.

---

### Post by Yizi on 2013-05-29
have you guys had any issues with the mouse slowing down?

---

