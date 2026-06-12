---
title: "Ati Support Build in!"
date: 2004-10-11
forum: Hardware &amp; Laptops
---

### Post by xkcdmagic8 on 2004-10-11
The Ubuntu dev team should take special interest in getting the setup script customized so that graphics cards such as the ATI 9700 PRO and more are set up properly with fglrx and fully preform with direct rendering. If this is done Ubuntu would be a great distrubution where no other has gone.  (now i beg you) plz:)? i have a 9700 pro and i followed the instructions and the fglrx driver was not installed (the apt-get succeded but no module was found!) I would gladly switch to ubuntu but this is a big problem (i like playing games and i also like to know that all my hardware is preforming to its fullest potential!)

---

### Post by daniels on 2004-10-11
[quote=nitinshantharam]The Ubuntu dev team should take special interest in getting the setup script customized so that graphics cards such as the ATI 9700 PRO and more are set up properly with fglrx and fully preform with direct rendering. If this is done Ubuntu would be a great distrubution where no other has gone.  (now i beg you) plz:)? i have a 9700 pro and i followed the instructions and the fglrx driver was not installed (the apt-get succeded but no module was found!) I would gladly switch to ubuntu but this is a big problem (i like playing games and i also like to know that all my hardware is preforming to its fullest potential!)[/quote]

Unfortunately we can't install the fglrx driver by default, because it's very difficult to make a working configuration.  Every system has little tweaks and adjustments that need to be made, and they're all different.

---

### Post by xkcdmagic8 on 2004-10-11
im sure its possible to have at least the most basic setup installed with would give better preformance even if not tweaked. :) anyway theres always the possibility to compile the fglrx driver on install - so it would detect it and compile it to ur needs and install it. :)

---

### Post by daniels on 2004-10-12
There is no 'most basic setup' with fglrx.  Some machines require the internal AGPGART, some do not.  Some require a crazy TLS option.  Some require explicit disabling of some features.  Some require your AGP bridge to be ramped down to 4x in the BIOS.

There is no sane default setup we can do that will work in most cases.

---

### Post by xkcdmagic8 on 2004-10-12
damn :) wish it would work just like in windows :)

---

### Post by AndersAA on 2004-10-13
dont use the ati driver per default, in it's current state it burns out DDC info in most monitors, atleast has in mine, I dont want that set up per default....

---

### Post by daniels on 2004-10-13
We cannot support binary-only drivers, in any case.

---

### Post by HungSquirrel on 2004-10-15
> i followed the instructions
What instructions?

Anyway, I registered here because I want to get my ATI acceleration working again.  I tried Ubuntu last week and liked it, especially because getting ATI drivers to work was a snap--*apt-get install fglrx-driver*, change my driver to fglrx, restart X, and boom! I had 3D acceleration.

Ubuntu uses the much improved Debian installer, so I decided to give Debian Sarge unstable a shot with the new installer (I had bad luck with the old one).  Well, apparently fglrx is a pain to install in Debian.  After two days of trying, I gave up and went back to Ubuntu.

...And now I can't get 3D to work.  [img]http://forum.hungsquirrel.org/images/smiles/icon_dumbass.gif[/img]


Edit: Disregard the above.  Forgot to install the restricted modules.  glxgears is reporting ~2500fps.

I'd like to take this opportunity to thank the developers for thinking of all these little things and making them so much easier.  I've never had ATI drivers working so easily before.   8)

---

### Post by daniels on 2004-10-16
[quote=AndersAA]dont use the ati driver per default, in it's current state it burns out DDC info in most monitors, atleast has in mine, I dont want that set up per default....[/quote]

By 'the ati drivers', you do mean fglrx rather than the default 'ati'/'radeon', right?

---

### Post by claymore on 2004-10-22
[quote=HungSquirrel]Anyway, I registered here because I want to get my ATI acceleration working again.  I tried Ubuntu last week and liked it, especially because getting ATI drivers to work was a snap--*apt-get install fglrx-driver*, change my driver to fglrx, restart X, and boom! I had 3D acceleration.[/quote]

Hello, all.  I'm not completely new to linux, but I am still pretty much a total idiot.  I tried to follow the instructions on the wiki, etc. (the link above is now dead), and I think I have everything working except that I don't know how to change the driver in ubuntu over to fglrx.  I have a Radeon 8500, which I was able to get going in hardware in Mandrake.  If I run fglrxconfig in Ubuntu, X completely stops working no matter what setting I put in.

---

### Post by nuopus on 2004-10-23
[QUOTE=nitinshantharam]The Ubuntu dev team should take special interest in getting the setup script customized so that graphics cards such as the ATI 9700 PRO and more are set up properly with fglrx and fully preform with direct rendering. If this is done Ubuntu would be a great distrubution where no other has gone.  (now i beg you) plz:)? i have a 9700 pro and i followed the instructions and the fglrx driver was not installed (the apt-get succeded but no module was found!) I would gladly switch to ubuntu but this is a big problem (i like playing games and i also like to know that all my hardware is preforming to its fullest potential!)[/QUOTE]

It is very easy to get it working ...

First download the latest ATI driver RPM from the ATI website here: [http://www2.ati.com/drivers/linux/fglrx-4.3.0-3.14.1.i386.rpm](http://www2.ati.com/drivers/linux/fglrx-4.3.0-3.14.1.i386.rpm)

Second, install it with alien. (alien -i fglrx-4.3.0-3.14.1.i386.rpm)

Then switch to the directory to build the modules. (cd /lib/modules/fglrx/build_mod)

Build the modules. (sh make.sh)

Switch to the fglrx directory to install it. (cd /lib/modules/fglrx OR cd ..) :-)

Run the installation: (sh make_install.sh)

Now run fglrxconfig to configure it and voila you have it!

I actually renamed the ubuntu made XF86Config-4 to XF86Config-4.orig before I did the fglrxcofnig and used vi to merge the two files because ubuntu handled my touchpad and mouse at the same time nicely and they have other options in there like font paths and such .... but it should work just letting the fglrx program do it.

---

### Post by chewy on 2004-10-23
[QUOTE=nuopus]It is very easy to get it working ...

First download the latest ATI driver RPM from the ATI website here: [http://www2.ati.com/drivers/linux/fglrx-4.3.0-3.14.1.i386.rpm](http://www2.ati.com/drivers/linux/fglrx-4.3.0-3.14.1.i386.rpm)
[/QUOTE]

has anyone had any success following this procedure on amd64?
obviously, i386 and amd64 will differ. but by how much and where?

---

### Post by nuopus on 2004-10-23
[QUOTE=chewy]has anyone had any success following this procedure on amd64?
obviously, i386 and amd64 will differ. but by how much and where?[/QUOTE]

Well the only thing I can say is try it? LOL

---

### Post by motu on 2005-03-01
hi all, i've tried to follow this procedure but that's what i get for the "sh make.sh":

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
root@motu:/lib/modules/fglrx/build_mod #


i really don't know what to do.

please help

motu

---

### Post by dewey on 2005-03-02
When I try to sudo alien -i, this is my output.
```

dewey@ubuntu:~ $ sudo alien -i fglrx*
dpkg: error processing fglrx-4-3-0_8.8.25-2_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx-4-3-0_8.8.25-2_i386.deb

```

I'd appreciate it if anyone could help me.

---

### Post by amp_man on 2005-04-03
are you using the driver link posted above and hoary? If so, hoary now uses x.org instead of xfree86, so go to the ati website and get the latest x.org version...if not, get the latest version anyways, a newer one has been released

edit: or just use the ati how-to here: [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) 
can't guaratee it works, I'm waiting til tomorrow to play with it

---

### Post by bongo on 2005-05-11
**MOTU:**
(Quoted from [http://www.mepis.org/node/3307](http://www.mepis.org/node/3307) )
> irst download the relevant source for whatever kernel you're using (e.g. 2.6.7) and unpack it to /usr/src/linux-2.6.7 and use the command ln -s /usr/src/linux-2.6.7 /usr/src/linux (or linux-2.4.26). Download the fglrx package from the ATI website and run alien fglrx_4.3.0-<version>.i386.rpm followed by dpkg -i --force-overwrite fglrx_4.3.0-<version>.i386.deb (the --force-overwrite switch is needed to overwrite libGL.so from the xlibmesa-gl package). Next compile the fglrx modules:


I recommend going to the linked page and read the rest of the information. But basically, unpack the rpm with alien to a deb file and then use dkpg to force overwrite the xlibglmesa-gl package.

---

### Post by binks on 2005-05-11
ok i am the noobie of all noobies and i got 3d working in 5 mins all i did was add the extra repsitories from the newbi guides 
then i used synaptic to install fglrx for xorg

then i did this bit   

The driver package provides an automatic configuration tool called fglrxconfig. Just don't use it, OK? fglrxconfig is useful if you want a dual-head setup, but before you try that please make sure that a single-head setup works by editing your XFree86 configuration file as outlined below. Also note that fglrxconfig will overwrite your existing XFree86 configuration file! 
Edit your /etc/X11/XF86Config-4: 
Section "Module"
  ...
  Load "GLcore"
  Load "glx"
  Load "dri"
  ...
  # Load "extmod" but omit DGA extension
  # (the DGA extension is broken in the fglrx driver)
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection
  ...
EndSection

Section "Device"
  Identifier "ATI"
  Driver     "fglrx" # this is the important bit

# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC"

# === Video Overlay for the Xv extension ===
  Option "VideoOverlay" "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  Option "UseInternalAGPGART" "no"
EndSection

Section "Screen"
  Identifier "your screen"
  Device     "ATI"
  Monitor    "your monitor"
  DefaultDepth 24
  SubSection "Display"
    Depth 24
    Modes "1280x960" # this is only an example,
                     # use your preferred resolution here
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

Stop and restart your X server. Figuring out how to do that on your system is left as an exercise, but usually you'll have to switch to a virtual console (text mode) by pressing Ctrl+Alt+F1, then stop and restart your display manager (kdm, gdm, etc.). If you know no better than to reboot your system, you will be in a lot of trouble if things don't work as expected: you might be stuck with just the console, or things could go really wrong and you could have to reboot into single user mode because your display and keyboard are completely locked. So please do learn how to properly stop and restart the X server. 
If it breaks your system, you keep all the pieces and I don't care. (But let me know what happened, OK?) 
 After your X server starts, check if OpenGL acceleration is enabled. Open a shell and type fglrxinfo or glxinfo: the "OpenGL renderer string" should say something like "RADEON 9600 XT Generic"; if it says "Mesa GLX Indirect" instead, it means that there is a problem. 


and it works cheers the best support forum ever 
thanks now for the dvb-c

---

