---
title: "Sony ATRAC3 decoder plugin for .rmj files"
date: 2008-10-03
forum: General Help
---

### Post by zorkerz on 2008-10-03
I have what I was lead to believe is a music album that contains .rmj files. 

Totem gives this error. 

> **An error occurred**
The playback of this movie requires a Sony ATRAC3 decoder plugin which is not installed.

Im not finding much about this. Has anyone run into files like this before? Is there any chance I will be able to find a decoder for them?

---

### Post by mdmcginn on 2009-06-07
One of my albums gives me that error message in Totem Movie Player (gstreamer). When Totem tries to search for suitable plugins, it comes back and says there aren't any. I was going to say that ATRAC3 is an inferior, proprietary format without Linux support, but the songs that give me that error will play for me using VLC Media Player and Gnome MPlayer. I don't know what other packages I installed that make that happen: maybe gstreamer good, bad and ugly.

---

### Post by hansdown on 2009-06-07
Hi mdmcginn.

Helix and mplayer are supposed to read this .

[https://answers.launchpad.net/ubuntu/+question/24855](https://answers.launchpad.net/ubuntu/+question/24855)

---

### Post by andrew.46 on 2009-06-08
Hi mdmcginn,

> **mdmcginn said:**
> One of my albums gives me that error message in Totem Movie Player (gstreamer). When Totem tries to search for suitable plugins, it comes back and says there aren't any. I was going to say that ATRAC3 is an inferior, proprietary format without Linux support, but the songs that give me that error will play for me using VLC Media Player and Gnome MPlayer. I don't know what other packages I installed that make that happen: maybe gstreamer good, bad and ugly.

I have had a look and certainly the svn MPlayer can play these files. I downloaded the following sample:

```
wget http://samples.mplayerhq.hu/A-codecs/ATRAC3/sample.ATRAC3.66kbps.44100Hz.Stereo.wav
```

and the svn MPlayer used ffatrc from libavcodec to decode:

```

andrew@skamandros~/Desktop$ mplayer sample.ATRAC3.66kbps.44100Hz.Stereo.wav 
MPlayer SVN-r29351-4.2.4 (C) 2000-2009 MPlayer Team

Playing sample.ATRAC3.66kbps.44100Hz.Stereo.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 66.1 kbit/4.69% (ratio: 8268->176400)
**[COLOR="Purple"]Selected audio codec: [ffatrc] afm: ffmpeg (FFmpeg Atrac 3 audio)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   4.1 (04.0) of 4.0 (04.0)  0.8% 

Exiting... (End of file)

```

There is also a windows codec available:

```

andrew@skamandros~$ mplayer -ac help | grep atrac

ffatrc      ffmpeg    working   FFmpeg Atrac 3 audio  [atrac3]
**[COLOR="Purple"]atrac3      acm       problems  Sony ATRAC3  [atrac3.acm][/COLOR]**

```

but as predicted above this external codec (-ac atrac3) crashed MPlayer completely :-).

Andrew

**Edit:** Mind you I could not found any such samples in Real Media Jukebox format...

---

### Post by zorkerz on 2009-06-09
Im still trying to get these files to play in rhythmbox. Anybody know how that might be done?

---

### Post by eugenevdm on 2010-04-10
Whilst trying to use Ubuntu One music store. After purchasing with Visa credit card Bob Marley tracks and trying to download a page that says:

Internet connection is required to access the music store

Please connect and reload.

"Reload" button.

Indeed I am connected. When pressing the button I get:

"No packages with the requested plugins found

The requested plugins are:

Sony ATRAC3 decoder"

Please assist.

---

