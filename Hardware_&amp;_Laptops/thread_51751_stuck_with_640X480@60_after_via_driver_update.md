---
title: "stuck with 640X480@60 after via driver update"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by hlm_worker on 2005-07-25
I successfully  :) followed the step by step script :
[http://www.ubuntuforums.org/showthread.php?t=37025&page=3&pp=10](http://www.ubuntuforums.org/showthread.php?t=37025&page=3&pp=10)
to update the VIA Unichrome driver (3D...) for the KM400A chipset.
But now I'm stuck with 640x480@60Hz resolution.
I got an LCD screen : 1280x1024 and 60 or 75Hz is available

I tried to add HorizSync, VertRefresh and Modeline fields into xorg.conf : it doesnt change anything.
**It works perfectly with vesa driver** without these fields.

```
Section "Device"
        Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
EndSection

Section "Monitor"
        Identifier      "CMC 17 AD"
        HorizSync        30-82
        VertRefresh      50-75
        Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
        Monitor         "CMC 17 AD"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```
And here are the logs :
```
(II) VIA(0): CMC 17 AD: Using hsync range of 30.00-82.00 kHz
(II) VIA(0): CMC 17 AD: Using vrefresh range of 50.00-75.00 Hz
(II) VIA(0): Clock range:  20.00 to 230.00 MHz
(II) VIA(0): ViaValidMode: Validating 1280x1024_60.00 (108880)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): ViaValidMode: Validating 640x350 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x400 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 720x400 (35500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) VIA(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (25200)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (31500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 640x480 (36000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) VIA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
../..
(II) VIA(0): ViaValidMode: Validating 1280x960 (108000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x960 (148500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1280x960" (hsync out of range)
(II) VIA(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x1024 (108000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x1024 (135000)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VIA(0): ViaValidMode: Validating 1280x1024 (157500)
(II) VIA(0): ViaModePrimaryVGAValid
(II) VIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) VIA(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)

../..
```

Any ideas or xorg.conf files?

---

### Post by gray-squirrel on 2005-07-25
I have the same exact situation.  I thought it might be a monitor problem - I have a MAG LT565 - but I no longer suspect that's the case.

I've also tried substituting certain files from previous snapshots, but still can't go higher than 640x480.

I sent a message to the Unichrome user list with my xorg.conf and Xorg.0.log.  You may want to [sign up](http://lists.sourceforge.net/lists/listinfo/unichrome-users) to the list and stay tuned for a solution.

[http://lists.sourceforge.net/lists/listinfo/unichrome-users](http://lists.sourceforge.net/lists/listinfo/unichrome-users)

In the meantime, I will wait for the next snapshot to be posted, and then I will be back at trying to make it work again.

adding: I had the same problem when upgrading from Ubuntu 4.10 to 5.04, but with a noisy screen back then.

---

### Post by hlm_worker on 2005-07-25
Bug#318348 on debian-X : xserver-xorg: Unichrome driver will only use 640x480 on KM400

I found this : [http://www.mail-archive.com/debian-x@lists.debian.org/msg36674.html](http://www.mail-archive.com/debian-x@lists.debian.org/msg36674.html) 

I try to investigate further :-k  ...

---

### Post by gray-squirrel on 2005-07-25
[QUOTE=hlm_worker]Bug#318348 on debian-X : xserver-xorg: Unichrome driver will only use 640x480 on KM400

I found this : [http://www.mail-archive.com/debian-x@lists.debian.org/msg36674.html](http://www.mail-archive.com/debian-x@lists.debian.org/msg36674.html) 

I try to investigate further :-k  ...[/QUOTE]

You have some great investigating skills there.  Thanks.  I will try this out later this evening.  I haven't done much compiling of sources for a while, so this will make my upcoming day(s) interesting.

I was going to say earlier that typing "sudo dpkg-reconfigure xserver-xorg" had no effect, but you posted the solution before I could reply.

---

### Post by gray-squirrel on 2005-07-25
Okey, I think I located the file in question.  It's via_mode.c, and the [corrected](http://cvs.freedesktop.org/xorg/xc/programs/Xserver/hw/xfree86/drivers/via)  version (incorporating the fix mentioned in the link above) can be found at

[http://cvs.freedesktop.org/xorg/xc/programs/Xserver/hw/xfree86/drivers/via/](http://cvs.freedesktop.org/xorg/xc/programs/Xserver/hw/xfree86/drivers/via/)

and selecting via_mode.c from the list, version 1.8.

It looks like it's just a matter of replacing the old file with this, and recompiling.  I'll let you all know how it works out.

---

### Post by hlm_worker on 2005-07-25
I just found it out. But not quick enough to reply before you.
I need to retrieve the source files package and recompile it.
Just need to find how to do this...

---

### Post by gray-squirrel on 2005-07-26
Success at last; a major hurdle cleared.  The driver is finally working.

Here is an easy way to deal with the x.org source file:


1. Go to [http://www.x.org/X11R6.8.2/src](http://www.x.org/X11R6.8.2/src) to download the X11R6.8.2 source (you can select any mirror location before downloading it).

2. After the source has been downloaded, unzip and then untar the file.  I put my copy inside /usr/src, you may choose another location:

```
sudo cp ~/Desktop/X11R6.8.2-src.tar.gz  /usr/src
cd /usr/src
gunzip X11R6.8.2-src.tar.gz
tar -xvf X11R6.8.2-src.tar
```

The X11 source files should all be in a directory called xc.

3. Then, three packages need to be downloaded and installed before going further, if they are not already on your system:

```
sudo apt-get install bison
sudo apt-get install flex
sudo apt-get install libpam0g-dev
``` 

(It took me three compiling attempts before figuring this out.)


4. Now, the fun begins.  We're going to go to the xc directory and begin compiling:

```
cd xc
make World > World.log 2>&1
```

While the computer is at work, you can watch a movie or take a power nap; this will take between 90 minutes to 2 hours (at least it did on my Sempron 2400+ system).  You can check the World.log file after it is finished to see if there are any errors in the compilation.

5. If the compiling succeeds, then we can test the via directory to see if everything is fine.

```
cd  /usr/src/xc/programs/Xserver/hw/xfree86/drivers
make Makefiles
cd via
make

```

6. Next, time to bring the updated VIA driver files in, using CVS.

```
cd /usr/src/xc/programs/Xserver/hw/xfree86/drivers
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/unichrome co xfree86
```

If prompted for a password, press Enter.

The files will be copied over into a folder named xfree86.  When that is finished, then type

```
rm -rf via
ln -s xfree86 via
```

to remove the old via directory and create a symlink so that we can refer to the xfree86 directory as via.

7. Now, we get to create new Makefiles and and the new VIA driver which will allow resolutions higher than 640x480 for the KM400:

```
make Makefiles
cd via
make
sudo make install
``` 

The driver via_drv.o can now be found in /usr/X11R6/lib/modules/drivers.  If it is not there, then you can copy it there:

```
sudo cp via_drv.o /usr/X11R6/lib/modules/drivers
```

Then it's only a matter of editing xorg.conf to once again reflect the change to the VIA Unichrome driver and restarting the computer.

I ran glxgears at 1024x768, and it reported a frame rate of 575.0 fps.  Not bad, not bad.

I'm not quite done yet; I want put this to the ultimate test: foobillard, followed by an excursion on the battlefield in Scorched3D.



* note - I put the X11 source in /usr/src, but I already added myself to the src group beforehand.  The same lines should work as listed if you chose to put the source in another folder and compile from there.  Just replace all occurences of /usr/src/xc with (your location)/xc.

---

### Post by gray-squirrel on 2005-07-26
I almost forgot to say that once everything works out for you, you can comment out the modelines in your xorg.conf file so that you have the option of setting your resolution and/or refresh rate.

---

