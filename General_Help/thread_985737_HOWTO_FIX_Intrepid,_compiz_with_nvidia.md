---
title: "HOWTO FIX: Intrepid, compiz with nvidia"
date: 2008-11-17
forum: General Help
---

### Post by loomsen on 2008-11-17
Hi everyone.

nvidia drivers have very restrictive permissions by default, 0600, which means only root will have access to the video device. 
As this seems to be the most common problem at the moment, and many threads are related to this problem, here's what you have got to do to fix your permissions(I don't know if this applies to ATI cards too)

You may suffer from this issues, if for instance compiz starts up for some seconds but then breaks again. If you did not explicitely grant yourself permissions to access your nvidia device, this will probably apply to you. (I don't know if this applies to the initial user account as well, the one created during installation, cause I preconfigured my installation prior to installing..)

This should work if you have proper access as well as a properly configured xorg:
[[img]http://www.ubuntu-pics.de/thumb/5915/screenshot_07_5IBjn8.png[/img]](http://www.ubuntu-pics.de/bild/5915/screenshot_07_5IBjn8.png)

Check that you, as your user, are a member of the group video, by typing
```
groups
```
into a terminal while logged in as your user
If you wanna check permissions of another user currently not logged in, run 
```

groups <username>

```


Should give you output like this:
> 
me[~] groups
me adm dialout cdrom video plugdev lpadmin admin sambashare jdown sabayon-admin
me[~] groups docter
docter adm cdrom audio plugdev fuse netdev admin sambashare jdown sabayon-admin
me[~] 


As you see, me is member of group video while docter is not. Now lets add docter to the group video:
> 
me[~] sudo adduser docter video
Adding user `docter' to group `video' ...
Adding user docter to group video
Done.
me[~] 



OK, now you can add a section like this to your xorg.conf, simply append it at the bottom.
Open up xorg.conf with:
```
gksudo gedit /etc/X11/xorg.conf
```

and add this to it:

```

Section "DRI"
   Group  "video"
   Mode   0660
EndSection

```

Save and close the file.

[color=green]NOTE:[/color] If you don't mind any user to have access to direct rendering and your 3D enhancements, you may as well set the Mode to 0666 instead of 0660.

Now restart your X-server, either by initiating a restart from a terminal or, if you're not familiar with that just reboot your computer.
Everything should work now, and you should be able to access and use your device.

---

### Post by loomsen on 2008-11-18
Part 2:

Fix DPI which isn't correctly set through autoselect:

Open up nvidia-settings and check which DPI is used if you don't have it explicitely configured in your xorg.conf. For me it wasn't, which led to broken fonts and somewhat "blurred" screen in total.

nvidia-settings:
[[img]http://www.ubuntu-pics.de/thumb/5916/screenshot_09_dkTfg5.png[/img]](http://www.ubuntu-pics.de/bild/5916/screenshot_09_dkTfg5.png)

I use 96x96, should be default. If I don't write it to my xorg nvidia choses to set 110x108.
Modify your Screen section, and add these two lines to it:
```

	Option "UseEdidDpi" "FALSE"
	Option "DPI" "96 x 96"

```


Mine looks like this 
[color=red]NOTE: don't just copy and paste unless your identifiers are set up accordingly! Rather take this as an example, and modify your own Screen Section:[/color]
```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
	Option "UseEdidDpi" "FALSE"
	Option "DPI" "96 x 96"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Now we're going to add a Modeline as well, so that we don't need the autoselect option anymore. To have one generated for your screen run one of the tools xorg ships with, for instance gtf.
Usage is shown by gtf -h. I have a laptop with a max screen resolution of 1440x900, so for me this will generate a custom Modeline:
```

gtf 1440 900 60

```
60 is the desired refreshrate in this case, you may adjust it to your likings if you want.

I generated another with 100 refresh rate for me. Your output should look sth like this:
> 
me[~] gtf 1440 900 60

  # 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
  Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

me[~] gtf 1440 900 100

  # 1440x900 @ 100.00 Hz (GTF) hsync: 95.30 kHz; pclk: 187.55 MHz
  Modeline "1440x900_100.00"  187.55  1440 1544 1704 1968  900 901 904 953  -HSync +Vsync

me[~] 


Now copy your custom Modelines and add them to your xorgs Monitor section.
[color=red]SAMPLE, DON'T JUST COPY AND PASTE[/color]
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
    Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
    Modeline "1440x900_100.00"  187.55  1440 1544 1704 1968  900 901 904 953  -HSync +Vsync
EndSection

```

Now you should be able to increase your refresh rate in compiz, and notice some quite massive change
CCSM -> General Options -> Display Settings
[[img]http://www.ubuntu-pics.de/thumb/5918/screenshot_11_1ga8mZ.png[/img]](http://www.ubuntu-pics.de/bild/5918/screenshot_11_1ga8mZ.png)

And now, enjoy the ride :)

---

### Post by yosemite610 on 2008-11-23
Apparently my system doesn't have a 'video' group.

(Note: Intrepid/NVidia7600/Compiz working well until most recent update from the compiz ppa*, now crashes 'randomly': Nov 23 09:22:52 homer kernel: [153687.928112] compiz.real[976]: segfault at 1a0 ip 08069d8d sp bfdc5340 error 4 in compiz.real[8048000+34000])

*deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main

---

### Post by zivagolee on 2008-11-23
> **yosemite610 said:**
> Apparently my system doesn't have a 'video' group.

(Note: Intrepid/NVidia7600/Compiz working well until most recent update from the compiz ppa, now crashes 'randomly': Nov 23 09:22:52 homer kernel: [153687.928112] compiz.real[976]: segfault at 1a0 ip 08069d8d sp bfdc5340 error 4 in compiz.real[8048000+34000])

Mine segfaults as well too...

---

### Post by loomsen on 2008-11-23
This is the most probable reason. Installing the driver should've created the group.

You can check through the users admin gui as well if you prefer.

[[img]http://www.ubuntu-pics.de/thumb/6280/screenshot_03_LG6FGZ.png[/img]](http://www.ubuntu-pics.de/bild/6280/screenshot_03_LG6FGZ.png)

Do below steps to add a user to a group:
[[img]http://www.ubuntu-pics.de/thumb/6279/screenshot_07_hSA89F.png[/img]](http://www.ubuntu-pics.de/bild/6279/screenshot_07_hSA89F.png)

Here's my very custom xorg.conf. 
[color=red]Take it as an example, if you copy and paste it into yours it won't work, due to pretty obvious reasons.[/color]

```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "record"
#    Load           "xtrap"
    Load	   "dri"
EndSection

Section "ServerFlags"
    Option         "Pixmap" "32"
#    Option         "GlxVisuals" "typical"
#    Option         "Xinerama" "0"
    Option	   "DoubleScan" "true"
EndSection

Section "DRI"
	Group	"video"
	Mode	0666
EndSection

##################### INPUT
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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


#######################OUTPUT 1
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DFP"
    DisplaySize     384    240
#    HorizSync       30.0 - 75.0
#    VertRefresh     60.0
######################INTERLACED###############################
# 1440x900 240.19 Hz (CVT) hsync: 125.38 kHz; pclk: 248.75 MHz
#Modeline "1440x900_120.00"  248.75  1440 1560 1712 1984  900 903 909 1044 interlace -hsync +vsync
# 1440x900 119.69 Hz (CVT 1.30MA) hsync: 58.17 kHz; pclk: 110.75 MHz
#Modeline "1440x900_60.00"  110.75  1440 1528 1672 1904  900 903 909 972 interlace -hsync +vsync
#####################################################
# REDUCED_BLANKING 1440x900 59.90 Hz (CVT 1.30MA-R) hsync: 55.47 kHz; pclk: 88.75 MHz
	Modeline "1440x900R"   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync
# INTERLACED 1440x900 119.69 Hz (CVT 1.30MA) hsync: 58.17 kHz; pclk: 110.75 MHz
#	Modeline "1440x900_60.00"  110.75  1440 1528 1672 1904  900 903 909 972 interlace -hsync +vsync
# DEF_75VREF 1440x900 74.98 Hz (CVT 1.30MA) hsync: 70.64 kHz; pclk: 136.75 MHz
#	Modeline "1440x900_75.00"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
# DEFAULT 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
#	Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
######################################################
# COMPOSITE 
#   ModeLine       "1440x900" 88.75 1440 1488 1520 1600 900 903 909 926 composite
######################################################
#    Option "PreferredMode" "1440x900R"
    Option         "DPMS"
EndSection

Section "Device"

#	Option 		"AllowSHMPixmaps" "0"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
EndSection

Section "Screen"

#	Option         	"UseEdidDpi" "FALSE"
#	Option         	"DPI" "96 x 96"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "CustomEdid" "DFP:/etc/X11/edid.bin"
    Option         "AllowSHMPixmaps" "0"
    Option         "PixmapCacheSize" "4000000"
    Option         "ConnectedMonitor" "DFP"
    Option         "TripleBuffer" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "DamageEvents" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
#    Option         "TwinView" "0"
    Option         "metamodes" "DFP:1440x900R"
    SubSection     "Display"
        Depth       24
	Modes		"1440x900R" #"1440x900_60" "1440x900"
   EndSubSection
EndSection

```

---

### Post by yosemite610 on 2008-11-24
Thanks for the more detailed explanation, I'm now a member of the video group. Unfortunately, it doesn't seem to effect my problem with the segfaults.

Here's my xorg.conf:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load    "dbe"
	Load	"glx"
    	Load	"dri"
EndSection

Section "DRI"
	Group	"video"
	Mode	0666
EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Result of cat /var/log/Xorg.0.log | grep EE:
```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
```

Last compiz segfault:
```
Nov 24 00:36:36 homer kernel: [208514.236370] compiz.real[3592]: segfault at 1a0 ip 08069d8d sp bfde6360 error 4 in compiz.real[8048000+34000]
```

Unless there was a specific change in the last update (unofficial, from PPA noted in earlier post) which would elicit these 'new' permissions-based errors, I think it's un-related to permissions. I'd be happy to be proved wrong, however.

Any other ideas?

---

### Post by loomsen on 2008-11-24
Hmm, not much left I could tell you. How you get the latest compiz(0.7.9 atm) you can find in my signature.

Here are my sources.list entries for compiz, don't know which is actually maintained tho, I pulled compiz from git and compiled it myself (well, with a little help of omegas script actually :D )

```

# 		shame compiz
# wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
# deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./
# 		compiz PPA
# deb http://ppa.launchpad.net/compiz/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/compiz/ubuntu intrepid main
# deb http://ppa.launchpad.net/mvo/ubuntu intrepid main

```

You could make sure you've got all dependencies installed:
```

sudo apt-get build-dep compiz-gnome
```

Instead of compiz-gnome you may use any compiz metapackage, if you don't mind KDE you can simply use 
```

sudo apt-get build-dep compiz
```

You need some deb-src lines in your sources.list then as well tho.

You can check which version of compiz actually is installed with a handy little command line tool called apt-show-versions. As I said, 0.7.9 should be the latest, what I know.

Or just get Omegas script and build it yourself...

---

### Post by yosemite610 on 2008-11-25
> **loomsen said:**
> Hmm, not much left I could tell you. How you get the latest compiz(0.7.9 atm) you can find in my signature.

Followed your instructions, upgraded to git 0.7.9 and it looks like the segfault happens a lot less now (just one, am hoping it was an anomaly). I am seeing artifacting now, image attached...

> **loomsen said:**
> Or just get Omegas script and build it yourself...

Took a look around your SIG/posts and didn't see any link to 'Omega's' script?

---

### Post by loomsen on 2008-11-25
Here you go.

[But if you don't really know what you're doing, if you want your compiz to be handled through Synaptic and autoupdatet, better stick to that.](http://forum.compiz-fusion.org/showthread.php?t=7744)

The artefacts are obviously related to the nvidia driver. I've fixed them by upgrading to nvidia beta driver. Same here, if you don't know what to do, stick to the actual driver, or take envyng to chose the right one for you.

---

