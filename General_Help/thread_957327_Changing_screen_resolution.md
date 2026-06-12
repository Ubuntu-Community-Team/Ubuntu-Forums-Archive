---
title: "Changing screen resolution"
date: 2008-10-24
forum: General Help
---

### Post by rmcellig on 2008-10-24
I just installed Ubuntu 8.04 on my HP DV2000 laptop (boy was that ever easy). My screen resolution is only 800x600 or 640x480. Those are my only options. How can I get a higher screen resolution?

---

### Post by matey3 on 2008-10-24
> **rmcellig said:**
> I just installed Ubuntu 8.04 on my HP DV2000 laptop (boy was that ever easy). My screen resolution is only 800x600 or 640x480. Those are my only options. How can I get a higher screen resolution?

I had the same problem, 
I think you can run the re-configurations (I think this command:?  sudo dpkg-reconfigure -phigh xserver-xorg)  or edit this file called xorg.conf under /etc/X11/
or look and see if there are other xorg.conf.xyz files there and rename them and then try them.
I did the last somehow my original xorg was good but it got renamed after I re-cofigured it? 
that folder (X11) has all the files you need I think.

---

### Post by jwhendy on 2008-10-24
I adjusted mine through xorg.conf.

In the ***Screen Section***, you should see some resolutions listed under 'modes:'. Just add your desired resolution in there. I cannot recall if that automatically changed my resolution or if it just made it appear in the system settings options.

If your looks like this:

Modes       "800x600" "640x480"

Make it look like this:

Modes       "1024x768" "800x600" "640x480"

Edit "1024x768" to whatever resolution you want to have... Hope this helps!

Save the file, log out, and log back in. If there's no change, open up your settings manager and see if there's a new option for your resolution. Sorry that I'm hazy on how to actually 'enable' the new setting... I can't remember offhand, but I know for sure you can get it in there via xorg.conf!


-John

---

### Post by rmcellig on 2008-10-24
Thanks John and Matey3. John, I am totally new to all of this and would like to know how to use and enable xorg.conf.

Thanks!!!

Randy

---

### Post by jwhendy on 2008-10-24
Not on the linux box right now, but I can get you through editing it...

From the terminal:

```

sudo nano /etc/X11/xorg.conf

```

This should open a file in the nano editor (what I use). You may get an error that you don't have nano. You can substitute 'vim' for 'nano' above to use the vim editor.

Once you see the file, scroll down until you see a section like this:

```

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "800x600" "640x480"
        EndSubSection
EndSection

```

You shouldn't need to change anything other than the 'Modes' line. Simply change it line to read:

```
Modes     "1024x768" "800x600" "640x480"
```

(Substitute your desired resolution for my "1024x768" placeholder). In nano, you can just type it in. In vim, you need to press 'i' which will get you into insert mode, at which point you can enter text. Don't worry if you get goofed, nothing is saved at this point.

Once you have the line how you want it and are sure about that, press Control+O in nano, and then Enter to write the file to the existing name of xorg.conf. Then press Control+X to exit.

If in vim, press Escape to get out of insert mode. Then type (with the colon) ':write' to write the file. Then type ':quit' to exit the editor.

Now you should just need to log out and back in, I believe. Then open up your settings manager and look for the new resolution you entered and choose it. If that doesn't work, try to restart. If that doesn't work, repost here and I'll try it tonight when I'm on my home computer and repost what I find.

If you goof anything up, just press Control+X in nano and exit without saving or type ':quit!' in vim to do the same. DO NOT save the file if you think you might have goofed something up. Better safe than sorry with this file - exit without saving, then restart from the beginning. Take your time and check your work :)

Let me know if this works!


-John

---

### Post by rmcellig on 2008-10-24
Hi John,

Sorry for some of the confusion I am having. I got to the part that says

Section "Screen"
Identifier "Default Screen"
Monitor   "Configured Monitor"
Device    "Configured Video Device"
End Section

How do I go to the place you described in your last posting. I don't see that. Maybe it's because I don't know how to navigate in this window.

Thanks John!!


Randy

---

### Post by jwhendy on 2008-10-24
Randy,


Want to send me your xorg.conf file?

You can email it to jw.hendy [at] gmail [dot] com. I'll take a look at it for ya.


-John

---

### Post by rmcellig on 2008-10-24
Sure. Where is it located?

---

### Post by jwhendy on 2008-10-24
Sorry - the location is the same as for editing it:

/etc/X11/xorg.conf


-John

---

### Post by lugolu on 2008-10-24
i have this problem since a week ago.

when linux try to boot 4 or 5 times try to init the X and then show an error message such as "this is a low resolution mode..." after that i can skip this message and init normally, but in 800x600.

i don't know what happened. i used it last monday and on tuesday doesn't work.

i tried to fix it installing ati drivers, but i couldn't.
([http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide))

when i execute fglrxinfo, it returns that is using mesa driver.

ubuntu 8.04
ati radeon 9200

---

### Post by jwhendy on 2008-10-24
Randy,


Try to just adding the section you see above so that your Screen Section looks like this:
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
                Modes     "1280x800" "800x600" "640x480"
        EndSubSection
EndSection

```
I read a bit about how Ubuntu handles configuration of the Xorg Server and it seems that it may just go with a default setting generated by trying to either detect your system, or if not specified, perhaps it just gives you the default options listed above. This edit will hopefully give you the added modes. I looked up your computer, and it's resolution should be as listed above. Hope it works!


-John

---

### Post by random turnip on 2008-10-24
This is quiete a common problem in Ubuntu.

Before ruching into all of these mountains of code make sure that you have given your account access to your graphics card.  This is pretty simple, go into System and make sure that you have clicked in your hardware section and entered your password.

Once you have done this you go into system again, then click on Screen Resolution and now the options supported by your graphics card will be in there.

---

### Post by rmcellig on 2008-10-24
Can I edit this file in a text editor? If not, how can I edit it from the terminal window?

Thanks John!!

Randy

---

### Post by rmcellig on 2008-10-24
Hi Random Turnip,

I have my Hardware Drivers window open and see under Device driver the NVIDIA accelerated graphics driver (latest cards). It is not enabled. When I select the enabled check box I get a Failed to Fetch followed by an internet address. 404 File not found. Should I go to the NVIDIA site and see if I can locate this driver?

nvidia-glx-new_169.12

If I can find it, how do I go about installing it in Ubuntu?


Thanks!!!

Randy

---

### Post by biowerks on 2008-10-25
Wow, I am really having a hard time getting this to work. I have edited my xorg.conf file to look like this:


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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 24
        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection


It started looking like this:

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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

as you can see there never was any description for "modes" I added the modes and tried to save and I get an error telling me:

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again. 

I do have administrative power... at least I think I do, I am using a username called owner that came with ubuntu when I downloaded it. (I had to get that username through the command line using ls /home then passwd owner so Im not sure if I have administrative power but I was able to create a new user and assign administrative power to that one and I tried it and got the same problem.

I am using gedit to try to write this stupid xorg.conf file so that I can actually use ubuntu.

---

### Post by blackened on 2008-10-25
> **biowerks said:**
>   

I do have administrative power... at least I think I do...

You don't. In the terminal type
```
gksudo gedit /etc/X11/xorg.conf
```

This will temporarily elevate you to superuser status (**su**peruser **do**) and allow you to change the file and save accordingly.

---

### Post by biowerks on 2008-10-25
Ok, I really want to use Ubuntu but I cant if the resolution is so messed up. All of my Icons are HUGE and the dialog boxes go off screen and I cant close some windows. It really is unusable. I have edited my xorg.conf file to look like this

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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        SubSection "Display"
                Modes     "1280x800" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

and when I go to change my resolution in system, prefrences, monitor resolution the only choices I have are 640 x 480 and 320 x 240. what am I doing wrong? Am I doing the wrong thing? I guess the best way to describe what I am trying to do is to say that when using windows you can slide the thing over to create more desktop space or less (making the Icons and windows smaller or larger) what do I need to do?

---

### Post by biowerks on 2008-10-25
I am now on my windows partition and I see that my post is formatted incorrectly. I dont know if the format of the text matters but in ubuntu the format has the tabs and spaces like the one above.

btw how do you get the box with the code in it to look like <tt>

---

### Post by biowerks on 2008-10-25
I fixed it myself. incase anyone wants to do this all you have to do is right click on applications and click on edit menus then click on other and add screens and graphics then goto that window and add your monitor from the list. My monitor wasnt on that list so I just kinda made it up... I have an eMachines computer and I know that it is made by gateway so I added a gateway monitor with the model numbers closest to my model and chose the resolution that I wanted and restarted and now Im in 1024x768 just like I wanted.

---

### Post by blackened on 2008-10-25
Just for information, could you post your current xorg.conf now that you have added the appropriate monitor?

Also, might just be release differences, but I don't have a menu called that available even through the menu editor.

---

### Post by biowerks on 2008-10-25
Sure no prob.

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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Gateway"
	Modelname	"Gateway FPD1730 R9"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1792x1344@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```



I actually have an eMachines F1770 monitor but Gateway FPD1730 R9 seemed close enough.

---

### Post by blackened on 2008-10-25
You're on Hardy right? Intrepid does all this differently I think. All I had to do to get my monitor working was specify hsync and vrefresh rates for it. Was able to get those off the side of the box it came in.

Anyway, glad you got it working, sorry I couldn't be any help.

---

### Post by Nylo on 2008-10-30
> **rmcellig said:**
> Hi John,

Sorry for some of the confusion I am having. I got to the part that says

Section "Screen"
Identifier "Default Screen"
Monitor   "Configured Monitor"
Device    "Configured Video Device"
End Section

How do I go to the place you described in your last posting. I don't see that. Maybe it's because I don't know how to navigate in this window.

Thanks John!!


Randy

Hey John,

I followed your instructions.  Why am I getting something different than you?

---

### Post by alberto ferreira on 2008-10-30
Press Alt+F2 then type "gksu displayconfig-gtk" and there choose your monitor and/or graphics card. Maybe it'll work

---

### Post by Nylo on 2008-10-30
> **alberto ferreira said:**
> Press Alt+F2 then type "gksu displayconfig-gtk" and there choose your monitor and/or graphics card. Maybe it'll work

After I paste "gksu displayconfig-gtk" nothing happens.  Whats the command line to get into my display?

---

### Post by jwhendy on 2008-10-30
I don't use Ubuntu, so I don't use 'gksu displayconfig-gtk'... All I know is xorg.conf, and my Screen Section looks like this:

```

Section "Screen"
    Identifier  "Videoconfig"
    Device      "Videocard1"
    Monitor     "Monitor1"

   DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes "1280x800_59.910" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1280x800_59.910" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

```

These listed resolutions are the ones that appear in my xfce settings manager. You can also run
```

xorgconfig

```
This gives you options to detect your hardware and settings. I ran it as myself, but you may have to do 'sudo xorgconfig' to actually save the file in /etc/X11/xorg.conf. I didn't need to alter mine, so I didn't go through the process to find out if I would have gotten a 'permission denied' at the end of the process.

Hope this maybe helps!



-John

---

### Post by jivabill on 2008-11-30
Well, I have a Compaq desktop small footprint machine about 5 years old.  I have a brand new out of the box Sylvania F70 Monitor.

I was running 7.10 Ubuntu, worked fine.  Then I made the mistake up upgrading to 8.04. Shortly after I did that I began to get Grub Error 18 on booting.  There seemed to be no real way in my case to overcome that so not finding a current Live CD for 7.10 I downloaded and installed 8.10.  And as to screen resolution it is a mess: all I get is 800 x 600 or 640 x 480 neither of which are very useful.

When I look at xorg.conf it does not have any data in SCREEN and MONITOR.  Just in SCREEN shows Identifier "Default Screen", Monitor "Configured Monitor", Device "Configured Video Device"

and in MONITOR shows "Configured Monitor"

No where else in the xorg.conf file are those configured items defined.  

So it looks like what we have here is that as Ubuntu evolves it goes further and further from working on hardware that is not brand new, seems to me that is one of the complaints about Vista.  Interesting.

Looks like my only option is to somehow go back to 7.10 and stay there.  If I can figure out how.
My two cents.
bill

---

