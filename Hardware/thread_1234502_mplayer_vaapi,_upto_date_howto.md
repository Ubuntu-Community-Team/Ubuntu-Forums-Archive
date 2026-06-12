---
title: "mplayer vaapi, upto date howto?"
date: 2009-08-07
forum: Hardware
---

### Post by metalfan_ on 2009-08-07
Hi,

im looking for a howto that helps me compiling or installing mplayer-vaapi.
ive found some sites so far:

[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)
build script is outdated, needs update

[http://art.ubuntuforums.org/showthread.php?p=6630583](http://art.ubuntuforums.org/showthread.php?p=6630583)
post #224, dates back to january (poulsbo-driver-2d and 3d didnt seem to exist back then)

[https://launchpad.net/~fitpc2/+archive/ppa](https://launchpad.net/~fitpc2/+archive/ppa)
you cant even post bugs there, very nice.
ive mailed the maintainer of the mplayer-vaapi package with my mplayer start error (compilation worked)
apparently they tried to build mplayer-vaapi for lpia which didnt work and no other arch. if i read the arch information corretly.


the best part of it is that today after all my mplayer experiments (dont worry, only used aptitude to install things) started to say that -vo blaxyz is not supported. it starts with -vo x11 now, but without fullscreen support. and i dont have a clue why

so whats the latest in mplayer-vaapi, how did you get it working?


greets

---

### Post by metalfan_ on 2009-08-08
compiling the mplayer-svn shapshot from 2009-08-08 with this patch [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-latest.tar.bz2](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-latest.tar.bz2)
results in:

```

cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include     -c -o allcodecs.o allcodecs.c
allcodecs.c: In function 'avcodec_register_all':
allcodecs.c:57: error: 'CONFIG_H263_VAAPI_HWACCEL' undeclared (first use in this function)
allcodecs.c:57: error: (Each undeclared identifier is reported only once
allcodecs.c:57: error: for each function it appears in.)
allcodecs.c:58: error: 'CONFIG_H264_VAAPI_HWACCEL' undeclared (first use in this function)
allcodecs.c:59: error: 'CONFIG_MPEG2_VAAPI_HWACCEL' undeclared (first use in this function)
allcodecs.c:60: error: 'CONFIG_MPEG4_VAAPI_HWACCEL' undeclared (first use in this function)
allcodecs.c:61: error: 'CONFIG_VC1_VAAPI_HWACCEL' undeclared (first use in this function)
allcodecs.c:62: error: 'CONFIG_WMV3_VAAPI_HWACCEL' undeclared (first use in this function)
make[1]: *** [allcodecs.o] Error 1
make[1]: Leaving directory `/home/julius/mplayer-vaapi-20090616/mplayer-checkout-2009-08-08/libavcodec'
make: *** [libavcodec/libavcodec.a] Fehler 2

```

---

### Post by metalfan_ on 2009-08-10
Found an uptodate patch in the minimyth repository, the mplayer svn version they use copiles fine with it but starting it with:

mplayer -vo vaapi -va vaapi somefile.mkv

results in:

```

[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS) "German DTS 754kbps", -aid 0, -alang ger
[mkv] Track ID 3: audio (A_DTS) "English DTS 1509kbps", -aid 1, -alang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8) "German", -sid 0, -slang ger
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x816  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
libva: libva version 0.30.4-sds2
mplayer: dri1_util.c:110: isDRI1Connected: Assertion `dri_state->fd >= 0' failed.


MPlayer interrupted by signal 6 in module: preinit_libvo
- MPlayer crashed. This shouldn't happen.

```

---

### Post by dothedog on 2009-08-13
metalfan_
Did you ever get this working? I am very close but have some video corruption on playback. I get a black bar about 1/5 from the bottom of the screen that goes about half way across the screen. This happens with VC-1 and h264 video (haven't tried others) Here is what I am using:

I have a Kohjinsha SC3 with Atom z520 Proc and Poulsbo (GMA500) Graphics
```

dothedog@Kohji-SC3:~$ uname -a
Linux Kohji-SC3 2.6.28-14-lpia #47-Ubuntu SMP Fri Jul 24 22:10:52 UTC 2009 i686 GNU/Linux

```
Using ubuntu-mobile ppa for:
```
xserver-xorg-video-psb - X.Org X server -- Intel Poulsbo (2D)
psb-modules - Kernel module built for -generic or -lpia kernel
psb-firmware - Binary firmware for the Poulsbo (psb) 3D X11 driver
psb-kernel-source - Kernel module for the Poulsbo (psb) 2D X11 driver
psb-kernel-headers - Kernel module headers for the Poulsbo (psb) 2D X11 driver
xpsb-glx - X11 drivers for Poulsbo (psb) 3D acceleration
poulsbo-driver-3d - Metapackage for the 3D Poulsbo (psb) X11 driver.
poulsbo-driver-2d - Metapackage for the 2D Poulsbo (psb) X11 driver.

```
Libva is from [http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)
I am using version 
libva1_0.29-2+sds12_lpia.deb
libva-dev_0.29-2+sds12_lpia.deb

libva1_0.29-2+sds12_lpia.deb loaded just fine. However the -dev package needed to get the libdrm dependency fixed (Changed depends line in Control file from libdrm-dev to libdrm-poulsbo-dev) Also, the 0.30 versions had dependency conflicts with libdrm so I had to fall back to the 0.29 version.

I also needed to do a
```
sudo ln -s /usr/X11R6/lib/modules/dri/psb_drv_video.so /usr/lib/va/drivers/psb_drv_video.so
```
to get libva working. 

here is the output from vainfo:
```
dothedog@Kohji-SC3:~$ vainfo
libva: va_DRI_GetDriverName: 0.1.0 psb (screen 0)
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_DRI_GetDriverName: 0.1.0 psb (screen 0)
libva: va_openDriver() returns 0
vainfo: VA API version: 0.29
vainfo: Driver version: Intel GMA500 - 5.0.1.0046

```

for mplayer-vaapi I used the latest from here: [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-20090804.tar.bz2](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/mplayer-vaapi-20090804.tar.bz2)

Make sure you have all the dependencies (e.g. svn) then do a 
```
./checkout-patch-build.sh
```
It takes a while but mplayer-vaapi should build. Then play with
./mplayer -vo vaapi -va vaapi filename

Let me know if you get the black bar or if this is something that is peculiar to my setup.

DoTheDog

---

### Post by jbernardo on 2009-10-02
I used libva 0.31.0-1+sds4, following the instructions at [http://www.splitted-desktop.com/~gbeauchesne/libva/]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/"), ignoring the depends from the karmic libva1 and libva-dev, only installing the depends the dpkg-buildpackage asked for. I also had to build mplayer with "--extra-cflags=-fno-strict-aliasing" passed to configure, to work around gcc 4.4.1 problems. Anyway, I see no acceleration at all, trying to play the 720p trailer for "The usual suspects" on my Asus 1101HA running karmic. Dragon player or kaffeine do a better job of playing this file. :(

---

### Post by dothedog on 2009-11-21
jbernardo,
I had libva libva-dev and mplayer-vaapi all configured/compiled on Karmic, acceleration was working but mplayer would crash randomly after a minute or two of playback (different places e.g. decode audio, decode video, etc.) I used the .debs from splitted-desktop for libva (used latest) and compiled mplayer-vaapi with the script there. Even tried the latest sds8 I believe and it didn't help. I am now dropping back to Jaunty as it did work there. If you have any success please post here.

Dothedog

---

### Post by jbernardo on 2009-11-22
Hi, I didn't use the debs - I built the libva with the "dpkg-buildpackage -rfakeroot -uc -us" command, installing a extra dependency whenever that failed. Maybe that is the difference?

---

### Post by jurekiteresa on 2009-12-10
Hi

My netbook has Intel GMA500 (Poulsbo) chipset.
For HD video files I use mplayer-vaapi with full succes from:

[http://gwenole.beauchesne.info/en/blog/2008/12/24/mplayer_with_va_api_acceleration](http://gwenole.beauchesne.info/en/blog/2008/12/24/mplayer_with_va_api_acceleration)
[http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)
[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)

I try use mplayerplug-in and gecko-mediaplayer for video flash embeded on youtube and other pages by Greasemonkey addons for Firefox with some user scripts eg:

[http://userscripts.org/scripts/search?q=mplayer&sort=rating](http://userscripts.org/scripts/search?q=mplayer&sort=rating)

But unfortunatelly mplayerplug-in ,gecko-mediaplayer and gnome-mplayer don't use Vaapi.
I cannot use vaapi even thoe I type manual vaapi on each programs.

Is there any chance to compile or add Vaapi support atleast for
gecko-mediaplyer?

Please advice

Regards

Jurek

---

### Post by michael37 on 2009-12-23
Stay tuned...  it doesn't quite work right yet.

```

libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [H264]  1280x720  24bpp  29.970 fps  1806.7 kbps (220.5 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isomavc1mp42
libva: libva version 0.31.0-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1280x720 => 1280x720 H.264 VA API Acceleration 
[vo_vaapi] Could not set up subpicture palette
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 119.6 kbit/8.47% (ratio: 14948->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1280x720 => 1280x720 H.264 VA API Acceleration 
[vo_vaapi] Could not set up subpicture palette

```

---

### Post by jbernardo on 2009-12-27
By now, I've managed to build mplayer-vaapi in a couple of ways, but the easiest is to either follow the instructions by dothedog, or use the script from [http://kanotix.com/files/fix/mplayer-vaapi-latest.txt](http://kanotix.com/files/fix/mplayer-vaapi-latest.txt) - this last one builds a .deb package, but for me failed building libva, I had to install it first using dothedog's instructions. After that I reran the script, and I ended with a working mplayer with vaapi acceleration. I also had to do the linking of the driver, as the script doesn't do it:
```
sudo ln -s /usr/X11R6/lib/modules/dri/psb_drv_video.so /usr/lib/va/drivers/psb_drv_video.so
```

Right now my remaining problem is subtitles. If I try to use A S S, no subtitles are displayed. If I don't use A S S, mplayer crashes, usually as soon as it finds the first subtitle.
Anyone been able to do any better?

---

### Post by michael37 on 2009-12-27
@jbernardo: which libva1 are you currently using?  Gbeauchesne says [here]("http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/") that libva1 should be 0.31.0 or greater.  DoTheDog instructions end up with libva1 version 0.29.

Granted, if you can build mplayer from source with new libva, then you can simply install binary package from [http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/](http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/)

---

### Post by jbernardo on 2009-12-27
I'm using 0.31.0 sds9 (the latest one). Gbeauchesne's script will work only with a 0.31.0 or later version, and the kanotix script just automates the whole process.

BTW, to fix the building of libva with the kanotix script, I just had to comment the sed line that re-enables i965. Without that line it builds.

---

### Post by michael37 on 2009-12-28
> **jbernardo said:**
> I'm using 0.31.0 sds9 (the latest one). Gbeauchesne's script will work only with a 0.31.0 or later version, and the kanotix script just automates the whole process.

BTW, to fix the building of libva with the kanotix script, I just had to comment the sed line that re-enables i965. Without that line it builds.

I fixed this line in kanotix script, and got libva to build (on lpia, btw).  Then, I found out that I needed a few more packages:
libgtk2.0-dev libpng12-dev zlib1g-dev libxinerama-dev libxv-dev
to build mplayer.

After that, the build worked.  However, mplayer is not in good shape.  It can play flv files, but it can't play H264.  It only knows how to use oss audio output device.

[h264 @ 0x89dcae0]get_buffer() failed (-1 0 0 (nil))
[h264 @ 0x89dcae0]decode_slice_header error
[h264 @ 0x89dcae0]no frame!

---

### Post by jbernardo on 2009-12-28
Strange, maybe that is because I had already built it by hand a few times and had the dependencies installed. I know that I built x264 from source and installed it, let me see if I have the time today to incorporate into the script and post the final version here.

As for the rest, if you do a "sudo apt-get build-dep mplayer" it should install everything you need. But since it is already in the script, something isn't right. You can always check your configure.log in /tmp/vaapi/mplayer-vaapi-20091221/mplayer-vaapi/ to check what was missing and why some codecs weren't built.

---

### Post by michael37 on 2009-12-28
> **jbernardo said:**
> Strange, maybe that is because I had already built it by hand a few times and had the dependencies installed. I know that I built x264 from source and installed it, let me see if I have the time today to incorporate into the script and post the final version here.

As for the rest, if you do a "sudo apt-get build-dep mplayer" it should install everything you need. But since it is already in the script, something isn't right. You can always check your configure.log in /tmp/vaapi/mplayer-vaapi-20091221/mplayer-vaapi/ to check what was missing and why some codecs weren't built.

I am guessing that alsa, etc are optional outputs and that's why mplayer may not have it in build dependencies.  Just a guess.  

Mplayer auto-detects installed libraries during configure. Here are packages that provide libraries that mplayer was looking for:
libpulse-dev
libasound2-dev
libesd0-dev
libsdl1.2-dev
libjack-dev

These had to be installed manually. 

Btw, my h264 decoding is still not working.  Any idea why?

---

### Post by jbernardo on 2010-01-17
> **michael37 said:**
> Btw, my h264 decoding is still not working.  Any idea why?

Have you been able to advance with this?

---

### Post by michael37 on 2010-01-17
> **jbernardo said:**
> Have you been able to advance with this?

Nope, I am using lucazade's binary build.  See his **non-PPA** script @ [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/).  I have no idea whether he built the package himself or found it somewhere.

---

### Post by jbernardo on 2010-01-18
I've tried his package also, but it shows the same problem with subtitles... :(

---

### Post by michael37 on 2010-01-23
Just curious, is there mencoder or any video encoding software that supports hardware acceleration like vaapi/vdpau/cuda/etc?

I have two computers with Atom, one with GMA 500 and another with Ion, that can't really handle encoding on CPUs.

EDIT: After extensive google searches, I found [this software]("http://www.badaboomit.com/") for Windows that supports Nvidia.

---

### Post by highlandsun on 2010-02-26
Out of curiosity, anyone still investigating this? I have it working with my Nvidia FX770 but it doesn't scale well. I.e., I have a 720x400 H264 FLV video which plays fine at 1:1 resolution. But if I try to use mplayer -fs (fullscreen, 1920x1200) the video lags the audio. If I don't use VAAPI, it will use ~40% of my CPU but with Xvideo it will play at any size without any speed issues.

---

### Post by highlandsun on 2010-02-26
Ah, using -vo xv -va vaapi works much better than -vo vaapi -va vaapi.

---

### Post by michael37 on 2010-03-01
> **highlandsun said:**
> Ah, using -vo xv -va vaapi works much better than -vo vaapi -va vaapi.

-vo vaapi works horribly with compiz.  I suspect WM is at fault, not mplayer.  It works perfectly with metacity, both in window or full-screen.

---

### Post by sol1tude on 2010-03-05
I have some flickering in some .mp4 hd videos. Compiz is disabled. How can I fix it? 
ps: im using vaapi with mplayer:
mplayer -fs -vo vaapi -va vaapi video.mp4

pps: i tried using built-in deinterlacers but video begins to lag

---

### Post by jbernardo on 2010-03-11
I just cleaned up my karmic lpia (removed all under /usr/local/lib and include, removed most "non-essential" packages, etc.), and rebuilt mplayer-vaapi using[ kanotix script]("http://www.kanotix.com/files/fix/mplayer-vaapi-latest-1.txt"). As it finally works with most subtitles, even As.S. works, I decided to try building with atom optimizations - changed the last debuild to:
```
DEB_BUILD_OPTIONS="--extra-cflags='-fno-strict-aliasing -march=core2 -mtune=pentium -mfpmath=sse'" time debuild -i -us -uc -b

```And finally, flicker free FULL-HD! With subtitles!

---

### Post by sol1tude on 2010-03-11
> **jbernardo said:**
> I just cleaned up my karmic lpia (removed all under /usr/local/lib and include, removed most "non-essential" packages, etc.), and rebuilt mplayer-vaapi using[ kanotix script]("http://www.kanotix.com/files/fix/mplayer-vaapi-latest-1.txt"). As it finally works with most subtitles, even As.S. works, I decided to try building with atom optimizations - changed the last debuild to:
```
DEB_BUILD_OPTIONS="--extra-cflags='-fno-strict-aliasing -march=core2 -mtune=pentium -mfpmath=sse'" time debuild -i -us -uc -b

```And finally, flicker free FULL-HD! With subtitles!

can you say more information about your tests and system? like what video container [.mkv, .mp4, ..], video frame and your display resolution, your notebook model & ram & cpu, kernel and psb driver version.
thanks a lot.

---

### Post by jbernardo on 2010-03-11
> **sol1tude said:**
> can you say more information about your tests and system? like what video container [.mkv, .mp4, ..], video frame and your display resolution, your notebook model & ram & cpu, kernel and psb driver version.
thanks a lot.

I've tried this with a few files mkv containers. For FullHD (1920x1280), I tried with a film - 23.975fps. For HD ready (720p), I tried a couple of films, at 23.975 fps, and a tv series, at 25fps. 
My notebook is a Asus 1101HA, Z520@1.33GHz, 2GB ram. The kernel is 2.6.31-20 lpia, the psb driver is the one Lucazade makes available, 2.2.0.32L.0041 from Xorg.0.log.

---

### Post by michael37 on 2010-03-11
> **jbernardo said:**
> I've tried this with a few files mkv containers. For FullHD (1920x1280), I tried with a film - 23.975fps. For HD ready (720p), I tried a couple of films, at 23.975 fps, and a tv series, at 25fps. 
My notebook is a Asus 1101HA, Z520@1.33GHz, 2GB ram. The kernel is 2.6.31-20 lpia, the psb driver is the one Lucazade makes available, 2.2.0.32L.0041 from Xorg.0.log.

This is great news.  I wonder if you can create a .deb.  That'd surely make it easier for everyone.

P.S. I decided to switch from lpia to i386 due to lack of future support.  It's sad, but lpia is not coming to Lucid...

---

### Post by sol1tude on 2010-03-11
> **michael37 said:**
> This is great news.  I wonder if you can create a .deb.  That'd surely make it easier for everyone.

P.S. I decided to switch from lpia to i386 due to lack of future support.  It's sad, but lpia is not coming to Lucid...
yep, i agree. if someone could build a deb..
btw: im using mplayer with vaapi from script placed [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/")
works very stable: .mp4 and .mov work perfectly with HD and FullHD BUT .mkv container does flickering.
so i hope [jbernardo]("http://ubuntuforums.org/member.php?u=116996") can build patched mplayer to us.

---

### Post by jbernardo on 2010-03-12
The script I pointed to creates the debs. That said, I have the ones I build for me, and of the x264 I also updated, so just tell me where to upload them I'll do it. I make no warranties, probably won't be able to update them frequently, and they are for lpia - since the transition to Lucid is still impossible, I see no reason to spend 10% more battery and to have a 10% slower computer.

But you can have them if you want, just tell me where to upload.

---

### Post by mnbv on 2010-03-12
Trying to use mplayer-vaapi-latest on amd64 platform, 
the build fails with the below:

fmt-conversion.c:102: error: 'PIX_FMT_VDPAU' undeclared here (not in a function)
make[1]: *** [fmt-conversion.o] Error 1
make[1]: *** Waiting for unfinished jobs....
make[1]: Leaving directory `/tmp/vaapi/mplayer-vaapi-20100224/mplayer-vaapi'


Any idea? Did someone else get this message?

---

### Post by neltnerb on 2010-05-10
FYI

[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia]("https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia")

I used this repository, installed mplayer, and it works out of the box for playing with vaapi acceleration. I am using the GMA4500 on an Asus UL30A-x5. I changed .mplayer/config to say:

> 
vo=xv
va=vaapi


so that mplayer automatically uses accelerated playback.

Purportedly it also works with vlc, but I didn't see it list vaapi as an option in the video preferences menu so I gave up. I've always liked mplayer better since it doesn't have the unnecessary and designed GUI anyway, so I didn't really care.

I am able to watch 1080p on my UL30A-x5 netbook (U7300 1.3GHz ultra low voltage core 2 duo) with 80-90% of the CPU with no flickering and smooth video. Without the acceleration, audio and video rapidly went out of sync, and with framedrop the motion was just barely watcheable, occasionally freezing for several seconds at a time. During playback with full screen brightness, the power consumption went up to 15W according to powertop.

Cheers,
Brian

---

### Post by baleks on 2010-05-10
neltnerb: thanks for the link!
Unfortunately, on CULV-processor system with 2-core seleron su2300 1.2Ghz (acer 1410) 1080p still not watchable (same sympthoms) :(

Experimenting with mplayer options, with mplayer -va vaapi -vo vaapi i got segmentation fault
mplayer -va xv -vo vaapi don't changes nothing but output lines of mplayer on console

---

### Post by michael37 on 2010-05-10
> **baleks said:**
> neltnerb: thanks for the link!
Unfortunately, on CULV-processor system with 2-core seleron su2300 1.2Ghz (acer 1410) 1080p still not watchable (same sympthoms) :(

Experimenting with mplayer options, with mplayer -va vaapi -vo vaapi i got segmentation fault
mplayer -va xv -vo vaapi don't changes nothing but output lines of mplayer on console


It's -vo xv -va vaapi.

vo = video output (to xv)
va = video acceleration (via vaapi)

I assume your vainfo command produces meaningful results.

---

### Post by baleks on 2010-05-11
```
baleks@BAleks-netbook:~$ vainfo 
libva: libva version 0.31.0-sds6
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: i965 Driver 0.1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD

```

I assume this means that my vaapi backend supports only MPEG2 decoding on my intel 4500MHD GPU unit, so H264 and other codecs still use my CPU :(

---

### Post by neltnerb on 2010-05-11
> libva: libva version 0.31.0-sds6
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: i965 Driver 0.1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD

Mine says the same thing. Perhaps I was overzealous in thinking it worked, but my x264 video decoding *did* go from very obviously chopping and skipping to smooth. Maybe something else changed (for instance, perhaps just having a more current version of mplayer improved the performance enough to make it work). I am also using the GMA4500 with a ULVC processor, but now when I decode the video I see 70-90% CPU utilization (as opposed to 100%). I deemed this to perhaps just be the result of a poor decoding implementation, but perhaps the improvement was instead the result of an excellent mplayer implementation.

---

### Post by michael37 on 2010-05-11
> **neltnerb said:**
> Mine says the same thing. Perhaps I was overzealous in thinking it worked, but my x264 video decoding *did* go from very obviously chopping and skipping to smooth. Maybe something else changed (for instance, perhaps just having a more current version of mplayer improved the performance enough to make it work). I am also using the GMA4500 with a ULVC processor, but now when I decode the video I see 70-90% CPU utilization (as opposed to 100%). I deemed this to perhaps just be the result of a poor decoding implementation, but perhaps the improvement was instead the result of an excellent mplayer implementation.

[s]Indeed, your chipset does not support hardware acceleration for H264.  [/s] corrected in later posts.

For me, vaapi works for Nvidia Ion and for Intel GMA500.

---

### Post by neltnerb on 2010-05-11
Sorry, I meant to say that I have a GMA 4500MHD. According to wikipedia, this chipset *does* support full AVC hardware decoding. Apologies for the confusion.

---

### Post by baleks on 2010-05-12
Confirm, according to [http://en.wikipedia.org/wiki/Intel_GMA#Specifications](http://en.wikipedia.org/wiki/Intel_GMA#Specifications)
GMA 4500MHD suppor full avc acceleration.

Va-Api page [http://www.freedesktop.org/wiki/Software/vaapi](http://www.freedesktop.org/wiki/Software/vaapi) says that (section News):
**Mar 26'10 -- Add H.264 decoding to Intel Ironlake (HD Graphics) platforms (libVA i965_h264 branch)**
what does it means? how to use it ?

found alone message in its mailinglist [http://lists.freedesktop.org/archives/libva/2010-March/000217.html](http://lists.freedesktop.org/archives/libva/2010-March/000217.html) asking this question (probably novice). But it was before mar 26.

---

### Post by michael37 on 2010-05-31
> **baleks said:**
> Va-Api page [http://www.freedesktop.org/wiki/Software/vaapi](http://www.freedesktop.org/wiki/Software/vaapi) says that (section News):
**Mar 26'10 -- Add H.264 decoding to Intel Ironlake (HD Graphics) platforms (libVA i965_h264 branch)**
what does it means? how to use it ?


The H264 support for Intel® HD Graphics was released on May 11th.  All sources are [here]("http://intellinuxgraphics.org/"), not sure if anyone tried building binaries of these new packages.  You probably also need xorg intel driver 2.11.0 from April release.

---

### Post by michael37 on 2010-05-31
> **michael37 said:**
> The H264 support for Intel® HD Graphics was released on May 11th.  All sources are [here]("http://intellinuxgraphics.org/"), not sure if anyone tried building binaries of these new packages.  You probably also need xorg intel driver 2.11.0 from April release.

And I stand to correct myself yet again!!! 

Here are the binary packages for Intel HD aka ironlake.

[http://www.splitted-desktop.com/~gbeauchesne/libva/ironlake.patches/]("http://www.splitted-desktop.com/~gbeauchesne/libva/ironlake.patches/")

---

### Post by jamsen on 2010-06-01
Hello,

I have been trying to setup my dell mini 12 to run mplayer vaapi for a few days now. Currently I am running 10.04 and have installed vaapi and built mplayer. I am getting problems when I try to watch a video, here is my output:
```
root@localhost:~$ ./mpvaapi -fs -vo vaapi -va vaapi tbu.mp4
MPlayer SVN-r31027-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tbu.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  1920x816  24bpp  23.976 fps  7403.5 kbps (903.8 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isomavc1
libva: libva version 0.31.0-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 94.8 kbit/6.17% (ratio: 11845->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Movie-Aspect is undefined - no prescaling applied.
VO: [vaapi] 1920x816 => 1920x816 H.264 VA API Acceleration  [fs]
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
A:   0.3 V:   0.0 A-V:  0.341 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 

```

When I quit mplayer I get this error:
```
MPlayer interrupted by signal 2 in module: flip_page
```

vainfo produces the following:
```
libva: libva version 0.31.0-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Intel GMA500 - 5.0.1.0046
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointMoComp
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

Is there anything obviously wrong? I have had this working with 9.10 a week or so ago.

Thanks.

---

### Post by michael37 on 2010-06-01
> **jamsen said:**
> Hello,

I have been trying to setup my dell mini 12 to run mplayer vaapi for a few days now. Currently I am running 10.04 and have installed vaapi and built mplayer. I am getting problems when I try to watch a video, here is my output:

Is there anything obviously wrong? I have had this working with 9.10 a week or so ago.

Thanks.

Yep, you are running 10.04.  Look at the table on the link [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by jamsen on 2010-06-02
> **michael37 said:**
> Yep, you are running 10.04.  Look at the table on the link [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Thanks, I was unaware that was the case. I have had this running with 9.10 previously but for the life of me cannot get it working again. Can you point me towards an up to date guide on setting this up? Cheers.

---

### Post by michael37 on 2010-06-02
> **jamsen said:**
> Thanks, I was unaware that was the case. I have had this running with 9.10 previously but for the life of me cannot get it working again. Can you point me towards an up to date guide on setting this up? Cheers.

The wiki link I gave you is up to date.  Isn't it clear on line #1 that vaapi in 10.04 is broken?  Regression from 9.10, caused by a new version of Xorg.

---

### Post by ashfame on 2010-06-07
> **michael37 said:**
> The wiki link I gave you is up to date.  Isn't it clear on line #1 that vaapi in 10.04 is broken?  Regression from 9.10, caused by a new version of Xorg.

Any idea by when it will be fixed?

---

### Post by hubus on 2010-06-14
> **ashfame said:**
> Any idea by when it will be fixed?

It's fixed. You have to use ppa/fix repository and vaapi will work. Additional information can be found here:
[http://ubuntuforums.org/showthread.php?t=1229345&page=109](http://ubuntuforums.org/showthread.php?t=1229345&page=109)

---

### Post by SuperMaximus on 2011-03-13
Guys, I've tried to install mplayer-vaapi on my Vaio P31ZRK (ubuntu 10.10) several times.
Last 2 times with help of script from site.

That's what I get when I launch mplayer with VAAPI VO:

max@max-vaio: mplayer -vo vaapi:gl -va vaapi japan1080.mov
MPlayer SVN-r32819-4.4.5 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing japan1080.mov.
libavformat file format detected.
[lavf] stream 0: audio (aac), -aid 0, -alang eng
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  1920x1072  24bpp  30.000 fps  9831.6 kbps (1200.1 kbyte/s)
Clip info:
 major_brand: qt  
 minor_version: 537199360
 compatible_brands: qt  
 creation_time: 2006-07-17 17:45:22
 title-eng: BBC Motion Gallery
 comment: [http://www.bbcmotiongallery.com/](http://www.bbcmotiongallery.com/)
 copyright: ©2006 BBC
 copyright-eng: ©2006 BBC
 title: BBC Motion Gallery
 comment-eng: [http://www.bbcmotiongallery.com/](http://www.bbcmotiongallery.com/)
Load subtitles in ./
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 160.2 kbit/11.35% (ratio: 20019->176400)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   6.7 (06.7) of 254.0 (04:13.9)  1.0% 

Audio is playing, video - not. When I launch -vo vaapi:xv, it plays OK, but without acceleration. Already sick'n'tired of installing mplayer-vaapi with no success.
Please help...

---

### Post by davuvnik on 2011-11-08
Hello everyone, I'm trying to find out if anyone knows about an error  related to vaapi subtitles, I've been playing some files, and some of  them work fine using vaapi but some don't, i believe this is an old  issue but i haven't found any solution, however I recently discovered  that vaapi actually works  and with some subtitles.
(I previously  used the -vo xv -va vaapi command but this isn't vaapi because it  stresses the CPU and I could barely see full 720p movies).

I have an ACER ONE 751H
Fresh Ubuntu 10.04 install, updated with latest kernel 2.6.32-35.78
psb driver ppa:gma500/ppa

i downloaded the default smplayer that comes with the driver.

this are the options I use:

Video output: vaapi
Audio: use software equalizer, global volume, user software control 110
allow framedrop and hard frame drop (both disabled)

Threads for decoding 2
H.264
loop filter enabled (I found out that if it is turned off, the few subtitles that did work, stop working at all)

Freetype suport enabled (if disabled also smplayer brakes down, with vaapi)
Use SSA/*** Library enabled
No extra options for mplayer

that's it, I should point out that the OSD controls look messed up while  playing vids but the subtitles work fine. while others at the time a  sub needs to be shown, this error comes out:
smplayer log:
/usr/bin/mplayer  -noquiet -nofs -nomouseinput -lavdopts threads=2 -sub-fuzziness 1  -identify -slave -vo vaapi -ao alsa -nokeepaspect -nodr -double  -stop-xscreensaver -*** -embeddedfonts -***-line-spacing 0  -***-font-scale 1 -***-styles /home/david/.config/smplayer/styles.***  -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20  -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -subpos 100 -volume 100  -nocache -ss 1013 -osdlevel  -slices -channels 2 -af  scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110  /media/FILES/Video/Movies/movie.mp4

MPlayer 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/FILES/Video/Movies/movie.mp4.
libavformat file format detected.
ID_VIDEO_ID=0
[lavf] stream 0: video (h264), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=und
[lavf] stream 1: audio (aac), -aid 0, -alang und
ID_SUBTITLE_ID=0
ID_SID_0_LANG=und
[lavf] stream 2: subtitle (unknown), -sid 0, -slang und
VIDEO:  [H264]  1280x536  24bpp  23.976 fps  1297.6 kbps (158.4 kbyte/s)
Clip info:
 major_brand: isom
ID_CLIP_INFO_NAME0=major_brand
ID_CLIP_INFO_VALUE0=isom
 minor_version: 1
ID_CLIP_INFO_NAME1=minor_version
ID_CLIP_INFO_VALUE1=1
 compatible_brands: isomavc1
ID_CLIP_INFO_NAME2=compatible_brands
ID_CLIP_INFO_VALUE2=isomavc1
 title: Super 8
ID_CLIP_INFO_NAME3=title
ID_CLIP_INFO_VALUE3=movie
 date: 2011
ID_CLIP_INFO_NAME4=date
ID_CLIP_INFO_VALUE4=2011
 genre: SciFi
ID_CLIP_INFO_NAME5=genre
ID_CLIP_INFO_VALUE5=SciFi
 comment: Tagged by h264enc 9.3.7 on dom oct 30 05:28:01 COT 2011
ID_CLIP_INFO_NAME6=comment
ID_CLIP_INFO_VALUE6=Tagged by h264enc 9.3.7 on dom oct 30 05:28:01 COT 2011
ID_CLIP_INFO_N=7
ID_FILE_SUB_ID=0
ID_FILE_SUB_FILENAME=/media/FILES/Video/Movies/Super 8/Super 8 720p.srt
SUB: Added subtitle file (1): /media/FILES/Video/Movies/movie.srt
ID_FILENAME=/media/FILES/Video/Movies/movie.mp4
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=H264
ID_VIDEO_BITRATE=1297608
ID_VIDEO_WIDTH=1280
ID_VIDEO_HEIGHT=536
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=2.3881
ID_AUDIO_FORMAT=MP4A
ID_AUDIO_BITRATE=112488
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_START_TIME=0.02
ID_LENGTH=6708.78
ID_SEEKABLE=1
ID_CHAPTERS=0
libva: libva version 0.31.0-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/psb_drv_video.so
libva: va_openDriver() returns 0
Opening video filter: [scale]
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
ID_VIDEO_CODEC=ffh264
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 112.5 kbit/7.32% (ratio: 14061->192000)
ID_AUDIO_BITRATE=112488
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=faad
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Movie-Aspect is 2.39:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=2.3881
VO: [vaapi] 1280x536 => 1280x536 H.264 VA-API Acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[h264 @ 0x1470f80]Cannot parallelize deblocking type 1, decoding such frames in sequential order
[***] PlayResX undefined, setting to 384
[***] fontconfig: Selected font is not the requested one: 'Liberation Sans' != 'Arial'


MPlayer interrupted by signal 11 in module: filter video
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

CONCLUSION:
I have a few theories about why it doesn't work
1)the size of the subs (not likely but happened with my nokia n8)
2)character encoding (this might affect showing them or not, but not giving an actual error, I'm guessing)
3)overlaped subtitles (as i write this post i noticed that some subtitles overlap)

if anyone knows the problem or has been trying some other things please tell.
sorry for the long post!!!

:lolflag:

---

