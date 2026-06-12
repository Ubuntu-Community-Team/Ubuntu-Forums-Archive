---
title: "Easycap DC60+ Sound Problem"
date: 2010-12-11
forum: Hardware
---

### Post by SteveDee on 2010-12-11
This relates to device: ID eb1a:2861 eMPIA Technology, Inc. which is supposed to be supported in recent kernels.

Due to enormous gaps in my understanding, I can't get the unit to produce sound when connected to a audio/visual source.
In addition, there seems to be a big difference between the 2 kernels tested on 'buntu 10.10.

As I have spent many hours experimenting, I'm now looking for someone who knows how the system works to explain a few things to me, rather than just trying further random tweaks.
 For example:-
    * what are the dsp and audio devices in /dev/ and which one contains the audio stream?
    * Is em28xx-alsa still required?
    * Are there other required modules that should be loaded when the Ezcap unit is plugged into the USB socket?
    * Have the interface methods changed between kernel 2.6.32-25 and 2.6.35-23, or are there serious bugs in the more recent kernel?

Here are some test details;

++++On kernel 2.6.32-25
I can view/record video without sound using mPlayer/mEncoder from a terminal.

The following devices are in /dev/ before connecting Ezcap:-
    * dsp
    * audio

Connecting the EzCap unit automatically adds the following devices in /dev/
    * video0
    * audio1
    * dsp1

I've tried using audio1 and dsp1 in the mEncoder command line, but neither works. However, when playing back my captured video in Movie Player, the properties view seems to show details for an audio stream:, for example-
MPEG1 audio, layer 3 (MP3), stereo, 44100Hz, bitrate=195kbs
Does this mean I have captured audio, but its just an empty stream?

I noticed that the em28xx-alsa module was not loaded, so tried loading em28xx-alsa like this:-
sudo modprobe em28xx-alsa...still no sound.

Also ran on another terminal:-
aplay /dev/dsp1
...which gave noise, but not the sound track.

Also ran alsamixer from terminal and set capture controls (which does include the capture control for Ezcap device).

using: arecord -l
shows eMPIA device.

++++On kernel 2.6.35-23
Before connecting Ezcap there are no dsp or audio devices in /dev/
After connecting, the only device added is video0
I can view video using mPlayer but cannot record anything using mEncoder

---

### Post by rmt1947 on 2010-12-14
Hi,

I'm not an expert on Linux audio and I have almost no experience of using the EasyCAP model DC60+ (USB ID eb1a:2861) in earnest, but I can tell you what little I know.

(1) The difference in behaviour between kernel 2.6.32 and 2.6.35 does not, I think, relate to the kernels themselves but rather to the way the kernel in Ubuntu 10.10 is configured by the people who package the distribution.  From Ubuntu release 10.10 onwards the kernel is configured to have no OSS capability at all.  This has been done as a deliberate act of policy:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/579300)

The special files /dev/audio1 and /dev/dsp1 are associated with the emulation of OSS by ALSA, and these will be absent when using Ubuntu 10.10 for the reason just stated.  If you use an earlier kernel such as 2.6.32 which has been built with OSS support configured you will see the two /dev/*.  Incidentally, though it's not important, I think /dev/dsp and /dev/audio are ALSA's emulation of OSS playback and capture on the computer's sound card. 

(2) The absence of OSS support in Ubuntu 10.10 is a problem for my easycapdc60 driver, which has up until now used OSS audio exclusively.  But it is irrelevant for the EasyCAP model DC60+, because the em28xx driver has always used true ALSA and does not require OSS.  (See more about this below.)

(3) An additional complication is that Ubuntu 10.10 enables PulseAudio by default.  PulseAudio is heavy (buffered) middleware which interposes itself between the userspace application (for example mplayer) and the ALSA layer.  The ALSA layer is in turn lightweight middleware positioned between the hardware and the device drivers for both capture and playback.  The result is that on Ubuntu 10.10 the path of the audio signal is something like

EasyCAP --> em28xx --> ALSA --> PulseAudio --> ALSA --> soundcard --> speakers

To save time, I omit at this point a rant on the plight of Linux audio.

(4) To obtain audio from the EasyCAP DC60+ the module em28xx-alsa must be loaded, but this ought to happen automatically - you should not need to load it manually using modprobe or insmod.  If the automatic load does not occur I think it means that the EasyCAP DC60+ has not been correctly recognized when it is plugged in and therefore the module-loading algorithms in the kernel have failed to conclude that the em28xx-alsa module is needed.

(5) To assist in the accurate recognition of the EasyCAP DC60+ it seems to be necessary to supply manually a "hint" when the em28xx module (not the em28xx-alsa module) is loaded:

modprobe em28xx card=n

where n is 35 according to post #154 at

[http://ubuntuforums.org/showthread.php?t=924504&page=16](http://ubuntuforums.org/showthread.php?t=924504&page=16)

n is 64 according to the definitions in source file em28xx-cards.c and n is 2 according to

[http://www.mail-archive.com/linux-media@vger.kernel.org/msg20489.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg20489.html)

I ought at some stage to go through the source code of the em28xx driver in order to see how the "card=n" logic works, but there always seems to be something more urgent to do  :-)

(6) Since the em28xx driver uses ALSA, it is necessary to supply ALSA device names to a program like mplayer if it is to read data from the EasyCAP DC60+, not OSS device names like /dev/audio1.  This is best explained by giving an example which works for my own driver with its nice new ALSA extension (as yet unreleased, awaiting final tests):

mplayer tv:// -tv driver=v4l2:norm=PAL:width=640:height=480:outfmt=uyvy:device=/dev/video0:input=0:fps=25:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.2,0:forceaudio:immediatemode=0 -hardframedrop -vo xv -ao alsa -msglevel all=9

The crucial numbers in an audio device specification such as "plughw.2,0" will depend on what audio hardware is present on your computer.  The appropriate numbers can be inferred from the output of the command `arecord -l`.  It helps to look in directories /proc/asound and /dev/snd when plugging and unplugging the EasyCAP in order to understand what is happening.

(7) I have had the pleasure of acquaintance with ALSA for no more than four weeks.  Some of the things confidently asserted above may be wrong.

Mike

---

### Post by SteveDee on 2010-12-16
> **rmt1947 said:**
> Hi,

I'm not an expert on Linux audio ...but I can tell you what little I know.



Many thanks for your help with this Mike, you seem to know quite a lot about this!

I've taken the simple route and have been experimenting by using arecord in a terminal with my analogue camera connected to the EzCap DC60+.

At the moment I can get sound by first doing this in a terminal:-
```

sudo rmmod em28xx
sudo modprobe em28xx card=2

```
...then opening Sound Preferences and ensuring the "2861 Analog Stereo" Input device level is high & not muted.
And then running:-
```

arecord -vv -fdat test.wav

```

The em28xx-alsa does not seem to be required.

I'm still struggling with mPlayer and the hwplug syntax.

The output from arecord -l includes:-
```

card 1: U0xeb1a0x2861 [USB Device 0xeb1a:0x2861], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

From this I'm guessing I should use hwplug:1,0 where "1" is the card number and "0" is subdevice? But perhaps you can enlighten me on this.

Anyway, at least I now have a way to get the sound working, so I just have to experiment some more with mPlayer & mEncoder arguments.

---

### Post by rmt1947 on 2010-12-16
Yes, I think your output from `arecord -l` implies you should be giving mplayer the clause

adevice=plughw.1,0

I believe a full stop must replace a colon in this string, because the mplayer command-line syntax reserves the colon as a clause separator.

I'm surprised that the em28xx-alsa module is not in use.  If it really does not appear anywhere amongst the output of the command

lsmod | grep em28xx

it must mean that some other module, snd_usb_audio perhaps, has taken over the EasyCAP's audio interface.  I didn't know that was possible.  (I only appear to know about this stuff because I've coincidentally been writing an ALSA driver for the other EasyCAP over the past few weeks.  I will have forgotten it all by New Year's Day - I hope.)

Mike

---

### Post by SteveDee on 2010-12-16
> **rmt1947 said:**
> ...I'm surprised that the em28xx-alsa module is not in use...

Just in case its of any interest, I've used "hardinfo" to create the 2 attached files (kernels 2.6.32-25 & 2.6.35-23).

Each shows the modules loaded before and after attaching EzCap, and then after "modprobe card=2".

---

### Post by rmt1947 on 2010-12-16
Thanks, that is indeed interesting.  At first glance it does seem that snd_usb_audio is doing the job.  Maybe it could do the same for the EasyCAP model DC60 if only I can manage to set things up correctly.  I'll investigate tomorrow.

Mike

---

### Post by rmt1947 on 2010-12-17
I did some tests today on a machine running Ubuntu 10.10, starting with an EasyCAP model DC60+ (USB ID eb1a:2861) following the procedure you described.  Without `rmmod em28xx; modprobe em28xx card=#` I get no sound, but with either card=2 or card=64 I do get sound.  After plugging in the EasyCAP, `ls -lart /dev/snd` gives

```
total 0
crw-rw----+  1 root audio 116,  2 2010-12-17 08:53 timer
crw-rw----+  1 root audio 116,  3 2010-12-17 08:53 seq
crw-rw----+  1 root audio 116,  6 2010-12-17 08:53 pcmC0D2c
crw-rw----+  1 root audio 116,  7 2010-12-17 08:53 pcmC0D1c
crw-rw----+  1 root audio 116,  4 2010-12-17 08:53 pcmC0D4p
crw-rw----+  1 root audio 116,  5 2010-12-17 08:53 pcmC0D3c
crw-rw----+  1 root audio 116, 10 2010-12-17 08:53 controlC0
crw-rw----+  1 root audio 116,  8 2010-12-17 08:54 pcmC0D0p
crw-rw----+  1 root audio 116,  9 2010-12-17 11:22 pcmC0D0c
drwxr-xr-x  20 root root     4300 2010-12-17 11:31 ..
crw-rw----+  1 root audio 116, 12 2010-12-17 11:31 controlC1
drwxr-xr-x   2 root root       80 2010-12-17 11:31 by-path
drwxr-xr-x   2 root root       60 2010-12-17 11:31 by-id
drwxr-xr-x   4 root root      300 2010-12-17 11:31 .
crw-rw----+  1 root audio 116, 11 2010-12-17 11:31 pcmC1D0c

```
and `ls /proc/asound` gives

```
card0  cards    hwdep  modules  seq     U0xeb1a0x2861
card1  devices  ICH5   pcm      timers  version
```

The module em28xx-alsa is not loaded.  After setting the GUI controls in the way you mentioned, I get good sound from the sequence of commands

```
arecord -t raw -f S16_LE -c 2 -r 48000 -D plughw:1,0 ./alsa.wav
aplay -f S16_LE -c 2 -r 48000 ./alsa.wav

```
and I get both video and audio from the command

```
mplayer tv:// -tv driver=v4l2:norm=PAL:width=640:height=480:outfmt=uyvy:device=/dev/video0:input=0:fps=25:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0 -hardframedrop -ao alsa
```

The audio from mplayer is perfect (to my ears) but the video is very jerky (zero entertainment value) on my test machine (3.06 GHz single-core x86 with 1GB RAM).  Disabling PulseAudio does not noticeably improve the video.

I then tried to repeat these tests with an EasyCAP model DC60 (USB ID 05e1:0408 ), using my easycapdc60 driver with its audio functionality disabled.  Although in these circumstances the snd_usb_audio module does acquire control of the EasyCAP's audio interface, it does not produces any sound:  I get the message  "arecord: pcm_read:1692: read error: Input/output error".  These tests are not relevant to the present thread, except in one respect:  If I re-enable the ALSA capability in the easycapdc60 driver and run mplayer with the model DC60 I get good sound _and_ good, smooth video.  I think I'm still overlooking something.

Mike

---

### Post by SteveDee on 2010-12-17
> **rmt1947 said:**
> 

...The module em28xx-alsa is not loaded....


I'm fairly sure the "[USB Audio]" bit in the output of arecord -l indicates it is using snd_usb_audio.

>   After setting the GUI controls in the way you mentioned, I get good sound from the sequence of commands

There must be another way to select the EzCap input, rather than using the Gnome-volume-control. I thought this should be possible via the "amixer" command but just can't see it (the reason I'm interested in this is that eventually I want to use this on Lubuntu not Ubuntu).
> 
...and I get both video and audio from the command

```
mplayer tv:// -tv driver=v4l2:norm=PAL:width=640:height=480:outfmt=uyvy:device=/dev/video0:input=0:fps=25:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0 -hardframedrop -ao alsa
```

The audio from mplayer is perfect (to my ears) but the video is very jerky (zero entertainment value) on my test machine (3.06 GHz single-core x86 with 1GB RAM).  Disabling PulseAudio does not noticeably improve the video.

I'm struggling with the mPlayer command line. On my laptop I need to include "-vo x11". It plays OK, but after stopping it, "arecord" does not work until I rmmod then modprobe again.
And on a desktop I've yet to get it to display video.

Re: your choppy video, did you check cpu%. I seemed to be running near 100% on laptop with 640x480. Its much better with 320x240.

---

### Post by rmt1947 on 2010-12-17
> There must be another way to select the EzCap input, rather than using the Gnome-volume-control. I thought this should be possible via the "amixer" command but just can't see it (the reason I'm interested in this is that eventually I want to use this on Lubuntu not Ubuntu).

I rebooted the machine and ran my mplayer command without any preceding manual action to select the input.  It worked:  jerky video plus good sound from the Easycap DC60+.  I terminated mplayer and ran `alsamixer` from a terminal window.  This brought up the AlsaMixer window, and I was apparently able to select the capture input via key F4, then F6.  But, as just mentioned, it seems unnecessary to do this provided the mplayer command explicitly specifies the input device.

> I'm struggling with the mPlayer command line. On my laptop I need to include "-vo x11". It plays OK, but after stopping it, "arecord" does not work until I rmmod then modprobe again.
And on a desktop I've yet to get it to display video.

I have Xvideo on my test machine and mplayer uses this by default.  If I force "-vo x11" it still works, though noticeably more video frames are dropped.  mplayer can be restarted after termination without difficulty.

> Re: your choppy video, did you check cpu%. I seemed to be running near 100% on laptop with 640x480. Its much better with 320x240.


On my machine there is no CPU overload.  When mplayer is delivering sound and jerky video at 640x480 the total CPU load is less than 25%, and the `top` utility shows that the principal contributors to this are

8%  mplayer
7%  Xorg
3.5%  pulseaudio

(These figures are not remarkable:  I get comparable CPU utilization with my easycapdc60 driver.)  If I run mplayer in silent mode:

```
mplayer tv:// -tv driver=v4l2:norm=PAL:width=640:height=480:outfmt=uyvy:device=/dev/video0:input=0:fps=25:noaudio -hardframedrop
```

the video is perfectly smooth.  So it seems that the snd_usb_audio module is supplying the audio stream to mplayer in a way which interferes with mplayer's processing of the video stream supplied by the em28xx module.

Mike

---

### Post by SteveDee on 2010-12-17
> **rmt1947 said:**
> I rebooted the machine and ran my mplayer command without any preceding manual action to select the input.  It worked...


Yes, I can run mPlayer (on laptop) without selecting the input via gnome-volume-control, and I can stop & restart it OK. But once mPlayer has been run, I can't then use arecord because there is no sound input.

When I first boot (& rmmod/modprobe) I can run arecord OK. And I've now found how to enable/disable capture.
In a terminal:-
```

amixer -c 1 sset Line Capture cap

```
...and...
```

amixer -c 1 sset Line Capture nocap

```
...where "-c 1" is the card number and "Line" is the control identity.

---

### Post by SteveDee on 2010-12-17
Mike, I don't know if this is relevant to your jerky video, but if I record using:-
```

mencoder tv:// -tv device=/dev/video0:input=1:norm=PAL-60:width=720:height=576:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0 -oac copy -ovc copy -o easySound

```
...and then play it back in an mPlayer based player (e.g. smplayer or Gnome Mplayer) its very jerky, probably 3 frames/sec.
But if I play back using VLC its very good!

---

### Post by rmt1947 on 2010-12-24
I tried your suggestion of mencoder capture followed by vlc playback, but it was unsuccessful on my test machine - the playback was jerky with both mplayer and vlc.  (I am running Ubuntu 10.10 on a 3.06 GHz single-core x86 machine with 1GB RAM and PulseAudio enabled, and using `sudo rmmod em28xx; modprobe em28xx card=64`.)  However, I found in subsequent experiments that I could get smooth video and good sound with vlc when run from the command line, and also with tvtime using sox for auxiliary audio processing.  My test results are as follows:


Jerky video:
```
mplayer tv:// -tv driver=v4l2:norm=PAL-BG:width=640:height=480:outfmt=uyvy:device=/dev/video0:input=0:fps=25:buffersize=16:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0 -hardframedrop -ao alsa -msglevel all=9
```

Jerky video in file easySound when played back with either mplayer or the vlc GUI:
```
mencoder tv:// -tv device=/dev/video0:input=1:norm=PAL:width=720:height=576:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0 -oac copy -ovc copy -o easySound 1>mencoder.out 2>mencoder.err

```

Smooth video and audio:
```
cvlc -vvv v4l2:///dev/video0:width=720:height=576 :norm=pal :input-slave=alsa://plughw:1,0 --demux rawvideo 2>vlc.err

```

Smooth video and audio:
```
(tvtime -d /dev/video0 -i 0 -n "PAL" 1>/dev/null 2>./tvtime.err) &
rc=1
while [ 0 -ne ${rc} ];
do
  tvtime-command run_command "(sox -c 2 -r 48000 -t alsa plughw:1,0 -s2 -c 2 -r 48000 -s2 -t alsa default 1>/dev/null 2>>./tvtime.err)" 1>/dev/null 2>>./tvtime.err
  rc=$?
  if [ 0 -eq ${rc} ]; then break; fi
  sleep 0.5
done
```


I conclude provisionally that:
(1) there is something wrong with the mplayer and mencoder command lines that we are using (or, alternatively and less probably, a problem in mplayer itself);  and
(2) the em28xx driver when used in conjunction with module snd_usb_audio is capable of giving good audio-video performance for the EasyCAP DC60+ (USB ID eb1a:2861).

Mike

---

### Post by celem on 2011-02-11
I just received my purchase of an EasyCap002 ( USB ID 05e1:0408 ). I loaded Mike Thomas' drivers from SourceForge. I am running Ubuntu 10.04. The install went without a problem. I tested the setup with Mike Thomas' test script - testNTSC.sh. I have not loaded any kernel modules. I get a good picture but the sound level is low and scratchy. I'll be looking into this a bit more over the next couple of weeks when time permits.

---

### Post by SteveDee on 2011-02-12
> **celem said:**
> I just received my purchase of an EasyCap002 ( USB ID 05e1:0408 )....

Hi, the 05E1 is a Syntek DC60 device, so you may get more help on this thread: [http://ubuntuforums.org/showthread.php?t=924504&page=18](http://ubuntuforums.org/showthread.php?t=924504&page=18)

It looks like some people have used different Card numbers with varying success.

---

