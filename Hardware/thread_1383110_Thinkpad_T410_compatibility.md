---
title: "Thinkpad T410 compatibility"
date: 2010-01-16
forum: Hardware
---

### Post by lgj on 2010-01-16
Does anyone have an idea of how compatible the new Thinkpad T410 is to Ubuntu? It is based on the Intel Calpella platform and can optionally come with switchable graphics.

---

### Post by OmegaAI on 2010-01-17
It will work just fine but I am not sure about how well the Hybrid graphics work... Most, if not all IBMs have great compatibility with Linux

---

### Post by Vignesh S on 2010-01-17
Yeah, IBM's/Lenovo's work very well with Ubuntu. I've used Ubuntu on an old IBM Thinkpad R31 without any problems, and I used a LiveUSB on Lenovo Thinkpad R61's and they didn't have any dramas with Ubuntu. As OmegaAI said though, I'm not so sure how Ubuntu will like the switchable graphics, though I'm pretty certain that provided you reboot after you change the switch, then it will work with either of the graphics controllers. I can't say for sure how it works though.

---

### Post by lgj on 2010-01-17
It comes with pretty new hardware:

- Intel Core i5-520M, Intel Core i5-540M, or Intel Core i7-620M
- Intel Graphics Media Accelerator HD, it's on the same chip of the main processor
- NVIDIA NVS 3100m Graphics 256MB DDR3 (optional)

I'm not sure if these are supported yet by Linux, in particular the graphic options. I've searched for Linux drivers for them but found nothing. If the GMA HD is sufficiently similar to the 4500MHD it may work with current drivers. As for the NVS 3100M, I didn't find it on the list of supported GPU's of nVidia Linux driver.

---

### Post by monkeybiziness on 2010-01-18
I just got a T410 (Core i5) running with 9.10 this weekend.

Two gotchas:

you need to disable compiz or you will get a freeze after the login.

1. Freeze at login
sudo chmod a-x /usr/bin/compiz

source: [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

or

sudo apt-get remove compiz

2. Realtek 8172 driver (aka Thinkpad wifi agn)

follow this thread

[http://ubuntuforums.org/showthread.php?t=1339877](http://ubuntuforums.org/showthread.php?t=1339877)

this is the file: (pcrofts)

[http://ubuntuforums.org/attachment.php?attachmentid=137846&d=1259389419](http://ubuntuforums.org/attachment.php?attachmentid=137846&d=1259389419)

this is how to install it: (tubby12)

save the driver to Desktop
Open the terminal
cd Desktop
unzip \*.zip
cd rtl8192se_linux_2.6.0010.1116.2009
make
sudo su
enter password
make
make install
exit

---

### Post by lgj on 2010-01-18
Do you have switchable graphics (Intel GMA HD + nVidia Quadro NVS 3100M)?

---

### Post by monkeybiziness on 2010-01-19
> **lgj said:**
> Do you have switchable graphics (Intel GMA HD + nVidia Quadro NVS 3100M)?

No, I have the AMT graphics only. I guess I should have read the original post a little more thoroughly!

The only issue that I seem to have with the system right now is that the terminal doesn't seem to scroll on long compiles. You have to move the mouse and then the terminal starts moving again.

---

### Post by lgj on 2010-01-19
Is it supported by the xorg-intel driver, or you had to use xorg-vesa?

---

### Post by monkeybiziness on 2010-01-19
I didn't do anything special during the install. I looked int he Xorg.0.log and the intel module does load. The i810 module does not load and the vesa module also loads. I can post any logs you want me to. So far the machine is fine other than the less than stellar graphic performance. I don't do anything that is graphically critical, so it isn't bothering me at this point.

---

### Post by lgj on 2010-01-19
I found this on Intel X.org driver page

[http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)

It seems that their latest package improves support for this GPU.

---

### Post by peepingtom on 2010-01-20
There won't be any support for instant switching of GPUs, although they can be switched through the BIOS. Hopefully we'll get some tools that allow us to switch GPUs with a simple xorg restart! I love the whole idea of switchable graphics, I was too wimpy to bet on shader-based video acceleration. Now we get to hedge our bets on VDPAU and possibly VA-API

---

### Post by dcast on 2010-01-20
I just ordered a new T410 with the nVidia dedicated graphics. I'll report back here how and if they work and give some insight into the trials and tribulations of getting them working if necessary. I imagine it will be here in about two weeks.

-dcast.

---

### Post by tehfade on 2010-01-25
I too have ordered a T410. Got the Core i7, switchable graphics and "Intel Ultimate-N 6300" wireless card.

Does anyone have any info on that card? I've Googled it and searched here, but found nothing.

---

### Post by Chenzo on 2010-01-25
Intel's product brief for both the 6200 and 6300 list "Ubuntu Linux" as a supported OS next to Windows. 

[http://www.intel.com/network/connectivity/products/wireless/adapters/6200-6300/techdocs.htm](http://www.intel.com/network/connectivity/products/wireless/adapters/6200-6300/techdocs.htm)

(click on "Intel® Centrino® Ultimate-N 6300 Product Brief" to get to the pdf document)

I don't know what that means, but I'd say it's a good indication it should work well.

If anything, it's cool that a big company like Intel is name-dropping Ubuntu, hopefully other hardware manuf. will follow suit.


I'm looking into buying a T410, so I look forward to hearing how it works with Ubuntu :)

---

### Post by Chenzo on 2010-01-26
I would also be curious to know if anyone has multitouch working on the trackpad. I'm guessing this is the same or similar trackpad as the t400s, and [this post]("http://ubuntuforums.org/showthread.php?t=1264148&highlight=lenovo+t+410&page=2") seems to suggest that it hasn't been working on that model.

Does anyone have two-finger scrolling working on the t410?

---

### Post by Dr. Funkenstein on 2010-01-27
The specs of this computer look really nice..... I'm waiting for the T410s to be available.

---

### Post by tehfade on 2010-01-29
Bump for an update. I am typing this on the new laptop. A new install of Xubuntu Karmic is fine so far except for the wireless. I spent WAY too long researching the problem, but it appears that the iwlagn driver wants to load ucode of version 3 or lower and version 4 is what is included. This can be fixed just by installing linux-backports-modules-karmic. If more info is required, search for iwl6000.

---

### Post by laszlok on 2010-01-30
Is that wireless the default Thinkpad mini-pcie card, or did you upgrade it? I am hoping the intel centrino ones don't have the driver issues as I heard that they are better cards anyway.

Another thing, which graphics card did you get and have you tried video out either vga or display port? I'm sure you can clone the output for a projector pretty easy but I wonder how difficult configuring X for multi monitor support would be.

If you have the time updating [http://www.thinkwiki.org](http://www.thinkwiki.org) might be a good idea. It doesn't look like there's anything on the t410 yet. Thanks for the update!

---

### Post by lgj on 2010-01-30
tehfade: That's good news, I'm considering buying this notebook. Did you get the discrete or the integrated graphics model? Do you know if VGA-out is working? This is important to me since I often have to present slides using a projector. I've heard some complaints about the fan being constantly on and loud, do you have this problem?

---

### Post by tehfade on 2010-02-01
The wireless card is the upgraded one, the "Ultimate-N 6300". I don't know the situation with the other two, but bear in mind that they are all different cards than what you got with a "centrino" in the past. You should check around for more info on them. I did update the wireless hardware compatibility wiki off this site for my card, and I might add it to thinkwiki if I have time.

I got the model with the discrete graphics because I wanted to do a little light gaming. I don't know about the VGA-out because I haven't tried it yet. The Nvidia card is recognized, and the "Enable Restricted Driver" icon shows up, but I haven't messed with the graphics at all yet. FWIW, I don't think it'll be too difficult to get working, because Nvidia stuff is pretty well supported.

The fan is dead quiet, not loud at all, so that's not going to bother you.

I've investigated some of the other features of the laptop. The fingerprint reader does NOT work. It is newer hardware that is not supported with thinkfinger. fprint might support it, but I haven't gotten that far yet. I don't really care about that though.

The hotkeys work fine, mostly. Suspend, lock screen, brightness, thinklight, trackpad/trackpoint and wireless on/off all work, and those are all I need. I'm sure that with a little bit of hackery, the two remaining ones will work fine.  

Suspend-resume isn't working. It'll suspend fine, but freezes on resume. Haven't really looked into that yet either.

Multitouch isn't working.

---

### Post by sjakub on 2010-02-01
@tehfade:

Do you know if the display port works?

---

### Post by Xenoterranos on 2010-02-01
I ordered this same laptop, but with the "INTEL CENTRINO WIRELESS 1000" card instead of the thinkpad one, and with integrated graphics.  Mine's not coming in for another 7 days :(, but I'll post problems / fixes as well.

My question for the OP is whether or not the battery life seems to suffer under Ubuntu.  Have you had any experience with reduced batt life vs windows?

---

### Post by dcast on 2010-02-01
Glad some people are putting up their experiences. I'm also happy to hear that the 6300 card and NVS 3100m are working since I have both of those in my config. UPS says it will be here on Wednesday morning. Really looking forward to it!

---

### Post by dcast on 2010-02-05
tehfade, how did you get the Nvidia graphics working? I just installed 9.10 and it works fine on the Live-CD, but I get no X11 when it starts off the freshly installed system and flickering? Did you experience the same problems?

---

### Post by dcast on 2010-02-06
Alright, got the graphics working as well as wireless. I'm very happy with this machine, so far the only problem is that USB does not work on suspend from resume.

---

### Post by Symmetry on 2010-02-06
I got a T410 with Intel integrated graphics and I've been having a lot of trouble.  When I put in a Ubuntu 9.10 install CD I get to the first menu, but selecting either "Try Ubuntu" or "Install Ubuntu" results in a solid black screen, though I hear the login music eventually if I go with "Try Ubuntu".  

Lucid works a bit better in that I get to a dekstop, but opening any windows leads to an X freeze.  Also, installing directly works but after installing I still have the problem with not being able to open any windows without X freezing.  After using CTRL-ALT F1 to do a apt-get upgrade from a terminal things actually got worse, and X started freezing on the login screen.  I'm going to try Lucid Xubuntu now and see if that works.

---

### Post by noarc on 2010-02-06
I'm also having a lot of trouble.  I have the integrated graphics and I get a black screen either using "Try now" or "Install" using the x86-64 9.10 ubuntu install disk.  Any tips?  Does the "server"/non-graphical install disk work better?

---

### Post by Symmetry on 2010-02-06
As [this thread]("http://ubuntuforums.org/showthread.php?t=1397534&highlight=arrandale&page=2") suggests Xubuntu works right out of the box.  And since I was just planning on going to just go with using Awesome as my WM with some selected other stuff (nm-applet, some volume manager, some power manager) anyways this is really a satisfactory solution for me.

---

### Post by Symmetry on 2010-02-06
Xubuntu works great when I initially install it, but for some reason applying all the recommended updates does the same thing as with GNOME, if I try to log in after applying them X Freezes.

My recomendation: install Xubuntu but don't update for now.

---

### Post by lgj on 2010-02-07
> **Symmetry said:**
> Xubuntu works great when I initially install it, but for some reason applying all the recommended updates does the same thing as with GNOME, if I try to log in after applying them X Freezes.

My recomendation: install Xubuntu but don't update for now.
You may want to install the latest xorg-intel-video driver from source, it has improved support for Intel GMA HD according to its Changelog.

It's available at: [http://xorg.freedesktop.org//archive/individual/driver/xf86-video-intel-2.10.0.tar.bz2](http://xorg.freedesktop.org//archive/individual/driver/xf86-video-intel-2.10.0.tar.bz2)

---

### Post by dcast on 2010-02-07
Does anyone have screen brightness working? I seem to be locked at max brightness. Using 2.6.31-19. When I use fn+Home or fn+End it registers that the screen should be dimming or brightening but nothing happens. Anyone have any insight?

---

### Post by peepingtom on 2010-02-09
Same issue on the T510, the backlight controls work with the nv driver but not nVidia proprietary. I'm also having issues with suspend, will post back when I have a solution. We really should file a big report about this backlight issue, i'll probably do it later today.

Could you guys do us all a favour and pleeeeease run renouveau if you have a t410 with nvs3100m?
[http://nouveau.freedesktop.org/wiki/REnouveau](http://nouveau.freedesktop.org/wiki/REnouveau)

UNfortunately those of us with more than 256mb of video ram can't run it.

Please, do it! We have a bit of an oddball OEM card here and it sure would suck to not be represented in the nouveau open souce driver development process


The 2.6.33 kernel has better suppot in certain instances. For example, resume from suspend to ram almost works in text mode. 
For anyone with suspen issues: run the proprietary drivers. When it resumes to a corrupted screen, try alt+sysrq+k to kill VT7. You'll lose your unsaved work, but it's easier on the machine than a hard reset. Remember, always try  magic sysrq key  before just yanking the power. alt+sysrq+r e i s u b  Your filesystem will thank you ;)

---

### Post by dcast on 2010-02-09
My suspend to RAM works just fine using proprietary driversb except for the USB issue. Let us know if you have filed a bug report and post a link.

---

### Post by peepingtom on 2010-02-09
Do you t410 users have a module loaded for smbus or the thermal management chip?
sudo lshw should tell you that, devices without modules are listed as "unclaimed".

Anyone started using hard drive active protection? There's some support in tp_smapi and hdapsd

---

### Post by Gompa on 2010-02-10
a installation guide for active protection on [this page]("http://www.h-bomb.nl/active-protection-in-ubuntu-9-10")

---

### Post by peepingtom on 2010-02-11
A little bit of a workaround for the backlight when using proprietary drivers:

Switch VTs with ctrl+alt+f1, change brightness, switch back to vt7

---

### Post by peepingtom on 2010-02-11
[http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

This enables trackpoint scrolling, this version is newer than the one in Lucid universe.

---

### Post by Xenoterranos on 2010-02-12
> **Symmetry said:**
> I got a T410 with Intel integrated graphics and I've been having a lot of trouble.  When I put in a Ubuntu 9.10 install CD I get to the first menu, but selecting either "Try Ubuntu" or "Install Ubuntu" results in a solid black screen, though I hear the login music eventually if I go with "Try Ubuntu". 

I got it to install by going to F6 options and disabling everything, then going into f4 options and starting in graphics safe mode (from the first screen the cd boots to).  I don't know if disabling everything was necessary, but it worked!  I have 9.10 x86-64 installed, and right now I'm working on getting it to recognize the screen as 1440x900 (WXGA+) instead of 1280x800.
(Anyone have any idea on this one?  Editing xorg hasn't worked so far)

---

### Post by Chenzo on 2010-02-26
Just got my T410 yesterday. I decided to skip the video issues with 9.10 and just installed Lucid alpha 3. I'm happy to say that nearly everything works! I have a T410 with a i5-540m, integrated graphics.

Here is what I've tested:
-Sound
-Video
-Webcam
-Wireless (intel 6300) 
-Volume buttons, mute button
(all these work out of the box)

The only thing that I've tested that doesn't work is multitouch. I haven't yet tried to figure out why it doesn't work.

Suspend almost works. The first time I tried it failed to suspend. The second time I tried it worked, but I received a crash report saying there was a kernel problem (even though everything seemed to be ok...)

I'll report back as I figure these things out. Of course, I can't recommend installing Lucid to anyone who doesn't want to deal with the issues of an alpha release. But, for anyone that does try, I ran into this bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/500250) see reply #3 for a fix.

---

### Post by nomnex on 2010-02-27
> **Chenzo said:**
> 
Here is what I've tested:
[...]
-Volume buttons, mute button
(all these work out of the box)


Promising. What about FN keys "Brightness Up/Down"?

---

### Post by Chenzo on 2010-02-27
The following Fn+ keys work:
Lock Screen (F2)
Suspend (F4)
Radio on/off (F5)
Switch Monitor (F7)
Hibernate (F12)
Screen Brightness (Home, End)
Thinklight (PgUp)
Play/Pause, Stop, Next, Previous

The following Fn+ keys don't work:
Battery (F3)
Voip (F6)
Trackpad on/off (F8)
Zoom (Space)

Ubuntu seems to recognize Battery and Trackpad (F3 & F8) but it doesn't seem to recognize Zoom and Voip (i.e. I was not able to assign keyboard shortcuts to those keys)

I'm pretty sure the brightness key issues are only for the Nvidia graphics.

Also, Hibernate seems to work. I'll continue to use hibernate/suspend the next few days and see what happens.

---

### Post by nomnex on 2010-02-27
> **Chenzo said:**
> I'm pretty sure the brightness key issues are only for the Nvidia graphics.
Also, Hibernate seems to work. I'll continue to use hibernate/suspend the next few days and see what happens.

thanks for the answer. What's your GPU config?

peepingtom, comment #33, relates the problem with nvidia drivers and brightness. Any one with a similar config:

Thinkpad T410
GPU: NVIDIA NVS 3100M (256MB), AMT
CPU: Core i7-620M (3.33GHz, 4MBL3, 1066MHz)
Wireless: Centrino Advanced-N 6200
Source: [LenovoJP]("http://shopap.lenovo.com/SEUILibrary/controller/e/jpweb/LenovoPortal/ja_JP/catalog.workflow:category.details?current-catalog-id=3634951826AE4D3881BFFF1AC5FCD957&current-category-id=979B16C53C2847CB942DF46C41EA26A0")

Btw, what the to proper driver to install for these cards: the nvidia open source or the proprietary nvidia?
And how do you get the brightness to work correctly (loading the laptop.lenovo module?)

---

### Post by Chenzo on 2010-02-28
I have integrated intel HD graphics. I didn't do anything to get brightness to work, it worked out of the box.

---

### Post by caesium5 on 2010-03-01
Wanted to buy the T410 and it only comes with Nvidia NVS 3100M Graphics Card over here.

Reading this post and couldn't really figure out if anyone had got the Nvidia NVS 3100M Graphics Card to work properly with the propriety Nvidia driver.

Anyone can confirm if the **Nvidia NVS 3100M Graphics CARD** is working properly with the **Nvidia driver** for the T410?

---

### Post by steve0921 on 2010-03-02
caesium5, I have a T410 with nvidia NVS 3100, running karmic 9.10. I have investigated two driver options:

open source nv driver: works to the extent this driver should (eg 2D only, no desktop effects, but can change screen brightness)

proprietary nvidia driver: works (I have tried desktop effects and simple 3D games), except for the screen brightness issue. As mentioned already, you can set the screen brightness by pressing Ctrl+Alt+F1, then change brightness, then switch back with Ctrl+Alt+F7

I haven't tried the nouveau driver.

So far the only significant problem I have is with suspend, which doesn't work with either graphics driver. I haven't had time to debug this much.

Multitouch doesn't work either, but I can live without that.

---

### Post by caesium5 on 2010-03-02
steve0921, [B]

thanks[/B] for the confirmation that the T410 will generally work in Linux except :
 - screen brightness (there is a work around) and 
 - no multi-touch is fine with me.


Tried to locate the video driver from nvidia's site but seems like there is no listing of the video card, how did you manager to locate the actual card from the nvidia site?
[http://img7.imageshack.us/img7/1562/15013008.jpg](http://img7.imageshack.us/img7/1562/15013008.jpg)


What about the ethernet port, just read somewhere that there is a problem about detected as 10 and not 100. any idea if it works?

Thanks in advance for the advise.


**NOTE**:  In case you are affected, found this message at nvidia site "http://www.nvidia.com/object/unix.html"

[B]> We believe recent NVIDIA UNIX graphics drivers are affected by a recently reported fan speed issue in 195.36.08 and 195.36.03.  
Until the problem is resolved, we recommend that UNIX users revert to the 190.53 web release, or the 195.30 public beta.[/B]

---

### Post by peepingtom on 2010-03-12
Another workaround for brightness control: [http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=32](http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=32)

It causes a buzzing noise that switching in VT does not. I've asked a question about it in that thread.

---

### Post by steve0921 on 2010-03-19
peepingtom: Thanks, that screen brightness fix worked for me. I don't hear any of the buzzing noise you mentioned.

caesium5: I am just using the driver packaged by ubuntu under System->Administration->Hardware Drivers. It is version 185 and so predates the fan speed issue you mention.

As for ethernet speed, I am able to transfer faster than 10Mbps. I don't have a gigabit router handy though, so I can't confirm whether that's working.

---

### Post by kcajith on 2010-03-21
Hi,
 
Iam having trouble with T410.Can i know the detailed steps to install 9.10.
Infact i have installed Ubuntu 9.10 and iam having two issues
1) T410 screen goes blank once i hit enter in the OS boot menu...
2)Upon connecting T410 to a TV iam able to see the Ubuntu login/pwd screen and upon loggin the Ubuntu freezes/hangs..
 
Iam new to linux would need some troubleshooting steps for solving these issues
 
I have captured the edit boot menu before i login to Ubuntu in the OS options screen during start up
 
My edit boot menu looks like this
recordfail=1
if [ -n${have_grubenv} ] ; then save_env recordfail : fi
set quiet=1
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set a47c1c77-83b2-40a8-8d9e-7d7b49e7b\
e19
linux /boot/vmlinuz-2.6.31-14-generic root-UUID=a47c1c77-83b2-40a8-8\
d9e-7d7b49e7be19 ro quiet splash
initrd /boot initrd.img-2.6.31-14-generic
 
Appreciate if you could help me resolve these issues.
 
Thanks
Ajith
 
> **monkeybiziness said:**
> I just got a T410 (Core i5) running with 9.10 this weekend.
 
Two gotchas:
 
you need to disable compiz or you will get a freeze after the login.
 
1. Freeze at login
sudo chmod a-x /usr/bin/compiz
 
source: [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)
 
or
 
sudo apt-get remove compiz
 
2. Realtek 8172 driver (aka Thinkpad wifi agn)
 
follow this thread
 
[http://ubuntuforums.org/showthread.php?t=1339877](http://ubuntuforums.org/showthread.php?t=1339877)
 
this is the file: (pcrofts)
 
[http://ubuntuforums.org/attachment.php?attachmentid=137846&d=1259389419](http://ubuntuforums.org/attachment.php?attachmentid=137846&d=1259389419)
 
this is how to install it: (tubby12)
 
save the driver to Desktop
Open the terminal
cd Desktop
unzip \*.zip
cd rtl8192se_linux_2.6.0010.1116.2009
make
sudo su
enter password
make
make install
exit

---

### Post by tylerwylie on 2010-04-12
VGA works, DisplayPort supports DVI passthrough for a DVI-DP adapter.  IWL ABGN 6300 works with backport'd modules, awesome linux laptop.  I think Lucid kernel updates and Fedora/OpenSUSE releases coming out will have better and better support for this amazing piece of laptop.

---

### Post by Gorgapor on 2010-04-19
Got a T410, pretty happy with it in general; most things seem to work for me.

The one big annoyance though is the laptop numpad. Fn + numpad keys does not work at all. This seems to be a linux driver problem, as it also happens in the ctrl-alt-f1 shell.

I can press Fn+numlock and they work, but that's very slow to do.

Has anyone else gotten their numpad to work on a T410?

Found this: [http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work)
Search for numpad on that page.

---

### Post by WakkiTabakki on 2010-04-21
> **Chenzo said:**
> 
The only thing that I've tested that doesn't work is **multitouch**. I haven't yet tried to figure out why it doesn't work.

Hi all
I have a T61 and am thinking about getting a T410. I have grown very fond of the multitouch, so I'm wondering whether the touchpad on the T410 supports it...
Could someone with a T410 post the result of:
```
cat /var/log/Xorg.0.log | grep -i synaptics
```

(if the line listing the available buttons contain "double" and "tripple" there's hardware support for multitouch)


Thanks
/N

---

### Post by Gorgapor on 2010-04-23
I'm on a T410, running Lucid. Here's my output. Looks like you're out of luck on the multitouch for the moment.

```

$ cat /var/log/Xorg.0.log | grep -i synaptics
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) Synaptics touchpad driver version 1.2.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)

```

---

### Post by andygraybeal on 2010-04-27
Has anyone tried one of the port replicators?

It looks like the options on the accessories page for the 410 are:

Thinkpad port replicator with Digital Video
Thinkpad port replicator series 3
Thinkpad mini dock series 3
Thinkpad mini dock plus series 3

I'm thinking about the "mini dock series 3" because it has the ability to work with dual screens.  

Is this item even worth the bother to purchase?
I'd like to get the 410 w/ Nvidia hardware.

thanks,
-Andy

---

### Post by jback2 on 2010-05-31
So the last post was written 4 weeks ago. What does this mean? I really would like to know if the T410 works fine with Ubuntu Lucid.

The one I would like to buy is configured with:

[LIST]
[*]Intel WiFi Link 6200a/b/g/n
[*]NVIDEA NVS 3100M mit 256MB DDR3 RAM
[*]High Definition (HD) Audio, Conexant 20585
[/LIST]

Does anyone have problems with one or more of this components? Or can anyone say that this config works fine for him? I really hope you can help me. Thanks a lot!

---

### Post by shutterbc on 2010-06-03
> **jback2 said:**
> So the last post was written 4 weeks ago. What does this mean? I really would like to know if the T410 works fine with Ubuntu Lucid.

The one I would like to buy is configured with:

[LIST]
[*]Intel WiFi Link 6200a/b/g/n
[*]NVIDEA NVS 3100M mit 256MB DDR3 RAM
[*]High Definition (HD) Audio, Conexant 20585
[/LIST]

Does anyone have problems with one or more of this components? Or can anyone say that this config works fine for him? I really hope you can help me. Thanks a lot!

I just bought a T410i and am currently running 10.04 Lucid on it.  I blew away the support partitions in the process, and I don't really think I'm missing them.  My el cheapo config is as follows:

- Intel WiFi 1000
- Intel HDA audio
- Intel HD Graphics

What works for me:
- DisplayPort dual monitor config
- Audio
- 3D graphics
- Webcam
- Just about everything else, except...

What **didn't** (appeared broken before 2.6.32-22 update):
[I](When I put the machine in suspend mode (i.e. close the lid) the battery continues to drain almost as if it were on.  Within 8 hours the battery is totally drained.  So much for keeping my 9 cell battery in good condition.

It looks like this may be related to the following bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/110784)

However in the bug they're complaining that it happens in hibernate mode whereas I find the problem in suspend mode.)[/I]

**Update 6/5/2010: After a kernel update, it seems to be keeping charge now?  Great!**

Another battery quirk is that after coming back from suspend/hibernate the battery capacity is sometimes off by a factor of 10, i.e. it thinks the battery has a capacity of 1000 Wh instead of 100 Wh, so it messes up the battery gauge.

---

### Post by jback2 on 2010-06-04
Thanks for your experiences. Does anyone have a NVIDEA NVS 3100M running on Lucid? How does it work? I really would like to have compositing/compiz enabled. Does this work with Nouveau? What about proprietary drivers and KMS?

---

### Post by shutterbc on 2010-06-04
I believe ThinkWiki has your answer:

[http://www.thinkwiki.org/wiki/NVIDIA_Quadro_NVS_3100M](http://www.thinkwiki.org/wiki/NVIDIA_Quadro_NVS_3100M)

So, yes, it should work, either Nouveau or proprietary drivers.

---

### Post by BennBuntu on 2010-06-06
I'm on t410 with NVS3100M, ubuntu 10.04. Can confirm it works well in 2D with the default 'nouveau' drivers including brightness buttons. 
Nvidia drivers work too, brightness only after adding a line to xorg.conf as per thinkwiki metioned above. Maybe have to use tabs not spaces in xorg.conf?, my X11 freaked out first time I tried.

edit: Wasn't the tabs, the quotation marks I'd pasted from tutorial weren't standard quotation marks.

---

### Post by stnd on 2010-06-08
Installed 10.4 Everything worked out of the box, but since then the volume up/down buttons have stopped working and the volume control in the upper right corner task bar has disappeared.

Any ideas?

---

### Post by BennBuntu on 2010-06-15
Remember changing anything sound related? I didn't have to touch anything for sound.
Found this for resetting sound settings, sounds safe enough.

[http://blog.zloether.com/2009/11/reset-sound-settings-in-ubuntu.html]("http://blog.zloether.com/2009/11/reset-sound-settings-in-ubuntu.html")

---

### Post by tuwxyz on 2010-07-05
[B]Ubuntu 10.04
T410s type 2904[/B]

_Network_:
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
and
03:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
Work OK out of the box.

_GFX_:
01:00.0 VGA compatible controller: nVidia Corporation NVS 3100M (rev a2)
Works OK with 195.36.24-0ubuntu1~10.04 nvidia propertiary driver and this line:
Option "RegistryDwords" "EnableBrightnessControl=1"
added to device section in /etc/X11/xorg.conf

2nd, integrated Intel card **has to be disabled in BIOS** in order to avoid blank screen after the propertiary driver install.

Also I had some issues with the integrated card:
- VT1,2...6 didn't work
- when I started Ubuntu 10.04 setup from pen drive created by unetbootin, I had problem with blank screen.

_Sound_:
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
Works after 1st aptitude update && aptitude safe-upgrade.

_Finger reader_:
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Follow this to make it work:
[http://menelkir.itroll.org/2010/05/upek-biometric-touchchiptouchstrip.html](http://menelkir.itroll.org/2010/05/upek-biometric-touchchiptouchstrip.html)

_Card reader_:
05:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
I don't know yet if it works.

My laptop has no multitouch.

_WWAN_:
Bus 002 Device 003: ID 05c6:9204 Qualcomm, Inc.
Does not work. Bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099)

_SSD_ 128GB works fine.

_Webcam_:
Bus 001 Device 005: ID 17ef:480d Lenovo 
I: Bus=0003 Vendor=17ef Product=480d Version=2338
N: Name="Integrated Camera"
works OK.

_Fn-keys_:
Fn+F2 - OK (Lock)
Fn+F3 - OK (Battery info)
Fn+F4 - OK (Sleep)
Fn+F5 - OK (Wi-Fi, Bluetooth)
Fn+F6 - does not work (voip)
Fn+F7 - OK (Screen)
Fn+F8 - OK (Touchpad)
Fn+F12 - OK (Hibernate)

Fn+Home and Fn+End work after patching xorg.conf (see GFX above).

Fn+PgUp - OK

Mute - OK
Volume Up/Down - OK
Mute mic. - doesn't work

Play/Pause, Stop, Back, Forward (Fn+down, up, left, right) - OK with Rhythmbox

Fn+Space - doesn't work

I think that's it.

---

### Post by judas3000gold on 2010-07-07
fyi
if you have problems with supsend/hibernate
pull out the sd-card

it's a kernel bug already reported
i wasted quite some time as I thought it was a kernel/nvidia driver problem

---

### Post by saturnblackhole on 2010-07-09
hey, im buying one of these next week can anyone with the nvidia graphics tell me how much battery life you get with it (also say what cell battery you have)?

---

### Post by tuwxyz on 2010-08-05
Came back to report that I had some problems with my screen (blinking 4cm wide vertical line). The screen has been replaced.
The same problem occurs on my coworker's 410s. The v-line appears less frequently so we haven't decided to service it yet.

Also I've managed to run WWAN. Follow the link provided before for solution.

@saturnbalckhole:

/proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         4329 mAh
last full capacity:      4260 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 213 mAh
design capacity low:     18 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            42T4833
serial number:             894
battery type:            LION
OEM info:                Panasonic

It lasts for ~2h of browsing, watching movies and some Transport Tycoon Deluxe.

---

### Post by eitan on 2010-08-06
Thank you for the tip about configuring the bios for discrete graphics only.  I was stumped for a couple of hours wondering why I can't turn on the nvidia driver without getting a blank screen.  I didn't even realize that the T410s I just got had switchable graphics.

---

### Post by eitan on 2010-08-09
I'm discovering that I'm really habituated to having the home/end/pgup/pgdown keys mapped to fn-left/fn-right/fn-up/fn-down key combinations.  any tips on how to get that working on a t410?  

thanks in advance. / eitan

---

### Post by Waaib on 2010-08-20
I just got given a new T410 at work. It has 8gb ram for some reason (I don't know why). 

I'm considering installing ubuntu 64bit. My only reason for this is that I think it will be fast. 

Comment, slander, opinion, advice appreciated.

---

### Post by BennBuntu on 2010-08-20
Very happy with 64 bit 10.04 on my t410 with nvidia gfx. Lenovo have even made a few bios fixes like 
"Fixed an issue where system might not be resumed on non-Windows ACPI OS."
[Link]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-74269#changes")

Only had to add one line to xorg.conf to get my brightness control working, everything else works except for fingerprint reader, but haven't tried.

Cheerio, pip pip

Benn

---

### Post by functionofxy on 2010-08-25
Is it possible to put a unit that has discrete graphics into GMA mode? Is this a bios option that works?

I ask because it might be beneficial to reboot in order to save battery life.

---

### Post by cayhorstmann on 2010-09-07
One caveat about the T410 series--I haven't been able to get the touchscreen to work in Ubuntu on my T410s. I had hoped to be able to use it during lectures, but it's just been a waste of $300.

There are two problems. 

1) The quality of the pickup is very poor--if you draw something with your finger, the result is so jittery that it's useless. 

2) The n-trig driver interferes with sleep mode. You simply cannot put the laptop to sleep unless you blacklist the driver. 

Both of these have not been fixed in the Maverick beta. 

These things worked fine under Windows. I reported a couple of bugs, but there don't seem to be a lot of people with the interest or know-how to attack n-trig touchscreen issues. Otherwise, the T410s is a great machine for running Ubuntu.

---

### Post by vinni_f on 2010-09-15
.

---

### Post by JackSchnippes on 2010-09-26
just in case someone still has issues with brightness controls, I just found this:

from [http://ubuntuforums.org/showthread.php?t=1515079#post9494941](http://ubuntuforums.org/showthread.php?t=1515079#post9494941)

> **BennBuntu said:**
>  
[...] Have to add 
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```to your  /etc/X11/**xorg.conf** under **devices** section. Make sure the quotation marks  are the same as if you type them.

---

### Post by n.l.o on 2010-11-15
> **lgj said:**
> Does anyone have an idea of how compatible the new Thinkpad T410 is to Ubuntu? It is based on the Intel Calpella platform and can optionally come with switchable graphics.

I am running 10.04 on T410 without any problems (except for this kernel bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281)).


Cheers

---

### Post by lazyacre on 2011-02-21
I am running a T401 and X210i both work great !!

---

### Post by Meow27 on 2011-03-26
im using a t410 on 10.10. 

so far, almost everything seems to be in perfect order. 


It would be nice if the middle button would scroll instead of being a mouse button#3. but im sure ill figure out how to do that. i found a link about it . Hopefully it works ^^ [--Link--]("http://www.eastwoodzhao.com/thinkpad-middle-button-scroll-ubuntu-linux-10-04-lucid-lynx/") [edit-- It worked!]

Also the mute mic button doesn't light up when pressed. since this is a software button, and since it works in windows, im sure this is a linux issue (which doesnt matter to me at the moement anyway)

Now if someone can tell me how i can switch between my nvidia card and my intel card, I'd appreciate it, optimus wont work in linux but i can still manually switch the cards before booting. 
From what I understand, installing the nvidia driver requires removing the intel drivers, which is something i cant afford to do :/

I'm also running the machine on an SSD. So far its fantastic!

---

### Post by bjordan1979 on 2011-03-29
Glad to hear most things are working well. I'm in the market for a new laptop and strongly considering a T410. Most likely I'll be running 10.04 (I generally stick to LTS releases for my main install).

Where any of you ever able to get the multitouch support working? I'm so used to using 2 fingers to scroll with my current laptop (an old Averatec running 10.04) that I'd really miss this feature.

Edit: My apologies. I searched before and have no idea how I didn't find [this thread]("http://ubuntuforums.org/showthread.php?t=1603657&highlight=t410") about two finger scrolling.

Last thing. How is this laptop on heat? My current laptop runs extremely hot because it's mostly vented through the bottom so when I set it in my lap it can't "breathe". After a while the heat caused issues. I saw one review stating the bottom of the T410 got hot.

---

### Post by Meow27 on 2011-04-01
> **bjordan1979 said:**
> Glad to hear most things are working well. I'm in the market for a new laptop and strongly considering a T410. Most likely I'll be running 10.04 (I generally stick to LTS releases for my main install).

Where any of you ever able to get the multitouch support working? I'm so used to using 2 fingers to scroll with my current laptop (an old Averatec running 10.04) that I'd really miss this feature.

Edit: My apologies. I searched before and have no idea how I didn't find [this thread]("http://ubuntuforums.org/showthread.php?t=1603657&highlight=t410") about two finger scrolling.

Last thing. How is this laptop on heat? My current laptop runs extremely hot because it's mostly vented through the bottom so when I set it in my lap it can't "breathe". After a while the heat caused issues. I saw one review stating the bottom of the T410 got hot.
right now since i cant figure out how to get the driver for nvidia to work, WITHOUT killing the intel driver, im sticking to the intel driver

the t410 has two vents (same fan) so it generally doesn't heat up if one side is choked, it will however increase the RPM speed of the fan.

another thing to note, though i have no evidence to back this up, i suspect that the latest models are running on the i5-560m CPU. i'd avoid the i7's because those are the older models. compare the two available CPUs on google and check for yourself :)  (yes there are multiple "versions" of the t410)

i was never spoiled with multi-touch, so i never bothered to fiddle with it :P

I'd stick with 10.10. It has better intel gfx driver support.

---

### Post by beew on 2011-04-01
> **Meow27 said:**
> right now since i cant figure out how to get the driver for nvidia to work, WITHOUT killing the intel driver, im sticking to the intel driver


I don't think you need to "kill" the Intel driver, is it open source so it is in the kernel anyway. If I understand correctly through the BIOS you select only one card, if the Nvidia card is being activated then the Intel driver would not be used. But if you want to use the Intel card you would have to uninstall the Nvidia driver.

Am I missing something?

Just out of curiosity, the Nvidia card is the expensive, high performance one, why would you be sticking to the Intel card? you can get a much cheaper laptop with an Intel card. :)

---

### Post by Meow27 on 2011-04-01
> **beew said:**
> I don't think you need to "kill" the Intel driver, is it open source so it is in the kernel anyway. If I understand correctly through the BIOS you select only one card, if the Nvidia card is being activated then the Intel driver would not be used. But if you want to use the Intel card you would have to uninstall the Nvidia driver.

Am I missing something?

Just out of curiosity, the Nvidia card is the expensive, high performance one, why would you be sticking to the Intel card? you can get a much cheaper laptop with an Intel card. :)

heat and power consumption. Since optimus (a technology that uses the nvidia card only under heavy load) doesn't work on linux, i have to switch with either the nvidia card or the linux card.

When I'm on the go. i cant afford to lose battery life and generate too much heat. when at home, that doesn't matter, so i'd have it on at home. on windows optimus works, and switching graphics manually isnt a problem either. only on linux it is :(

i posted a thread about my problem here
[http://ubuntuforums.org/showthread.php?t=1719501](http://ubuntuforums.org/showthread.php?t=1719501)

---

### Post by jzimmer on 2011-05-10
I've just gotten a T410 as a work computer and I wonder whether anyone has a working Fan control daemon/app for Ubuntu 10.04.
I've tried the suggestions of several old posts (2008, 2009), but they all don't seem to work properly.

Thanks in  advance 
newbie alarm!

---

### Post by cpbl on 2011-05-10
Thinkfan works very nicely for me on my T410s.
apt-get install thinkfan
and see the instructions at [http://sourceforge.net/projects/thinkfan/](http://sourceforge.net/projects/thinkfan/)

---

### Post by deesugar on 2011-09-15
I am having a screen freeze issue with Wubi on a Lenovo T410s. happens once a day (at least). The last time it happend I looked at the Sys log and found this:

Sep 15 14:55:48 ubuntu kernel: [19037.067533] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung Sep 15 14:55:48 ubuntu kernel: [19037.069578] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 4209795 at 4209786, next 4209796)Sep 15 14:55:49 ubuntu kernel: [19038.771207] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hungSep 15 14:55:49 ubuntu kernel: [19038.771497] [drm:i915_reset] *ERROR* GPU hanging too fast, declaring wedged!Sep 15 14:55:49 ubuntu kernel: [19038.771502] [drm:i915_reset] *ERROR* Failed to reset chip.Sep 15 14:56:37 ubuntu pulseaudio[1413]: module-alsa-card.c: Failed to find a working profile.Sep 15 14:56:37 ubuntu pulseaudio[1413]: module.c: Failed to load module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.Sep 15 14:56:46 ubuntu acpid: client 1215[0:0] has disconnected



lspci Output:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 



Anyone have an idea on this?

---

