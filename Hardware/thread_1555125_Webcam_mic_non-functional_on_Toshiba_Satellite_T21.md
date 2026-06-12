---
title: "Webcam mic non-functional on Toshiba Satellite T215D-S1150"
date: 2010-08-17
forum: Hardware
---

### Post by jdb2 on 2010-08-17
This was adapted from a post on the Linux Mint forums. I'm running Linux Mint 9 Isadora KDE 64-bit which is a derivative of Kubuntu 10.04 Lucid 64-bit :

I've been trying to get the webcam mic on my Toshiba Satellite T215D-S1150 notebook/netbook to work to no avail. My model has a Realtek ALC269 audio chipset combined with an ATI southbridge ( ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40) ) using the "snd_hda_intel" kernel module. I've attempted using basically every combination of settings in "alsamixer" that makes sense. In addition to that, I've tried adding the "options snd-hda-intel model=" parameter in "/etc/modprobe.d/alsa-base.conf" starting with "basic" and trying every combination of "Input Source." I've also tried the "auto", "lenovo", "toshiba" and "3stack" models, but nothing works -- In each instance I get nothing when I try "arecord -t wav -f cd filename" and/or try-to-capture-sound/access-the-mic in eg. VLC Media Player or Skype where in the case of VLC I've tried "Open Capture Device..." where I've tried every possible audio device node with "Audio device name" and in the case of Skype I've tried "Skype Test Call."

My ALSA system information for the default model and the model "basic" respectively can be accessed here :

[http://www.alsa-project.org/db/?f=5a7e986d7cad81213d2ef64f02ae478c7994c4d7](http://www.alsa-project.org/db/?f=5a7e986d7cad81213d2ef64f02ae478c7994c4d7)

[http://www.alsa-project.org/db/?f=f334a100b0c173875d838e57e42e7c23d98da8b7](http://www.alsa-project.org/db/?f=f334a100b0c173875d838e57e42e7c23d98da8b7)



Currently I'm at a loss as to what the problem is or what further action to take.

I'd be grateful for any assistance.


Thanks,

jdb2

---

### Post by SkylinesSuck on 2010-12-28
I know this is old, but just for reference, this worked for me with the same netbook.........

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

### Post by SkylinesSuck on 2011-03-18
This also worked for me:

sudo aptitude install linux-backports-modules-alsa-lucid-generic

---

### Post by jdb2 on 2011-03-18
I should have posted this reply much earlier, but I fixed the problem months ago by adding the [Ubutu-Audio-Dev]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa") repo to my software sources and installing the latest ALSA drivers ( 1.0.23 ) as well as changing the driver model from "basic" back to "auto" ( the default). Also, I've upgraded to the backported 2.6.37-12-generic #26~lucid1 Natty kernel which obsoletes the need to install the backported ALSA drivers.


In any case, thanks for your help. :)

jdb2

---

