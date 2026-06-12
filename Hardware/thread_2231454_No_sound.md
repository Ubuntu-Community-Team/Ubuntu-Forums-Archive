---
title: "No sound"
date: 2014-06-25
forum: Hardware
---

### Post by vmweenie on 2014-06-25
ETA: The soundcard IS enabled in BIOS. 

Brand new homebuilt machine, MSI MS-7721 w/ AMD A8-6600K APU with Radeon(tm) HD Graphics. Ubuntu 13.10 kernel 3.11.0-23-generic.  Pulled my hair out trying to get the Realtek USB WiFi working. Now with not getting sound working I have no hair left.  

So [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) says 
[CENTER]Warning **As of 2012, much of the information on this page is outdated. Please refer to the official sound debugging guide and Ubuntu Audio Development team's pages for more up-to-date information.**[/CENTER] 

Ruh roh!  Okay, we go to [the official sound debugging guide]("https://wiki.ubuntu.com/DebuggingSoundProblems").  That tells me to make sure I have the latest alsa drivers so I go to yet another page [wiki.ubuntu.com/Audio/UpgradingAlsa]("https://wiki.ubuntu.com/Audio/UpgradingAlsa")  which says:[I]Make sure you only have one override of ALSA drivers installed at a time. Make sure you uninstall the previous override before trying a new one, otherwise it is unclear which version will take precedence. 
[/I] I have no idea what that means. Okay back to the referring page which then sends me to [wiki.ubuntu.com/Audio/HDAGeneric]("https://wiki.ubuntu.com/Audio/HDAGeneric")  I follow the instructions:
```
Erewhon:~$ grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: ATI ID aa01
/proc/asound/card1/codec#0:Codec: Realtek ALC887-VD

```  
According to that page, the "ATI ID aa01" is not supported while the Realtek is.  OK.  Plodding on I'm sent to alsaproject.org. Now at this point I can'tdecie whether I'm in the Garden of Forking Paths or the Minotaur's labyrinth.  Whatever, I want some sound! So here I am at alsaproject.org. I follow a link [Is my soundcard supported]("http://www.alsa-project.org/main/index.php/Matrix:Main")  I don't see any Realtek listing so I hit the Intel listing but I have no idea what I'm looking at/for. Okay then, let's go to   
[/URL] [ alsaproject.org SoundcardTesting]("http://www.alsa-project.org/main/index.php/SoundcardTesting") which instructs me to ```
aplay -vv /usr/share/sounds/alsa/Noise.wav 
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
ALSA <-> PulseAudio PCM I/O Plugin
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 24000
  period_size  : 6000
  period_time  : 125000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 6000
  period_event : 0
  start_threshold  : 24000
  stop_threshold   : 24000
  silence_threshold: 0
  silence_size : 0
  boundary     : 6755399441055744000
##### +                                            | 10%
```. 
Umm, okay? but not a single peep was heard.        

*whines softly*  
At this point I don't know where I am much less where I've been.  Some of the other things I did, recommended at various pages far and wide aross the great interwez.  

```
Erewhon:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ID aa01 Digital [ID aa01 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Gee. At this point I will mention that in the BIOS(UEFI) I can see where the speakers are plugged in, whether front or back so I'm pretty sure I got the harnesses and jumpers and stuff in their right places. Sowatch what happens when I move my (known good) speakers from the rear jack to the front headphone jack
[IMG]http://i.imgur.com/T7hy4La.png[/IMG]  

[IMG]http://i.imgur.com/DcqZtwl.png[/IMG]

So alsamixer is detecting the speakers.  

Following the advice of various people far and wide across teh great interwebz I did some other stuff.  So here are some screen caps: 
pavucontrol:  [IMG]http://i.imgur.com/CYQWf5A.png[/IMG] 
[IMG]http://i.imgur.com/G8zzuqR.png[/IMG]   
[IMG]http://i.imgur.com/C3mAUe8.png[/IMG]
At some point I was told to ```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
``` which output a shitton of info.  I have no idea what the relevant parts are. Then I saw to do 

```
Erewhon:~$ LC_ALL=C cat /proc/asound/card*/codec#* | LC_ALL=C fgrep --before-context=4 --after-context=1 "Subsystem Id" 
Erewhon:~$ LC_ALL=C lspci -vvnn | LC_ALL=C fgrep --after-context=1 "Audio device" 

00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7721]
--
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:d721]
```  


Which looks familiar but says different stuff than the above. 

From elsewhere I tried ```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` and added the following line at the end of the file:

```
options snd-hda-intel model=generic
```  

Still no sound. How about options snd-hda-intel model=ALC887-VD?  Nope.  

Of course at various times I've ```
 sudo alsa force-reload
``` and rebooted at times but still nothing. 

 

I'M DYING HERE! HALP!

---

### Post by Yellow Pasque on 2014-06-25
First off, undo any customizations you performed to /etc/modprobe.d/alsa-base.conf and then force-reload.
Next, give the ALSA info (upload it and give the link).

Also, see: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

> According to that page, the "ATI ID aa01" is not supported while the Realtek is. OK
If you run 'sudo update-pciids' then aa01 may be replaced with a human-readable name.

---

### Post by vmweenie on 2014-06-25
> **Temüjin said:**
> First off, undo any customizations you performed to /etc/modprobe.d/alsa-base.conf and then force-reload.

Done. 

> 
Next, give the ALSA info (upload it and give the link).


Done.  [http://www.alsa-project.org/db/?f=0a4a50e6734dd0f02d94b1543f756b99ea80204a](http://www.alsa-project.org/db/?f=0a4a50e6734dd0f02d94b1543f756b99ea80204a)

> 
Also, see: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

That info ought to be put in a stickied thread right here!  With credit due of course.    

> 
If you run 'sudo update-pciids' then aa01 may be replaced with a human-readable name.

Done. No change.   

Thank you!

---

### Post by sp40140 on 2014-06-29
I have HD7770 vid card. HDMI audio didn't work. the Kernel has it disabled. The only way to fix it was to upgrade to kernel 13.4 or better and use OpenGL drivers. It worked for me.
It might work for you.

Cheers,

---

