---
title: "No sound in Karmic, HP Pavilion DV6"
date: 2009-12-12
forum: Hardware
---

### Post by Grannun on 2009-12-12
I recently installed Karmic onto my DV6 laptop and there is no sound.  I went though the the troubleshooter and it didn't find anything.  Headphones don't work either.  I consider myself pretty knowledgeable when it comes to linux, so you can assume I know how to do most things without walking me through it.

Thanks

---

### Post by Grannun on 2009-12-19
bump

---

### Post by Digikid on 2009-12-19
I do not have that model but I DO have a Touchsmart TX2 1224CA from HP and there is a possibility that you may have the same problem that I had.  Try it and see what happens.

Did you activate your modem drivers?  If the answer is yes then DEACTIVATE them and see if your sound works.

I find that this is a common thing with HP Laptops.  For most models the modem drivers kill the sound.

Besides in this day and age....I doubt that you need the 56k modem anyways.  ;)

---

### Post by RedSingularity on 2009-12-19
Post the ouput of aplay -l

---

### Post by JorgePap on 2009-12-20
Hi! I'm new to the forum and Linux, and I have the same problem on my pavilion dv6 2030ev, which i loaded Karmic Koala 9.10 after windows 7. Everything is fine but no sound at all. I searched the forums tried a new install of alsa but in vain...

My output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jorge@jorge-laptop:~$ 

any help will be appreciated!

---

### Post by RedSingularity on 2009-12-20
In a terminal type 

alsamixer

and make sure the volume is all the way up.

---

### Post by Digikid on 2009-12-21
> **JorgePap said:**
> Hi! I'm new to the forum and Linux, and I have the same problem on my pavilion dv6 2030ev, which i loaded Karmic Koala 9.10 after windows 7. Everything is fine but no sound at all. I searched the forums tried a new install of alsa but in vain...

My output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jorge@jorge-laptop:~$ 

any help will be appreciated!

Try me method above as it WILL work.

---

### Post by JorgePap on 2009-12-21
Sorry no results from alsamixer. The volumes are all up (100) but still no sound!
.....:confused:

How do I deactivate my modem drivers? (I am a newbee, yes!)

---

### Post by Sxeptomaniac on 2009-12-21
Unfortunately, the DV6 has had a lot of problems with sound.  I have one as well.  I actually had it all working correctly for a little while, but lost my headphones when I made the mistake of upgrading my kernel.  Here's what I know:

You need to start by editing /etc/modprobe.d/alsa-base.conf.  Do this by putting the following into a terminal (if I correctly remember the text editor in Gnome):

> sudo gedit /etc/modprobe.d/alsa-base.conf

At the bottom of that file, you need to add the following line (these are the additions I've had the most success with, but I currently only have my main speakers and built-in microphone working):
> alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-3 enable_msi=1

There's the possibility that might work if you are using Karmic.  If you are not, you'll also need to upgrade ALSA.  The easiest way to do that is with a script, available and explained [in this thread](http://ubuntuforums.org/showthread.php?p=6589810).

Once it's done, you'll probably need to check your mixer settings, but it should work.  I'll update this thread if I can figure out what I did to get my headphones working again.

---

### Post by Digikid on 2009-12-21
> **JorgePap said:**
> Sorry no results from alsamixer. The volumes are all up (100) but still no sound!
.....:confused:

How do I deactivate my modem drivers? (I am a newbee, yes!)

Go into your hardware drivers section and unselect the modem drivers.  Thats it.

---

### Post by Sxeptomaniac on 2009-12-22
> **Digikid said:**
> Go into your hardware drivers section and unselect the modem drivers.  Thats it.

Sorry, but that problem sounds identical to mine, and I never activated any modem hardware drivers.  The only hardware driver I've got running is for my ATI graphics chipset.

---

### Post by Digikid on 2009-12-22
Thats good I guess.  It was just a thought since it worked fine for me.

---

### Post by Grannun on 2009-12-22
Thank you Sxeptomaniac, I did both things you described and I now have working sound! I don't know which one did it, but I don't care cause it works.  Thanks again

---

### Post by hotshot247 on 2009-12-22
i have a toshiba satellite laptop but this might work for you. go to the ubuntu software center and type "gnome alsa mixer" and install it and then open gnome alsa mixer when you get it installed and see if "external amplifier" is checked and if it is, uncheck it. that worked for me. let me know if it works for you.

---

### Post by JorgePap on 2009-12-23
Fine end for me too!

Many thanks folks for your advice. I have my speakers working now but the sad is that i don't know which trick make them sound!... I also installed The Ubuntu Restricted Extras:

sudo apt-get install ubuntu-restricted-extras

which i found in 

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic) 

The sound come right after that. :)

---

### Post by karthik.shrinarsi on 2009-12-24
> **JorgePap said:**
> Hi! I'm new to the forum and Linux, and I have the same problem on my pavilion dv6 2030ev, which i loaded Karmic Koala 9.10 after windows 7. Everything is fine but no sound at all. I searched the forums tried a new install of alsa but in vain...

My output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jorge@jorge-laptop:~$ 

any help will be appreciated!




try the alsa mixer version 1.0.22.I hope it will work..

---

### Post by kronictokr on 2009-12-26
after beating my head in the table , found it :D

there is a post here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/427670](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/427670)

that say to install linux-backports-modules-alsa-karmic and reboot , for karmic of course. and it worked for me. that and fiddling arround with system>>preferences>>>sound  lets you pick sound devices and manipulate and turn on or off most of your sound aspects.

and dont forget about the restricted extras as well, easy to install  in synaptics 

ive got the ati working perfectly as well

hp pavillion dv6  ati4200 atherosII dual core

edit: was gona post a link to the ati solution, in case some1 had the same computer, but closed it by mystake. just check my posts

---

### Post by AllanP on 2009-12-27
Thanks Sxeptomaniac. I have an HP DV6-2043CA laptop and have put many hours in trying to get sound working. I used your method and Bob's your uncle; sound.
sudo gedit /etc/modprobe.d/alsa-base.conf
and put at the bottom of the file:
alias snd-card-0 snd-hda-intel
alias snd-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-3 enable_msi=1

Still no sound until I followed the ALSA instructions here: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810).

Thanks again. Now if I could get a bit more battery life in Linux.

---

### Post by kronictokr on 2010-01-03
last post, kronictokr, only if u can read linux

[http://ubuntuforums.org/showthread.php?t=1350637&highlight=ati+radeon+4200+HD](http://ubuntuforums.org/showthread.php?t=1350637&highlight=ati+radeon+4200+HD)

---

### Post by kronictokr on 2010-01-03
ubuntu karmic 9.10 sound fix solved

did a fresh install , did a full update, waited and 24 hrs later did another, installed ati catalyst, then&#8230;..

redone for more recent pakages, as well, removed a couple useless ones
doesnt involve removing pulse. gets sound through hdmi earphones and laptop speakers
still testing, but all works

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-19-generic linux-backports-modules-alsa-2.6.31-19-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-19-generic vlc

sudo reboot

enjoy!!

leave a message if you have any problems. but this shouldnt harm anything at all

getting great sound :grin:

---

### Post by etherealknight on 2010-01-04
I have the same problem except that my headphones do work...

I've added the lines to the .conf file

I've made sure all the volume levels were up

I don't have anything grabbing my sound before pulse server does

I've upgraded alsa

I don't have any modem drivers active

and here is the output of aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


thanks for any help

---

### Post by Sxeptomaniac on 2010-01-04
> **etherealknight said:**
> I have the same problem except that my headphones do work...

I've added the lines to the .conf file

I've made sure all the volume levels were up

I don't have anything grabbing my sound before pulse server does

I've upgraded alsa

I don't have any modem drivers active

and here is the output of aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


thanks for any help

You apparently have a different version of the DV6 from mine, as my chipset is ATI, not NVidia.  See if you can find your exact model number and check the [snd_hda_intel options list](http://ubuntuforums.org/showthread.php?t=1043568).  You may need to adjust what you add to the end of the ALSA configuration file.  It's not well organized right now, but there are a number of different DV6 models listed there.

Also, I see from the thread that the [upgrade script is being updated](http://ubuntuforums.org/showpost.php?p=8608142&postcount=558) (probably to ALSA 1.0.22, which, [according to the changelog](http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22), will better support DV6 series laptops).  I'm working on manually updating my ALSA, but having a little trouble myself (probably a side-effect from one of the many other attempts I've tried).

---

### Post by etherealknight on 2010-01-04
> **Sxeptomaniac said:**
> You apparently have a different version of the DV6 from mine, as my chipset is ATI, not NVidia.  See if you can find your exact model number and check the [snd_hda_intel options list]("http://ubuntuforums.org/showthread.php?t=1043568").  You may need to adjust what you add to the end of the ALSA configuration file.  It's not well organized right now, but there are a number of different DV6 models listed there.

Also, I see from the thread that the [upgrade script is being updated]("http://ubuntuforums.org/showpost.php?p=8608142&postcount=558") (probably to ALSA 1.0.22, which, [according to the changelog]("http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22"), will better support DV6 series laptops).  I'm working on manually updating my ALSA, but having a little trouble myself (probably a side-effect from one of the many other attempts I've tried).

I can see where upgrading could be a problem... I've tried to fix my sound in various ways and one of them accidentally killed my wireless XD I got that up and running again though.. I will try editing the file again and see what happens..

---

### Post by etherealknight on 2010-01-04
> **etherealknight said:**
> I can see where upgrading could be a problem... I've tried to fix my sound in various ways and one of them accidentally killed my wireless XD I got that up and running again though.. I will try editing the file again and see what happens..
 
well.. I changed the configuration to model= laptop-hpmicsense

still no sound... my pulse server shows that sound is being played.. but I can't hear it...

---

### Post by Sxeptomaniac on 2010-01-07
[The ALSA upgrade script is updated](http://ubuntuforums.org/showthread.php?t=1046137).  I'm going to update my kernel headers and run it.  We'll see how it goes.

---

### Post by loignoro on 2010-01-13
> **Sxeptomaniac said:**
> Unfortunately, the DV6 has had a lot of problems with sound.  I have one as well.  I actually had it all working correctly for a little while, but lost my headphones when I made the mistake of upgrading my kernel.  Here's what I know:

You need to start by editing /etc/modprobe.d/alsa-base.conf.  Do this by putting the following into a terminal (if I correctly remember the text editor in Gnome):



At the bottom of that file, you need to add the following line (these are the additions I've had the most success with, but I currently only have my main speakers and built-in microphone working):


There's the possibility that might work if you are using Karmic.  If you are not, you'll also need to upgrade ALSA.  The easiest way to do that is with a script, available and explained [in this thread]("http://ubuntuforums.org/showthread.php?p=6589810").

Once it's done, you'll probably need to check your mixer settings, but it should work.  I'll update this thread if I can figure out what I did to get my headphones working again.

I have this and not sound, but i install this pakage and ok, include headphones:

> sudo apt-get install linux-backports-modules-alsa-karmic-generic

thanks for all :P

---

### Post by kronictokr on 2010-01-30
ubuntu karmic 9.10 sound fix solved

did a fresh install , did a full update, waited and 24 hrs later did another, installed ati catalyst, then&#8230;..

redone for more recent pakages, as well, removed a couple useless ones
doesnt involve removing pulse. gets sound through hdmi earphones and laptop speakers
still testing, but all works

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-19-generic linux-backports-modules-alsa-2.6.31-19-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-19-generic vlc

sudo reboot

enjoy!!

leave a message if you have any problems. but this shouldnt harm anything at all

getting great sound :grin:

---

### Post by alambiko on 2010-02-02
hi!
the same problem with hp dv6850el+ubuntu 9.10.
yea it's really, if i disable internal modem audio& mic are ok, & at the same time if i able, modem is ok but audio (& mic to rec is off).
mty problem is that where i live there's no adso, no wireless & no umts..so i need to use the intern modem dial up 56 k.
please, can someone help me? thanx

---

### Post by kronictokr on 2010-02-14
you should try the above post

hit tab enter twice at the right time during install
 reboot
yay sound

---

### Post by mkoenig1975 on 2010-02-25
> **kronictokr said:**
> ubuntu karmic 9.10 sound fix solved

did a fresh install , did a full update, waited and 24 hrs later did another, installed ati catalyst, then…..

redone for more recent pakages, as well, removed a couple useless ones
doesnt involve removing pulse. gets sound through hdmi earphones and laptop speakers
still testing, but all works

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-19-generic linux-backports-modules-alsa-2.6.31-19-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-19-generic vlc

sudo reboot

enjoy!!

leave a message if you have any problems. but this shouldnt harm anything at all

getting great sound :grin:

I know this may seem silly but I JUST installed Ubuntu and I see the info above, I have ATI catalyst installed but how do I do whatever you're referring to after that? I have a dv6-2066dx with 6GB of Ram and no sound and no idea how to get sound. It's killing me. Help please!

---

### Post by kronictokr on 2010-02-25
top left, click Applications>>Accessories>>Terminal

then copy and paste this VVVVV into it, you have to right click in terminal to paste, hit enter, then tab enter twice when it asks, wait till its done reboot, you should be greeted with sound

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-19-generic linux-backports-modules-alsa-2.6.31-19-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-19-generic vlc

---

### Post by viharm on 2010-03-24
I have HP Pavilion dv6-1216sa laptop with AMD chipset, onboard sound and ATI Mobility Radeon HD 4530 graphics (with HDMI sound).

I am happy to report that kronictokr's method works for me - for built-in speakers, earphones as well as HDMI sound.

However jack-sensing is not available so when earphones are plugged in the laptop speakers are still active. Hopefully will get there soon. But this is indeed a great relief. Thanks to kronictokr.


Regards.

---

### Post by Cephiro on 2010-03-25
> **kronictokr said:**
> ubuntu karmic 9.10 sound fix solved

did a fresh install , did a full update, waited and 24 hrs later did another, installed ati catalyst, then…..

redone for more recent pakages, as well, removed a couple useless ones
doesnt involve removing pulse. gets sound through hdmi earphones and laptop speakers
still testing, but all works

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-19-generic linux-backports-modules-alsa-2.6.31-19-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-19-generic vlc

sudo reboot

enjoy!!

leave a message if you have any problems. but this shouldnt harm anything at all

getting great sound :grin:

Thanks, this solved the problems I was having with sound in a HP dv6 laptop. The quality of the sound sucks, but at least it's there. ;)

---

### Post by danj-1 on 2010-05-19
> **kronictokr said:**
> ubuntu karmic 9.10 sound fix solved

did a fresh install , did a full update, waited and 24 hrs later did another, installed ati catalyst, then&#8230;..

redone for more recent pakages, as well, removed a couple useless ones
doesnt involve removing pulse. gets sound through hdmi earphones and laptop speakers
still testing, but all works

sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-19-generic linux-backports-modules-alsa-2.6.31-19-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-19-generic vlc

sudo reboot

enjoy!!

leave a message if you have any problems. but this shouldnt harm anything at all

getting great sound :grin:
I did this and it seems to have worked.  what are the side-effects here?  I should always use the linux 2.6.31-19 version?  Did this command specifically set grub to always boot into this version? It seems to have.  If so, how?  Thanks for the info

---

### Post by kronictokr on 2010-05-25
glad to have helped some people out.!!

ar far as the kernel version, modify the script, just by changing it to whatever kernel version you are or want to run, then rerun the scrip, and you should be good to go :)

---

