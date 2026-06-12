---
title: "question re video card &amp; hardware (in general)"
date: 2018-05-13
forum: Hardware
---

### Post by wfriedwaldgmail.c on 2018-05-13
I'm running ubuntu on a very inexpensive HP laptop c2015.

it's perfectly fine for everything I need to do EXCEPT when I play a video, often the movement "stutters" or stalls.  I get the feeling that's because there isn't enough processing power to make it go smoothly, or the video card isn't powerful enough? I certainly can't play a blu-Ray-quality file - they're way too big.

question: is there a way I can upgrade the hardware, go to a better video card, to make everything play smoothly?

or: would everyone recommend that I just buy another low-cost laptop that might be at least slightly better?

can anyone recommend an inexpensive laptop, upon which I can install the latest version ubuntu, and it will be able to properly play a video file of 1080p or so?

thanks very much,

w

---

### Post by SeijiSensei on 2018-05-14
What CPU do you have?  If you don't know, run the command "lscpu | grep name" to see.  For instance, on my system that returns
```
Model name:          Intel(R) Core(TM) i5-4460  CPU @ 3.20GHz
```

Whether you can upgrade the video card is something only HP can tell you.  On low-end machines, the video is usually integrated into the system hardware.  Looking up "HP laptop c2015" doesn't return a specific model, but a large class of machines with widely varying capabilities.

You don't tell us what software you're using to play videos.  You might give the combination of mpv and smplayer a try.
```

sudo apt update
sudo apt install mpv smplayer

```
SMPlayer is a nice GUI front end for mpv and its older sibling mplayer.

---

### Post by Autodave on 2018-05-14
Also, depending on your RAM availability, adding more RAM or switching to a lighter desktop such as Xubuntu or Lubuntu could help quite a bit. Ubuntu is a quite heavy desktop.

---

### Post by wfriedwaldgmail.c on 2018-05-14
thanks!  here's the first answer :

```
Model name:            Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz
```

I have tried running video files on two apps - the built in 
"VIDEOS" (VIDEO PLAYER)  - not sure what it's called, but it's the one that comes with Ubuntu
and 
VLC - which I also use in Mac (and even windows) it plays pretty much everything.

but some videos "stutter" with both programs, and neither can effectively play bluRay.

I could try mpv + smplayer and see what happens, see if the stuttering persists.

thanks!

w

PS: the stuttering isn't continually, just an occasional blip, every 5-10 minutes or so.


PS: if this is of any use:

```
will@will-HP-Stream-Notebook-PC-11:~$ sudo apt update
[sudo] password for will: 
Ign:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease
Ign:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease              
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports InRelease            
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty Release                        
  404  Not Found [IP: 91.189.91.23 80]
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates Release                
  404  Not Found [IP: 91.189.91.23 80]
Hit:7 [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                              
Err:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-backports Release              
  404  Not Found [IP: 91.189.91.23 80]
Hit:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Ign:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease              
Err:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security Release  
  404  Not Found [IP: 91.189.88.149 80]
Reading package lists... Done
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
------ AND THEN:
```
will@will-HP-Stream-Notebook-PC-11:~$ sudo apt install mpv smplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ffmpeg libavdevice57 libqt5script5 libsdl2-2.0-0 libuchardet0 libva-wayland1
  rtmpdump smplayer-l10n smplayer-themes youtube-dl
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed:
  ffmpeg libavdevice57 libqt5script5 libsdl2-2.0-0 libuchardet0 libva-wayland1
  mpv rtmpdump smplayer smplayer-l10n smplayer-themes youtube-dl
0 upgraded, 12 newly installed, 0 to remove and 8 not upgraded.
Need to get 10.1 MB of archives.
After this operation, 32.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 libqt5script5 amd64 5.7.1~20161021+dfsg-2build1~3
  404  Not Found [IP: 91.189.91.23 80]
Ign:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 youtube-dl all 2017.03.26-1
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 libsdl2-2.0-0 amd64 2.0.5+dfsg1-2ubuntu3
  404  Not Found [IP: 91.189.91.23 80]
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 libavdevice57 amd64 7:3.2.4-1build2
  404  Not Found [IP: 91.189.91.23 80]
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 ffmpeg amd64 7:3.2.4-1build2
  404  Not Found [IP: 91.189.91.23 80]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 libuchardet0 amd64 0.0.1-1ubuntu1 [65.2 kB]
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 libva-wayland1 amd64 1.7.3-2
  404  Not Found [IP: 91.189.91.23 80]
Err:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 mpv amd64 0.24.0-1
  404  Not Found [IP: 91.189.91.23 80]
Err:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 smplayer amd64 17.3.0~ds0-1
  404  Not Found [IP: 91.189.91.23 80]
Ign:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 smplayer-l10n all 17.3.0~ds0-1
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 smplayer-themes all 1:17.2.0-1
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe amd64 rtmpdump amd64 2.4+20151223.gitfa8646d.1-1 [43.5 kB]
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe i386 youtube-dl all 2017.03.26-1
  404  Not Found [IP: 91.189.91.23 80]
Err:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe i386 smplayer-l10n all 17.3.0~ds0-1
  404  Not Found [IP: 91.189.91.23 80]
Err:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty/universe i386 smplayer-themes all 1:17.2.0-1
  404  Not Found [IP: 91.189.91.23 80]
Fetched 109 kB in 0s (477 kB/s)
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qtscript-opensource-src/libqt5script5_5.7.1~20161021+dfsg-2build1~3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qtscript-opensource-src/libqt5script5_5.7.1~20161021+dfsg-2build1~3_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/y/youtube-dl/youtube-dl_2017.03.26-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/y/youtube-dl/youtube-dl_2017.03.26-1_all.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libs/libsdl2/libsdl2-2.0-0_2.0.5+dfsg1-2ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libs/libsdl2/libsdl2-2.0-0_2.0.5+dfsg1-2ubuntu3_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/libavdevice57_3.2.4-1build2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/libavdevice57_3.2.4-1build2_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_3.2.4-1build2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/f/ffmpeg/ffmpeg_3.2.4-1build2_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva-wayland1_1.7.3-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libv/libva/libva-wayland1_1.7.3-2_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mpv/mpv_0.24.0-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/m/mpv/mpv_0.24.0-1_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer/smplayer_17.3.0~ds0-1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer/smplayer_17.3.0~ds0-1_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer/smplayer-l10n_17.3.0~ds0-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer/smplayer-l10n_17.3.0~ds0-1_all.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer-themes/smplayer-themes_17.2.0-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/smplayer-themes/smplayer-themes_17.2.0-1_all.deb)  404  Not Found [IP: 91.189.91.23 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

THANKS AGAIN!

---

### Post by SeijiSensei on 2018-05-14
Ubuntu 17.04 ("Zesty") reached its [end-of-life in January of this year]("http://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/").  Most ordinary users should install only versions with "long-term support."  An LTS version is released in April of even-numbered years.  The most recent is 18.04 ("Bionic"), though 16.04 will be supported through early 2021.  You should consider installing one of these. Non-LTS versions receive only nine months of support.

---

### Post by wfriedwaldgmail.c on 2018-05-14
oh thank you!

as always, I am delighted to do whatever the fine folks on this forum recommend.

can you give me the steps  (terminal commands) necessary to install 18.04 ?  (I thought I had done it already ... apologies.)

w

---

### Post by SeijiSensei on 2018-05-14
You could try using "sudo do-release-upgrade", but I strongly recommend starting with a clean installation from scratch.  You can pick a "flavor" from here:  [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) 

The easiest method is to use Ubuntu's Startup Disk Creator app to create a bootable USB key: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Make sure you back up everything you care about first, of course.

See [https://ubuntuforums.org/showthread.php?t=2391433](https://ubuntuforums.org/showthread.php?t=2391433) for a discussion of upgrading versus installing  from scratch.

---

### Post by wfriedwaldgmail.c on 2018-05-14
okay! one follow-up question: whenever I have done a "clean" install in the past, that has meant going into the BIOS and making some adjustments there - that's kind of tricky for me.  if the system is currently running an unbuntu-linux OS, then I wouldn't have to mess around with the BIOS, hopefully, to put on a new unbuntu-linux OS, would i?

thanks again!

w

---

### Post by wfriedwaldgmail.c on 2018-05-15
another follow-up question: what are the specific steps to making a USB boot / install device when working on my current Ubuntu 17 OS?  (I could also make a USB boot install device on my Mac desktop.  Although, of course, the laptop is a PC-Windows machine.)

thanks!

w

---

### Post by SeijiSensei on 2018-05-15
> **wfriedwaldgmail.c said:**
> another follow-up question: what are the specific steps to making a USB boot / install device when working on my current Ubuntu 17 OS?  (I could also make a USB boot install device on my Mac desktop.  Although, of course, the laptop is a PC-Windows machine.)

I posted the answer to this question above.  Did you not read it? [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by wfriedwaldgmail.c on 2018-05-15
apologies! thanks!  sorry I missed that.

w

---

