---
title: "Anyone tried Ubuntu on Dell Latitude D620 ?"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by jede on 2006-04-15
Hi,

I'm going to order the new Dell Latitude D620 notebook. I need to use it with Linux. Has anyone experience with installing Ubuntu Linux (Breezy or Dapper) on it? Would be nice to get some feedback...

Bye,
Stefan

---

### Post by moephan on 2006-04-15
FWIW, I know they're not exactly the same, but I have a Dell Latitude that says c510/c610 on the label. I bought it reconditioned. Under breezey everything, incuding wireless, worked without tweaking, except sound input.

D'oh, I should have mentioned that my computer didn't come with a wireless card, and I had to turn off the "tap to click" feature on the trackpad because it was super annoying. I turned it off in xorg.config

---

### Post by jede on 2006-04-16
[QUOTE=moephan]FWIW, I know they're not exactly the same, but I have a Dell Latitude that says c510/c610 on the label. I bought it reconditioned. Under breezey everything, incuding wireless, worked without tweaking, except sound input.

D'oh, I should have mentioned that my computer didn't come with a wireless card, and I had to turn off the "tap to click" feature on the trackpad because it was super annoying. I turned it off in xorg.config[/QUOTE]

Thanks for the reply but the new D620 contains completely other components then older versions. And they are very new, that's why I'm asking for some experience.
For example it contains the Intel GMA 950 onboard graphic chipset and the  Intel 3945ABG wireless card.

---

### Post by dragonflyFZX on 2006-04-18
hi, 

i just received my dell latitude d620 and immediately installed dapper on it :D 

I am still strugling with it, but that has probably much more to do with me knowing very little about hardware, and on top of that being an absolute beginner in linux.  

But here are my experiences:  The installation from CD went very smooth.  After rebooting, X failed to start, so i had to go into a terminal using ctrl+alt+f1.  A simple 

```
sudo dpkg-reconfigure xserver-xorg
```

was sufficient to get X going, so i could proceed in KDE.  Sound was working out of the box, and i get a message at startup that a bleu tooth adapter has been found (could not try it cause i dont have bluetooth devices (yet)).  I also immediately upgraded to the 686 kernel with smp to get the two cpus working (i am not sure this is really needed, cause i read somewhere that dapper has standard support for more than 1 CPU).  After installing gkrellm, i found that i have 2 cpu's and they are both working.  During the installation, my ethernet card was also detected and i was surfing the internet without problems (i have adsl).

So far so good.  One thing that was bothering me was the graphics.  It wasn't looking as nice as dapper on my previous laptop, and definetly not as nice as in windows on the d620.  Also, it seemed the widescreen was not supported.  It took me a while to fix it, but it now works seamlessly (see [http://ubuntuforums.org/showthread.php?t=160521]("http://ubuntuforums.org/showthread.php?t=160521") on how to do it.)  

Now i am trying to get the wifi working.  I am getting somewhere using this post:

[http://ubuntuforums.org/showthread.php?t=140085&highlight=wireless+dell]("http://ubuntuforums.org/showthread.php?t=140085&highlight=wireless+dell")

but still not there.  Using the wifi lan manager in KDE, i keep getting the message that i am out of range, tho if in windows, it seems that i am in range of several networks.  But again, this maybe has to do with the fact that i have absolutely no experience with wireless connections, and i am just trying out various things without knowing what i am doing.  But hey, that is the way to learn things, right?

I haven't tried to burn cds or dvds yet.

To sum up, i am pretty sure that i will get everything working in the near future.  We just need more people buying this laptop and installing ubuntu on it :D

---

### Post by jede on 2006-04-18
Hi dragonflyFZX,

thank you for your experience report. That sounds really good. Graphics and sound are supported, that's great. I think WLAN will also be working, the drivers are available and it's a configuration question. Maybe it's not working out of the box, but this is OK.

I still have some questions:
(1) Does the function keys, especially for screen brightness and volume are working? On my last laptop they have not, it was terrible to have the brightness always on maximum...
(2) Is the fan and heat management working in linux properly (as it does on Windows)? On some laptops the fan will always or never run on linux or the laptop gets very hot ...
(3) Do you have testet suspend to disk or suspend to rum? (not so important) 

All in all - are you happy with this laptop or do you have some general problems with it? Unfortunately there are not many test available yet ...

Thanks,
Stefan

---

### Post by jede on 2006-04-19
Hi dragonflyFZX,

one more question: in the reviews they often say that the display quality is not very good. The brightness is not very high and the screen is blurry on fast scenes or when playing games.
What's your opinion about the display? Is it sufficient for normal usage and for watching pictures and movies? Or does it only looks good in dark environment ?

Thanks,
Stefan

---

### Post by dragonflyFZX on 2006-04-22
hey jede,

i have to admit that i never use all these things.  Your questions are real eyeopeners to me.  I never even noticed those function keys to adjust the brightness on my laptop, let alone i have ever used them.  damn they are handy :rolleyes: 

So the brightness function keys work out of the box on dapper.  The laptop even has an ambient light sensor.  I guess that is working to (i will confirm this later when it is dark :)   The volume up down mute buttons (which are seperate buttons) do not work, but again, i have not *really* tried to get them working.

The heating and fan, gkrellm says the cpu is about 6O degrees, and to be honest, i have never heard the fan.  But then again, with two cpus (and i have chosen the 2Ghz version) my laptop has not really been overstreched yet.

For the graphics, now that i get the screen working in the right resolution, i am very happy with it.  I do not play games, so cant help you on that, but saw a movie yesterday, and didnt notice any blurring.

All in all, i am extremely happy with my new machine. 

Oh yeah, i bought a bleutooth mouse and got it working using this post

[http://www.ubuntuforums.org/showthread.php?t=87919]("http://www.ubuntuforums.org/showthread.php?t=87919")

but not entirely, cause i have to repair it when it goes in sleep mode.  But as you prob noticed, i am a busy man, and have way too little time to play around with my computer...

---

### Post by jede on 2006-04-23
Hi dragonflyFZX,

sounds great. Unfortunately Dell has problems to  deliver the model I want to have (Intel has not enoug Core Duo's :-)
By the way: which type of display do you have: the 1280x800 or 1440x900 ?

Bye,
Stefan

---

### Post by dragonflyFZX on 2006-04-23
i have the 1440x900

BTW: when i ordered my laptop, expected time of delivery was more then one month later.  However, in practice, the laptop was delivered in about one week.  Given my impatience, i was very pleased :D

and oh yeah, i burned a dvd with it today, using k3b (doing serveral other things in the process).  It just worked.

---

### Post by jede on 2006-04-23
Interesting, they seem to deliver quite fast. I've heard it from other people too.

Thanks,
Stefan

---

### Post by charles.figura on 2006-04-27
Hey, dragonflyFZX -

You mentioned that your display on your D620 is working now.  Have you got DRI/DRM enabled?  Have you tried measuring the frame rate with glxgears?  (Yeah, I know, it's not a solid benchmark, but its suggestive, at least...)

I've been looking at the D620 as a replacement for my Presario2500, and the only
thing holding me back right now is the D620's graphics card.

Thanks!

---

### Post by dragonflyFZX on 2006-04-28
[QUOTE=charles.figura]Hey, dragonflyFZX -

You mentioned that your display on your D620 is working now.  Have you got DRI/DRM enabled?  Have you tried measuring the frame rate with glxgears?  (Yeah, I know, it's not a solid benchmark, but its suggestive, at least...)

I've been looking at the D620 as a replacement for my Presario2500, and the only
thing holding me back right now is the D620's graphics card.

Thanks![/QUOTE]

ok, you have to help me here.  Dont have a clue what you are talking about.  How do i know if DRI/DRM is enabled?  How do i measure the frame rate?

I told you i am a noob if it comes to graphics.

---

### Post by charles.figura on 2006-04-28
[QUOTE=dragonflyFZX]ok, you have to help me here.  Dont have a clue what you are talking about.  How do i know if DRI/DRM is enabled?  How do i measure the frame rate?

I told you i am a noob if it comes to graphics.[/QUOTE]


No worries.
A few things to check.  First, take a look at your xorg.conf file.  It should have a couple of lines.  There should be a 'load "dri"' up where you load modules, and probably down towards the end there should be a "DRI" section, with a line that says 'Mode 0666'. 
I think Ubuntu should have set that up automatically.

You can take a look at your infocenter.  The XServer section should list XFree86-DRI under your the 'supported extensions ' subsection.

There's probably a few other things to look for, but that should give you a start.  Of course, the easiest thing to do is to type 'glxgears -printfps' in your shell window.

Assuming there are no errors, it should pop up a little window with three gears rotating around.  If you sit and wait, it will print a frame number in your shell window, telling you how many frames were rendered per five seconds, and the average number of frames per second.  Don't resize the glxgears window, and don't cover it up.  Wait a few iterations - the first few are a bit slower.

Good gear numbers... on my desktop with a decent GeForce video card, I can get a couple thousand frames per second.  On my presario with an ATI Radeon IGP340M, I'm lucky to get about 300 fps.

Again, it's not  a solid benchmark, but it gives you an idea. I also usually try the celestia astronomy package, and see how smoothly it works at fullscreen.  That's usually enough to tell me how well the video will work for me.

Oh - another, unrelated question.  How much battery life have you been getting from your D620?  And what size battery do you have with it?

Thanks!

---

### Post by dragonflyFZX on 2006-04-29
okay,

there is a "DRI" section, with a line that says 'Mode 0666' at the end of the xorg.conf file.  However, there is no 'load "dri"' up where you load modules.

Furthermore, there is no XServer section listing XFree86-DRI under your the 'supported extensions ' subsection.

As for the framerate
1258 frames in 5.0 seconds = 250.444 FPS
1207 frames in 5.0 seconds = 239.240 FPS
6038 frames in 5.0 seconds = 1206.278 FPS
6210 frames in 5.0 seconds = 1233.966 FPS
6677 frames in 5.1 seconds = 1317.393 FPS
6700 frames in 5.1 seconds = 1318.663 FPS
6713 frames in 5.1 seconds = 1325.575 FPS
4781 frames in 5.3 seconds = 904.100 FPS
4597 frames in 5.1 seconds = 909.746 FPS
6535 frames in 5.0 seconds = 1306.102 FPS
6853 frames in 5.1 seconds = 1352.791 FPS
4487 frames in 5.3 seconds = 852.405 FPS
1244 frames in 5.0 seconds = 248.800 FPS
1724 frames in 5.0 seconds = 344.767 FPS
4440 frames in 5.3 seconds = 834.380 FPS
1212 frames in 5.2 seconds = 234.945 FPS
1205 frames in 5.2 seconds = 233.112 FPS
2533 frames in 5.0 seconds = 503.278 FPS
6560 frames in 5.0 seconds = 1311.030 FPS
6447 frames in 5.0 seconds = 1285.673 FPS
6753 frames in 5.1 seconds = 1323.860 FPS
4010 frames in 5.4 seconds = 739.115 FPS
1325 frames in 5.5 seconds = 240.660 FPS

dont have a clue what this means.  I have to admit i dont know anything about graphics and i was already very happy i got the widescreen going.  But if you can help me get things better/faster cause you think my setup is not ok, please tell me.  
Oh yeah about the battery life, again, i use the laptop for work, so i have not really expermented with it.  Sorry!

---

### Post by jede on 2006-05-08
Hi, this is just a little status report:

I got my D620 this weekend and I installed Ubuntu Dapper Drake Beta2 on it. The installation worked very fine. I just needed to install the 915resolution package (and configure it, very easy) and add the linux-image-686 for dual core (smp).

Graphics works. 3D acceleration also.
Sound works.
Network works.
Bluetooth works.
Special keys works. (Sound volume, Mute, Screen brightness).
Suspend to Disk works. Wow !!!
ACPI for fans, battery status and so on works.
PCMCIA works.

I didn't tried WLAN yet, but it should be possible, the IPW3945 is supported now. I've also not tested infrared yet.

The only strange thing is a silent buzzing when it runs on battery. When I connect it to power then this buzzing sound is gone. This is not the case in Windows XP. Does somebody has the same problem ?

All in all I must say this is a very nice laptop and the Linux support is very good.  

The quality of this laptop is also very solid. Only the keyboard sounds a little bit "cheap", the keys are a little bit loosen. Is it the same for other users too ?
But the ergonomic of the keyboard and the touchpad is OK.

Bye,
Stefan

---

### Post by dragonflyFZX on 2006-05-12
my wireless network is working very well.  IPW3945 is now indeed supported.  But tell me, how did you get the special keys working (the sound volume and the mute buttons that is, screen brightness works).  Furthermore, how do i check if i have 3d acceleration?  How did you setup your graphics, cause i think i can get more out of it.

---

### Post by jede on 2006-05-12
Hi,

the special buttons for volume and mute waorked out of the box. They are bound by default to the appropriate gnome-functions. Are you using KDE? Maybe it's not configured by default there...
Graphics and 3D support worked out of the box. The only thing was the 915 resolution trick you allready know. To test your 3D you simply need to install and start e.g. planetpenguinracer, formally known as tuxracer. You will see whether you have 3D acceleration or not ...

How have you installed WLAN? Are you installed it manually or do you using some special Dapper packages ? Are you using WPA and network-manager ?

Bye,
Stefan

---

### Post by jede on 2006-05-12
I've got also WLAN to work now. I just installed the packaes network-manager and network-manager-gnome. But WLAN works only with WEP encryption, it's not possible to connect to WPA networks, it reports that it's unsupported by the hardware.
Does WPA works for someone else ?

Bye,
Stefan

---

### Post by DavidFourer on 2006-05-13
> Dell Latitude that says c510/c610 Under breezey everything, incuding wireless, worked without tweaking, except sound input.

I had to turn off the "tap to click" feature on the trackpad because it was super annoying. I turned it off in xorg.config

Please tell me how to turn off the touch in trackpad.  I found a file called xserver-xorg.config.  Searching the file for "touch" I found:
[COLOR="Blue"] if [ -e "$XF86CONFIG" ] && [ ! -e "$XORGCONFIG" ]; then
    touch "$CONFIG_AUX_DIR/.migrateconfig"[/COLOR]  Am I on the right track?
I have trouble editing files as root and need a primer.  Seems I didn it once or twice and forgot how.[COLOR="Green"]OK, I think I got gedit running as root, but have not changed anything  I found /etc/x11/xorg.conf/  I found another old thread [http://ubuntuforums.org/showthread.php?p=1012109#post1012109](http://ubuntuforums.org/showthread.php?p=1012109#post1012109)  Still working[/COLOR]

Thanks

---

### Post by charles.figura on 2006-05-13
Hooplah.  My D620 came yesterday, and by last night I had my wireless working, accelerated graphics working.  Linux is just getting too easy to install, even on a laptop.  My wife suggests that I need to install an old redhat version first then upgrade, just to give a challenge.

I had trouble getting wireless up until I saw someone's post that the latest ieee80211 version didn't seem to work with the intel hardware.  I backed off on that and it's working fine.

Accelerated graphics is great.  I'm getting a steady 1790-1810 fps on glxgears.  I don't think I've ever seen frame rates like that on a laptop before.

BUT - I do have a problem.  My suspend to disk doesn't work (though it did a couple of times, but not lately) - it seems that the screen never comes back.  I think that the system has restored, I just can't see it.
The other thing (and this is weird) is that the screensaver only show up on the upper half or so of the screen - completely blank in the lower half.

My video config - I installed the 915resolution package and replaced the existing 5a with a 1440x900 mode.  I also configured my xorg.conf to load the  i810 driver, and added a 24bit 1440x900 mode to the display section.  That made glxgears fly (and celestia is beautiful), but I suspect that may have goobered the suspend.  Jede - you mentioned that your suspend-to-disk was working.  What's your config like?  

Anybody have a recommendation on this?

Thanks.

Oh - DragonflyFZX - when you tried glxgears, you said you didn't have a "load dri" in your xorg.conf.  Mine does, but it set it up automatically.  Try adding it and restarting your xserver, and see what your gears do - I think that should help you get moving faster.  Maybe break your suspend-to-disk.  If it does, maybe that's what I need to *undo*.

[QUOTE=jede]
...

Suspend to Disk works. Wow !!!
...

The only strange thing is a silent buzzing when it runs on battery. When I connect it to power then this buzzing sound is gone. This is not the case in Windows XP. Does somebody has the same problem ?

[/QUOTE]

Yeah, I seem to note this too.  It's not too bad, but I see it.  Hear it, rather.

---

### Post by jede on 2006-05-14
Hi Charles,

I didn't have the problem with the screensaver, but my display has the 1280x800 resolution.
Thanks for the hint with the ieee80211 driver, I'll try that...

Bye,
Stefan

---

### Post by zachtib on 2006-05-18
does the intel wireless card support wpa yet?

---

### Post by dragonflyFZX on 2006-05-18
hey people,

nice to  see some more people around with this laptop.  and putting ubuntu on it, and loving it.  makes life of a beginner interesting.  Thanks charles to suggest adding the load dri in the xorg.conf.  Now the gears are going smooth.  However, would you mind sharing your xorg.conf, cause my framerates are still about 200 below yours.

Oh and for the special keys, i indeed run kde, and there it does not work out of the box...

---

### Post by thepurplemonkey on 2006-05-19
Is anyone running the D620 spanning screens with Xinerama? I can't get it working.](*,)

---

### Post by howardcheng on 2006-05-19
I just got my D620 and installed Breezy Badger.

I have had no luck with the display whatsoever, even after looking at the advices here and using 915resolution.

I don't have networking working either so it's hard to post the logs, but I'll type in as much and as accurately as I can.

First, output from lspci:
> 
0000:00:02.0 VGA Compatible controller: Intel Corp.: Unknown device 27a2 (rev 03)
0000:00:02.1 Display controller: Intel Corp: Unknown device 27a6 (rev 03)


I can get it to X to start using vesa, but not i810.  If I use i810 it says:
> 
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) No devices detected.

Fatal server error:
no screens found

If I used PCI:0:2:1 instead than it complains about PCI:0:2:0.  I can't figure out how to put both.

Help would be greatly appreciated.

---

### Post by RatCatcher on 2006-05-20
Hi there,

I'm having exactly the same problems with breezy badger on a Latitude D820  - any help greatfully received!!

---

### Post by RatCatcher on 2006-05-20
[QUOTE=howardcheng]....I can get it to X to start using vesa, but not i810....[/QUOTE]

Hi Howard,

How do you choose which driver to use? How do I select vesa?

---

### Post by RatCatcher on 2006-05-20
OK - I am writing this from Ubuntu running on my D820, however, I cannot get the wireless going and I am running with the VESA driver like Howard, not the proper i810 driver. I also have loads of unknown devices in device manager. Where do I go next.....?

---

### Post by jede on 2006-05-20
Why you are forced to run Breezy? Dapper seems to be very solid and stable for me...

Bye,
Stefan

---

### Post by howardcheng on 2006-05-20
Okay, I got X running on Dapper.  Now I got to try and get everything else to work.  Thanks.

---

### Post by howardcheng on 2006-05-21
The system beep (in console and terminals) are extremely loud.  I have looked everywhere to try to reduce the volume but with no success.  I can't seem to find anything that controls the PC speaker.  I don't want it off.  I just want it in lower volume.  Any hints?

---

### Post by jede on 2006-05-21
You can use the "xset b" command. I prefer to switch it off, so I added the command "xset b off" to the autostart session commands of Gnome. It was too loud :-(
You can also specify options for making it not so loud, see the man page.

Bye,
Stefan

---

### Post by howardcheng on 2006-05-21
Now I am trying suspend-to-ram and suspend-to-disk.  Neither of them worked.  When it wakes up the screen is blank.  Switching between virtual consoles with Ctrl-Alt-F* give garbled screens, and it didn't respond to anything (including Ctrl-Alt-Del).  The only way out is the power button.

Has anyone gotten that to work?

---

### Post by jede on 2006-05-21
I can report that SuspendToDisk works without any problem on Dapper out of the box.

Stefan

---

### Post by dragonflyFZX on 2006-05-21
howard,

are you running kubuntu?  It is not working on my machine either.

---

### Post by howardcheng on 2006-05-21
I'm running Dapper Beta 2.   Suspend doesn't work for me (either to disk or ram).

---

### Post by howardcheng on 2006-05-21
xset doesn't work for me.  I can turn it off, change the pitch, and change the duration.  But the first parameter doesn't do as advertised: it changes the duration and not the volume.

---

### Post by charles.figura on 2006-05-22
[QUOTE=dragonflyFZX]hey people,

nice to  see some more people around with this laptop.  and putting ubuntu on it, and loving it.  makes life of a beginner interesting.  Thanks charles to suggest adding the load dri in the xorg.conf.  Now the gears are going smooth.  However, would you mind sharing your xorg.conf, cause my framerates are still about 200 below yours.
[/QUOTE]

dragonflyFZX -

Sorry that I didn't respond to you sooner.  I had an ugly mishap - after editing my bios, I found that I couldn't boot.  At all.  Couldn't get into bios configuration, anything - instead got a 'Time-of-Day clock stopped' error.  Talked to the folks at Dell and they said something was goofy with the bios (not my fault) and sent me a new one, just got it today and I'm up and running, finally.


Here's my xorg.conf.  Is there a better way than just pasting this in the window here?

Oh - and I'm trying something new in a moment.  There's a cool link for  XGL - using direct hardware acceleration for GL.  It's supposed to open up whole new avenues of eye-candy.  I'll let you know how that goes.  Pray that I don't end up with another brick.

xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"Protocol"		"ExplorerPS/2"
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
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
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
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by charles.figura on 2006-05-22
[QUOTE=dragonflyFZX]my wireless network is working very well.  IPW3945 is now indeed supported.  But tell me, how did you get the special keys working (the sound volume and the mute buttons that is, screen brightness works).  Furthermore, how do i check if i have 3d acceleration?  How did you setup your graphics, cause i think i can get more out of it.[/QUOTE]

Here's what I did for the volume keys.  It works great.
First: make a file in you bin directory named 'hotkeys_define':
```

keycode 174=XF86AudioLowerVolume
keycode 176=XF86AudioRaiseVolume
keycode 160=XF86AudioMute

```

If you type: (inserting the appropriate path)
xmodmap /path/to/bin/hotkeys_define
X will associate those names (XF86...) with those keys.  If you type
xev
and press the buttons, it will show you those names associated with them.

Now - do an
apt-get install xmms-XF86audio
It does require xmms, but you don't have to use xmms to make this work.  I like xmms, so that's not a problem for me.  Now try out the volume keys again.  You should get a quick pop-up in the middle of the screen that tells you what you did.  Shiny.

Lastly - make sure that those keys get associated with those names next time you boot up.  Create a file in ~/.kde/Autostart named 'hotkeystart':
```

#!/bin/bash
xmodmap /path/to/bin/hotkeys_define

```

Presto.  You should be golden.

Again - this will control your master volume, whether or not you're running xmms.  And I like xmms more than kaffeine.  Not more than caffeine, but that's a different story.

---

### Post by charles.figura on 2006-05-22
[QUOTE=howardcheng]I'm running Dapper Beta 2.   Suspend doesn't work for me (either to disk or ram).[/QUOTE]

Man, I'm frustrated by suspend AND hibernate.  Before my bios whacked, Suspend was working pretty well.  Now I can't get it to work at all.  When I try to wake it up, the monitor never wakes up.  I've tried deactivating DPMS (as per a different thread), but nothing goes.  Funny thing is, the computer seems to be alert, at least somewhat - if I hit capslock or numberlock, it toggles the little light.  But no display.

And somebody check this out - if I try to hibernate, that too does not work.  When the computer boots up, it doesn't see the hibernate image in swap - just boots up normally.  AND since there's (supposedly) a hibernate image still sitting in swap, the computer doesn't see the swap partition.  If I take a look at the system info -> memory, there's no swap available.  I can get it back by doing a 'sudo mkswap /dev/sda5' (sda5 being my swap partition) and rebooting.

Has anyone else seen this behavior?  It's as if the computer knows how to write a hibernate image, but doesn't know how to read one.
Ug.

Howard, dragonfly, do you guys have the 1440x900 screen?

---

### Post by jede on 2006-05-22
Hi Charles,

I'm looking forward to hear about your XGL experiences. It will be interesting to see if the performance of the internal card is sufficient ...

About you bios timing problem:
I also have problems: the internal clock often changes to invalid values whenever I boot into Windows XP. With Linux it works. Hopefully my machine will not get broken as yours ...
Does the Dell people say that this is a problem on all D620's ?

Bye,
Stefan

---

### Post by charles.figura on 2006-05-22
[QUOTE=jede]Hi Charles,

I'm looking forward to hear about your XGL experiences. It will be interesting to see if the performance of the internal card is sufficient ...

About you bios timing problem:
I also have problems: the internal clock often changes to invalid values whenever I boot into Windows XP. With Linux it works. Hopefully my machine will not get broken as yours ...
Does the Dell people say that this is a problem on all D620's ?

Bye,
Stefan[/QUOTE]

Hm.  Well, I wish I had more fun to report on XGL.  Here's the link that I was using:
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

It was simple enough to do, but when I fired it up, it didn't work right.  I had no window management - no window frames, nothing worked right.  Now, I'll admit, I *did* get to see some fun accleration, but the system was not usable.  I'll probably play around with it some more over the next few days.  I do know some guys with an i810 series display driver who are using it successfully.

As for the bios - I couldn't get a clear answer on that.  I think this may have just been a one-time problem.  Here's a full account of what happened:
1.  Got the computer a week ago Thursday last & immediately installed Dapper.  Worked great.
2.  Over that weekend, tweaked and installed and transferred files.  At some point, started having a trivial problem with GRUB.  The 3 second countdown wouldn't.  It stuck at '3 seconds' until I hit escape to enter the menu.  When I did that, it would put me in the menu & I could boot up just fine.
3.  Did some research, found that some others had seen that problem (NOT with the D620).  Apparently some garbage from bios wasn't getting cleared out, and Grub was interpreting it as a keypress or something, so wouldn't count down.  I figured on going into bios to see if there was a reset I could do.
4.  Went into bios configuration.  Didn't find anything that would help, but while I was there, thought I'd tweak some things there.  (note to self, don't do that....)  Turned off bluetooth (have no such devices), a few other things.  When I booted up the machine, the bios progress bar got about 3/4 of the way done and then stopped.  Screen blanks, and I got an error message at the top - 'real time clock stopped'.  NO WAY to recover.  Can't get back into bios, nothing.  Can't get into bios on reboot.  Dead.  Fresh new brick.
5.  Talked to Dell, both on-line chat and email.  on-line chat weren't helpful - wanted me to boot from usb or cdrom and flash new bios.  Can't do that if computer won't get through bios startup, guys.  Finally talked to Dell email help, they said they'd send a new machine out.  never really got an answer, and no one ever said DIP about the error message.  I'd complain more, but they sent me a new machine, so I can't complaing too much.

Here's what I'm figuring - the bios tweaking *shouldn't* have messed things up.  I'm thinking that there was a bad bios cmos battery or something, & that the real time clock was goobered and THAT lead to the grub error.

I'll tell you, if I see my grub countdown hack again I'm going to get really nervous.

---

### Post by jede on 2006-05-22
Hi Charles,

thanks for your BIOS adventure report. I hope I'll never have the same things ...

Bye,
Stefan

---

### Post by jede on 2006-05-22
Hi Charles,

one more question:
Do you also have the problem with the beep noise when running in battery mode? When connected to power it all works fine. Has this been fixed on your new device ?

Stefan

---

### Post by dragonflyFZX on 2006-05-22
hey charles,

nice to have you back.  I believe i read something about the bios thing over here.  Is this close to the problem you are faceing?

see last post in
[http://www.ubuntuforums.org/showthread.php?t=178482]("http://www.ubuntuforums.org/showthread.php?t=178482")


thanks for your replies on my posts.  I will compare your xorg.conf with mine if i have a second.  I already tried your how to for the special keys.  It works great up to the point where i have to make it startup each time i boot.  When i create the file you mention, kde opens kate with the contents of the file in it.  Dont worry, i will get it to start some other way, i have done these things before.

and oh yes, i have 1440x900

D

---

### Post by charles.figura on 2006-05-23
[QUOTE=dragonflyFZX]hey charles,
nice to have you back.  I believe i read something about the bios thing over here.  Is this close to the problem you are faceing?

see last post in
[http://www.ubuntuforums.org/showthread.php?t=178482]("http://www.ubuntuforums.org/showthread.php?t=178482")
[/QUOTE]

Wow.  Yep, that looks like it.  Now I'm more nervous than before.  Looks like it wasn't just a one-of incident.  D620 users should take a look at that.

[QUOTE=jede]
Do you also have the problem with the beep noise when running in battery mode? When connected to power it all works fine. Has this been fixed on your new device ?
Stefan[/QUOTE]

Are you referring to the high-pitched buzz mentioned earlier in this thread?  If so, then yes, I've still got it, though it's not too bad.  Interestingly enough, if I put my head up really close and listen, I hear what almost could sound like morse code.  Perhaps I'm directly communicating with the NSA.
Whups, now I'll be on the watchlist....

---

### Post by charles.figura on 2006-05-23
Here's a question particularly for those with the 1440x900 display.  I've got a goofy screensaver - only shows up on the upper 2/5 or so of the screen.  Below that is black.  This happens on the GL screensavers.

---

### Post by dragonflyFZX on 2006-05-23
hi charles,

yes, i've got the same thing with the screensaver...


edit: btw, i tried the xgl thing with the link you gave.  I think i ran into the same issues as you did.  I didn't have window frames anymore.  Tho i have to admit that some of the things were working (like the famous cube thing).  But it was somehow slow.  You've got any breakthroughs?


D

---

### Post by charles.figura on 2006-05-23
[QUOTE=dragonflyFZX]hi charles,

yes, i've got the same thing with the screensaver...

edit: btw, i tried the xgl thing with the link you gave.  I think i ran into the same issues as you did.  I didn't have window frames anymore.  Tho i have to admit that some of the things were working (like the famous cube thing).  But it was somehow slow.  You've got any breakthroughs?
D[/QUOTE]

Ug.  I've got this crazy notion that the screensaver and the suspend are tied together in some goofy way.  No, no, not causally - but I suspect that if someone figures out one, the other one will go away - they're both evidence of a bum driver, either for the display or for the video adapter.

As a result, I think I've put the XGl on hold - I'm betting that it won't work until the rest of it does.

Right now I've got something weirder.  I've disabled suspend and hibernate, since they don't work.  But sometimes if I close my lid & open it back up (without the machine suspending), the keyboard doesn't wake up.  I can use the touchpad/twiddle stick, the system is responsive, but the keyboard has no action.  Caps lock won't toggle the lighth on/off.  Gork?  I can reboot, but it hangs before X cuts out.

This is too goofy.

---

### Post by howardcheng on 2006-05-24
[QUOTE=charles.figura]
Right now I've got something weirder.  I've disabled suspend and hibernate, since they don't work.  But sometimes if I close my lid & open it back up (without the machine suspending), the keyboard doesn't wake up.  I can use the touchpad/twiddle stick, the system is responsive, but the keyboard has no action.  Caps lock won't toggle the lighth on/off.  Gork?  I can reboot, but it hangs before X cuts out.

This is too goofy.[/QUOTE]

I have tried using the 386 kernel (no SMP) and waking up from suspend went further: at least I get X back with gnome running...except that everything I tried to do results in "input/output error".  If I use the 686 kernel (with SMP) I get a blank screen with the mouse cursor.  In either case, switching to other consoles with Ctrl-Alt-F? gives a garbled screen, and I could not reboot the system (input/output error in the 386 case, and nothing responds in the 686 case).

---

### Post by charles.figura on 2006-05-24
[QUOTE=howardcheng]I have tried using the 386 kernel (no SMP) and waking up from suspend went further: at least I get X back with gnome running...except that everything I tried to do results in "input/output error".  If I use the 686 kernel (with SMP) I get a blank screen with the mouse cursor.  In either case, switching to other consoles with Ctrl-Alt-F? gives a garbled screen, and I could not reboot the system (input/output error in the 386 case, and nothing responds in the 686 case).[/QUOTE]

Well, my dippy keyboard error seems to have been the result of a problem with the .kde configuration directory - there was some goofy configuration set, but I'm not sure where.  I may try to ferret it out.

Howard, you're definitely getting further than I am if you can see something on your screen.  But it doesn't sound useful at that point, either.

I did come across this note from someone using Suse 10.2 - [http://www.fzu.cz/~kolorenc/d620/](http://www.fzu.cz/~kolorenc/d620/)
He's running on a D620 and had success with Suspend to Ram when he started running a 2.6.16 kernel, but not before.  I'm tempted to download the source from kernel.org and try it out.  I'm figuring on doing a 'make oldconfig' and working from there.  I'll keep y'all informed....

---

### Post by charles.figura on 2006-05-25
Has anyone tried using an external CRT or projector?  I tried using a projector today with no luck.  I tried playing around with the i810switch and the i855crt with no luck.  Any successes?

---

### Post by jede on 2006-05-25
I've also tried the VGA out. Unfortunately it outputs the 1280x800 resolution with a invalid frequence for LCD monitors. It would be good to know how to switch to the resolution of the externel LCD whenever switching to it....

---

### Post by chinook on 2006-05-28
So I've tried all the suggested things in this thread and yet I cannot get the 1440x900 resolution to work.  Is anyone else having trouble with this?  I'm running Dapper flight 5 with all the current updates.  I've installed and configured 915resolution including editing the /etc/default/915resolution file.  I've attached my xorg.conf file so you can look at it.

Thanks

---

### Post by charles.figura on 2006-05-28
[QUOTE=chinook]So I've tried all the suggested things in this thread and yet I cannot get the 1440x900 resolution to work.  Is anyone else having trouble with this?  I'm running Dapper flight 5 with all the current updates.  I've installed and configured 915resolution including editing the /etc/default/915resolution file.  I've attached my xorg.conf file so you can look at it.
[/QUOTE]

Chinook -

Here are a few thoughts.  My xorg.conf does NOT specify video ram for the card (there under the i810 load) or the sync and refresh rates for the display.  I don't know if they might be causing the problem or not.  You might try taking a look at /var/log/Xorg.0.log and see if you spot any errors.  If so, you might try removing the aforementioned lines from the xorg and letting it figure it out.

The other thing you should do is this - at a shell prompt, type
sudo 915resolution -l
That will show you all available video modes.  Do you see a mode for 1440x900?  When I was first using the /etc/default/915resolution location to set the mode, I had problems since I didn't give it a mode number to rewrite.  When I specified mode = 5a in the 915resolution file, it worked like a charm.

Let us know - we should be able to get you up and running.

---

### Post by dragonflyFZX on 2006-05-30
hey people,

did anyone try to get the infrared port working?  I am trying, but...

i read that the first thing i should do is enable the ir port in the bios, as this is disabled by default.  If i do so, ubuntu starts, but when it is time to bring up X, it hangs.  I cant even get into a terminal.  Poweroff is the only thing that is left.  Anyone has this problem too???

---

### Post by jede on 2006-05-30
This is an allready known bug in linux-image 2.6.15-23 (older versions have worked). It's been reported here:
[https://launchpad.net/bugs/45542](https://launchpad.net/bugs/45542).

This problem exists on many laptops. I have disabled infrared in bios and it works fine. Hopefully this bug will get fixed soon ...

Bye,
Stefan

---

### Post by chinook on 2006-05-31
[QUOTE=charles.figura]Chinook -

Here are a few thoughts.  My xorg.conf does NOT specify video ram for the card (there under the i810 load) or the sync and refresh rates for the display.  I don't know if they might be causing the problem or not.  You might try taking a look at /var/log/Xorg.0.log and see if you spot any errors.  If so, you might try removing the aforementioned lines from the xorg and letting it figure it out.

The other thing you should do is this - at a shell prompt, type
sudo 915resolution -l
That will show you all available video modes.  Do you see a mode for 1440x900?  When I was first using the /etc/default/915resolution location to set the mode, I had problems since I didn't give it a mode number to rewrite.  When I specified mode = 5a in the 915resolution file, it worked like a charm.

Let us know - we should be able to get you up and running.[/QUOTE]

Charles,

Thanks for the reply.  Looking at /var/log/Xorg.0.log reveals this:
(II) I810(0): Not using mode "1440x900" (no mode of this name)

This is odd as the 915resolution stuff should have taken care of that no?

Running sudo 915resolution -l shows:

 Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1440x900, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1440x900, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1440x900, 24 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

So Mode 5a should be fine for me.  In /etc/default/915resolution I have:

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE
#
MODE=5a
#
# and set resolutions for the mode.
#
XRESO=1440
YRESO=900
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=24

I'm not sure what to do at this point.  Thanks for the help.

Steve ](*,)

---

### Post by charles.figura on 2006-05-31
[QUOTE=chinook]Charles,
[deleted]
Mode 5a : 1440x900, 24 bits/pixel

So Mode 5a should be fine for me.  In /etc/default/915resolution I have:
[deleted]
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=24

Steve ](*,)[/QUOTE]

Steve -
Try leaving the bit default blank on /etc/default/915resolution.  It sounds counterintuitive, but I ran into this before, too.  It seems that if you specify 24bit, it won't work.  When I run 915resolution -l, I get:
```

Mode 5a : 1440x900, 32 bits/pixel

```
and no 24 bit modes.  But it works with the proper 24 bit, despite the fact that bios thinks it's a 32bit mode.
Weird.  

Try leaving the bit default blank:
```

BIT=

```
and let us know.

---

### Post by chinook on 2006-06-01
[QUOTE=charles.figura]Steve -
Try leaving the bit default blank on /etc/default/915resolution.  It sounds counterintuitive, but I ran into this before, too.  It seems that if you specify 24bit, it won't work.  When I run 915resolution -l, I get:
```

Mode 5a : 1440x900, 32 bits/pixel

```
and no 24 bit modes.  But it works with the proper 24 bit, despite the fact that bios thinks it's a 32bit mode.
Weird.  

Try leaving the bit default blank:
```

BIT=

```
and let us know.[/QUOTE]


Thanks again Charles,

I removed the 24 from my 915resolution file and restarted X but it was the same as before.  I then removed the horizontal and vertical synch stuff from my xorg.conf file and that broke X when I tried to restart it.  I did notice something more in my Xorg.0.log file though, it is complaing that my vertical/horizontal rates are too high.  Here is what it says:

(WW) I810(0): config file hsync range 28-72kHz not within DDC hsync ranges.
(WW) I810(0): config file vrefresh range 43-60Hz not within DDC vrefresh ranges.(II) I810(0): Generic Monitor: Using hsync range of 28.00-72.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) I810(0): Not using mode "1440x900" (no mode of this name)
(II) I810(0): Not using mode "1280x800" (no mode of this name)
(II) I810(0): Not using mode "1152x768" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0):  Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"


Thanks again,

Steve

---

### Post by charles.figura on 2006-06-01
[QUOTE=chinook]
I removed the 24 from my 915resolution file and restarted X but it was the same as before.  I then removed the horizontal and vertical synch stuff from my xorg.conf file and that broke X when I tried to restart it.  I did notice something more in my Xorg.0.log file though, it is complaing that my vertical/horizontal rates are too high...
[/QUOTE]

Steve -
Okay, I was taking a look at your xorg.conf.  I didn't see anything overtly different from my own xorg.conf (which I've attached, for grins).  I'm not sure what the i2c module does (which I load), and I already mentioned that I don't specify refresh/sync rates.  Oh, and I don't think that the intel display drivers have any dedicated RAM - I was under the impression that they share resources with the mainboard.  If so, I don't know what effect specifying RAM might have.

Couple of thoughts:  how did you install 915resolution?  Did you do an apt-get, or did you make from source as described earlier in the thread? 
And have you done an apt-get update and upgrade lately?

I may be starting to grasp at straws here....

---

### Post by chinook on 2006-06-01
For the love it's working now.  I don't know why or what changed (I didn't change anything but I did reboot) but it is working now.  It will be interesting to see if it sticks.

Thanks for the help,

Steve

---

### Post by charles.figura on 2006-06-02
HIBERNATION!  Ooh-da-lolly.

You've heard my attempts to hibernate before.  I dunno if any of you ran into the same problems I did, but the fix is easy.  Go to your /boot/grub/menu.lst, and add a bit to the end of your primary boot line.  So on mine, the default looked like this:
```

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

```
Add a line to the kernel line -
resume=/dev/sda5
where sda5 is my swap partition.  Take a look at /etc/fstab if you don't know what your swap partition is.  It should look like:
```

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/sda1 ro quiet splash resume=/dev/sda5
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

```

And bango.  Everything comes back for me.  Unfortunately, KNetworkmanager doesn't automatically restart the web, but that's easy enough.  We've got full video acceleration on recovery.  I haven't found a downside yet.

Okay, I got this one figured out.  Someone else figure out suspend-to-ram.

---

### Post by dragonflyFZX on 2006-06-03
hi charles,

are you sure this is all you changed?  When i try this, and close the lid of my laptop, it goes into hybernate mode.  When i open it again, there is disk activity and the bluetooth indicator goes on, but the screen remains black.  The only thing i can do is push the off button...:???:

edit: sorry my bad...

it seemed i defined standby as the behaviour when i close the lid.  Now that i set it to hybernate, it seems to work.  Tho i have to admid i dont really know the difference between all this hybernate/standby/suspend to disk/suspend to ram/shutdown...

As i have it now, if i close the lid, my laptop seems to shut down, although i dont get to see the splash screen.  To wake it up again, i have to push the power button and i get the grub menu.  If i choose ubuntu, i get weird vertical lines on my screen and then it goes black.  If i then press enter, i am back where i started.  So tell me, why would i use this?  Why not just shut down the machine?

I have another question: the d620 has this cool ambient light feature.  Is there a possibility to manage this from within ubuntu?  In windows, it tells me when it is on or off, and i can change the average brightness with a setup  tool, a bit like what you can do in the bios.
 
And about the suspend to ram... I am affraid i am not good enough to help you out here.  I would really love to help, but i am a mere mortal user an just beginning with linux.  Most thing i find myself are probably trivial for people like you.  Although i was very happy to be able to file one of the first experience reports of running dapper on the d620 :-)

---

### Post by charles.figura on 2006-06-03
[QUOTE=dragonflyFZX]hi charles,
...
it seemed i defined standby as the behaviour when i close the lid.  Now that i set it to hybernate, it seems to work.  Tho i have to admid i dont really know the difference between all this hybernate/standby/suspend to disk/suspend to ram/shutdown...

As i have it now, if i close the lid, my laptop seems to shut down, although i dont get to see the splash screen.  To wake it up again, i have to push the power button and i get the grub menu.  If i choose ubuntu, i get weird vertical lines on my screen and then it goes black.  If i then press enter, i am back where i started.  So tell me, why would i use this?  Why not just shut down the machine?
[/QUOTE]

dragonflyFZX -

Suspend to Ram (or standby) stores the system state in RAM.  The system shuts down but mantains power to RAM to keep the system state alive.  Power usage is much less than leaving the machine running - processor, video driver isn't running, you're not generating heat, etc.  Plus it should wake up very quickly, without waiting for boot-up.  It's great for taking the machine home or to work - you don't have to close everything down.  I don't know how long a suspend to ram will take to drain a battery.  This is typically the default action for closing the lid.

Suspend to Disk (hibernate) writes out the system state to the swap partition on your harddisk.  This doesn't take power once it shuts down - so you're not slowly draining your battery (unlike standby).  The reason you'd do this instead of just powering down is that it does write out the system state - all of your windows, desktops, everything should wake up exactly as you'd left them.  So if I'm in the middle of coding and it's time to go home, I don't have to shut down my editors.  Frankly, if suspendtoram worked, I wouldn't use hibernate unless I didn't think I could get recharged. anytime soon.

As for the funky display while it's waking up, it's just garbage in the display buffer.  That should clear up as the system starts writing to the display.  I typically just let the countdown timer on grub wind out, and the default starts up the hibernate image automatically.
[QUOTE=dragonflyFZX]
I have another question: the d620 has this cool ambient light feature.  Is there a possibility to manage this from within ubuntu?  In windows, it tells me when it is on or off, and i can change the average brightness with a setup  tool, a bit like what you can do in the bios.
 
And about the suspend to ram... I am affraid i am not good enough to help you out here.  I would really love to help, but i am a mere mortal user an just beginning with linux.  Most thing i find myself are probably trivial for people like you.  Although i was very happy to be able to file one of the first experience reports of running dapper on the d620 :-)[/QUOTE]
I don't know about software control of the ambient light feature.  I know that the autoadjust function key (Fn-leftarrow) seems to work fine.  I haven't played around with anything else.

And I suspect that the suspend-to-ram (and the funky screensaver) is well beyond most of our abilities.  I suspect someone who knows something about video drivers is going to have to fix this one.  I'd just like to hear someone with an i8xx or i9xx display driver say that they've seen the partial screensaver too.  I saw this same thing on a Vaio B100 that I installed Dapper on.  

It's stupid (just a screensaver), but it's bugging me.

---

### Post by naturalfreak on 2006-06-08
I am relatively new to Linux and completely new to Ubuntu.  I just installed 6.06 on my d620 and followed the instructions with 915resolution to update the display ([http://www.math.dartmouth.edu/~sarunas/D620F6.html)](http://www.math.dartmouth.edu/~sarunas/D620F6.html)).  When I reboot, 915resolution reports the correct updated resolution listings, but the display is not using the correct resolution.  If I look under System > Preferences > Screen Resolution the 1440x900 resolution is not listed.  

However, if I do the following, the display shows up correctly:
1. CTRL-ALT-F1
2. sudo killall gdm
3. sudo gdm

Any ideas?  It sounds like something simple but I just don't know linux very well.

---

### Post by naturalfreak on 2006-06-08
It looks like I figured it out (though not sure why).  DRI was not enabled under the Device for the i810 in the etc/X11/xorg.conf.  I added 

Option "DRI" "true"

Not sure why, but it seemed to work.

[QUOTE=naturalfreak]I am relatively new to Linux and completely new to Ubuntu.  I just installed 6.06 on my d620 and followed the instructions with 915resolution to update the display ([http://www.math.dartmouth.edu/~sarunas/D620F6.html)](http://www.math.dartmouth.edu/~sarunas/D620F6.html)).  When I reboot, 915resolution reports the correct updated resolution listings, but the display is not using the correct resolution.  If I look under System > Preferences > Screen Resolution the 1440x900 resolution is not listed.  

However, if I do the following, the display shows up correctly:
1. CTRL-ALT-F1
2. sudo killall gdm
3. sudo gdm

Any ideas?  It sounds like something simple but I just don't know linux very well.[/QUOTE]

---

### Post by dro0g on 2006-06-15
Suspend-to-RAM on my D620 is now working for me after the kernel update today!!

As soon as I installed the kernel update today I tested suspend and its working great, both from the GDM login screen as well as once I've logged in. I think this kernel update resolved whatever the issue was with the SATA controller getting restarted. 

USB comes back up fine, network (wired and Intel wireless) comes back up fine with NetworkManager. Sound comes back ok.

woo-hoo!

---

### Post by howardcheng on 2006-06-15
[QUOTE=dro0g]Suspend-to-RAM on my D620 is now working for me after the kernel update today!!

As soon as I installed the kernel update today I tested suspend and its working great, both from the GDM login screen as well as once I've logged in. I think this kernel update resolved whatever the issue was with the SATA controller getting restarted. 

USB comes back up fine, network (wired and Intel wireless) comes back up fine with NetworkManager. Sound comes back ok.

woo-hoo![/QUOTE]

Confirmed.  Using 2.6.15-25-686.  Suspend-to-RAM and Hibernate both work!

---

### Post by jede on 2006-06-16
Wow, that's like christmas. I read it here and tried suspend to ram with kernel 2.6.15-25. And it works !!!

---

### Post by charles.figura on 2006-06-16
[QUOTE=jede]Wow, that's like christmas. I read it here and tried suspend to ram with kernel 2.6.15-25. And it works !!![/QUOTE]

You guys must have done the separate wireless install.
While I did that the first time, I found that the linux-restricted-modules package installed it automatically.
And while suspend on the -25 kernel seems to work (for the test or two I tried), without the restricted-modules package my wireless won't work.

Hopefully won't be too long on that front.

I wonder if the goofy external monitor display issues I'd seen are fixed, too?

Still looks like my Gl screensavers don't display on the whole screen, though. :sad:

---

### Post by jede on 2006-06-17
Yes, that's the only problem left for me: the external monitor or beamer output didn't work correctly :-( Has anyone got this fixed ?

---

### Post by charles.figura on 2006-06-18
[QUOTE=jede]Yes, that's the only problem left for me: the external monitor or beamer output didn't work correctly :-( Has anyone got this fixed ?[/QUOTE]

Jede -
 
This isn't going to be much help, I fear.  I had not had luck trying out the external monitor/projector when I first tried it.  Then about a week ago I tried again, and just toggling the Fn-F8 combination made it go - it worked.

I *did* find a couple of problems.  When display was on both screens (laptop and external) the laptop display was a bit off - in order to click on something, I'd have to click *above* it!

I also found that there seemed to be a limited number of cycles I could perform.  I mean, if I kept toggling FnF8, eventually my laptop display wouldn't come back on.

I wonder if that's fixed under the new kernel.
I may have to go try that out.

Of course, I have the 1440x900 display, and we already know that that's a bit different then the 1280....

---

### Post by charles.figura on 2006-06-18
Okay - here's what I've got on the external monitor, and it's repeatable.

Start on laptop display.
FnF8 -> CRT on
FnF8 -> Both on
FnF8 -> Both on (screens shut off & then back on)
FnF8 -> CRT on
FnF8 -> laptop on
FnF8 -> dead.  backlight may or may not come back on, but
display won't.

This result holds under both 2.6.15-23 and 2.6.16-25 kernels.

I teach, and use my laptop in the classroom.  Looks like I'm going to have to just make sure that I reboot after class.  :?

---

### Post by jede on 2006-06-18
Hi Charles,

I have EXACTLY the same problems with my D620, which has the 1280-resolution. It's not fine when the laptop needs to be used on presentations or in a classroom. Maybe we should file a bugreport in LaunchPad (or maybe it was allready).

Bye,
Stefan

---

### Post by charles.figura on 2006-06-18
I just filed the external monitor problem as a bug on Launchpad -
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/50243](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/50243)

As you say, it's not practical for class.  Fortunately, I've got until September.  I can be optimistic for a week or two...

---

### Post by charles.figura on 2006-06-19
Well, now that suspend and hibernate are working, has anyone succeeded in setting up the keyboard shortcut keys (Fn-Esc and Fn-F1)?

Using xev and xmodmap, I managed to set the Fn-F1 key to make the machine hibernate, but Fn-Esc doesn't show up under xev, so I can't set it up.

Has anyone had any luck?  Or tried?

---

### Post by jede on 2006-06-19
Yes, FN+F1 works for me too, FN+ESC not.
But I haven't tried to fix it, I can just put a exit icon on the panel and that's enogh for me. 
You can also configure gnome-power-manager that it suspends to ram when you close the display (when you're using Gnome).

Stefan

---

### Post by usererror on 2006-06-19
I have a D620 with work, but I am looking to purchase one for myself, or the D420 which is being release on July 1st.  I can't get a demo of it until that date however.  But after reading this thread I am way too eager to get the D620 so I may just order it and not get the D420! :)

---

### Post by howardcheng on 2006-06-19
[QUOTE=jede]Yes, FN+F1 works for me too, FN+ESC not.
But I haven't tried to fix it, I can just put a exit icon on the panel and that's enogh for me. 
You can also configure gnome-power-manager that it suspends to ram when you close the display (when you're using Gnome).

Stefan[/QUOTE]

Both Fn+F1 and Fn+Esc work for me.

---

### Post by charles.figura on 2006-06-19
Howard -

Are you running Gnome or KDE?  Did you have to do anything to get the FnEsc and FnF1 working, or did they work out-of-the-box?

---

### Post by howardcheng on 2006-06-20
[QUOTE=charles.figura]Howard -

Are you running Gnome or KDE?  Did you have to do anything to get the FnEsc and FnF1 working, or did they work out-of-the-box?[/QUOTE]

I'm using Gnome, and the buttons worked out-of-the-box.  I did not have to do anything special.

---

### Post by ollyshaw on 2006-06-27
Hi guys,

My experiance of the D620 using kubuntu dapper:

install, select safe graphics mode, installs no probs

graphics, install 915resolution, then run dpkg-reconfigure xserver-xorg, i just used the standard options, works great on 1440x900

wireless, i messed around with a few things, however all you need to do is make sure the restricted modules are installed for your kernal.

Suspend works, but does not seem to bring the wireles up again each time.

Hope this helps!

Olly

---

### Post by charles.figura on 2006-06-28
Olly -

Well, sounds like the install finally ironed out the rest of the bugs.  How about the following (from earlier in the post) -
1.  Do you see the partial screensaver issue mentioned above with the GL screensavers?
2.  Have you tried extensive testing with an external monitor and/or projector? (also see above)
3.  Have you tried repeated suspend/awake cycles?  I'm seeing that I can't suspend and wake up with impunity - maybe a couple of times at most.

---

### Post by ollyshaw on 2006-06-29
Hi Charles,

1.  Do you see the partial screensaver issue mentioned above with the GL screensavers?

I had this problem with some dell machines using dapper, including my d620. I added the following packages

kscreensavers-xsavers
xscreensaver-gl
xscreensaver-gl-extra
xscreensaver-data

That fixed it in kde for most gl screensavers.


2.  Have you tried extensive testing with an external monitor and/or projector? (also see above)

No, I have not trusted linux for a presentation for a while (sorry guys!)

3.  Have you tried repeated suspend/awake cycles?  I'm seeing that I can't suspend and wake up with impunity - maybe a couple of times at most

I seem to get a mix, suspend always seems to work and awake fine, however the wireless card dies something like 25% of the time.

Great thread, 

Cheers,

Olly

---

### Post by charles.figura on 2006-06-29
Olly -

Thanks.  The only thing I hadn't installed was the xscreensaver-gl-extra.  That gave me some more gl screensavers (which did work right), but the particle ones (particle fountain, solar winds, flux, others...) still don't function correctly.

---

### Post by allyson on 2006-07-10
First of all, I too cannot use hibernate on this 620. I really appreciated the help given in this thread as to what to do if you have hibernated your machine! Therefore can't help with FnF1 or FnEsc...

About external monitors: a little modification to the xorg.conf file allowed me to use two monitors at once with no problems, as separate desktops. Perhaps this would be good enough for the teachers? This is a general purpose external monitor configuration: it works whether or not I have the second (LCD) monitor attached. Please note that I have the 620 with the 1440x900 screen, and am connecting to an LCD monitor over an analog cable. I also don't have the fancy nvidia graphics card - just the bog standard Intel one. Please adjust your settings accordingly, and backup your xorg.conf before making any changes. I got help on this from a website dealing with something vaguely similar that I can't find anymore, so apologies for not crediting it! 

Perhaps this is obvious to all (this is my first post!), but I thought it might be useful to show people what worked for me. Below are a list of modifications I made to my xorg.conf

I modified my "Device" section FROM THIS:

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

TO THIS:

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option          "VBERestore" "TRUE"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller1"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "DevicePresence" "false"
        Screen          1
EndSection

DON'T FORGET TO CHANGE ALL OTHER MENTIONS OF "Intel Corporation Mobile Integrated Graphics Controller" TO ""Intel Corporation Mobile Integrated Graphics Controller0". 
ADDED A NEW MONITOR LIKE THIS:

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync       30-83
EndSection

ADDED A NEW SCREEN SECTION FOR THE NEW MONITOR:

Section "Screen"
        Identifier      "External Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller1"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

REMOVED THIS LINE FROM "ServerLayout":

	#Screen		"Default Screen"

..AND ADDED THESE LINES INSTEAD:

        Screen          0 "Default Screen" 0 0
        Screen          1 "External Screen" Above "Default Screen"


thanks :)

---

### Post by charles.figura on 2006-07-11
> **allyson said:**
> First of all, I too cannot use hibernate on this 620. I really appreciated the help given in this thread as to what to do if you have hibernated your machine! Therefore can't help with FnF1 or FnEsc...



Allyson -

Thanks for posting your xorg.conf.  I don't know that it will work too well for me - all of my start-up apps show up on the external display, so if I'm not plugged into a projector, everything's missing.  Do you know of a fix for that?

As for hibernation - 
1. Do you have hibernation enabled under your power management settings?
2. Try taking a look at my page: [http://mcsp.wartburg.edu/figura/D620.html](http://mcsp.wartburg.edu/figura/D620.html)
   I outline what I did to get hibernation working for me.
Hibernation has been working very well for me, but I don't use it too frequently -
mostly I've been using Suspend to Ram.

Thanks!

---

### Post by allyson on 2006-07-12
Hi Charles,

Unfortunately, I don't know a fix for what you described, though I'll keep looking. For me, it works just fine as I am always starting new sessions from scratch, and so always start with an empty external monitor.

Thanks for the tip for hibernating. Unfortunately, it didn't work for me - something to do with my monitor setup, I think! It almost comes up from hibernation, but it can't start the x server. Perhaps I try with my xorg.conf just set to one monitor, and see if that helps.

thanks :) Allyson

---

### Post by jede on 2006-07-15
Hi Allyson,

tahnks for the dualhead explaination. I tested it with Xinerama and it works great and stable. Very nice!

Stefan

---

### Post by jede on 2006-07-15
Since the Dapper kernel was updated to 2.6.15-26 my notebook completely freezes when trying to switch to external monitor when pressing FN+F8. (I don't mean the dualhead mode.) I can't switch to console and nothing else. With 2.6.15-25 it has been working.
Does anybody has the same problems ?

Bye,
Stefan

---

### Post by jede on 2006-07-16
Hi,

I found a very reliable solution for the clone mode when an external display (or beamer) needs to be attached, e.g. on presentations.
Both the laptop and the external display are always enabled and display 1024x768 at 60 Hz.

When I need to use the external display I just need to copy this xorg.conf.clone to xorg.conf and restart the gdm (STRG+ALT-DELETE). The special function keys are not used here, they make the problems mentioned before.

It would be nice when there would be an option to choose at boot time which X configuration needs to be used (normal, clone or dualhead), I have no idea how to do this ...

Bye,
Stefan

Here is my xorg.conf.clone:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier 	"Intel Corporation Mobile Integrated Graphics Controller0"
	Driver 		"i810"
	BusID 		"PCI:0:2:0"
	Option 		"VBERestore" "TRUE"
	Option 		"MonitorLayout" "CRT,LFP"
	Option		"Clone" "true"
	Screen 		0
EndSection

Section "Device"
	Identifier 	"Intel Corporation Mobile Integrated Graphics Controller1"
	Driver 		"i810"
	BusID 		"PCI:0:2:0"
	Option 		"DevicePresence" "false"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier 	"External Monitor"
	Option 		"DPMS"
	HorizSync 	30-83
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller0"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes 		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"External Screen"
	Device 		"Intel Corporation Mobile Integrated Graphics Controller1"
	Monitor 	"External Monitor"
	DefaultDepth 	24
	SubSection "Display"
		Depth 		24
		Modes 		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by pumpkin_escobar on 2006-07-24
just an oddity that i noticed about suspending to RAM

system is a d620 with the NVS Quadro running dapper and KDE

i originally got my laptop without the bluetooth adapter and suspend to RAM just worked out of the box with no messing around

subsequently got the bluetooth adapter and after installing it, suspend to RAM wouldn't work, it wouldn't 'go to sleep' when i closed the lid

i've found that when the bluetooth adapter is enabled, there doesn't seem to be anything i can do to get it to suspend properly

so what i've done is 'attached' only the bluetooth adapter to the external wireless button (setup is in the bios) and now i just enable/disable the adapter whenever i need it

KDE doesn't seem to have any problem recognizing it even after multiple enable/disables

maybe it'll save someone else some time...

---

### Post by howardcheng on 2006-07-31
> **jede said:**
> Hi,

I found a very reliable solution for the clone mode when an external display (or beamer) needs to be attached, e.g. on presentations.
Both the laptop and the external display are always enabled and display 1024x768 at 60 Hz.



Your xorg.conf doesn't work for me all that well.  For some strange reason I cannot get X to use anything other than 1440x900, even though I tried to specify a different resolution.  When I use your xorg.conf I do get something on the screen but it isn't perfect: the edges are chopped off, and if I moved a window too close to the edge the whole screen darkens.

Here is my xorg.conf.  Any help would be deeply appreciated.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller0"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "VBERestore" "true"
        Option          "MonitorLayout" "CRT,LFP"
        Option          "Clone" "true"
        Screen          0
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller1"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT"
#       Option          "DevicePresence" "false"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"      "false"
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"      "false"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller0"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller1"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection



Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by carl.davis on 2006-08-23
Maybe we should trade laptops :)  All I want to do is get 1440x900 working :(

I am trying to get my new laptop to utilize the 1440x900 resolution with simply no luck. I have read several different ways to use the 915resolution and have had no luck with any of them. Here is what I am doing now:

Setting /etc/defaults/915resolution to

MODE=5a
XRESO=1440
YRESO=900
BIT=

After a reboot a 915resolution -l shows that setting in mode 5a.
DefaultDepth 24 in xorg.conf
Subsection Display depth 24 is 1440x900 and no others, except for other depth settings which are all 1440x900. When I start X it only goes to 1024 x 768 (at least by the screen resolution preferences) Any help here is greatly appreciated.

---

### Post by serusie on 2006-08-25
If you have installed 915resolution and still cannot get 1440x900 try running
```
sudo dpkg-reconfigure xorg-server
```
This will reconfigure the xorg.conf file ( backup the orignal one first ).

I have configured a D620 (1440x900) to use xinerama, dual-desktop, or clone-monitor ( at 1024x768 ). I used a xorg.conf.template file and a script to change the default layout. If you still have problem you may try copying them.

/etc/X11/xorg.conf.template
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerFlags"
	Option "DefaultServerLayout" "##DefaultLayout##"
EndSection

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"Protocol"		"ExplorerPS/2"
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
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"LFP Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 0
	Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
        Identifier      "CRT-Clone Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        #Option          "VBERestore" "TRUE"
        Option          "MonitorLayout" "CRT,LFP"
        Option          "Clone" "On"
        Screen          0
EndSection

Section "Device"
	Identifier	"CRT Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 1
        #Option          "DevicePresence" "false"
	#Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
	Identifier	"LFP Monitor"
	Option		"DPMS"
	DisplaySize	303 189
EndSection

Section "Monitor"
	Identifier	"CRT Monitor"
	Option		"DPMS"
	DisplaySize	340 272  # width x height in mm
EndSection

Section "Screen"
	Identifier	"LFP Screen"
	Device		"LFP Device"
	Monitor		"LFP Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT Screen"
	Device		"CRT Device"	
	Monitor		"CRT Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "CRT-Clone Screen"
	Device "CRT-Clone Device"
	Monitor "CRT Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"LFP Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "ServerLayout"
  Identifier "Dual-desktop Layout"
  Screen 0 "LFP Screen" 0 0
  Screen 1 "CRT Screen" RightOf "LFP Screen"
  InputDevice	"Generic Keyboard"
  InputDevice	"Configured Mouse"
  InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
  Identifier "Xinerama Layout"
  Screen 0 "LFP Screen" 0 0
  Screen 1 "CRT Screen" RightOf "LFP Screen"
  Option "Xinerama" "true"
  InputDevice	"Generic Keyboard"
  InputDevice	"Configured Mouse"
  InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier	"Clone Layout"
	Screen		"CRT-Clone Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

'xlayout' script ( to change layout )
```

#!/bin/sh

xorgdir="/etc/X11"
xorgfile="$xorgdir/xorg.conf"
xorgtemplate="$xorgdir/xorg.conf.template"

usagemsg="\
Usage:
  xlayout layout
  where layout can be s(ingle), d(ual), x(inerama) or c(lone)"

if [[ $# < 1 ]]; then
  echo "$usagemsg";  exit
fi

case "$1" in
  s | single ) layout="Default Layout";;
  x | xinerama ) layout="Xinerama Layout";;
  d | dual* ) layout="Dual-desktop Layout";;
  c | clone ) layout="Clone Layout";;
  * ) echo $'error: unknown layout\n'"$usagemsg"; exit -1;;
esac

sudo sh -c "sed -e 's/##DefaultLayout##/$layout/' $xorgtemplate > $xorgfile"

```

---

### Post by jede on 2006-08-29
The script for changing the default layout is great. Thanks !!!

Bye,
Stefan

---

### Post by jackcy on 2006-11-19
When I try to run the script it displays:

/usr/bin/xlayout: 13: cannot open 1: No such file
/usr/bin/xlayout: 13: [[: not found
Password:


But it changes the mode correctly.

What can I change on the script to get clone screen with 1280x800 on LFP and 1280x1024 on my CRT?

Thanks
Jackcy

---

### Post by ianb on 2006-12-21
> **jackcy said:**
> When I try to run the script it displays:

/usr/bin/xlayout: 13: cannot open 1: No such file
/usr/bin/xlayout: 13: [[: not found


I think this is a problem with the change from /bin/sh away from bash -- if you replace the first line with "#!/bin/bash" it'll probably work

---

### Post by pacesie on 2007-01-19
I am "serusie" who posted the xorg.conf above.
Edgy is nice and all, but xinerama on my D620 stop working properly after the upgrade. Since I also have problem with the Fn+F7 monitor switch, I have to add an "external monitor" layout in xorg.conf to get a nice display on external monitor (only). If anyone have xinerama working on Edgy could you post the xorg.conf? Thanks!

jackcy:

To be sh compliant change line 13 to
   if [ $# -lt 1 ]; then

You cannot get clone screen of different resolutions, you may try using 1024x768 for both.

Here is my updated files ( xinerama has problems on Edgy but the setting should be correct ):

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerFlags"
	Option "DefaultServerLayout" "##DefaultLayout##"
EndSection

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
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
	Option		"Protocol"		"ExplorerPS/2"
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
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"LFP Primary Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "MonitorLayout" "CRT,LFP" # Use laptop monitor for primary display (Is primary on pipe-B?)
	Screen 0
EndSection

Section "Device"
	Identifier	"CRT Primary Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "MonitorLayout" "LFP,CRT"  # Use external monitor for primary display
	Screen 0
EndSection

Section "Device"
	Identifier	"Secondary Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 1		      # Secondary display
EndSection

Section "Device"
        Identifier      "Clone Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Option          "Clone" "on"
	#Option          "MonitorLayout" "NONE,CRT+LFP"   # with overlay(?), need to disable option "clone"
        Screen          0
EndSection

Section "Monitor"
	Identifier	"LFP Monitor"
	Option		"DPMS"
	#DisplaySize	303 189
EndSection

Section "Monitor"
	Identifier	"CRT Monitor"
	Option		"DPMS"
	#DisplaySize	340 272  # width x height in mm
EndSection

Section "Screen"
	Identifier	"LFP Primary Screen"
	Device		"LFP Primary Device"
	Monitor		"LFP Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT Primary Screen"
	Device		"CRT Primary Device"	
	Monitor		"CRT Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT Secondary Screen"
	Device		"Secondary Device"	
	Monitor		"CRT Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Clone Screen"
	Device "Clone Device"
	Monitor "CRT Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"LFP Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier	"External Monitor Layout"
	Screen		"CRT Primary Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
  Identifier "Xinerama Layout"
  Screen 0 "LFP Primary Screen" 0 0
  Screen 1 "CRT Secondary Screen" RightOf "LFP Primary Screen"
  Option "Xinerama" "true"
  InputDevice	"Generic Keyboard"
  InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
  InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
	Identifier	"Clone Layout"
	Screen		"Clone Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerLayout"
  Identifier "Dual-desktop Layout"
  Screen 0 "LFP Primary Screen" 0 0
  Screen 1 "CRT Secondary Screen" RightOf "LFP Primary Screen"
  InputDevice	"Generic Keyboard"
  InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
  InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

```

#!/bin/sh

xorgdir="/etc/X11"
xorgfile="$xorgdir/xorg.conf"
xorgtemplate="$xorgdir/xorg.conf.template"

usagemsg="\
Usage:
  xlayout layout
  where layout can be s(ingle), d(ual), x(inerama) or c(lone)"

if [ $# -lt 1 ]; then
  echo "$usagemsg";  exit
fi

case "$1" in
  s | single ) layout="Default Layout";;
  x | xinerama ) layout="Xinerama Layout";;
  e | external ) layout="External Monitor Layout";;
  d | dual* ) layout="Dual-desktop Layout";;
  c | clone ) layout="Clone Layout";;
  * ) echo "error: unknown layout\n$usagemsg"; exit 1;;
esac

sudo sh -c "sed -e 's/##DefaultLayout##/$layout/' $xorgtemplate > $xorgfile"

```

---

### Post by shutterbc on 2007-01-20
Hmm... I'll have to try multimonitor support via docking station soon.

Right now I have a strange issue though -- sound was working great on Edgy (6.10) until I installed a kernel update (2.6.17-10) in December.  From that point onward, I haven't been able to get any system sounds.  Applications don't have audio output unless I tell them to use OSS instead of ALSA.  The volume control panel applet still works, however.

I've also got Beryl working nicely, except for the fact that it seems suspend to RAM doesn't work when it's active.

---

### Post by Frolleboy on 2007-12-19
> **howardcheng said:**
> I'm running Dapper Beta 2.   Suspend doesn't work for me (either to disk or ram).

Hi, I read some where that the SWAP needs to be the same size or bigger then the amount of RAM to get hirbanete/suspend to work. It works on my D620 with kubuntu 7.10

---

### Post by doggyworld on 2007-12-31
Has anyone found something weird with the sound on the D620?  I've successfully installed 7.10 and everything is working great except for the sound on some games.

Specifically, if I load Neverball/Neverputt, it gives a scratchy sound.  This never happened on my other Ubuntu desktop running 7.04.  The sound in DVD's and playing MP3's seem to be fine however.  I'm wondering why it's scratchy on the games though.  This also happens when I load up Chromium.

My specs on my D620 are:
C2D 2.0 Ghz
2 GB DDR2
NVS Quadro 110M
1490 WiFi

Everything except for WiFi loaded fine and the WiFi was easy to install from one of the posts here.

---

### Post by theproc64 on 2008-01-14
I got Gutsy working great with all the fn keys working.  I used a tutorial to get my broadcom wireless card working with ndiswrapper.  I only have one problem, about every one in five times I wake the computer up from suspend the computer is frozen and the cursor is still blinking:confused:.  Any ideas?

specs
core duo 1.66
1 g ddr2
intel 945gm graphics
1280x800 screen

---

### Post by theproc64 on 2008-01-24
It appears that the most recent update to xserver solved the problem.  THIS IS WHY I LOVE UBUNTU!!:):popcorn:

---

### Post by theproc64 on 2008-02-26
Nope, problem still there.

---

