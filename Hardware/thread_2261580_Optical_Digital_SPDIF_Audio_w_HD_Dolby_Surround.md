---
title: "Optical Digital S/PDIF Audio w/ HD Dolby Surround"
date: 2015-01-19
forum: Hardware
---

### Post by Panda_Stonetree on 2015-01-19
[SIZE=3]Greetings Everyone,

I have fiddled with Linux a few times in the past, and mainly while in college. I have recently decided to move from a Windows based gaming PC to Linux.  I am a Remote Hands Technition, so I can easily understand most of what I come across.  However this Sound issue is very much irritating me.

I love Gnome3, and don't want to switch to another desktop. I use Ubuntu Gnome 14.04.1 64-bit, as this is the only one that agrees with my "Sapphire HD 5750 1GB GDDR5 PCIE" video card using propiatary AMD drivers, otherwise I wont have 3D acceleration.

*I start with a fresh GPT partition table. Install using official Ubuntu Gnome Desktop x64 ISO. No additional options or packages installed. I then complete a full update/upgrade before attempting to troubleshoot.* [/SIZE]
```

$ sudo apt-get -y update
$ sudo apt-get -y upgrade
$ sudo apt-get -y dist-upgrade
$ sudo apt-get -y check
$ sudo updatedb && shutdown -r now

```





[HR][/HR]
[SIZE=3]_**Problems:**_[/SIZE]

**1.  Delayed Audio Start / Latency:**
I cannot hear system sounds due to audio start latency. When I test the audio channels L/R, I hear the voice clearly however it starts delayed. Instead of hearing *"Left Channel....Right Channel"*. I hear *"t Channel....Right Channel"*. I belive I have corrected this issue by disabling *"module-suspend-on-idle"* in the pulse audio configuration at */etc/pulse/default.pa* however this is only on PulseAudio.  Is there a way to acomplish this in ALSA? Basically I want to keep the Optic Lit and keep it active even when there is no sound.

**2.  System Sound UI Crashes:**
When using the Sound Controls located under System Settings:  This application seems to panic and crash. It starts fine and such, but when clicking on options under Sound Effects, it crashes the sound driver and i have to force restart ALSA using
```

$ sudo alsa force-reload
```
The application window also tends to grow in length when clicking on the sound effects, at which it always crashes and submits a bug report automatically. Im assuming all of this is somehow related to improper configuration or drivers.

**3. No Dolby Surround / HD:**
My system supports 8-channel HD Dolby Surround, but It's not working.  I have attempted to test for 8 channels, and most I can hear is 4.

**4. Volume level isn't saved. It's always maxed after boot:**
After boot, the volume level is always maxed out. When looking at the levels using System Sound, the sliders stays where I left it but the actual volume is maxed.  One tick on the slider corrects the volume, but only until I shutdown.






[HR][/HR]
 [SIZE=3]_**Attempted Troubleshooting Steps:**_[/SIZE]

I have spent over 3 weeks crawling through the internet looking for answers. I have also reviewed the official Ubuntu Sound community help at [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) .  While there is information out there that says it corrects my problems, nothing done has corrected my issues.

I have adjusted the following files to the indicated settings:

**/etc/pulse/default.pa**
This may have fixed my latency issue.
```
# load-module module-suspend-on-idle
```

**/etc/modprobe.d/alsa-base.conf**
This is supose to give me digital surround sound, but it seems to completely trash the audio. Even though all the proper inputs/outpus now appear, none of them actually play. If somehow I do get sound to play, ALSA quickly crashes.
```
options snd-hda-intel model=6stack-dig
```

**/etc/asound.conf**
I really havn't noticed anything with this. But I would like Optical to be default.
```

pcm.!default {
   type plug
   slave {
             PCM "iec958"
   }
}

```






[HR][/HR]
[SIZE=3]_**Basic Specs:**_[/SIZE]

Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
6.00GB Tripple-Channel DDR3 (8-8-8-20)

ASUS P6T6 WS Motherboard - [http://www.asus.com/Motherboards/P6T6_WS_Revolution/](http://www.asus.com/Motherboards/P6T6_WS_Revolution/)
- Intel® X58/ICH10R/NVIDIA NF200 Chipset
- Onboard AD2000B 8-Channel High Definition Audio CODEC (AD1989B Chipset - AD808 FiberChip)
- Digital Optical S/PDIF-output

Hauppauge WinTV HVR-1850 (Model 85xxx, Combo ATSC/QAM/FM/AM) - [http://www.hauppauge.com/site/support/support_hvr1800.html](http://www.hauppauge.com/site/support/support_hvr1800.html)
- 2x RCA Input
- 2x RF Digital/Analog Inputs
- 1x S-Video Connector

Sapphire HD 5750 1GB GDDR5 PCIE - [http://www.sapphiretech.com/presentation/product/product_index.aspx?pid=289&lid=1](http://www.sapphiretech.com/presentation/product/product_index.aspx?pid=289&lid=1)
- 1x HDMI

TurtleBeach PX51 - [http://www.turtlebeach.com/PX51](http://www.turtlebeach.com/PX51)
- Digital Optical S/PDIF-input

Ubuntu Gnome 14.04.1 64-bit
- Linux hive 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

ALSA Information -   [http://www.alsa-project.org/db/?f=2f678c3407b0ca5a0d9cdaed7781cfcc5fe111b9](http://www.alsa-project.org/db/?f=2f678c3407b0ca5a0d9cdaed7781cfcc5fe111b9)

PulseAudio 4.0





[HR][/HR]
[SIZE=3]If anyone can help me, it would be much appreciated.  If you need any additional information, let me know and I will get it as soon as I have a moment, which is normally after 3:00 PM MST (-7 GMT).[/SIZE]

---

