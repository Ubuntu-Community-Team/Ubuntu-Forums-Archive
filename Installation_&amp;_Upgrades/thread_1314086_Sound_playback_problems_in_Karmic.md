---
title: "Sound playback problems in Karmic"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by fantan on 2009-11-04
Hi for all helpful users!

I did a clean install of Karmic (9.10) on my desktop computer after the new version came out. After clean installation in the new system I got a lot of problems accoring to sound playback.
My configuration is as follows:
- motherboard: Asus
- processor: Intel(R) Pentium(R) 4 CPU 3.20GHz, 3199.901 MHz
- memory: 1 GB/666 Mhz
- HDD-s: SAMSUNG HD161HJ 140GB
	 Maxtor 6L080LO 80 GB
- Graphic video card: GeForce 7300 GS
- Sound card: CMI8738

On my computer I have four partitions. 
On 1. of them installed Linux Mint 7 Gloria (9.04) Hungarian
On 2. of them installed Linux Mint 7 Gloria (9.04) Russian
On 3. of them installed Kiwi Linux 9.04 with LXDE desktop
All three old systems use the same hardware and are working wery well, without any problem, especially according to sound and video possibilities.

I made a clean install of the new version (9.10 Karmic) on the 4. partition. Of course before installation I checked the md5sum of downloaded ISO file (ubuntu-9.10-desktop-i386.iso), checked the burned CD two times. The burned CD is without any defects and errors.

The istallation and the boot process went without problems.
The problems began when I tried to play an mp3 file with Rhytmbox. Rhytmbox has downloaded the needed codecs and other packages, after that the playback has a lot of problems. 
The playback starts well, but abruptly the sound gets stumble in one's play, cracks, and at the same time the processor load is 100% . In this case of course after some time the sound stops or the system totally freezes.
After that I downloaded and tested the sound playback with several downloaded players as well.

The afore mentioned situation happens again independently which program runs: audacious, qmmp, moc, exaile, amarok, mplayer, vlc, mpg123, mpg321, music123, etc. At last I uninstalled all other players and leaved just mplayer.
 
I tried a lot of setup variations in multimedia system setup: Pulseaudio, Alsa, OSS, the result is the same. I uninstalled the pulseaudio totally, but theese problems are abiding. I installed again the pulseaudio.

I did a comparison of the play of the same mp3 song in Linux Mint 7 Gloria and in the newly installed Karmic with own mplayers.
The result was as follows:

In the Linux Mint 7 Gloria:

"albert@Mint ~ $ MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Israel - Hava Nagila Hava.mp3.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback..."

--------------------------------------------------------------------------
In the Karmic:

"albert@Karmic:~/Zenék$ MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Israel - Hava Nagila Hava.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[B][I][pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440) [/I][/B]
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback..."
--------------------------------------------------------------------------

It seems the problem is in pulse in Karmic I think (or this is my mistake?):
"[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440" 

On the page [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440) I found:

"This is fixed now in [http://git.0pointer.de/?p=pulseaudio.git;a=commit;h=e61728e67a656c0bbd12b13bb4c1777d0e3163f4](http://git.0pointer.de/?p=pulseaudio.git;a=commit;h=e61728e67a656c0bbd12b13bb4c1777d0e3163f4)
Sorry for the long delay.
Make sure we don't get stuck when prebuf is too high"

And the fix on the [http://git.0pointer.de/?p=pulseaudio.git;a=commit;h=e61728e67a656c0bbd12b13bb4c1777d0e3163f4](http://git.0pointer.de/?p=pulseaudio.git;a=commit;h=e61728e67a656c0bbd12b13bb4c1777d0e3163f4) is as follows:

"If prebuf is greater than tlength minus minreq we might end up waiting
for the buffer to fill up further however without ever asking for more
data from the client since less minreq bytes might be missing.
This fixes bug #440"

OK!

I totally can't understand what is the fix, where and how it fixes the problem and what do I do.  

Can anybody help me, what and how to do, to really fix the sound playback problem in Karmic?

Thanks in advance!

Fantan

---

### Post by fantan on 2009-11-04
Nobody can help me?

fantan

---

### Post by Bunnybugs on 2009-11-04
This is a bug that much people experience...

Try: System>Administration>System Test

Do the sound test, and report a bug when asked..

You can also try this: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but this works for only one boot-session, maybe 2 if you are lucky

---

### Post by fantan on 2009-11-04
Thank you very much!
I'm not at my computer, but I'll try your suggestions later!

Thanks again!

fantan

---

### Post by Bunnybugs on 2009-11-04
Everyone is working on a solution for this problem, so I guess that it won take long anymore untill there is a fast/stable solution!

---

