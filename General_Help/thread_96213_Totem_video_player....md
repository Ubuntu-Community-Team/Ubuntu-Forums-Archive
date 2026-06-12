---
title: "Totem video player..."
date: 2005-11-28
forum: General Help
---

### Post by DiscoKiller on 2005-11-28
is it just me or does totem have absolutely no use what so ever apart from scaring the shit out of me when it fails to play a movie.....any movie....anything at all....oh and if u were wondering what scared me it is the notification noise which means ERROR...!!!

---

### Post by frodon on 2005-11-28
Install the totem-xine package and the codecs you need and you will never get probems again.

---

### Post by derekfv on 2005-11-28
Absolutely - never works for me either, Derek

---

### Post by bugi on 2005-11-28
[QUOTE=DiscoKiller]is it just me or does totem have absolutely no use what so ever apart from scaring the shit out of me when it fails to play a movie.....any movie....anything at all....oh and if u were wondering what scared me it is the notification noise which means ERROR...!!![/QUOTE]

You can install totem-xine or if you want to use gstreamer, just download all available plugins with "gstreamer" in name ;-) It works for me, maybe gstreamer is not perfect yet but most of the movies work :-)

---

### Post by frodon on 2005-11-28
This is the most popular codecs you may need to read videos : w32codecs, libdvdcss2, gstreamer0.8-plugins, gstreamer0.8-lame, gstreamer0.8-ffmpeg, gstreamer0.8-faac, gstreamer0.8-faad, libxvidcore4, lame, sox, ffmpeg, mjpegtools, vorbis-tools, mpg321

Install those you need, a basic totem needs the totem plugins however totem-xine don't need them.

---

### Post by mrsad on 2005-11-28
i found that even after installing all the gstreamer plugins, totem-xine is still able to play more media files. so that's what i'm using at the moment, and it is trouble free.

---

### Post by bugi on 2005-11-28
Unfortunately Totem with gstreamer doesn't play all of my mp4 videos, some like those from go-open series work well, but another one don't work at all. Hopefuly new versions of gstreamer would be better ;-)

---

### Post by Kevinator on 2005-11-28
I managed to get totem-gstreamer to play a DVD (by installing all the gstreamer codecs and libdvdcss), but the performance was abysmal. I don't know why. Turning on DMA didn't help. Removing all the gstreamer stuff and adding totem-xine plus a few suggested packages fixed it. I didn't even get around to testing media files - if I can't properly play DVDs, I won't use it.

---

### Post by frodon on 2005-11-29
I agree with all of you, i found totem-xine far better than totem-gstreamer but i prefer that the users make their own choice, that why i gave you the needed gstreamer plugins.

---

### Post by vivekrawal on 2005-11-29
hello!!! I am new to linux world and i am very happy to have found UBUNTU. I guess I have most of the things working. I was also able to install some packages from Debian DVD using synaptic. But today I realised there was a problem. when i tried to play a VCD, totem will not work. i am not able to install totem-xine or gstreamer plugins also because of the following issue.

totem-xine:
 Depends: dbus-1 but it is not going to be installed
 Depends: libhal0 but it is not going to be installed
 Depends: libnautilus-burn0 but it is not going to be installed

I do not know how to get around this.

I also tried to install VLC and was not successful in that too. It also gave me following message.
vlc:
 Depends: dbus-1 but it is not going to be installed
 Depends: libhal0 but it is not going to be installed
 Depends: wxvlc but it is not going to be installed

could some one please help me with instructions to sort this out?

Vivek

---

### Post by frodon on 2005-11-29
Maybe you have a problem in your source.list file, could you post it here ? to open it : ```
sudo gedit /etc/apt/source.list
```Recommended source.list : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by vivekrawal on 2005-11-29
my /etc/apt/sources.list file

deb cdrom:[Debian GNU/Linux 3.1 r0a _Sarge_ - Official i386 Binary-2 (20050607)]/ sarge contrib main
deb cdrom:[Debian GNU/Linux 3.1 r0a _Sarge_ - Official i386 Binary-1 (20050607)]/ sarge contrib main
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main


are there any problems here? 
vivek

---

### Post by frodon on 2005-11-29
There's some missing repositories like breezy-updates repositories, look the link i gave in the post #11, there's all the needed repositories in with some useful informations. 
Add the repositories you don't have or just cut and paste it.

---

### Post by vivekrawal on 2005-11-30
Thank you so much. I have done what you and successfully installed totem-xine through synaptic. Though totem-gstreamer got uninstalled as a result. But video player is now working.
Cheers.


[QUOTE=frodon]There's some missing repositories like breezy-updates repositories, look the link i gave in the post #11, there's all the needed repositories in with some useful informations. 
Add the repositories you don't have or just cut and paste it.[/QUOTE]

---

### Post by DiscoKiller on 2005-11-30
You know what?, i wrote the original thread slagging totem off and lo and behold, without tweaking a smegging thing the little blighter goes and plays an episode of the mighty boosh. i love it. anyway, i appreciate all your help and advice but theres one file extension thats eluded me thusfar, WMV files appear nearly impossible for me to play. i had them going on hoary but breezy is aving none of it. love me more and tell me which progs you recommend and the procedures for getting the little beasties to work. 

hugs DK

---

### Post by frodon on 2005-12-01
For wmv files you need to install w32codecs : 
[http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs)

---

### Post by akiro.yamamoto on 2005-12-01
Go here for more:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by frodon on 2005-12-01
This link is also in the first link i gave ;)

---

### Post by DiscoKiller on 2005-12-01
nice one peoples. worked a treat the old w32codecs malarky, many thanks

---

