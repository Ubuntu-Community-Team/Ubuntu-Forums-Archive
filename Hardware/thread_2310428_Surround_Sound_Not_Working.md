---
title: "Surround Sound Not Working"
date: 2016-01-19
forum: Hardware
---

### Post by HDTimeshifter on 2016-01-19
I can't get sound out of my rear surround speakers.When I pull up the Sound Control Panel, it is set to Digital Output (SP/DIF), however, the Fade:  (Rear/Front) is greyed out. The Subwoofer is also greyed out. When I try to test the sound, it only has tests for Front Left and Front Right. When I switch to Analog Output, all the sliders are active. If I select Analog Surround 4.1 Output, and Test Sound, I get tests for Front Left, Front Right, Rear Left, Subbowoofer, Rear Right tests show up (but don't work since I'm using a digital RCA cable). When I originally set up the speaker system, I tested it with all speakers. So I'm not sure if it stopped working with a later Ubuntu version, or only worked with WIndows like in this thread [http://ubuntuforums.org/showthread.php?t=2215005&page=2&highlight=sound]("http://ubuntuforums.org/showthread.php?t=2215005&page=2&highlight=sound"). I have an ASUS P5Q Pro motherboard that I'm attaching the SP/DIF cable to. Or is it that Ubuntu 14.04 LTS doesn't support surround sound on the P5Q?

---

### Post by HDTimeshifter on 2016-01-21
I found [http://opennomad.com/content/ubuntu-1210-and-spdif-or-iec958-or-optical-audio-output]("http://opennomad.com/content/ubuntu-1210-and-spdif-or-iec958-or-optical-audio-output"), but there's still no Digital Surround option available in the pavucontrol drop-down lists.

---

### Post by blm-ubunet on 2016-01-21
Mult-channel (MCH) audio (>2) over S/PDIF is only possible with matrix encoded bitstream passthru'.
Most devices (receivers) only support AC3/DTS & not all support max bitrates.

S/PDIF over HDMI supports the HDA formats.

So to get MCH you have to be outputting to Digital Stereo IEC958 output device.
Pulse audio supports bitstream passthru for AC3 etc. You have to set the receiver capabilities because S/PDIF is one-way comms protocol.

If you want to take discrete MCH (i.e. use mixer, add bass boost other effects) & output over S/PDIF you have to use the alsa a52/AC3 encoder plugin. Historically, this required building plugin from source & was complicated by the debian avconv/libav debarcle & channel mapping inconsistencies.
There was a potential DTS encoder with alsa plugin as well:
"dcaenc"
& updated fork+:
[https://github.com/filler56789/ffdcaenc-2](https://github.com/filler56789/ffdcaenc-2)
DNK if the alsa plugin will build..

---

### Post by HDTimeshifter on 2016-01-22
I have an Altec-Lansing AD880 4.1 system. If I set it to Dolby Pro-Logic, then I get surround sound (but it is matrixed from 2-channel audio). If I set it to Dolby Digital, I get no surround sound from either CD songs (PCM) or Dolby Digital DVDs.

---

### Post by blm-ubunet on 2016-01-22
Nothing wrong with Asus P5Q mobo iec958.. have been using this for >8 years.
It works fine with DTS / 640kbps AC3 & 96K/24bit PCM.

To get AC3/DTS passthru' to work you have to:
- set the external device to dolby digital A52/AC3.
Using pavucontrol:
- set ( on configuration tab) device to be digital stereo iec958
- on the output tab set the output to digital output
- click the advanced drop down gadget
- set AC3 (tick box)
- test

Guess it is possible your device has limited bitrate, IIRC default AC3 is 480Kbps, but that would imply you have to run a proprietary windows only driver ( AC3 encoder).


Having problems compiling the a52 alsa plugin against latest ffmpeg but this DTS alsa plugin works:
[https://github.com/darealshinji/dcaenc](https://github.com/darealshinji/dcaenc)

---

### Post by HDTimeshifter on 2016-01-22
My Altec Lansing AD880 manual doesn't have bitrate specs, but I'll try the pavucontrol settings you suggested.

I've actually been running the Altec Lansing PC 4.1 system in parallel with a receiver and with hi-fi 2.1 system (Martin-Logan sub and B&W bookshelves) mainly because it has the surround speakers and I don't have to go to the closet where the receiver is to turn it on, but can turn on the Altec Lansing system from its right speaker power button. For a while, I had my P5Q SP/DIF out to a splitter so I could route it to both the Altec Lansing or my receiver. Another option I might try is hooking up a spare set of bookshelf speakers I have to my receiver to see if I can get Dolby Digital AC3 surround output through that. At least the display will show whether it's switching to DD or Pro-Logic depending on the signal received. The Altec Lansing system is supposed to automatically switch to AC3 upon receiving an AC3 signal as well. If my hi-fi system works out and I find permanent space for the rear bookshelf speakers, I might even scrap the Altec Lansing system, but would like to confirm that it works first.

---

### Post by HDTimeshifter on 2016-01-24
I checked the pavucontrol AC3 option (which was the only thing missing), but the Altec Lansing Dolby Digital LED still doesn't light up and no sound from the surround speakers either. I guess I'll try my hi-fi receiver next.

---

### Post by blm-ubunet on 2016-01-24
Definitely try with the HT amp AVR.
Unless it has Marantz, Yamaha, Pioneer, Arcam, Denon, Onkyo (or even sony) written on the front & back I wouldn't trust it.

---

### Post by HDTimeshifter on 2016-01-24
It's a JVC RX-884VBK. I put the DVD into a DVD player and the Dolby Digital with 5.1 channel graphics all light up. But when I switched back to the computer (actually physically switched cables to eliminate problems from splitters since there is only 1 digital RCA input) and put the DVD in the computer, only the Pro Logic lights up on the AVR so I'm pretty sure the computer is not sending out MCH audio. In fact the AVR doesn't like splitters as when I have the cable to the PC connected at the same time as the one from the DVD player, I loose audio from the DVD player and is probably why I kept dual speaker systems in the room since I can't really run audio from the PC to the AVR. I also tried setting the pavucontrol to Digital Surround 5.1 (IEC958/AC3) Output, but that freezes up the video.

Any other things I should try?

---

### Post by blm-ubunet on 2016-01-25
Maybe I misunderstand but.. I don't believe you can use a splitter to combine the 2 S/PDIF signals..
Each has a running clock (with output is active?) & they load each others outputs.
You can probably buy an active input mux device.

What are you using to play the DVD (on PC)?
Most of the players need special cmd-line options (or GUI setups) to drive AC3/DTS out over S/PDIF.

Your rear panel S/PDIF coax RCA is an adaptor bracket fitted into one expansion slots?
This plugs into pin header on the mobo ?

---

### Post by HDTimeshifter on 2016-01-26
I'm using Videos (default Ubuntu video app?). Is there a better one I should try?

The rear panel SP/DIF is just the one on the P5Q motherboard.
[IMG]https://www.asus.com/Motherboards/P5Q_PRO/gallery/[/IMG]

---

### Post by blm-ubunet on 2016-01-26
Sorry, forgot S/PDIF adaptor bracket wasn't required with this mobo..
Rear I/O panel S/PDIF RCA should be fine, exact same connection works here (for years).

I doubt the std movie player is capable of supporting bitstream pass thru' AC3/DTS.

Players that do are: mpv, VLC, ffplay mplayer(old), smplayer, kodi (OTT), mythtv (OTT).
mpv & mplayer require profile file set-up & don't have GUI.
ffplay (ffmpeg) has no GUI & std ubuntu version is no good.
smplayer or VLC could be easier to get started.

None of them have [de|r]ecent versions in std ubuntu repos..

I don't know what video h/w you have..
All above should be able to do h/w video decoding (not sure VLC can do VDPAU directly) but a core2duo can decode & de-interlace most video okay.

A well seasoned user here, "m4man", has an excellent ppa for mpv etc.

---

### Post by HDTimeshifter on 2016-01-26
I have an ASUS EN9500GT video card and Core2 Quad Q6600.

I had tried building a Core2 Duo HTPC with MythTV early in 2008, then that fall, built this PC with Ubuntu as the primary OS and joined Ubuntu forums. My thought was to have the HTPC stream content to this PC in my office bedroom via LAN, but the HTPC never worked out as I had trouble getting OTA reception with my HDHomeRun. But MythTV remains a working option. What is OTT? PPA? I think I played around with VLC a few years back, but maybe only the Windows version. I looked that up last night, but didn't find any repositories and didn't want to mess with compiling it. The 2.1 speaker setup didn't work well for DVDs as the bookshelf speakers were too far apart, but I added a spare bookshelf speaker as a center channel this weekend and that seems to work better. I'll probably try MythTV on this PC and test a DTV USB also. If I can get DTV on my PC, then I can scrap the old tube TV, DVD/VHS player, and cassette player in the closet hooked up to my AVR and just use my PC to watch TV, DVDs, and play CDs with audio routed through the AVR. I don't have space for bookshelf speakers as surround speakers in the rear of the room and the B&Ws are much better quality than the little Altec Lansing PC speakers. I would like to have AC3 rather than Dolby Pro Logic for the center channel, however.

---

### Post by blm-ubunet on 2016-01-29
To test AC3 paasthru' you need to configure the player.

Some incomplete (possibly incorrect) cmdline examples:
play AC3 track to iec958:
mpv --audio-spdif=ac3,dts --ao=alsa:device=iec958
play discrete MCH using AC3 encoder:
mpv --af=lavcac3enc=tospdif=yes:bitrate=448

vlc --ao alsa --alsa-audio-device iec958

OTT== over the top
PPA==personal package archive (3rd party repositories)
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by HDTimeshifter on 2016-05-16
I gave up on trying to figure out MythTV (and now that ski season is basically over, have more time to tinker) and installed VLC today, and got it working. :-)

---

