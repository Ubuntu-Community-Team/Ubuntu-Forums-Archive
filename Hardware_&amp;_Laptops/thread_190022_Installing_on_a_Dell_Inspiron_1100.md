---
title: "Installing on a Dell Inspiron 1100"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by ssnitily on 2006-06-05
It's well known that the installation resolution for this laptop is incorrect and is locked at 640x480. Since the default installer for 6.06 involves booting and running a GUI and these installation screens are much larger than this it's very difficult to install as you can't see what you are tabbing to and can't click on any buttons as they are well bellow the viewable area on the screen.

I've tried many different fixes from these forums and edited xorg.conf several times but nothing has gotten me out of 640x480. I've went onto the #ubuntu IRC chat channel to find it being flooded with others needing help and when I ask "can someone help me with a laptop issue?" the response is "they work if you open them ;)", it isn't very bright on my disposition towards the community. I would really like to use Ubuntu as I don't want to shell out another $200+ for windows xp or even (god forbid) vista. I've tried to read technical posts and seek help on IRC but if nothing in the community has helped and having to pay around $250 to get personalized support what can I do?

---

### Post by durableapostle on 2006-06-06
I had the EXACT same problem.  Here's what I did:

1) In a terminal window type: sudo gedit /etc/X11/xorg.conf

2) Change your data to what I have below (actually, add this info, <i>in addition to</i> what you already have):

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Dell 1024x768 Laptop Display Panel"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
Option "dpms"
EndSection

and in Section Screen, change the monitor line to read

Monitor "Monitor0"

3) Save, close gedit, and then restart the x drive (crtl, alt, backspace).  It should work.

4) Now, this is the part where you'll need help elsewhere... After a hard restart, this will probably go back to the small screen.  You'll need to configure things so that this loads earlier in the startup sequence.  I had a friend help w/ this... sorry, I don't know how he did it.  Ask around the forums.  At least you'll be able to easily fix it every time until you can get help with the part I can't help you with.

---

### Post by Nex on 2006-06-07
well i have the same laptop and what i ended up doing was installing 5.10 first then updating from there. Its not a good work around but it worked. I still had problems with the screen size but just reconfiguring xorg worked for me in that reguard.

---

### Post by ed_agamemnon on 2006-06-07
you'll also want the 915resolution package installed...

---

### Post by jer2eydevil88 on 2006-06-10
Maybe its something I am doing wrong but adding that extra monitor to my xorg.conf file didn't fix the problem even temporarily.

Don't I have to add 1024x768 to some other part of that configuration file?

---

### Post by sbmd on 2006-06-21
Thankx for this fix, it worked great the first second i ctl, atl backspaced. Thankx alot i have been looking ofr a little while for this.

---

### Post by lilchris173 on 2006-07-04
Wow that worked perfectly! I love the OSS Community. But... dell.. bah.. this was a naughty spot on dell in my book. (we shouldn't have to do this stuff)\\:D/

---

### Post by wbmj on 2006-07-04
The 1100 BIOS needs to be updated. My guess is you have the factory version installed. It doesn't correctly access shared memory for the video card. If you go to the Dell website you can download the BIOS upgrade for free.

---

### Post by sidlinux on 2006-08-06
For those of you Dell Inspiron 1100 laptop owners that want to run Ubuntu Dapper Drake (6.06).  Ubuntu on the Dell Inspiron 1100 is awesome.  So here's what you have to do to get your laptop to show 1024x768 resolution.

First, make sure you go to the Dell website and update your BIOS to ensure that it shows Version "A32".  If you don't, I guarantee that it MAY not work.

I will assume that you have installed Ubuntu 6.06 on your laptop.  I haven't tested the Dapper Drake version of Kubuntu, Edubuntu, or Xubuntu.  If I figure out how to get it to work, I'll post the procedures.

Back up your /etc/X11/xorg.conf file.  No excuse for not backing up your important files.

I'm sure when you boot up to Ubuntu, you will have the VGA screen.  Make sure you go to Applications-->Accessories--Terminal.  You should see the command prompt.  Then type the following:

**sudo gedit /etc/X11/xorg.conf**

and enter your login password.

Then go to the section where it says:

[B]
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Monitor"
        Identifier      "Second Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection



Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
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
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
[/B]

Make sure you copy the bold text and paste it in your xorg.conf.  

Save it and reboot.

Upon rebooting, you would still see the 640x480 screen.  DON'T PANIC.  We're not finished yet.

Now go to System-->Preferences-->Screen Resolution.  You will see the attachment called Screenshot.png.  Click on the the button that has two triangles - one pointing up and one pointing down and select your preferred resolution.  (We're almost there)

Click the **Apply** button.  

Enjoy Ubuntu!!! :KS 

If you have wireless issues, make sure you get the Dell TrueMobile 1100 PCMCIA card - This thing works out of the box and the live Ubuntu CD/DVDs and their derivatives.

If you have issues on watching mpgs and AVIs, make sure you install the MPlayer movie player.  Use Synaptic Package Manager  (SPM) to install it.

If you have issues on listening to mp3s, make sure you install the XMMS Music Player.  Use SPM to install it.

Chatting online with MSN, Yahoo messenger, or AIM?  You can catch me at sidneyjuachon on Yahoo Messenger.  Please let me know in advance if you wish to chat.

Everything I mentioned in this post are my suggestions.  It's entirely your call if you decide to use it.

Good luck with your Dell Inspiron 1100 and a few cups of Ubuntu.:D 

Cheers,

Sidney

---

### Post by sidlinux on 2006-08-06
There are more than one solution to this problem.  I cite my sources to my xorg.conf file and the *Ubuntu Hacks* book (covers Dapper Drake), which I purchased.  It resolved the video issue for me.  I encourage you to pick up a copy if you can.:D 

Cheers,

Sidney

---

### Post by wearerowan on 2006-08-06
ok. So I'm having the same problem. I've actually had this problem before with this system using other os's. Anyway, I copied the text into the .conf and nothing changed. I went all over Dell's site but the only bios upgrade they have is a windows .exe. Is there something I'm missing? Where specifically should the text be pasted? And, do I need to change anything else in that file?

---

### Post by frogotronic on 2006-08-06
> **wearerowan said:**
> ok. So I'm having the same problem. I've actually had this problem before with this system using other os's. Anyway, I copied the text into the .conf and nothing changed. I went all over Dell's site but the only bios upgrade they have is a windows .exe. Is there something I'm missing? Where specifically should the text be pasted? And, do I need to change anything else in that file?

I have good resolution (including TWINVIEW) on a Dell Inspiron 8100 using an NVIDIA GeForceGo2 card, here's my config file:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

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

Section "ServerLayout"
    Identifier     "TwinView Configuration"
    Screen          0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
    EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 70.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 Go]"
    Driver         "nvidia"
    VendorName "Videocard vendor"
    BoardName "NVIDIA GeForce2 Go"
    Option "NvAGP" "2"
    Option "RenderAccel" "1"
    Option "CursorShadow" "0"
    Option "ConnectedMonitor" "dfp, dfp"
    Option "NoPowerConnectorCheck"
    Option "TwinView" "1"
    Option "Metamodes" "NULL,1400x1050; 1400x1050,1400x1050; 1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1400x1050,NULL; 1280x1024,NULL; 1024x768,NULL"
    Option "SecondMonitorHorizSync" "31-82"
    Option "SecondMonitorVertRefresh" "56-76"
    # Option "NoTwinViewXineramaInfo"
    Option "TwinViewOrientation" "Clone"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050" "1280x1024" "1280x960" "1152x864" "800x600" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x1050" "1280x1024" "1280x960" "1152x864" "800x600" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x1050" "1280x1024" "1280x960" "1152x864" "800x600" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x1050" "1280x1024" "1280x960" "1152x864" "800x600" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050" "1280x1024" "1280x960" "1152x864" "800x600" "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1280x1024" "1280x960" "1152x864" "800x600" "1024x768"
    EndSubSection
EndSection
```

---

### Post by sidlinux on 2006-08-14
> **wearerowan said:**
> ok. So I'm having the same problem. I've actually had this problem before with this system using other os's. Anyway, I copied the text into the .conf and nothing changed. I went all over Dell's site but the only bios upgrade they have is a windows .exe. Is there something I'm missing? Where specifically should the text be pasted? And, do I need to change anything else in that file?

If you haven't upgraded your bios to A32, I don't think you'll get it to work.  If I remember, you need to boot up to Windows to update your bios to A32 because it turned out to be a Windows-based program.  That's the way Dell has it setup.  I remembered doing that when I updated my BIOS to version A32.  If you can, send us a copy of the xorg.conf file.

We like you to get your Dell Inspiron 1100 to work with Ubuntu, the way you wanted it to work.

Cheers :D ,

Sidney

---

### Post by sidlinux on 2006-08-14
Here's a link to a site titled "Linux on the Dell Inspiron 1100". at [http://www.geocities.com/randomnumbergenerator2001/?200614](http://www.geocities.com/randomnumbergenerator2001/?200614)

Hope this information resolves any video/BIOS issues you need to address on your inspiron 1100.  

Sidney

---

### Post by vkennedy85 on 2006-08-30
I too am having this problem with my 1100.  But my xorg.conf file already has the 1024 768 resolution 'mode' in it, so why don't the options show up?

Also when I type sudo gedit 'path' i get an error, it says 'cannot open display: (null)

---

### Post by ontologicalbach on 2006-09-20
Thanks for your help sidlinux. I am running a dual-boot Inspiron 1100 with the A31 BIOS. My screen resolution, like everyone elses, was stuck on 640, which is really frustrating, because it makes it really difficult to install Dapper because of minimum size of the install GUI. I finally plugged my laptop into a monitor (make sure you do this while the laptop is off, otherwise the screen goes all crazy, and you have to do a hard reset). Anyway, here's the way I got the screen resolution to 1024.

I opened the xorg.conf file using:
sudo gedit /etc/X11/xorg.conf

then I entered my password, and then saved a copy of xorg.conf to my home desktop, just to be safe.

For anyone who did not figure out what to delete and what to save, this is what worked for me...

Delete all of this:
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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


Then, copy in what sidlinux posted (everything in bold below):
[B]Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Section "Monitor"
Identifier "Second Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection[/B]

Save (make sure you're saving to the /etc/X11/ file and not the one you backed up in a different location... almost made that mistake. Reboot the computer.

My computer actually jumped right to 1024 mode without me even telling it to change. Sidlinux had a different experience I guess, and he had to go to System->Preferences->Screen Resolution and change from 640 to 1024. Like sidlinux said, don't panic right away if it doesn't work. I think probably the vital step is to upgrade your BIOS... at least to A31 (what I'm running). You'll need a windows installation to update the BIOS I'm pretty sure, so make sure you leave a windows partition on till you're all set up in Ubuntu. Hope this helps.

---

### Post by vkennedy85 on 2006-10-15
How do I know which BIOS I have, and when I know that how can I update it?

---

### Post by ralos on 2006-11-11
thanks to SIDLINUX is fixed my configuration of my inspiron 1100 , and was not necessary change the resolution manually automatically when i did the steps he said including the restart, the new aspect become 1024x768 thank you so much!!!

---

### Post by starkey on 2006-11-29
[QUOTE=ontologicalbach;1522445]"Thanks for your help sidlinux. I am running a dual-boot Inspiron 1100 with the A31 BIOS. My screen resolution, like everyone elses, was stuck on 640, which is really frustrating, because it makes it really difficult to install Dapper because of minimum size of the install GUI. I finally plugged my laptop into a monitor (make sure you do this while the laptop is off, otherwise the screen goes all crazy, and you have to do a hard reset). Anyway, here's the way I got the screen resolution to 1024."

*****

Thanks for the additional detail on what to delete prior to adding sidlinux's text.  

The problem I'm having, though, is my inability to install in the first place from the 6.06 Live CD.  The default 640x480 resolution doesn't show the entire install screens, so I can't get the OS installed onto an editable disk.  Hence, despite having the A32 BIOS, I can't make the changes to xorg.conf.  ](*,)  Chicken or the egg thing.  

In Install, on the language selection screen, I tried to accept the highlighted English (which was visible), then hit Alt-F to activate the hidden Forward button, but the install hung there, so I'm obviously doing something wrong.

Does anyone have any hints on how to get Dapper Drake installed on an Inspiron 1100 in the first place, so the requisite X configuration edits can be made?  Is there a command-line installation that can be done without having to deal with X?

---

### Post by starkey on 2006-11-29
Further to my last message, booting from Live CD, I selected the Safe Graphics Mode.  X failed to load, and from the command prompt I did sudo nano /etc/X11/xorg.conf .

The file on the CD already lists 1024x768, 800x600, and 640x480 modes, but >System>Preferences>Screen Resolution still only lists 640x480.

---

### Post by jgordon510 on 2006-12-01
Starkey said:
> The problem I'm having, though, is my inability to install in the first place from the 6.06 Live CD.
If you look at the bottom panel, you should have the install program in your window list.  Right click on it.  Select "move".  That will allow you to shift its location enough to click the needed buttons.

---

### Post by ceng1984 on 2006-12-23
Starkey,

I just came across this message. If you haven't completed your 6.06 install and are still having the problem of not seeing the complete screen due to the 640x480 screen, try the following:

During the installation (GUI screens showing, press the ALT key + left mouse key anywhere in the window. This will move the app around so you can bring the accept/next/back, etc buttons into view. This should work on any GUI screen, I believe. It is similar to moving a window by selecting the title bar at the window top to move the window, but it allows you to move the window by grabbing it anywhere.

Hope this helps,

ceng1984

---

### Post by Ahz on 2007-01-29
I have this Dell Inspiron 1100, and I finally got x working properly just NOW.  What I did was this.

FIRST.  I installed Dapper 6.06 from the Live CD starting under the safe graphics mode.  Everything went well, except the video was laggy and yucky.  I then installed the 915resolution package via synaptics package mgr.  

SECOND.  I read and re-read all the applicable threads here and went over my xorg.conf file.

THIRD.  I used $ sudo gedit /etc/X11/xorg.conf  and changed the driver from "vesa" to "i810"

I also added these lines to the .conf file

> **x1982mitzu said:**
> 
Identifier "Generic Monitor"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
Option "DPMS"
EndSection
 
Then ctr alt backspace to restart x and it worked.   Of course it was a much larger ordeal than it looks like here, but now I have video acceleration going and my Daily shows look like they are supposed to.  I`m quite pleased.  

If you are frustrated with your dell, hang in there, the fix is out there, you just gotta keep at it.   Oh, and don`t forget to backup your original xorg.conf file before you go playing with it.  I forgot, and had a helluva time getting back into it to fix it.  All ok now tho. And, update yer BIOS before you get too deep.  A32 is what you need.  

CHeers to the folks on the forum!
\Gordon

---

### Post by starkey on 2007-01-29
Thanks for the assistance on navigating the screen with Alt-Leftmouse - that worked handily.  I've been frustrated by the process, though, since I'm able to navigate only to the timezone screen before the computer just locks up.  Despite having the means to navigate the process, I've yet to complete an install.

I appreciate Ahz's instructions on setting up the video.  If I can ever figure how to get the operating system on, they'll be very useful.  I have the A32 BIOS installed.

I have an old ThinkPad 760EL that I'd love to put Ubuntu on, as well, but with that thing I'm frustrated by the BIOS not supporting a bootable CD.  It'd be a real treat if one could install from an executable on the CD, without having to boot from it first.
Best regards,
Starkey

---

### Post by Ebiggs on 2007-02-25
If you can't get through the normal install of 6.06, try using the 6.10 Alternate Install disc.  It installs through a text mode similar to how Windows XP's install begins.

Edit: I'm about to use Sid's changes once my Inspiron finishes some updates; but will Ahz's fix have better performance (he says he has 3D acceleration now)?

---

### Post by starkey on 2007-02-25
Thanks, Ebiggs - I'll look into the 6.10 alternate install.  I've given up on the Inspiron - put Winderz XP on it and gave it to another user.  I'll try the alternate install on the old ThinkPad.
Starkey

---

### Post by Ebiggs on 2007-02-25
> **starkey said:**
> Thanks, Ebiggs - I'll look into the 6.10 alternate install.  I've given up on the Inspiron - put Winderz XP on it and gave it to another user.  I'll try the alternate install on the old ThinkPad.
Starkey

No problem.  I had tried installing the normal 6.10 disc on the laptop before and it had the resolution problems and was EXTREMELY slow.  It needs more RAM to be able to run a LiveCD.

Now I've just gotta work out the kinks on my gaming PC.

---

### Post by BDNiner on 2007-09-07
I used the 7.04 alternate cd and the install went well, but when i restart all i get is a blank screen. The last thing i saw was grub. I tried to install with the GUI but the laptop would crash on the screen where you select the language. any help with this?

---

### Post by BDNiner on 2007-09-07
Nevermind, i upgraded the memory and I am good to go.

---

### Post by Dragorth on 2007-09-08
Hey guys, had a similar problem with Kubuntu. After instilation, I was able to use the Control applet to change the settings to the correct state. I chose the intel 845 display driver, and the dell 1024x768 LCD display option for the primary monitor. This doesn't give me the control of hacking the x.org file, but it did take less than 3 mins. It should have been able to work before instilation, but I didn;t try. If it does, then great, if not then it SHOULD!!!  Hope it helps. BTW, thanks for the site to install linux, great info there!!
See ya round!

---

