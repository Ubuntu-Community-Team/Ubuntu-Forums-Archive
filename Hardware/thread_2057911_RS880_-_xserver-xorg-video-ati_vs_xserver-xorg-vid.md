---
title: "RS880 - xserver-xorg-video-ati vs xserver-xorg-video-radeon"
date: 2012-09-14
forum: Hardware
---

### Post by eingousef on 2012-09-14
Hello,

I use an ubuntu 12.04.1 (lubuntu flavor) with the free AMD drivers from the ubuntu repositories on a Radeon HD 4250 aka AMD 880G aka RS880 IGP, and I have strange issues with the free drivers, depending if the xserver-xorg-video-ati package is installed or not.

When xserver-xorg-video-ati and xserver-xorg-video-radeon are both installed, the GL games I launch run fine, but I can't record them in a screencast. No matter if I use ffmpeg, recordmydesktop or glc-capture, all I get is a video that show the desktop and turns to a black screen when it's supposed to show the game running (the mouse cursor is diplayed, though). With SDL games screencasts work fine.

When I uninstall the xserver-xorg-video-ati package, I can screencast the GL games, but they are a bit slow (no matter if I'm recording or not), my mouse cursor blinks and 0ad displays nothing but text and cursor when I launch it.

So, here's my question : Is xserver-xorg-video-ati doing more than being a simple wrapper that launch the radeon driver depending on GPU recognition ? What does it do exactly ?

[I]Update: Got my answer. Yes, actually it does more than that. xserver-xorg-video-ati seem to be necessary to make the radeon driver work completely. I don't know the details.
I can record a screencast with the xserver-xorg-video-ati package now. It seems that there was something wrong with some packages from the install cd, a simple :

apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

solved the problem.

I'm still unable to record screencast with the catalyst drivers, though, but this the catalyst's fault, I guess.[/I]

---

