---
title: "No Sound Over HDMI"
date: 2012-09-14
forum: Hardware
---

### Post by bestdarncomputers on 2012-09-14
The problem that I am having is that I have a Zotac Nvidia GeForce8400 GS. Output VGS, DVI, HDMI. All of the outputs work videowise, but HDMI does not have audio. S/PDIF cable is connected from video card to MOBO. As you can see the device is not listed in aplay -l or aplay -L. I have seem other people with the same issues with these posts are a few years old and none seemt work with me.

Sound shows 
Digital Output (S/PDIF)
Headphones
Analog Output


AlsaMixer v 1.0.25
Have to unmute SPDIF each time i reboot, and it will not allow me to increase the volume of S/PDIF or S/PDIF D.


aplay -l 

derek@Ubuntu-Server:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L

derek@Ubuntu-Server:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=SB
    HDA ATI SB, ALC887-VD Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC887-VD Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC887-VD Digital
    Hardware device with all software conversions

Reckon the first step would be to get the device to appear on the aplay list correct? New to adding addition hardware, HDMI connection to tv from computer, as well as ubuntu 12.04.1.  I have found a number of posts that have similar issues but can't seem to get any of their fixes to work. Is there a link that someone has the can describe things step by step, that would be VERY helpful.

If you need any more info just ask I'll be glad to give you what you ask for.

I'm currently running Ubunut 12.04.10
MSI 760GM-P23 (FX) AMD Series Motherboard
Kingston 8GB DDR3 1333MHZ DIMM 2 x8GB - 16 GB total
AMD Phenom II X6 processor
Seagate 1TB Serial ATA HD 7200/32MB/SATA-6G
With one LG 24X DVDRW and one Lite ON 24X DVDRW Optical Drives
ZOTAC GeForce 8400 GS 1GB PCIe

---

### Post by BicyclerBoy on 2012-09-14
First some background:
audio over HDMI on the 8xxx & 9xxx geforce cards is pre-azalia S/PDIF only & only if the card is luck to have the input..
This audio is not intel HDA audio..

Some of the nVidia chipset graphics mobos (from that era) do support HDA.

So this means:
The audio comes from the mobo soundcard & is connected to the video card by s/pdif link. This link is one-way comms & does not support HDA or capability reporting (ELD/EDID/hot-plugging).
No HDMI device (codecs) show in aplay etc..
No HDMI events in dmesg.
No reported HDMI audio capability.

The audio device you use in this h/w arrangement is the mobo souncard s/pdif iec958 device.
You can only output stereo PCM & AC3/DTS as pass-thru'.

Try this in terminal:
speaker-test -l 2 -r 48000 -c 2 -D iec958

To test the AC3/DTS need to use mplayer/VLC etc..
vlc -aout alsa -alsa-device iec958
mplayer -ao alsa:device=iec958 -ac hwac3 test.ac3
and try to play media with AC3/DTS track..
(above cmds might not be exactly right..)

Most TVs should handle PCM & AC3.

---

### Post by bestdarncomputers on 2012-09-14
Well that answers a lot. Did not have a S/PDIF cable with the card when i got it, had to create my own till the company sends me a replacement that is a bit more up to specs. 

I will test what you said later tonight after the kids go to bed and I can have the living room tv back again.

Once again thank you for the information.

---

### Post by bestdarncomputers on 2012-09-15
Went through alsamixer and made sure the S\PDIF was not muted, which it often does mute itself form some reason. Changes the audio out to S\PDIF through the speaker settings.

> derek@Ubuntu-Server:~$ speaker-test -l 2 -r 48000 -c 2 -D iec958

speaker-test 1.0.25

Playback device is iec958
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.633509
 0 - Front Left
 1 - Front Right
Time per period = 5.973183
derek@Ubuntu-Server:~$ ^C

No Audio Out After this test.

Opened VLC, changes audio output module: ALSA audio output, checked Use S/PDIF when available, selected HDA ATI SB, ALC887-VD Digital IEC958 (S/PDIF) Digital Audio, saved and nothing there either. 

Attempted to play a DVD that I had ripped using PCM Codec.

In Movie Player, I changed the Audio Output Type to AC3 Passthrough, still nothing there.

> To test the AC3/DTS need to use mplayer/VLC etc..
vlc -aout alsa -alsa-device iec958
mplayer -ao alsa:device=iec958 -ac hwac3 test.ac3
and try to play media with AC3/DTS track..
(above cmds might not be exactly right..)

You're right these commands aren't exactly right. But I'll keep playing with them and see if I can't get them to work right.

---

### Post by BicyclerBoy on 2012-09-15
Can never remember the right vlc cmds ...
vlc --aout alsa --alsa-audio-device iec958 ??
vlc --aout=alsa --alsa-audio-device=iec958 ??


Are you sure your internal s/pdif cable is not reversed ?

Try
speaker-test -l 2 -c 2 -r 44100 -D iec958

---

### Post by bestdarncomputers on 2012-09-24
Okay so update.

After wasting a week of my life emailing Zotac the finally sent me a S/PDIF cable that should have been included with my card but was not. Got the cord in the mail the other day, plugged it in. flipped the TV input over and BOOM sound! Seems me homemade cord just wasn't cutting it but the OEM worked just fine.

---

