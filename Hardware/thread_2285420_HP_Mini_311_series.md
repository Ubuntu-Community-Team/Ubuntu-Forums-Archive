---
title: "HP Mini 311 series"
date: 2015-07-05
forum: Hardware
---

### Post by matthew82 on 2015-07-05
Hi all! My name is Matt. I currently own an HP Mini 311. I have icelord's bios hack h.15 flashed and currently OC to 2.3ghz. Pics or it didn't hppen, right?:p [[IMG]http://i1305.photobucket.com/albums/s551/92ninjas/HPMINIOC_zps8nzbj3wa.jpg[/IMG]]("http://s1305.photobucket.com/user/92ninjas/media/HPMINIOC_zps8nzbj3wa.jpg.html")

I have been doing some research on these machines. I would like to be able to utilize the full ION graphics. However, mine is stuck on ION LE. I compared the HP Mini 311 w/ LE and HP Mini w/ full ION. Only difference I have been able to decipher is the Full ION HP Mini 311 came from factory with win7 and came with 2gb RAM while the ION LE version only came with XP and 1 GB onboard. Both use the same bios. Both logic boards are identified as Board ID 3651. I'm not sure how to correct it. Most people who have stated their opinions about going full ION say it's not worth it. However, I believe it is. Especially w/ Ubuntu 14.04 LTS on here. I'm currently limited to playing 720p movies and the games I am able to play (Steam supported) could use the extra oomph. If Full ION were to be granted, I would be able to play 1080p flawlessly. That's enough for me to be interested in somehow trying to make the system recognize that it is Full ION Capable.

Pardon me if I posted this in the wrong section. Collaboration.... BEGIN!

---

### Post by Yellow Pasque on 2015-07-06
> If Full ION were to be granted, I would be able to play 1080p flawlessly.
The only difference is that ION LE doesn't support DirectX 10. "Upgrading" makes sense if you run Windows 7 (or later) and you want to play DX10 games, though adding DX10 won't help your video playback.
On Linux, DirectX games run in Wine are using OpenGL, so "upgrading" won't help you or give you some magic speed boost.

Check vdpauinfo to make sure VDPAU is setup properly:
```
sudo apt-get install vdpauinfo
vdpauinfo
```

---

### Post by matthew82 on 2015-07-06
> **Temüjin said:**
> The only difference is that ION LE doesn't support DirectX 10. "Upgrading" makes sense if you run Windows 7 (or later) and you want to play DX10 games, though adding DX10 won't help your video playback.
On Linux, DirectX games run in Wine are using OpenGL, so "upgrading" won't help you or give you some magic speed boost.

Check vdpauinfo to make sure VDPAU is setup properly:
```
sudo apt-get install vdpauinfo
vdpauinfo
```
here's what I got from vdpauinfo:

```
display: :0   screen: 0API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  331.113  Mon Dec  1 20:30:22 PST 2014


Video surface:


name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 


Decoder capabilities:


name               level macbs width height
-------------------------------------------
MPEG1                 0  8192  2048  2048
MPEG2_SIMPLE          3  8192  2048  2048
MPEG2_MAIN            3  8192  2048  2048
H264_MAIN            41  8190  2032  2048
H264_HIGH            41  8190  2032  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048


Output surface:


name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 


Bitmap surface:


name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192


Video mixer:


feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -


parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4


attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  



```

---

### Post by kerry_s on 2015-07-06
if you want some extra, running a lighter desktop would help. unity is probably sucking all kinds of extra resources.

---

### Post by matthew82 on 2015-07-07
> **kerry_s said:**
> if you want some extra, running a lighter desktop would help. unity is probably sucking all kinds of extra resources.
hmmm... interesting point. I have it split partitioned with Xubuntu. I hardly go to that one because some of the apps I use don't work on it but work on regular ubuntu. Any recommendations for a different/lighter DM?

---

### Post by kerry_s on 2015-07-07
> **matthew82 said:**
> hmmm... interesting point. I have it split partitioned with Xubuntu. I hardly go to that one because some of the apps I use don't work on it but work on regular ubuntu. Any recommendations for a different/lighter DM?

well if xubuntu don't do it, try ubuntu-mate.
strange apps should work across all de, unless it's made for just unity.

i use a hp-mini 210-1010nr currently using elementary, but normally i use ubuntu mate.
i taught a friend how to install, so i'm just keeping the os for awhile incase he calls with issues. plus he still has my usb drive. :)

---

### Post by matthew82 on 2015-07-11
> **kerry_s said:**
> well if xubuntu don't do it, try ubuntu-mate.
strange apps should work across all de, unless it's made for just unity.

i use a hp-mini 210-1010nr currently using elementary, but normally i use ubuntu mate.
i taught a friend how to install, so i'm just keeping the os for awhile incase he calls with issues. plus he still has my usb drive. :)
I'll have to experiment with a couple different OS variations. Also, I HAD lubuntu on here thinking it would run smoother then ubuntu. Needless to say lubuntu is no longer on here. I'll try usb booting them 1st and see how it goes.

Are there any other suggestions to be able to have my mini at least play 1080p flawlessly w/ VLC?

---

### Post by Yellow Pasque on 2015-07-11
The key is to use a video player with good support for VDPAU (like mpv). The Atom N270 is a pretty wussy CPU and is going to struggle to play HD video without assistance from the GPU.
If you insist on VLC, see this page for getting it to play using VDPAU: [http://www.remlab.net/op/vlc-vdpau.shtml](http://www.remlab.net/op/vlc-vdpau.shtml)
You can also try using a VDPAU wrapper if you don't want to use a PPA to upgrade to VLC 2.2.x:
```
sudo apt-get install vainfo vdpau-va-driver
vainfo  #make sure this prints a list of "Supported profile and entrypoints"
```

Also, I don't usually advocate throwing money at problems, but if you want to use this system with any sort of regularity, finding a cheap 1GB SO-DIMM module of DDR3-1066 or DDR3-1333 would probably be worthwhile.

---

### Post by kerry_s on 2015-07-11
> **matthew82 said:**
> I'll have to experiment with a couple different OS variations. Also, I HAD lubuntu on here thinking it would run smoother then ubuntu. Needless to say lubuntu is no longer on here. I'll try usb booting them 1st and see how it goes.

Are there any other suggestions to be able to have my mini at least play 1080p flawlessly w/ VLC?

these things weren't made for 1080p, stick to 720p local, 480p streaming, you'll be much happier & have to work less since your not trying to make it do more than it was built for.

---

### Post by matthew82 on 2015-07-11
> **Temüjin said:**
> The key is to use a video player with good support for VDPAU (like mpv). The Atom N270 is a pretty wussy CPU and is going to struggle to play HD video without assistance from the GPU.
If you insist on VLC, see this page for getting it to play using VDPAU: [http://www.remlab.net/op/vlc-vdpau.shtml](http://www.remlab.net/op/vlc-vdpau.shtml)
You can also try using a VDPAU wrapper if you don't want to use a PPA to upgrade to VLC 2.2.x:
```
sudo apt-get install vainfo vdpau-va-driver
vainfo  #make sure this prints a list of "Supported profile and entrypoints"
```

Also, I don't usually advocate throwing money at problems, but if you want to use this system with any sort of regularity, finding a cheap 1GB SO-DIMM module of DDR3-1066 or DDR3-1333 would probably be worthwhile.

At the time of this reply, I have not inputted that code yet. However, I did buy the 2gb SO-DIMM for the mini several months ago. I knew that it needed it. I did purchase it with the same frequency as the on-board RAM (1066mhz). I have my bios performance settings set to Unlinked capped at 1066mhz for the RAM. I'm not sure if I would even see/experience any benefit with getting the 1333mhz SO-DIMM. With the hacked bios, it did enable me to allocate up to 512mb RAM for graphics purposes. I'll try the code and report back.

[[IMG]http://i1305.photobucket.com/albums/s551/92ninjas/e81ce982-7e1a-4ee8-bd3b-d79c89bb2060_zpskifu7u9a.png[/IMG]]("http://s1305.photobucket.com/user/92ninjas/media/e81ce982-7e1a-4ee8-bd3b-d79c89bb2060_zpskifu7u9a.png.html")

Edit: I am not set on using strictly VLC for movie/video playback. I just use it the most b/c it has given me less problems than Parole and others.

vainfo provides me with the following:

```
~$ vainfolibva info: VA-API version 0.35.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/nvidia_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.35 (libva 1.3.0)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
```

---

### Post by matthew82 on 2015-07-15
Here's a screen shot of Inex on Xubuntu.
[[IMG]http://i1305.photobucket.com/albums/s551/92ninjas/Inexmemusagexubuntu_zpssoyjemg1.png[/IMG]](http://s1305.photobucket.com/user/92ninjas/media/Inexmemusagexubuntu_zpssoyjemg1.png.html)

I hopped on Xubuntu to see if it was still going to give me the fritz on cooperating. It prompted me to DL some updates, which I did. Rebooted. All seems going smoothly for now. The difference in the amount of processes is incredible to me between Ubuntu and Xubuntu. I may end up keeping Xubuntu 14.04 on here after all.

---

### Post by kerry_s on 2015-07-15
good for you. xubuntu is a worthy os for netbooks.
i'm using xubuntu 15.04 myself.

so you have any luck with your 1080p quest ?

you know the broadcom wireless is in additional drivers, no need to download. it's also in the installer iso, so if your running live you can still run additional drivers to activate your wireless.if you select third party during install it will install the drivers.

---

### Post by matthew82 on 2015-07-16
> **kerry_s said:**
> good for you. xubuntu is a worthy os for netbooks.
i'm using xubuntu 15.04 myself.

so you have any luck with your 1080p quest ?

you know the broadcom wireless is in additional drivers, no need to download. it's also in the installer iso, so if your running live you can still run additional drivers to activate your wireless.if you select third party during install it will install the drivers.

Still questing to have the 1080p movies play flawlessly. Once I find out what combination of settings and software works I will post it here.
I actually have had Xubuntu 14.02 LTS installed on the HDD way before I joined the forums. It just took me awhile to hop onto the forums with my issue(s).

Edit: The Proprietary Driver listed there has never worked for me. IDK why.

---

### Post by matthew82 on 2015-08-29
Found [this]("http://geeknizer.com/1080p-minimum-requirements/") on the interwebz. I'm not going to get 1080p out of this dinosaur. Though, the 720p plays excellent. It's a bit choppy in fast-action scenes. I think that's due to the monitor being limited to 60hz refresh rate.

Currently on the Ubuntu 14.04 LTS as of this post. I have to change some settings in the BIOS so that I won't loose my Wifi due to screen inactivity on the xubuntu partition. It's strange. I did follow some tips off of this page [here]("http://ubuntuforums.org/sites.google.com/site/easylinuxtipsproject/Home"). Specifically, [I cleaned up Ubuntu]("http://sites.google.com/site/easylinuxtipsproject/clean") then [made it speedy]("http://sites.google.com/site/easylinuxtipsproject/speed"). I only did a few of the tips listed in each one. They have helped made Ubuntu more efficient on this dinosaur. I actually enjoy being on this more than I do my laptop with Windows 7 on it. :biggrin: I now despise the machines @ work running Windows 7.

---

### Post by kerry_s on 2015-08-29
i been running full ubuntu for a few weeks now on my hp-mini 210
i just change a few things in compiz config & i'm good to go. i also have it full screen all apps larger than 25, that way small things like the calculator stay normal.

---

### Post by matthew82 on 2015-11-25
Dead Thread Revival! I have found a fix. Somewhat. It's a command line that someone posted on [AskUbuntu.com]("http://askubuntu.com/questions/53019/how-to-watch-videos-that-have-1080p-using-x264-video-codec-and-ac3-for-audio") . The command is
```
mplayer -vc ffh264vdpau -fs /path/to/your/file
```

and works beautifully! I'm able to watch 2 Guns 1080p.No choppiness, still frames, sluggish playback. All smooth as silk. I'm satisfied for now.

---

