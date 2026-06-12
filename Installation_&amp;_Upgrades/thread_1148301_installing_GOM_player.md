---
title: "installing GOM player"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2009-05-04
I user GOM player in windows and do not want to use it through Wine...
I want to install it in 9.4 and hence tried the following

 sudo apt-get -y install gstreamer*


but got the following error..


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting gstreamer0.10-ffmpeg-full for regex 'gstreamer*'
Note, selecting gstreamer0.10-alsa for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-audiosink for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad-doc for regex 'gstreamer*'
Note, selecting gstreamer-tools for regex 'gstreamer*'
Note, selecting gstreamer0.10-x for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-fluendo-mpegdemux for regex 'gstreamer*'
Note, selecting bluez-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-doc for regex 'gstreamer*'
Note, selecting libgstreamer0.10-0 for regex 'gstreamer*'
Note, selecting gstreamer0.10-packagekit for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse for regex 'gstreamer*'
Note, selecting libgstreamer0.10-ruby for regex 'gstreamer*'
Note, selecting libgstreamer-plugins-base0.10-dev for regex 'gstreamer*'
Note, selecting gstreamer-dbus-media-service for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad-multiverse for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-really-bad for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-good for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins for regex 'gstreamer*'
Note, selecting gstreamer0.10-audiosource for regex 'gstreamer*'
Note, selecting ultrastar-ng-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-ffmpeg for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-farsight for regex 'gstreamer*'
Note, selecting libghc6-gstreamer-dev for regex 'gstreamer*'
Note, selecting gstreamer0.10-pitfdll for regex 'gstreamer*'
Note, selecting gstreamer0.10-videosink for regex 'gstreamer*'
Note, selecting kaffeine-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-lame for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse instead of gstreamer0.10-lame
Note, selecting gstreamer0.10-plugins-good-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-doc for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-good-doc for regex 'gstreamer*'
Note, selecting gstreamer0.10-pulseaudio for regex 'gstreamer*'
Note, selecting gstreamer0.10-visualization for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-good instead of gstreamer0.10-visualization
Note, selecting phonon-backend-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad-multiverse-dbg for regex 'gstreamer*'
Note, selecting totem-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-bad for regex 'gstreamer*'
Note, selecting gstreamer0.10-nice for regex 'gstreamer*'
Note, selecting gstreamer0.10-doc for regex 'gstreamer*'
Note, selecting gstreamer0.10-fluendo-mp3 for regex 'gstreamer*'
Note, selecting gstreamer0.10-esd for regex 'gstreamer*'
Note, selecting gstreamer0.8-tools for regex 'gstreamer*'
Note, selecting libgstreamer0.10-ruby1.8 for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base-apps for regex 'gstreamer*'
Note, selecting gstreamer-codec-install for regex 'gstreamer*'
Note, selecting gstreamer0.10-fluendo-mpegmux for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-ugly-multiverse-dbg for regex 'gstreamer*'
Note, selecting libgstreamer-perl for regex 'gstreamer*'
Note, selecting libgstreamer0.10-dev for regex 'gstreamer*'
Note, selecting gstreamer0.10-sdl for regex 'gstreamer*'
Note, selecting gstreamer0.10-gnomevfs for regex 'gstreamer*'
Note, selecting gstreamer0.10-plugins-base for regex 'gstreamer*'
Note, selecting gstreamer0.10-videosource for regex 'gstreamer*'
Note, selecting libgstreamer-plugins-base0.10-0 for regex 'gstreamer*'
Note, selecting gstreamer0.10-gnonlin for regex 'gstreamer*'
Note, selecting gstreamer0.10-tools for regex 'gstreamer*'
Note, selecting gstreamer0.10-gnonlin-dbg for regex 'gstreamer*'
Note, selecting gstreamer0.10-schroedinger for regex 'gstreamer*'
Note, selecting libgstreamer0.10-0-dbg for regex 'gstreamer*'
Note, selecting deejayd-gstreamer for regex 'gstreamer*'
Note, selecting gstreamer0.10-gnonlin-doc for regex 'gstreamer*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-bad: Conflicts: gstreamer0.10-fluendo-mpegdemux but 0.10.15-1 is to be installed
                             Conflicts: gstreamer0.10-fluendo-mpegmux but 0.10.4-1 is to be installed
E: Broken packages



Please help me!!
Thanks!!

---

### Post by canadiandude007 on 2009-05-04
Can I ask why you want to use GOM player?

I would advise firstly to install the restricted format components:

> sudo apt-get install ubuntu-restricted-extras

I would see here for more information about this:

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

If you explain why you would like to use GOM, then perhaps we can assist further.

---

### Post by richlyn9 on 2009-05-04
i guess i am confused....
Gstreamer and GOM player are two differrent things..:lolflag:


But I don't like that i cannot forward other video formats in VLC so what's a better option?

---

### Post by richlyn9 on 2009-05-04
> **canadiandude007 said:**
> Can I ask why you want to use GOM player?

I would advise firstly to install the restricted format components:



I would see here for more information about this:

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

If you explain why you would like to use GOM, then perhaps we can assist further.

i use VLC in ubuntu and of late i see that i cannot foward a movie to play from the location i left it yesterday   then i used GOM which has better features and plays all formats hence the choice.

---

### Post by infinitejones on 2009-05-04
Try using Movie Player (applications -> sound & video -> movie player) - that tends to be a bit better at letting you move forward through a video file, when vlc has problems.

---

### Post by lovinglinux on 2009-05-04
GOM player is great, but I don't think you will be able to use it. I tried, but was a no go.

I would recommend VLC and smplayer.

---

### Post by spiralx on 2009-06-28
I have just tried Movie Player on "The Golden Compass", and got nowhere.  Having piled through a libdvdread4 install using Synaptic, followed by Terminal command for libreadcss2, PLUS an Ubuntu restricted media codec addition, I've had enough for now.

Ubuntu ain't good at playing DVD's.  Another reason the unwashed masses will stick with Windows.

---

### Post by lovinglinux on 2009-06-28
> **spiralx said:**
> I have just tried Movie Player on "The Golden Compass", and got nowhere.  Having piled through a libdvdread4 install using Synaptic, followed by Terminal command for libreadcss2, PLUS an Ubuntu restricted media codec addition, I've had enough for now.

Ubuntu ain't good at playing DVD's.  Another reason the unwashed masses will stick with Windows.

Follow the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683).

---

### Post by mathewd on 2010-03-04
I have some .k3g files (cell phone video files) that I'd like to play on my Ubuntu machine. VLC doesn't seem to support them (so says the error message I get) but does yield some choppy video without the audio portion.

Is there a means in Ubuntu to play these .k3g files? Thanks much for any help ^_^

---

### Post by richlyn9 on 2010-03-10
> **mathewd said:**
> 
Is there a means in Ubuntu to play these .k3g files? Thanks much for any help ^_^

Sorry for replying late(its an old thread and lo longer visited)
in future if you have any issues open a new thread and post your query.
Posting in old threads may never get you an answer.

Coming to your question.
i haven't myself come across .k3g files but GOM should be able to play them (according to this link [http://extension.informer.com/k3g/](http://extension.informer.com/k3g/) )

---

