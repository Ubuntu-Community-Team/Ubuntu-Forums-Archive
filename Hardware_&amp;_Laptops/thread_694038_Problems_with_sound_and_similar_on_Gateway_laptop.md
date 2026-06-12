---
title: "Problems with sound and similar on Gateway laptop"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by safesite on 2008-02-11
I am fixing a laptop of the brand Gateway for one of my friends with the Ubuntu Feisty Fawn 7.04.

I have worked around a lot of problems by simply trying things out and I'm new to Linux myself.

However, I still have some problems remaining with this laptop.

1. There is absolutely no sound whatsoever. Not in the internal loudspeakers, earbuds, you name it.

2. I can't run DVD's as Totem is dying on me while playing or says that it can't play the DVD format if it doesn't die.

3. When I insert music-CD's I can't get any sound either. The thing start playing and I can use sound juicer to extract songs to the ogg-format but nothing there is nothing to hear.

Anybody with a solution to all that?

Appreciate it.

Cheerio...

---

### Post by safesite on 2008-02-12
Anybody on this one please? Thnx! :KS

---

### Post by Powerman2442 on 2008-02-12
I have the same problem. The only thing is that everything worked just fine. Then, I decided to update cause there was 188 new updates. When I restarted and logged back in I had sound then it just stopped. No sound what-so-ever. Not sure what to do at this point. And I have a Gateway laptop as well. 

If you figure out anything let me know.

---

### Post by safesite on 2008-02-12
Hi and thanks for the reply.

I don't know but I expected a bit more from Ubuntu and Linux than this. As mentioned this is a friend's laptop and I can make most things work but the sound.

I usually look around and try to find solutions myself before bothering others but making the sound work and then having these problems seems to me out of proportion, close to the ridiculous.

I have read a few posts from people here on the forum that had the EXACT same or similar problems with their Gateway laptops and sound but the solutions are so different, confusing and vague to me and partially written in code (you know..., install this here, code that there etc.) that it becomes even more ridiculous to an average user or beginner trying to make these things work than it already is.

In my honest opinion I have to say that I'm getting tired of these problems and if the people who make Ubuntu and want to 'promote' it and get people to use Linux instead of Windows and expect to get anywhere close to that goal within the nearest future they better start providing some support instead of letting people dangle in the air. So far nobody here on the forum has even replied to my problem and given a possible solution and that just makes me want to install Windows again.

However, I hope that you solve your problems. I also updated but didn't check on the sound issue before the update. I just know that it doesn't work now after the update. Seems even more ridiculous to me that it doesn't after the update which should make things work better really. :)

---

### Post by KCPokes on 2008-02-12
To be honest you really can't expect a miracle solution if you've provided no insight as to your specific setup.  You state a Gateway laptop.  I have a Gateway laptop and mine works with no issues.  Obviously that doesn't mean that all will, but my point is unless you provide some insight as to what your setup consists of, what you've tried, etc.... there really isn't much people can do to assist.  If I ask you why my sound on my Dell laptop doesnt work in WIndows, do you now have enough information to fix it?  Probably not, so please try to provide some details if you expect assistance.

---

### Post by Powerman2442 on 2008-02-12
Yeah safesite this is free so you can't expect somone to anwser right away. I just reinstalled and didn't update again. I looked around and there were other people with problems and they had "solutions", but they were laid out for a noobie.

Mine occured right after I downloaded and installed the 188 updates it said I had. Wish there was a system restore option. :P I am looking for a program to make a backup of Ubuntu as is right now. If you know of one tell me.

---

### Post by Yellow Pasque on 2008-02-12
Please run some commands so we know what hardware we're troubleshooting:
```
sudo update-pciids; lspci
cat /proc/asound/card0/codec#* | grep Codec
```

EDIT: Also make sure you run amixer and make sure that ALSA didn't mute itself after an update or something (it has a nasty habit of doing that).

---

### Post by Powerman2442 on 2008-02-12
> **Temüjin said:**
> Please run some commands so we know what hardware we're troubleshooting:
```
sudo update-pciids; lspci
cat /proc/asound/card0/codec#* | grep Codec
```

EDIT: Also make sure you run amixer and make sure that ALSA didn't mute itself after an update or something (it has a nasty habit of doing that).

Okay I looked around and figured out how to get into the menu. Where exactly should I look to see if it is muted. Cause I may try to update again. I hope it will just mute itself. Otherwise I have to live without sound or reinstall... again.

---

### Post by Yellow Pasque on 2008-02-12
There are things you should try before you resort to reinstalling, and remember that here's no guarantee that reinstalling will fix it (this ain't Windows!).

I'm sorry, but I have to confess that I don't know much about the ALSA mixer, (I use OSS4) so I don't know exactly how to tell you to check the volume. Nevertheless, I do have some handy ALSA links. What would really help is if you ran those commands for us (Applications -> Accessories -> Terminal).

Scripts to get ALSA1.0.16: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
An hda-intel thread: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Powerman2442 on 2008-02-12
Hmm, never reinstalled Windows XP in the 6 years I have had it. Or Vista in the few months I have had it. Regardless The I hear sound now, but I know it happened right after I updated. Which is why I havn't updated yet. I am looking for a backup program right now. When I find a good one I will update and see what happens.

---

### Post by safesite on 2008-02-12
powerman --> This might be free but you are having the exact same problem so you ought to be as interested in help as I am. Why don't we try together to get that solution, shall we? Instead of pulling on each side of the rope into opposite directions that is...

kcpokes --> To be honest..., I'm in this the first time as stated previously so why not help and guide people to give you the information instead of as Temujin did. Now that way I can provide you with what you need and here it is. Easy as kiddyplay if you ask me this way...


lebanon@lebanon-laptop:~$ sudo update-pciids; lspci
--03:08:03--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 130,896 (128K) [text/plain]

100%[=================================================================================>] 130,896      107.13K/s             

03:08:05 (106.91 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [130896/130896]

Done.
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
lebanon@lebanon-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec

---

### Post by Powerman2442 on 2008-02-12
I know dude, I was just saying. I respect peoples help here. I just updated again. We will see what happens. If my sound stops again I will post more information.

---

### Post by Powerman2442 on 2008-02-12
Okay I just updated and I have no sound. I did the commands you listed before and here is what I got.

--21:02:26--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 130,896 (128K) [text/plain]

100%[====================================>] 130,896      112.70K/s             

21:02:32 (112.43 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [130896/130896]

Done.
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Codec: SigmaTel STAC9250
Codec: Motorola Si3054

Update: I just went on Synaptic and downloaded alsamixergui and gnome-alsamixer. Neither of them or the built in volume controller say that card is muted or off. Volume is jacked up on everything.

---

### Post by Powerman2442 on 2008-02-12
I also got this from typeing "amixer" into terminal. Eveything looks like it is 100%.

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Front Mic' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

I also used "alsamixer" and everything is jacked up on it as well. I figured out how to mute it this way as well. If I press mute (m) multiple times I hear a little crackle and pop in my headphones if I listen closely.

---

### Post by Yellow Pasque on 2008-02-12
@Powerman, I would try the directions in this thread, especially if you have one of the gateway laptops it lists undet the Sigmatel/STAC 9250 codec.: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

@safesite, I see you have an ICH4 Intel AC97 chip, which uses the intel-8x0 alsa driver. I'm not sure how to troubleshoot this off the top of my head. If I have more time later tonight, I might be able to search around and help you further.

---

### Post by Powerman2442 on 2008-02-12
Thanks very much sir, or mam?! :O lol

I'll keep your posted.

---

### Post by KCPokes on 2008-02-12
Powerman, post your /etc/modprobe.d/alsa-base file.  My setup seems very similar to yours, including the codecs, so I'd be curious in seeing what you have in yours that differs from mine, since my has been working out of the box.  

Safesite, I got nothing.  It is about attitude and I choose to just move on.  I believe in helping those that help themselves, which means you will need to do some homework yourself.  Good luck to you.

---

### Post by Powerman2442 on 2008-02-12
Yeah, this is extremely weird. I have been messing with the alsa commands in terminal and started smashing stuff, next thing I know I hear a beat sound come from the Gaim messanger. I was like what. Decided to go on YouTube and watch a music video. There is sound. 

I wish I knew what I did. I was just messing with the alsa commands like I said hitting "m" on all of them and space. Apparently it did something. I was just about ready to do Tamujin's idea here... [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24) and it started working. I will let you guys know if something else happens to it. I'll see if I can't help safesite as well.

---

### Post by KCPokes on 2008-02-12
> **Powerman2442 said:**
> Yeah, this is extremely weird. I have been messing with the alsa commands in terminal and started smashing stuff, next thing I know I hear a beat sound come from the Gaim messanger. I was like what. Decided to go on YouTube and watch a music video. There is sound. 

I wish I knew what I did. I was just messing with the alsa commands like I said hitting "m" on all of them and space. Apparently it did something. I was just about ready to do Tamujin's idea here... [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24) and it started working. I will let you guys know if something else happens to it. I'll see if I can't help safesite as well.

Sounds like something was somehow muted....sound may be up but alsamixer tends to want to mute output.  Glad to hear you got it worked out.

---

### Post by Powerman2442 on 2008-02-12
Yeah, they said there would be and M under the setting if it was muted. There wasn't any... but when I hit "m" to mute and unmute and heard what appeared to be static if I listened closely. Next thing I know it is working. Not sure.

---

### Post by Powerman2442 on 2008-02-13
I spoke to soon. I rebooted tonight and guess what... no african safari sounds, or whatever they are. lol

This time I am going to pay more close attention and see if I can't figure this out.

---

### Post by Powerman2442 on 2008-02-14
Well I just ran some more checks and it seems I have an extra codec after reboot. Maybe from the updates?

derek@ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9250
Codec: Motorola Si3054
Codec: Generic ffff ID ffff

Here is my audio device under the following command.

derek@ubuntu:~$ sudo update-pciids; lspci
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

I type in "amixer" like I did before and got this...

derek@ubuntu:~$ amixer
amixer: Mixer default load error: Invalid argument

I typed in "alsamixer" like before and I got this...

derek@ubuntu:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument

KCPokes: When you said "Powerman, post your /etc/modprobe.d/alsa-base file. My setup seems very similar to yours, including the codecs, so I'd be curious in seeing what you have in yours that differs from mine, since my has been working out of the box." would you mind telling me how to do this? Thanks

Update: Since the commands I tried above did not work, and they did before I wondered if the update did something to the alsa program after I installed and rebooted. I never rebooted the first time. O went into Synaptic and reinstalled all of my Alsa and Alsa Mixer programs.

I have been trying to use gnome-alsamixer and it starts loading but never opens and just shuts down.

I am going to try to update alsa to the version Temujin gave me.

Update: I installed the latest version of Alsa that Themujin posted earlier. When I rebooted I heard sound from the login screen. But when I got to the part where you hear the african music there was no sound. I went on YouTube and tried to listen to a music video with no luck. And yes I did the second part of Temujin's post. Everything worked fine there.

Then, I installed a few mixer programs to see if anything was muted. I installed the following on Synaptic.

alsamicergui
aumix
gamix
gnome-alsamixer
qamix

All of them worked properly, unlike before, and all of them send every sound settings was cranked to it's max. I check my notebook and mute is off as well. No clue where to go from here untill KCPokes or someone else gets back with me about the /etc/modprobe.d/alsa-base and where to install that one line.

---

### Post by Powerman2442 on 2008-02-14
> **KCPokes said:**
> Powerman, post your /etc/modprobe.d/alsa-base file.  My setup seems very similar to yours, including the codecs, so I'd be curious in seeing what you have in yours that differs from mine, since my has been working out of the box.  

Safesite, I got nothing.  It is about attitude and I choose to just move on.  I believe in helping those that help themselves, which means you will need to do some homework yourself.  Good luck to you.

Ahh-ha! I figured it out. Here it is...

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

The one link that one of you provided said this, "for me. Then adding the line

options snd-hda-intel model=dell-m42

to /etc/modprobe.d/alsa-base solved my headphones problem."

Does it matter where I add that line? I would try it tonight but I don't want to mess anything up. Thanks

---

### Post by safesite on 2008-02-14
> **Powerman2442 said:**
> Ahh-ha! I figured it out. Here it is...

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

The one link that one of you provided said this, "for me. Then adding the line

options snd-hda-intel model=dell-m42

to /etc/modprobe.d/alsa-base solved my headphones problem."

Does it matter where I add that line? I would try it tonight but I don't want to mess anything up. Thanks

Powerman --> Did you get it to work now? I mean for good? Let me know and we see if your input can help make those Gateway's work. I am not completely understanding the process with the codes and I'd be most grateful to get a quick walkthrough if possible so I can repeat those steps you did. Thanks.

Temüjin --> Thanks. I appreciate this. I'll be looking out for your next post if you stumble upon something.

kcpokes --> It sounds to me like you don't want to help but people to understand things on their own that they don't have the slightest clue about. If I'd do I wouldn't post in this forum so you don't make sense. Regarding the attitude thing you got I am the one who wishes you good luck cause you'll need it if you really think this way. If I'd be able to help myself as mentioned before I'd not be asking. These codes might as well be written in Chinese. Would you sit down and learn Chinese 'just by helping yourself'...?! I think we both know the answer to that. I believe in helping others if I can (and I often do) and others helping me if they know something I don't. Now I might be mistaken but I reckon that's a better, more efficient and much less selfish and productive approach in solving problems than the one you projected in your last post. The internet is such a vast place that I too urge you to move on and leave my thread as I'm sure you must be busy 'helping others that help themselves' elsewhere in this universe. I am also sure that Temüjin and Powerman share my attitude since I only got help and input so far from them and which I believe is more prevalent among the average user than yours and thus hope and guess that we'll find a way also without your help. So you go right ahead and continue sulking somewhere else. 'Good luck!' =; =D>

---

### Post by Powerman2442 on 2008-02-14
KCPokes has given me ideas as to what to search for same with Temujin. I've learned quite a bit from this one problem I had, which is why I am useing Ubuntu. I am getting confused however because when I go on YouTube and watch a video there is no sound, but sounds are coming from the Gaim instant messanger program that came with Ubuntu. The first dong sound that came from the login screen works, but the african music played with loading gnome and my user settings (I think this is what it is loading) doesn't make a noise. 

The whole YouTube thing may be a plugin problem, I will look more into that. But the sound seems to come in and out and it wishes. Like when I restart or shutdown. Then, boot back into Ubuntu it doesn't want to make sounds.

Not sure if you can call my problem fixed or not safesite. On the top of page two, the first post you made, it had your sudo update-pciids; lspci command. The problem is I don't see an Audio Device listed. Look at the next post from me with all of my info and I have this "00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)" I don't see an audo device. Also when you did the next command cat /proc/asound/card0/codec#* | grep Codec there are no codes listed like there are in mine. Not sure but this seems weird to me. Maybe Ubuntu itself doesn't have codecs or even notices you audo hardware there?

Open up terminal and try typing in amixer also you can try alsamixer as well. If they don't work get on Synaptic and look for gnome-alsamixer or alsamixergui.

Remember Temujin said, "@safesite, I see you have an ICH4 Intel AC97 chip, which uses the intel-8x0 alsa driver. I'm not sure how to troubleshoot this off the top of my head. If I have more time later tonight, I might be able to search around and help you further."

Maybe you should look up ICH4 Intel AC97, or maybeing intel-8x0 alsa driver in the forums or google. A lot of the info I found came from google and the forums.

Also you can tru updateing to the latest version of alsa, which is what I needed to do because it was telling me the program or whatever didn't exist. Temujin gave this link to me and it is very easy. All I did was save ti to favorites, take a screenshot of the directions and saved it to my desktop. Then, I downloaded the following files and did what he told me to. If you need and help with this part let me know. Seemed pretty easy to me, but I have been going crazy with Ubuntu.

---

### Post by Yellow Pasque on 2008-02-14
Powerman, I think you're running into the standard mixer problems with ALSA. Look into PulseAudio for multiple sound streams. In fact, Ubuntu 8.04 is going to have Pulseaudio as  a standard package.

---

### Post by safesite on 2008-02-19
> **Powerman2442 said:**
> KCPokes has given me ideas as to what to search for same with Temujin. I've learned quite a bit from this one problem I had, which is why I am useing Ubuntu. I am getting confused however because when I go on YouTube and watch a video there is no sound, but sounds are coming from the Gaim instant messanger program that came with Ubuntu. The first dong sound that came from the login screen works, but the african music played with loading gnome and my user settings (I think this is what it is loading) doesn't make a noise. 

The whole YouTube thing may be a plugin problem, I will look more into that. But the sound seems to come in and out and it wishes. Like when I restart or shutdown. Then, boot back into Ubuntu it doesn't want to make sounds.

Not sure if you can call my problem fixed or not safesite. On the top of page two, the first post you made, it had your sudo update-pciids; lspci command. The problem is I don't see an Audio Device listed. Look at the next post from me with all of my info and I have this "00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)" I don't see an audo device. Also when you did the next command cat /proc/asound/card0/codec#* | grep Codec there are no codes listed like there are in mine. Not sure but this seems weird to me. Maybe Ubuntu itself doesn't have codecs or even notices you audo hardware there?

Open up terminal and try typing in amixer also you can try alsamixer as well. If they don't work get on Synaptic and look for gnome-alsamixer or alsamixergui.

Remember Temujin said, "@safesite, I see you have an ICH4 Intel AC97 chip, which uses the intel-8x0 alsa driver. I'm not sure how to troubleshoot this off the top of my head. If I have more time later tonight, I might be able to search around and help you further."

Maybe you should look up ICH4 Intel AC97, or maybeing intel-8x0 alsa driver in the forums or google. A lot of the info I found came from google and the forums.

Also you can tru updateing to the latest version of alsa, which is what I needed to do because it was telling me the program or whatever didn't exist. Temujin gave this link to me and it is very easy. All I did was save ti to favorites, take a screenshot of the directions and saved it to my desktop. Then, I downloaded the following files and did what he told me to. If you need and help with this part let me know. Seemed pretty easy to me, but I have been going crazy with Ubuntu.

Powerman --> Thanks very much for your very long and detailed help. I just did the reinstall of alsa-utils and the very first install of alsamixergui and gnome-alsamixer and all at the same time. However there was no improvement. I tried to play a Music-CD in Rythmbox Music Player and Serpentine Audio CD Creator but without any sound. The CD itself and the programs seem to work fine apart from the sound problem.

In regards to the Gaim Messenger I haven't really tried that one yet but I can inform you that all other sounds in any other programs or the OS haven't been playing just once yet. Not even while boot up is taking place nor when the log in is happening. So, I don't think there is any difference. The problem that persists must be connected to the audio hardware and the lack of recognition of the same in the Ubuntu software. Isn't that a driver problem? If you ask me I think that this is where the main-problem is.

However, I don't have any clue about drivers in Ubuntu as well as that I use Ubuntu for real the first time now. You said that you can't see any audio controller in my list as it is in yours but I don't understand this because at the same time you said that Temujin stated I had the  ICH4 Intel AC97 chip. Now, I'm a bit confused here but isn't that exactly what we need in order to make the sound work? Where is the difference between the audio controller and the chip? We are talking about the hardware that is needed for the sound here. Aren't we?

Furthermore I tried to check on Google as you suggested and when searching for the driver itself I stumbled right away over this post in the Ubuntu-forum in which some people have the exact same problems as I/we have with our laptops. The link is here:

[http://ubuntuforums.org/showthread.php?p=4308756](http://ubuntuforums.org/showthread.php?p=4308756)

Unfortunately there seems to be no easy answer yet and neither do I know where to find that driver you mentioned or at least haven't found it so far (and where does one find those for Ubuntu. If only I knew :) ).

When you said 'try updating to the latest version of alsa' did you mean the steps I described in the first paragraph in this post? I mean the update and install in the Synaptic Package Manager? Because as mentioned I did this already without any success.

In regards to  youtube and playing videos and sound I have the same problem. I don't think this has anything to do with codecs nor plug-ins. The videos are flash and thus shouldn't need codecs nor plug-ins apart from the flash-plugin (at least I have never heard of special codecs for flash nor other plug-ins than the flash-player itself). The videos play fine when the flash-player is installed in Firefox but the sound is lacking as well.

In the link to the other thread I just posted before someone is saying the following:


...'I have the same problem with my laptop. Compaq 700Z with an VIA AC97 chipset.

I don't think I can add much to the conversation since I'm quite new to linux, slowly learning (found a lot of usefull debugging infos in here). But I can vaguely retrace the apparering of my bug : After a clean install from a 7.10 cd, my sound did work. I then configured my wifi network and installed all the software updates I could find.
The problem is I can't recall if the problem appeared right after I updated, or after I started fiddling with the installed packages

Feel free to ask me for more details if needed, I'll be keeping an eye on this thread'...


Apparently this means that it is - as mentioned before - a problem of the software/drivers. The fact that he used Ubuntu 7.10 and got the sound working and I use 7.04 makes me think that the newer version is maybe shipping with the lacking drivers that you, I and others need. Meddling with the software or updating - also this version - however seems to worsen or recreate the problem. I have ordered the 7.10 CD but it will first arrive in 4-6 weeks from now so I don't know the answer to this just yet. It seems so but I can't say for sure.

By the way, I tried to make a test and reinstalled Ubuntu 7.04 to see if there were any changes in regards to the sound-problem I am having now BEFORE I downloaded and installed the missing updates but there wasn't.

Well, I'll keep searching for the driver but I do not really know where to find it. Give me some feedback when you get the time.

Thanks...


Temujin --> Any news on those drivers you talked about or a possible solution to the problem?

---

### Post by e6600 on 2008-02-24
i have the same ac'97 audio chipset that safesite has
need a fix!!! im a complete terminal noob, and the only thing i really know how to do is copy/paste codes into terminal

---

### Post by safesite on 2008-02-26
> **e6600 said:**
> i have the same ac'97 audio chipset that safesite has
need a fix!!! im a complete terminal noob, and the only thing i really know how to do is copy/paste codes into terminal

Sorry to hear that mate. I wish I could help you out but I'm stuck like you and nobody seems to be seriously interested in coming forward to help nor care about 'promoting Linux among the average user'. That and the attitude here of the Ubuntu support has made that I and my buddy are now putting Windows back onto the laptop we can't seem to get working properly and are dropping Ubuntu - FOREVER!

I hope you work it out but I doubt you'll be more successful. I won't need no more 'solutions' from this forum and maybe you might want to think about going back to Windows as well. At least that's junk that you already know. This however seems apparently like if it's new junk.

Go Ubuntu...! ):P=D>

---

