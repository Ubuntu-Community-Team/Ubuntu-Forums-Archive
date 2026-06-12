---
title: "Intel 845GL Video Problems"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by sureluvmyspam on 2005-04-27
I just loaded Ubuntu on an older Gateway and it did not detect my video properly.  According to the Gateway site, this has an integrated Intel 845GL.  Other Linux distros (Xandros, Mepis, Knoppix) have detected it, but for some reason it is not right on Ubuntu.

The resolution is very low 640 x 480 with no other options.

A possitive note: Other than Xandros, this was the first disto I've tried that allowed me to browse my Windows network without much fuss.


Any suggestions?

---

### Post by daniels on 2005-04-27
It's a bug in the Intel driver, and it'll be fixed with the first xorg upload to Breezy; it's probably worth a hoary-updates release as well.

---

### Post by soljp on 2005-04-28
Same problem here.

I am very new to linux and have been wanting to switch for long time but did not find a distro that has some catch in it . Ubuntu 5.04 was a breath of fresh air. It has all that one can ask for. Many thanx to every one out here making this work.

Now the problem:

I have an Intel 845GVSR mother board with in-built video. I GB Ram, P4 2.4 GHz with 1MB L2 cache. Wanted to use this a file server and to hast some groupware apps. I tried installing Ubuntu and Kubuntu, the result is the same. It boots with 600x480 resolution with very low depth.

I even tried to tinker with the etc\X11\xorg.conf file. After this x crashed on startup. I was able to install arklinux and lycoris without any problems. It boot up well with 1024x768 res and gave me all the options.

Is there a patch? or a fix. any help please.

thanks and peace

---

### Post by sureluvmyspam on 2005-04-28
[QUOTE=daniels]It's a bug in the Intel driver, and it'll be fixed with the first xorg upload to Breezy; it's probably worth a hoary-updates release as well.[/QUOTE]
 Any idea when this will be fixed?

---

### Post by geopfm on 2005-04-28
I've been having the same problem also.  I googled around for a bit and one site said to change your bios shared memory from 1MB to 8MB.  Mine was already set to 8 so...still screwed.  Back to Suse for a while.

---

### Post by baza41 on 2005-04-28
[QUOTE=daniels]It's a bug in the Intel driver, and it'll be fixed with the first xorg upload to Breezy; it's probably worth a hoary-updates release as well.[/QUOTE]


This -really- is worth fixing in Hoary because there are a lot of intel based video cards out there. I don't really want to wait six months for something to be fixed that was not broken until xfree86 was replaced (too early?) by xorg.


Baza

---

### Post by sureluvmyspam on 2005-04-29
[QUOTE=daniels]It's a bug in the Intel driver, and it'll be fixed with the first xorg upload to Breezy; it's probably worth a hoary-updates release as well.[/QUOTE]


I just reloaded Xandros on that same computer with the Intel 845GL video driver and Xandros configures it correctly, so I checked to see what X system it uses and it is xorg.

---

### Post by sureluvmyspam on 2005-04-29
[QUOTE=baza41]This -really- is worth fixing in Hoary because there are a lot of intel based video cards out there. I don't really want to wait six months for something to be fixed that was not broken until xfree86 was replaced (too early?) by xorg.


Baza[/QUOTE]
 I agree.  I work on a system with about 60 computers made by Gateway and Dell and the majority have Intel integrated video.

---

### Post by sureluvmyspam on 2005-04-30
I fixed it!  

I loaded Xandros on the same system and went to the /etc/X11 directory and copied the xorg.conf onto a floppy.  Then I reinstalled Ubuntu and used the root shell to copy the xorg.conf from the floppy.  I rebooted to a high resolution screeen.  I did get an error that my x settings were different than my Gnome.  I just told it to overide the Gnome settings with the X.  Looks like it worked.  I can write this up in more detail if anyone is interested.

---

### Post by Zathras on 2005-05-01
[QUOTE=sureluvmyspam]I fixed it!  

I loaded Xandros on the same system and went to the /etc/X11 directory and copied the xorg.conf onto a floppy.  Then I reinstalled Ubuntu and used the root shell to copy the xorg.conf from the floppy.  I rebooted to a high resolution screeen.  I did get an error that my x settings were different than my Gnome.  I just told it to overide the Gnome settings with the X.  Looks like it worked.  I can write this up in more detail if anyone is interested.[/QUOTE]

Please do...I am!

Thanks,

Zathras

---

### Post by momo66 on 2005-05-01
[QUOTE=sureluvmyspam]I fixed it!  

I loaded Xandros on the same system and went to the /etc/X11 directory and copied the xorg.conf onto a floppy.  Then I reinstalled Ubuntu and used the root shell to copy the xorg.conf from the floppy.  I rebooted to a high resolution screeen.  I did get an error that my x settings were different than my Gnome.  I just told it to overide the Gnome settings with the X.  Looks like it worked.  I can write this up in more detail if anyone is interested.[/QUOTE]
 This happened to me as well it seems that it leaves out the Horizontal and Vertical sync lines in the xorg.conf file.  If you put these in manually it gives you the higher resolutions.

---

### Post by duglass on 2005-05-02
[QUOTE=sureluvmyspam]I fixed it!  

I loaded Xandros on the same system and went to the /etc/X11 directory and copied the xorg.conf onto a floppy.  Then I reinstalled Ubuntu and used the root shell to copy the xorg.conf from the floppy.  I rebooted to a high resolution screeen.  I did get an error that my x settings were different than my Gnome.  I just told it to overide the Gnome settings with the X.  Looks like it worked.  I can write this up in more detail if anyone is interested.[/QUOTE]


i would enjoy this too, i just installed on my dell and i am having the same problem.

thanks in advance

---

### Post by sureluvmyspam on 2005-05-02
[QUOTE=Zathras]Please do...I am!

Thanks,

Zathras[/QUOTE]
 Zathras,

I hope this works for you, too.

1. Download the Open Circulation edition of Xandros at: [http://www.xandros.com/about/downloads.html](http://www.xandros.com/about/downloads.html)
2. Run this on the computer with the Intel 845GL video.  
3. When the system boots into Xandros, navigate to /etc/X11 and copy the xorg.conf file to a floppy.
4. Run the Ubuntu install on the same system.
5. When it boots into Ubuntu, click on Places> Computer.  Open Floppy and copy drag the xorg.conf file to your desktop.
6.Open a root terminal (Applications>System Tools> Root Terminal)
7. In the root terminal, type cd /Desktop
8. Then type cp xorg.conf /etc/X11
9. Reboot the system and you should have a higher resolutions screen.
10. You may get a message that the xserver settings are different than the Gnome settings. I just clicked on Xserver overrites Gnome.

I haven't had any problems with this.... so far.
I'm sure there are just a few lines in there somewhere that could be edited, perhaps someone who knows more than I do can get in there and figure it out.

Good luck.

---

### Post by duglass on 2005-05-02
[QUOTE=sureluvmyspam]Zathras,

I hope this works for you, too.

1. Download the Open Circulation edition of Xandros at: [http://www.xandros.com/about/downloads.html](http://www.xandros.com/about/downloads.html)
2. Run this on the computer with the Intel 845GL video.  
3. When the system boots into Xandros, navigate to /etc/X11 and copy the xorg.conf file to a floppy.
4. Run the Ubuntu install on the same system.
5. When it boots into Ubuntu, click on Places> Computer.  Open Floppy and copy drag the xorg.conf file to your desktop.
6.Open a root terminal (Applications>System Tools> Root Terminal)
7. In the root terminal, type cd /Desktop
8. Then type cp xorg.conf /etc/X11
9. Reboot the system and you should have a higher resolutions screen.
10. You may get a message that the xserver settings are different than the Gnome settings. I just clicked on Xserver overrites Gnome.

I haven't had any problems with this.... so far.
I'm sure there are just a few lines in there somewhere that could be edited, perhaps someone who knows more than I do can get in there and figure it out.

Good luck.[/QUOTE]


is there anyway you could just post the xorg.conf file here. so i can just copy and paste it into my system?

---

### Post by duglass on 2005-05-02
here is a fix xorg config file.

it fixed my screen res issue

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
       FontPath        "unix/:7100"                    # local font server
       # if the local font server has problems, we can fall back on these
       FontPath        "/usr/lib/X11/fonts/misc"
       FontPath        "/usr/lib/X11/fonts/cyrillic"
       FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
       FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
       FontPath        "/usr/lib/X11/fonts/Type1"
       FontPath        "/usr/lib/X11/fonts/CID"
       FontPath        "/usr/lib/X11/fonts/100dpi"
       FontPath        "/usr/lib/X11/fonts/75dpi"
       # paths to defoma fonts
       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
       Load    "bitmap"
       Load    "dbe"
       Load    "ddc"
       Load    "dri"
       Load    "extmod"
       Load    "freetype"
       Load    "glx"
       Load    "int10"
       Load    "record"
       Load    "type1"
       Load    "vbe"
EndSection

Section "InputDevice"
       Identifier      "Generic Keyboard"
       Driver          "keyboard"
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
       Option          "Protocol"              "ImPS/2"
       Option          "Emulate3Buttons"       "true"
       Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
       Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
       Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
       Driver          "i810"
       BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
       Identifier      "Generic Monitor"
       ModelName       "Dell 1024x768 Laptop Display Panel"
       HorizSync       31.5 - 48.5
       VertRefresh     59.0 - 75.0
       Option          "DPMS"
EndSection

Section "Device"
       Identifier      "Videocard0"
       Driver          "i810"
       VendorName      "Videocard vendor"
       BoardName       "Intel 845"
       VideoRam        10000
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
       Monitor         "Generic Monitor"
       DefaultDepth    24
       SubSection "Display"
               Depth           1
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           4
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           8
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           15
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           16
               Modes           "1024x768" "800x600" "640x480"
       EndSubSection
       SubSection "Display"
               Depth           24
               Modes           "1024x768" "800x600" "640x480"
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
```


just copy and paste it into your xorg config file
i am running a Dell on the 845GL chipset, now at 1024x768

enjoy

---

### Post by osxjamie on 2005-05-02
I tried using your xorg.conf file and it crashed upon reboot so i am really glad i backed up the old one first.  i posted another thread on here "same video card, different symptoms" because while my problem is similar, i have different issues.  Basically what i ideally would like is somehow to configure it to where in the change resolution screen i can also choose my refresh rate.  upon initial installation i like many was stuck at 640 x 480.  somehow i managed to fix that but every other option is now at 85 hz and apparently my monitor can't handle that because it squeals and the vid card screws up on the login screen by moving most of the image off the monitor, moving the mouse to that side causes the image to slowly scoot back over and recenter itself.  honestly i'm not sure if my issue is the video card not working with current settings or monitor but i know the login screen thing suggests it is not the monitor because the monitor wouldn't respond to my mouse movements by recentering the image.

---

### Post by sureluvmyspam on 2005-05-03
[QUOTE=momo66]This happened to me as well it seems that it leaves out the Horizontal and Vertical sync lines in the xorg.conf file.  If you put these in manually it gives you the higher resolutions.[/QUOTE]

Here is the REAL Fix:

There **is **a line missing.  To fix it:
1. Open a terminal by clicking on >Applications > System Tools > Terminal
2. type sudo gedit /etc/X11/xorg.conf
3. you will be prompted for a password
4. In gedit, click on > File > Save Copy to back up original file  (should go to your home directory)
5. Click save.
6. Scroll down to section titled Section "Monitor" and add:
HorizSync 31.5-60 before the EndSection.  Should look something like this:

Section "Monitor"
[INDENT]Monitor       Gateway EV73"[/INDENT]
[INDENT]Option        "DPMS"[/INDENT]
[INDENT]**  HorizSync           31.5-60**[/INDENT]
EndSection

7.  Once you have made this change save the file and overwrite the orig xorg.conf.
8.  Restart the system and you should have high-rez graphics.

---

### Post by kelvinq on 2005-05-11
SUCCESS WITH ACER TRAVELMATE 820!

I just edited xorg.conf and added the lines "       HorizSync       31.5 - 48.5
       VertRefresh     59.0 - 75.0" after "Monitor" and now it works beautifully.

So your xorg.conf should look something like this:
==
Section "Monitor"
       Identifier      "Generic Monitor"
       ModelName       "Dell 1024x768 Laptop Display Panel"
       HorizSync       31.5 - 48.5
       VertRefresh     59.0 - 75.0
       Option          "DPMS"
EndSection
==

Apparently the modelname doesn't matter, it's generic anyway.

Good luck. Feel free to email me at [email]k-q@gmx.net[/email] if you need help. Hope the next ubuntu release will fix this. :)

---

### Post by nascent16 on 2005-05-18
It may also be a good idea to check your manual or online for the correct Horizontal and Vertical sync/refresh rates. I don't see how it would do permanent damage to an LCD, but keeping software settings consistent with hardware capabilities is always a good idea. I know Dell publishes this information online.

---

### Post by baza41 on 2005-05-18
[QUOTE=daniels]It's a bug in the Intel driver, and it'll be fixed with the first xorg upload to Breezy; it's probably worth a hoary-updates release as well.[/QUOTE]

I think it does rate a fix in Hoary rather than leaving it until, is it October Breezy comes out? I was a bit disappointed when I read the bugzilla that it was waiting for a fix in Breezy.

I know all use Intel on-board chip users, i810 etc. will love you if you send out a fix for Hoary.

Baza

---

### Post by INFT3920uniproject on 2005-05-19
[COLOR=Navy]Thanks heaps to all in this thread, especially duglass, as we have had the same problem on our uni lab PCs (Compaq Evo D51S model with Compaq 7500 monitor).  After installing Ubuntu 5.04, we were locked into the 640 x 480 res prob.  VERY annoying!! ](*,) 

A quicker fix than sureluvmyspam's Xandros d/l fix is to add the HorizSync and VertRefresh lines in the xorg.cnf file as demonstrated by duglass.  Agree with nascent16 with checking on the sync rates with the PC manufacturer. After doing this, we added the following two lines into the "Monitor" section (as shown by duglass). These are according to the Compaq specs:

[B]HorizSync 30.0 - 70.0
VertRefresh 50.0 - 140.0[/B]

That was it. Now works beautiful. Thanks again, everyone!   :grin:  

Note: Ubuntu correctly detected the 82845G/GL Intel vid chip and monitor and even put in the choices of resolutions automatically [up to 1024 x 768] so the ONLY thing missing was the Horiz and Vert sync rates.

Garth A.
Russ N.
INFT3920 class, University of Newcastle[/COLOR]

---

### Post by daniels on 2005-05-21
I'm organising a fix for hoary-updates now.

---

### Post by Silversierra on 2005-10-01
Thanks to those in this thread!  I finally got ubuntu working at higher than 640x480.

I have a dell e551c monitor, and I just had to add my HorizSync and VertRefresh rates, 30 - 54, and 50 - 120.

Wow, now that I'm not stuck in 640x480 it's much better.

---

### Post by PeaceMessenger on 2005-11-22
I'm trying to install Breezy to a Dell Inspiron 1100 which has Intel 845GL, and I'm not getting the right screen resolution.  It's basically unusable.  I tried the adding in the Horizontal and Vertical lines into the xorg.conf but all that did was cause xorg to not work.

Also, if I install the updates to Breezy that come up right after install, that does xorg in too, so it won't boot into Gnome and I just get a command line - looks just like when I tried fixing the xorg file myself.

What happened to all the promises to fix this under Breezy in this thread? I've tried to install multiple times and I'm tired of staying up late nights.  Maybe I need another distro, but I'd like to have my desktop and laptop on the same one, and Ubuntu works great on my desktop.

---

### Post by cdafoe on 2007-02-16
I am having very similiar problems to those listed above, but have tried all of the fixes suggested and can't get any of them to work.  However, i'm a novice to ubuntu/linux so it might be something I'm doing wrong.  Any help would be appreciated.  

Here's what I have:

Acer Tm230xv with an Intel 845GL chipset.  I can boot up Ubuntu 6.10 live cd, but it only will display 640x480.  I installed Ubuntu to the hd, and it was successful.  However, when it tries to boot off the hd, it starts booting, you can see some command-line comments on the screen, then the screen goes black and it never goes any farther.

Upon reading this forum, I made multiple changes to the xorg.conf file.  I couldn't figure out how to use the live-cd version to make changes to the HD, it kept telling me that hda1 was read-only, and I couldn't figure out how to change that.  I was able to boot it up with a Knoppix cd, which will allow me to edit files on hda1.

First I changed the HorizSync and VertRefresh settings to 31.5-48.5 and 59.0-75.0.  Didn't fix it.  Then I tried using 28-96 and 50-75 (because that is what it shows up as using when the Knoppix cd boots up).  That didn't work either.

Then I looked at the complete xorg.conf file that was posted above.  I found that I didn't even have the "Device" section that is right below the "Monitor" section.  So I added that. 

After doing that, it would get alot further in the boot process.  But then I get a graphical error message that says "Failed to start the X server.  Its likely that it is not set up correctly.  Would you like to view the X output to diagnose the problem"  Pressing return shows the following error messages:

Error:  i810(0) : No video bios modes for chosen depth
Error:  Screen(s) found, but none have a usable configuration.  
Fatal server error
No screens found.


I've tried everything I know find to fix the problem.  Any help would be appreciated.

Thanks 
Chris

---

### Post by MyMistake on 2007-11-29
PeaceMessenger,

Did you ever get you Inspiron 1100 working right? I'm trying with mine now and am having a terrible time with the video. I'd love to hear how you solved the problem.

Thanks!

---

