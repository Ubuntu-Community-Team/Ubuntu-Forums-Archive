---
title: "x264 x264HP mplayer vlc"
date: 2005-12-05
forum: General Help
---

### Post by bruno on 2005-12-05
Hello,
I try to find a way to play some avi file with these codecs.
Example of video
here :  [http://www.vsofts.com/h264/clips_d1.html](http://www.vsofts.com/h264/clips_d1.html)
or here : [http://www.leadcodecs.com/Download/H264-Videos.htm](http://www.leadcodecs.com/Download/H264-Videos.htm)

I google and can't find answer, is it possible or not to play these file on linux?

vlc doesn't play at all or bab image.
and mplayer no image and this kind of log 

[I][I]mplayer CarelessEnglish_720x352_Q23.avi
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 8, Stepping: 1)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing CarelessEnglish_720x352_Q23.avi.
AVI: Missing video stream!? Contact the author, it may be a bug :(
Ogg stream 0 has a header marker but is of an unknown type
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libvorbis] Ogg/Vorbis audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 64.2 kbit/4.18% (ratio: 8020->192000)
Selected audio codec: [vorbis] afm:libvorbis (OggVorbis Audio Decoder)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bps)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Video: no video
Starting playback...
A:   2.5 (02.5)  0.7% 85%

MPlayer interrupted by signal 2 in module: play_audio
alsa-uninit: pcm closed[/I]
[/I]

**I try to force to use different codec, with these codecs =**
[I]
mplayer -vc help | grep 264

ffh264      ffmpeg    working   FFmpeg H.264  [h264]
vssh264     vfw       working   VSS H.264  [vssh264.dll][/I]


But it doesn't work too.
*mplayer -vc ffh264 file.avi*

Is it a solution under linux to play these kind of files ?

tks for any kind of help

Bruno

---

### Post by CompShrink on 2006-02-07
I don't know if you're still trying, it's been 2 months since your post, but incase you're still looking, or someone else has this issue:

If you install totem-gstreamer (default for breezy) and gstreamer-ffmpeg (in breezy repositories), then you can play x264 (aka h264). BUT, I have a lot of audio/video sync issues with this. I hear this is largely fixed in gstreamer 0.10, but Dapper is NOT stable, I wouldn't try using packages from there.

What I have found to work really well is:

[http://ubuntuforums.org/showthread.php?t=85190](http://ubuntuforums.org/showthread.php?t=85190) these builds of MPlayer (they're .deb files, so just open a terminal and use dpkg -i /DOWNLOADED/PATH/mplayer_1.0cvs_i386.deb )

Only issue I have with it is 1 dependancy conflict, because I'm using CVS libfaac0, otherwise those should work fine.

I use the one that the user mentioned is compiled on a p3 with SSE and MMX, it's a pretty good base level, as anyone using under a p3 will probably not be able to play decent looking x642 anyway, as it takes more processor speed than xvid/divx etc.

That mplayer also plays MKVs with softsubtitles, which I couldn't get Totem to do.

How this helps someone.

---

