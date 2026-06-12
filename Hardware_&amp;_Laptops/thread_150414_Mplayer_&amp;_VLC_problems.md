---
title: "Mplayer &amp; VLC problems"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2006-03-26
Here's the problem:

My digital camera produces videos in a QuickTime format that is basically JPEG's strung toghether end-to-end. Xine plays this video (without sound and with a funky video, I think that it is interpreting sound data as video) at full speed, but Mplayer's audio skips, and the video lags. Is there an extra package that I can install to get this working?

I tried VLC, and it plays it good, but there's no sound! Is there a plugin for VLC to get sound with quicktime videos?

AAANd, both mplayer and vlc will play the _audio_ from a WMV file, but no video. What package would I need there (I know I need win32codecs, but I can't seem to find it in ubuntu)?

---

### Post by Perfect Storm on 2006-03-26
If you're on i386

```
 sudo gedit /etc/apt/sources.list 
```

add:
[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

save and exit.

```
sudo apt-get update
sudo apt-get install w32codecs
```

NB: This is illegal in the U.S.

---

### Post by enigma_0Z on 2006-04-05
Alright, I've got w32codecs installed, but I've still got another problem:

When I open quicktime videos from my camera, the video & audio is choppy... Additionally, I get this output:

```
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu6 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Failed to open /dev/rtc: No such file or directory (it should be readable by the user.)
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing 000_0159.MOV.
Quicktime/MOV file format detected.
--------------
MOV track #0: 206 chunks, 206 samples
Image size: 320 x 240 (24 bpp)
Display size: 320 x 240
Fourcc: jpeg  Codec: 'MOTION JPEG'
--------------
MOV track #1: 206 chunks, 0 samples
Audio bits: 8  chans: 1  rate: 11025
Fourcc: NONE
--------------
MOV: longest streams: A: #1 (206 samples)  V: #0 (206 samples)
VIDEO:  [jpeg]  320x240  24bpp  20.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, u8, 88.2 kbit/100.00% (ratio: 11025->11025)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
Building audio filter chain for 11025Hz/1ch/u8 -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 11025 Hz/1 channels/1 bpf/3763 bytes buffer/Unsigned 8 bit
AO: [alsa] 11025Hz 1ch u8 (1 bytes per sample)
Building audio filter chain for 11025Hz/1ch/u8 -> 11025Hz/1ch/u8...
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12
alsa-space: xrun of at least 0.144 msecs. resetting stream?,?% 0 0
alsa-space: xrun of at least 0.154 msecs. resetting stream?,?% 1 0
alsa-space: xrun of at least 0.159 msecs. resetting stream8.2% 2 0
alsa-space: xrun of at least 0.154 msecs. resetting stream5.8% 3 0
alsa-space: xrun of at least 0.152 msecs. resetting stream4.5% 4 0
alsa-space: xrun of at least 0.154 msecs. resetting stream3.7% 5 0
alsa-space: xrun of at least 0.154 msecs. resetting stream3.1% 6 0
alsa-space: xrun of at least 0.163 msecs. resetting stream2.7% 7 0
alsa-space: xrun of at least 0.156 msecs. resetting stream2.4% 7 0
alsa-space: xrun of at least 0.153 msecs. resetting stream2.2% 8 0
alsa-space: xrun of at least 0.154 msecs. resetting stream2.0% 9 0
alsa-space: xrun of at least 0.149 msecs. resetting stream1.8% 10 0
alsa-space: xrun of at least 0.153 msecs. resetting stream1.7% 11 0
alsa-space: xrun of at least 0.148 msecs. resetting stream1.5% 12 0
alsa-space: xrun of at least 0.147 msecs. resetting stream1.4% 13 0
alsa-space: xrun of at least 0.148 msecs. resetting stream1.3% 14 0
alsa-space: xrun of at least 0.145 msecs. resetting stream1.3% 15 0
alsa-space: xrun of at least 0.145 msecs. resetting stream2.9% 15 0
alsa-space: xrun of at least 0.143 msecs. resetting stream2.7% 15 0
alsa-space: xrun of at least 0.148 msecs. resetting stream2.5% 15 0
alsa-space: xrun of at least 0.149 msecs. resetting stream2.4% 15 0
alsa-space: xrun of at least 0.146 msecs. resetting stream2.2% 15 0
alsa-space: xrun of at least 0.144 msecs. resetting stream2.1% 15 0
alsa-space: xrun of at least 0.145 msecs. resetting stream2.0% 15 0
alsa-space: xrun of at least 0.151 msecs. resetting stream1.9% 15 0
alsa-space: xrun of at least 0.148 msecs. resetting stream1.8% 15 0
alsa-space: xrun of at least 0.156 msecs. resetting stream1.7% 15 0
A:   9.2 V:  10.2 A-V: -1.034 ct: -0.383 206/206  7%  0%  1.7% 15 0
alsa-uninit: pcm closed
```

I tried to play the video in vlc, and the video plays fine, but without any sound at all! Is there something I'm just missing?

---

### Post by Perfect Storm on 2006-04-05
Hmmm...you could try some diffrent things.

Before starting running the quicktime video do:
```
killall esd
```

or try change sound driver in VLC:
```
wxvlc
``` 
then press <ctrl>+<s> 
Remember to select 'advanced options' (right lower corner).
Then try diffrent options in Audio ---> Output Modules in VLC.

-------
How about other multimedia formats? Are they playing well? Do you have sound on Ubuntu and only got problems with your camera quicktime format? Is it possile to save it as another format?

---

