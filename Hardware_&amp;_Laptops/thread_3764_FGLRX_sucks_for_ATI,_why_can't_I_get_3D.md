---
title: "FGLRX sucks for ATI, why can't I get 3D?"
date: 2004-11-09
forum: Hardware &amp; Laptops
---

### Post by Slovak on 2004-11-09
I have followed and refollowed how-to's, wiki's, faq's etc and for the life of me cannot get 3D to work. When I follow Ubuntu's original guide, all goes well until I touch fglrxconfig. Then once I either restart X the traditional way, or reboot the machine all I get is a black screen upon reboot with the only way to recover being a hard reboot into recovery mode to restore my original XF86Config-4 file that I have backed up to my home directory. Now if I use mattyh's how-to in the how-to section, I get as far as his step #2 and the adding...Option "UseInternalAGPGART" "no" to this section of my XF86Config-4 file...
Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
Driver "fglrx"
BusID "PCI:2:0:0"
Option "UseInternalAGPGART" "no"
EndSection
As soon as that is added and I reboot same results, the dreaded black screen. I have tried tried saying "yes" instead of "no" for the AGPGart and I get the same exact results. The only way I can reboot normally is not adding Option "UseInternalAGPGART" "no"
It does not matter whether my driver says "ATI" or "fglrx" it still reboots as long as the AGPGart line is not added.
Although I have not looked at all logs as of yet, I know for a fact that AGPGart is a kernel related option, because one can compile it into the kernel or as a module for the kernel IF everything else in the kernel is configured correctly, like mtrr for the chipset, the chipset itself, etc., etc. Now most everyone in various forums around the web agree that AGPGart and ATI always get along better if it is compiled into the kernel instead of as a kernel module. I don't know what the case is with the Ubuntu kernel, I am just saying what I know and have read elsewhere. Either way I think something is up with the kernel not allowing me to have 3D working properly because AGPGart is a kernel option/problem.
My specs are as follows...
ASUS TUSL2-C mobo with Intel 815 chipset
ATI Radeon 9800XT (retail from ATI)
One other thing I know for sure, Intel 815 support is an experimental option in the 2.6.9 kernel, so maybe, just maybe that has something to do with me and no 3D.
Any ideas before I nuke Ubuntu for good and stick with Slackware 10 since 2D is 2D no matter which distro one uses?

---

### Post by Slovak on 2004-11-09
Should I install the 686 kernel for my system, my processor is a 1.4Gig Tualatin with 512 cache, more or less designed to be used as a server processor. I am currently using the 386 kernel.
If so, what is the command to upgrade to the 686 kernel, and do I need to do anything after it config wise?

---

### Post by mattyh on 2004-11-09
Ok, I've been searching the net to see if I can find a solution for you.  When you boot up to this black screen, I need you to see if Ctrl+Alt+F2 or any other Ctrl+Alt+F*x *(x being a number) will work.  If so, there is hope.  If you could check that out I'll see what else I can find.  Thanks.

---

### Post by wallijonn on 2004-11-09
This is what I have installed from SPM (package name)

linux-image-2.6.8.1-3-686
linux-restricted-modules-2.6-686
linux-headers-2.6.8.1-3-686

Since I have over 1G of mem, installing the 686 kernel got rid of the 'use high mem kernel' boot error message.

---

### Post by Slovak on 2004-11-09
[QUOTE=mattyh]Ok, I've been searching the net to see if I can find a solution for you.  When you boot up to this black screen, I need you to see if Ctrl+Alt+F2 or any other Ctrl+Alt+F*x *(x being a number) will work.  If so, there is hope.  If you could check that out I'll see what else I can find.  Thanks.[/QUOTE]

No go with either kernel image, 386 or 686

---

### Post by Slovak on 2004-11-09
[QUOTE=wallijonn]This is what I have installed from SPM (package name)

linux-image-2.6.8.1-3-686
linux-restricted-modules-2.6-686
linux-headers-2.6.8.1-3-686

Since I have over 1G of mem, installing the 686 kernel got rid of the 'use high mem kernel' boot error message.[/QUOTE]

Me too, as of now, but it still didn't help at all. I don't even get to run fglrxconfig, just adding the agpgart as either yes or no is all it takes to reboot into a black screen. I have tried with both kernels, I even changed my agp in the bios from 4x to 2x, and played with the agp app size changing it from 32Mb to 64Mb and none of the above helps, WTF?  :-x

---

### Post by Slovak on 2004-11-09
This is driving me nuts, as well as others who cannot figure out why either.

---

### Post by HiddenWolf on 2004-11-09
One of the few moments that I am very happy I bought a cheap-ass 9200. It's supported perfectly well by the ATI drivers. 

Disgrace tho that they are so sucky.

---

### Post by wallijonn on 2004-11-09
[QUOTE=Slovak]This is driving me nuts, as well as others who cannot figure out why either.[/QUOTE]

Looking at your XF86Config-4 file I can see that your video card is not being recognised as an R350.

Are you enabling TV-out when you run the config file? Don't. 

If you run [COLOR=RED]/usr/X11R6/bin/xf86cfg[/COLOR] (save a copy of the XF86Config-4 for me) and then run [COLOR=RED]fglrxconfig[/COLOR] does it do the same? 

I also notice that it is trying to load cryllic and CID fonts. Did you run fglrxconfig with a clean install? (I'm assuming that you have, but the copy of your last XF86Config-4 file may not have been generated on a clean install).

---

### Post by wallijonn on 2004-11-10
[QUOTE=Slovak]Intel 815 support is an experimental option in the 2.6.9 kernel, so maybe, just maybe that has something to do with me and no 3D.

Any ideas before I nuke Ubuntu for good and stick with Slackware 10 since 2D is 2D no matter which distro one uses?[/QUOTE]

Are you saying that Ubuntu doesn't work in 2D?

If you want to try the 2.6.9 kernel, I believe Hoardy is 2.6.9. You'd have to change Warty -> Hoardy in your repositories, then install the 2.6.9 kernel, then switch back to the Warty repositories.

Just a thought.

---

### Post by HungSquirrel on 2004-11-10
I have a similar problem.  The cause is the DRI module.  If I comment it out of my XF86Config-4, I can load X fine.  If I leave it commented, I can't get X to load.  This is very odd because I used to be able to run X fine with DRI before.

---

### Post by Slovak on 2004-11-10
[QUOTE=wallijonn]Are you saying that Ubuntu doesn't work in 2D?

[/QUOTE]

No, I am saying that if all I am able to get is 2D then I might as well go back to a distro that I am more comfortable with, and uses KDE, like Slackware 10. I say this because 2D is 2D no matter the distro. I always wanted to try debian, and Ubuntu came along. Plus it was supposedly easy to set up 3D in Ubuntu.  :lol:

---

### Post by Slovak on 2004-11-10
[QUOTE=wallijonn]Looking at your XF86Config-4 file I can see that your video card is not being recognised as an R350.

Are you enabling TV-out when you run the config file? Don't. 

If you run [COLOR=RED]/usr/X11R6/bin/xf86cfg[/COLOR] (save a copy of the XF86Config-4 for me) and then run [COLOR=RED]fglrxconfig[/COLOR] does it do the same? 

I also notice that it is trying to load cryllic and CID fonts. Did you run fglrxconfig with a clean install? (I'm assuming that you have, but the copy of your last XF86Config-4 file may not have been generated on a clean install).[/QUOTE]

No I am not enabling TV out. The attached is a copy of my original XF86Config-4 renamed to a txt file that I saved to my home directory directly after a clean install of Ubuntu, before any messing around.
I will run xf86cfg when I get home tonight.

---

### Post by allen on 2004-11-10
[QUOTE=Slovak]No I am not enabling TV out. The attached is a copy of my original XF86Config-4 renamed to a txt file that I saved to my home directory directly after a clean install of Ubuntu, before any messing around.
I will run xf86cfg when I get home tonight.[/QUOTE]

if when you restart it black screens again try the attached file (save it to your home dir beforehand just in case). i've changed ati to fglrx and inserted the InternalAGP line. AND removed the dri load module. dri is only supported in ati radeons <=9200 ?
make the changes yourself if you want. its basically commenting out DRI in the load section.

as HungSquirrel said its likely due to the dri module. 

if your using DRI then don't bother of course.

---

### Post by Slovak on 2004-11-10
I will try right now, be back soon/

---

### Post by Slovak on 2004-11-10
[QUOTE=allen]
make the changes yourself if you want. its basically commenting out DRI in the load section.

as HungSquirrel said its likely due to the dri module. 

[/QUOTE]

Well at least it works so far, the damn DRI hosed me up, I have not run fglrxconfig yet, but when I run fglrxinfo it still says MESA 
 :-s

---

### Post by allen on 2004-11-10
[QUOTE=Slovak]Well at least it works so far, the damn DRI hosed me up, I have not run fglrxconfig yet, but when I run fglrxinfo it still says MESA 
 :-s[/QUOTE]
 i assume you've loaded fglrx ?

```
echo fglrx | sudo tee -a /etc/modules
```

other than that i can't get why 3D acceleration still isn't working.

---

### Post by Slovak on 2004-11-10
Yes it is loaded, I am baffled

---

### Post by Slovak on 2004-11-10
Well the problem is definately DRI. 
mattyh, I was able to boot to the desktop once I commented out the dri section, ran fglrxinfo and still says mesa. I then ran fglrxconfig, answered everything as told in how-to's, rebooted to a black screen  :shock:  I then rebooted again into rescue mode, and ran sudo pico /etc/X11/XF86Config-4 and discovered that once again dri magically appeared, so I commented it out again, now I can reboot into desktop, but no 3D at all, still says mesa, and this....
slovak@john:~ $ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
 and when I run this....
slovak@john:~ $ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  1 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  1 24  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  1 24  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

Notice how both say exactly the same thing...DRI is missing. Now what, sounds like no DRI=no 3D.

---

### Post by ashley_v on 2004-11-10
[QUOTE=][/QUOTE]
 Hey I bought an ati card once.  As soon as I popped that baby in it stopped working.  I booted once and bam tv-out worked with no installation of drivers and I was pleased.  Then after next boot it just stopped working.  Ati and Linux, it requires lots of work.

I took the card back and bought an Nvidia, and thanks to Nvidia's outstanding support for the Linux community I have had no problems since.

Hope you get yours working.

---

### Post by wallijonn on 2004-11-10
different chip detections:

[http://dri.sourceforge.net/cgi-bin/moin.cgi/ATIRadeon#head-7b41b7438a39536bc8928468711d04ca56deadac](http://dri.sourceforge.net/cgi-bin/moin.cgi/ATIRadeon#head-7b41b7438a39536bc8928468711d04ca56deadac)

You'll have to ask the Ubuntu devlopers on their thoughts on this:

[http://dri.sourceforge.net/cgi-bin/moin.cgi/Download#head-23e78008e2cfec027df1a2b91af770a551b24b13](http://dri.sourceforge.net/cgi-bin/moin.cgi/Download#head-23e78008e2cfec027df1a2b91af770a551b24b13)

[http://www.nixnuts.net/files/README.txt](http://www.nixnuts.net/files/README.txt)

[http://www.nixnuts.net/files/binary/](http://www.nixnuts.net/files/binary/)


.

---

### Post by Slovak on 2004-11-10
What the hell is all that supposed to mean?

---

### Post by Slovak on 2004-11-10
I tried it anyway, apt-get says it couldn't locate the package, and I added them to my sources.list

---

### Post by HungSquirrel on 2004-11-11
So what do I do to get DRI to work?  I had 3D acceleration working when I first installed the fglrx package, but after I rebooted my machine I couldn't.

I miss my 3d.  :(

---

### Post by HiddenWolf on 2004-11-11
ATI has really left the community out in the cold.

I informed them a few days ago, that my next purchase will be a nvidia solution.
Hoping that if enough people would do that, ATI would wake up and do something. :-S

---

### Post by HungSquirrel on 2004-11-11
You got that right.  I had no problems with my secondhand Geforce3 Ti200.  Last year I spent $300usd on this Radeon 9800 and I can't get it to work for crap in Linux.

---

### Post by Slovak on 2004-11-11
Me either, ATI sucks. Today at 4pm est check out rage3d.com and log into their irc channel because they are having a live chat session with the driver makers from ATI concerning linux drivers. I wish I could be home from work at that time, because I sure would tell them what I think.

---

### Post by HiddenWolf on 2004-11-11
When I made the full-time switch to linux, I soon figured out how lucky I am.

I run a very crappy 9200, the last one reasonably well supported by both DRi and fglrx.
I bought the card to last me a few months since my older gfx2 wouldn't function on the agp slot of my new motherboard. Those few months have stretched to a year by now

Now I'm just going for amd64/pci-e. And for that I want to wait untill there are tv-tuners and audio cards using the pci-e bus. So I'll be happily using this pc for a while yet.

---

### Post by mattyh on 2004-11-11
Wow, a lot has happened on this thread since I last checked!  Sorry it took me so long to get back on this.  One possibility I'm finding on the gentoo forums is that you need to disable FSAA, because there is some known bug.  Might take me a bit to find it considering there is a 76 page thread on ATI driver problems [img]http://www.ubuntuforums.org/images/smilies/icon_exclaim.gif[/img].  I am sorry to hear you are having so many problems.  It sounds like there is compatibility issue with the dri module on your computer.  I really can't say I've had any experience with that.

---

### Post by HungSquirrel on 2004-11-11
FSAA was disabled by default after I ran fglrxconfig, but I still can't boot X with fglrx.

```
Option "FSAAEnable"                 "no"
```

---

### Post by HiddenWolf on 2004-11-11
DRI either works, or it doesn't work.

In gentoo I've had installs where it came up first boot, then an identical install on a virtually identical system, and never got it to work.
Debian is even worse.


For graphics problems, trial and error is the key.
Go into #ubuntu IRC, ask for help, and pray there is someone with the patience to walk you through it.

---

### Post by HungSquirrel on 2004-11-11
I FIXED IT!!!!!!!!!!111111  HOO-AH!!!!!1111  W00T!!!!!1111  ET CETERA!!!!!111



Err, sorry, I am just excited.  :)


First, a bit of background.  ATI graphics cards [don't play nicely with non-DDC monitors](http://www.ati.com/support/infobase/3955.html).  DDC is a sort of plug n play technology for monitors.  My ancient CTX VL950 doesn't have DDC, so my Radeon card doesn't play nicely with it.  The solution is to disable DDC.

Well, I was looking through XF86Config-4 and I noticed this line:

```
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
```

By removing the comment on that line and restarting X, not only did I get X to start, but I also got wonderful 3D DRI acceleration.  Hope this helps someone.


P.S.  WOO-HOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!111111111111111oneoneone

---

### Post by Slovak on 2004-11-11
You just became my best friend IF this works, brb.........

---

### Post by Slovak on 2004-11-11
It didn't work for me  :cry:  Post your xf86config so I can see what you have in there.

---

### Post by tUrtleAE86 on 2004-11-11
I guess it was worth the 5 days wait. =]

I followed the BinaryDriverHowTo from the Ubuntu Wiki.

sudo apt-get install linux-386
sudo apt-get install fglrx-driver
echo fglrx | sudo tee -a /etc/modules 

sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/XF86Config-4

In your XF86Config-4 file, comment out the following section:
Section "DRI"
       Mode    0666
EndSection

The results:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

But, for some reason I can only run this as root.

When I run as regular user, I get:

libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.3 Mesa 4.0.4

So, this seems like a permissions or environment thing. Any ideas??

---

### Post by Slovak on 2004-11-11
[QUOTE=tUrtleAE86]I guess it was worth the 5 days wait. =]



In your XF86Config-4 file, comment out the following section:
Section "DRI"
       Mode    0666
EndSection

[/QUOTE]

Comment out what? all three lines? Section "DRI"
       Mode    0666
EndSection

All that does is boot to a black screen for me. DRI=3D in ATI, without it no 3D.

---

### Post by Slovak on 2004-11-11
[QUOTE=HungSquirrel] The solution is to disable DDC.

Well, I was looking through XF86Config-4 and I noticed this line:

```
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
```

By removing the comment on that line and restarting X, not only did I get X to start, but I also got wonderful 3D DRI acceleration.  Hope this helps someone.


[/QUOTE]

Well I am glad it worked for you, my monitor is newer and needs DDC, so it didn't work for me.

---

### Post by HungSquirrel on 2004-11-12
> In your XF86Config-4 file, comment out the following section:
Section "DRI"
Mode 0666
EndSection

. . .

But, for some reason I can only run this as root.
The Section "DRI" details who is allowed to access the 3D renderer.  If you comment out that section, only root can use it.


> Post your xf86config so I can see what you have in there.

[http://hungsquirrel.org/XF86Config-4](http://hungsquirrel.org/XF86Config-4)

---

### Post by Slovak on 2004-11-12
Isn't that some crap, the only thing in your config that is different than mine is your monitor resolutions, and  sync rates, other than that exactly the same and no 3D for me  #-o  I have even changed my resolutions and sync rates to very conservative sections and no go for me. I still get the dri crap as being missing when I comment out dri, and when I don't comment it out I just get the infamous black screen of death.

---

### Post by tUrtleAE86 on 2004-11-12
Ahhhh it all make sense now. I thought that DRI and DRM were unrelated.

Thanks!  :mrgreen:

---

### Post by HungSquirrel on 2004-11-12
Slovak,
I think I also changed this line from default.

```
Option "BlockSignalsOnLock"         "off"
```

Not sure what it does, but it's one of the things I fiddled with in my epic battle against the black screen of death.

Out of curiosity, is ther any way you could open your case and touch the power cord right around the area where it plugs into your video card?  I ask because mine sometimes gets REALLY hot and I was wondering if that's normal.

---

