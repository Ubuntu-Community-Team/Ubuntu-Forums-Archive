---
title: "[deb] xserver-xorg-video-intel_2.1.0-1ubuntu1_i386 feisty backport (965GM X3100 fix)"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by Voland666 on 2007-07-07
This is the last (as of today) xf86-video-intel module released by Intel, backported by me from 7.10 Gutsy Gibbon to 7.04 Feisty Fawn. It is built against the X server in the official repositories, so if you're experiencing issues on your graphic adapter (most likely the X3100 included in the i965GM chipset) it's just a matter of download & install.

It should fix the following bugs affecting the 1.9.94-1ubuntu3 release:
 - Fuzzy screen on some panels.
 - 24 bpp configuration resulting in 16 bpp and leading to nasty color bands in place of smooth gradients.

Sadly some are still here
 - Can't play video with XV extension when used together with a compositing manager such as compiz or xcompmgr. It's necessary to fall back to X11 to fix totem-gstreamer, totem-xine, gxine and mplayer.
 - Setting gamma in the relevant "Monitor" section of xorg.conf is acknowledged in X.log but has no effect. It's possible to use xgamma as a workaround (e.g. placing a small script in /etc/X11/Xsession.d/).

The following may depend on some problem in Xorg 7.2 which has already been fixed in the upcoming 7.3, since I did not notice them in Gutsy
 - Compiz (both Feisty's official 0.3 and CompizFusion 0.5 GIT) freezes the machine as soon as you try its nicer effects (such as wobbly windows and minimize-maximize effects provided by the animation plugin). Disabling those plugins results in a less impressive desktop, but allows for a good stability while mantaining transparencies, shadows and avant-window-navigator for those who use it.
 - Incorrect DPI computation leading to small characters on high res screens. Use gnome-font-properties to specify the correct value.
 - EXA acceleration not availlable.

HOWTO:
 - Download the attached package
 - Install it by means of gdebi: just double-click it
 - If you are already using an older version of xserver-xorg-video-intel, just restart GDM or reboot the system. Otherwise, you need before to change the "Driver" option under the "Device" section of /etc/X11/xorg.conf to "intel". An example xorg.conf is included for reference (DO NOT COPY IT OVER YOURS!).
 - Optional: To get faithful colors, include the appropriate "Gamma" option in section "Monitor".  Refer to the attached files.
 - Optional: If you use compiz or xcompmgr, you may need to change the default video out plugin for your multimedia framework, or you'll likely get black screens or nasty player crashes. For gstreamer, just use gstreamer-properties.
 - Optional: For compiz not to freeze the machine, disabling the (nicest) plugins may also be needed. For the 0.3 version included in Feisty, open gconf-editor and put in the /apps/compiz/general/allscreens/options/active_plugins the appropriate values. For me the following list is working fine: "gconf,svg,png,decoration,annotate,screenshot,move,resize,place".

NOTE:
 - Some files in this package, those implementing the Xv Motion Compensation function in particular, conflict with those installed by the legacy xf86-video-i810 driver. If you have the xserver-xorg-video-i810 package, you will have to remove it BEFORE installing xserver-xorg-video-intel.
Do that only if your graphic adapter suffers from lack of support by the legacy driver (most likely, if you have an i965GM/X3100 chipset) 
Editing /etc/X11/xorg.conf may be needed.

OFFTOPIC:
Is there anybody from Kyiv, Ukraine? I'm going there for three months and I'm looking for a job...

Hope this helps. It works as described on my Dell Latitude D630. Have fun.
luigi

KEYWORDS
Intel intel-video xserver-xorg-video-intel xf86-video-intel 965 965GM i965 i965GM X3100 Santa Rosa SantaRosa CentrinoDuo Centrino Duo Dell Latitude D630

---

### Post by biogon on 2007-07-07
Woot... smooth 24bit images now.

Thank you!

-j

---

### Post by mwiertz on 2007-07-08
Superb job!

Thanks a lot!

---

### Post by Atomic Dog on 2007-07-09
I'm gonna bump this up as I know this is helpful to intel vid owners.

---

### Post by jvalenzuela on 2007-07-09
Thanks a lot Voland666 !!!

I've probed a lot of active_pluggins combination and all of them hangs the computer (switcher, minimize, scale, clone, etc). Now, I suppose we must wait till these runs correctly.

---

### Post by Sanny78 on 2007-07-09
Great job! Thank you very much!

This works like a charm on my Dell D830!!

---

### Post by viralata00 on 2007-07-09
(Reading database ... 152261 files and directories currently installed.)
Unpacking xserver-xorg-video-intel (from .../xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb) ...
dpkg: error processing Desktop/xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb (--install):
 trying to overwrite `/usr/lib/libI810XvMC.so.1.0.0', which is also in package xserver-xorg-video-i810
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 Desktop/xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb
 got this error? any sugestion?

---

### Post by talava on 2007-07-09
The patch worked, but it didn't bring anything new to my Acer 6292 compared to the older intel-xorg-driver. 3d still not working and even screensavers crash the system. (video working though)

Nice job making installing the new driver so effortless tough. The old one took me half an hour to install and perfect.

---

### Post by WHiZZi on 2007-07-09
Wow, Compiz works on my Dell D830 with the 965GM videocard.. Only Google Earth still crashes the whole system :)

Thanks for this deb!

---

### Post by Voland666 on 2007-07-09
To avoid conflicts with the legacy xserver-xorg-video-i810, you will have to remove it *before* installing the new xserver-xorg-video-intel, which replaces and supersedes it completely. But I suggest doing so only if you are not satisfied with the current graphics performance, stability or support (most likely, if you have a newer, not supported chipset such as i965GM/X3100).
Notice that, in order for X to start correctly, a change in /etc/X11/xorg.conf may be needed:

# sudo gedit /etc/X11/xorg.conf
```

Section "Device"
        ...
        Driver          "i810"
        ...
EndSection

```

must become:

```

Section "Device"
        ...
        Driver          "intel"
        ...
EndSection

```

Again, if your configuration is not broken, you'd better NOT fix it...

---

### Post by Voland666 on 2007-07-09
Most likely, you now got a 24 bit - true color video mode instead of a 16 bit one. As for 3D crashes, I think they are due to the Xorg or Mesa versions in Feisty or a wrong interaction of them with the driver. In fact, nearly everything works properly in Gutsy right now with this very same driver. Sadly, I don't think we'll see such kind of updates in Feisty soon, if ever...

---

### Post by WHiZZi on 2007-07-10
Hmm. Compiz still runs pretty unstable. It crashes a lot :(

When I switch task (Alt-tab) it crashes most of the time. Also un-minimize seems to hang the system. I just disabled compiz because it's not workable this way. I disabled the items as described in the topicstart but that doesn't work well.

But, the good side is that it runs at 24bit color and the fuzzyness on my Dell D830 is gone. Whoohoo

EDIT: Hmm.. It seemed that Compiz put all the items back in the gconf-editor. After deleting them there again it's stable

---

### Post by torekiki on 2007-07-10
I use 1400x900, but with this driver my screen is blur...:(

---

### Post by davidmorawski on 2007-07-10
Does this work for Ubuntu 64-bit? I tried to force the install with dpkg -i --force-architecture, but that seemed to break my display until I reinstalled the previous version of xserver-xorg-video-intel with apt-get.

I'm running the 64-bit version of Feisty on my Core 2 Duo Dell Latitude D630.

Thanks,

Dave

---

### Post by gcarrillo on 2007-07-10
Can you provide instructions as to how to create the .deb?  I have a Core 2 Duo so the install complains that the .deb is for the wrong architecture (i386)...this request pertains to the above request; support for 64bit architectures.  I have a Dell Latitude D830, as did a user above,  but I guess I installed 64 bit version of Ubuntu...

This would be greatly appreciated!

---

### Post by ifinishwhatistar on 2007-07-11
Any temporary fixes for us 64-bit users?

---

### Post by JoSch on 2007-07-14
I backported the driver to Feisty 64Bit: [http://ubuntuforums.org/showthread.php?t=500668](http://ubuntuforums.org/showthread.php?t=500668)
Enjoy!

---

### Post by gcarrillo on 2007-07-14
Thank you, JoSch!  This resolved the color banding issue ;)

---

### Post by gcarrillo on 2007-07-15
A quick note:  I actually still had a small amount of banding even after following these steps because I used Voland´s gamma settings on a D830.  His link regarding gamma was very useful, but I took out all the gamma mods made to xorg.conf and 95x11-xgamma, and gradients now look completely smooth.

---

### Post by tokker73 on 2007-07-16
Referring to the instructions in the original post (download attached packages and double click): 

Can somebody tell me how I can do this from the command prompt, because my system closes GDM and leaves me with only a command prompt (I explained my problem in the post below but so far no useful answers...)

[URL="http://ubuntuforums.org/showthread.php?t=500696"]

Thanks in advance

---

### Post by JoSch on 2007-07-16
Had the same problem and also did everything Voland listed from the command line.
Because you have to be logged in to download attachments just use wget with cookie managment (complicated) or a command line browser like lynx. See my answer on your original thread.

---

### Post by tokker73 on 2007-07-17
I managed to do install the package the command line (I removed the i810 package first). Everything seemed to be OK. I started dpkg reconfigure... and changed the driver to intel.I rebooted and now, instead of an alert, I just get a black screen. ALT F2 doesn't give me back my command prompt. The only thing I can do is boot in "repair" mode to get the command prompt.
Does anybody have any idea what my problem is (Besides the fact that I'm an ignorant fool, hahaha)?

Thanks

---

### Post by tokker73 on 2007-07-17
Correction of the previous post: I managed _to_ install the package **using only **the command line (as I don't get any desktop)

---

### Post by JoSch on 2007-07-17
Maybe you did something wrong within dpkg-reconfigure?
Maybe you set the amount of memory or did a wrong configuration of your screen?
You only have to set the driver to intel - the rest can stay default.
It is also possible to grab a fresh xorg.conf and change the device section.

---

### Post by tokker73 on 2007-07-17
I used the command sudo dpkg-reconfigure -phigh xserver-xorg to reset the xorg.conf file. Is that the right way to do it. Then the reconfiguring tool opens but I just close it pressing Esc a few times. Then I get into the config file by typing sudo nano /etc/X11/xorg.config. When this opens, I change "vesa" to "intel" and save. In the command propmpt I type sudo reboot.

When it reboots, I don't get the black screen anymore, but again the original error message

The log file shows (I just give you the lines that I think might mean something to you):

(WW) intel: No matching Device section for instance (Bus ID PCI:0:2:1) found
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory
Fatal server error: AddScreen/ScreenInit failed for driver 0

Does that clarify things? Thanks.

---

### Post by JoSch on 2007-07-18
just type:```
sudo dpkg-reconfigure xser-xorg
```
dpkg-reconfigure will only write to your xorg.conf if you get through all steps! At least I thought it would be so...
Now to you errors...
(WW) intel: No matching Device section for instance (Bus ID PCI:0:2:1) found
=>just let dpkg-reconfigure xserver-xorg.conf guess where the card is installed and accept this value - maybe you entered sth. wrong in the past?

(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
=> I also do not have /dev/agpgart so I dont think this is critical - it has to be connected to another error. in ubuntu feisty agpgart ist automatically loaded as a module - to confirm this try```
lsmod | grep agp
```

(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
=> this is what I mentioned a few posts earlier: do not give any value if it asks you for video ram - not even zero! leave this entry blank!

And again: do not cancel dpkg-reconfigure in the middle - do the complete configuration!

---

### Post by tokker73 on 2007-07-18
JoSch, thanks again for your explanations.

However, everything you suggest, I already did right after I installed the package: I went through the whole reconfiguration proces until I ended up at my command line, and I only changed the driver from vesa to intel and besides that I kept everything default where possible (on a few occasions you have to make a choice - about the mouse, for example.) The only extra choice I remember making is choosing the resolution of my laptop (I added the resolution that I found in the sales folder). I did not set any value for the video memory nor did I choose that bus ID myself.

If nothing else works, would it help to upgrade to gutsy or install everything again using the 64bit version? (since I have a core2duo processor...)

---

### Post by Syke on 2007-07-18
I've tried numerous hacks/patches/64-bit/etc. to get my x3100 to work in Feisty. Nothing worked fully. Except Gutsy. Gutsy works great on the x3100. But I never got Gutsy WiFi working. So at this point it is either 3D working or WiFi working, but not both.

---

### Post by JoSch on 2007-07-18
Hrm... this seems to be a difficult problem...
I suspect that maybe you accidentally messed up some configuration at some step?
Gutsy will also not work from the start - you will have to make a sudo apt-get update, sudo apt-get upgrade after installation to get the latest intel driver from the gutsy repositories. And then again choose the intel driver in xorg.conf.
I would try this options:
Reinstall feisty with the alternate cd and edit xorg.conf by ONLY changing the driver from vesa to intel after you downloaded volands driver with lynx and installed it with dpkg. I would not recommend to use dpkg-reconfigure xserver-xorg because one could mess sth. up. I think it's easier to edit  xorg.conf because then you know what you've changed.
So if you did this - and this time you can be sure your xorg.conf is clean because you manually edited it - and it is STILL not working I would try gutsy.
After downloading gutsy tribe 2 alternate and installing it you do not have to go through the step of downloading a special driver. You'll just have to upgrade your system with```
sudo apt-get update
sudo apt-get upgrade
```and then editing xorg.conf manually as above.
If you manage to do this with lynx maybe it would be useful to post your current xorg.conf here so you can compare them (with diff) to the one that will be installed later and check if there were differences.

---

### Post by JoSch on 2007-07-18
> **Syke said:**
> I've tried numerous hacks/patches/64-bit/etc. to get my x3100 to work in Feisty. Nothing worked fully. Except Gutsy. Gutsy works great on the x3100. But I never got Gutsy WiFi working. So at this point it is either 3D working or WiFi working, but not both.

I can confirm that the X3100 graphics work like a charm in gutsy but with volands backported driver for i386 and mine for 64bit I also had no problems with feisty.
Just open up a new thread with your wifi problem - if it worked in feisty there is no way it shouldn't in gutsy. You can PM me the link to your thread I would be glad to help.

EDIT: you mentioned 3D - do you mean compositing features or 3D acceleration (shown with glxinfo)

---

### Post by Syke on 2007-07-18
I only had a few minutes to play with it, but I was scrolling through the screensavers, going ooh, ahh, it's working, when BAM, lockup, when I switched to Euphoria or so. Going to play with it some more tomorrow.

---

### Post by tokker73 on 2007-07-18
JoSch, before I follow your suggestion and start again I would like to check 1 thing/ ask 1 question. Would it be possible that the bus which xorg suggests is not the right one?
As you saw in the log file I posted before it is mentioning the missing device on bus 0:2:1. However the config file mentions bus 0:2:0. When I try to make them the same by changing the config file to 0:2:1 and I restart the laptop, the error log wilt talk about bus 0:2:0. They never talk about the same bus. (I've seen this problem in another thread somewhere. I don't remember where but I do remember that it wasn't solved there...)

And what happens if I change the bus to 0:0:0?
I get two lines in the log file:
(WW) intel: No matching Device section for instance (Bus ID PCI:0:2:0) found
(WW) intel: No matching Device section for instance (Bus ID PCI:0:2:1) found

I tried lspci to find out on which bus the 965GM chip is located but I only get to see the last screen without being able to scroll to the top of the list which is not on the screen. How can I have it shown page by page so I can sort of scroll? Something like /w MS-DOS used to have, I mean.

So I would like to try 1 more thing: manually changing the bus number. If that doesn't work i'll start all over again...

Thanks again...

---

### Post by JoSch on 2007-07-18
A also noticed your bus id. Mine is 0:2:0 and since we both have the same chipset I assume it should be the same on your notebook.

You have different options to review ANY console output:
1. simply type your command, press enter and croll up and down with SHIFT-PAGEUP/DOWN

2. pipe your command to another! piping is a method in unix that allows to give the output of one command directly to another so that you can for example pipe your lspci command to a viewer that pages and lets you scroll with UP/DOWN or to to a program that searches your output for certain keywords and prints those lines

2.1. for viewing lspci with less:```
lspci | less
``` all output of lspci will be piped to less in which you can scroll with UP/DOWN or  PAGEUP/DOWN

2.2. for extracting only those lines you want to see pipe the lspci output to grep. grep allows you to search everything that is passed to it and only output the appropriate lines.```
lspci | grep VGA
``` if it says 00:02.0 as on my Dell D830 your card is located at 0:2:0

---

### Post by tokker73 on 2007-07-19
I checked the bus number with lspci

It says

00:02:0 VGA compatible controller: Intel corporation Mobile Integrated Graphics controller (rev 03)
00:02:1 Display controller: Intel corporation Mobile Integrated Graphics controller (rev 03)

Is this why there seem to be different references to two different bus numbers?

The question is of course: What to do about this? Does this mean I need to have 2 bus numbers assigned? And how do I do this? Add a set of lines in the config file?

Thanks again.

---

### Post by JoSch on 2007-07-19
No.
The only line important is the one with "VGA compatible controller".
I also checked on my laptop and it gave exaclty the same two lines instead that I have a (rev 0c)
But from my xorg.conf and dpkg-reconfigure xserver-xorg auto detection I can tell you that your Bus id is definitely 0:2:0 - as I said: we both have the same chipset/graphics.
Maybe try to manually change the bus to 0:2:0 in xorg.conf or dpkg-reconfigure xserver-xorg - even if it says otherwise. From your lspci output I'm sure that 0:2:0 is your correct bus id.

---

### Post by Antioch on 2007-07-19
Josch / Voland: Did you try the new drivers with the new X.org 7.3? I'm curious if they are stable and you can use the new graphical effects. I'm looking to buy a laptop with the X3100 graphics chip but I first want to make sure it can handle Compiz-Fusion without breaking a sweat. So, if you could please give some feedback as to the X3100's ability to handle CompizFusion in Gusty (read: with all the newest drivers/Xorg/kernel) I'd greatly appreciate it. Checking the X3100's power with Compiz is the last item on my checklist before I buy my new machine.

Again, I appreciate it a lot! :KS

---

### Post by JoSch on 2007-07-19
This thread is about X3100 with feisty NOT with gutsy!
I run gutsy on another machine with intel GMA915 graphics. Compiz Fusion is VERY UNSTABLE there! I just recommend you this thread: [http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)
You seem not to realize that comiz fusion/beryl is NOT for a productive environment. I tested it for years on different intel, nvidia and amd chips but is was never as rock stable as I need it to be.
Now with gutsy + X3100 there is another problem: the intel driver also isn't very mature!!
There is a reason for it not to be in the official feisty repositories and that voland and I had to backport it from gutsy - atm the only thing you can do with compiz + X3100 is testing and sending bug reports. This is what I do.
I removed gutsy from my laptop (another box then mentioned above) because it was to unstable and installed feisty. Because I wanted to use the intel X3100 driver I backported it.
So to make sure I write no wrong info here I just fired up compiz on my feisty install with my backported 64bit driver.
Freeze - Reboot.

EDIT: Okay - now can just anybody tell me how to deactivate compiz from the command line? It freezes before I can access the desktop effects menu...
EDIT2: I started some screensaver from the commandline and they also crash X. But I can confirm, that I can run starcraft flawlessly! :-D
EDIT3: Just tested Diablo II and it also had no problems - I'm perfectly happy now!

---

### Post by Antioch on 2007-07-19
Yes, I realize it's unstable and I'm sorry this is about Fiesty, not Gusty. I would just like to know if, when you were trying Compiz, was the X3100 good enough to render everything perfectly - without lag?

I know that Compiz Fusion is in development and that the Intel drivers are immature - but putting those aside, is the X3100 hardware enough to handle Compiz completely? Compiz and driver stability and maturity will come with time.

Thanks. =)

---

### Post by JoSch on 2007-07-19
The X3100 is **definitely** enough for compositing features!
As I mentioned even my Intel GMA915 handles it without hassle - and this card is more then three years old I think!
You are also on the best side with using intel hardware because they are the only graphics cards atm that have real GPL drivers. This means, that in the (near) feature you will have the very least problems with intel hardware if you want to use comiz compared to proprietary ati or nvidia drivers  hardware.

---

### Post by tokker73 on 2007-07-21
JoSch, I did what you suggested. Install Feisty again with alternate CD, then download the backported driver package with lynx and install it (after removing the i810 driver), and then changing only from vesa to intel through the xorg.conf file. All this without any result. Still the same problem.

The good news however is that i downloaded the alternate gutsy cd and that after installing, updating and upgrading, it finally works. The quality of the screen doesn't seem perfect yet but is good enough for now. The standard brown wallpaper seems to have some kind of ripples in it, the different shades of brown don't seem to blend in with each other smoothly, it kinda looks like a treetrunk with the different age bands...). Any idea how to improve this, or this wallpaper supposed to be like that?

Also I am not able to download all the upgrades. Is that normal?

---

### Post by fd9_ on 2007-07-21
Are these drivers stable? (Forget about Desktop Effects, I'm talking about regular 3D games).

---

### Post by JoSch on 2007-07-23
Only played Starcraft and Diablo II and they never crashed. Say some OSS Games you play. I can test them on my laptop.

@tokker: I'm surprised it only works in Gutsy for you! Be careful with gutsy. I experienced a lot of crashing - more than in the feisty alphas. What is it that you cannot upgrade?

---

### Post by Lek130 on 2007-07-24
Hi there! 

I am using a D630 with the same intel  chipset on feisty. I upgraded my drive [http://users.piuha.net/martti/comp/d630/](http://users.piuha.net/martti/comp/d630/) and followed the instructions there and have to say, that it wokrs great.

THANKS FOR ALL THE FISH --- AHEM WORK. Great stuff.

In effect it worked so well - with the latest mesa/etc changes via apt-get update/upgrade, that I can attach a second Monitor and work in CLONE MODE. Why do I want clone mode, if its not a project???

Hmmm ... No I really like to work on an extended mode. Based on your setup how can I? I tried lots of stuff (searched a lot), but it never worked somehow. :(  The good thing, I really know now how to fix xorg.conf on command line (in effect, nowadays I just cp a backup file and instantly restart gdm :) ). 

I tried displayconfig-gtk which actually is really COOL. It allows easily to manage multiple monitors and changes drivers accordingly. Not that it works, but its supposed to with Xorg7.3 - that's why I am interested in it. I really dont care about Compiz (works well with feisty/latest driver). 

... but I really like this 2nd screen to work in extended mode and "plug'n'play" projector working. 

Any suggestions?

----

Why? My company actually uses WXP Images. Being CTO I changed  that for me and installed Feisty with Virtualbox (which has the image - just in case). This is so cool and I am so much more productive with 4 virtual desktops running at the same speed one lousy WXP Laptop did before ... Of course, it I travel around it looks better if it all works :) and projecting and 2nd monitors is a big thing here. 

THX

---

### Post by Syke on 2007-07-24
> **JoSch said:**
> Only played Starcraft and Diablo II and they never crashed. Say some OSS Games you play. I can test them on my laptop.
Starcraft and D2 are strictly 2-D games.

Try Nexuiz or OpenArena (both in the feisty repos).

---

### Post by JoSch on 2007-07-24
They are 2D Games but the require hardware acceleration - you see this when you try to play this games with a driver that gives you "hardware acceleration: none" in glxinfo - it will be choppy like hell.

Just tried nexuiz: freeze...

---

### Post by victorgreen on 2007-07-30
well it works, but my brightness fn end and fn home controls make the screen flicker badly when pressed and no longer seemed to be linked to the gnome brightness applet. the bightness can be all the way down and the applet shows it being maxed at 100%. 

I guess its not that big of a deal as they both still will control the brightness... 

Google Earth still crashes the X so badly it cant seem to revert without a hard restart. Has anyone gotten it to work yet? Im using a Thinkpad X61.

---

### Post by WHiZZi on 2007-07-30
For those who would like to experiment:

I installed xserver, libc6, the intel drivers AND Beryl from Gutsy on Feisty and now everything is working! 

I have all 3D effects on my Dell D830 (with the X3100 videocard), even the rotating cube including transparency :D

I did the following:
Editted the /etc/apt/sources.list and added:
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy main restricted universe multiverse


Then:
(Ignore the updates!)
> 
sudo apt-get update
sudo aptitude install xserver-xorg-video-intel xserver-xorg libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils mesa libdrm2 libxdamage libgl1-mesa  libglu1-mesa mesa-utils x11proto-print xorg-server xnest xprint xserver-xorg-video-intel beryl beryl-manager 


Then I removed the 2 lines I added from /etc/apt/sources.list and another
> 
apt-get update


Then, I made sure I set the default color depth on 16bit by changing the line:
> 
DefaultDepth 24
 to 
> 
DefaultDepth 16

under the Screen-section in /etc/X11/xorg.conf

Next I added the following lines to the bottom of the xorg.conf
> 
Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection


and changing the lines in the Device-section to
> 
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "monitor-TV" "TVOutput"
        Option  "CacheLines"    "32768"
        Option  "DRI"   "true"
        Option  "PageFlip"      "true"
        Option  "TripleBuffer"  "true"


After I rebooted, my screen was perfectly fine and I could start Beryl (and the 3D Effects too). Also Google Earth works without problems.

I've got the most of this from [this topic](http://ubuntuforums.org/showthread.php?t=506744&highlight=d830) by fd9_ and added a few small bugs.

Again, this is only for those who'd like to experiment with Feisty. I have it running on my laptop from work and the laptop worked for a few days now without problems!

---

### Post by JoSch on 2007-07-31
You install the same driver versions as they are backported by voland and me but you get no freezes...
Can anyone try out Beryl - not compiz - with our backported driver?
Can someone confirm if 3D Games work with WHiZZi's way?
Sadly I will have to use 16bit color so I will stick to my backport for now.

---

### Post by Lek130 on 2007-07-31
hey! The funny thing is, that compiz and beryl work pretty well for me. Though I still don't get my 2nd monitor right ;-) 

though some of the special effect with beryl are not working the same way to other setups. last night i setup feisty on my (2 yrs older) HP Desktop with nvidia. that worked very well. 3d cube workplace switch and all the effects. its a bit to much, but ok.

So using beryl make the interface looking nicer ... 

>> I had to rebuild my laptop painfully last week. I installed 2-3 updates via root console vs user+sudo. THis screwed up access rights badly and to many so that I could fix it. Now I am using the server-kernel, which is somewhat different :(( vs the generic kernel.

---

### Post by WHiZZi on 2007-07-31
> **JoSch said:**
> You install the same driver versions as they are backported by voland and me but you get no freezes...
Can anyone try out Beryl - not compiz - with our backported driver?
Can someone confirm if 3D Games work with WHiZZi's way?
Sadly I will have to use 16bit color so I will stick to my backport for now.

Well, Supertuxkart seems to work. I don't know about any other games, but OpenGL works.

And I don't see any difference between 24bit or 16bit color. I think that the driver automaticly chooses the color depth and ignores the xorg.conf for that. All color-fades are correct

---

### Post by Lek130 on 2007-08-01
update

i moved to the generic kernel in feisty 704. Using Beryl now and all effects work on the 965gm. very neat. Cube, transparency, etc, etc. 

not sure i keep it, because its a bit over the top for me.

p.s. i dont want to annoy you guys, but if anyone has suggestions for configuring xorg.conf for two monitors (expanding not cloning mode). I would appreciate. When I start up I am in clone mode. Where the Monitor / LCD has the correct setup - 1280x1024 @60 ... However for the LCD the max is 1280x800 (or so). The the bottom 10% is cut own in clone mode on the LCD. 

So what would be needed is to have two monitor setups in xorg.conf which allows for xorg to understand the different resolutions required ... It appears this has been resolved in Gutsy (displayconfig-gtk) but I have a company laptop and dont dare to upgrade yet. 

Any suggestions on xorg.conf

Any stability views on gutsy?

Thanks.

---

### Post by markusfarkus on 2007-08-02
What if I can' t even get the machine to boot off of the CD.  I haven't installed Ubuntu just yet.  I have a Dell Latitude D630

---

### Post by markusfarkus on 2007-08-02
My Graphics card is the offending Intel 965

Thanks

---

### Post by jsage on 2007-08-02
> **markusfarkus said:**
> What if I can' t even get the machine to boot off of the CD.  I haven't installed Ubuntu just yet.  I have a Dell Latitude D630

markus, to install Ubuntu you'll need to use the alternate CD.  the process is documented in this thread:

[http://ubuntuforums.org/showthread.php?p=2996678#post2996678](http://ubuntuforums.org/showthread.php?p=2996678#post2996678)

fwiw, i've got gutsy running on my D630 with the following exceptions:

sound
cd-rom
intel 4965AGN (but 3945ABG works)
suspend

have fun,
john

---

### Post by lithium06 on 2007-08-02
does this intel x3100 video update help with resume from suspend?

---

### Post by markusfarkus on 2007-08-02
So are you saying that you have no sound or cd-rom?

---

### Post by Lek130 on 2007-08-03
On Feisty you can D630 and similar models to work without any exceptions. The default option for the installer does not work - see comments above. Also follow the link just given above to setup graphics.

From my point of view - using the advice and intel grapihc card driver given here - the graphics work very well. inclusive 3d (beryl, compiz) desktops and so on. WIFI works with the original windows driver and using ndiswrapper to load it ... its all here. If you take 20 minutes to read about it on both threads (this one and the d630 one) you will be on your way very, very well.

Cheers.


D630 setup thread: [http://ubuntuforums.org/showthread.php?p=2899347](http://ubuntuforums.org/showthread.php?p=2899347)

---

### Post by jsage on 2007-08-04
> **markusfarkus said:**
> So are you saying that you have no sound or cd-rom?

that is correct.  however, lek is also right.  to get things working, you have to be willing to compile and install certain modules, as outlined in the threads noted.

since i'm running gutsy on the D630, that would be problematic for me, as the kernel is changing frequently.  i'm content to wait for gutsy release before compiling my own patches and modules.

have fun,
john

---

### Post by prenudos on 2007-08-14
I have a new cpu INTEL G33 with the integrated Intel GMA 3100, I did the steps on the post, but don't get any results
When I change the original XORG 

Section "Device"
        ...
        Driver          "vesa"
        ...
EndSection

to

Section "Device"
        ...
        Driver          "intel"

       ...
EndSection

I loose Everything!
And hvae to come back to the old XORG again.

Anyone can help me?

---

### Post by markusfarkus on 2007-08-14
Check out this link from jsage [http://ubuntuforums.org/showthread.php?p=2996678#post2996678](http://ubuntuforums.org/showthread.php?p=2996678#post2996678)
Browse to page two and three and there is a lot of help on getting your machine's video working.  I had major problems with my machine this weekend and finally got it working via this forum post.

---

### Post by dyous87 on 2007-08-16
I tried this on my Sony Vaio VGN-FZ140E running Feisty and it would not work. I did

```
sudo dpkg-reconfigure xserver-xorg
```

and selected the intel drivers after installing this package. After i restarted X I was greeted with a black screen. Even trying to restart the computer it wouldn't load X. I had to go back to the vesa drivers.

Has anyone had a similar experience or know what I can do to get this working?

---

### Post by Artemis3 on 2007-08-16
Just like the package in the official repository, you are supposed to remove i810 first...

Sadly, video playback with compiz doesn't work. Changing the output is a workaround, but the problem is still the same. It is painful to hunt each and every program trying to use Xv, there is gstreamer, xine, mplayer, vlc, etc.

I hope this gets fixed in either compiz-fusion or the intel driver. In the meantime it is either 3d desktop or video, not both. Or the old i810 driver if you don't mind a dotted video playback...

---

### Post by dyous87 on 2007-08-16
I have removed i810 first but I cannot get it to work for some reason. I wish it would because these vesa drivers are painfully sluggish.

---

### Post by markusfarkus on 2007-08-17
I don't have a Sony laptop, but on my Dell I had to manually add the lines in the /etc/X11/xorg.conf to look like the attached and everything worked fine.  The file is for a Dell D630, but it might point you in the right direction.  (note: for me when I copied the file over top of my xorg.conf it would not work...I had to type the changes by hand).

---

### Post by dyous87 on 2007-08-17
hmm that is rather odd. I will try it out and let you know then. 

thanks,
David

---

### Post by Artemis3 on 2007-08-17
> **dyous87 said:**
> I have removed i810 first but I cannot get it to work for some reason. I wish it would because these vesa drivers are painfully sluggish.

Try Driver "intel" in the section device (instead of i810)

---

### Post by Lek130 on 2007-08-18
> **markusfarkus said:**
> I don't have a Sony laptop, but on my Dell I had to manually add the lines in the /etc/X11/xorg.conf to look like the attached and everything worked fine.  The file is for a Dell D630, but it might point you in the right direction.  (note: for me when I copied the file over top of my xorg.conf it would not work...I had to type the changes by hand).

Actually using your xorg.conf speeds up my display and also improves me using beryl (wobbley ,etc.) ... 

so its all good.

still no luck on the extended mode with the external monitor :(

---

### Post by PacketCollision on 2007-08-19
> **dyous87 said:**
> I tried this on my Sony Vaio VGN-FZ140E running Feisty and it would not work. I did

```
sudo dpkg-reconfigure xserver-xorg
```

and selected the intel drivers after installing this package. After i restarted X I was greeted with a black screen. Even trying to restart the computer it wouldn't load X. I had to go back to the vesa drivers.

Has anyone had a similar experience or know what I can do to get this working?

I have the same problem, using the official version from Gutsy (I just did a clean net-install).  I have the Intell GMA3100 graphics subsystem (G33 chipset).  I'm hoping there's a newer version of the drivers that supports this chipset.  VESA drivers worked in Feisty, but in Gutsy the bottom of the screen is corrupted.

Has anyone managed to make a GMA3100 work?

EDIT:  running 'sudo dpkg-reconfigure xserver-xorg' and setting the correct amount of video memory appears to have fixed it.  My card config in xorg.conf now looks like this:
```

Section "Device"
        Identifier      "Intel Integrated Graphics Controller GMA3100"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        VideoRam        131072
        Option          "UseFBDev"              "true"
EndSection

```

Hopefully that helps.

---

### Post by Lek130 on 2007-08-20
> **PacketCollision said:**
> I have the same problem, using the official version from Gutsy (I just did a clean net-install).  I have the Intell GMA3100 graphics subsystem (G33 chipset).  I'm hoping there's a newer version of the drivers that supports this chipset.  VESA drivers worked in Feisty, but in Gutsy the bottom of the screen is corrupted.

Has anyone managed to make a GMA3100 work?

EDIT:  running 'sudo dpkg-reconfigure xserver-xorg' and setting the correct amount of video memory appears to have fixed it.  My card config in xorg.conf now looks like this:
```

Section "Device"
        Identifier      "Intel Integrated Graphics Controller GMA3100"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        VideoRam        131072
        Option          "UseFBDev"              "true"
EndSection

```

Hopefully that helps.

I guess on Feisty the recommendation was to NOT enter the VideoRam. But let the system ID it. It may not be at all the point - me not knowing gutsy - but just trying to help.

Axel

---

### Post by dyous87 on 2007-08-22
i tired all that but nothing makes the drivers work. i removed the i810 ones, I edited the xorg.conf be hand I even inserted the right amount of video memory but every time I am still greeted with the black screen and have to revert back to vesa.

---

### Post by wekim on 2007-08-22
Hi Voland666,

Your thread looks like the solution to a problem I have been facing for some weeks, however do you have any suggestions for i686 (64bit) architecture.

Thanks for any help

---

### Post by leetrum on 2007-08-23
Any chance of compiling an amd64 edition or providing the src package and build instructions?

Thanks!

---

### Post by starcannon on 2007-08-26
Cool thanks, beryl seems to be fine with it for me so far. Still cant Wine/Cedega World of Warcraft though :( 

I don't expect that a great Feisty setup for this gpu is gonna happen, so I can't wait till October for the Gutsy release, till then thanks loads for the bandaide.

Dell Inspiron 1420n P Ubuntu Edition (next time I'll get one with MS winders and Nvidia and just wipe HDD and install Ubuntu that way and save the hassle)

---

### Post by PlantHead on 2007-09-05
GMA 3100, Intel G33 Express Chipset

This worked fine for me after upgrading my kernel.
However I had to add.

intel_agp
agpgart

to /etc/modules/ 
sudo gedit /etc/modules

Hope that helps someone.

---

### Post by HueponiK on 2007-09-10
It worked very well! Thank you so much:)
:guitar:

---

### Post by luzdegas on 2007-09-11
I have installed the 64 bit version of the drivers. Now when I go to the GUI resolution panel the resolution I wanted (1440x900) is available, but when I choose it the screen look "shrinked", with two lateral black bands on the sides. I have G33 intel chipset and a 19" viewsonic monitor (1935vw). This is happening because my monitor is "wide"?
Thanks in advance.

---

### Post by bryanagee on 2007-09-11
You are a life saver.... We just got new Dell Vostro 200 Machines in our office with the nice 20 inch widescreens, and I really didn't want to be stuck in windoze...

---

### Post by Voullie on 2007-09-14
Hi, don't know if this is the right place to post, but here goes. Have a hp 6510b with the intel 965. I'm using Feisty. Changed the "i810" under "Driver" in xorg.cong to "intel". Still have some problems though.

1. can't enable desktop 3D effects and use totem at the same time.

2. When enabling desktop 3D effects I can't use the cube workspace effect (have installed beryl but still won't work).

3. In xorg.conf the "Screen" section lists 1024x768 as highest resolution even though the options in System->properties->Screen shows 1280x800, which one is it using?

4. Can't use the s-video output, when starting up the computer with the S-video cable connected to the TV, TV-out options in totem are disabled.

My xorg.conf  file is listed at the end of this post. I appreciate all tips on how to solve all or any of these problems.

/Voullie, an Ubuntu noob 

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Allmänt grafikkort"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Allmän skärm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Allmänt grafikkort"
	Monitor		"Allmän skärm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by PlantHead on 2007-09-14
Have you downloaded the driver in the first post of the thread?
You also need to un-install the old i810 driver before installing the new one.

---

### Post by Voullie on 2007-09-15
Hey,

yes, did the sudo apt-get install xserver-xorg-video-intel when I installed feisty fawn from the alternate CD. I was told that this uninstalls the i810 at the same time. Maybe I was wrong. Before I installed the intel package the OS wouldn't even startup though.

cheers/ V

---

### Post by Ballestein on 2007-09-16
the "apt-get remove" should do the trick

After installing this driver, I've been trying to playback some video. No problems with playback, but I get tearing. Is there anyway to set "sync to vblank", through some control panel or in xorg.conf?

Thanks,
Ballestein

---

### Post by Lek130 on 2007-09-17
[QUOTE=Voullie;3363748]Hi, don't know if this is the right place to post, but here goes. Have a hp 6510b with the intel 965. I'm using Feisty. Changed the "i810" under "Driver" in xorg.cong to "intel". Still have some problems though.

1. can't enable desktop 3D effects and use totem at the same time.

2. When enabling desktop 3D effects I can't use the cube workspace effect (have installed beryl but still won't work).

3. In xorg.conf the "Screen" section lists 1024x768 as highest resolution even though the options in System->properties->Screen shows 1280x800, which one is it using?


My xorg.conf  file is listed at the end of this post. I appreciate all tips on how to solve all or any of these problems.

>>>
Using it with Beryl and 3d effects enabled, no issues at all and using the max solution 1280x800. Although XORG should automatically have that, I dont think manual changes will have much impact.

Follow the thread and some of the earlier postings and have latest driver updates on your computer that should work.

whats your config?

---

### Post by Voullie on 2007-09-17
quote Lek130:
[I]Using it with Beryl and 3d effects enabled, no issues at all and using the max solution 1280x800. Although XORG should automatically have that, I dont think manual changes will have much impact.

Follow the thread and some of the earlier postings and have latest driver updates on your computer that should work.

whats your config?
[/I]

Lek130, Which config are you reffering to?
 
Succeeded in getting the workspace cube working with compiz. But I think something's off with the contrast now. Especially the fonts gone weird. It's not fixable with System->Preferences->Font either.

/V

---

### Post by Lek130 on 2007-09-18
> **Voullie said:**
> quote Lek130:
[I]Using it with Beryl and 3d effects enabled, no issues at all and using the max solution 1280x800. Although XORG should automatically have that, I dont think manual changes will have much impact.

Follow the thread and some of the earlier postings and have latest driver updates on your computer that should work.

whats your config?
[/I]

Lek130, Which config are you reffering to?
 
Succeeded in getting the workspace cube working with compiz. But I think something's off with the contrast now. Especially the fonts gone weird. It's not fixable with System->Preferences->Font either.

/V

All your configs :) Computer/Laptop Model, Feisty?, etc ... Because if you would follow this thread and enhance your XORG.CONF (as per outlines here), you should have full Beryl or Compiz, all supported resolutions, etc.

---

### Post by Voullie on 2007-09-18
I'm running feisty fawn on a hp 6510b. It has the Intel 965GM X3100. I'm using the latest intel driver and the i810 driver is removed. My xorg.conf as of latest changes is below. Hope this info is enough. I'm new to Linux/Ubuntu so please bear with me.

/V 

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Allmänt grafikkort"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option 		"monitor-TV" "TVOutput"
	Option 		"CacheLines" "32768"
	Option 		"DRI" "true"
	Option 		"PageFlip" "true"
	Option 		"TripleBuffer" "true"
EndSection

Section "Monitor"
	Identifier	"Allmän skärm"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"TVOutput"
	Option		"Ignore" "true"
EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Allmänt grafikkort"
	Monitor		"Allmän skärm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Lek130 on 2007-09-18
Here is my xorg.conf. I am using.

Question: What is the max resolution you are getting and what is your system capable off? 

For me XORG figures out automatically the max usable resolution (dependent on monitor and card) and uses it. 

With some add-on's below beryl and the like work very well. There is only single feature I turned off in beryl, because it lead to screen irritations around the windows (blur effects).  

Did you read this thread from the beginning to the end?

 
--------
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option "SHMConfig" "on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"XAANoOffscreenPixmaps"	"Enable"
	Option		"DRI"	"Enable"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option		"AIGLX"	"Enable"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by odrium on 2007-09-19
It worked perfectly, and gamma option too. Thanks.
By the way I have a Sony VAIO CR123E.

---

### Post by Voullie on 2007-09-19
Quote Lek130
[I]
Question: What is the max resolution you are getting and what is your system capable off?

For me XORG figures out automatically the max usable resolution (dependent on monitor and card) and uses it.

With some add-on's below beryl and the like work very well. There is only single feature I turned off in beryl, because it lead to screen irritations around the windows (blur effects).

Did you read this thread from the beginning to the end?[/I]

Yes, I've followed the thread from the beginning. My system is capable off 1280x800 and I have i up and running on that now. Also got my desktop effects running with Compiz by installing various drivers from the gutsy repositories and changing gstreamer-properties to "X Window System (No Xv)".

The only thing I still haven't got working is the S-video to my TV. when I boot up with the computer connected to the TV through the S-video there is a white flicker on the TV-screen but nothing more. Don't know what to try next, feels like I already tried everything. The only thing I can think of right now is if my /etc/modules is missing something. It looks like:
[I]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
libata
ata_piix
piix[/I]

/V

---

### Post by jacob01 on 2007-09-19
i installed your driver and so far it is working good except for the screen resolution being so low   800x600   and the refresh rate around 56   i was running the old intel driver with screen res around 1024x745 with the refresh rate at 75, and that was good can any one help me out 

the driver is good from what i have seen in glxgears i have seen a bit of an improvement in my fps:)

---

### Post by MrGando on 2007-09-20
wow, now this is WEIRD...

I was having problems to achieve a 1680x1050 resolution with this video card... well this driver now is leting me choose the 1680x1050 resolution.... the problem is that when I select it my LG monitor doesn't seem to like it , and the whole resolution doesn't fit in the screen. :(

This is weird because I can get 1680x1050 with my MacBook and my Windows machine so something must be wrong ...

here is my xorg.conf


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	VideoRam	256000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"LG22"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel"
	Monitor		"LG22"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Lek130 on 2007-09-20
Why don't you try m xorg.conf, the relevant sections adapted for you. 
I noticed that you use the video ram. something i never did. 

I tried around a few times. Although the resolution was not a real issue, but more beryl and the like. This driver is not as well documented as to which xorg option it supports how. I looked into the source code to figure some stuff out ;-) though i dont want to say that I really went deep, just checked what ever i could ... 

Gutsy might be a good choice for you. It supports hot plug moitors and stuff. Final is October and some people are alreadzy very happy with the tribe 5.

---

### Post by coscos on 2007-10-02
for those who was not able to get this solution work on your ubuntu 7.04, this may help. Besides doing the intel driver upgrade and changing the xorg.conf file as suggested in this thread, run these commands:

sudo apt-get update
sudo apt-get dist-upgrade

After this, reboot. Your kernel should be upgraded to 2.6.20-16 (from 2.6.20-15). 

After days of research, this fix my problem!! Hope this helps.

---

### Post by doobliebop on 2007-10-03
Just wanted to chime in that I finally got mine working. Thanks to everyone for your hard work!

 After the xorg configuration I had to add

intel_agp
agpgart

to my /etc/modules file

---

### Post by susam on 2007-10-06
but it doesn't support the 64bit Ubuntu Feisty......I have only resolution 800*600 and 640*480 
Can anybody tell me what to do with a 64bit OS.

---

### Post by Lek130 on 2007-10-16
hi! 

I upgraded to Gutsy on Sunday! It took about 2+ hours for my d630. I did try gutsy so on my 2 year old desktop PC.

I went the ubunto.org recommended way of using the update manager. That worked without issue and after the final reboot the system came up again in almost working condition.

I have to praise the update manager. Going from anything to anything in Windows (XP to Vista etc) is lengthy and unhappy, but compared to ubuntu ... NICE.

I knew that Gutsy has issues with d630 sound and so I dont have sound anymore (similar to my initial feisty installation some month back). I knew that, I am not worried about it (USB headset always does the trick, which is more important to me).

The 3d effects - compiz fusion did not work initially. in effect this graphic chip set has been blacklsited and an easy file change to not blacklist make it work - NO ISSUES. Beryl was nice but Fusion is the killer.
 
WIFI now is easy as it has a restricted driver there. No issue at all. 

DUAL MONITORS - my main motiviation for the upgrade - did not work at first. It took some reading and then I found a how to with the easy answer.

Look at [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
It explains the issues with the intel graphic driver very well. I got it working in 3D highest possible resolution on monitor and laptop screen, but only with monitors being virtually below each other. There is an issue with the addressable memory in the driver ... read it there. I tried it and it works!

:KS

Its really cool. In effect using 3d and the cube. Gives you a big super cube. For each workspace you get a 2nd one on the 2nd screen. With CTRL ALT CURSOR you see both flpping by. NEAT! :guitar:

and gutsy is faster. 3d at any rate. although it was fast before. 

BTW I did of course do a full backup (using tar and a big USB disk), just to make sure I can go back. After all I am working on this thing.

Very cool. 

If you have some time. Go for it. I would recommend a weekend, just in case so that you have time revert back, in case you use it for your work.

Its not difficult upgrading or even going back for that matter, just time consuming.

Cheers!


UPDATE I tried this link [http://ubuntuforums.org/showthread.php?t=575653](http://ubuntuforums.org/showthread.php?t=575653) and got sound working instantly. :) Now Gutsy for me is the better feisty and I would recommend people the upgrade.

---

### Post by Lek130 on 2007-10-29
Does anyone know the development schedule or roadmap for the intel driver set? The Virtual Buffer in the driver is not covering all the capabilties of the 965 card in the dell 630. It appears to me, that it tries to cover a medium set of functions for all the intel 9xx cards. 

This is great for older cards, but the new cards will have some limitations. For instance, if using 2 monitors the virtual resolution is limited (See above "above or below each other, but not left or right of each other). 

I am sure there are other ares ... 

If anyone knows, please share it.
:popcorn:

---

### Post by bluenote on 2007-10-30
...

---

### Post by bageh on 2007-11-05
Still not working for me: I've tried to compile wine with opengl, but there's no why, wine said there's something wrong with may opengl setup.

Anyway, congratulations for the topic.

---

### Post by Lek130 on 2007-11-06
Can you be more specific as per your setup (hw, ubuntu version, etc.). Please advise.

---

### Post by derwenzel on 2007-11-23
Great. Now I can work without getting a headache.
However, updating just the intel driver did not work. I also had to install gamma patch, but that wasnt difficult.

cya,
  derwenzel

---

### Post by derwenzel on 2007-11-27
Hi again,
today I recognized that the backported driver does not support my external monitor anymore. :(

So far, I just had to boot with external monitor plugged in to get X in 1600x1200 resolution. It worked fine. However, switching between 1600x1200 and 1440x900 wasnt possible since the next smaller mode was 1024x768. But that was fine for me. I either worked on my laptop or with external monitor.

Now, with the new driver that does not happen anymore. I always get an 1440x900, although I boot with external monitor plugged in. 

Any ideas?

I would like to stay with Feisty. So please do not recommend to switch to Gusty.

Thanks and regards,
  derwenzel

PS: Here my xorg.conf:
---
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
 ....
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
....
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
....
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        VertRefresh     50
        DisplaySize     305 190
        Gamma           0.75 0.65 0.60  #see also /etc/X11/Xsession.d/95x11-xgamma
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1600x1200" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1600x1200" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1600x1200" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1600x1200" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1600x1200" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1600x1200" "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by Lek130 on 2007-11-28
Well, I never got 2 monitors working (Dell 630/Intel965 graphic set) with feisty - in extended mode. Clone mode always workd of course. I could only resolve that issue in Gutsy. I tried all recommended approachs, but the driver is limited. I think you would need to look at the driver source code. In the comments in the source code it gives hints on the configuration. 

the way it works in gutsy is setting the VIRTUAL setting in xorg.conf and then using xrandr in the command line. You can try it in feisty too, just not sure it will work, as xorg and xrandr had a serious upgrade.

Curious: What holds you back on Feisty? I upgraded via updater to Gutsy - so no new install at all and no hassle - albeit I did do a full system backup.

Cheers

---

### Post by visionofarun on 2007-12-05
I am on Gutsy Gibbon, X86_64. Any idea where I can get the drivers for X3100?

---

### Post by Lek130 on 2007-12-07
it should be automatically installed. You have an issue? 
You look up further up and you will find some explanation how to install it manually.

---

### Post by damoda on 2008-01-12
Hi,

Thanks for the awesome post. With the help of your post I was able to get Gutsy (Ubuntu 7.10) and Compiz running on a Toshiba A200-03V. I had a bit of trouble though at first, but here is the steps I did:

Added intel as the driver in the xorg.conf.
SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
sudo apt-get install compizconfig-settings-manager

After that I tried resetting X and logging in and out.
I had to restart the computer for some reason to get everything working.

David

---

### Post by WebsGhost on 2008-02-26
hey , I'm new where , and just wanted to say tanks for the post , it's help me so much , after 2 months I can run compiz :)

it's running on LG E500 laptop

---

### Post by Howrrang on 2008-03-02
i really dont understand how to install these files......by Gdeb.....just double click..
please can somone "dummy"-explain a bit more  please....

---

### Post by p-jo on 2008-06-06
Has anyone got an update on this? I'm using 8.04. There is a newer version of xserver-xorg-video-intel, and even if I remove it the contributed version here is not compatible with the current xserver-xorg-core

My screen resolution works ok, but the screen is too far to the left..

---

### Post by Joeb454 on 2008-06-06
I don't think a fiesty-backport would work too well in Hardy ;)

---

