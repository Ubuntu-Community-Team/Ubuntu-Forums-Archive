---
title: "ATI AIW Capture?"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by FyberOptic on 2005-07-05
Hiya, maybe somebody can shed some light on this for me.  I've got an ATI All-In-Wonder 9600xt, and just got it setup to use glrx for 3d support and it works great.  But now I've tried to figure out how to capture video, but I've come up at a total loss.  

When I run xawtv, I get:

```

WARNING: v4l-conf is compiled without DGA support.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```

So obviously the device isn't even being detected, as /dev/video0 really doesn't exist, but no matter how much looking I've done, I can't find any mention of how to make anything work.  I heard about Gatos, and installed that package, but xatitv just gives me:

```

GATOS: No ATI PCI/AGP Cards ?
GATOS: gatos_inita(): Invalid argument
xatitv: gatos_init(): Invalid argument

```

So I have no idea where to go from here.  I'd really appreciate if somebody could help me get this working, if it's even possible.  I've got Ubuntu setup pretty good here for multimedia on my desktop, and wouldn't mind using it more often if I could just have my tv-in capability.  Thanks in advance!

---

### Post by WildTangent on 2005-07-05
try tvtime

```
sudo apt-get install tvtime
```

and then run it by typing tvtime in a terminal window (it also appears in your application menu IIRC)

-Wild

---

### Post by FyberOptic on 2005-07-05
I get the same deal from that program:  videoinput: Cannot open capture device /dev/video0: No such file or directory

In the Input Source setting for it, I can't click the Change Video Source button or anything, either.  Unless that's only for adjusting things on a card which actually works.

---

### Post by sgamer on 2005-08-31
*bump* 

I'm experiencing this same problem...any solutions?

---

### Post by camp on 2005-09-07
Hi there,

I'm experiencing the same... haven't found anything to solve it either... Have you managed to make your card work yet? Or still the same?

Anyone that can help me/us!?
/Camp

---

### Post by Tylo on 2005-09-19
I'm going to go ahead an bump this again.

I have an AIW 9600 pro, and have the latest drivers loaded and working correctly. However, I experience the same problem. I know that the ATI driver do not support the TV capture for AIWs.

Does this mean it isn't ever going to work? Has anyone ever got it working?

---

### Post by Ibbelz on 2005-12-18
I am experiencing the same problem over here? Still no solution for this problem? I really want to use my capture card in Ubtuntu. Please help. :)

---

### Post by freagel on 2005-12-21
Thanks for the answer, I guess we should wait for support then.
Great to hear I am not alone in this world.

---

### Post by Noremacam on 2005-12-21
I have a 9800 AIW, and I've had no luck either. The ati website says it doesn't support video capture for linux... Shame.....

---

### Post by walopower on 2006-01-05
Same problem here.
Remote control working without doing nothing.
I install before aiw 9800le to Win XP, but that is not easy either.
But when aiw is finaly installed, it is easy to use and capture very cood guality video. But ATI Multimedia Center for windows, is very buggy.
In windows has individually WDM drivers, i think that is what we need...

---

### Post by AdrianVeidt on 2006-01-05
Look fellas. The GATOS project made capture software for AIW cards for years. That code was merged into the unstable end of XORG recently. The brand new stable release of XORG does have GATOS drivers included, so the next release of Ubuntu, Dapper, will have full support for TV/Capture, or you can upgrade to the unstable release right now and get it. Software like TVtime and such rely on the BTTV hardware chips, which ATI does not use, so that stuff won't work. GATOS doesn't create dev/video0 to capture, so the software doesn't have a clue what you're talking about when you try to use it. Upgrade to Dapper, or some other OS that uses the new XORG 6.9/7.0, such as PCLinuxOS, and you'll get the capture features.

---

### Post by walopower on 2006-01-06
Thanks so much.
(Releace will coming at Ubuntu 6.04 (The Dapper Drake): April 2006)


You can get it work now also, but it is more complicate.
[http://gatos.sourceforge.net/](http://gatos.sourceforge.net/)
Say that you need 

ati.2 (maybe fglrx will work too?)
km
AVview (Maybe any app will work too)

So only driver you possibly need is km.
Unfortunately, I am allready installed km, but not /dev/video0 still yet.
Maybe it is still possible?
Do i need compile kernel after installed km, becouse it is kernel module?

There is also discussion of same subject.
[http://ubuntuforums.org/showthread.php?t=90520](http://ubuntuforums.org/showthread.php?t=90520)

---

### Post by AdrianVeidt on 2006-01-06
ATI's closed-source drivers will work for 3d acceleration, but not for the TV in/out features of AIW cards. ATI has put exactly zero effort into making a Multimedia Center for linux. I remain somewhat confident that they will take up this effort at some point, but until then, there are drivers made by third party programmers. The binaries on GATOS's site were designed for previous versions of the X server. Installing them on Ubuntu will result in no noticable change. Compiling the drivers into the X server may or may not work. That's beyond my knowledge level at this point. I'm simply waiting for the new Xorg 6.9/7 to be incorporated into Ubuntu so I can use the TV features of this card.

---

### Post by Zyphrexi on 2006-02-01
I'm thinking of getting the AIW 2006 edition, but I don't know how great the support is. Normally i'm an Nvidia guy, but that AIW looks tasty. so if i dist-upgrade to dapper the AIW should work? how well? Can anyone report on it's abilities? I want to get all the info before i commit to a card.

---

### Post by techflat on 2006-04-04
Hi there people.

I've been having the same problem for a while, only my card is an All-in-Wonder X600 Pro.

I havn't been able to make it work yet.

About what gatos does with the /dev/video0 maybe you can explain it a little bit further. I found, not too hard to see it, the file where tvtime gets it's input device configuration, maybe changing something there will work but I don't know.
(/etc/tvtime/tvtime.xml)

Hopefully ati will create some good working drivers for linux.

I'm not planing on buying another tv card so I still use windows when I want to work and watch tv.... [-( 

If anybody has the solution, please post it!!!!



(PS: ati.2 drivers seem to work better for me. I am not shure if it's only an impression I have)

---

### Post by dreadthenight on 2006-05-04
I've been browsing ATI AIW related posts here, hoping that I could figure out a way to get capture functionality working.  I installed Ubuntu today on a new machine and couldn't find any option to upgrade it to "unstable" - I looked through the update program, package manager, and ran some Google searches.  Is upgrading to unstable easy to do?

Thanks for the advice!

[QUOTE=AdrianVeidt]Look fellas. The GATOS project made capture software for AIW cards for years. That code was merged into the unstable end of XORG recently. The brand new stable release of XORG does have GATOS drivers included, so the next release of Ubuntu, Dapper, will have full support for TV/Capture, or you can upgrade to the unstable release right now and get it. Software like TVtime and such rely on the BTTV hardware chips, which ATI does not use, so that stuff won't work. GATOS doesn't create dev/video0 to capture, so the software doesn't have a clue what you're talking about when you try to use it. Upgrade to Dapper, or some other OS that uses the new XORG 6.9/7.0, such as PCLinuxOS, and you'll get the capture features.[/QUOTE]

---

### Post by pedalwrench on 2006-06-23
Just to let every one know that I too have been dealing with this issue for a while.  So far I found that ATI does not really care about the linux community and will not be releasing TV-in driver support.  ](*,) 

I found that the best option is to sell my AIW 9600 Pro and get a new nvidia card and a haupauge card to replace the one ATI card. 

Anyone interested in ATI card? cheap? PM me.:mrgreen:

---

### Post by slackerbox on 2006-07-31
I am also interested in getting this work.  I have a ATI Rage 128 All-in-Wonder card that I'm trying to get working for video input.

I've installed the **GATOS** software package with Synaptic but it doesn't see the /dev/video0 object so it won't do anything.

Has anyone figured this out yet?

---

### Post by ricesteam on 2006-08-01
Looks like there still no solution...seems like a small fraction only have this problem, so I think we're on our own.

So far I'm been trying to install AvView from [http://gatos.sourceforge.net/avview.php](http://gatos.sourceforge.net/avview.php).

I'm still an inexperienced user, and have failed to install it successfully.  It seems like AvView depends on ffmpeg which in turn, depends ALSA 0.9.x.  I think I've installed most of the required libraries, but I'm not sure since none of the programs will install.


So now I'm stuck trying to install ffmpeg.

If we work together, we can get this working!

---

### Post by rjean on 2006-08-07
I have ATI AIW 128 Pro. I have had it showing TV in linux, but that was a few years ago, probably in Gentoo. I followed the Gatos instructions, but they were written for XFree86 specific versions. So far I haven't tried km or Avview with Ubuntu.  I have tried MAKEDEV video4linux and although the output says it is making all the devices - (including video0) they don't show up in dev.

---

### Post by gilbert27 on 2006-09-25
Hi!!

Finally, I found a way to make my All In Wonder 9600XT work under K/Ubuntu Dapper Drake 6.06 (and Gentoo 2006.1)!!

After a lot of trial, here's how I did it!

The All In Wonder 9600XT is based on ATI's Theatre 200 video capture and encoding chip ... check [here](http://www.tweaknews.net/reviews/aiw9600xt/) and [here](http://www.firingsquad.com/hardware/ati_all_in_wonder_9600xt/)
to know more about this multimedia card!!

First, download (with Synaptic or Adept) everything in relation with xserver-xorg-...., X11-..., X11proto...etc  and particularly xserver-xorg-ATI.

Go into your motherboard BIOS ("Advanced Menu" "Chip Configuration") and set those following options this way::

AGP Performance Control       Enabled    (optional)
[color=red]** AGP Disk Write Control          Enabled**[/color]
Video Memory Cache Mode    [USWC]        (optional)(Activating this option causes fuzzy horizontal lines on my screen! Check if your Graphic Card support it!)

The most important option to enable is [color=red]**AGP Disk Write Control**[/color] ..... otherwise your screen will freeze when you'll start AVView!


More about these options [here](http://www.rojakpot.com/showFreeBOG.aspx?lang=0&bogno=260) and [here](http://www.sharkyextreme.com/guides/hwGuides/article.php/1463741)



And now here's the most important part to make TV Capture work!
[color=red]**Your All In Wonder must be already installed under Windows!**[/color]
Go to your Windows partition and copy this file " [http://marc.theaimsgroup.com/?l=livid-ati&m=110160050909101&w=2]**ativmc20.cod**]()"

(this module will necessary to capture TV Channels)... (and it still doen't exist under Linux)
It should be located here :::
C:\WINDOWS\system32\drivers\[color=blue]ativmc20.cod[/color]

copy it to your K/Ubuntu partition in
[color=blue]/usr/lib/xorg/modules/multimedia/[/color]
and rename it [color=red]**rt2_pmem.bin**[/color]
$ cd /usr/lib/xorg/modules/multimedia
$ sudo mv ativmc20.cod rt2_pmem.bin
$ dir /
$ dir /usr/lib/xorg/modules/multimedia
>  bt829_drv.so    rt2_pmem.bin    tda9885_drv.so         theatre_drv.so
fi1236_drv.so   tda8425_drv.so  theatre200_drv.so      uda1380_drv.so
msp3430_drv.so  tda9850_drv.so  theatre_detect_drv.so 


[color=red]Your graphic card driver must be Radeon ATI (Xorg modular 7.0 or 7.1)[/color] and not ATI fglrx!!
Now edit your /etc/X11/xorg.conf file and add the following option "AGPFastWrite" in the Section "Device"

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_dateoftheday
$ sudo nano -w /etc/X11/xorg.conf
Section "Device.............
......
....
   [color=red] Option     "AGPFastWrite" "1"[/color]
......
......
EndSection

For exemple, here's my copy of xorg.conf file::
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
        Option          "XkbVariant"    "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
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
        #Option     "VideoKey"                  # <i>
        #Option     "RageTheatreCrystal"        # <i>
        #Option     "RageTheatreTunerPort"      # <i>
        #Option     "RageTheatreCompositePort"  # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"                 # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "RenderAccel"               # [<bool>]
      [color=red]**Option     "AGPFastWrite"    "1"**[/color]
        Identifier      "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "S/M 950p"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Monitor         "S/M 950p"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "640x480"
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
EndSection

Section "DRI"
        Mode    0666
EndSection 


Reboot your system!
and check if everything loaded fine!
> 
$ cat /var/log/Xorg.0.log
.........
........
.......
(II) RADEON(0): Tuner is on port 0
(II) RADEON(0): Composite connector is port 2
(II) RADEON(0): SVideo connector is port 6
(II) RADEON(0): Rage Theatre: Connectors (detected): tuner=0, composite=2, svideo=6
(II) RADEON(0): RageTheatre: Connectors (using): tuner=0, composite=2, svideo=6
(II) RADEON(0): video decoder type used: 0x0006
(II) RADEON(0): Going to load the corresponding theatre module
(II) Loading sub module "theatre200"
(II) LoadModule: "theatre200"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre200_drv.so
(II) Module theatre200: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): Microcode: Use default microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use default microcode type: BINARY
(II) RADEON(0): Microcode: device_id: 4d4a
(II) RADEON(0): Microcode: vendor_id: 1002
(II) RADEON(0): Microcode: rev_id: 1b
(II) RADEON(0): Microcode: num_seg: 4
(II) RADEON(0): Microcode: dsp_init OK
(II) RADEON(0): Microcode: dsp_download OK
(II) RADEON(0): VIP_GPIO_CNTL: 600001
(II) RADEON(0): VIP_GPIO_INOUT: 600000
(II) RADEON(0): VIP_GPIO_CNTL: 600011
(II) RADEON(0): VIP_GPIO_INOUT: 710010
(II) RADEON(0): Rage Theatre setting standard 0x0000
(II) RADEON(0): Microcode: Use microcode path: /usr/lib/xorg/modules/multimedia/rt2_pmem.bin
(II) RADEON(0): Microcode: Use microcode type: BINARY
(II) RADEON(0): Microcode: device_id: 4d4a
(II) RADEON(0): Microcode: vendor_id: 1002
(II) RADEON(0): Microcode: rev_id: 1b
(II) RADEON(0): Microcode: num_seg: 4
(II) RADEON(0): Microcode: dsp_init OK
(II) RADEON(0): Microcode: dsp_download OK
(**) RADEON(0): RADEONScreenInit finished
........
.........
......

check if any  errors appears:
$ cat /var/log/Xorg.0.log | grep EE






Now download and compile AVView and ffmpeg! (it is not necessary to install it)

Download ffmeg-0.4.8 :
$ cd $HOME
$ mkdir Downloads
$ cd Downloads
Download ffmpeg-0.4.8 from [http://www.escomposlinux.org/lfs-es/blfs-es-5.1/multimedia/ffmpeg.html](http://www.escomposlinux.org/lfs-es/blfs-es-5.1/multimedia/ffmpeg.html)
$ wget [http://switch.dl.sourceforge.net/sourceforge/ffmpeg/ffmpeg-0.4.8.tar.gz](http://switch.dl.sourceforge.net/sourceforge/ffmpeg/ffmpeg-0.4.8.tar.gz)
$ tar -zxvf ffmpeg-0.4.8.tar.gz
$ cd ffmpeg-0.4.8
  [color=red]**ffmpeg is tricky to configure! you will have to adjust the make and cflags options according to your own hardware (CPU)! **[/color]
I have an AMD Athlon XP 1800+
Also I have not figured out how to configure mingw32 and faad options (just don't include them)

Check here ::: [http://gentoo-wiki.com/CFLAGS](http://gentoo-wiki.com/CFLAGS) and [http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)
(I tested ffmpeg under Gentoo ... but it also compile fine under K/Ubuntu) (Take note that ffmpeg doesn't compile with gcc-4.0... so use gcc-3.4)

$ ./configure --cc=gcc-3.4 --cpu=athlon-xp --extra-cflags=-O2 -march=athlon-xp -pipe --enable-mp3lame --enable-vorbis --enable-a52 --enable-pp --enable-shared-pp --enable-shared

or more safely
./configure --cc=gcc-3.4 --cpu=athlon-xp --extra-cflags=-O2 -march=athlon-xp -pipe --enable-mp3lame --enable-vorbis

$ make


Download AVView here [http://sourceforge.net/project/showfiles.php?group_id=12629](http://sourceforge.net/project/showfiles.php?group_id=12629)

$ cd $HOME/Downloads
$ wget [http://switch.dl.sourceforge.net/sourceforge/gatos/avview-0.80.7.tar.gz](http://switch.dl.sourceforge.net/sourceforge/gatos/avview-0.80.7.tar.gz)
$ tar -zxvf avview-0.80.7.tar.gz
$ cd avview-0.80.7
the --cc= option doesn't exist in avview so I will use gcc-3.4 this way:::
$ export CC=/usr/bin/gcc-3.4

$ ./configure --with-ffmpeg=$HOME/Downloads/ffmpeg-0.4.8
> user@user-desktop:~/Downloads/avview-0.80.7$ ./configure --with-ffmpeg=$HOME/Downloads/ffmpeg-0.4.8
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... /usr/bin/gcc-3.4
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether /usr/bin/gcc-3.4 accepts -g... yes
checking for /usr/bin/gcc-3.4 option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of /usr/bin/gcc-3.4... gcc3
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking whether byte ordering is bigendian... no
checking how to run the C preprocessor... /usr/bin/gcc-3.4 -E
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for working alloca.h... yes
checking for alloca... yes
checking whether /usr/bin/gcc-3.4 needs -traditional... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for rint... no
checking for select... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strerror... yes
checking for dlopen in -ldl... yes
checking for uncompress in -lz... yes
checking for sin in -lm... yes
checking for pthread_create in -lpthread... yes
checking for vbi_capture_v4l_new in -lzvbi... yes
checking for snd_card_get_name in -lasound... yes
checking for lirc_init in -llirc_client... yes
The libraries mp3lame, ogg, vorbis and vorbisenc might be required by ffmpeg
checking for lame_encode_buffer in -lmp3lame... yes
checking for oggpack_write in -logg... yes
checking for vorbis_book_init_encode in -lvorbis... yes
checking for vorbis_encode_init in -lvorbisenc... yes
checking linux/videodev.h usability... yes
checking linux/videodev.h presence... yes
checking for linux/videodev.h... yes
checking libzvbi.h usability... yes
checking libzvbi.h presence... yes
checking for libzvbi.h... yes
checking for X11/extensions/Xinerama.h... yes
checking for XCreateSimpleWindow in -lX11... yes
checking for XInitExtension in -lXext... yes
checking for XvPutVideo in -lXv... yes
checking for XineramaIsActive in -lXinerama... yes
checking for Tcl configuration... found /usr/lib/tcl8.4/tclConfig.sh
checking for Tk configuration... found /usr/lib/tk8.4/tkConfig.sh
checking for existence of /usr/lib/tcl8.4/tclConfig.sh... loading
checking for existence of /usr/lib/tk8.4/tkConfig.sh... loading
checking ffmpeg version... ok
checking for ANSI C header files... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for fcntl.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for sys/ioctl.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... (cached) yes
checking whether /usr/bin/gcc-3.4 needs -traditional... (cached) no
checking for memset... (cached) yes
checking for strdup... (cached) yes
checking for strerror... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating start_avview.no_install
config.status: creating config.h
config.status: executing depfiles commands

------------------- Configuration -------------------

  X11 libraries                        -L/usr/X11R6/lib
  X11 cflags
  TCL location                        /usr
  TCL version                         8.4.12
  TK location                         /usr
  TCL version                         8.4.12
  ALSA support                        yes
  Movie recording                     enabled
  Path to compiled ffmeg source       /home/user_name/Downloads/ffmpeg-0.4.8

  Binaries will be installed in       ${exec_prefix}/bin
  Script files will be installed in   ${prefix}/share/AVview 

$ make

./start_avview.no_install

(under Gentoo I have to start it twice before it works)
---------------------------------------------------------
[i](optional) 
If you want to install it 
just do: (you must be root)
$ sudo make install
and to uninstall
$ sudo make uninstall[/i]
---------------------------------------------------------

To start it from your desktop just add this command with an icon! 

The AVView window will appear 
Select Control Window in the menu
Encoding must read NTSC-tuner (for local capture)(with an antenna)
Select Alsa Mixer and choose your sound card ... do the adjustment 
Sound will be located in LINE

Now my television work fine ....but I can't record anything!!! ..... yet!!!

When I'am clicking on RECORD it tells me::::

"Looking for km device that corresponds to PCI:01:00.0"

The program search for KM module (GATOS)!! (which we are not using)

and I&#12288;just don't know where is located my tuner in /dev ?
Someone have any idea about it?????


Also I still have not figured out how to make the FM tuner work! (I don't know where is my tuner in /dev)

---

### Post by CarpKing on 2006-09-28
I will be trying this soon!  This is a rather depreciated section of the forums though; perhaps you should post this in "Howtos, Tips, and Tricks."  

Do you know if this will also work with apps like TVTime instead of AVView?

---

### Post by gilbert27 on 2006-10-07
I followed your suggestion and I transfered everything [HERE](http://ubuntuforums.org/forumdisplay.php?f=100).

I know it also works with XAWTV so I suppose it should work with TVTIME (TV capture works with Xvideo)! ...but you'll have to find out how to configure  TVTIME with Xvideo!

---

### Post by themitchy on 2006-10-10
When configuring AvView it gives me

** Avview requires ALSA version 0.9.x

Which package does it look at to be up to date?

**Answered this myself: had to install libasound2-dev**

---

### Post by diskreet on 2006-10-16
Hi,

I also have a display card (Club 3d RADEON 9250 VIVO) with an (AIW) RAGE 128 chipset. I haven't been able to get a /dev/video0 to show up, but xawtv shows picture via the "Capture: overlay" method nonetheless. Alas, the picture has jitter/stutter.

If I've understood correctly, I could run the deinterlacing plugin (which might or might not fix the stutter) in xawtv if I'd get the card to appear correctly in /dev/video0. I tried the method above, copied the file from Windows, added:

```
Option "AGPFastWrite" "1"
...
Option "UseFBDev" "true"
```

to my xorg.conf. (Both of these lines were missing)

After reboot, 'cat /var/log/Xorg.0.log | grep EE' reported about missing framebuffer devices. No, there aren't any /dev/fb* present either.

Anyone have an idea what should I do? Is it even possible to get a RAGE128 card to show up in /dev/video0?

---

### Post by marksquare on 2006-10-26
I also have a radeon 9000 vivo with video capture.

Thanks for all the suggestion: I finally succeded in seeing may composite tv input.

For recording I used th km module by gatos and i succeed in recording video from avview (for audio i'm still studying..).

I have a 2.6.17 kernel and xorg 7.1 with debian sid.

The only thing I did was to go in the source of km module and comment the code in which there is the check for your drm kernel module (in radeon.c, if I remember well, where it says "upgrade your kernel"). 

Remember to load the km module before the drm and radeon module on startup and after videodev. I put it in /etc/modules (whith videodev) so it is modprobed before X starts.

As the km module is loaded you will see /dev/video0 as video capture device.

  Bye and thanks 
  Marco

---

### Post by urgru on 2006-10-28
Tried the above HOWTO with a Radeon 9800Pro All In Wonder.  Enabling AGPFastWrite and UseFBDev caused X.org to blackscreen on my machine, but the microcode module is loading cleanly w/ a log that exactly matches that in the HOWTO.

After installing various required libs and tcl/tk, I built ffmpeg (gcc 3.4, athlon64 for cpu and marc, no pp or sharing) and AVView.  AVView starts cleanly, but doesn't show any video or offer sound.

Any help or hints?  Have others gotten working video using the instructions above?  Is UseFBDev absolutely necessary?

---

### Post by watson540 on 2006-11-10
Hello guys,

I, too have struggled with the AIW features of ATI cards and have been following GATOS for a few years now.
    I was excited to see GATOS has been integrated with Xorg now and I Have managed to get a picture at times but not always. A few things:
The AGPFastWrite option will lock your box hard (it did mine) and is not needed.
To those of you wanting a '/dev/video' device with these cards, give it up, it simply cannot happen as this card does funny things that are only compatible with XV, so you can only use AVView, xawtv or possible mplayer or xine to view tv, no tvtime.
As of right now i have gotten a picture (no sound yet) but i dont get it all the time, I have to start avview and then play around with the 'debug' slider all the way at the bottom of the settings dialog (the one where you adjust the color and brightness, etc.) Also playing around with the overlay mode seemed to help. (has modes 1-3 to set)
You also cannot get it to show a picture while running beryl
I can see the 'snow' on every channel except for channel 3, which is the channel i hooked a vcr up to to test this, but as i said only sometimes if you play with enough settings you can get a picture to show up. But even if you save those settings the next time yoiu start avview it will be a blank screen again. To me it seems like a lost cause for the GATOS drivers because even when i did get a picture it wasnt too perfect anyway. Please if anyone else out there has experience chime in and maybe we can get this goping eventually. Any questions of me? just post them here and i will reply.

---

### Post by sysdemin on 2007-01-05
Hi All
    Great to know that someone also own ATI cards with multimedia capabilities.
    I have an ati 9250 vivo edition (r200 theatre chip but no TV-tuner) and I just got the video in to work in Edgy. I had to add the line  ```
Load    "theatre_detect"
``` into /etc/X11/xorg.conf in the modules section. i2c should also be there but it already was. I could then see that the chip was detected in /var/log/Xorg.0.log
   I then went to download AVview from sourceforge and had to install the packages```
 sudo apt-get install libasound2-dev build-essential libzvbi-dev tcl8.4-dev tk8.4-dev xorg-dev
```, before the ./configure script of AVview would complete without error. make then finished and gave a working executable where I can see composite video. Sound is taken care of via a seperate cable from sound out of video to the microphone jack on my soundcard. After trying to get this working under Debian and Dapper Drake the video in feature is finaly working :-) (It might had worked under Dapper if I had know about the theatre_detect module, I guess).
  It was not nescessary to set AGPfastwrite or FB device, microcode from windows etc. I guess the last is nescessary for the TV-in and not video in.
I would also like to transfer some of my old videos to harddisk, so Is the km nescessary for capture or just ffmpeg compiled into avview? Which other programs have people got running with the ati cards?

---

### Post by magquatre on 2007-01-21
im considering trying gilbert's instructions with my ati aiw 8500DV, does anyone know if it doesnt work with this older card?

UPDATE:

I can get tv and composite to work with sound using xawtv after doing gilbert's instructions (not including the ffmpeg, avview section). But after a session of using xawtv successfully and rebooting my machine, xorg blackscreens before the login screen loads. To fix it i run in recovery mode and just use my old xorg.conf file with the fglrx driver instead of the ati driver. So if i want to use the tv i have to fix my xorg.conf file, then reboot and then run xawtv. but from then on ill have to fix my xorg.conf file to the old driver before rebooting again.

Anyone know whats happening here?

```


Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Option "AGPFastWrite" "1"
        Identifier  "ATI Technologies, Inc. R200 BB [Radeon All in Wonder 8500DV]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
        Option "UseFBDev" "true"
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection



Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "ATI Technologies, Inc. R200 BB [Radeon All in Wonder 8500DV]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection


```

---

### Post by Garibaldi3489 on 2007-01-26
Any updates on this? I have an ATI AIW 9600 (not sure about the TX) and would like to try it too but I think I have fglrx

---

### Post by silverdoctor on 2007-03-20
Hey guys

I've got an ATI Radeon 9800 Pro 256MB with vivo.

Added

Load	"theatre_detect"
Load	"i2c"

in modules of xorg.conf as suggested.

and changed driver to "ati" under device

I can view composite in using avview - but only on the second time I start it up.

That's great but the video is jumpy, will make you sea sick or your eyes sore or something watching it. Same signal as windows and the it's fine in windows. What can I do to stop it from jumping?

Thanks.

---

### Post by superFerra on 2007-07-14
> **marksquare said:**
>  ...

Remember to load the km module before the drm and radeon module on startup and after videodev. I put it in /etc/modules (whith videodev) so it is modprobed before X starts.

As the km module is loaded you will see /dev/video0 as video capture device.

  Bye and thanks 
  Marco

Hi all,

i'm having problems compiling KM module:

i've installed from synaptic linux-headers-2.6.20.29 and build-essentials
tar xvf km-0.6...tgz (from gatos project)
cd km
but when i issue "make"
afeter few lines complain about "linux/config.h" missing
How can i fix it?
What am i missing?
Tried to install kernel-package, linux-source packages too but still doesn't compile.
May i've worng path set?
May i'm missing some packages??

Please help!!
TIA

---

### Post by superFerra on 2007-07-15
:confused:

up....

please

---

### Post by jfrieben on 2007-07-20
[QUOTE=superFerra;3017850]Hi all,
but when i issue "make"
afeter few lines complain about "linux/config.h" missing

This header file is deprecated. Simply remove the corresponding lines in the various source files. This worked for me.

---

### Post by superFerra on 2007-09-12
> **jfrieben said:**
> [QUOTE=superFerra;3017850]Hi all,
but when i issue "make"
afeter few lines complain about "linux/config.h" missing

This header file is deprecated. Simply remove the corresponding lines in the various source files. This worked for me.

I'm not as lucky as you. Can you send me that module compiled against the last kernel? (Is it possible?) Or help me to figure out my problem... ASAP i'll post my error logs...

TIA

---

### Post by superFerra on 2007-09-16
well
i did it! i had to download the svn version to compile it.
Now, How do i install it ??
tring "make test" what should happen??

Please help

---

### Post by amadeus266 on 2007-09-29
Anyone got this working yet? I have an AIW 9200 and liked being able to watch videos on my computer instead of having to compete with my 5 teenagers for time in front of the tv. I no longer have windows on this machine so obviously I would like it to work under Ubuntu (Gutsy)

---

