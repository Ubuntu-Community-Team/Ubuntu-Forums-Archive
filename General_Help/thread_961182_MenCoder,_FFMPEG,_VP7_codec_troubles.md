---
title: "MenCoder, FFMPEG, VP7 codec troubles"
date: 2008-10-28
forum: General Help
---

### Post by iSlayter on 2008-10-28
Hello everybody.

I've got a problem. On my web-server stores 250 Gb of videos encoded with codec **VP7**.

Now I must:

[LIST]
[*] Re-encode videos with xvid.
[*] Take screenshots in GIF format from 10 frames.
[*] Place watermark from transperent GIF
[/LIST]

Initially I wanna use FFMPEG, but when I install it I get error while encoding because he doesn't understand input codec. And also I know that getting screenshots is very slowly in FFMPEG (for screenshot at 30 minute it takes 52 seconds). So I decide to try Mplayer. But he is not support watermarks at all.

AFAIR VP7 is part of Intel Indeo codecs which versions above 3.0 doesn't supported in any opensource project.

Then I find rather interesting lines at [http://www.mplayerhq.hu/design7/info.html](http://www.mplayerhq.hu/design7/info.html)
> # Intel Indeo3 (3.1, 3.2)
# Intel Indeo 4.1 and 5.0 (using x86 DLL or XAnim codecs)

Then when I install mplayer and try to use it I've got another error:

> root@Ubuntu-804-hardy-LTS-64-minimal:/www/pages/klipz.ru/1# mencoder test.avi -o test2.avi -of lavf   -ovc xvid
MEncoder 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

success: format: 0  data: 0x0 - 0x0
Seek failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

What's wrong with it? :((((

---

### Post by geirha on 2008-10-28
Have you installed the [w32codecs](apt://w32codecs) package from the [medibuntu repository](http://www.medibuntu.org/)?

---

### Post by cordel on 2008-10-28
My guess is that you have not installed the required dll as it lists. This will likely need to be run under wine as well to have use of the dll or run on ms machine. Might check the mplayerhq.hu faq, I seen a hint about this there I think.

---

### Post by iSlayter on 2008-10-28
> **geirha said:**
> Have you installed the [w32codecs](apt://w32codecs) package from the [medibuntu repository](http://www.medibuntu.org/)?

Sorry, I'm very newbie :(
I try to do it this way:
> root@Ubuntu-804-hardy-LTS-64-minimal:~# apt-get install w32codecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

How I can change repository server on other from ssh?
Before tuning server I already use Ubuntu as a Desktop but install everything with synaptic. Not manually :(

---

### Post by geirha on 2008-10-28
The medibuntu link I provided has instructions on how to add the medibuntu repository (Repository Howto). After it is added, running apt-get install w32codecs should work as expected.

---

### Post by iSlayter on 2008-10-28
> **geirha said:**
> The medibuntu link I provided has instructions on how to add the medibuntu repository (Repository Howto). After it is added, running apt-get install w32codecs should work as expected.

Thanks! I try to follow manual at link you provided but now I get same error.

> root@Ubuntu-804-hardy-LTS-64-minimal:~# apt-get install w32codecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package **w32codecs is not available**, _but is referred to by another package_.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: **Package w32codecs has no installation candidate**


**BTW** how can I get list of packages by PCRE (for example "/w32codesc(.*)/i"?

---

### Post by geirha on 2008-10-28
> **iSlayter said:**
> Thanks! I try to follow manual at link you provided but now I get same error.


You need to run ```
sudo apt-get update
# or
sudo aptitude update
```

To download the package lists first. Forgot to mention that.
> **iSlayter said:**
> 
**BTW** how can I get list of packages by PCRE (for example "/w32codesc(.*)/i"?

aptitude search accepts regular expressions

```
aptitude search '^w[0-9]+codecs$'
```

This is documented in /usr/share/doc/aptitude/

---

### Post by iSlayter on 2008-10-28
w32codecs unexist becaus ubuntu installed - x64.

Already install w64codecs but it doesn't help.

> root@Ubuntu-804-hardy-LTS-64-minimal:/www/pages/klipz.ru/1# mencoder test.avi -o test2.avi -of lavf -ovc xvid
MEncoder 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Step                                 ping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

success: format: 0  data: 0x0 - 0x0
Seek failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...


Why this error ocures again and again? :(

[http://ubuntuforums.org/showthread.php?t=502179](http://ubuntuforums.org/showthread.php?t=502179) here I find the same problem but mencoder show error when I try to use key
> -xvidencopts

---

### Post by geirha on 2008-10-28
Try running update-manager, it should give you an update on mencoder since the medibuntu has it's own version of mencoder as well. Might be needed to use those w64codecs.

---

### Post by iSlayter on 2008-10-28
> **geirha said:**
> Try running update-manager, it should give you an update on mencoder since the medibuntu has it's own version of mencoder as well. Might be needed to use those w64codecs.

Sorry again but how I can update mencoder? I type "apt-get install mplayer" and it downloads near 53mb of something. Then I try command:
> **mencoder test.avi -o test_converted.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=1:vbitrate=1800 -ffourcc XVID**

MEncoder 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

success: format: 0  data: 0x0 - 0x0
Seek failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...


How I can use those 64 win codecs?

---

### Post by iSlayter on 2008-10-28
ouch shittttt. I try all of it on empty file :lolflag:

now..
> root@Ubuntu-804-hardy-LTS-64-minimal:/www/pages/modesco/letsmoto.com/klipz.ru/1# mencoder 232.avi -o test_converted.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=1:vbitrate=1800 -ffourcc XVID
MEncoder 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

success: format: 0  data: 0x0 - 0x148ad2
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [VP70]  768x576  24bpp  25.000 fps  1887.3 kbps (230.4 kbyte/s)
[V] filefmt:3  fourcc:0x30375056  size:768x576  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Requested video codec family [vp7] (vfm=vfwex) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x30375056.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...
[email]root@Ubuntu-804-hardy-LTS-64-minimal:/www/pages/modesco/letsmoto.com/klipz.ru[/email]/1#



---

### Post by highgeere on 2008-10-28
I ran into the same error after attempting a conversion per [http://ubuntuforums.org/showthread.php?t=502179](http://ubuntuforums.org/showthread.php?t=502179) .

"Requested video codec family [vp7] (vfm=vfwex) not available."

 Obviously that codec is not available; that's why I'm trying to convert the file! Anyone have any thoughts about getting around this? The poster from the above-linked thread didn't have any problems with it, so why am I? I am also running AMD64, so perhaps that is related.

---

### Post by iSlayter on 2008-10-28
already try to look at [ftp://mplayerhq.hu/MPlayer/releases/codecs/](ftp://mplayerhq.hu/MPlayer/releases/codecs/)
1. wget [ftp://mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2](ftp://mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2)
2. tar -rf all-20071007.tar.bz2
3. mv * /usr/lib/codecs/ (directory with codecs)

but an error has occured again :(

---

### Post by JowCG on 2009-02-27
This is an old topic, but I have a question, I can run videos on VP7 in Gnome MPlayer, but I can't in Totem. This is not a problem, I don't use the Totem, just wanted to know why it doesn't work.

---

### Post by Mr_Bumpy on 2009-06-18
Good question.  I know MPlayer installed from [Medibuntu]("http://www.medibuntu.org/") also plays VP70 files, FWIW.

---

### Post by andrew.46 on 2009-06-18
Hi Mr_Bumpy,

> **Mr_Bumpy said:**
> Good question.  I know MPlayer installed from [Medibuntu]("http://www.medibuntu.org/") also plays VP70 files, FWIW.

I believe MPlayer uses an external codec to play vp7 files:

```

andrew@skamandros~$ mplayer -vc help | grep vp7
vp7         vfwex     working   On2 VP7 Personal Codec  [**[COLOR="Purple"]vp7vfw.dll[/COLOR]**]

```

Can Totem source external windows codecs?

Andrew

---

### Post by sazawal on 2012-03-14
I have downloaded mplayer from medibuntu and it seems that vp7 codec is already installed. But my file with vp7 codec is not not showing the video. Although the audio is working fine. Here is the output of the command

```
$ mplayer -vc help | grep vp7
vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]
```And here is the terminal output when I tried to play my file (.ogm format) with mplayer

```
$ mplayer blues.ogm 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing blues.ogm.
libavformat file format detected.
[ogg @ 0x1598a20]max_analyze_duration reached
[lavf] stream 0: video (unknown), -vid 0
[lavf] stream 1: audio (vorbis), -aid 0
VIDEO:  [VP70]  640x352  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
SUB: Added subtitle file (1): ./blues.srt
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
**Requested video codec family [vp7] (vfm=vfwex) not available.**
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x30375056.
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8000->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   3.6 (03.5) of 5566.3 ( 1:32:46.3)  0.4% 

MPlayer interrupted by signal 2 in module: play_audio
A:   3.8 (03.7) of 5566.3 ( 1:32:46.3)  0.4%
```

I am using 64-bit ubuntu 10.10. I guess the reason could be my 64-bit architecture. Have you guys tried out with 64-bit linux?

---

