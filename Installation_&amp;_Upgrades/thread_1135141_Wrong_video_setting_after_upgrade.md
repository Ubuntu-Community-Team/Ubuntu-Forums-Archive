---
title: "Wrong video setting after upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by irv on 2009-04-24
After upgrading to 9.04. my laptop will not boot. The video is messed up. I went to the recovery mode but there is no setting for fixing video anymore. I ran repair broken packages but that didn't fix the video. is there a command to do this if I drop to the shell prompt.
Thanks for the help.

---

### Post by MidGe48 on 2009-04-24
OK,

I have the same problem.

I upgraded from Kubuntu 8.10 to 9.04 today. well, first day it was available. :)

The upgrade seem to have been successful. It went to its logical end, the reboot without any problems, except a few restart, and the upgrade going to the net rather than using the CD about half way through. I restarted a few times, but it only wanted to go to the net for the files download after about 770 files out of 1900+. 

Ok, after the reboot, it showed  a Kubuntu logo, correctly. Did a disk check (routine) and then continued with he boot. After that it showed me a completely messed up graphic. Unreadable!

Now, I can start a safe boot and get to the command line. The screen looks OK. Even after a startx command it looks messed up. If I stop via the hardware, I, again, get the correct logo showing the progress bar. No problems with the graphic for boot up or shut down, only when trying to run!

My computer is a Dell with a Radeon graphic card. I sort of think the problem is a graphic driver, but I may be wrong. I am a Linux newbie after all.

The question is, first, how can I start running Linux with a basic screen, as I am somewhat handicapped when it comes to command lines, and second, how can I fix this to reflect my screen resolution (1920x1200) as it did for Heron and Ibex?

Unfortunately the upgrade got rid of my past versions of Linux. I must have said yes, or no, when the reverse was needed during the upgrade.

Of course, :( , I didn't backup,  but I am very keen on not loosing my data which I presume is still there, since Linux seems to be running alright!

Thanks for any help that may be forthcoming!

Michel

May any other information be helpful towards me getting some help?

---

### Post by irv on 2009-04-24
> **irv said:**
> After upgrading to 9.04. my laptop will not boot. The video is messed up. I went to the recovery mode but there is no setting for fixing video anymore. I ran repair broken packages but that didn't fix the video. is there a command to do this if I drop to the shell prompt.
Thanks for the help.

I was wrong, there is a xfix on the recovery menu, which I ran but it did not fix the problem. It will not boot into xwindows the graphics are all messed up. It won't even give me the login screen. I am not sure where to go from here.
I am sure there must be others who are having this same problem. We need help if someone has something we can try.
Thanks again

---

### Post by akse on 2009-04-24
I'm having the same problem with xubuntu 8.10->9.04 upgrade.  Loading dialog shows up correctly but when its the time for login screen, everything is messed up.  On top I had black with some weird red vertical stripes and about half of the screen at bottom was completely blue.  I reconfigured the xorg.conf by using the line in the file: sudo dpkg-reconfigure -phigh xserver-xorg.  This command made the red stripes go away but it still about 2/3 blue and the top 1/3 is black :)  The computer is somewhat old and it has some sort of integrated graphics card. Seems to be VIA. It worked ok in 8.10.  Any help is appreciated :)

---

### Post by irv on 2009-04-24
I have spent some time going through the post on the upgrade and there are others having the same problem of sorts, but I have not found any answers to our problem yet. I would hope there is someone out here that can help. I am not new to Linux, but this one really has got me. 
The laptop I am using is a no-name that I have had Ubuntu running on for a long time now with not to many problems. I would like to get this fix so not to do a fresh install. I have everything set just like I want and do not want to have to start all over again.

---

### Post by chzumbrunnen on 2009-04-24
Exactly the same issue here. So at least I'm not alone, that gives me hope that the problem can be fixed soon.
Any help I can give to help the ones who'd like to help me?

I'm on an ASUS noteboog F3JP, but that's about all I know without further help on what commands I should enter...

---

### Post by akse on 2009-04-24
Okey I got my screen fixed now. Not really sure what I did but something to do with the xserver and xorg packages.

First I removed both xorg and xserver packages (sudo apt-get remove xser... etc)

Then I reinstalled them and while browsing the list of xserver packages I saw xserver-xorg-video-via (I had the via integrated chip) so I fetched that package too. Only problem was that the source servers are quite jammed up atm :)

I hope this helps anything.

---

### Post by irv on 2009-04-24
> **akse said:**
> Okey I got my screen fixed now. Not really sure what I did but something to do with the xserver and xorg packages.

First I removed both xorg and xserver packages (sudo apt-get remove xser... etc)

Then I reinstalled them and while browsing the list of xserver packages I saw xserver-xorg-video-via (I had the via integrated chip) so I fetched that package too. Only problem was that the source servers are quite jammed up atm :)

I hope this helps anything.

could you post a step by step how you did this? It would be helpful for me and for others.
Thanks

---

### Post by MidGe48 on 2009-04-24
I seem to have the correct packages installed, afaik. I did an apt -cache search for radeon and it gave me a list of packages that should meet my needs(!?). Are all packages listed, used? Where can I find the actual configuration? 
lshw tells me that for the display: driver is fglrx_pci and the module is fglrx! Does anyone know how to configure, if that is the answer. 
I have a Mobility Radeon HD 3650 [ATI] on the problem computer.
Anywhere else where I could look for the problem solution?
Ought I to report this as a bug ?

I am a newbie that surely is getting to learn a bit about the command line! :redface:

---

### Post by MidGe48 on 2009-04-24
OK, fixed the problem,

The only needed thing was to run the following from the command line:
aticonfig --initial -f

Then rebooting and everything was dandy.  :)

Now, for my backup!  :)

Hope this help others!

Added:  Well the backup will have to wait. I now have the following problem   p, li { white-space: pre-wrap; }  [COLOR=#000000][FONT=DejaVu Sans]
[/FONT][/COLOR]
[COLOR=#000000][FONT=DejaVu Sans]No command arguments supplied![/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]Usage kdesudo [-u <runas>] <command>[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]Kde will now exit...[/FONT][/COLOR]

[COLOR=#000000][FONT=DejaVu Sans][/FONT][/COLOR]
[COLOR=#000000][FONT=DejaVu Sans][/FONT][/COLOR]And everything freezes!? :( [COLOR=#000000][FONT=DejaVu Sans]
[/FONT][/COLOR]

---

### Post by irv on 2009-04-24
> **MidGe48 said:**
> OK, fixed the problem,

The only needed thing was to run the following from the command line:
aticonfig --initial -f

Then rebooting and everything was dandy.  :)

Now, for my backup!  :)

Hope this help others!

Added:  Well the backup will have to wait. I now have the following problem   p, li { white-space: pre-wrap; }  [COLOR=#000000][FONT=DejaVu Sans]
[/FONT][/COLOR]
[COLOR=#000000][FONT=DejaVu Sans]No command arguments supplied![/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]Usage kdesudo [-u <runas>] <command>[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]Kde will now exit...[/FONT][/COLOR]

[COLOR=#000000][FONT=DejaVu Sans][/FONT][/COLOR]
[COLOR=#000000][FONT=DejaVu Sans][/FONT][/COLOR]And everything freezes!? :( [COLOR=#000000][FONT=DejaVu Sans]
[/FONT][/COLOR]

the aticonfig --initial -f command will not work for me because I don't have the ati adapter. I have a laptop and I don't even know what adapter I have. It is a no name. all I know is it worked with ubuntu 8.10. Is there a way I can tell what video adapter I have on-board?

---

### Post by erm27 on 2009-04-24
run the command lspci from a terminal to list your devices.
should return a bunch of stuff, you're obviously concerned with your VGA or Display controllers. Here are mine for example:

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

Linux isn't like Windoze, just cause you don't have a graphical interface doesn't mean you'll have to reinstall everything. You will need to find the right "drivers"/package for your video card, or a generic one just to get you up and running again. But don't give up, I've learned that using Linux there is always another way of getting something working.(If you can boot :) )

---

### Post by MeanStreak on 2009-04-24
Having exactly the same problem as the other posters. 

The upgrade to 9.04 went as expected. At its completion I rebooted and the initial Ubuntu loading screen appeared, followed by a series of other screens with scrambled graphics, before finally displaying a scrambled Ubuntu logo repeated twice on the top half with the bottom half of the screen covered in scrambled graphic lines. 

The recovery options when I boot in recovery mode so far have not worked. Please advise! I cannot access my machine and this is a critical failure!

:frown:

---

### Post by MeanStreak on 2009-04-24
In the command line, I ran "lspci":
VGA: ATI Technologies Inc RV370 5B60 (Radeon X300 (PCIE)]
Display: ATI Technologies Inc RV370 [Radeon X300SE]

Tried running "aticonfig --intial -f" however no supported adapters connected.

---

### Post by erm27 on 2009-04-24
Hey you have the same vid specs as me :)

I haven't tested this locally though, I remotely access my server and tunnel my X sessions over ssh. Anyway, I found a post which references this ATI guide: 

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installation_Guide_for_Ubuntu_Jaunty_.28v_9.04.29]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installation_Guide_for_Ubuntu_Jaunty_.28v_9.04.29")

It's very extensive, but I'm sure you can fix the problem if you follow it.

---

### Post by MeanStreak on 2009-04-24
Yeah I saw we had the same specs after I posted! :)

Thanks for the link - I'll go and investigate.

---

### Post by MeanStreak on 2009-04-24
Hi,

To install the restricted drivers, the universe and multiverse repositories need to be enabled, which I can't do if I can't login.

The open source ones are the ones I really want, however it says they're already working by default and provides no instructions how to confirm/configure this. 

Thirdly, I could try editing the /etc/X11/xorg.conf file however there's no instructions on how I do this. 

I'm really lost. Did you have to do any configuration to get Ubuntu working with your ATI specs?

---

### Post by erm27 on 2009-04-24
well, I don't boot into the graphical interface
I ssh into my server and then forward an X session
I use a separate computer to connect
The catalyst driver isn't used, so no fancy graphix or effex
It really just looks like a case of bad drivers . .. 
I'm going to try and install the radeon drivers, or the ati (simple) graphics, if I really have to, I'll try to get VESA working. (16 bits ?)

#xorg.conf======================================

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier  "Generic Keyboard"
#	Driver      "kbd"
#	Option	    "XkbRules" "xorg"
#	Option	    "XkbModel" "pc105"
#	Option	    "XkbLayout" "us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier  "Configured Mouse"
#	Driver      "mouse"
#	Option	    "CorePointer"
#EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	[COLOR="Red"]Driver	"ati"[/COLOR]
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1024x768"
	EndSubSection
EndSection

---

### Post by MeanStreak on 2009-04-24
Thanks. I'm really not familiar with editing my Xorg file, etc. so detailed step-by-step instructions on a fix would be really helpful. eg. boot into recovery mode, select "....'" menu, then when the command line comes up type "....". Sorry, I know this takes time, but it's the best way to spread help to a lot of users who may be new to Ubuntu.

---

### Post by MeanStreak on 2009-04-24
It's working now. I booted into Recovery Mode, selected the command line option and ran the following command:
```
apt-get remove xorg-driver-fglrx
```

Rebooted as normal and can now login. Phew.

---

### Post by erm27 on 2009-04-24
AHHhhhhh, it looks like the fglrx driver (Catalyst?) isn't working for X300? 

Would like to see if anyone else with_out_ ati graphics is having trouble.

---

### Post by sigmabetatooth on 2009-04-25
I am having potentially similar problems with my display.  It looks as if it is not detecting that I have a widescreen monitor on my laptop and therefore shows black bars on both sides.

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

---

### Post by irv on 2009-04-25
> **sigmabetatooth said:**
> I am having potentially similar problems with my display.  It looks as if it is not detecting that I have a widescreen monitor on my laptop and therefore shows black bars on both sides.

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

Mine is almost the same. It is an Intel but different model number. This one always worked with other releases of Ubuntu.  
> 00:02.0 VGA Compatible Controler: Intel Corporation 82852/855GM Ingrated Graphice Device (rev 02)
00:02.1 Display Controller: Intel Corporation 82852/855GM Ingrated Graphice Device (rev 02) 

---

### Post by irv on 2009-04-25
OK, this worked for me also. I ran:
Code:
> apt-get remove xorg-driver-fglrx
Rebooted and "WALA" I was back running in Ubuntu 9.04. Now to check it out and make sure everything else is working.
My question is, what is xorg-driver-fglrx anyway, and why wasn't it removed on installation. This might give a lot of users this same problem after installing 9.04.
Thanks for all the help in this post. If this works for all then we can mark this one solved.

---

### Post by alphacrucis2 on 2009-04-25
> **erm27 said:**
> AHHhhhhh, it looks like the fglrx driver (Catalyst?) isn't working for X300? 

Would like to see if anyone else with_out_ ati graphics is having trouble.

Everyone who has one of the cards that ATI dumped from Catalyst 9.4. The dumped cards are not compatible with the fglrx that is available for jaunty. You can't run the old Catalyst 9.3  fglrx driver either, as it won't work with the x.org server 1.6 that is in jaunty. You have to use the open source driver. My card was actually one of the ones still supported in Catalyst 9.4 but I still had a problem which was cured by manually running 

```
aticonfig --initial -f
```

from the recovery console. 

It is always a good idea to browse through the testing forum to see what problems people were having with the alpha & beta versions before jumping into an upgrade to a new release.

---

### Post by erm27 on 2009-04-25
> **irv said:**
> OK, this worked for me also. I ran:
Code:

Rebooted and "WALA" I was back running in Ubuntu 9.04. Now to check it out and make sure everything else is working.
My question is, what is xorg-driver-fglrx anyway, and why wasn't it removed on installation. This might give a lot of users this same problem after installing 9.04.
Thanks for all the help in this post. If this works for all then we can mark this one solved.

Interesting because xorg-drivers-fglrx is a driver for ATI video cards ONLY. Did you manually try to install this? Were you prompted with an alert that said the "ATI driver wasn't fully functional with 9.04, do you want to install anyway. Yes or No?" Then perhaps you hit Yes? Otherwise I don't understand why the update tried to use a different vid driver. Nice job resolving your issue guys. :guitar:

---

### Post by erm27 on 2009-04-25
> **sigmabetatooth said:**
> I am having potentially similar problems with my display.  It looks as if it is not detecting that I have a widescreen monitor on my laptop and therefore shows black bars on both sides.

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

Have you tried to manually edit your xorg.conf file to include the resolution you would like to use? This might help. Or have you used the Display utility under Preferences?

---

### Post by irv on 2009-04-25
> **erm27 said:**
> Interesting because xorg-drivers-fglrx is a driver for ATI video cards ONLY. Did you manually try to install this? Were you prompted with an alert that said the "ATI driver wasn't fully functional with 9.04, do you want to install anyway. Yes or No?" Then perhaps you hit Yes? Otherwise I don't understand why the update tried to use a different vid driver. Nice job resolving your issue guys. :guitar:

No I didn't manually try to install it? And I don't remember being prompted with an alert that said anything about a "ATI driver". It was a clean Install with out errors. It did take a long time to do the upgrade because it timed out downloading the files but I just restarted the upgrade and it went well. I just let it run all night and finished in the morning.

---

### Post by bobonthenet on 2009-04-26
```
apt-get remove xorg-driver-fglrx
```

also worked for me, don't really know what that is but I'm glad it worked.  The sign on screen looks amazing btw.

---

### Post by irv on 2009-05-04
I am just going to say this thread is solved so we can put it to rest.

---

### Post by vajeen on 2009-05-22
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

please help to correct my resolution.....1024x768 is the highest available now..but i used 1152x864 earlier version.

---

### Post by irv on 2009-05-23
> **vajeen said:**
> $ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

please help to correct my resolution.....1024x768 is the highest available now..but i used 1152x864 earlier version.

I don't know if this will help but check out these threads:
[URL="http://ubuntuforums.org/showthread.php?t=1153437"]
http://ubuntuforums.org/showthread.php?t=1153437[/URL]
or
[http://ubuntuforums.org/showthread.php?t=1164109&highlight=resolution]("http://ubuntuforums.org/showthread.php?t=1164109&highlight=resolution")
Its a place to start.

---

### Post by vajeen on 2009-05-27
thanks man it helped..............

---

### Post by MonochromeNight on 2009-07-05
> **MidGe48 said:**
> OK, fixed the problem,

The only needed thing was to run the following from the command line:
aticonfig --initial -f

Then rebooting and everything was dandy.  :)



Worked perfectly for me, I even got compiz working. Thanks!

---

### Post by crankyoldbugger on 2009-07-09
I'm having a similar problem, where my login screen is garbage.  I've looked over several of the posts here, they seem to have good ideas but I don't know how to get to a command prompt if I am unable to log in.  Any suggestions?

---

### Post by irv on 2009-07-09
> **crankyoldbugger said:**
> I'm having a similar problem, where my login screen is garbage.  I've looked over several of the posts here, they seem to have good ideas but I don't know how to get to a command prompt if I am unable to log in.  Any suggestions?
To get to a command prompt: If you only have Ubuntu installed, when the grub starts to load hit the [ESC} key and arrow down to failsafe boot. When the next menu comes up arrow down to boot to a command line. Or is it is a video problem the last option on this menu is fix video.
If you have a dual boot, when the grub comes up arrow down one on the menu and boot with failsafe, and do the same as above.

---

### Post by crankyoldbugger on 2009-07-09
Thanks for your response, but unfortunately my problem is a bit more stubborn.
 
I tried the "Fix Video" option, but it didn't do anything useful.
 
Is there some sort of parameter I can put in the boot command lines?  I can edit those (although that's about all that I can do...)

---

### Post by crankyoldbugger on 2009-07-09
Perhaps I can clarify a bit more...
 
I have a dual boot set up with XP on the other side.
 
I can get to the Ubuntu Recovery Menu via the Grub thing.
 
In there, "xfix" is listed, but after running it several times I still get the garbage login screen (I'm assuming it's the login screen, by the way.. I have no idea for sure what it is.  It's like looking at a Pay-TV channel that you never paid for.)  Once I'm on this screen I have no options but to kill the power.
 
I should mention that I had to use the AMD64 Alternate CD to install and the standard Desktop CD also failed to display properly.
 
My machine is obviously running and AMD processor.  It's an HP with an ATI Radeon HD2600 video card (AGP).
 
I know that I had older versions of Ubuntu (and also Fedora) loaded ok, but in some cases I had to edit the boot commands (can't remember what I had to do exactly, unfortunately...)
 
As you can probably assume, I really know nothing about Linux.  I appreciate your help!

---

### Post by irv on 2009-07-09
> **crankyoldbugger said:**
> Thanks for your response, but unfortunately my problem is a bit more stubborn.
 
I tried the "Fix Video" option, but it didn't do anything useful.
 
Is there some sort of parameter I can put in the boot command lines?  I can edit those (although that's about all that I can do...)

Goto: [http://ubuntuforums.org/showthread.php?t=364201]("http://ubuntuforums.org/showthread.php?t=364201")
If you do this from the command you can use vi and not gedit. If you know how to use vi. If you can boot with the live CD, mount your filesystem drive, It should be sda1 and then you can do what is said in the post I gave you a link too.

---

### Post by crankyoldbugger on 2009-07-10
Well that was fun...
 
She's working now.  All I had to do was boot to the recovery console, then get a command line prompt.
 
From there, use VI to add the following to my xorg.conf:
 
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
             EndSubSection
EndSection
 
Rebooted, and got a bunch of errors about X server sessions, which I promptly ignored.
 
This would at least allow me to see the login screen, so long as I selected "run in basic display for this session only" (or whatever it said).
 
Opened up a terminal and ran
 
sudo aticonfig --initial -f
 
Then, I went to ATI.com and downloaded the appropriate drivers.
 
To install the driver, I again had to use sudo, of course.
 
Rebooted and whamo! A beauty screen.
 
Thanks irv and everyone else for your help!

---

### Post by irv on 2009-07-10
Glad to see you got everything going. I know what you went through, I had to do it a few time myself in the last few years.
Yesterday I had a server HD crash and it was an all day affair getting it going again. 5 Hours restoring files also.

---

