---
title: "Ubuntu 11.04: Nvidia problem: Laptop - can't connect to external monitor"
date: 2011-06-16
forum: Hardware
---

### Post by blueskyabove on 2011-06-16
Upgraded to 11.04 and have problems with the display and the Nvidia driver. I've activated the drivers in the "Additional drivers" panel twice and used Synaptic to run Nvidia-update (followed by a restart). I still have "This driver is activated but not currently in use" in the Additional Drivers control panel plus, in the header, "No proprietary drivers are in use on this system".  I've run all the system updates.

There are two consequences of this: one is minor and the other serious. The minor one is that there is no Advanced option (or whatever it is called) in the Appearance control panel but I can live without the special whizzy effects!  The major one is that my laptop won't redirect output to an external monitor or a projector. The Ubuntu Display control panel won't detect a second display when the "Detect monitors" button is clicked. It also can't detect the laptop's own display type and labels it as "Unknown". Using the Nvidia X Server control panel, I can see that the laptop's display is a Seiko/Epson panel and, when I click the "Detect displays" button I do get the second display (a flat panel monitor),but it is labelled: "CRT-0 disabled".

My laptop is a Dell Vostro 1400 laptop with a GeForce 8400M GS display card installed.

Given that the Nvidia driver is very widely used, it seems a bit odd that the Ubuntu testing process did not pick this up before release and even more odd that it is not being fixed quickly - not good enough really.  And, this is a big deal for the uptake of Ubuntu insofar as this issue might stand in the way of a laptop connecting to an external monitor which is something that users of laptops routinely do in a work context.

All this worked just fine under 10.10. I've combed the web and there does seem to be a problem in this deneral area with various symptoms and no obvious solution. I'm at the limit of my technical knowledge here and help and advice would be greatly appreciated!

---

### Post by mberend on 2011-06-17
Hi

I have the same exact problem. I am using Lenovo T510 with 11.04.
My sypmtoms:
- This driver is activated but not currently in use
- cant use the external monitor as primary
-  Ubuntu Display control panel won't detect a second display
- no advanced settings (didn't even know they exist)

I can use twinview making my external monitor a part of the whole display but I want it to work as the primary monitor when Lenovo is docked. Can't make this work. Very frustrating. First time migrated from Windows and this is not encouraging... 

Please help. Thanks

---

### Post by foresthill on 2011-06-17
> **mberend said:**
> Hi

I have the same exact problem. I am using Lenovo T510 with 11.04.
My sypmtoms:
- This driver is activated but not currently in use
- cant use the external monitor as primary
-  Ubuntu Display control panel won't detect a second display
- no advanced settings (didn't even know they exist)

I can use twinview making my external monitor a part of the whole display but I want it to work as the primary monitor when Lenovo is docked. Can't make this work. Very frustrating. First time migrated from Windows and this is not encouraging... 

Please help. Thanks

Are you using the "Nvidia Settings" applet? If you don't see it in your programs menu, try typing nvidia-settings in the terminal. That is, if you can find the terminal in Unity (they hid it somewhere that I can't find). 

If you need to use the terminal command and can't find the terminal, log out and click on your username and then at the bottom of the screen choose "Ubuntu Classic" and log back in. Terminal will be under "Applications / Accessories".

Once you get into nvidia settings, it SHOULD have a section where you can configure multiple monitors. 

HTH.

---

### Post by tsmiller55 on 2011-06-17
Guys, 
Same thing here.  I went from 10.10, where I was using my external monitor successfully to 11.04 where I have problems. I have information that might help.

If I run kubuntu from the cdrom, everything works.  I see both monitors.

If I run kubuntu from the hard disk, the system will not even recognize that I have an external monitor.  

This is from a fresh install of 11.04.  Without any changes to anything on disk.  Maybe this info will at least help someone think about what is happening.

tom

---

### Post by blueskyabove on 2011-06-21
Tried the Nvidia Settings thing but no change.  11.04 still won't play with an external monitor and the laptop's Fn/F8 key combo won't redirect the output either.  Again, 10.10 worked fine.

Is this just us few having this problem?  Surely there must be more in the same boat?  Is anybody with the capacity to deal with this actually looking at this thread?  If they are, any  chance of a response?

If not, where do we take this problem to get it fixed, who do we tell?  This is another barrier to Ubuntu becoming a widespread system punching its weight with Windows and Apple.  It's not yet a true consumer oriented product.

---

### Post by mberend on 2011-06-23
> **foresthill said:**
> Are you using the "Nvidia Settings" applet? If you don't see it in your programs menu, try typing nvidia-settings in the terminal. That is, if you can find the terminal in Unity (they hid it somewhere that I can't find). 

If you need to use the terminal command and can't find the terminal, log out and click on your username and then at the bottom of the screen choose "Ubuntu Classic" and log back in. Terminal will be under "Applications / Accessories".

Once you get into nvidia settings, it SHOULD have a section where you can configure multiple monitors. 

HTH.

Thanks for your reply. Yes I am using the nvidia applet, and also I am using ubuntu-classic. I can add the second monitor from the applet, but it will never switch it as a primary. The best I could make it work is as a twinview, that is my external monitor was an extension of the laptops desktop. It just doesn't want to switch to the external only. Also since I installed the nvidia driver, the ubuntu monitors applet doesn't recognise any monitors. 
Another thing. I just disabled nvidia and reverted to nouveau drivers and the external monitor works fine.

---

### Post by rcond on 2011-06-25
Hi guys,
I also have the same problem. I was successfull exporting video using the "NVIDIA X Settings" with "sudo" (executing the gnome-control-center from the terminal) and the twin view option, however, once I disconnected the external monitor (my LCD TV in this case) the video did not remain the same in the notebook, in fact it got scrambled and I had to start Ubuntu 11.04 in safe mode and select the "Restart X server" option in order to reset the X configuration. Now I'm stuck and can't export video unless I do the same steps to revert the X server configuration.
I have a Dell VOSTRO 1500 with NVIDIA 8400GS (the same problem occur with NVIDIA proprietary drivers that I downloaded from the oficial site and the drivers ubuntu offers to install which usually is slower than the most current driver).
I think there is no solution for that unless wait for the lTS version or come back to Windows (wich will be my case). :(

---

### Post by gregboone on 2011-06-30
Same issue.  Migrated from 10.10 to 11.04 and can no longer see the TV I use as a monitor from time to time.  I have tried all the settings with in NVIDIA X control panel whatever it is called.  Anyway, very very irritating.  Why they have to break the darn thing when making it Unity?  Okay, anyway, I am okay with Unity, gotten used to it... I am but a SURFER/EMAILER pretty much anyway, but like to watch some Youtube video on my big screen from time to time...

If you get or find a solution, please email me: [email]luv_hot_chiles@hotmail.com[/email]

---

### Post by vulgrin on 2011-07-27
Anyone solve this yet?

Having similar issues here. Though I can't even run the Nvidia applet.  If I do what it says and create the nvidia xorg.conf, then X won't start.  Have to go in and remove the conf before I can get back in at all.

Dell XPS 15z.  Really frustrating - all I want to do is be able to make an external monitor the primary and close the laptop.  Something that I've been able to do on Windows for years and years...

---

### Post by blueskyabove on 2011-07-28
No, nobody has solved it yet.  As far as I can see, nobody has tried or is interested - apart from us sufferers.  No idea where to go with this at all. And I'm astonished that nobody tested this on a laptop before rolling out 11.04, it's such a fundamental part of the functionality of a laptop - the capacity to connect to an external monitor.  It's one small reason (among others) why Ubuntu/Linux, good though it is, is not yet a product fit for a mass market.

---

### Post by vulgrin on 2011-07-28
Well. I'm going back to windows on that laptop it appears, running Ubu in a VM only when I need to.

I don't really expect them to be able to test on every platform or every bit of functionality.  I mean, that's why its a FOSS product.  If I were paying $100 for it, I'd definitely expect it to work.  Unfortunately, I just don't have the time to beta test right now - I need it to work.

That's just how it goes in the OSS field. You're choosing spending time over spending money.  Kind of like the difference between going to the grocery store or growing your own food. :)

---

### Post by AgentZ86 on 2011-07-28
> **vulgrin said:**
> Well. I'm going back to windows on that laptop it appears, running Ubu in a VM only when I need to.

I don't really expect them to be able to test on every platform or every bit of functionality.  I mean, that's why its a FOSS product.  If I were paying $100 for it, I'd definitely expect it to work.  Unfortunately, I just don't have the time to beta test right now - I need it to work.

That's just how it goes in the OSS field. You're choosing spending time over spending money.  Kind of like the difference between going to the grocery store or growing your own food. :)

I understand the fustration, however keep in mind even paying $100 dollars does not mean it will work.

I am a windows support tech and made most of my money fixing windows problems for people and installing software that they could not install including drivers etc. etc.

This will not solve your ubuntu problem, but this post has various differences in subject matter that may not be the same as the other persons issue.

Some are posting about problems with external monitors, which is the topic of this post while others are posting about additional possibly related problems but perhaps not.

The 11.04 topic regarding xorg I have found that some nvidia legacy driver support is not installed by default to match the  latest version of xorg thus the nvidia proprietary driver must be installed manually.

Jockey will not pick it up and installed it for you.

So some older nvidia cards may not get 3d support and activate and may be forced to use the experimental driver which may not get the twin view working properly as well with the nvidia app.

For those using cards that are supported by the new xorg such as the GS8400 etc. I wish I knew most about the driver and hope someone posts about the external monitor issue.

I'm sure you all have tried (fn) keys or whichever keys your laptop requires in order to switch to external monitors.

So this must be related to the nvidia setting app. 

Here is something interesting I found on the net you can try

[http://www.bigfatostrich.com/2011/05/solved-ubuntu-11-04-broken-external-display/](http://www.bigfatostrich.com/2011/05/solved-ubuntu-11-04-broken-external-display/)

And in launchpad here is something some have gotten working read down the page someone posted some hack solutions and also simpler solutions that may not be hacks but temp fixes here too

[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/154729](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/154729)

Hope this helps and sorry for the problems.

---

### Post by offbeat404 on 2011-07-29
> **foresthill said:**
> Are you using the "Nvidia Settings" applet? If you don't see it in your programs menu, try typing [COLOR="Red"]nvidia-setting[/COLOR]s in the terminal. That is, if you can find the terminal in Unity (they hid it somewhere that I can't find). 

If you need to use the terminal command and can't find the terminal, log out and click on your username and then at the bottom of the screen choose "Ubuntu Classic" and log back in. Terminal will be under "Applications / Accessories".

[COLOR="red"]Once you get into nvidia settings, it SHOULD have a section where you can configure multiple monitors. [/COLOR]

HTH.

yup, this worked sweet on my dv4 w/ GeForce G 105M. 

~thank you sir

---

### Post by SwimDude0614 on 2011-08-02
I'm using Canonical's experimental driver and can not use my external monitor. I have an HP Elitebook 8530w with the NVIDIA Quadro 770m.

---

### Post by realzippy on 2011-08-02
*Canonical's experimental driver*

What do you mean?Nouveau?
Why not using the nvidia driver ?

---

### Post by SwimDude0614 on 2011-08-02
I'm not sure what it is called, but in the "Hardware Drivers" window of 11.04, I was offered a non-NVIDIA driver that said "experimental" and downloaded roughly 10^4 times faster (that's just an estimate) than all of the NVIDIA drivers I've installed via the same method. It works much better than other drivers and even plays flash better! For the most part, I'm loving it. Except for the lack of external monitor support :(

---

### Post by bmg2k10 on 2011-08-08
I had a heck of a time getting this sorted out. It's been awhile since I dubbed with the xorg.conf file (which 11.04 doesn't have by default, but doesn't complain if it's there. I'm not sure if it will work with the available drivers to download, but it worked with the nvidia 280.x driver (downloaded from nvidia and built local)
I'm successfully running on an external monitor ONLY now and I have the option of turning the lcd back on on the laptop (sorry, a bit scatter brained at the moment, using an old compaq presario v6210us) 
The xorg.conf file will most likely need to be updated after reboot (you may need to run nvidia-xconfig first, then edit) If you're stuck and can't edit, use ctrl/alt/F1 to go a console, log in and edit from there with vi or nano or other. Some of the settings in the following are irrelevant or extra garbage from the nvidia-settings tool once I was in X (the refresh rates were all wrong so I was limited to 640x480 until I fixed those)
I hope this helps somewhat.


[SIZE=2]**My totally bunked up xorg.conf file is as follows (sorry, I didn't bother to clean it up)**[/SIZE]:


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 280.13  (buildmeister@swio-display-x86-rhel47-05.nvidia.com)  Wed Jul 27 17:18:55 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       31.5 - 54.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select @1024x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


[SIZE=2]**My .nvidia-settings-rc (for those interested):**[/SIZE]

#
# /home/bryan/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Mon Aug  8 08:48:09 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = Yes
Timer = Graphics_Card_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

ubuntu:0.0/CursorShadow=0
ubuntu:0.0/CursorShadowAlpha=64
ubuntu:0.0/CursorShadowRed=0
ubuntu:0.0/CursorShadowGreen=0
ubuntu:0.0/CursorShadowBlue=0
ubuntu:0.0/CursorShadowXOffset=4
ubuntu:0.0/CursorShadowYOffset=2
ubuntu:0.0/SyncToVBlank=0
ubuntu:0.0/LogAniso=0
ubuntu:0.0/FSAA=0
ubuntu:0.0/TextureSharpen=0
ubuntu:0.0/AllowFlipping=1
ubuntu:0.0/FSAAAppControlled=1
ubuntu:0.0/LogAnisoAppControlled=1
ubuntu:0.0/OpenGLImageSettings=1
ubuntu:0.0/RedBrightness=0.000000
ubuntu:0.0/GreenBrightness=0.000000
ubuntu:0.0/BlueBrightness=0.000000
ubuntu:0.0/RedContrast=0.000000
ubuntu:0.0/GreenContrast=0.000000
ubuntu:0.0/BlueContrast=0.000000
ubuntu:0.0/RedGamma=1.000000
ubuntu:0.0/GreenGamma=1.000000
ubuntu:0.0/BlueGamma=1.000000
ubuntu:0.0/DigitalVibrance[CRT-0]=0
ubuntu:0.0/ImageSharpening[CRT-0]=0
ubuntu:0.0/XVideoTextureSyncToVBlank=1
ubuntu:0.0/XVideoBlitterSyncToVBlank=0
ubuntu:0.0/XVideoSyncToDisplay=1

---

### Post by bmg2k10 on 2011-08-08
One more note, don't panic when the ubuntu logo on startup gets screwed up. That's normal. If I recall, it requires editing grub settings to display correctly again, which I don't remember at the moment.

---

### Post by blueskyabove on 2011-08-13
Really appreciate all the information about configuring the various drivers/control panels and all that.  BUT ... it's not what I remotely want to have to do and I ain't gonna do it!  It's such a basic function of any operating system to allow a laptop to connect to an external monitor via a simple key combination without having to fiddle with the back office settings - all other operating systems do it.

Sorry to hammer on about this - you may yawn if you wish - but it should have been sorted before the release of 11.04.  Ubuntu will NEVER crack anything more than a tiny fraction of the mass market if it doesn't get this kind of basic thing right.  Still, nobody who manages and maintains Ubuntu is listening or hearing what is being said here (and elsewhere).  How do we get these messages to the people who write the code?

---

### Post by dfarrell07 on 2011-08-26
Well, I had this trouble as well, and I managed to fix it. I'm running Ubuntu 11.04 from a Lenovo W520 with a Nvidia Quadro 2000M GPU. When I plugged in a external monitor via VGA, Monitors showed my main laptop monitor as 'unknown' and would not detect the external display when I clicked 'detect monitors.' I have been using Ubuntu since 8.04 (on a Lenovo T61p), and had not had this trouble before. 

To fix it, open 'Nvidia X Server Settings.' If you are using Unity, you can hit the Windows button and use that search feature to find it easily. 

Select 'X Server Display Configuration' from the left menu. It is the second option for me.

For me, this showed both my laptop monitor and my external monitor. Click on the external monitor representation and then click the 'configure' button.

Select 'TwinView' - each monitor will show different content. Now hit ok.

Select the representation of your primary monitor (my laptop monitor for example), and tick the box called 'Make this the primary display for the X screen.'

You will now have to click the 'Save to X Configuration File' button. Keep the default settings, and click save.

Note: You may want to back up your settings, but I don't think that is necessary. If you really want to, run this in your terminal to backup your xorg config file to a file called xorg.conf_backup: 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

To undo your changes to xorg.conf, run this:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

After saving your xorg.conf file, you will have to restart the X Server before you can apply your settings. (If you try to click apply, it will tell you this)

I tried to use this command to restart X:

sudo /etc/init.d/gdm restart

However, that seemed to end X and left me with a black screen and a single white underscore at the top left of my screen, and X did not reboot. I then hit my power button (didn't have to hold it down), and my computer rebooted. Others just reboot right away, and that seems to work as well. It also seems possible simply to log out and log back in in order to restart X.

As it was rebooting, my external monitor started working perfectly. I can drag things between monitors, my top bar is on both my laptop and external display, and my resolution and rendering are working perfectly.

Hope this helps!
dfarrell07

---

### Post by dfarrell07 on 2011-08-26
> **blueskyabove said:**
> How do we get these messages to the people who write the code?

Submit bug reports on Launchpad. First, check if a bug report already exists, and add yourself as affected. If none exists (unlikely), create one with as much detail as possible.

---

### Post by blueskyabove on 2011-08-28
Hi dfarrell, thanks for all that.  I tried most of the same things as you and it worked - sort of.  Firstly, the transfer of things between the 2 monitors did not work consistently.  Second, unless the external monitor was attached to the laptop (DEll Vostro 1400 in my case) at startup, I had to repeat the whole process each time I connected the monitor.  

However, I'm absolutely immovable from my original position on this namely, that Ubuntu should be able to support the laptop key combination (Fn + F8 in my case) which allows you to switch and manage output to an external monitor and/or the laptop.  Windows does this just fine and, until the arrival of 11.04, so did Ubuntu.  It's just substandard in terms of specifying the essential functions required of a system and in testing the final result (either they tested for this and found it but thought its absence wasn't important [WHY?] or they didn't test this function at all).  Yet again, Ubuntu will fail as a widely used alternative (and otherwise excellent) operating system until it sorts out these these basic things.

---

### Post by bpb_21 on 2011-08-29
Gotta chime in - I've had the exact same experiences with Ubuntu 11.04 and my Acer laptop with an nVidia GeForce 9650GT card.  I finally got it working at work with an external monitor.  I got home, hooked up a different external monitor and all the sudden Ubuntu can no longer detect my internal bluetooth adapter.  WTF with that?!  It will really make you angry, for sure!
That being said, Linux on the desktop will always be sort of a do-it-yourself option when compared to those more commercial OSes on the market.  If you want everything to just work out of the box, buy a McComputer or an iProduct (and have no choice in configuring it like you want whatsoever).  I'd rather play with Linux, bumps and all, and learn a little in the process.  Even if I do have to trade my previously flawless internal bluetooth adapter for external monitor functionality, Ubuntu has come leaps and bounds over the years I've been experimenting it.  It still remains my main production OS.

---

### Post by bpb_21 on 2011-08-29
Ok, forget what I said earlier. This disappearing Bluetooth adapter is infuriating and all I was trying to do was use an external monitor! I have to change my official position on this: how in the hell did this crazy external monitor fault get past quality control in the 11.04 release?!

---

### Post by blueskyabove on 2011-08-31
Indeed, how DID this external monitor thing get past 11.04 quality control?  I've been hammering on about this all along and it's not good for Ubuntu and its aspirations for greater acceptance.

You would have thought that, by now and without and prompting from infuriated users like ourselves, someone in the Ubuntu Team would have spotted this themselves because it is happening to them and would have immediately done something about it.  But, apparently, not.  Does not inspire confidence and confidence in your operating system is what you need in order to get on with your work or whatever.  Fiddling with the thing to get it to do basic stuff is not acceptable and this is why, sadly, the Mac and Windows 7 win with your average, non IT literate end user where Ubuntu does not.

It's fundamental functionality this external monitor thing and, I repeat, Ubuntu 11,04 should not have been released until this was solved.  The previous version handled all this just fine.

One day, they (!) will sort this AND apologise I guess.

---

### Post by bpb_21 on 2011-08-31
Ok, so I plugged in an external usb Bluetooth adapter and my bluetooth settings were restored.  I tried a third monitor at work and had to restart but did get it working.  Now my internal bluetooth adapter works again.

Lord help me when I go to plug in a projector.

The multiple monitor setup is almost essential for web development/programming, so yes I agree that it's something you'd think everyone would notice right off the bat.

But, now that I've calmed down and can use my bluetooth mouse again, I think Linux will always be a do-it-yourself kind of desktop operating system.  I guess what I'm saying is that you shouldn't expect it to work, at least not without some spare time and effort on your part.  That's probably pessimistic, but then again it's probably a realistic assumption to make.

I'd agree this is why the iOS (and other iProducts) are more popular now with the average end user.

With any Linux distribution you're just going to have to spend some time on forums, blogs, support documents, etc. no matter what, for potentially anything.  That's the price you pay for open source, I suppose.

Now, do my Linux issues compare to issues I've had with Windows?  That's an entirely new discussion.

---

### Post by nrabett on 2011-09-09
Same problem, but curiously only when I use the Nvidia card on my Asus eee 1015pn laptop. When using the Intel integrated graphics card, everything is fine. Apparently, Ubuntu is unable to detect the external screen because Ubuntu incorrectly assumes that the Nvidia driver is not in use (it says "installed, but currently not in use" in the "hardware drivers" section, but I am certain that I use the Nvidia card.)

BTW, how many of us have disabled the Unity desktop?

---

### Post by bpb_21 on 2011-09-09
> **nrabett said:**
> BTW, how many of us have disabled the Unity desktop?

I've finally gotten my nVidia issues ironed out.  Interestingly I'm running Gnome3 (I think, isn't that the newest version that would have been used but for Unity?) and it does pretty good after settling down at first.

Also, I have an old Acer Travelmate C110 that I run Ubuntu 11.04 on (classic interface - hardware can't support Unity) and the external monitor connection works without any special configuration whatsoever.  Just plug a monitor in the VGA connection and it automatically duplicates on both the laptop screen and the monitor screen.  Maybe the dedicated graphics cards are what gives Ubuntu such a hard time?

---

### Post by OpenMouth_os on 2011-09-11
I have a Lenovo W520 (nvidia quadro 1000) and, as many of you, also can't get my second monitor working. Why is it that on Windows, it's just plug and play, and on Linux you have to fiddle around with xconfigs, search the web for solutions etc.. 

It's really really frustrating that the Ubuntu team can't get these BASIC things solved!

Rather than spending so much effort on fancy interfaces (Unity), the Ubuntu developers should focus on creating a stable, more platform flexible and less bugged OS I can fully depend on.   

As much as I like Linux, I have to admit that I had far less trouble with Windows 7 than with Ubuntu 11.04.

---

### Post by livermouse on 2011-09-14
I am having the same issue. I have Nvidia GeForce GT 540M on a m11x alienware notebook, running a fresh install of 11.04. I'm actually using the nouveau drivers instead of the proprietary nvidia drivers, since try as I might I could not get those installed properly. No matter what I do, I cannot get ubuntu to detect an external monitor.

---

### Post by dfarrell07 on 2011-09-15
For Nvidia cards, you will likely have to install the proprietary drivers. I also have a W520 with a 2000M, and I am using dedicated graphics with the proprietary drivers just fine (after the quick fix I described earlier).

Again, instead of ranting on this form that no dev will ever read, go to launchpad, search for the bug you are describing, and mark yourself as affected. If there is no such bug that has already been reported, which is highly unlikely, create the bug report with as much detail as possible. The devs look for bug reports to fix, not deep down in a very old form post. It is your responsibility to report bugs to launchpad if you want them fixed. This is how open source projects work. There is no support staff to rant to, just random people like me that care. You will have to contribute to the effort yourself.

There is no question that the devs tested the **** out of using multiple monitors, and got it working on most/all test systems. To see in detail what is up with that area of work, again, you have to go look at launchpad. It is impossible to support all hardware, especially at the rate it advances, by default. 

To the posters that apparently have not gotten it working yet: Please either post more details of what is wrong, what you have tried, etc. here, or create a new thread on the forms with as much detail as possible, and others will help you troubleshoot it. If you really think you have a bug, do the launchpad process.

---

### Post by finny388 on 2011-09-22
me too

---

### Post by blueskyabove on 2011-09-24
Now posted as a bug in Launchpad: Bug #858046.

---

### Post by melcior on 2012-01-18
> **vulgrin said:**
> Anyone solve this yet?

Having similar issues here. Though I can't even run the Nvidia applet.  If I do what it says and create the nvidia xorg.conf, then X won't start.  Have to go in and remove the conf before I can get back in at all.

Dell XPS 15z.  Really frustrating - all I want to do is be able to make an external monitor the primary and close the laptop.  Something that I've been able to do on Windows for years and years...

The miniDisplay Port usin a conversor has solved my problem. I use a Acer X223HQ and a Startech,com MDP2VGA conexion. You can manage the monitors in System Preferences --Monitors

Hope it helps you

---

### Post by baibhav on 2012-03-05
Hi,
I'm not sure if the above solutions, solved each of your problem.
But the link below helped me to connect to the monitor/project.

[http://www.baibhav.com.np/article/6-computer-tips-a-tricks/32-projector-external-monitor-display-problem-on-ubuntu-1110-solved-.html](http://www.baibhav.com.np/article/6-computer-tips-a-tricks/32-projector-external-monitor-display-problem-on-ubuntu-1110-solved-.html)

---

### Post by cjpetrie on 2012-03-14
Good website but did not help for Sony Vaio X under 11.10.

---

### Post by fillemazendacus on 2012-03-19
To get connected to external monitor (if not answered yet):

1. System Settings &#8594; Additional Drivers
2. Activate '[Recommended] NVIDIA Driver', Restart Ubuntu
3. Dash home &#8594; type 'nv'
4. NVIDIA X Server Settings &#8594; X Server Display Configuration
Try different solutions you like (my HP laptop monitor is disabled and external Monitor works, VGA)

Hope it helps you too!

---

### Post by cjpetrie on 2012-03-29
> **fillemazendacus said:**
> To get connected to external monitor (if not answered yet):

1. System Settings &#8594; Additional Drivers
2. Activate '[Recommended] NVIDIA Driver', Restart Ubuntu
3. Dash home &#8594; type 'nv'
4. NVIDIA X Server Settings &#8594; X Server Display Configuration
Try different solutions you like (my HP laptop monitor is disabled and external Monitor works, VGA)

Hope it helps you too!
Found NVIDIA in the setttings menue and activated it. It seemed to change some configuration file after making a backup. Then I restarted. Black screen - the X server is broken. I can login with command line only. Can anyone please point me to the correct configuration file? I should be able to restore it with emacs.

---

### Post by cjpetrie on 2012-03-29
> **cjpetrie said:**
> Found NVIDIA in the setttings menue and activated it. It seemed to change some configuration file after making a backup. Then I restarted. Black screen - the X server is broken. I can login with command line only. Can anyone please point me to the correct configuration file? I should be able to restore it with emacs.
Found the info in [http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-96-xconfig.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/alt-nvidia-96-xconfig.1.html) and all is well again: that is most things still don't work in 11.10, but at least the X server does.  Think I will be chaning to Mint.

---

### Post by cjpetrie on 2012-04-28
I tried a fresh boot of 12.04. The results were worse. Only a half-screen and the mouse made trails. Finally I have had it with a bloated and botched Ubuntu. Converted to CrunchBang. All problems solved.

---

