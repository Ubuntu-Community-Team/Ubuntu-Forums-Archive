---
title: "DVD playback problems"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by s_p_a_r_k_y on 2005-04-17
I'm having trouble getting DVDs to play. I have mplayer, ogle, vlc, gxine, and xine installed.
I have the linux kernel 2.6.10-5-386 installed...I didn't compile it myself.

Mplayer craps out when I try mplayer dvd://
```
 
mplayer dvd://
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



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
Playing dvd://.
libdvdread: Using libdvdcss version 1.2.5 for DVD access
Reading disc structure, please wait...
There are 23 titles on this DVD.
There are 13 chapters in this DVD title.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001ffa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000087e2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000087e2)!!
libdvdread: Elalibdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0035b6e6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00395ad4
libdvdread: Elapsed time 1
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 1
DVD successfully opened.
Cache fill:  0.00% (0 bytes)    MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8771.6 kbps (1096.5 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 24000->192000 (192.0 kbit)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
==========================================================================
vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG 1 or 2 (libmpeg2))
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
AO: [oss] 48000Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
Building audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

xine gives starts the DVD menu of the DVD, but when I click on play in the menu I get this xine error
```
The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g: not disc in drive). Error reading NAV packet:"

```

I installed hoary on my friends computer and he gets the same thing, so I don't think its just my laptop. However his xine doesn't crash when he hits play, he can watch about 5 minutes but when he skips ahead more than that it gives the same error as above. The DVD works on my mythbox which is a 2.4 kernel.

Is this a kernel issue with the ubuntu hoary and reading DVDs or what seems to be the problem?

---

### Post by brickbat on 2005-04-17
Hi,

I can play dvds fine - just not in mplayer.  I tried installing it and after half a day I got it installed but couldnt get dvd playback.

I installed instead xine and totem xine and i can watch dvds perfectly in totem.  Also i installed kubunu and can watch them with Amarok as well.

mplayer and Ubuntu seem to have irreconcilable differences.

ciao
bb

---

