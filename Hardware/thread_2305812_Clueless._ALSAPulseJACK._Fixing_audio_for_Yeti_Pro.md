---
title: "Clueless. ALSA/Pulse/JACK. Fixing audio for Yeti Pro microphone and basic sound."
date: 2015-12-09
forum: Hardware
---

### Post by JCopse on 2015-12-09
I am new to Ubuntu. I've been running 14.04 for a month or two without any problems and it has been a better experience than Windows, though more confusing. Up until today all of my audio was working fine, and my keyboard automatically connected with volume controls. Today I got my (Blue) Yeti Pro USB microphone and plugged it in, and found that Audacity would only let me record by switching to something called Jack. Jack let em record, but I had to switch back to ALSA to hear playback. So I thought I needed some plugins and went to do a Google search. Tons of confusing results later, I just tried opening Synaptic Package Manager and downloading anything I could find about Jack. That sort of random downloading has worked out well for em before, but it seems to have totally screwed me up on linux. After restarting my computer, my volume icon was gone and no audio was working. I followed a guide about uninstalling ALSA and pulse and then reinstalling. That didn't fix anything. I found another page that said Jack and pulse don't actually work together so I uninstalled pulse and restarted again. Audacity now lets me use ALSA for playback (via sound71 - a surround sound driver I guess?) and recording (via Yeti Stereo Microphone, which wasn't in the list before the restart). The problems are that now no other audio works, and the surround71 outputs any computer sound (including mouse clicks and anything I say into the microphone). YouTube videos don't play sound, I cant' hear anything with RhythmBox, and so on.

I found sites that had a lot of very complicated instructions about how to make Ubuntu work with Jack and ALSA with no pulse, but because I'm new to Ubuntu almost everything written there goes over my head because it assumes a level of fluency. I know how to use sudo from terminal but I don't don't even know Ubuntu's basic file structure sow hen a terminal commend I'm told to use doesn't work or returns an error, I have no idea what to try next.

Does anyone here use Jack without pulseaudio or have a Yeti that they got to work without Jack? Can someone help me try to get my volume icon back without leaving em unable to use my microphone?


Edit: I didn't uninstall anything when using package manager, I only added things that didn't prompt or an uninstall of other packages. Could it be that something I added is preventing a normal process from loading?

Also I see that right now my sound is set to my HDMI card as output but I don't have anything connected to my HDMI. It should be using my Intel HDA SB card which shows up as Azalia, not my Turks/Whistler HDMI audio. My system profiler & benchmark app sees both but I can't choose the Azalia from my Ubuntu sound settings. Audacity sees the ATI SB but it only gives me a Digital Audio option not the Analog option that I think is what works because my speakers aren't USB.


Edit 2: Relevant "Subdevice 0/1" line from terminal?

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Microphone [Yeti Stereo Microphone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


also...

alsa force-reload
gives
/sbin/alsa: 104: /sbin/alsa: cannot create /var/run/alsa/modules-removed: Permission denied

Is this a problem?


Edit3: I removed the Jack-related apps from the Software Center and when I restarted it gave me a KDE can't open something error related to pulseaudio. I'm pretty sure I'm using GNOME not KDE, so I don't know why that error happened. Could it be because something I installed switched me to KDE without knowing it? Here's the log of what I installed from Synpatic Package Manager 

Commit Log for Wed Dec  9 08:29:32 2015


Installed the following packages:
alsaplayer-common (0.99.80-5.1ubuntu1)
alsaplayer-gtk (0.99.80-5.1ubuntu1)
alsaplayer-jack (0.99.80-5.1ubuntu1)
guile-1.8 (1.8.8+1-8ubuntu3)
guile-1.8-libs (1.8.8+1-8ubuntu3)
jack-capture (0.9.71-1)
jack-mixer (9-3build1)
jack-stdio (1.4-1)
jackeq (0.5.9-2)
japa (0.8.4-1)
libbio2jack0 (0.9-2.1)
libclthreads2 (2.4.0-5)
libclxclient3 (3.9.0-1)
libmikmod2 (3.1.16-1)
libzita-alsa-pcmi0 (0.2.0-2)
libzita-resampler1 (1.3.0-2)
pulseaudio-module-jack (1:4.0-0ubuntu11.1)
pulseaudio-module-jack-dbg (1:4.0-0ubuntu11.1)
pulseaudio-module-lirc (1:4.0-0ubuntu11.1)
python-fpconst (0.7.2-5)
snd (11.7-3)
snd-gtk-jack (11.7-3)
swh-plugins (0.4.15+1-7)
vlc-plugin-jack (2.2.1~trusty1)
wah-plugins (0.0.2-2)
zita-ajbridge (0.4.0-1)
zita-mu1 (0.2.0-2)

Installed the following packages:
a2jmidid (8~dfsg0-1)
aj-snapshot (0.9.6-1)
alsa-firmware-loaders (1.0.27-2ubuntu3)
alsa-source (1.0.25+dfsg-0ubuntu4)
alsa-tools (1.0.27-2ubuntu3)
alsa-tools-gui (1.0.27-2ubuntu3)
aptitude (0.6.8.2-1ubuntu4)
aptitude-common (0.6.8.2-1ubuntu4)
build-essential (11.6ubuntu6)
debconf-utils (1.5.51ubuntu2)
debhelper (9.20131227ubuntu1)
dh-apparmor (2.8.95~2430-0ubuntu5.3)
dpkg-dev (1.17.5ubuntu5.5)
fakeroot (1.20-3ubuntu2)
fxload (0.0.20081013-1ubuntu1)
g++ (4:4.8.2-1ubuntu6)
g++-4.8 (4.8.4-2ubuntu1~14.04)
gnome-alsamixer (0.9.7~cvs.20060916.ds.1-5)
jack-tools (20101210-2.1)
libalgorithm-diff-perl (1.19.02-3)
libalgorithm-diff-xs-perl (0.04-2build4)
libalgorithm-merge-perl (0.08-2)
libasound2-plugins-extra (1.0.27-2ubuntu2)
libboost-iostreams1.54.0 (1.54.0-4ubuntu3.1)
libcdt5 (2.36.0-0ubuntu3.1)
libcgraph6 (2.36.0-0ubuntu3.1)
libcwidget3 (0.5.16-3.5ubuntu1)
libfakeroot (1.20-3ubuntu2)
libflowcanvas5 (0.7.1+dfsg0-0.2ubuntu2)
libfltk1.1 (1.1.10-17)
libglademm-2.4-1c2a (2.6.7-2ubuntu1)
libgvc6 (2.36.0-0ubuntu3.1)
libmail-sendmail-perl (0.79.16-1)
libmxml1 (2.7-1)
libpathplan4 (2.36.0-0ubuntu3.1)
libraul10 (0.8.0+dfsg0-0.1)
librubberband2 (1.8.1-4)
libstdc++-4.8-dev (4.8.4-2ubuntu1~14.04)
libsys-hostname-long-perl (1.4-3)
meterbridge (0.9.2-11)
module-assistant (0.11.6)
mudita24 (1.0.3+svn13-4)
multimedia-jack (0.2)
multimedia-tasks (0.2)
patchage (0.5.0+dfsg0-0.1)
po-debconf (1.0.16+nmu2ubuntu1)
qasconfig (0.17.2-2)
qastools-common (0.17.2-2)
qtractor (0.5.11-3)
tasksel (2.88ubuntu15)
tasksel-data (2.88ubuntu15)
vorbis-tools (1.4.0-1ubuntu3)

Installed the following packages:
mtp-tools (1.1.6-20-g1b9f164-1ubuntu2.1)
squeezelite (1.4-1)

---

### Post by JCopse on 2015-12-10
I eventually got sick of messing with it and decided to just install Ubuntu 15.10. Everything worked out of the box without having to add a single package. :)

---

