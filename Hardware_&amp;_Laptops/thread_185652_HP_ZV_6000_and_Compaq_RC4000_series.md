---
title: "HP ZV 6000 and Compaq RC4000 series"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by almahtar on 2006-06-01
Discuss.

I know that for me the install was nice and smooth.  After it installs, I had to do a few things to get everything perfect.

I.  Graphics

1.  Go into your bios settings and put your video mode to UMA + Sideport and share 128 megs of ram with the video card.  ATI's Linux drivers seem to only work this way for me.

2.  Download the latest ( 8.25.18 ) drivers from ati.com, reboot into recovery mode, and type:

```
 updatedb
locate fglrx.ko

```, delete any instances of fglrx.ko you see, then install the ati drivers

II.  Wireless
1.  Make sure you have ndiswrapper-utils installed (apt-get install ndiswrapper-utils)
2.  Make sure you have the .inf and .sys files for your card from the card's windows drivers
3.  ```
 ndiswrapper -i <drivername>.inf
ndiswrapper -m
modprobe ndiswrapper
```
4. Make sure ndiswrapper's working ok with "ndiswrapper -l" (should see device detected and working (not verbatim))
5.  I think all the ZV6000's and RC4000's have Broadcom cards.  If so, disable the linux native broadcom drivers (they don't quite work as well as ndiswrapper yet IMHO, and will definitely cause problems if you keep both them and ndiswrapper) by adding the line "blacklist bcm43xx" to the end of /etc/module.d/blacklist
6.  Install network-manager-gnome (which is different from network-manager, which is already installed).  It handles switching wireless nets between different access points very well.

III.  Media Card reader - I've had this work out of the box half the time, and do absolutely nothing the other half.  Even on the same machine.  Needs more testing and research.

Anyone else running Dapper on these machines?  Tell me your thoughts.  I'm writing this late at night after a long day, so I've likely made mistakes.  Also, I was vague on a few steps so as not to bog people down with details: if you need clarification say so and I'll not just respond with explanation but update this post as well.

Loving the Drake :-)

---

### Post by snowpalmer on 2006-06-01
I have a Compaq R4000.  My laptop only shipped with 256 megs of ram and I haven't been able to upgrade yet.  So there are a few things I had to do different on my machine.

1) Use the Alternate Install CD.  You need more than 256 megs of ram to install from the normal cd.

2) If I want hardware accelleration I just installed xorg-driver-fglrx and then ran dpkg-recongigure xserver-xorg.  After that I rebooted and enabled only UMA.  Giving 128 of my precious 256 of ram would kill me.  So I lose my sideport for the time being.

3) Added a bunch of stuff to my xorg.conf that I found on a post here.  It helps tremendously if I have the fglrx driver but accelation disabled.

4) I'm still using the broadcom drivers that come with ubuntu.  Downloaded bcm43xx-fwcutter (enable the extra repos) and ran the script inside.  

```
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

Before I enable the card though I have to use this command.

```
sudo iwconfig eth0 rate 11M
```

I'm not sure how to make that automatic on boot though.

I think that's about it.  It's working fairly well right now.  I'm running the 64-bit version btw.

---

### Post by snowpalmer on 2006-06-01
This is what I added to my xorg.conf in your ati device section.  When I want to turn the sideport back on I change "no_dri" to "yes".

    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
    Option "mtrr"                       "off" 
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "31.5 - 60.0" 
    Option "VRefresh2"                  "60 - 85" 
    Option "ScreenOverlap"              "0" 
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "NTSC-M"
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x06419064"
    Option "Capabilities"               "0x00000000"
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
    Option "CenterMode"                 "off"
    Option "PseudoColorVisuals"         "off"
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    Screen 0

---

### Post by almahtar on 2006-06-01
Gotcha.  Yeah, if you can't afford to lose the 128 MB of ram then you have to settle for 2D acceleration, which works fine for 99% of what you'll want to do.  You might try sharing less than 128 MB (share like... 16 or 8) and seeing if it works:  I've been too lazy to, so it could work.

The 64-Bit version does take a lot more RAM, by the way.  If you're noticing that your memory is really putting the hurt on you I'm willing to bet that 32-Bit would be faster for you.  I'm running 32-Bit because I am sharing memory with the video card and I'd rather not run 64-Bit with the 384 megs left over.

Wireless: does your wireless work with WPA? I'd heard it didn't with the built in broadcom support (*yet*).

I've been running the beta for ages (just reinstalling fresh right now so I can have the same set-up as others in case they need help), and I didn't try the built-in drivers, but ran ndiswrapper with wpa-supplicant and gnome-network-manager.  The combo of the 3 was the first time I finally didn't have to manually set up my wireless after reboots or when I go from work to home/school or whatever (because of gnome-network-manager), and the first time I got WPA support (because of the gnome-network-manager and wpa-supplicant).  That's why I recommended it.  Let me know if gnome-network-manager plays nice with your the bcm43xx module, by the way.

Oh, and you might want to blacklist ndiswrapper if you have it installed ("sudo nano /etc/modules.d/blacklist", and add the line "blacklist ndiswrapper" to the end).  That might help so you don't have to manually bring your wireless up.

---

### Post by snowpalmer on 2006-06-01
I'm connecting to an unsecured wireless network so I don't know whether or not WPA works.  I need to get myself a better wireless access point ](*,) 

In 6 weeks I'll have a 1 GB stick of ram on the way and then I'll be sitting pretty.  64-bit takes up more ram than 32-bit?  That's interesting.  I swear this *seems* faster.. well.. faster than windows that is :) 

I need to try my memory reader.. that's interesting that it would even work half the time for you.  I thought it was a pretty closed book as far as specs go.  I'm very excited to see how well wine is working :) 

I forgot a step above.. I had to download the bcm43xx-fwcutter package and run the script inside. (for my wireless)

---

### Post by Zodiakos on 2006-06-02
Compaq R4000...

I got wireless running without a hitch (all I did was install the bcm43xx-fwcutter package, run the script, and poof, worked on reboot), but I cannot, for anything get the fglrx drivers to work... X simply starts with a blank screen and hangs (alt+ctrl+backspace does nother, nor does trying to switch to console).  No drum sounds.  I've tried reinstalling, uninstalling, changing my sideport in the bios to UMA and adding 128M... nothing seems to work. :(  I feel like my hardware is being unutilized!

---

### Post by Tails on 2006-06-02
well, I am running on my Compaq R4100.... well.. i havent install the ATI driver just yet... too lazy atm.. :P but I will soon.. :P but even without ATI drivers, it runs great!:cool:

---

### Post by OneSeventeen on 2006-06-02
I just downloaded and burned 6.06, and will hopefully install it on my ZV6000 over the weekend.

The last time I got hardware accelleration working without always being at 50% CPU usage, I had to recompile a kernel, so it is great to hear this shouldn't be the case anymore!

I'm still an ndiswrapper fan because it works so well, but I'll definitely let you know how this works on my machine.

I will be formatting my linux partitions and using the GUI installer, hopefully leaving my windows partition alone.  Any tips on how to remove the old Ubuntu on a dual-boot system before installing the new one?  (I don't want to update since I've messed stuff up while being a noob and learning linux for the first time)

---

### Post by snowpalmer on 2006-06-02
I just switched to ndiswrapper.  The bcm43xx was working but it seemed like I had to fiddle with it every reboot in order for it to come up.

On a strange note though network-manager doesn't recognize either my wireless or wired network connections.

---

### Post by almahtar on 2006-06-03
Ok I may have spoken too soon on the 3D.  I had it working in Flight 7, and did all the upgrades without anything dying, so I figured it'd be just as easy in the official release.  Turns out not :-\.  I need to dink around some more to get an answer, and rest assured I'll be on it.  In the mean time I can solve the black screen of death problem: boot into recovery mode and edit /etc/X11/xorg.conf, and in the device section that has "driver" "fglrx", add a line that says "Option"  "nodri".

Gnome will still be just as responsive because you still get 2D acceleration so your CPU isn't interrupted every time it wants to draw a single pixel; you won't have 3D though.  Totem is known to crash when 3D doesn't work, so use Xine or Mplayer.  Don't even try XGL/Compiz without 3D acceleration, either: it'll be really slow or not work at all.

I'm on the case as far as enabling 3D goes, though, so be watching out for a solution.  The wierd thing is that all the Xorg.0.log entries end in "DRI successfully initialized".  No error messages at all in the whole log.  dmesg gives no love either...

Anyway, can anyone running the bcm43xx drivers verify if there's WPA support or not?  How about media card readers for everyone?  The 2.6.15 kernel has *experimental* media card reader support, so if we can figure out what does and doesn't work we can help future kernels have better support.

Things I know nothing about:

    1.  The modem
    2.  The pcmcia
    3.  The Firewire
    4.  The Bluetooth

I have never used any of these.  Anyone know if they work?

---

### Post by almahtar on 2006-06-03
[QUOTE=snowpalmer]I just switched to ndiswrapper.  The bcm43xx was working but it seemed like I had to fiddle with it every reboot in order for it to come up.

On a strange note though network-manager doesn't recognize either my wireless or wired network connections.[/QUOTE]

Is this network-manager-gnome or just the one that comes with Dapper?

---

### Post by OneSeventeen on 2006-06-03
I just installed network-manager-gnome, but don't see any icons... do I need to start the app, or will it start the next time I reboot?

Anyway, the major thing I had an issue with was finding the corect drivers.  Simply using the .inf/.sys files did not work either, following the instructions I found almost a year ago, I was able to get ndiswrapper working super-fast!

Check out [this thread on linuxquestions.org](http://www.linuxquestions.org/questions/showthread.php?postid=1756590#post1756590) addressing the issues with these zv6000 laptops.

It even links to a zip file with all of the files needed.  (I had to copy the entire folder, not just the two files mentioned)

Hope this helps someone else!

I also noticed the cardreader reads my SD card perfectly!!

The only problem so far is while I was typing this message earlier (and installing apps using synaptic at the same time) firefox just quit unexpectedly...  we'll see if that was just because I was doing to many things at once.

---

### Post by Zodiakos on 2006-06-03
See, I didn't have to mess around with ndiswrapper at all... all I did was run the fwcutter script to download the firmware, and installed networkmanager... and poof, it worked (on next reboot).  The dapper broadcom drivers worked perfectly.  The only reason they don't work by default for this laptop is because they need the firmware, which isn't installed by default.

---

### Post by OneSeventeen on 2006-06-03
[QUOTE=Zodiakos]See, I didn't have to mess around with ndiswrapper at all... all I did was run the fwcutter script to download the firmware, and installed networkmanager... and poof, it worked (on next reboot).  The dapper broadcom drivers worked perfectly.  The only reason they don't work by default for this laptop is because they need the firmware, which isn't installed by default.[/QUOTE]
Where do I find the fwcutter script?  And does the broadcom driver support WEP encryption?

---

### Post by almahtar on 2006-06-03
It supports WEP, yes.  Not sure about WPA though.

Getting network-manager-gnome to show up: log out then back in should do it.  You probably won't need to reboot.  Make sure the interface is in your "/etc/network/interfaces/" with lines like:

"auto wlan0
iface wlan0 inet dhcp"

(for ndiswrapper)

or

"auto eth0
iface eth0 inet dhcp"

for bcm43xx

---

### Post by Zodiakos on 2006-06-03
WPA support is always done through WPA supplicant anyways, and the broadcom driver works through that.  My home router is set up with WPA, and it does work with it fine.

The package name for the fwcutter script is bcm43xx-fwcutter.  You'll have to enable the universe repositories to see it, I think.

---

### Post by snowpalmer on 2006-06-03
What is the problem you are having with 3D acceleration?  As long as I change my system to not use the sideport I don't have any problems.  I'm using the drivers from the repository.

---

### Post by snowpalmer on 2006-06-04
Also my card reader isn't working.  I put a memory stick in there just to test it and nothing happened.  dmesg didn't show up any new either.

---

### Post by snowpalmer on 2006-06-04
[QUOTE=almahtar]Getting network-manager-gnome to show up: log out then back in should do it.  You probably won't need to reboot.  Make sure the interface is in your "/etc/network/interfaces/" with lines like[/QUOTE]

Both of my network interfaces are in /etc/network/interfaces.  I have done several reboots since I installed it (from the repos) and it still isn't doing much. I switched to ndiswrapper from bcm43xx.. is it strange that my card is still eth0 instead of wlan0?

---

### Post by Zodiakos on 2006-06-04
My problem is simply that it's not working.  I've followed every installation tutorial for the fglrx drivers I can find; they simply don't work.  Are you sure you have DRI enabled?  If not, it's not actually 3D accellerated.  The driver works fine until I enable DRI, then X boots to a blank screen.  Even stranger, most of the tutorials involve making a symbolic link from /usr/lib/dri to a certain directory (it differs depending on the tutorial).  The strange thing is that I don't even HAVE the directories they refer to.  /usr/X11R6/modules doesn't exist, etc.  Since I have no idea what files are actually needed to get DRI working, and I can't find ANY documentation about them, I'm filing this under "WTF mates?"

I'm certainly not faulting the ubuntu team for this; they simply don't make X, and they don't have the time to test every laptop in the world.  I do partially blame ati, since I did buy the hardware, and I expect them to make a useable graphics driver which would work on major operating systems (and yes, I believe linux should fall under that catagory).  I really just don't think I should have to go through this much trouble to get 3D acceleration working, though.

If you DO have the driver working with DRI enabled, please post the results of the glrxinfo command... if it still says something about Mesa3d, you DON'T have 3D acceleration working.

---

### Post by OneSeventeen on 2006-06-04
Quick update, after rebooting the network-manager gnome does show up, and currently says "No network connection", which is pretty amazing considering I'm posting this over a wireless connection.

My wireless card (through ndiswraper) is eth1  I'll download and install the broadcom script later today and see if that makes a difference.

Changing through the normal network settings dialog works even better than in Breezy, so no real complaints (at least I don't have to reboot each time I switch networks!), but having a shiny GUI to automagically switch would be awsome.

Does it store WEP keys?  so I can just have it switch from an unsecured to a secure connection without having to do anything?

Also, a simple step by step guide on enabling DRI on this specific model would be awsome!  (with every step, including where to get drivers and what commands to type, and maybe a sample xorg config file, for newbies like me)

---

### Post by OneSeventeen on 2006-06-04
Okay, I've got the broadcom drivers working great, now I just want to get 3d accelleration and DRI running.  Simply switching from "ati" to "fglrx" definitely doesn't work for me, so I might try the ati drivers.

My only question now is how do I revert to the Ubuntu drivers if the ATI doesn't work?

---

### Post by OneSeventeen on 2006-06-04
[QUOTE=Zodiakos]If you DO have the driver working with DRI enabled, please post the results of the glrxinfo command... if it still says something about Mesa3d, you DON'T have 3D acceleration working.[/QUOTE]

Following the instructions [here](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25), I installed the xorg-driver-fglrx (instead of just swapping "ati" for "fglrx", which I did before my previous post #-o ) and fglrxinfo returns:
```
oneseventeen@tigershark:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)
```
And glxgears returns:
```
oneseventeen@tigershark:~$ sudo glxgears -printfps
5472 frames in 5.0 seconds = 1094.317 FPS
5448 frames in 5.0 seconds = 1089.590 FPS
5451 frames in 5.0 seconds = 1090.046 FPS
5382 frames in 5.0 seconds = 1076.216 FPS
```

It may not be super-amazing, but it gets the screensavers working nicely!

We'll see if GLX/Compiz works with these drivers.

---

### Post by OneSeventeen on 2006-06-04
Okay, after following [This Guide](http://www.ubuntuforums.org/showthread.php?t=168618), I got XGL/Compiz running!!

This is all with no proprietary drivers!! Simply using Ubuntu's bcm43xx and xorg-driver-fglrx!!

This is awsome, now if it weren't for using the flash player, I'd be pretty open-sourcing it at the moment.  I have to hand it to the folks at Ubuntu, they've done an amazing job with this release.

I'll try to stop dominating the thread, and let some other people post, then I'll answer any questions I can as far as getting this laptop running smoothly with Ubuntu.

---

### Post by Zodiakos on 2006-06-04
The xorg-driver-fglrx is a proprietary driver, I thought... it's just the compiled package for ubuntu.  It's still ati's driver, just packaged nicely.  I'm certainly not going to swear on that though, I know next to nothing about that stuff.

But... I DID finally get it running... those were the same instructions I've been using, time and time again on this laptop... until I noticed something.  There was an extraneous line that I assume ubuntu kept adding on fresh install to my xorg.conf file (Something about screen 1:5:0... I don't remember because I was stupid and deleted it...).  On a hunch, I deleted it.  And lo and behold... X suddenly booted up in full DRI mode.  I decided to press my luck further, and turned on Sideport in the bios... but no go.  For some reason, X will only boot correctly in UMA ONLY mode... which is horrendous.  128MB totally wasted...  ATI makes me cry, I swear.

I have the Compaq R4000... if anyone else has any troubles, be sure to delete any extraneous lines that refer to screen in the driver section.  It might just help.

Now, to get XGL/Compiz running...

-edit:  According to this, [http://ati.cchtml.com/show_bug.cgi?id=183](http://ati.cchtml.com/show_bug.cgi?id=183) the reason is that the kernel is always showing 256MB of video memory for some reason.  Unknown whether it's a kernel bug, an HP/Compaq bios bug, or a bug in the ATI drivers.  Possibly all 3, who knows?  According to the comments there, it's pretty much random from model to model whether it works with only UMA enabled, or Sideport+UMA.

---

### Post by snowpalmer on 2006-06-05
[QUOTE=OneSeventeen]Okay, after following [This Guide](http://www.ubuntuforums.org/showthread.php?t=168618), I got XGL/Compiz running!![/QUOTE]

That's great! Did you have to do anything special?  I followed the instructions and I can get into Xgl.. but the startcompiz script just gives me a pure white screen.

---

### Post by snowpalmer on 2006-06-05
[QUOTE=Zodiakos]I have the Compaq R4000... if anyone else has any troubles, be sure to delete any extraneous lines that refer to screen in the driver section.  It might just help.[/QUOTE]

That's strange.  Is this the line you are talking about?

```
BusID           "PCI:1:5:0"
```

I have a Compaq R4000 and it hasn't seemed to affect my 3D. I'm glad you got yours working.. strange that that was the problem.

---

### Post by Zodiakos on 2006-06-05
Yep, that's the line, right there.  Upon removing it, everything just.... worked.

---

### Post by OneSeventeen on 2006-06-05
[QUOTE=snowpalmer]That's great! Did you have to do anything special?  I followed the instructions and I can get into Xgl.. but the startcompiz script just gives me a pure white screen.[/QUOTE]
First, I installed the video drivers by simply:
```
sudo apt-get update 
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
(as described [here](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25))
Then I rebooted.

I then installed, through synaptic, compiz-gnome, compiz, xserver-xgl, libglitz1 , and libglitz-glx1.
(The rest were already installed.)

Then, as described [here](http://www.ubuntuforums.org/showthread.php?t=168618):

I created /usr/bin/startxgl.sh with:
```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session
```(and chmodded it to 755)

Then, I created /usr/bin/startcompiz (later chmodded to 755) with:
```
killall gnome-window-decorator 
wait
gnome-window-decorator & DISPLAY=:1
compiz --replace gconf
#fixes the shift-backspace bug
xmodmap /usr/share/xmodmap/xmodmap.us
```

Then, I made an XGL session by ```
sudo gedit /usr/share/xsessions/xgl.desktop
```
Then added to that file:```
[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```
Then I added "/usr/bin/startcompiz" to the startup items for my session. (Under System>Preferences>Sessions>startup-programs)

Then I logged out, and before logging in I selected Options>Choose Session, and I chose "XGl", then logged in as normal (telling it to only use "XGL" for this session, since I don't know if it will work, or if I will like it)

Then, while logging in, your cursor turns to an X, you get the hatched BG, and after a while things go close to what they should be like.

Then, go to gconf-editor, navigate to apps>compiz>general>allscreens>options, and double-click on "active_plugins".
Then add (in this order):
```
gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher
```

And now, move the windows around, hit <ctrl>+<alt>+<right arrow>/<left arrow>, <alt>+<tab>, and my favorite, <ctrl>+<alt>+<click & drag in blank desktop space>

Once again, this is just a summary of what I did, combining [this Ubuntu ATI driver install guide](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25), and [this Compiz install guide](http://www.ubuntuforums.org/showthread.php?t=168618)

I would still like to know how to zoom in and out, as <start key> + <mouse wheel up/down> doesn't seem to work for me.

It is also important to note that windows without buttons aren't draggable unless you hold the alt key down.

Oh, and Apple fans should enjoy the F-12 key.

**Some Quick Network Questions**
It appears that I still can't use network-manager-gnome, is there a place I need to go to tell it to use eth1?  I also need to restart my computer in order to go from a WEP encrypted connection to an open network....
**EDIT:** Restarting with the new network selected still doesn't work... so I'm not sure how to switch to an unsecured network... I've even made a new profile with nothing in the key field, and with the new essid.... kind of odd/dissapointing, but we'll see.
**Edit:** Restarted again and it seems to be working... glad it works, but would prefer not to have to restart to switch networks... network-manager-gnome still shows no wireless networks...

---

### Post by snowpalmer on 2006-06-06
[QUOTE=OneSeventeen]First, I installed the video drivers by simply[/QUOTE]

Thanks for the info. It was basically what I had done before but this time it worked!  I just reinstalled using i386 instead of amd64.. maybe that was the difference.  I'm actually very surprized at how well it works on my system.  Only 256 megs of ram and 32 megs shared with the video.  Not too shabby.

---

### Post by rekahsoft on 2006-06-06
Could some one show how to get the ATI propriatary drivers working in one easy to follow summary...i have tried every how-to manual on the net and have not yet get it working. Thanks.

---

### Post by Zodiakos on 2006-06-07
Just a question... did you also install NetworkManager in addition?  Network-Manager-Gnome is only the frontend.

---

### Post by OneSeventeen on 2006-06-07
[QUOTE=Zodiakos]Just a question... did you also install NetworkManager in addition?  Network-Manager-Gnome is only the frontend.[/QUOTE]
I just installed Network-Manager-Gnome, and I assume that NetworkManager was either already installed, or it was listed as a dependency, since it works now without having to install anything else (that I know of)

I'd also like to add about XGL/Compiz:
installing XGL/Compiz successfully removed restart and shut down from my shut down menu, so I have to log out, then shut down from the logon screen.

---

### Post by snowpalmer on 2006-06-08
[QUOTE=OneSeventeen]I'd also like to add about XGL/Compiz:
installing XGL/Compiz successfully removed restart and shut down from my shut down menu, so I have to log out, then shut down from the logon screen.[/QUOTE]

I see the same thing here. It's very strange. I'd like to have those buttons back actually :D But I will have to say that I'm really enjoying this Xgl/Compiz.  A couple of my co-workers are enjoying it as well :)

---

### Post by george.guimaraes on 2006-06-09
Hey guys,

I own a ZV6000 (actually, a ZV6123cl). I managed to get ATI drivers and 3d acceleration working but only using UMA mode only (128MB video memory wasted!! :mad: :mad: )..

Anyone get 3d with Sideport enabled?!?! Please let me know!


George...

---

### Post by rekahsoft on 2006-06-09
this is a WTF question:
on boot (after grub decompresses my kernel) i get the following errors:
```
unable to alocate resource 7 of PCI Bridge at 0000:00:04.0
unable to alocate resource 8 of PCI Bridge at 0000:00:05.0
```Is this effecting my fglrx driver installation? I am guessing it in not alocating my video card memory (I have a Radeon 200M in a compaq R4000). I have tried every how-to manual on the web and still no luck...and i think this might be the issue. I have tried in UMA, UMA + sideport and Sideport. Thanks for the help :)

---

### Post by snowpalmer on 2006-06-09
[QUOTE=rekahsoft]i get the following errors:
```
unable to alocate resource 7 of PCI Bridge at 0000:00:04.0
unable to alocate resource 8 of PCI Bridge at 0000:00:05.0
```Is this effecting my fglrx driver installation?[/QUOTE]

That shouldn't make a difference.  I have a Compaq R4000 and I get the same message. (my fglrx is working just fine)

```

~$ dmesg | grep "allocate resource region"
[4294669.864000] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[4294669.864000] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0

```

Did you try that little exerpt from OneSeventeen from above?  I have configured it differently before and got it to work.. but that way was extremely easy.

---

### Post by snowpalmer on 2006-06-09
[QUOTE=george.guimaraes]I managed to get ATI drivers and 3d acceleration working but only using UMA mode only (128MB video memory wasted!! :mad: :mad: )..

Anyone get 3d with Sideport enabled?!?! Please let me know![/QUOTE]

It's been hit and miss with me.  There was one time I rememeber I booted with 128 UMA and 128 Sideport. But maybe I am remembering wrong because I can't seem to get it to work now.  I agree.. I hope ati does something about this.  I would really love to use my Sideport.

---

### Post by rekahsoft on 2006-06-09
Could someone show how to get fglrx working...i have tried everything i have read yet have not had it working...i wonder where the problem with the Radeon 200M on Compaq R4000's lays...the kernel, the driver or the bios...couls someone with this exact set-up that has 3d acceleration working show what they did. Thanks

---

### Post by snowpalmer on 2006-06-11
[QUOTE=rekahsoft]Could someone show how to get fglrx working...i have tried everything i have read yet have not had it working...i wonder where the problem with the Radeon 200M on Compaq R4000's lays...the kernel, the driver or the bios...couls someone with this exact set-up that has 3d acceleration working show what they did. Thanks[/QUOTE]

Enable UMA only (no sideport)

On a fresh install run these commands and reboot.  This is all I had to do on my machine.

```

sudo apt-get update 
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

---

### Post by rekahsoft on 2006-06-11
Thanks, i will try this again...after i clean my system. I believe i already have but i will again and make sure i have UMA enabled....btw is there any third party ATI driver that supports 3D acceleration?

---

### Post by rekahsoft on 2006-06-13
OK...i have been at this forever...i still can't get this ...stuff working...i have tried everything and i still have had no luck....grrrrr...anyone could you please help.

---

### Post by almahtar on 2006-07-12
Yeah baby! Up and running with the 8.26.18 fglrx drivers + xgl and compiz :-)  All the hardware's working except the inconsistent behavior with the media card reader.

---

### Post by OneSeventeen on 2006-07-17
I just wanted to add that my card reader has been more reliable than my USB ports lately, that the latest updates have broken XGL, and that I can no longer connect to some wireless networks.

Well, it connects to the networks, but cannot get on the internet... if I reboot in windows, windows tells me there is something wrong with the network prevenging me from getting on line, then it pauses, then tells me everything is fine and I can now get on the internet... weird to say the least!

Does anyone else have weird issues with the wireless on this laptop?
(it works 100% of the time on my home network)

---

### Post by doog on 2006-07-17
> **rekahsoft said:**
> Thanks, i will try this again...after i clean my system. I believe i already have but i will again and make sure i have UMA enabled....btw is there any third party ATI driver that supports 3D acceleration?

Not that I know of other that'll work with full Sideport/onboard memory and DRI.  When I asked ATI about this, they gave their canned response and said they don't support laptops and to ask the device manufacturer. HP/Compaq are still selling a ton of laptops with these chipsets so DON'T fall for it. The ATI Linux driver is so poor, the laptop isn't worth the hassles.

---

### Post by peregrine on 2006-08-15
Hey thanks for the great tutorial. I used to run a version of [Slax]("http://slax.linux-live.org") on a machine with a dead harddrive. Then I got it running with a new hd and Ubuntu for my mom and I bought a compaq R4000. Little did I know the good deal I got would cost me so much work for Ubuntu. 

Its really too bad we cannot use sideport memory. But can we enable sideport+uma? So when I use windows I have the full use of my sideport?

Thanks :)

---

### Post by OneSeventeen on 2006-09-22
Just to revive this old thread, since I still have my ZV 6000, I just tried XGL for the first time in months, and apparently recent drivers have fixed XGL and it works again!!

Yay!

Now to show off linux to the mac users around here :p

I've also noticed that the card reader still works great, which is very surprising!

---

### Post by george.guimaraes on 2006-09-22
What driver did you use? Where can i get it?

Thx!

---

### Post by arron on 2007-01-07
I read that some people have the memory card working for this laptop and some don't.  When i run lspci it comes up with:

```
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 Class 0805: T
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controllerexas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
```

and when i insert a memory stick syslog reports:

```
kernel: [17181421.468000] tifm_7xx1: ms card detected in socket 2
```

It can tell its a memory stick, and when it goes in and out of the slot.  Does anyone have this working, its the last hardware hurtle for my windows-linux transition, aside from a messenger webcam chat.

Arron

---

### Post by postadelmaga on 2007-03-03
anyone have xgl/compiz or Beryl working on Compaq r4000 ??
if you get it please post about sideport and ultradma setting in your bios ... (that is the problem i think)
and also xorg.conf setting ....

for me :
fglrx                ok (ver.8.34)
direct rendering ok
beryl                no
compiz             no

in my case when i start xgl session i got an error and X crashes
while the 'normal' session work ok.
i hope you could help me ... :KS

---

### Post by arron on 2007-03-03
I got it working... long story.  First do you have 3d rendering (ati drivers installed)?

First step is to make sure you have the ati drivers working:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

when you have it working, run glxgears to make sure.

Now for the fun part:

remove any beryl/compiz you have installed, the newest one is not compatible. after its off add this to your /etc/apt/apt.sources for the beryl depository:

```
## beryl
deb http://ubuntu.beryl-project.org/ edgy main
deb-src http://ubuntu.beryl-project.org edgy main
```

then install a older package set that works on the laptop:

```
$ sudo apt-get install beryl=0.1.99.2~0beryl1 beryl-core=0.1.99.2~0beryl1 beryl-manager=0.1.99.2~0beryl1 beryl-plugins=0.1.99.2~0beryl1 beryl-plugins-data=0.1.99.2~0beryl1 beryl-settings=0.1.99.2~0beryl1 beryl-settings-bindings=0.1.99.2~0beryl1 emerald=0.1.99.2~0beryl1 libberyldecoration0=0.1.99.2~0beryl1 libberylsettings0=0.1.99.2~0beryl1 libemeraldengine0=0.1.99.2~0beryl1
```

then you need to have the xgl server (the above may install it, let me know if it does or not), this is for the ati card

```
$ sudo apt-get install xserver-xgl
```

then you will have to make a script to run it:

```
$ sudo gedit /usr/local/bin/startxgl.sh
```

then paste this in:

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```

make it executable:

```
$ sudo chmod a+x /usr/local/bin/startxgl.sh
```

now you need to make a option to run the xgl server keeping the settings (or something like that):

```
$ sudo mkdir -p /etc/X11/sessions
$ sudo gedit /etc/X11/sessions/xgl.desktop
```

and paste:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

now restart x.  for some reason there is a bug with the  ATI driver that makes a white cube, run:

```
$ LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl
```

You may have to run this at each startup.  If you get a white cube after a reboot, let me know, and let me know where you found a place to stick it, i think the /usr/local/bin/startxgl.sh script would do the trick.

if all goes well, you can now start beryl:

```
$ beryl-manager
```

And now it *should* work.  i would be interested to know if these steps work for you on a fresh machine.  It took a lot of tinkering and different setup to get it to work for me, but i believe this is what it needs.  Id love to know if this works on a fresh machine.  Post your results on the steps you take and your results.  This was on my Compaq R4000 series.


links with more info:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration)
[http://forum.beryl-project.org/viewtopic.php?f=36&t=4046](http://forum.beryl-project.org/viewtopic.php?f=36&t=4046)

Someting im still unsure of, if adding that ```
$ LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl
``` line will make the default ubuntu beryl package work. try that out first and see if it fixes your errors.

---

### Post by arron on 2007-03-03
> **postadelmaga said:**
> 
for me :
fglrx                ok (ver.8.34)
direct rendering ok


Do you have a link to get 8.34 working?  I found some info that the newer ones had a error (might of been fixed now) and im now running 8.32.5 and it runs great for 3d games.  Does glxgears work ok for you, or choppy, and can you run a 3d game?  Where did you get that driver from, and any good howto for it?

Arron

---

### Post by arron on 2007-03-03
[IMG]http://arron.dnip.net:81/files/Screenshot.png[/IMG]

Here is a screen shot on my R4000 series (R4125CA).

Good luck, let us know how you make out.

---

