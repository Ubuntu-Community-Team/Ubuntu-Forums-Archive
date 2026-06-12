---
title: "Ati Radeon Xpress 200M + Edgy + FGLRX working how to"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by d-E-a-D on 2006-12-19
Ok, finally it's working! let's show how!
Running on HP Pavilion Dv5176.

[SIZE=4]Right now i'm out off time, but when i have some, i'll try to install ATI drivers from ATI site into version V 7.04
Right now just activate all options in the repositories,  do a update in System -> Administration -> Update Manager,  go to System -> Administration ->Restricted Drivers Manager and activate ATI driver.
NOTE: DESKTOP EFFECTS DOES NOT WORK !!!!! ATI DOES NOT SUPPORT COMPOSITE EXTENSION!![/SIZE] 

1st of all sorry 4 my bad English.
2nd I have Sideport ONLY activated.
3rd [SIZE=4]!!!! EDGY 32bit Fresh Install !!!! Users said that it works on 64bit too! :D[/SIZE] 

Download [ati-driver-installer-8.32.5-x86.x86_64]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run") driver from ati.

Now, step by step:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkp

sudo gedit /etc/X11/xorg.conf
```Add this to xorg.conf:
```
Section "Extensions"

    Option  "Composite" "Disable"

EndSection
```!!!! GO TO THE FOLDER WERE YOU DOWNLOAD ATI DRIVER !!!!

```
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r)

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh

sudo dpkg -i xorg-driver-fglrx_8.32.5-1*.deb
sudo dpkg -i fglrx-kernel-source_8.32.5-1*.deb
sudo dpkg -i fglrx-control_8.32.5-1*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

sudo shutdown -r now
```And that should work!

Now, let's get XGL and Beryl working:
Add this to your sources.list (/etc/apt/sources.list):
```
deb http://ubuntu.beryl-project.org/ edgy main
``````
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update

sudo apt-get install xserver-xgl
sudo apt-get install beryl emerald-themes

sudo gedit /usr/local/bin/startxgl.sh
```Add this to startxgl.sh:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
``````
sudo chmod a+x /usr/local/bin/startxgl.sh
sudo gedit /usr/share/xsessions/xgl.desktop
```Add this to xgl.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session by d-E-a-D
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```Logout with ctrl + alt + backspace

Change to session "Xgl" and login.
Run:
```
beryl-manager
```If you want you can add it to System - Preferences - Sessions to your startup.

Off topic, if you have MY LAPTOP SERIES with broadcom Wireless adapter, just do this after a fresh install:
```
sudo aptitude install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```And your broadcom will be working right away!

If you wan't to use a wireless manager, compwiz18 is tha man! :D just download his *.deb at [here]("http://ubuntuforums.org/showthread.php?t=299462").

EDIT: I stop using XGL and Beryl just because i need to use 3d at full throttle... i'm waiting for AIGLX and COMPIZ under ATI.

[size=4]TESTED ati-driver-installer-8.33.6-x86.x86_64 AND IT WORKS!!!! just follow this how to but with *8.33.6* instead *8.32.5*!!!! [/size]
Note: XGL NOT TESTED.

Cumps

---

### Post by ramasdf123 on 2006-12-20
hope fully this work, i am going to give it a shot now and replay back

---

### Post by kcallis on 2006-12-20
Was that for the 64-bit version or the 32-bit version of Edgy? Because I no longer see 32-bit version at ati.amd.com... All of the mergers... How is one suppose to keep up?

---

### Post by ramasdf123 on 2006-12-21
awesome it works on the 1st try so i'ill keep this updated if anything happens...

i would like to correct something though

```

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64 --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh

```

I had to change it to 

```

sudo ln -sf bash ~/Desktop
bash ati-driver-installer-8.32.5-x86.x86_64 --buildpkg Ubuntu/edgy
sudo ln -sf dash ~/Desktop

```

and when you download the ati-driver-installer-8.32.5-x86.x86_64 it is going to be *.run extention, you have to remove that to make it work

for now it works so if it does crash i will update

thank d-E-a-D

---

### Post by KLineD on 2006-12-21
Many many thanks to you d-e-a-d for this excellent guide. I was having a lot of troubles getting my ati card to work in edgy fresh install

---

### Post by thx_1138 on 2006-12-21
Good starter guide for users just wanting to get this done with minimal searching, I basically went through all these steps and the only thing I would add to it would be is to make sure the xgl.desktop file has been enabled to executed. This can be done by simply navigating to the /usr/share/xsessions/ folder and right clicking on the xgl.desktop icon and selecting Properties. Once there head to the properties tab and click on the checkbox next to Execute. Xgl would not load up properly unless I had enabled this.

I used these pages in which point out the exact same steps on this post
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL)
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

Enjoy the 3D desktop effects!

---

### Post by d-E-a-D on 2006-12-21
I've edited the post, it should be working now.

Now I'm trying to use compiz instead of beryl because its much stable, but i still getting problems, if anyone could make it working please report.

Cumps

---

### Post by paulobear on 2006-12-26
Hi dEaD --

Your post was a breath of fresh air -- mostly. :) 

The ATI driver now works for my HP DV8110us notebook -- an AMD64 Turion machine.  Woohoo!  I don't get a splash screen after I login -- all I see is the XWindows hashed screen and an 'x' mouse cursor.  The Gnome desktop manager starts up just fine.

But when I try to run beryl-manager, it catches signal 11, and all is messed up at that point.  There are no window widgets, (close, minimize, etc) and the desktop menu bar and the workspace bar is gone.  I can log out and then log back in to a Gnome XGL session so all is not lost.

I did try to set up my graphics memory to use both sideport and uma (udma??) and added 128Mb of shared memory (also tried no shared memory).  This resulted in the splash screen (after the login screen) to go pure white with an "arrow" mouse cursor.  It changes to the normal Gnome round/busy mouse cursor for a moment and then changes back.  There is some disk activity, and then it all just stops.  The mouse is mobile, but my desktop never shows up.

I didn't start from a clean Edgy install.  I had attempted to install fglrx/compiz some time earlier after I'd installed Edgy.  So there may be something messed up there.  I'll try to re-install some time this week.

All in all, I'm a very happy camper.  The fact that fglrx is working is a great step for me!

PaulOBear

---

### Post by TusharG on 2006-12-26
All though I started my card on the day when ATI released 8.32.5 drivers, I still see follow Error in /var/log/Xorg.0.log log, My card is working fine with glxgears, and with fglrxinfo is displaying correct information. 

LOG:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

---

### Post by paulobear on 2006-12-26
Hi - 

Hey, I have discovered that I'm having the same error:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

Any ideas?

Thanks,

PaulOBear

---

### Post by compwiz18 on 2006-12-26
> **paulobear said:**
> Hi dEaD --

Your post was a breath of fresh air -- mostly. :) 

The ATI driver now works for my HP DV8110us notebook -- an AMD64 Turion machine.  Woohoo!  I don't get a splash screen after I login -- all I see is the XWindows hashed screen and an 'x' mouse cursor.  The Gnome desktop manager starts up just fine.

But when I try to run beryl-manager, it catches signal 11, and all is messed up at that point.  There are no window widgets, (close, minimize, etc) and the desktop menu bar and the workspace bar is gone.  I can log out and then log back in to a Gnome XGL session so all is not lost.

I did try to set up my graphics memory to use both sideport and uma (udma??) and added 128Mb of shared memory (also tried no shared memory).  This resulted in the splash screen (after the login screen) to go pure white with an "arrow" mouse cursor.  It changes to the normal Gnome round/busy mouse cursor for a moment and then changes back.  There is some disk activity, and then it all just stops.  The mouse is mobile, but my desktop never shows up.

I didn't start from a clean Edgy install.  I had attempted to install fglrx/compiz some time earlier after I'd installed Edgy.  So there may be something messed up there.  I'll try to re-install some time this week.

All in all, I'm a very happy camper.  The fact that fglrx is working is a great step for me!

PaulOBear
Are you running Ubuntu 64bit? If so then you have a bug that isn't the fault of this tutorial.

---

### Post by paulobear on 2006-12-26
Yeah, I think I mentioned that.  So what's the bug?  Can you point me to a workaround?

Thanks,

PaulOBear

---

### Post by compwiz18 on 2006-12-27
Sorry, I was a little unclear because I wasn't sure if you were running 32bit on that 64bit processor or if you were running 64 on your 64.  anyways.  I just got mine working, had to compile from source.  But you can use my compiled stuff: [http://ubuntuforums.org/showpost.php?p=1934890&postcount=30](http://ubuntuforums.org/showpost.php?p=1934890&postcount=30)

---

### Post by d-E-a-D on 2006-12-27
> **paulobear said:**
> Hi - 

Hey, I have discovered that I'm having the same error:

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

Any ideas?

Thanks,

PaulOBear

AIGLX is on by default in Ubuntu 6.10 and ATI doesn't support AIGLX at least till today, that's why you get that error saying that AIGLX will turn off.
You can only use XGL with ATI fglrx drivers for now.
And 200M does not work with open source drivers... bad memory report or something.

Cumps

---

### Post by paulobear on 2006-12-28
Hi Cumps - 

I looked for AIGLX in Synaptic, but didn't really find anything except some packages that looked related, but not the main package(s).  Can you tell me what to look for, or what I need to do to turn off AIGLX?

Thanks,

PaulOBear

---

### Post by paulobear on 2006-12-28
Hi Compwiz - 

Doh! (whaps forehead).  Yes, I'm running Ubuntu-64 on an AMD64 Turion machine. :)  I'll give your debs a try.  Do you know if I'll still need to disable AIGLX and how I might do that?

PaulOBear

---

### Post by compwiz18 on 2006-12-28
> **paulobear said:**
> Hi Compwiz - 

Doh! (whaps forehead).  Yes, I'm running Ubuntu-64 on an AMD64 Turion machine. :)  I'll give your debs a try.  Do you know if I'll still need to disable AIGLX and how I might do that?

PaulOBear

AIGLX won't work - you have to use XGL with the ATI drivers, unless you are using the open source ones, which you won't be if you have a ATI 200M (they aren't supported), so yes, you will have to use XGL, and you'll have to disable AIGLX. see 
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) for disabling composite extension

---

### Post by paulobear on 2006-12-28
Hi Compwiz - 

Sorry for being dense.  I checked out the link you provided, but my xorg.conf already has the Composite extension disabled.  Is that all I need to do to disable AIGLX?  If so then why am I getting this AIGLX error?  Or is there something else that I need to do - blacklist, rmmod, uninstall a package?

Thanks,

PaulOBear

---

### Post by compwiz18 on 2006-12-28
Sorry - I'm a bit confused.  What program is giving you that AIGLX error? Beryl? If so, what part of Beryl? Something else? If so, what program?

---

### Post by paulobear on 2006-12-28
Hi Compwiz - 

There were two issues that I was having.  Both have been solved at this time.  Beryl lives! :)

The first was in X when it was starting up.  After logging in using an XGL session, that error showed up in the X log file (/var/log/Xorg.0.log):

(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

I googled "ubuntu disable AIGLX" and found the following: [http://www.nevercorner.net/forum/viewtopic.php?pid=8281](http://www.nevercorner.net/forum/viewtopic.php?pid=8281) which showed a means to turn off AIGLX in X:

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

I stuck the above code in xorg.conf near the composite disable code, and now I do not get the AIGLX error in the X log.

I still was having the second error which was beryl-manager catching signal 11 and dying.  To solve this issue, I installed your "hand crafted" debs and that rectified the problem.  :)

I have a lot to learn, just to make good use of this windows manager.  I don't understand probably a 10th of the options. :)

I do get constant requests to update beryl components from the update manager.  I have locked the current version for those components in Synaptic, but I still get the requests to update them.  Do I need to turn off the update manager or is there something I'm missing? (Well, I'm pretty certain there is sometihng that I'm missing. :))

I also notice that the shutdown option has gone missing since  I'm using fglrx.  The workaround is to logout, then shutdown.  When using gnome/metacitcy, I could suspend my notebook, but w/beryl, that's broken.  I can live w/it. :)

Thanks for everything dEaD and Compwiz!

Paul

---

### Post by compwiz18 on 2006-12-28
I just removed the Beryl repos since they are useless anyways...I guess I'll have to check the Beryl release page every once in a while.  Would be nice if they had a RSS feed for me...

---

### Post by TFrog on 2006-12-28
This was the absolute best How To I've found on setting up the ATI proprietary video drivers for the Xpress 200M chipset.  I followed DeAd's How To exactly for the first part and my fps went from a measly 600fps in glxgears -printfps to just shy of 1700fps in glxgears -printfps.  My hat is off to you DeAd.

My only problem was when I went to install Beryl.  My Edgy install wasn't fresh but I had errors when downloading the debs for Beryl.  The server timed out several times.  However, it appeared to install.  I removed Beryl for the one and only reason that it sucked up 600fps in speed from my chipset.  Oh well, I wasn't very much on GLITZ anyway.  Still a fine How To overall.  Thanks again.

---

### Post by nickpaton on 2006-12-28
HP Compaq nx6125 with Radeon Express 200M graphics with Edgy 6:10 32bit installed.

This HOWTO works a treat for installing the above drivers.

Not interested in Beryl, so haven't tried.

Many thanks DeAd for the hard work

Nick

---

### Post by compwiz18 on 2006-12-28
By the way, I'd like to confirm this works on 64bit Edgy.

---

### Post by paulobear on 2006-12-28
> **compwiz18 said:**
> By the way, I'd like to confirm this works on 64bit Edgy.

Yes, I can confirm this as well.

PaulOBear

---

### Post by xraykp on 2006-12-29
another one working!!  

HP dv8000 series--ati 200m 64 bit install

beryl running

---

### Post by TFrog on 2006-12-30
> **d-E-a-D said:**
> Ok, finally it's working! let's show how!
Running on HP Pavilion Dv5176.

1st of all sorry 4 my bad English.
2nd I have Sideport ONLY activated.
3rd [SIZE="4"]!!!! EDGY 32bit Fresh Install !!!![/SIZE] (64bit i think it should work too, if anyone gives a try please report)

Download [ati-driver-installer-8.32.5-x86.x86_64]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run") driver from ati.

Now, step by step:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bkp

sudo gedit /etc/X11/xorg.conf
```

Add this to xorg.conf:
```
Section "Extensions"

	Option  "Composite" "Disable"

EndSection
```

```
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r)

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh

sudo dpkg -i xorg-driver-fglrx_8.32.5-1*.deb
sudo dpkg -i fglrx-kernel-source_8.32.5-1*.deb
sudo dpkg -i fglrx-control_8.32.5-1*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

sudo shutdown -r now
```

And that should work!

Now, let's get XGL and Beryl working:
Add this to your sources.list (/etc/apt/sources.list):
```
deb http://ubuntu.beryl-project.org/ edgy main
```

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
sudo apt-get update

sudo apt-get install xserver-xgl
sudo apt-get install beryl emerald-themes

sudo gedit /usr/local/bin/startxgl.sh
```

Add this to startxgl.sh:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

```
sudo chmod a+x /usr/local/bin/startxgl.sh
sudo gedit /usr/share/xsessions/xgl.desktop
```

Add this to xgl.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session by d-E-a-D
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Logout with ctrl + alt + backspace

Change to session "Xgl" and login.
Run:
```
beryl-manager
```

If you want you can add it to System - Preferences - Sessions to your startup.

Off topic, if you have broadcom Wireless adapter, just do this after a fresh install:
```
sudo aptitude install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

And your broadcom will be working right away!

Could you do a How To for XGL/Beryl for those of us that use KDE/Kubuntu.  The rest of your How To is wonderful.  Got my Compaq from around 600fps to just shy of 1700fps.  I'd like to have something here to make my Winbloze friends jealous ;)  Not that I relish eye candy but I'd like to try it just as an experiment as well.

---

### Post by grimmson on 2007-01-01
your the best dead man i've seen in a long time. Thanks a lot for your time. have a toshiba satellite m115 and get 1400 fps in glxgears first try. You the man!!!

---

### Post by chuko on 2007-01-01
I switched from dapper to edgy just to have fglrx working on my hp dv5000 laptop, and it really worth a try, Success at the first attempt!!!!! REALLY thank you d-e-a-d!!!!! :-D :-D :-D :-D :-D :-D

---

### Post by kcallis on 2007-01-02
> **xraykp said:**
> another one working!!  

HP dv8000 series--ati 200m 64 bit install

beryl running
Almost a winner... My DV8000 is running well under 64-bit and edgy and was able to get the fglrx running on the first go with the how-to. The problem is that I when I tried to above my abilities and step up to Beryl this is what I ran into:

kcc ~ $ glxinfo 
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 1.2 (2.0.6234 (8.32.5))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon

kcc ~ $ glxgears &
[1] 16266
kcc ~ $ Xlib:  extension "XFree86-DRI" missing on display ":1.0".
X connection to :1.0 broken (explicit kill or server shutdown).

Now is that correct, or am I missing something? Also, how does one get info on how many fps are running?

---

### Post by damagedspline on 2007-01-03
Well, I would like to thank the howto collector
I got beryl & 8.32.5 fglrx working on a Fujitsu-Siemens Amilo A1650G (turion 64 & xpress 200) with i386 ubuntu.

Just a small question: Am I the only one with bad video decoding performance @fullscreen?

I've tried X11, Xv and gl (2) - all with bad fps or hard frame dropping.

Edit: btw, forgot to mention, resume from suspend stopped working - worked ok on 8.28.8

---

### Post by nawzyah on 2007-01-06
I tried following this guide but ran into some issues.  I wanted to chime in because I've searched this forum and google for a solution to no avail.

I posted a new thread if you're so inclined to help just follow the link: [http://www.ubuntuforums.org/showthread.php?t=332501]("http://www.ubuntuforums.org/showthread.php?t=332501")

Just a gist of what the issue is:  I'm running i386 Ubuntu on a Toshiba A105-S2111 laptop with Xpress 200m, but the Phoenix BIOS lacks any UDA/Sideport configuring functions.  This leads me to black screens after boot instead of the GUI login.

---

### Post by baosheng on 2007-01-06
Hi guys, I followed exactly this how-to and XGL session can be logged in well. But after I started beryl via "beryl-manager", the whole screen doesn't response to my mouse and keyboard. I even can't use Alt+F1~F6 to switch to console. How does this happen? How can I fix this problem?

---

### Post by brandon moore on 2007-01-06
the how-to looks great. i've made it roughly halfway through but i'm having some trouble with this step:

```
sudo module-assistant build fglrx
```

i'm on a turion 64 laptop, if that helps

here is the log file, where i think the error is occurring:

```

 &#9474; dh_testroot                                                                &#8593; 
 &#9474; rm -f configure-stamp                                                      &#9646; 
 &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               &#9618; 
 &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        &#9618; 
 &#9474; rm -rf .tmp_versions                                                       &#9618; 
 &#9474; rm -rf patch                                                               &#9618; 
 &#9474; dh_clean                                                                   &#9618; 
 &#9474; rm /usr/src/modules/fglrx/debian/control                                   &#9618; 
 &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      &#9618; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           &#9618; 
 &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               &#9618; 
 &#9474; /usr/src/modules/fglrx/debian/control; \                                   &#9618; 
 &#9474;         fi                                                                 &#9618; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   &#9618; 
 &#9474;         mv /usr/src/modules/fglrx/debian/postinst   
 &#9474; dh_clean                                                                   &#8593; 
 &#9474; rm /usr/src/modules/fglrx/debian/control                                   &#9618; 
 &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      &#9618; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           &#9646; 
 &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               &#9618; 
 &#9474; /usr/src/modules/fglrx/debian/control; \                                   &#9618; 
 &#9474;         fi                                                                 &#9618; 
 &#9474; if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   &#9618; 
 &#9474;         mv /usr/src/modules/fglrx/debian/postinst                          &#9618; 
 &#9474; /usr/src/modules/fglrx/debian/fglrx-kernel-2.6.19.1.postinst; \            &#9618; 
 &#9474;         fi                                                                 &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; touch configure-stamp                                                      &#9618; 
 &#9474; dh_testdir                                                                 &#9618; 
 &#9474; /usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
 &#9474; make[1]: Entering directory `/usr/src/linux-headers-2.6.19.1'              &#8593; 
 &#9474;   CC [M]  /usr/src/modules/fglrx/firegl_public.o                           &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:89:26: error: linux/config.h: No    &#9618; 
 &#9474; such file or directory                                                     &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:456: warning: initialization from   &#9618; 
 &#9474; incompatible pointer type                                                  &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function &#8216;firegl_stub_open&#8217;:    &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:579: warning: assignment discards   &#9618; 
 &#9474; qualifiers from pointer target type                                        &#9646; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function                        &#9618; 
 &#9474; &#8216;firegl_put_user_ptr&#8217;:                                                     &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#9618; 
 &#9474; to integer of different size                                               &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#9618; 
 &#9474; to integer of different size    
 &#9474; /usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#8593; 
 &#9474; to integer of different size                                               &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#9618; 
 &#9474; to integer of different size                                               &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_request_irq&#8217;:    &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:2568: warning: passing argument 2   &#9618; 
 &#9474; of &#8216;request_irq&#8217; from incompatible pointer type                            &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c: In function                        &#9618; 
 &#9474; &#8216;__ke_unregister_ioctl32_conversion&#8217;:                                      &#9618; 
 &#9474; /usr/src/modules/fglrx/firegl_public.c:2591: warning: &#8216;return&#8217; with a      &#9618; 
 &#9474; value, in function returning void                                          &#9618; 
 &#9474; make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1              &#9618; 
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/linux-headers-2.6.19.1'               &#9646; 
 &#9474; make: *** [build] Error 2                                                  &#8595; 
 &#9474; 
```

---

### Post by compwiz18 on 2007-01-07
Hello again!

I can help.  The nice people on the wiki where this info came from were so kind as to remove my fix for this error, but I think I can help you.

Change to /usr/src/modules/fglrx and then make a linux directory.  Now touch config.h: something like this
```

cd /usr/src/modules
sudo mkdir linux
sudo touch config.h

```

---

### Post by brandon moore on 2007-01-07
> **compwiz18 said:**
> Hello again!

I can help.  The nice people on the wiki where this info came from were so kind as to remove my fix for this error, but I think I can help you.

Change to /usr/src/modules/fglrx and then make a linux directory.  Now touch config.h: something like this
```

cd /usr/src/modules
sudo mkdir linux
sudo touch config.h

```


Thanks again for helping me out here....

```
brandon@brandon-laptop:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect
brandon@brandon-laptop:~$ cd /usr/src/modules/fglrx/
brandon@brandon-laptop:/usr/src/modules/fglrx$ ls
agp3.c         configure-stamp  drm_proc.h          linux
agp_backend.h  debian           firegl_public.c     Makefile
agpgart_be.c   drm_compat.h     firegl_public.h     make.sh
agpgart.h      drm.h            i7505-agp.c         nvidia-agp.c
agp.h          drm_os_linux.h   libfglrx_ip.a.GCC3
config.h       drmP.h           libfglrx_ip.a.GCC4
brandon@brandon-laptop:/usr/src/modules/fglrx$ cd linux/
brandon@brandon-laptop:/usr/src/modules/fglrx/linux$ ls
config.h
brandon@brandon-laptop:/usr/src/modules/fglrx/linux$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

```

This was after a restart. Do I need to do anything else?

---

### Post by commike37 on 2007-01-07
I have an HP Pavilion dv8000z (probably one of the worst laptops for Linux) with Dapper, and here's my experience.

I got the XPress 200M to work following the "Method2" directions from the following link (but instead using the 8.32.5 driver).  The method given there is very close to your directions, but for some reason something went wrong when I used your directions.  It doesn't matter if I use shared memory or not, which was an issue for some users.
[[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

bcm43xx-fwcutter got my wireless light activated, but it still doesn't seem to work.  Scanning with
```
iwlist eth1 scan
```
only works some of the time, but every attempt to connect to a network so far has failed and usually causes nothing to turn up with a scan.  It's not a huge deal to me, though, as a while back I bought I wireless card as a solution to this problem.

---

### Post by compwiz18 on 2007-01-07
> **brandon moore said:**
> Thanks again for helping me out here....

```
brandon@brandon-laptop:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect
brandon@brandon-laptop:~$ cd /usr/src/modules/fglrx/
brandon@brandon-laptop:/usr/src/modules/fglrx$ ls
agp3.c         configure-stamp  drm_proc.h          linux
agp_backend.h  debian           firegl_public.c     Makefile
agpgart_be.c   drm_compat.h     firegl_public.h     make.sh
agpgart.h      drm.h            i7505-agp.c         nvidia-agp.c
agp.h          drm_os_linux.h   libfglrx_ip.a.GCC3
config.h       drmP.h           libfglrx_ip.a.GCC4
brandon@brandon-laptop:/usr/src/modules/fglrx$ cd linux/
brandon@brandon-laptop:/usr/src/modules/fglrx/linux$ ls
config.h
brandon@brandon-laptop:/usr/src/modules/fglrx/linux$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

```

This was after a restart. Do I need to do anything else?
Oops, sorry, did you run **sudo module-assistant build fglrx** again?

---

### Post by d-E-a-D on 2007-01-07
> **commike37 said:**
> I have an HP Pavilion dv8000z (probably one of the worst laptops for Linux) with Dapper, and here's my experience.

I got the XPress 200M to work following the "Method2" directions from the following link (but instead using the 8.32.5 driver).  The method given there is very close to your directions, but for some reason something went wrong when I used your directions.  It doesn't matter if I use shared memory or not, which was an issue for some users.
[[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

bcm43xx-fwcutter got my wireless light activated, but it still doesn't seem to work.  Scanning with
```
iwlist eth1 scan
```
only works some of the time, but every attempt to connect to a network so far has failed and usually causes nothing to turn up with a scan.  It's not a huge deal to me, though, as a while back I bought I wireless card as a solution to this problem.

This how to is ONLY for EDGY and works perfectly... in dapper i use some other method for Xpress 200M and i can only use 8.24 drivers. For broadcom i have to install some home made package to work (Thanks to compwiz18 ). As i said, this is a EDGY HOW TO.

Cumps

---

### Post by baosheng on 2007-01-07
hi, guys.
I followed all these steps but I got following output after I entered beryl-manager

forrest@flavia:~$ XGL Present
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

Is there anything else I need to configure?

---

### Post by brandon moore on 2007-01-08
> **compwiz18 said:**
> Oops, sorry, did you run **sudo module-assistant build fglrx** again?

Okay, I finished running the rest of the commands after this one. I have an glx login and direct rendering is enabled. But when I login to a glx session and run beryl-manager, it doesn't seem to work properly... the titlebar goes away and I can't switch desktops at all.

---

### Post by bladez90 on 2007-01-08
I am having trouble with my Radeon Xpress 200 (RS482) not 200M, the setup seemed to work properly but the 3D acceleration is strange and when i tried to sign in to the xgl session the screen went white and I had to restart the x server again.

Here is my "/etc/X11/xorg.conf" file (only the video part)

```
Section "Monitor"
	Identifier   "Acer AL1714"
	HorizSync    30.0 - 82.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS482)"
	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseInternalAGPGART" "no"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200 (RS482)"
	Monitor    "Acer AL1714"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"

	Option  "Composite" "Disable"

EndSection
```

This is my "fglrxinfo"

```

evan@evan-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

And this is a screen shot of the strange 3D acceleration:

[IMG]http://i6.photobucket.com/albums/y216/bladez90/Screenshot.png[/IMG]

Any help would be much appreciated. Thx in advance.](*,)

---

### Post by d-E-a-D on 2007-01-09
Bladez90 that's memory issues... Try to use Sideport ONLY memory in BIOS settings, if that doesn't work, try other combinations like UMA + Sideport or UMA only, things like that.

Cumps

---

### Post by compwiz18 on 2007-01-09
> **brandon moore said:**
> Okay, I finished running the rest of the commands after this one. I have an glx login and direct rendering is enabled. But when I login to a glx session and run beryl-manager, it doesn't seem to work properly... the titlebar goes away and I can't switch desktops at all.
What version of Beryl and what platform? 32bit or 64bit? Edgy or Dapper?   Sorry if you already answered those in another thread...

64bit gave me a bit of trouble...at least your graphics drivers worked.

---

### Post by brandon moore on 2007-01-09
> **compwiz18 said:**
> What version of Beryl and what platform? 32bit or 64bit? Edgy or Dapper?   Sorry if you already answered those in another thread...

64bit gave me a bit of trouble...at least your graphics drivers worked.

It all seems to be working fine now that I'm on a 32-bit system.  In fact, it may have worked on the 64 bit install, but I didn't try it because glxinfo | grep render said direct rendering wasn't working. I tried it on the 32 bit install anyway and it cranked right up! The only trouble I'm having is getting the themes to work - no big deal.

The interesting thing is that this is the output I get from glxinfo | grep render on this install:

```
brandon@brandon-gateway:~$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON XPRESS Series Generic

```

---

### Post by compwiz18 on 2007-01-09
If you are using the XGL session, direct rendering should be no.  If you aren't, then it should:

```
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON XPRESS Series Generic

```

look like that

---

### Post by bettermentflux on 2007-01-10
> **d-E-a-D said:**
> 
EDIT: I stop using XGL and Beryl just because i need to use 3d at full throttle... i'm waiting for AIGLX and COMPIZ under ATI.


Have you heard something that would give us hope of running AIGLX on the ATI Xpress 200M?

Crossing fingers...

---

### Post by d-E-a-D on 2007-01-10
> **bettermentflux said:**
> Have you heard something that would give us hope of running AIGLX on the ATI Xpress 200M?

Crossing fingers...

lololol no... :(  I'm just waiting and "Crossing fingers..." like you...

Cumps

---

### Post by compwiz18 on 2007-01-11
Ditto.  Beryl takes too much juice out of my poor little 200M...and I can't stand the GNOME processor graph jumping around even when I'm not doing anything.  That's one of the reason I dumped XP - my Ubuntu only does what I want, when I want.  Not when the computer decides it wants to - with the exception of the update notifier, of course.

---

### Post by d-E-a-D on 2007-01-11
> **compwiz18 said:**
> Ditto.  Beryl takes too much juice out of my poor little 200M...and I can't stand the GNOME processor graph jumping around even when I'm not doing anything.  That's one of the reason I dumped XP - my Ubuntu only does what I want, when I want.  Not when the computer decides it wants to - with the exception of the update notifier, of course.

Your words are my words... thanks for the... "words"... lol

Cumps

---

### Post by tuxsg on 2007-01-11
It works for me too! after some tricky changes...

HPdv8310us (hpdv8000 series).

Now the adept updater shows updates for the beryl debs, I installed your compiled ones.

Should I update? if not, how can I mark this ackages for no appear again? Deleting the beryl repositories?


How can I get more themes?

Thanks a lot!

---

### Post by mikesignguy on 2007-01-12
$ glxgears -printfps

---

### Post by hollerith on 2007-01-13
For those with PC World Advent 7105PA laptops:  THIS WORKS.  Thanks all.  

Fresh install Edgy, follow this guide IMPORTANT: don't forget to recompile the ati-driver AGAIN after you install Beryl and to start Beryl-Manager otherwise you'll just see the meta-city manager, and get the errors mentioned in this post.  

I did get 'module-assistant not found'* errors which I'll have to investigate, but it didn't affect me since I just reran the whole ati script. 

* Any ideas?  I think I saw something on the zillions of threads but can't remember where...

Now to get that Marvell Libertas integrated WLAN adapter] working...

---

### Post by xxrealmsxx on 2007-01-14
Everything worked, however I am unable to choose Beryl as a window manager. My system just sticks to Gnome :(.

realms@realms-laptop:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension
realms@realms-laptop:~$ glxgears -printfps
10194 frames in 5.0 seconds = 2038.796 FPS
12918 frames in 5.0 seconds = 2583.554 FPS
12904 frames in 5.0 seconds = 2580.684 FPS
14224 frames in 5.0 seconds = 2844.654 FPS
15089 frames in 5.0 seconds = 3017.620 FPS
14892 frames in 5.0 seconds = 2978.218 FPS
15484 frames in 5.0 seconds = 3096.615 FPS
11283 frames in 5.0 seconds = 2256.518 FPS
realms@realms-laptop:~$ grep "Driver" /etc/X11/xorg.conf
        Driver      "kbd"
        Driver      "mouse"
        Driver      "synaptics"
        Driver      "wacom"
        Driver      "wacom"
        Driver      "wacom"
        Option      "VendorName" "ATI Proprietary Driver"
        Driver      "ati"
        Driver      "fglrx"


What am I doing wrong?

---

### Post by xxrealmsxx on 2007-01-14
Ok I figured it out, I was not selecting an XGL session.

Works now, Thanks!

---

### Post by erkki70 on 2007-01-15
Many thanks d-E-a-D!!!
Works like a charm on a Fujitsu-Siemens Scaleo J 1610. (or 1510 not sure as the PC belongs to a friend)
Only 512 mb RAM but very snappy and useable.
Couple of reboot were needed as I had issues with window borders not showing properly but all stable Beryl now.
My friend is enjoying his PC and doesn't want to boot up XP anymore ;)
Great how-to, thanks again.

Cheers,

Erkki

---

### Post by locutus42 on 2007-01-15
Nice work. Starting from a script posted to another thread, I finally have ATI 200M 3D support working with Sideport-only on a Compaq R4000 w/Dapper LTS.

FYI, I'd modified the version of the ati-8.32.5-builder.sh script for easy upgrades to newer ATI driver versions. I now just need to change the version number on one line( ATIVERSION=...). Doing the same sort of thing with the Edgy scripts could also ease updates to new driver versions.

```

#!/bin/bash
#
# filename: ati-fglrxDriver-builder.sh
#
apt-get update
apt-get install module-assistant build-essential wget
apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
ATIVERSION=8.32.5
ATIVERSION=8.33.6
DRIVER=ati-driver-installer-${ATIVERSION}-x86.x86_64.run
if [ -f ${DRIVER} ] ; then
  echo "already have ${DRIVER}"
else
  wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/${DRIVER}
fi
chmod +x ${DRIVER}
./${DRIVER} --buildpkg Ubuntu/dapper
dpkg -i xorg-driver-fglrx_${ATIVERSION}-1_i386.deb fglrx-kernel-source_${ATIVERSION}-1_i386.deb fglrx-control_${ATIVERSION}-1_i386.deb
rm /usr/src/fglrx-kernel*.deb
module-assistant prepare
module-assistant update
module-assistant build fglrx
module-assistant install fglrx
depmod -a
aticonfig --initial
aticonfig --overlay-type=Xv

```

---

### Post by compwiz18 on 2007-01-16
Another thing I found if you compile your own kernel is that it will place a deb with the fglrx drivers for the new kernel in /usr/src/, and you can just double click install for upgrade.

---

### Post by oveh on 2007-01-18
Works perfect with my ati x300 card! Thank you :mrgreen:

---

### Post by brandon moore on 2007-01-18
all was working perfectly until i did today's beryl upgrades... any idea how to fix it now? it just crashes.

---

### Post by compwiz18 on 2007-01-19
There shouldn't of been any updates...

Anyway, if I remember, you're using amd64?  So you will probably have to reinstall my debs from the other post.

If you aren't using amd64, I don't know why it would crash...should be fixed quickly then.

---

### Post by Zinnin on 2007-01-19
hey, I went through the tutorial and got the following error upon loading beryl 

** (beryl-manager:6194): WARNING **: Beryl caught deadly signal 11

I had it installed, but screwed it up somehow after it was working, since it was a fresh install I just redid the ubuntu install and redid the tutorial, but instead of working perfectly like it did before I am getting that error...I am out of ideas help would be welcome

I am running a 

Compaq Persario V5000 Laptop
AMD Sempron Mobile 
512 mb ram, 128 of it is shared to the ATI Radeon Xpress 200m

---

### Post by xxrealmsxx on 2007-01-20
I did the update as well and it broke.

However, with a recent upgrade to 0.2 and following the instructions on the first post mine is working on a zv6000.

---

### Post by LavaHot on 2007-01-21
hey guys, i'm having trouble with the driver, when I enter ```
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
``` it says there's no such file, I tried the fix toward the bottom of page 1, but that didn't help. any suggestions?

---

### Post by BGreet on 2007-01-21
For some reason when I try and run an XGL session my screen goes white and I can't see anything (I know the session is still going on as sound still works, and I can faintly see some menus when I click around).  I have a dv8000, running 32bit ubuntu 6.10, and followed the instructions on page 1 to a t with no errors coming up.  Any ideas what it could be?  Thanks 

Edit:  Sorry, figured it out had both UMA and Sideport memory active in bios

---

### Post by kason on 2007-01-23
kason@Senator:~$ sudo dpkg -i xorg-driver-fglrx_8.32.5-1*.deb
dpkg: error processing xorg-driver-fglrx_8.32.5-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.32.5-1*.deb

I was following the tutorial allong when I got that error. Any idea how to resolve the issue? I hope I am not missing anything completely obvious. Thanks.

---

### Post by rlozano on 2007-01-24
anybody knows how you do it in an edgy that is not fresh install and have an existing fglrx already?

thanks in advance and would appreciate feedback. :)

---

### Post by compwiz18 on 2007-01-24
> **rlozano said:**
> anybody knows how you do it in an edgy that is not fresh install and have an existing fglrx already?

thanks in advance and would appreciate feedback. :)
It should just work.  Try it.  You can't do anything irreversibly bad to it.  edit: Just backup /etc/X11/xorg.conf before you mess with anything.

---

### Post by page1ink. on 2007-01-25
awesome! it worked right away! thank you =)

---

### Post by Zinnin on 2007-01-25
I got it working now, all I did was get the updated beryl and it started working fine

---

### Post by spednik on 2007-01-27
hey there. 

I was running a previous version of fglrx (8.28 i think), but heard upgrading would help my pitifull xpress 200 run beryl.   everything worked fine until the  ```
sudo aticonfig --initial
``` 
when i run that, i get the ouput 
```
Found fglrx primary device section
Nothing to do, terminating.
```

if anyone could help, that would be great, thanks in advance.

---

### Post by Zuuswa on 2007-01-27
I just recently upgraded my 6.06 LTS to Edgy Eft, and rightly so, it Eft my video drivers up . . . I had FGLRX installed and running fine, with XGL and Beryl and the works, but after following this and many other 'how-to's in the forum, I cannot get Direct Rendering to work.  fglrxinfo and glxinfo both tell me that I have the dreaded Mesa driver issue . . . I have tried numerous ways to fix this, but to no avail.  It appears to me that the FGLRX module isnt being loaded by the kernel, but when I try to manually load it, my comp hard-locks right after I stop gdm.  I have a Compaq Presario R4000 series laptop, running a 32 bit install on a 64 bit processor.  Switching between UMA, Sideport and UMA+Sideport didnt make any differance.  If anybody can help me with this, I would appreciate it.

And spednik, that output is perfectly normal.  It is simply telling you that your xorg.conf file already has fglrx listed as your device driver, so aticonfig --initial didnt need to do anything.

. . : : EDIT : : . .
Ok, so I decided today I would try to get the drivers working on my 64 bit installation.  Under Dappr 64, FGLRX would not work, much like the problem I stated above . . . yet after upgrading to Edgy 64, I followed the same exact steps for installing the driver and now I have full 3d acceleration!  All I know is, the next computer I purchase will NOT have an ati chipset . . . despite years of loyalty to the company, I must abandon them for NVidia because ati refuses to support their open source consumers.

---

### Post by demonhunter on 2007-01-29
fellows,

is it working using UMA+Sideport?? Or are you guys using just Sideport or just UMA?

thnx.

---

### Post by dragonlor20 on 2007-01-30
Thank you thank you thank you thank you thank you thank you thank you thank you....  will always remember 2am on Jan. 30th as the day I got windows that wiggle.

---

### Post by dutchman25 on 2007-01-30
I have a HP dv5000 with a Ati Xpress 200M card running 64-bit Kubuntu.  I have not had success with this tutorial even though it seems like everyone else has.

Here's my problem: Everything dealing with the fgrlx driver installs without error.  But when I "fgrlxinfo" I get:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Additionally, when I "modprobe fglrx," I get: (after dmesg | tail)
[  587.379477] [fglrx] Maximum main memory to use for locked dma buffers: 904 MBytes.
[  587.379661] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed.

Any help would be tremendously appreciated.

---

### Post by hotshot23t on 2007-01-31
Hi I was going through the steps and I ran into an error.  When I ran **sudo module-assistant build fglrx**  I got an error saying it could not build fglrx-kernel-source.  I then tried the post from compwiz18 with the follow commands.

cd /usr/src/modules
sudo mkdir linux sudo 
touch config.h  

I tried it again and still had the same error.  Any help is appreciated! Thanks

---

### Post by ctt1wbw on 2007-01-31
> **bladez90 said:**
> I am having trouble with my Radeon Xpress 200 (RS482) not 200M, the setup seemed to work properly but the 3D acceleration is strange and when i tried to sign in to the xgl session the screen went white and I had to restart the x server again.

Here is my "/etc/X11/xorg.conf" file (only the video part)

```
Section "Monitor"
	Identifier   "Acer AL1714"
	HorizSync    30.0 - 82.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS482)"
	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseInternalAGPGART" "no"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200 (RS482)"
	Monitor    "Acer AL1714"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"

	Option  "Composite" "Disable"

EndSection
```

This is my "fglrxinfo"

```

evan@evan-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)
```

And this is a screen shot of the strange 3D acceleration:

[IMG]http://i6.photobucket.com/albums/y216/bladez90/Screenshot.png[/IMG]

Any help would be much appreciated. Thx in advance.](*,)

This section of your xorg.conf file:

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200 (RS482)"
	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseInternalAGPGART" "no"
	BusID       "PCI:1:5:0"
EndSection

I had to change the driver to read fglrx instead of ati and mine worked.

---

### Post by sdmike on 2007-01-31
Ok I did everything correctly and it worked
Then when I rebooted and logged into XGL, the beryl icon came up in the toolbar but no cool special effects came up.

WHAT HAPPENED?

Just when I thought I had it I lost it.

:)

---

### Post by ctt1wbw on 2007-01-31
If you saw the beryl splash screen, things should work.  Do you have the beryl emerald icon in your top panel?

---

### Post by sdmike on 2007-01-31
I didn't see the splash screen BUT I do have the beryl-manager icon.

---

### Post by ctt1wbw on 2007-01-31
Click on it and select reload window manager.  if that doesn't work, try shutting down and logging back.  I'm sure you got it loaded correctly if you see the emerald icon.

---

### Post by sdmike on 2007-01-31
I clicked select windows manager to Beryl and the screen flickered but no effects.

---

### Post by ctt1wbw on 2007-01-31
I'd love to be able to give you the right answer, but I just got it going on Sunday, a few days ago.  I'm still trying to figure out all the settings and stuff.

Someone help this guy out!  :)

---

### Post by ctt1wbw on 2007-01-31
Check this out:

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

This is what I followed to get it working.

---

### Post by ctt1wbw on 2007-01-31
Okay, I think I know what your problem is.  Try shutting down and rebooting.  Before you login, select the xgl session.  I just logged out and then logged back into a standard gnome session.  I see the emerald icon as well, but no beryl effects.

---

### Post by ctt1wbw on 2007-01-31
Dammit, now my xgl session isn't working at all, no beryl, no nothing...  :confused:

---

### Post by ctt1wbw on 2007-01-31
Damn you ATI, you stupid *******!!!!  I'm going to have to reinstall because your drivers ****** my system up!!!!!!!!!!!!

---

### Post by sdmike on 2007-01-31
I fixed it! I had to click on the beryl icon and switch it back to load beryl for the gui. I was in xgl everytime but beryl wasn't being enabled.

---

### Post by hotshot23t on 2007-02-01
Hi I was wondering if anyone could help me out.  When I ran the **sudo module-assistant build fglrx** I got an error saying that it could not build the package fglrx-kernel-source-8.32.5-1.  I tried what compwiz 18 said with adding the linux directory and tried it again and no success.  Any help is appreciated.  Thanks!

---

### Post by Uncelilo on 2007-02-02
> **hotshot23t said:**
> Hi I was wondering if anyone could help me out.  When I ran the **sudo module-assistant build fglrx** I got an error saying that it could not build the package fglrx-kernel-source-8.32.5-1.  I tried what compwiz 18 said with adding the linux directory and tried it again and no success.  Any help is appreciated.  Thanks!

I'm also having problems when I try to call build. Below is part of the log that module-assistant is printing.  I'm using a newer kernel, so I'm guessing it may be caused by that. But I'm not sure how to fix it. Any suggestions on how to fix this would be great.

```
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules     &#9618; 
make[1]: Entering directory `/usr/src/linux-headers-2.6.19.2'              &#9646; 
 CC [M]  /usr/src/modules/fglrx/firegl_public.o                           &#9618; 
/usr/src/modules/fglrx/firegl_public.c:89:26: error: linux/config.h: No    &#9618; 
such file or directory                                                     &#9618; 
/usr/src/modules/fglrx/firegl_public.c:456: warning: initialization from   &#9618; 
incompatible pointer type                                                  &#9618; 
/usr/src/modules/fglrx/firegl_public.c: In function ‘firegl_stub_open’:    &#9618; 
/usr/src/modules/fglrx/firegl_public.c:579: warning: assignment discards   &#9618; 
qualifiers from pointer target type 
 /usr/src/modules/fglrx/firegl_public.c: In function                        &#8593; 
‘firegl_put_user_ptr’:                                                     &#9618; 
/usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#9618; 
to integer of different size                                               &#9618; 
/usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#9618; 
to integer of different size                                               &#9618; 
/usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#9618; 
to integer of different size                                               &#9618; 
/usr/src/modules/fglrx/firegl_public.c:1348: warning: cast from pointer    &#9618; 
to integer of different size                                               &#9618; 
/usr/src/modules/fglrx/firegl_public.c: In function ‘__ke_request_irq’:    &#9618; 
/usr/src/modules/fglrx/firegl_public.c:2568: warning: passing argument 2   &#9646; 
of ‘request_irq’ from incompatible pointer type                            &#9618; 
/usr/src/modules/fglrx/firegl_public.c: In function                        &#9618; 
‘__ke_unregister_ioctl32_conversion’:  
 /usr/src/modules/fglrx/firegl_public.c:2591: warning: ‘return’ with a      &#9618; 
value, in function returning void                                          &#9618; 
make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1              &#9618; 
make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      &#9618; 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.19.2'               &#9646; 
make: *** [build] Error 2
```

---

### Post by sdmike on 2007-02-02
Mine stopped working on the third day. lol

---

### Post by hotshot23t on 2007-02-02
Yea I'm using a new kernel as well so maybe thats the problem, but I need it for the wireless.  I hope someone can help us.

---

### Post by dutchman25 on 2007-02-02
I fixed my "MESA" problem by reverting back to the Ubuntu generic kernel.  I could not get the fglrx to build correctly with a 2.6.19.1 kernel.

Now I have to weigh my options: cutomized kernel or 3D desktop?

---

### Post by fuligin on 2007-02-02
Obviously im doing something wrong that everyone else isnt. 
Well I download 
ati-driver-installer-8.32.5-x86.x86_64.run 
to my desktop, 
everything goes well till i get to this section 

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh


I get the following error
bash: ati-driver-installer-8.32.5-x86.x86_64.run: No such file or directory

How would i be able to get this part to work, 

Thank you all

---

### Post by BGreet on 2007-02-02
Make sure you're in the same directory that the file is in when you type that

---

### Post by xxrealmsxx on 2007-02-03
And todays update broke it.
I knew I shouldn't have clicked ok :(

---

### Post by LinuxNewbie_1 on 2007-02-03
> **fuligin said:**
> Obviously im doing something wrong that everyone else isnt. 
Well I download 
ati-driver-installer-8.32.5-x86.x86_64.run 
to my desktop, 
everything goes well till i get to this section 

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh


I get the following error
bash: ati-driver-installer-8.32.5-x86.x86_64.run: No such file or directory

How would i be able to get this part to work, 

Thank you all

New to this myself - took me two days to figure it out!

sudo ln -sf bash /bin/sf
change this to:
sudo ln -sf bash ~/Desktop

first, rename the downloaded file - remove the ".run" portion
now next line:
bash ~/Desktop/ati-driver-installer-8.32.5-x86.x86_64 --buildpkg/Ubuntu/edgy

Final line:
sudo ln -sf dash ~/Desktop

The hopefully, you'll continue on your merry way (I hope).  If not, I'm afraid I'm out of ideas...

Good Luck

---

### Post by Carlton1 on 2007-02-04
Can anyone help?  I am following this code to load the ATI driver, but when I get to

bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy 

I get the reply that there is no such driver

I'm sure that I'm doing something wrong, as I am very new to the command line, but any help would be appreciated.

Thanks,

Carlton

---

### Post by zerofx on 2007-02-04
> **nawzyah said:**
> I tried following this guide but ran into some issues.  I wanted to chime in because I've searched this forum and google for a solution to no avail.

I posted a new thread if you're so inclined to help just follow the link: [http://www.ubuntuforums.org/showthread.php?t=332501](http://www.ubuntuforums.org/showthread.php?t=332501)

Just a gist of what the issue is:  I'm running i386 Ubuntu on a Toshiba A105-S2111 laptop with Xpress 200m, but the Phoenix BIOS lacks any UDA/Sideport configuring functions.  This leads me to black screens after boot instead of the GUI login.
 
I'm in the same boat, there is no settings to set in regards to the UMA/Sideport issue of this particular laptop. Although I have an A105-S2081, which features the very same Xpress 200M chipset.

I follow the howto (and a few other similar howto's) to a T, but in my case everytime I disable the Composite, I get a black screen. And everytime I leave that step out all I get is the missing xlib XFree86-DRI is missing on screen 0 BS.

A default Kubuntu clean install after enabling the Universe and Multiverse repos, followed by an apt-get update.
I've done both the easy way and followed the directions for the bleeding edge/current drivers from ATi's website.

I've done this at least five times now and each time I get so far, it ends up in one of the two.

Hmm... Any thoughts?

---

### Post by Angafirith on 2007-02-05
While I did not use this FAQ, the steps are identical to those I took to get Compiz and Beryl working on my 64-bit Compaq v5210us laptop.

I thought I'd share a little tip that I learned from [this post in a similar thread]("http://ubuntuforums.org/showpost.php?p=2097475&postcount=104"):

If you are using a session to start XGL and want to be able to Shutdown/Reboot from said session, merely add the following lines to your script above where you start the gnome-session:

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"

```

My script looks like this:
```

#!/bin/bash
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
export DISPLAY=:1
DISPLAY=:1 gnome-session

```

---

### Post by peregrine on 2007-02-05
This is broken. I followed it step by step to no avail. I have a compaq presairo r4000 with the 200m and nothing. I follow the steps and reboot and then x crashes. So I reload the old conf up and try again to install the fglrx drivers to no avail. This is on a brand new install, completely updated and everything. I'm really sad that all these people say it works but I cannot share with the happiness.

If there is anything anyone can do to make this work I would be overjoyed to finally have a reason to stay with ubuntu now that someone has made some decent wireless drivers....now only if i could properly use my sideport and 200m.....*dies a little inside everytime he reinstalls fglrx and fails*

Peregrine

---

### Post by ctt1wbw on 2007-02-06
For some reason, only the ati drivers from the ati website work for me and I have the Xpress 200m card.  Follow these directions and see how it goes:

Install from ati.com (latest version of drivers)
Instructions for 6.10 (Edgy)

    *

      Download what's needed:
    *

      Download the appropiate drivers from [WWW] ati.amd.com. You will need the ATI Driver Installer, not the separate XFree86/X.org rpm packages. Save the installer into an empty directory (or at least one containing no *.deb files), since it will create some new files.
    *

      Make sure the universe section of the Ubuntu repositories is enabled (See the AddingRepositoriesHowto), and then run:

sudo aptitude install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-$(uname -r) 

    *

      Disable Composite Extension:

In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. To disable Composite you must edit the /etc/X11/xorg.conf file, so add these lines at the end of xorg.conf:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

    *

      Blacklist old fglrx module from linux-restricted-modules

As ubuntu's linux-restricted-modules package includes the fglrx module from an old driver version (8.28.8), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

sudo gedit /etc/default/linux-restricted-modules-common

We need to add fglrx (only! don't remove anything!) to this:
DISABLED_MODULES="somemodule2 fglrx"

Next,

    *

      Perform the following commands (where <version> is the version number of the installer):

sudo ln -sf bash /bin/sh
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
You may need to wait a few mintues for this to complete.

This will create a number of .deb files in the current directory.

    *

      next,

sudo dpkg -i *.deb

next you build the kernel module - (also note, this has to be done every time you upgrade the kernel)

sudo module-assistant prepare,update
sudo module-assistant build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb

now see Modifying xorg.conf. Skip the "lrm-manager" and "depmod" commands.

After a reboot, confirm that it worked, by issuing the "fglrxinfo" command, as mentioned elsewhere on this page. Look at the troubleshooting sections to confirm if the output of the command is correct.

---

### Post by sdmike on 2007-02-06
Ok it worked with me but now when I log into XGL. The beryl icon comes up and you can still go into beryl but when it boots into XGL it says Beryl-xgl has been closed due to an error.

So what would I need to do to get it working again?

---

### Post by peregrine on 2007-02-06
hey ctt1wbw Im trying to install everything as you say but I get hung up when you type the command 'sudo dpkg -i *.deb' this is the error message I get.
```
 Selecting previously deselected package fglrx-control.
(Reading database ... 102025 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.32.5-1_i386.deb) ...
Preparing to replace fglrx-kernel-source 8.32.5-1 (using fglrx-kernel-source_8.32.5-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Selecting previously deselected package fglrx-sources.
Unpacking fglrx-sources (from fglrx-sources_8.32.5-1_i386.deb) ...
Preparing to replace xorg-driver-fglrx 8.32.5-1 (using xorg-driver-fglrx_8.32.5-1_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: No such file or directory
dpkg: error processing xorg-driver-fglrx_8.32.5-1_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.32.5-1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-control:
 fglrx-control depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing fglrx-control (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-kernel-source (8.32.5-1) ...
Setting up fglrx-sources (8.32.5-1) ...
dpkg: dependency problems prevent configuration of xorg-driver-fglrx-dev:
 xorg-driver-fglrx-dev depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing xorg-driver-fglrx-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xorg-driver-fglrx_8.32.5-1_i386.deb
 fglrx-control
 xorg-driver-fglrx-dev
jason@jason-laptop:~/Desktop$ sudo dpkg -i *.deb
(Reading database ... 102048 files and directories currently installed.)
Preparing to replace fglrx-control 8.32.5-1 (using fglrx-control_8.32.5-1_i386.deb) ...
Unpacking replacement fglrx-control ...
dpkg (subprocess): unable to execute old post-removal script: No such file or directory
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error processing fglrx-control_8.32.5-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace fglrx-kernel-source 8.32.5-1 (using fglrx-kernel-source_8.32.5-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-sources 8.32.5-1 (using fglrx-sources_8.32.5-1_i386.deb) ...
Unpacking replacement fglrx-sources ...
Preparing to replace xorg-driver-fglrx 8.32.5-1 (using xorg-driver-fglrx_8.32.5-1_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: No such file or directory
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: No such file or directory
dpkg: error processing xorg-driver-fglrx_8.32.5-1_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Preparing to replace xorg-driver-fglrx-dev 8.32.5-1 (using xorg-driver-fglrx-dev_8.32.5-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-kernel-source (8.32.5-1) ...
Setting up fglrx-sources (8.32.5-1) ...
dpkg: dependency problems prevent configuration of xorg-driver-fglrx-dev:
 xorg-driver-fglrx-dev depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing xorg-driver-fglrx-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-control_8.32.5-1_i386.deb
 xorg-driver-fglrx_8.32.5-1_i386.deb
 xorg-driver-fglrx-dev

```

Any ideas on whats going on?

---

### Post by ctt1wbw on 2007-02-06
Let's see, did you already install the xorg-driver-fglrx from the Ubuntu repos?  That's what it looks like.  If you did, make sure you follow that part where it says to blacklist old fglrx drivers.

---

### Post by xxrealmsxx on 2007-02-06
> **sdmike said:**
> Ok it worked with me but now when I log into XGL. The beryl icon comes up and you can still go into beryl but when it boots into XGL it says Beryl-xgl has been closed due to an error.

So what would I need to do to get it working again?

Mine did the same.

This how to worked for me and i followed it verbatim. However, after updating to Beryl I got screwed :(.

---

### Post by peregrine on 2007-02-06
Alright well I just reinstalled ubuntu (had some other errors apparently) so now Im going to try it on a fresh install. So I won't need to blacklist fglrx correct?

Also when I blacklist it do I need to put in 'fglrx<version>' or is that fine? And when I edit the xorg.conf in the last line is that just chanining the Driver   'ati' to Driver 'fglrx'?

Peregrine

Update!: Well looks like blacklisting fglrx is a bad idea. Cause now I have to reinstall linux again. This is what happend.

I went through the steps step by step. Followed each instruction. When I get to the blacklist I do as you say. I then do the part with the *.deb i get the same errors. Alright well lets reboot see if it will restrict fglrx. So I reboot and it hangs at mount root partition. Alright okay I'll go in at recovery mode. I did tried to edit the blacklist file to no avail cause sudo only works if your logged in. SO I type login my uname and pass and then alls I get is /dev/something over and over again. Broken. SO if you have any idea...it would help.


Update 2!!: Alright reinstalled again. And followed this tutorial [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually)

Its very similar but has one missing step which was to install build essiantial. thanks for your help nonethe less. :)

---

### Post by sdmike on 2007-02-06
Ok so if Beryl isn't working on my laptop when it was before what should I do?

When I log into XGL I get an error that says beryl-xgl has failed.

---

### Post by zerofx on 2007-02-07
**Edit**: I managed to get it working. There must be something broke because when I update and then configure the driver, it all goes to crap. But this time I did a fresh install, config'ed the driver, and it worked without a hitch. Haven't updated yet, I'm afraid to because I just got it working. At least I know what steps to take.

---

### Post by peregrine on 2007-02-07
Alright so I got the card working how do you know if sideport is working also?

Peregrine

---

### Post by sdmike on 2007-02-07
Is there a way I can get it to work without reinstalling ubuntu because that would be super lame.

---

### Post by andrinho on 2007-02-08
Hi,

I applied this howto and everything works fine. Thank you for the description!

The only problem is that I cannot change display brightness any more. The keys (fn+ f9 and f9) do not work any more after installing the ATI driver.

Any ideas?

Thank s,
andrinho

---

### Post by sdmike on 2007-02-08
All I can say is don't update beryl.

---

### Post by ctt1wbw on 2007-02-09
> **peregrine said:**
> Alright so I got the card working how do you know if sideport is working also?

Peregrine

I read that the newest ATI drivers, 8.33.6, I think, are to the point where you don't need to enable sideport memory.  So if you installed the drivers from ATI, then you are okay.

---

### Post by barbe-et-hache on 2007-02-09
I have a R4000 with an ati express 200m and beryl working.
I'am using the 8.32.5 flgrx driver version because the 8.33 stocked my laptop at logout. 
In order to make XGL work I had to reconfigure xorg with the command 
$ sudo dpkg-reconfigure xserver-xorg
This will help you to get a fresh xorg.conf file. The restart you x server (ctrl+alt+backspace)

To run beryl, I'm using the following script : 
#!/bin/sh
beryl-manager
sleep 1
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

I had the *Checking for non power of two texture support : failed* error before

---

### Post by TFrog on 2007-02-09
For those familiar with the ATI drivers.  It was mentioned in a posting 2 postings back of this one about the 8.33 drivers.  If you look carefully at the AMD/ATI website, this driver is **NOT** compatible with the 200M Radeon Xpress chipset in many laptops by HP/Compaq or any other laptop containing these chipsets.  I too noticed that driver and read further before attempting anything.  **I REPEAT THE 8.33 DRIVER IS NOT FOR THE 200M CHIPSETS!**

Not sure if dEaD mentioned it or not, but you **MUST** recompile your drivers for **EVERY** kernel update.  I just updated to 2.6.17.11 kernel and had to recompile to get glxgears to show me 1700fps again as well as load up the latest ndiswrapper for my wireless to work correctly.

Thanks again dEaD for the excellent HOWTO.  I have it permanently bookmarked for any re/install.  Will be using this for when I do move to Fiesty Fawn.

---

### Post by ctt1wbw on 2007-02-09
> **barbe-et-hache said:**
> I have a R4000 with an ati express 200m and beryl working.
I'am using the 8.32.5 flgrx driver version because the 8.33 stocked my laptop at logout. 
In order to make XGL work I had to reconfigure xorg with the command 
$ sudo dpkg-reconfigure xserver-xorg
This will help you to get a fresh xorg.conf file. The restart you x server (ctrl+alt+backspace)

To run beryl, I'm using the following script : 
#!/bin/sh
beryl-manager
sleep 1
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

I had the *Checking for non power of two texture support : failed* error before

Man, no WONDER I can't logout!  Doh!  Now I am going to have to get the older drivers.  Thanks for the tip!

---

### Post by ctt1wbw on 2007-02-09
Kind of a dumb question, but I need to reinstall the ATI drivers, from the 8.33.6 to the 8.32.5 driver.  Will that overwrite the driver with the new one, or what do I need to do?

---

### Post by ctt1wbw on 2007-02-11
Nevermind.

Okay, I had to revert back to the ATI 8.32.5 drivers because the newest ones won't support my XPress 200m card.

Here's what I got so far:

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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "fglrx"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "ATI Radeon XPress 200m"
HorizSync 28.0 - 72.0
VertRefresh 43.0 - 60.0
Option "DPMS"
EndSection

Section "Device"
Identifier "ATI Radeon XPress 200m"
Driver "fglrx"
Option "UseFBDev" "true"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
BusID "PCI:1:5:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Radeon XPress 200m"
Monitor "ATI Radeon XPress 200m"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900"
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection



UNDER MODULE, I HAD TO ADD LOAD "FGLRX" TO GET IT WORK.

ctt1wbw@WaynesWorld:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

ctt1wbw@WaynesWorld:~$ glxgears -printfps
Xlib: extension "XFree86-DRI" missing on display ":1.0".
9948 frames in 5.0 seconds = 1974.433 FPS
12426 frames in 5.0 seconds = 2479.243 FPS
12451 frames in 5.0 seconds = 2477.821 FPS
12426 frames in 5.0 seconds = 2473.300 FPS
12426 frames in 5.0 seconds = 2479.273 FPS
12443 frames in 5.0 seconds = 2476.971 FPS
12426 frames in 5.0 seconds = 2477.211 FPS
12426 frames in 5.0 seconds = 2477.801 FPS
12443 frames in 5.0 seconds = 2476.035 FPS
X connection to :1.0 broken (explicit kill or server shutdown).
ctt1wbw@WaynesWorld:~$


THAT'S ALMOST A THOUSAND FPS MORE THAN WHAT I HAD WHEN I HAD IT WORKING THE LAST TIME!!!!!

---

### Post by Lonthong on 2007-02-12
Eeehhhhhhhhhhh??????
I have Version 8.33.6 installed for some time without any problem. (No Berryl nor compiz)
My VGA is X1100 which is identical to 200M.

I did have a log-out problem before. However adding one line "AlwaysRestartServer=true" to gdm.conf-custom solved that

---

### Post by ctt1wbw on 2007-02-12
Well, that's good to know.  I didn't know how to do that, otherwise I would have kept the same driver.  Anyhoo, I'm up and running and it seems to be much faster than before.  Who knows.  I'm happy.

---

### Post by compwiz18 on 2007-02-12
> **TFrog said:**
> For those familiar with the ATI drivers.  It was mentioned in a posting 2 postings back of this one about the 8.33 drivers.  If you look carefully at the AMD/ATI website, this driver is **NOT** compatible with the 200M Radeon Xpress chipset in many laptops by HP/Compaq or any other laptop containing these chipsets.  I too noticed that driver and read further before attempting anything.  **I REPEAT THE 8.33 DRIVER IS NOT FOR THE 200M CHIPSETS!**

Not sure if dEaD mentioned it or not, but you **MUST** recompile your drivers for **EVERY** kernel update.  I just updated to 2.6.17.11 kernel and had to recompile to get glxgears to show me 1700fps again as well as load up the latest ndiswrapper for my wireless to work correctly.

Thanks again dEaD for the excellent HOWTO.  I have it permanently bookmarked for any re/install.  Will be using this for when I do move to Fiesty Fawn.
Really?

I have the 8.33.6 drivers working fine - the ATI website even says they are supported: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.33.6.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.33.6.html)

It works fine on my Edgy with kernel 2.6.19.1...

for all who doubt me:
```

01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

```

and 3D with Beryl and such works perfectly...

---

### Post by ctt1wbw on 2007-02-12
I used those drivers and had a logout problem like some others had.  Plus, for some reason, I was only getting about 1600 fps on glxgears.  Now I am using the previous driver and the logout problem is gone and I am getting about 2700 fps.  I don't know if it's related to the driver, something else I did to my xorg file or not.

---

### Post by compwiz18 on 2007-02-12
My friend has an intel card with the intel drivers and has the same logout problem, I think.

---

### Post by TFrog on 2007-02-13
My apologies to all.  I just visited the ATI sight again today.  I'm currently downloading the 8.33.6 drivers as I post this.  I guess at the time I had a case of open mouth insert foot.  In this case it was all the way to the hip.  LOL.  Will be loading the drivers as soon as I get them downloaded.  Hope they improve my fps from the current 1700fps.

---

### Post by TFrog on 2007-02-13
Update on 8.33.6 ATI drivers.  Compaq 4125US model will work with them but fails to shutdown or restart properly.  FPS with glxgears - printfps shows same fps speeds.  ctt1wbw I noticed that during a window resize or movement during glxgears I to got the 2700fps and actually got over 3k fps at one time but not a consistant reading over 1700 fps.  Had to revert back to 8.32.5 drivers for now till someone can come up with a fix for the restart/shutdown issue under KDE 3.5.6.

---

### Post by ctt1wbw on 2007-02-13
> **TFrog said:**
> Update on 8.33.6 ATI drivers.  Compaq 4125US model will work with them but fails to shutdown or restart properly.  FPS with glxgears - printfps shows same fps speeds.  ctt1wbw I noticed that during a window resize or movement during glxgears I to got the 2700fps and actually got over 3k fps at one time but not a consistant reading over 1700 fps.  Had to revert back to 8.32.5 drivers for now till someone can come up with a fix for the restart/shutdown issue under KDE 3.5.6.

Good, I'm glad it worked out for you.  I haven't messed with resizing a window running glxgears yet.  I'll try that out one day.

---

### Post by compwiz18 on 2007-02-13
> **ctt1wbw said:**
> Good, I'm glad it worked out for you.  I haven't messed with resizing a window running glxgears yet.  I'll try that out one day.
I think the 8.32.5 drivers are better because (at least for me) they allow suspend/resuming the computer.

---

### Post by ctt1wbw on 2007-02-13
How often does ATI come out with drivers?

---

### Post by ljoslin on 2007-02-14
I followed the How-to, everything worked perfectly however,
when I run beryl-manager It loads, unfortunately all I get is a white cube, it rotates end everything!  DRI dosn't appear to be loading.

glxinfo

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 1.2 (2.0.6286 (8.33.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon
larry@larry-laptop:~$ 

any help would be great!  Thanks

-=Larry=-

---

### Post by Lonthong on 2007-02-14
I just downgraded from v 8.33.6 to 8.32.05.
Glxgears fps is the same for both version.
V 8.32.05 does not have have any log out issue (I had log out issue with v 8.33.6 which was quite easy to solve).
On both version I suffer suspend/resume problem.......

BenQ P41, Turion X2 with Ati X1100 (identified as X200m)

---

### Post by compwiz18 on 2007-02-14
> **ctt1wbw said:**
> How often does ATI come out with drivers?

About once a month, I think...the new ones are due out soon, it has been a while.

edit: btw, they have a RSS feed if you want instant updates: [http://ati.amd.com/online/rss/atilinuxdriver.rss?OTC-rssfeedlinux](http://ati.amd.com/online/rss/atilinuxdriver.rss?OTC-rssfeedlinux)

---

### Post by andrinho on 2007-02-14
> **TFrog said:**
> 

Not sure if dEaD mentioned it or not, but you **MUST** recompile your drivers for **EVERY** kernel update.  I just updated to 2.6.17.11 kernel and had to recompile to get glxgears to show me 1700fps again as well as load up the latest ndiswrapper for my wireless to work correctly.



Hi,

I updated the Dapper kernel to 2.6.15.28 and have some trouble with the ati driver; causes 100% CPU load. I will probably have to recompile. As I am a total noob: what will I have to recompile and how does this work?
Sorry about this question, but I googled and found no solution.

Thank you very much,
andrinho

---

### Post by Lonthong on 2007-02-14
> **andrinho said:**
> Hi,

I updated the Dapper kernel to 2.6.15.28 and have some trouble with the ati driver; causes 100% CPU load. I will probably have to recompile. As I am a total noob: what will I have to recompile and how does this work?
Sorry about this question, but I googled and found no solution.

Thank you very much,
andrinho

How to recompile:
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx-kernel
sudo module-assistant install fglrx-kernel
sudo depmod -a
sudo shutdown -r now

---

### Post by andrinho on 2007-02-15
Thanks a lot Lonthong: I applied your commands and everything works fine now!:)

---

### Post by angel12 on 2007-02-18
> **ljoslin said:**
> I followed the How-to, everything worked perfectly however,
when I run beryl-manager It loads, unfortunately all I get is a white cube, it rotates end everything!  DRI dosn't appear to be loading.

glxinfo

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 1.2 (2.0.6286 (8.33.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon
larry@larry-laptop:~$ 

any help would be great!  Thanks

-=Larry=-

i am getting the same thing happening here, on an hp dv5035nr. Like said above, i can rotate the cube and everything, and my pointer changes to resize winddows and such, i just cant see anything, all white on the desktop except for top and bottom of cube, which is the beryl logo

---

### Post by Peter Sommer-Larsen on 2007-02-21
Hi ppl

Ive got fglrx running in my xfce4 session.. glxgears runs very smoth..,
but when i start a XGL session, I cant get my fglrx running.. glxgear runs like 2sec
and then it goes lagging...
When I start beryl-manager my screen goes totally white, but I see the mousecourser..!?
wierd.. plz help..

---

### Post by Peter Sommer-Larsen on 2007-02-21
oh and Ive got a "Ati Radeon Xpress 200M" on a "amd64", running Edgy (made a dist-upgrade
this morning..)

---

### Post by ctt1wbw on 2007-02-21
The latest update to beryl and beryl-manager gives EVERYONE the white screen.  Even me.  I'm sure the devs know about it by now.  Been going on for a few days now.

---

### Post by Peter Sommer-Larsen on 2007-02-21
> **ctt1wbw said:**
> The latest update to beryl and beryl-manager gives EVERYONE the white screen.  Even me.  I'm sure the devs know about it by now.  Been going on for a few days now.

oh ok.. thx m8

---

### Post by TFrog on 2007-02-21
I just attempted this in Feisty Fawn Herd 4 just as a thought.  When you get to the step that reads:

sudo module-assistant build fglrx

the build fails for some reason.  Not sure what is the cause.  However, I'm unable to load the 8.32.5 or the 8.33.6 ATI drivers under Feisty Fawn for the 200M card.  Anyone with experience on Feisty Fawn that may have gotten this to work with it please let us know how you got it to work.  Till then I suggest you **NOT** attempt this HowTo in Feisty Fawn.

---

### Post by Peter Sommer-Larsen on 2007-02-21
But I still dont get why my fglrx works in xfce-4 sessions and doesnt work in XGL sessions..
does anybody have an idea why this could be ?

---

### Post by Peter Sommer-Larsen on 2007-02-21
Here is my xorg.conf file.. i forgot..

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
#	Load  "fglrx"
#	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "dk"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Standard Skærm"
	ModeLine     "1280x800@60" 83.9 1280 1312 1624 1656 800 816 824 841
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Standard Video Kort"
	Driver      "vesa"
	BusID       "PCI:1:5:0"

EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option 	    "UseFBDev" "true"
#	Option      "XAANoOffscreenPixmaps"
#	Option        "BlockSignalsOnLock" "on"
#	Option       "KernelModuleParm" "locked-userpages=0"
#	Option       "mtrr" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Standard Video Kort"
	Monitor    "Standard Skærm"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1200x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection


```

---

### Post by compwiz18 on 2007-02-21
> **TFrog said:**
> I just attempted this in Feisty Fawn Herd 4 just as a thought.  When you get to the step that reads:

sudo module-assistant build fglrx

the build fails for some reason.  Not sure what is the cause.  However, I'm unable to load the 8.32.5 or the 8.33.6 ATI drivers under Feisty Fawn for the 200M card.  Anyone with experience on Feisty Fawn that may have gotten this to work with it please let us know how you got it to work.  Till then I suggest you **NOT** attempt this HowTo in Feisty Fawn.

Not sure were I got this so it may be wrong - but I _think_ that 8.33.6 only works in kernel vresions lower then (and not including) 2.6.20, which is what Fiesty uses isn't it?

> **Peter Sommer-Larsen said:**
> But I still dont get why my fglrx works in xfce-4 sessions and doesnt work in XGL sessions..
does anybody have an idea why this could be ?

If XGL runs, then fglrx is working properly.  XGL takes total control over the graphics card, so nothing will run well - it is impossible.  [SIZE="1"](people who know more about this then I do - sorry for the bad explanation of how XGL works)[/SIZE]

---

### Post by Peter Sommer-Larsen on 2007-02-22
But how can fglrx run when i cant run "glxgears" properly I my XGL session?

---

### Post by compwiz18 on 2007-02-22
> **Peter Sommer-Larsen said:**
> But how can fglrx run when i cant run "glxgears" properly I my XGL session?

With diagrams! (even if they don't help, I had fun making them :D)

[ATTACH]25879[/ATTACH]

So without XGL, glxgears, games, what ever you have running connect directly to the fglrx driver.

[http://ubuntuforums.org/attachment.php?attachmentid=25878&d=1172143683](http://ubuntuforums.org/attachment.php?attachmentid=25878&d=1172143683)

But when you add XGL, everything trying to use the fglrx drive gets denied (the red arrows) because XGL is hogging the entire thing.

At least that's how I understand it.

---

### Post by compwiz18 on 2007-02-22
> **Peter Sommer-Larsen said:**
> But how can fglrx run when i cant run "glxgears" properly I my XGL session?

With diagrams! (even if they don't help, I had fun making them :D)

**So without XGL, glxgears, games, what ever you have running connect directly to the fglrx driver.**

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=25879[/IMG][/CENTER]

**But when you add XGL, everything trying to use the fglrx driver gets denied (the red arrows) because XGL is hogging the entire thing.**

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=25880&d=1172143944[/IMG][/CENTER]

At least that's how I understand it.

---

### Post by Dock on 2007-02-22
Hey! I just got everything working and I logged into the Xgl session, but when I enable Beryl-manager and then right-click the icon and select Beryl, my screen goes white and stays white. If you have any advice it would be much appreciated! Thanks!

---

### Post by Peter Sommer-Larsen on 2007-02-22
Wow thx alot m8 !!!!!!!!!! Now I understand! Is there a solution to this problem, or is it because
of ATI as allways ?

Thx again

---

### Post by Peter Sommer-Larsen on 2007-02-22
> **Dock said:**
> Hey! I just got everything working and I logged into the Xgl session, but when I enable Beryl-manager and then right-click the icon and select Beryl, my screen goes white and stays white. If you have any advice it would be much appreciated! Thanks!

All ppl get a white screen.. there is something wrong with the new Beryl-software..

---

### Post by Peter Sommer-Larsen on 2007-02-22
Here is how to fix the white screen:

************************************************ Quote:

Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2
you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0

---

### Post by Dock on 2007-02-22
It worked! Thanks so much for your time and help!

---

### Post by ctt1wbw on 2007-02-22
Well, ATI just released new drivers yesterday, up to 8.34.8 now.  And it specifically mentions the Radeon XPress 200m chip as officially supported.  

Anyone?  Anyone?  Bueller?  :)

---

### Post by TFrog on 2007-02-22
> **compwiz18 said:**
> Not sure were I got this so it may be wrong - but I _think_ that 8.33.6 only works in kernel vresions lower then (and not including) 2.6.20, which is what Fiesty uses isn't it?



If XGL runs, then fglrx is working properly.  XGL takes total control over the graphics card, so nothing will run well - it is impossible.  [SIZE="1"](people who know more about this then I do - sorry for the bad explanation of how XGL works)[/SIZE]

Compwiz18,

Not sure how true that is.  I'll check out the AMD/ATI website about that driver.  I'll also check out the Feisty Forum.  But, yes you are correct about the kernel in Feisty.  To be precise it's 2.6.20-8.  Also, Feisty uses Xorg 7.1 for further information.

---

### Post by compwiz18 on 2007-02-22
> **Peter Sommer-Larsen said:**
> All ppl get a white screen.. there is something wrong with the new Beryl-software..
I didn't get a white screen.  But maybe I'm just weird.

---

### Post by compwiz18 on 2007-02-22
> **ctt1wbw said:**
> Well, ATI just released new drivers yesterday, up to 8.34.8 now.  And it specifically mentions the Radeon XPress 200m chip as officially supported.  

Anyone?  Anyone?  Bueller?  :)
I'm using it right now on 2.6.20.1 with 8.34.8 and Beryl :D  works great.

---

### Post by compwiz18 on 2007-02-22
> **TFrog said:**
> Compwiz18,

Not sure how true that is.  I'll check out the AMD/ATI website about that driver.  I'll also check out the Feisty Forum.  But, yes you are correct about the kernel in Feisty.  To be precise it's 2.6.20-8.  Also, Feisty uses Xorg 7.1 for further information.
That is the way I see it in my head, so it may or may not be correct.  Sorry.

If you are wondering, you can get 8.34.8 running in Fiesty with a patch.

---

### Post by TFrog on 2007-02-23
> **compwiz18 said:**
> That is the way I see it in my head, so it may or may not be correct.  Sorry.

If you are wondering, you can get 8.34.8 running in Fiesty with a patch.

You talk of a patch for Fiesty to allow the running of 8.34.8 ATI drivers.  I'm curious about this patch.  Do you have further information or a URL to such?

---

### Post by compwiz18 on 2007-02-23
> **TFrog said:**
> You talk of a patch for Fiesty to allow the running of 8.34.8 ATI drivers.  I'm curious about this patch.  Do you have further information or a URL to such?
[http://ubuntuforums.org/showthread.php?p=2201311](http://ubuntuforums.org/showthread.php?p=2201311)

The patch works on 2.6.20(.1) so it should work on Fiesty.  Be warned, people have had mixed results.

---

### Post by dario123 on 2007-02-24
error

---

### Post by ztirffritz on 2007-02-25
I tried to install the new drivers and it almost worked.  I'm getting an error message that it failed after less than 10 seconds then it kicks me out of Gnome again.  I can log into Gnome using SafeMode though.  I'm troubleshooting the issue now.

//UPDATE//

 sudo chmod a+r /etc/profile
 
This seemed to fix it all up.

---

### Post by ztirffritz on 2007-02-25
Finally got it to work with the new ATI driver.  Took a bit of hacking and trial & error.  But Beryl is now working on my Compaq Presario V2410US.  I found that restarting the X Server (Ctrl+Alt+BkSpc) was not sufficient.  I had to actually reboot the computer when moving between different sessions.  Otherwise it would take 5-10 minutes to actually load.  Once I finally got XGL to load and tried to start Beryl the screen just went white.  Did a version regression to fix that.  The latest Nvidia drivers included compositing in their drivers so that XGL isn't even needed, in fact, Beryl won't even work in XGL.  You just boot GDM as you normally would.  Maybe that is where the problem with the latest version of Beryl lies.

---

### Post by Peter Sommer-Larsen on 2007-02-26
So we dont need XGL to run Beryl with the new  Ati Radeon Xpress 200M drivers ??
I that what you are saying?

---

### Post by TFrog on 2007-02-27
> **compwiz18 said:**
> [http://ubuntuforums.org/showthread.php?p=2201311](http://ubuntuforums.org/showthread.php?p=2201311)

The patch works on 2.6.20(.1) so it should work on Fiesty.  Be warned, people have had mixed results.

Thanks for the url.  I looked at the patch and decided I'll wait till Herd 5 or the Beta to attempt it again in Fiesty.  I've also had issues with 8.33.6 as well as 8.34.8 drivers putting my system in a perpetual loop on reboot and shutdown with Edgy.  I've reported that to ATI as well as this thread as the means of which I installed the drivers.  Maybe they'll come up with a fix for that issue.

---

### Post by ztirffritz on 2007-02-28
> **Peter Sommer-Larsen said:**
> So we dont need XGL to run Beryl with the new  Ati Radeon Xpress 200M drivers ??
I that what you are saying?

ATI drivers still require XGL for Beryl as far as I know.  Nvidia no longer requires XGL.  The latest version of Beryl actually required that I NOT use XGL on my other computer using an Nvidia card.  I think that this is why the latest version of Beryl is not working with the ATI stuff.

---

### Post by scifi76 on 2007-03-01
The OP's instructions worked great for me, however today there was an update to the linux restricted modules which screwed things up and caused my card to start using the mesa drivers again.

I managed to fix this by repeating the instructions, however does anyone know why the updated restricted modules have this affect and how to solve the problem should there be any future updates?

Also how do you remove a particular update from showing in the update manager? IE if you never want to update that item?

---

### Post by thegnuer on 2007-03-02
Hey It worked for me on
HP nx6125 with AMD64 with Ubuntu 

Thanks a million ,

---

### Post by lavinog on 2007-03-04
> **TFrog said:**
> Thanks for the url.  I looked at the patch and decided I'll wait till Herd 5 or the Beta to attempt it again in Fiesty.  I've also had issues with 8.33.6 as well as 8.34.8 drivers putting my system in a perpetual loop on reboot and shutdown with Edgy.  I've reported that to ATI as well as this thread as the means of which I installed the drivers.  Maybe they'll come up with a fix for that issue.

taken from: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

 **If suspend and hibernate not working**

If after fglrx installation suspend and hibernate stop working. I mean it suspends and hibernates but does not start and just gives black screen. Then put POST_VIDEO to false:

in /etc/default/acpi-support add:
> 
# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

worked for me on edgy

---

### Post by SurR3AL on 2007-03-04
hey is this tutorial only for the ati express 200M or for any ATI card? i have a 9200 SE...will it work??

---

### Post by compwiz18 on 2007-03-04
> **SurR3AL said:**
> hey is this tutorial only for the ati express 200M or for any ATI card? i have a 9200 SE...will it work??
I would suggest you try [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by SurR3AL on 2007-03-04
> **compwiz18 said:**
> I would suggest you try [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

hey thanks :) but i dont have ubuntu yet....only in a week...so will check it out den :D
& i also found [this]("http://odintsoff.wordpress.com/2007/01/27/english-ubuntu-610-ati-radeon-xgl-beryl/") tutorial :)

---

### Post by djevoultion on 2007-03-06
help cannot install module-assistant. 

home@home-laptop:~$ sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package module-assistant is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package module-assistant has no installation candidate
home@home-laptop:~$

EDIT: Nevermind got it installed and fixed the white screen.. beryl seems to run a bit slow . i have a zv6000 with xpress 200m 
when  i right click beryl manager, Beryl settings manager wont load :S but emerald theme will load. please help if you have a fix.

---

### Post by andrinho on 2007-03-07
Hi!

A while ago I installed the proprietary ATI driver and everything works fine except the adjustment of display brightness (fn + f9, f10).

Before I installed the ATI driver it worked perfectly, but now  that the driver is installed I haven't found a way to adjust the brightness. Unfortunately, my forum search wasn't successful.

Anybody an idea on how to adjust the display brightness? 

Thank you!
andrinho

---

### Post by bdogg64 on 2007-03-09
Thanks for the post d-e-a-d .. I got this working on my laptop finally.... beryl and xgl up and running! :popcorn:

---

### Post by ludovit on 2007-03-11
Thanks d_E_a_D,
I got my Beryl running on first try. Awesome post. I love the Beryl.:) 

My hardware/software:

Gateway MX-6431 laptop, AMD Turion 64, 512MB RAM, ATI Radeon Xpress 200M 64MB video (shared, up to 256MB), Ubuntu Edgy 6.10_x64, fglrx 8.34.8_x64.

thanks again
ludovit

---

### Post by sdmike on 2007-03-12
I loaded everything but all I get is a white screen. but I know beryl is running because I can flip the cube and the beryl diamond pic is ontop of the cube?

So what went wrong?

---

### Post by robin.w on 2007-03-12
:KS :KS :KS Thanks a lot and congratulation d_E_a_D!!!:KS :KS :KS 

You rock, you're king! Finally I can enjoy beryl as well!!!

  All good

         Robin

---

### Post by forcesofhabit on 2007-03-13
> **sdmike said:**
> I loaded everything but all I get is a white screen. but I know beryl is running because I can flip the cube and the beryl diamond pic is ontop of the cube?

So what went wrong?

I have the same issue here. If anyone could help out that'd be great!

---

### Post by rieske on 2007-03-13
> **sdmike said:**
> I loaded everything but all I get is a white screen. but I know beryl is running because I can flip the cube and the beryl diamond pic is ontop of the cube?

So what went wrong?

[http://forum.beryl-project.org/viewtopic.php?f=36&t=3756](http://forum.beryl-project.org/viewtopic.php?f=36&t=3756)

this solved the problem for me.

---

### Post by joey5761 on 2007-03-13
Hi all,

could please advise me where can i get a driver for this chipset ATI Radeon Xpress 200M. I bought a notebook model MT3104B (UK Version) from Gateway last 2 weeks. Come with Vista basic. I need to do my work with windows XP. I format my notebook and start freshly install a new windows XP Professional. The problem is that, i downloaded a driver from amd for XP and still not detect my ATI Radeon Xpress 200M. Please help...
Thanks

---

### Post by Palmstroem on 2007-03-13
Hi all,

I followed the famous unofficial Wiki guide [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) and also tried tseliots Envy script to install the latest ATI drivers. Installation was no problem but the system randomly froze. This problem was rare with the older drivers and became intolerable with the latest 8.34.8 version. Therefore I downgraded to 8.28.8 and it works OK - although speed is a bit reduced. Still it is much better than the mesa driver.

My hardware: 2x AMD Opteron 270 processors, 4 GB RAM, Radeon X1300 card.

Conclusion (for me!): do **not** use the latest drivers! :(

---

### Post by ztirffritz on 2007-03-15
Beryl 0.2 was released earlier.  Anyone try it yet?  Does it fix the "white screen" problem?

---

### Post by ztirffritz on 2007-03-17
I took the plunge and installed the Beryl Updates.  All seems to be working, but there are some issues with logging out and shutting down.  Unless I issue the "shutdown -h now" command from the terminal the system hangs during shutdown.  Logging out is also an issue.  It locks up with a black screen when I try to logout.

---

### Post by totalnub on 2007-03-19
WOW, Just got my graphics card working thanks to your guide. Very easy to do. :) THANK YOU VERY MUCH!!

My system:
Pavillion zv6000
Amd Athlon 64 3200+
2GB Ram
Ati Radeon Xpress Mobility 200m
Ubuntu 6.10 64-bit
Broadcom 4306 wireless card (this is the only thing i have left to fix.... >.< any pointers?)

---

### Post by Peter Sommer-Larsen on 2007-03-22
Does the latest Beryl fix the white screen problem ? Has anybody tried ?
Damn i dont get why it has to be so hard getting beryl to work.. its so nice a program..!?!?!?!?!

Or well.. beryl is working.. but without 3D accel. DAMN ATI !!!

---

### Post by highway_superstar on 2007-03-28
Gateway MT6456
AMD 64 Turion X2
ATI Radeon Xpress 200M

Ran the setup word for word. . .

WORKING!!!!

Fresh Edgy_64 install, all updates. . . 


let's see how long this will last. . .

---

### Post by Lonthong on 2007-03-28
> **ztirffritz said:**
> I took the plunge and installed the Beryl Updates.  All seems to be working, but there are some issues with logging out and shutting down.  Unless I issue the "shutdown -h now" command from the terminal the system hangs during shutdown.  Logging out is also an issue.  It locks up with a black screen when I try to logout.

I also had log out issue with Ati driver v 8.33.6 & V 8.34.8.
This solved my problem:
 add"AlwaysRestartServer=true" under "Daemon" to yr gdm.conf-custom

---

### Post by peregrine on 2007-04-04
Hey I was wondering if anyone got the new 8.35.5 drivers up and running. I'm just about to install them myself. And wanted to know if anyone had troubles or anything?

Thanks.

---

### Post by acmarfil31 on 2007-04-07
Thank you d-e-a-d for posting this.  I have been trying to run beryl on my nx6125 laptop, gladly i found this post.

Just plainly works, even though my Ubuntu-Edgy 32-bit is not newly installed.

Keep it up man.

---

### Post by ethidda on 2007-04-08
Thank you so much. It's my second day on linux and it worked like a charm for me (even though I had no idea what I was doing)

@ peregrine, I used the latest (35) version of the driver. It works.

---

### Post by ethidda on 2007-04-08
This is probably really stupid, but my whole system crashes when I do ```
mplayer <some file> -vo gl
``` The other vo options don't work as well on my gnome setup, so I set gl as the default. Does anybody have any ideas about this?

---

### Post by tallok on 2007-04-10
This thread/walkthrough was awesome.  Beryl works great on my Toshiba Satellite M115 S1061 with an ATI eXpress 200m.  I thought I was screwed until I found this.

---

### Post by jet2230 on 2007-04-11
thank you very much.

i have a [samsung r20]("http://www.comet.co.uk/cometbrowse/multipleImage.do?sku=384097&zoom=yes") with integrated ati 1250[http://ati.amd.com/products/radeonxpress1250dsk/index.html]("http://ati.amd.com/products/radeonxpress1250dsk/index.html").

i was not really expecting this to work but i was wrong. glxgears now works flawlessly.

all i did was copy and paste ur code. 

thanks again.

---

### Post by inspiteofmyself on 2007-04-14
this is one awesome howto...excellent work. ive tried numerous ones of these on 3 seperate installs onto this laptop in the past 2 days (since i decided id try ubuntu after using debian forever...)

this was the first that did a thing for me in terms of actually working as written.

not only is 2d and 3d acceleration enabled and fully working, but i got the eyecandy as a bonus...and to top of all off, you kept me from having to use ndiswrapper to get the broadcom adapter to function...

-- a happy hp zv6000 user :D

---

### Post by inspiteofmyself on 2007-04-15
and then i killed it...

not sure what has happened here, all i did was install some ubuntu accessories, and games that were available on the Add/Remove Programs tool...did not make any changes to anything...

when i restart my Xgl session now, i get the gnome splash screen, the top gnome panel, and the bottom gnome panel. the desktop keeps the gray checkered X look, the cursor loads properly, and the panels remain completely blank.

there is a rare occasion that the bottom panel will have the hide/show desktop icon, but thats all ive seen so far. if i start a regular gnome session from gdm, everything seems to load and work just fine.

ive tried deleting all of the beryl and metacity rc files from my home directory to no avail.

i also enabled root logins in gdm and tried xgl as root and received the same result.

anyone else ever have this happen that has a solution? ive searched this forum for the last hour, and seen similiar posts, but no real solutions...just people saying "nevermind, got it fixed" without ever saying how...i doubt they know how they did it. hehe...

---

### Post by dustman on 2007-04-16
why does beryl crash after a few minutes of working flawlessly? :| The system simply logout's and I get the login screen again, and again, and again ... :(

---

### Post by inspiteofmyself on 2007-04-17
> **dustman said:**
> why does beryl crash after a few minutes of working flawlessly? :| The system simply logout's and I get the login screen again, and again, and again ... :(

i have not gotten anything quite like that, i do have beryl crash at some random times, and have found it best that if it does indeed crash, that you just let it stay disabled until you can get a good reboot in.

now, ive seen several people talking about how gnome stopped working for them...it loads panels partially, and then freezes solid. i had that problem (last 2 posts by me in this thread), and hopefully people will be able to find this thread before they decide to give up on it all completely ;)

anyway, i deleted all of my configuration, and all of the xorg and gnome related files from my home directory...that did me no good whatsoever (and i did not think that it would, because i had already restored my home directory from a backup). actually, it did do me some good, because it reset my network icons in my panel so now i get a wireless indicator where i had none before. lol...

what did seem to work though, was removing the X and gnome related files from /tmp...

---

### Post by jennt on 2007-04-17
hi, thanks for the guide!

but i have one problem, beryl only works occasionally.
there are times when i go into xgl session, it would either just freeze or my (top or bottom) taskbar would be missing, i would then have to cold restart my laptop ( i have a toshiba satellite with graphics driver ati xpress 200m)

i've done that a couple of times now, it kind of seems like beryl picks when it wants to show up lol.. can someone please explain to me why's that?

thanks in advance :)

---

### Post by El Viejo Lobo on 2007-04-20
It was nice with Edgy, I just finished to upgrade my Laptop to Feisty Fawn. I installed the Accelerating Graphic Driver from "Administration/restricted drivers manager"
I cannot use Google Earth (it freezes) or Tuxkart (too slaw).
How can I reinstall the same drivers that I had installed from this place, but this time on Feisy fawn:(

---

### Post by Fluxid on 2007-04-21
H!
I've just installed Feisty and tried with fglrx drivers
On Edgy everything was fine: i've had direct rendering both on AIGLX and XGL.
Today i decided to try newest available fglrx from ATI website.
the only differences in install was that there was no fglrx-control package build, and aticonig crashes at run.
But i've compied some parts of xorg.conf from my old edgy confiuration, and.. it works! ... mostly.

on AIGLX i have direct rendering:

```
display: :0  screen: 0
direct rendering: Yes
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6458 (8.36.5)
```

but on XGL:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.2 (2.0.6458 (8.36.5))
```

These are parts of my xorg.conf:

```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

...

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DRI" "on"
	Option	    "RenderAccell" "on"
	Option	    "FSAAEnable" "off"
	Option	    "FSAAScale" "0"
	Option	    "Centermode" "on"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#	Option	    	"AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option  "Composite" "0"
EndSection
```

It looks like this "AIGLX" option is not required, propably it's on by default.

Now, my startxgl.sh script look like this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
sleep 2
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

I think i'll try with my old drivers, which worked perfectly on edgy... but how do i remove actual drivers? Can i just "overwrite" them?

[EDIT]
OOPS! Sorry, i didn't know there's thread about 200M and feisty... how do i remove posts? :/
[EDIT2]
:/ This another thread is closed...

---

### Post by czmiel on 2007-04-30
Dear ATI,

NEVER NEVER NEVER AGAIN!!!

Regards,

former fan and consumer

---

When it comes to open-source ATI Xpress 200M drivers, hopefully something is happening...
[http://gitweb.freedesktop.org/?p=mesa/drm.git;a=commitdiff;h=a70f8e0ab265cc4a26ed2f9e92ab0618bd920a93;hp=b25558bb7377f6df6d457b50067a1d245f7911fd](http://gitweb.freedesktop.org/?p=mesa/drm.git;a=commitdiff;h=a70f8e0ab265cc4a26ed2f9e92ab0618bd920a93;hp=b25558bb7377f6df6d457b50067a1d245f7911fd)

---

### Post by jbernardo on 2007-05-01
> **jennt said:**
> 
but i have one problem, beryl only works occasionally.
there are times when i go into xgl session, it would either just freeze or my (top or bottom) taskbar would be missing, i would then have to cold restart my laptop ( i have a toshiba satellite with graphics driver ati xpress 200m)


I have the same problem on a ecs331 based laptop (advent 7083). Xgl freezes it hard, even alt-sysreq won't work. I gave upon Xgl for now - and since the chipset is a xpress 200m I can't use the open source radeon driver and AIGLX. The xpress 200m chipset seems to be a piece of cr** right now, I even get lots of "APIC" errors in syslog.

---

### Post by hino on 2007-05-01
I tried to see if this would work for the Radeon x1650 i got all the way to ```
sudo module-assistant build fglrx
``` which failed. *sigh* any clue why it would fail at that part?

---

### Post by jbernardo on 2007-05-02
I just gave up and since I had the opportunity to return the laptop (due to a lot of other problems, including a probably defective wifi card), I did it. My next laptop won't be a 200m chipset one, for sure!

---

### Post by enzobelmont on 2007-05-02
> **jbernardo said:**
> I just gave up and since I had the opportunity to return the laptop (due to a lot of other problems, including a probably defective wifi card), I did it. My next laptop won't be a 200m chipset one, for sure!

i envy you.... jezzzz

please linux users follow my wise advice:


STAY AWAY FROM ATI

---

### Post by siralphred on 2007-05-29
worked !

---

### Post by floke on 2007-05-29
Was messing around with some LiveCD's the other day and discovered that the latest Mandriva can run Beryl and Metisse (but why would you want to?) on the ATI200M from the LiveCD - out of the box, with no extra configuring - just select 3d from the sessions menu and away you go.

I was absolutely flabbergasted! Worth trying just to see that it can actually work on the ATI200M.

Go give it a bash and enjoy; and then wonder why it doesn't work on any other distro!

---

### Post by ogmious on 2007-05-31
Just was reading some of this thread...

In regard to APIC errors with turion64 boards ecs331 etc...

just pass ACPI_SKIP_TIMER_OVERRIDE in kernel boot parameters and no more APIC errors

also fixes clock going fast after resume from suspend,,

---

### Post by strm on 2007-06-04
After following the instructions precisely, this is what my XGL session looks like, I am not sure what is wrong, though I do suspect my ATI drivers, is there any way to check if these were installed properly and if the card is in fact working properly?

---

### Post by housegecko on 2007-06-13
I wanted to thank D-E-A-D for his GREAT tutorial.  I had worked for days to get my dual-core ATI Mobility X14 to display Beryl correctly.  You have made me a very happy camper and again Thanks for sharing.
Regards......The Gecko

---

### Post by redson2 on 2007-06-19
I tried to do sudo aticonfig --initial and I got this

```
$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfa12a51 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d4ef5b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7cf9ebc]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 03:01 3393978    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 03:01 3393978    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7cc0000-b7ccb000 r-xp 00000000 03:01 2523200    /lib/libgcc_s.so.1
b7ccb000-b7ccc000 rw-p 0000a000 03:01 2523200    /lib/libgcc_s.so.1
b7cd6000-b7cd7000 rw-p b7cd6000 00:00 0 
b7cd7000-b7cd9000 r-xp 00000000 03:01 2557192    /lib/tls/i686/cmov/libdl-2.5.so
b7cd9000-b7cdb000 rw-p 00001000 03:01 2557192    /lib/tls/i686/cmov/libdl-2.5.so
b7cdb000-b7cdc000 rw-p b7cdb000 00:00 0 
b7cdc000-b7ce0000 r-xp 00000000 03:01 3392773    /usr/lib/libXdmcp.so.6.0.0
b7ce0000-b7ce1000 rw-p 00003000 03:01 3392773    /usr/lib/libXdmcp.so.6.0.0
b7ce1000-b7ce3000 r-xp 00000000 03:01 3392762    /usr/lib/libXau.so.6.0.0
b7ce3000-b7ce4000 rw-p 00001000 03:01 3392762    /usr/lib/libXau.so.6.0.0
b7ce4000-b7e1f000 r-xp 00000000 03:01 2557186    /lib/tls/i686/cmov/libc-2.5.so
b7e1f000-b7e20000 r--p 0013b000 03:01 2557186    /lib/tls/i686/cmov/libc-2.5.so
b7e20000-b7e22000 rw-p 0013c000 03:01 2557186    /lib/tls/i686/cmov/libc-2.5.so
b7e22000-b7e25000 rw-p b7e22000 00:00 0 
b7e25000-b7e4a000 r-xp 00000000 03:01 2557194    /lib/tls/i686/cmov/libm-2.5.so
b7e4a000-b7e4c000 rw-p 00024000 03:01 2557194    /lib/tls/i686/cmov/libm-2.5.so
b7e4c000-b7f39000 r-xp 00000000 03:01 3392756    /usr/lib/libX11.so.6.2.0
b7f39000-b7f3d000 rw-p 000ed000 03:01 3392756    /usr/lib/libX11.so.6.2.0
b7f3d000-b7f4a000 r-xp 00000000 03:01 3392777    /usr/lib/libXext.so.6.4.0
b7f4a000-b7f4b000 rw-p 0000d000 03:01 3392777    /usr/lib/libXext.so.6.4.0
b7f4b000-b7f4c000 rw-p b7f4b000 00:00 0 
b7f4c000-b7f53000 r-xp 00000000 03:01 3392799    /usr/lib/libXrender.so.1.3.0
b7f53000-b7f54000 rw-p 00006000 03:01 3392799    /usr/lib/libXrender.so.1.3.0
b7f54000-b7f59000 r-xp 00000000 03:01 3392797    /usr/lib/libXrandr.so.2.1.0
b7f59000-b7f5a000 rw-p 00005000 03:01 3392797    /usr/lib/libXrandr.so.2.1.0
b7f63000-b7f66000 rw-p b7f63000 00:00 0 
b7f66000-b7f7f000 r-xp 00000000 03:01 2523157    /lib/ld-2.5.so
b7f7f000-b7f81000 rw-p 00019000 03:01 2523157    /lib/ld-2.5.so
bf9fe000-bfa14000 rw-p bf9fe000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

What happened?

---

### Post by wrgross on 2007-06-22
I'm having the same seg fault.

I was able to compile this yesterday, even using the latest driver from the ATI site.

I just reinstalled Ubuntu from scratch as I spent a lot of time hacking my install yesterday, so who knows where the bad juju is coming from.

<pray />
Bill

---

### Post by vcinfio on 2007-10-14
Hey guys im new to linux, i am getting stuck after a couple steps. in the very first post under the instructions, it says go to the folder where you download the installer, i downloaded it on my desktop... how i do do that in the terminal???

---

### Post by sevenearths on 2008-02-14
> **d-E-a-D said:**
> Ok, finally it's working! let's show how!
Running on HP Pavilion Dv5176.

[SIZE=4]Right now i'm out off time, but when i have some, i'll try to install ATI drivers from ATI site into version V 7.04
Right now just activate all options in the repositories,  do a update in System -> Administration -> Update Manager,  go to System -> Administration ->Restricted Drivers Manager and activate ATI driver.
NOTE: DESKTOP EFFECTS DOES NOT WORK !!!!! ATI DOES NOT SUPPORT COMPOSITE EXTENSION!![/SIZE] 

You say that ATI doesn't support composite mode. Isn't that the whole point of installing beryl, or is that the point of downloading the drivers from the ATI web site and doing the install that way?

Plus your post says:

[QUOTE=d-E-a-D;1906817]```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

```[QUOTE]

does gnome-session need to be replaced with kde-session if your using Kubuntu?

Sorry for all the questions

:confused:

---

### Post by compwiz18 on 2008-02-15
sevenearths:

These instructions are kind of old (Last edited by d-E-a-D : April 21st, 2007 at 10:41 PM)  ATI has since released drivers supporting the composite extension.

If you want to use these drivers, I'd suggest using this howto: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Details on using Beryl (now compiz-fusion) are provided on that page also: [Desktop Effects]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects")

---

### Post by sevenearths on 2008-02-15
hey compwiz18

thanks for the post but it didn't work because I'm a nOOb.

I've spent a day and a half on this and still have no movement.

I tried the links but they on really helped with the ati install and didn't tell me anything about beryl. I am currently following this page:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

but have got stuck at the bottom. :( Direct rendering reads 'no'

anyway rebooted with ati driver enabled in 'restricted drivers manager' and got 'yes', so followed part of the following thread:

[http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon](http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon)

and I got bouncy windows. HURRAY!!!

and it took me 5hrs to find the animations tab. HUMMMMM!

---

### Post by C.T.Anwar on 2008-02-25
hi i have recently installed ubuntu in my compaq presario V5000 and was trying to install my ATI radeon xpress 200M card with you instruction . it was going fine till ti reached the

sudo module-assistant build fglrx

command , in the blue screen it says that failed to build ... and after that everything stops .
any ideas? 
thanks

---

### Post by compwiz18 on 2008-02-25
Again, these instructions are kind of old (Last edited by d-E-a-D : April 21st, 2007 at 10:41 PM)

If you want to use these drivers, I'd suggest using this guide (it is far more recent, especially if you are using the latest version of Ubuntu): [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by sevenearths on 2008-02-27
Sorry C.T.Anwar, I've just seen your post and its two days old

I feel for you, I went through the same process

check out 'michael37' post at

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=569654&highlight=600m+gutsy]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=569654&highlight=600m+gutsy")

(his is post no.7)

it should sort you out :)

+ the method above is solid as well

---

