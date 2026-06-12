---
title: "Skype crash when I start my webcam"
date: 2008-09-09
forum: General Help
---

### Post by dimitarc on 2008-09-09
If I try to start my webcam in a call or if I try to press the test button in skype options it crashes. Just skype. After opening it again I it works fine until I do the same thing. 

After opening skype in terminal this is what I get when I press the test button in Video Options:

```
Skype V4L: Failed to set picture format
Skype V4L: Could not find a suitable capture format
Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 84
Aborted

```

After searching some forums I found other people with the same problem but they fixed it with installing skype-static from medibuntu. I did the same, it did not help. I steel have the same problem.

I tried searching this forum for a solution for my problem but I did not found one. I hope someone will help me and I hope I did not missed the category for this thread. 

All the best, Dimitar

---

### Post by CyberCowboy on 2008-11-24
> **dimitarc said:**
> If I try to start my webcam in a call or if I try to press the test button in skype options it crashes. Just skype. After opening it again I it works fine until I do the same thing. 

After opening skype in terminal this is what I get when I press the test button in Video Options:

```
Skype V4L: Failed to set picture format
Skype V4L: Could not find a suitable capture format
Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 84
Aborted

```

After searching some forums I found other people with the same problem but they fixed it with installing skype-static from medibuntu. I did the same, it did not help. I steel have the same problem.

I tried searching this forum for a solution for my problem but I did not found one. I hope someone will help me and I hope I did not missed the category for this thread. 

All the best, Dimitar

Confirmed as I'm getting the exact same problems in Intrepid, were you able to fix it?

---

### Post by AmyRose on 2008-11-24
In Intrepid, to fix this problem, I installed the **libv4l-0** package and preload it with Skype like this:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by PouncingAnt on 2008-12-04
Thanks! That advice was spot on for me!

---

### Post by sparks40 on 2008-12-04
Is the following an environment variable and if so where does it get set, (i.e. the .profile file, etc.)?

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

TNX

---

### Post by bradosav on 2008-12-05
Guys, I'd really appreciate some help. Thanks.

**The problem:**
   I've been trying to get my camera work in skype for a few weeks now. If i click on test or start my video, the program   crashes.

**The solution:**
   [http://mrk.sed.pl/node/22](http://mrk.sed.pl/node/22) has a script that routes a gstreamer stream as a fake webcam into skype, appropriately called skype video hijacker. this is the script: 

#!/bin/bash
#
# setup gstfakevideo preload to hijack calls made
# to /dev/video0
#
#This script runs Skype with libskype_dsp_hijacker.so "filter"
#It allows redefining of what devices Skype uses for 
#microphone, speakers and mixer (especially microphone and
#speakers can use different devices)

# -- CONFIGURATION --

#default configuration when no option is specified

export HIJACKVIDEO="/dev/video0"
export GST_PIPE="videotestsrc is-live=true ! video/x-raw-yuv,width=640,height=480,framerate=10/1 ! videoscale ! ffmpegcolorspace ! vertigotv ! ffmpegcolorspace"

function help {
cat <<EOT

Redirect Skype video to gstreamer pipeline

Usage: $0 [pipeline definition, gst-launch syntax]

Edit the script for full flexibility

EOT
}
  

case "$1" in 
  -h|--help) help; exit;;
# broken
  --video) 
    export HIJACKVIDEO="$2"
    shift
    shift
    ;;
esac

export GST_PIPE="$*"

test -n "$GST_PIPE" || unset GST_PIPE

prefix=/usr/local
exec_prefix=${prefix}

#prefer use of libskype_dsp_hijacker from current directory
if test -f ./libgstfakevideo.so; then 
  libdir=.
else
  libdir=${exec_prefix}/lib
fi

LD_PRELOAD=${libdir}/libgstfakevideo.so
if test -f /lib/libdl.so.2; then
    LD_PRELOAD=$LD_PRELOAD:/lib/libdl.so.2
fi
export LD_PRELOAD

# ! video/x-raw-yuv,width=320,height=240,format=(fourcc)YV12 ! identity"
# invoke the program with the args given

exec skype



**The problem with the solution:**

   The author is very brief on the instructions and i don't have the knowledge to supplement. Skype doesn't crash, but instead displays a test image: vertical colored bars and a snowy field. When I run the script from the terminal, output is this:

$ ./gstfakevideo 
gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=800e7606 nr 6
gst.c shim_ioctl (236): VIDIOCGPICT
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=400e7607 nr 7
gst.c shim_ioctl (243): VIDIOCSPICT depth:24, colorspace:15
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80207609 nr 9
gst.c shim_ioctl (255): VIDIOCGWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=4020760a nr 10
gst.c shim_ioctl (259): VIDIOCSWIN
gst.c shim_ioctl (313): result=0 error=0 Success

Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 84


**What I have:**
   The webcam works very well in ekiga using a v4l2 plugin.
   My hardware drivers app shows GSPCA ZC03xx/VC3xx USB Camera Driver enabled and in use.

**My system**
  Ubuntu 8.04 running a 2.6.24-21-generic kernel
  Skype version 2.0.0.72
   The newest available UVC driver pack installed a few days ago from [http://linuxtv.org/hg/~pinchartl/uvcvideo/file/0280330fd4a0]("http://linuxtv.org/hg/%7Epinchartl/uvcvideo/file/0280330fd4a0")




could someone please help?!?

Thanks

P.S.
I installed libv4l to try one of the suggestions above. i guess the v4l1compat.so resides in /usr/local/lib/libv4l on 8.04, but camera doesn't work, even with that path. the output:
$ env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

---

### Post by SGAZ on 2009-01-20
> **AmyRose said:**
> In Intrepid, to fix this problem, I installed the **libv4l-0** package and preload it with Skype like this:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Thanks AmyRose!  Creative Webcam NX and Skype worked under 8.04 but totally failed under 8.10.  This solution fixed it right up!

---

### Post by ftmichael on 2009-03-06
> **AmyRose said:**
> In Intrepid, to fix this problem, I installed the **libv4l-0** package and preload it with Skype like this:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

This worked beautifully for me too, with my Logitech QuickCam Chat.  I edited the entry in my Applications menu so it runs that command instead of just **skype** when I click it.  Thanks so much!

---

### Post by sandy8925 on 2009-03-07
Thanks a lot man! I was having the same problem with Skype video and this fixed it.

---

### Post by MockY on 2009-04-23
Thanksk, 
this was unfortunately needed in Jauty as well.
However, this fixed the problem with the vertical green lines. Now I hope it fixed the crashing issues as well.

---

### Post by cas118 on 2009-04-24
Using the env command in Jaunty is having no joy for me.

Shame.

I get the following
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
ALSA lib ../../../src/pcm/pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib32/alsa-lib/libasound_module_pcm_bluetooth.so
Skype V4L: Failed to set picture size (320x240)
Skype V4L: Failed to set picture size (324x248)
Skype V4L: Failed to set picture size (352x288)
Skype V4L: Failed to set picture size (160x120)
Skype V4L: Failed to set picture size (176x144)
Skype V4L: Failed to set picture size (640x480)
Skype V4L: Failed to set picture size (1024x576)
Skype V4L: Failed to find suitable capture size for 320x240
Skype V4L: Could not find a suitable capture format
Starting the process...
Skype Xv: Xv ports available: 31
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 281
Aborted

```

---

### Post by Neville Grech on 2009-04-25
Same thing exactly is happening to me when I upgraded to Jaunty...

---

### Post by cool_penguin on 2009-05-03
Bravo !! Thank you so much. Editing the entry for Skype in the main menu from "skype" to "env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" did the trick.

I can now use my Logitech QuickCam Deluxe for notebook perfectly well with skype. 

Have a great day.

Cheers,
Harish

---

### Post by cool_penguin on 2009-05-03
Oops !! Forgot to mention that I did this on a fresh install of Jaunty.

---

### Post by e.m.fields on 2009-06-04
Hey guys - for those of us using this solution on** ***64-bit Skype*****: 

The solution here -> [http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/]("http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/") worked for me: 
> Note: I am using 64-bit Ubuntu so I installed the skype package from here.
I was getting the following error when launching skype

    ERROR: ld.so: object ‘/usr/lib/libv4l/v4l1compat.so’ from LD_PRELOAD cannot be preloaded: ignored. 

and had to install the 32-bit v4l libraries.

    sudo apt-get install lib32v4l-0 

As a result I had to modify /usr/local/bin/skype to reflect this. So rather than

    LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 

I had

    LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype 

Hopefully this will provide some solutions. 

**On that subject - I'm thinking we need a more organized / centralized system for getting [B]* Solutions *** filtered of this chaotic jungle of forum posts into a format easier to sift through. [/B]

Realistically - every problem we solve isn't going to end up in the wiki.

**I think this is the #1 thing holding ubuntu/linux back** - the ease & speed with which the community can solve problems and then disseminate that information. If every time I have a problem I have to sift through 2 hours of webforums, something could be made more efficient.

Open call for criticism / responses?
- fields

---

### Post by alexandre_bastien on 2009-11-18
Thanks for the hint with skype 64 bits. It worked for me. I'm using an old VIJE Talk Webcam from SavitMicro. It is recognized as a Z-Star Microelectronics Corp. ZC0302 Webcam. I'm using Ubuntu 9.10 64 bits.

By the way I agree so much with you. I really think that we should develop something that would be inbetween bug report and the wiki. Maybe a centralized place where we could find proved workaround for particular systems. For myself, I keep a detailed procedure of every workaround that worked properly for me since I started using Linux (6 years ago). But, there's no where for me to post these. They are not general enough to go on the wiki, and they already got a bug report associated with them.

---

### Post by kweetniet on 2009-12-04
> **AmyRose said:**
> In Intrepid, to fix this problem, I installed the **libv4l-0** package and preload it with Skype like this:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Help me
What is intrepid?
where do put the code?

---

### Post by Vgui on 2009-12-04
> **AmyRose said:**
> In Intrepid, to fix this problem, I installed the **libv4l-0** package and preload it with Skype like this:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Thanks a bunch! This worked for me on Xubuntu 9.10 with an old Logitech webcam, and also fixed the webcam for other apps (like Camorama).

---

### Post by tubsi on 2009-12-19
I start skype with:

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

When testing the camera in the options dialog it works fine, but when trying to use it in a call skype crashes and i get:

*** glibc detected *** skype: malloc(): memory corruption: 0x0b240360 ***
Segmentation fault

Any help will be apreciated :)

---

### Post by joepz on 2010-01-12
Exact same problem here. :(
Skype crashes when starting video during a call.
Video test works fine. I also use the preload command.

Ubuntu 9.10
Skype 2.1.0.47
Logitech webcam (of some kind)
I haven't found a fix yet.

Hopefully a fix soon

---

### Post by tormod on 2010-01-21
> **tubsi said:**
> When testing the camera in the options dialog it works fine, but when trying to use it in a call skype crashes and i get:

To avoid the crash, select "Start my video automatically when I am in a call" in Options -> Video Devices. It only crashes if you enable video manually after having started the call (in my experience at least).

---

### Post by kg4cna on 2010-01-28
> **AmyRose said:**
> In Intrepid, to fix this problem, I installed the **libv4l-0** package and preload it with Skype like this:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Excellent!  Works like a charm now :)  I added that line to the menu entry too so it's starts up I click on Skype.  Very nice ;)

BTW: My cam is a LogiTech C120m ($18.88 retail at the big box store nearby).

**Edit to add the laptop I use the cam on is running Intrepid.

Thanks!
A~

---

### Post by tormod on 2010-01-29
After upgrading to skype 2.1.0.81, I don't have to use LD_PRELOAD any longer (with Logitech S7500 on lucid).

---

### Post by raym0nd on 2010-02-23
> **e.m.fields said:**
> Hey guys - for those of us using this solution on** ***64-bit Skype*****: 

The solution here -> [http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/]("http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/") worked for me: 



The solution described in [http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/]("http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/") has worked for me too:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

After upgrading to 64-bit Ubuntu 9.10 and reinstalling skype, my Logitech webcam did not work in skype anymore. It did work under 64-bit Ubuntu in 9.04. Now it works fine.

Thanks for the tip.

---

### Post by giorgio_rome on 2010-02-24
Hi,
I was using Skype on Ubuntu 8.10 and it was working fine.
I'm now running a new installation of Ubuntu 9.10 with same HW and I have problem with the webcam.
Looking into several post I found that starting Skype with :

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

helps to start skype with webcam working.
I have set skype to have webcam automatically enabled when call is issued and the webcam is working within skype (test into video device section is fine) but as soon as I make a call and the call is answered skype crash with the following error:
*** glibc detected *** /usr/bin/skype: malloc(): memory corruption: 0x0ba254f0 ***

Ubuntu 9.10
Skype  2.1.0.81
Webcam Logitech QuickCam Express Plus 
(lsusb Bus 005 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus)

This webcam seems not to be supported into
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)
but the link seems to be not frequently updated.

Any further suggestion on things to do or to check ?

thanks in advance

giorgio

---

### Post by andybleaden on 2010-03-04
That has all been really helpful. 

For those like me who did not fully grasp the menu edit option

A way to fix the Skype/Logitech issue in Kubuntu and I assume Ubuntu as well is to edit the application menu which is not so scarey as it seems.

So here is how I did it it in Kubuntu 9.10.

I right clicked the 'kick off application launcher button' traditionally in the left corner and selected Menu Editor

In the KDE Menu Editor Box that comes up I selected 'Internet' by clicking on the + sign next to it and opened all the internet applications then scrolled down and clicked on 'Skype' 

Now on the right hand side of the KDE menu editor under the General Tab is a box called Command with the words skype written in it. This starts the Skyep programme. So far so good? Ok. I clicked on it and deleted it and then copy and pasted this command in
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

(Which until now I have been using via Konsole to start Skype...not very user friendly...especially for my family!)

After pasting it in I then pressed the save icon in the corner. 

This has now saved the command above for everytime you start skype!

When skype starts up next time it will automatically point skype to the camera.You can now fire up skype and test in  Options on the bottom left Blue S button or by hitting ctrl and O, clicking Video Devices and hitting the Test button next tothe details of your webcam.

Hope that makes it clearer.

If it makes you feel better it has taken me 3 months to get around to working this out for myself. ;) I just never understood the edit to the application fix suggested

However a big thankyou to all of those above who came up with the fix.

---

### Post by jhoney142 on 2010-03-04
> **AmyRose said:**
> In Intrepid, to fix this problem, I installed the **libv4l-0** package and preload it with Skype like this:

```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
Hi,
 Its working Thankyou:o

---

### Post by bjoern-b on 2010-03-14
Hi all,

I've got the same problem as tubsi, joepz and giorgio_rome. I'm using Ubuntu 9.10 and Skype 2.1.0.81 (32bit).

Without LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype I don't see any image.
With LD_PRELOAD the webcam works in the skype test window. Starting video in a call (with and without manual enabling) skype crashes with the error message:
*** glibc detected *** /usr/bin/skype: free(): invalid next size  0x0b25f508 ***

Btw: If I try cheese I always get only the first image regardless if I use LD_PRELOAD. 

Any ideads? Thanks in advance.
Björn

---

### Post by Cope57 on 2010-03-14
I heard a rumor long ago about people so ugly that thier camera would break.  Now that we are in the digital world, does this apply to webcams? ;)

---

### Post by giorgio_rome on 2010-03-15
> **Cope57 said:**
> I heard a rumor long ago about people so ugly that thier camera would break.  Now that we are in the digital world, does this apply to webcams? ;)

Perhaps Ubuntu has more aesthetic requirements , because, in my case, same webcam works with M$ Windows ;)

---

### Post by rstoya05-lx on 2010-06-20
> **raym0nd said:**
> The solution described in [http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/]("http://www.eoinmurphy.org/2009/04/26/logitech-webcam-skype-under-ubuntu/") has worked for me too:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype

After upgrading to 64-bit Ubuntu 9.10 and reinstalling skype, my Logitech webcam did not work in skype anymore. It did work under 64-bit Ubuntu in 9.04. Now it works fine.

Thanks for the tip.

I've 64-bit Ubuntu. On Lucid I've noticed the Skype menu item (under Applications - Internet) uses the script /usr/bin/skype-wrapper. The script contains this line:

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@"
```

According to this discussion this is correct for 64-bit system but for me Skype crashes when I try to start the camera. If I switch to this line it doesn't:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib/qt4/plugins /usr/bin/skype "$@"
```

Not really sure why that is? 

I've also noticed right-click menus on Skype (after upgrading to Lucid) use a dark foreground and background color making them unreadable unless you mouseover. Anyone have a solution for that?

---

### Post by kafkaPenguin on 2010-07-11
andybleaden
Thanks for your indepth solution.  Worked like a charm for me.

Okay I spoke too soon. :/  Skype worked fine for all the TESTING, but as soon as I called someone it crashed as soon as it connected.  This happens whether I call or they call.  I have tried all the solutions here and none seem to work.  My older version of Skype at least had the video working.  This 2.1 version wont even run that as it just crashes on connect.  this is the end of the call:


003fb000-003fd000 r-xs 00000000 08:05 254488     /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2                                               
003fd000-003fe000 r-xp 00000000 08:05 1685717    /usr/lib/libv4l/v4l1compat.so   
003fe000-003ff000 r-xp 00000000 08:05 1685717    /usr/lib/libv4l/v4l1compat.so   
003ff000-00400000 rwxp 00001000 08:05 1685717    /usr/lib/libv4l/v4l1compat.so   
00400000-0042b000 r-xp 00000000 08:05 1669755    /usr/lib/libfontconfig.so.1.3.0 
0042b000-0042c000 r-xp 0002a000 08:05 1669755    /usr/lib/libfontconfig.so.1.3.0 
0042c000-0042d000 rwxp 0002b000 08:05 1669755    /usr/lib/libfontconfig.so.1.3.0 
0042d000-00433000 r-xs 00000000 08:05 254428     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2Segmentation fault   


anyone have any ideas how to fix this?  very frustrating! Should I just go back to the older version?  I'm running this in Karmic btw.  Any advice will be much appreciated.

---

### Post by malmsteen84 on 2011-01-03
i got same problem here..
i use 10.10 and skype 2.1.0.81 beta

1. "skype-wrapper" command =
   video test crashes, skype terminates

2. "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype" command =
   video test crashes, skype terminates, error message : Segmentation fault

3. "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype" command =
   video test crashes, skype terminates, error message : Segmentation fault


you know what i'm talking about? i CANT even test my webcam.
but, cheese and gstreamer-properties play very fine with the webcam... strange

---

### Post by banyai on 2011-02-01
[I]Unfortunately,under Ubuntu 10.10 (64 bit) to your code I get an error message:
[/I]
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

(<unknown>:2892): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: falsche ELF-Klasse: ELFCLASS64

(<unknown>:2892): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2892): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: falsche ELF-Klasse: ELFCLASS64

(<unknown>:2892): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2892): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: falsche ELF-Klasse: ELFCLASS64

(<unknown>:2892): Gtk-WARNING **: Loading IM context type 'ibus' failed

*and  the video does notv react any more.* **By the way, I have checked, the lib-files are there!**

---

### Post by mrtsmith on 2011-03-21
This issue i'm running into is on Ubuntu 10.04 using the creative vf0470. Using the LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 

Though the person on the other side using skype for windows they can hear and see me but I cannot see them or myself.


If I go to options and press test video, in terminal mode I get this message in repetition yet the webcam light shows its on.
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes).

Now my laptop running 10.10 I get and see video using the LD... in term but my voice sounds slow

---

### Post by mrtsmith on 2011-03-21
I got the answer apparently having cairo-dock running prevents the cam from working.


But a new issue arises when I'm using skype to do video, if I show my video, then my picture breaks a line through skype and the very top have gets copied to the same box size my video is , I try to replicate it

            ---------------
            |             |
            |Person O     |
            |      -|-    |
            |       |     |
            |             |
            |_____________|
            |Me |         |
            |___|->_0_____|

I tried to replicate as best as possible, if I turn on my personal view it goes away , still have the same issue with laptop except video is fine audio is not.

Thanks

---

### Post by jvan_ca on 2011-04-14
I'm running Ubuntu 10.10 on my Sony Vaio FZ-180E which runs the R5u87X video driver.  The camera works fine in cheese, however when I load Skype the camera light comes on, but the screen remains black.  When I attempt to video conference with someone the video screen goes white until I close the call.

I attempted your suggestion in the terminal, but to no avail, had the exact same problem as I mention above.

Here is the information from what I received when I typed in my terminal with your code:

user@user-VGN-FZ180E:~$ env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
libv4l2: error dequeuing buf: Device or resource busy

Also, here is my lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Hoping that you can assist me, or atleast point me in the right direction.

---

