---
title: "Stupid ALSA and Intel 82801H sound card"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by PacShady on 2008-04-06
**This post is related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/210865](https://bugs.launchpad.net/ubuntu/+bug/210865)
**This post is related to an ALSA bug filed at**: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3886](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3886) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
I have tried everything to get this damn card to work but for nothing. All ALSA can do is produce sound through the headphones; the two speakers and subwoofer remain silent. Not only that, but alsamixer refuses to work, spitting out this error:

```
ALSA lib simple_none.c:1741:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument
```


This is what I've tried so far:
* upgraded to Hardy Beta, and tried both 64bit and 32bit (note: this means I tried Gutsy first)
* installed linux-backport-modules
* purged alsa-base, alsa-utils and linux-sound-base and reinstalled them
* downloaded alsa-source and recompiled modules
* recompiled all of ALSA from source from the project page
* modified /etc/modprobe.d/alsa-base options for snd-hda-intel
* TRIED (and failed) to install PulseAudio to see if it would work
* TRIED (and mostly failed) to install OSS to see if it would work
* renamed my ~/.asoundrc file
* installed gnome-alsamixer and alsamixergui hoping to get around the error above
* got the alsa_1 and alsa_2 scripts (linked below) to reinstall ALSA from source
* and probably more I can't remember

I've been at this for the past week. I'd like to make it clear at this point I'm also using KUBUNTU, because most instructions are given for a GNOME interface which doesn't help us KDE users one iota. I'm also using Hardy Beta.

These are the sites, pages and threads I've used so far in my attempts to fix my sound on my own:
* [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")
* [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
* [Howto: Open Sound System in Ubuntu Feisty]("http://ubuntuforums.org/showthread.php?t=575521")
* [ Temujin's OSS install guide]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60")
* [Ubuntu Wiki's PulseAudio Guide]("https://wiki.ubuntu.com/PulseAudio")
* [Temujin's ALSA source install scripts]("http://ubuntuforums.org/showpost.php?p=4298894&postcount=24")

I managed to get SOME success with OSS, but the only things I could find to explain how to install it in Ubuntu didn't go into detail about how to get KDE to work well with it. KMix fried altogether, even with the advice on the OSS Howto above for it. The sound server would fail to start by itself automatically, and when I started it manually in Sound Settings it didn't seem to start completely or properly so most programs still wouldn't use it. PulseAudio was an epic fail, with "Connection Refused" at every attempt to communicate with it and not one person seemed to have the same problem, so there wasn't anything for me to fix it.

I've put a bug report [here]("https://bugs.launchpad.net/ubuntu/+bug/210865") and [here]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3886"), but so far they're getting very little attention, and since I seem to be the only one with this problem to this extent, I don't see the problem being fixed anytime soon. For this reason I'm still trying to find a way to fix it.

I know this much. From aplay -l, I have three devices loaded on the one card, two are ALC883 (one analog, one digital), and one is ALC263. From OSS being able to work, as well as aplay -L, ALC883 is the actual output sound component I need (dunno what ALC263 is then :s). However, KMix registers in the lower right corner that it's using the ALC263 device. Whether this is why my sound won't work, or if it's just another side effect of ALSA being screwed, I don't know. And now some details from outputs (there's also a copy of alsa-info.txt attached to this post):

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 4: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
cat /proc/asound/modules
0 snd_hda_intel
```

```
sudo lspci -vv
...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Mitac Unknown device 8227
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000 Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0
...
```

```
cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
  6: [ 0- 2]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 20: [ 0- 4]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 28: [ 0- 4]: digital audio capture
 33:        : timer

```

```
aplay -L
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

```
cat ~/.asoundrc
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/pacshady/.asoundrc.asoundconf>

```

```
cat ~/.asoundrc.asoundconf
# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
!defaults.pcm.card Intel
defaults.ctl.card Intel
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off

```

```
cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux ShadyLappyMKII 2.6.24-15-generic #1 SMP Tue Apr 8 00:33:51 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xfc200000 irq 22

Audio devices:
0: ALC883 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC268

```

So I guess my question is this: is there a way of fixing ALSA to work with my card? If not, then how can I properly and fully replace ALSA with a working alternative?

'Shady


**UPDATE:** I've managed to get my sound working by installing the OSS drivers, installing libsdl1.2debian-all from apt-get, and then adding the following line to /etc/rc.local:
```
apt-get install libsdl1.2debian-all --reinstall --force-yes -y
```
It's a really cheap-and-nasty hack, and definitely doesn't look to be a permanent solution, but at least it all seems to work. Kaffeine works so long as xine is set to use OSS, Flash works as well it seems. The only thing is KMix doesn't seem to work, not sure how to fix it yet. Also, plugging headphones in doesn't swap focus from the main speakers to the headphones, it just plays sound through both. One needs to mute the int-black channels under the first jack of codec1 (which control the front speakers and subwoofer) to turn off speaker sound while headphones are in. Don't know how to fix that either.

ALSA is still broken. My bug reports are being ignored by both Ubuntu and ALSA maintainers. I've given up on ALSA now since I got OSS to work. I'd like to get KMix working though, and I want to get the volume control buttons on my laptop to work again as well. Plus, the headphones should turn off the main speakers when they're plugged in. Any ideas are welcome.

**UPDATE:** A patch has been made for ALSA to work with this card. The patch can be downloaded from [this post]("http://ubuntuforums.org/showpost.php?p=4871189&postcount=30"), follow the instructions there to get it installed. Thanks very much to RenZO for putting this patch together!

---

### Post by ChampAmp on 2008-04-06
If you are still interested in having this work under Gutsy, try the backports (get the generic package) discussed here....I have this chipset, I installed the packages, rebooted, and BAM.....sound!

[Backport Solution]("http://ubuntuforums.org/showthread.php?t=687726&highlight=82801H")

---

### Post by PacShady on 2008-04-06
Thanks, but I should've added that to the list of things I've tried :( backports didn't help.

---

### Post by PacShady on 2008-04-08
Bump

---

### Post by PacShady on 2008-04-08
Bump, again *sigh* this is gonna take a while to get someone's attention I see.

---

### Post by PacShady on 2008-04-08
Bump!

---

### Post by PacShady on 2008-04-09
BUMP :mad:

I must say I'm surprised by one thing. I downloaded KNOPPIX since it's supposed to be the gold standard for hardware detection in Linux. I booted it up, and it couldn't even find my sound card at all! Not to mention my wireless and my TV Tuner card (which I haven't even ATTEMPTED to get working yet, but it wouldn't even show up under lspci like it does in Ubuntu). Surprising news indeed.

Still doesn't change the fact that I CAN'T GET MY SOUND WORKING AND NO ONE SEEMS TO CARE :(

---

### Post by PacShady on 2008-04-09
Bumperific

Hey, let's see how many times I need to bump this thread to get someone's attention? These forums are set up ridiculously badly if threads only stay on the front page for a whole 3 hours.

---

### Post by Yellow Pasque on 2008-04-09
Try the scripts here? I didn't write them, so I'm not sure of alsa_2.sh's purpose, but it might be necessary for you.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

Also, for OSS4, it has its own mixer, ossxmix.

---

### Post by dupe576 on 2008-04-09
Ok.. I have a similar sound card.. so i figured I'd post here..

Except mine is the Intel 82801G,

from lspci:

**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**

I also followed the directions in the link [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
just as the OP did.

out put of dmesg | grep -i snd | tail -10:

[B][   12.900000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   12.900000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   12.900000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   12.900000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   12.900000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   12.900000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   12.900000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   12.900000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   12.900000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   12.900000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step[/B]

And this is generated at startup.  Is this module compiled against a wrong kernel version?

I used this command to configure the alsa drivers I installed...

```
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

```
so.. that confuses me...

when i tried to compile the third package.. the utils package.. it gave me this error:

[B]checking for libasound headers version >= 1.0.15... not present.
configure: error: Sufficiently new version of libasound not found.[/B]

What do I need this utils package for?  This also confuses me.

I grepped for modules belonging to my "sound" driver listed in /proc/devices and it gave me this output:

 ```
ls /dev/ -l | grep 14,
crw-rw---- 1 root   audio    14,   1 2008-04-09 20:11 sequencer
crw-rw---- 1 root   audio    14,   8 2008-04-09 20:11 sequencer2

```

On my other ubuntu machine (where the sound works), it shows many more device files than that (adsp, audio, dsp, mixer to be exact)

same thing when I look in the /dev/snd/ folder:
```
 ls /dev/snd -l
total 0
crw-rw---- 1 root audio 116,  1 2008-04-09 20:11 seq
crw-rw---- 1 root audio 116, 33 2008-04-09 20:11 timer
```

The ubuntu machine that works shows many more files.

Output of cat /dev/sndstat:

[B]Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux alex-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG[/B]


Someone please help!

I'm just starting to learn about all this stuff and I'm starting to understand some of it, but I don't have all the pieces together in my head yet.  

I will continue to research a solution.. but some help would be greatly.. GREATLY appreciated!

---

### Post by PacShady on 2008-04-09
> **Temüjin said:**
> Try the scripts here? I didn't write them, so I'm not sure of alsa_2.sh's purpose, but it might be necessary for you.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

Also, for OSS4, it has its own mixer, ossxmix.

Just tried those scripts, they also didn't help. I'll add them to the list of things that didn't work for me.

So far, OSS is the only thing that's had ANY success, although not complete. Since you've got the HOWTO for getting OSS working, maybe you can help me getting that set up? I can install OSS with your HOWTO, but the sound server doesn't seem to start up automatically at boot (I have to test the sound in Kubuntu's Sound Settings to start the sound server). What's more, KDE (artsd?) doesn't like using the OSS unless I install or reinstall libsdl1.2debian-oss or libsdl1.2debian-all within that session (some part of that package must also need to start up at boot to work properly and it's not). Any idea how I can fix that? Somehow, I don't like my chances of getting ALSA up and running anytime soon.

'Shady

---

### Post by Yellow Pasque on 2008-04-09
Sorry, but I'm not very familiar with the K side of the Linux world. IIRC, I installed the Kubuntu 8.04 beta on an old laptop disk I have. I'll try to play with it and install OSS4 tomorrow.

---

### Post by PacShady on 2008-04-10
> **Temüjin said:**
> Sorry, but I'm not very familiar with the K side of the Linux world. IIRC, I installed the Kubuntu 8.04 beta on an old laptop disk I have. I'll try to play with it and install OSS4 tomorrow.

Thank you. Let me know how it goes. If you get it working correctly, I'll just change over to OSS. I don't think I'll bother waiting for someone to fix ALSA since my problem seems to be an isolated case that will never be fixed.

'Shady

---

### Post by PacShady on 2008-04-12
Hey Temujin, had any luck with getting artsd to work with OSS yet?

What about this PulseAudio thing the Gnome-ish guys seem to be getting into lately? Would a combined PulseAudio-OSS system work better with artsd and KDE than OSS by itself? I couldn't work out how to get PulseAudio to work though, kept saying "Connection Refused" whenever I tried to do anything with it. I don't know if it'll work (while I know OSS WILL work if I can get it set up).

'Shady

---

### Post by Demianmex on 2008-04-13
Hello well, for me was a pain make my 82801G works too, but after a lot of researching and probing y made it!, y just followed the steps from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and when you edit sudo nano /etc/modprobe.d/alsa-base
add the next line

 options snd-hda-intel model=laptop-eapd

y add the next lines, then check your sound configuration and go to preferences and look for a channel called SIDE then you can control the volumen from your speakers from there

---

### Post by PacShady on 2008-04-13
> **Demianmex said:**
> Hello well, for me was a pain make my 82801G works too, but after a lot of researching and probing y made it!, y just followed the steps from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and when you edit sudo nano /etc/modprobe.d/alsa-base
add the next line

 options snd-hda-intel model=laptop-eapd

y add the next lines, then check your sound configuration and go to preferences and look for a channel called SIDE then you can control the volumen from your speakers from there

I already followed the steps in that Wiki page; there's a list on my original post of the things I've already tried, and the pages I've already visited to make things work.

The problem isn't in alsa-base, at least not in the snd-hda-intel model option; I've established that much (after trying every possible option for both ALC883 and ALC263). Especially since I'm willing to bet the problem with my sound not working is directly linked with the fact alsamixer refuses to work at all (see original post for details).

'Shady

---

### Post by PacShady on 2008-04-16
Bump.

Anyone got any ideas yet?

---

### Post by Yellow Pasque on 2008-04-16
Check your software sources (I just helped someone tonight who ran the scripts but didn't have the proper repos enabled). All the sources except CD should be checked. Then, update your available packages and try the script(s) again.

---

### Post by PacShady on 2008-04-16
> **Temüjin said:**
> Check your software sources (I just helped someone tonight who ran the scripts but didn't have the proper repos enabled). All the sources except CD should be checked. Then, update your available packages and try the script(s) again.

I already have all my sources enabled. Before I do anything with a new system, I enable all Ubuntu repos including universe and multiverse for all of them including backports and security. The sources are not the problem. Besides, the scripts didn't really seem to do much more than I already tried manually when installing ALSA from source, including the source from ALSA project itself.

---

### Post by PacShady on 2008-04-16
OK, I've got the CLOSEST to getting the sound working ever so far. This is what I did:

* Installed OSS and restarted so it replaced ALSA's modules
* Went to *System Settings > Sound System* and pressed "Test Sound" (this starts the sound server which, for some reason, isn't starting by itself at boot)
* Installed/Reinstalled either libsdl1.2debian-all or libsdl1.2debian-oss

After following these steps, the sound works flawlessly from what I can tell. Flash works, Kaffeine works, system sounds work, everything works (the only thing that doesn't is KMix, which is a bit of a pain, and I don't like ossxmix because it's not a very well designed GUI, and I don't know how to set up my laptop volume control buttons to work with it). Well, except for the subwoofer, but that's no biggie (I mean seriously, a subwoofer on a laptop? WTF?). Oh, and the fact that when I plug my headphones into the headphone port, they don't turn off the main speakers. Not sure why that's happening, or how to fix it.

BUT, when I restart the computer, I lose sound again. I have to follow the last two steps each time to get sound back up and running, which is definitely a pain. Temujin (or anyone else for that matter), do you have any ideas as to what's stopping sound from starting up by itself, and what I can do to fix it? Or even where to look for it?

---

### Post by PacShady on 2008-04-16
OK, so the subwoofer is working. Not only that, the majority of the sound is actually coming from it (the front speakers are actually very quiet, not sure how to fix that). The headphones still don't change focus from the main speakers though - the sound just plays through both the speakers and the headphones at once. I have to mute the main speakers in ossxmix (listed as two separate "int-black"'s in the first jack of codec1 - one for front speakers, one for subwoofer) if I want the speakers to be quiet while listening to headphones (listed as "green" in the same section).

I managed a bit of a cheap-and-nasty hack to get the sound to work at boot. I added the line:

```
apt-get install libsdl1.2debian-all --reinstall --force-yes -y
```

to my /etc/rc.local file. This seems to get the sound working at boot, although as I said, it's a really dirty hack to get something working that should be much simpler and more efficient to fix.

'Shady

---

### Post by PacShady on 2008-04-17
OK, still can't get KMix to work. I tried recompiling it from source even. KMix can't find the mixer device, so I get no sliders at all.

Also, the sound is fairly quiet, mostly through the main speakers (subwoofer volume isn't too bad). I checked the volumes in ossxmix, and they won't go up any higher. Any ideas on how I can boost the volume?

---

### Post by Yellow Pasque on 2008-04-18
Ok, I finally got Kubuntu 8.04 up and running and OSS installed. I, too, have no KMixer. IIRC correctly from the OSS4 forums, someone is working on a patch. I'll keep you updated.

---

### Post by PacShady on 2008-04-19
> **Temüjin said:**
> Ok, I finally got Kubuntu 8.04 up and running and OSS installed. I, too, have no KMixer. IIRC correctly from the OSS4 forums, someone is working on a patch. I'll keep you updated.

Thanks Temujin, you're a champ!

Do you know if there's any way of boosting the sound output beyond what ossxmix says is the maximum? The sound is clear as a bell (even better than my old laptop running ALSA, dunno if that's just because OSS is better, or because this laptop has high def sound), but it's just a bit quiet for my liking.

---

### Post by RenZO on 2008-04-26
PacShady, I have exactly the same hardware and same problem.
I managed to get sound with OSS4 :
[http://www.4front-tech.com/release/oss-linux_v4.0-1015_i386.deb](http://www.4front-tech.com/release/oss-linux_v4.0-1015_i386.deb)

And volume in gnome with this patch :
[http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz](http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz)

But I'm waiting for a solution working with alsa, to work in all software without any fight :)

---

### Post by PacShady on 2008-04-26
It could be some time before ALSA gets fixed, seems we're a low priority since this problem isn't very common. Feel free to confirm my bug reports, at least that might let them know I'm not the only one with this issue, and it might raise the priority a little.

'Shady

---

### Post by Yellow Pasque on 2008-04-29
> **PacShady said:**
> It could be some time before ALSA gets fixed, seems we're a low priority since this problem isn't very common. Feel free to confirm my bug reports, at least that might let them know I'm not the only one with this issue, and it might raise the priority a little.

'Shady
I tried to uninstall Ubuntu's kmixer and build a new one from source, but it was a nightmare. kmixer is part of the kde multimedia package (so much for modularity...) and it's not easy to figure out which packages are needed. However, I think it's doable since OSS is the default sound system in the build files.

I'm completely out of my element when dealing with K stuff. It just doesn't compute for me.

---

### Post by PacShady on 2008-04-29
> **Temüjin said:**
> I tried to uninstall Ubuntu's kmixer and build a new one from source, but it was a nightmare. kmixer is part of the kde multimedia package (so much for modularity...) and it's not easy to figure out which packages are needed. However, I think it's doable since OSS is the default sound system in the build files.

I'm completely out of my element when dealing with K stuff. It just doesn't compute for me.

I also tried this idea, and you're right, it's hard to split kmixer from the rest of kdemultimedia. I somehow managed to do it by removing references to the other packages in the main configure file. Still, the same problem seemed to happen (kmixer can't seem to find the sound card, and therefore has no channels to adjust), so either I didn't do it properly (ie. the messing around with the files I did screwed something up), or there's some other file/s somewhere that's still messing with it, or else kmixer is still not liking OSS.

*sigh* why did they decide to make ALSA the default sound server in the first place when they used to use OSS? It would've made things so much easier now.

'Shady

---

### Post by Yellow Pasque on 2008-04-29
WARNING: THE FOLLOWING TEXT IS A RANT

For the history on OSS and ALSA: [http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5)
But that's in the past...
Right now, OSS is the technologically superior sound system with awesome developers. The ALSA project started out as a workaround/hack and it shows in the coding and documentation on their site. In the past, I've tried to urge Ubuntu users towards OSS, but n00bs were very confused and some people thought of OSS3 as soon as the they read 'oss'. So I played along with the ALSA stuff and I really hate (I rarely use the word 'hate') their missing documentation. I learned more about ALSA from these forums than their site. Users have to conjure their speaker arrangement out of thin air (e.g. 3-stack, dell-3stack, lenovo, makeupaname). Basically, one has to dig through their (ever-changing) source code to figure out what options are available. Not very user friendly...

How about interacting with the developers? If you have a problem with OSS, you can go to the OpenSound forum ([http://www.opensound.com/](http://www.opensound.com/)) and if there really is a problem with the driver, there's a good chance 'dev' and/or 'Hannu' will get involved in solving it. ALSA? Check out their community portal: [http://www.alsa-project.org/main/index.php/AlsaProject:Community_Portal](http://www.alsa-project.org/main/index.php/AlsaProject:Community_Portal)

OK, I'm done. The only thing I could suggest to you is to try out the OSS 4.1 Mercurial repo. (I'm in the process of scripting a simple install).
```
sudo apt-get install mercurial build-essential gawk
sudo hg clone http://mercurial.opensound.com/ 

```

---

### Post by RenZO on 2008-05-03
We have the solution!
I explain how to do on alsa-project, thanks to Raymond :)

Maybe you want my patched module:
[http://poiresdujardin.free.fr/patch/snd-hda-intel_mitac8227_ubuntu_hardy_2.6.24-16.tar.gz](http://poiresdujardin.free.fr/patch/snd-hda-intel_mitac8227_ubuntu_hardy_2.6.24-16.tar.gz)

Extract the archive in your tree:
sudo tar -xvzf *.tar.gz -C /

Add the model in your /etc/modprobe.d/alsa-base :
options snd-hda-intel model=mitac


Enjoy !!!

---

### Post by PacShady on 2008-05-03
Thanks RenZO, your patch seemed to do the trick! My alsamixer is up and running, I have kmix working again, and most importantly SOUND!

Will this patch be included in the next update to alsa-driver?

---

### Post by PacShady on 2008-05-03
OK there is one problem I've found so far. So far I haven't been able to find a way to get my volume settings to save at shutdown and restore at reboot. I have to manually change the volume settings to the level I want each time the system is restarted. Any ideas on how to fix this?

---

### Post by PacShady on 2008-05-04
OK, I managed to get my sound to save and restore at boot, but I feel this is a bit of a cheap hack as well.

Add the line "alsactl restore 0" to /etc/rc.local
Add the line "alsactl store 0" under the line "echo -n "Stopping K Display Manager: kdm"" in /etc/init.d/kdm

It's a round about way of doing it, but it does the job. The only thing is it won't save the volume if KDE isn't shut down properly. But besides that, it should work.

---

### Post by PacShady on 2008-05-04
OK, the latest kernel update just borked the patch. Oh joy of joys :mad:

---

### Post by RenZO on 2008-05-04
Yes :)

*Replace this file in alsa-driver source:*
[http://poiresdujardin.free.fr/patch/patch_realtek_mitac8227.tar.gz](http://poiresdujardin.free.fr/patch/patch_realtek_mitac8227.tar.gz)

*And now compile:*
./configure --with-cards=hda-intel
make
sudo make install

*Copy the module in ubuntu alsa path:*
sudo cp /lib/modules/$( uname -r )/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/sound/alsa-driver/pci/hda

[I]Check the model in your /etc/modprobe.d/alsa-base:
[/I]options snd-hda-intel model=mitac

---

### Post by PacShady on 2008-05-04
Right, I seem to have managed to make a new patched module for the latest kernel update (2.6.24-17). It seems that, until the patch file is added to ALSA officially, the module will need to be recompiled manually each time the kernel is updated.

Instructions for doing so are as follows:
* download [alsa-driver-1.0.16 source]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2") and extract
* download [this patch]("http://poiresdujardin.free.fr/patch/patch_realtek_mitac8227.tar.gz") and extract to alsa-driver-1.0.16/alsa-kernel/pci/hda/
* configure by running "sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes", then 'sudo make' and 'sudo make install'
* run "sudo cp /lib/modules/$( uname -r )/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/sound/alsa-driver/pci/hda/"
* if you haven't done it yet already, be sure to add "options snd-hda-intel model=mitac" to the end of /etc/modprobe.d/alsa-base

---

### Post by PacShady on 2008-05-04
> **RenZO said:**
> Yes :)

*Replace this file in alsa-driver source:*
[http://poiresdujardin.free.fr/patch/patch_realtek_mitac8227.tar.gz](http://poiresdujardin.free.fr/patch/patch_realtek_mitac8227.tar.gz)

*And now compile:*
./configure --with-cards=hda-intel
make
sudo make install

*Copy the module in ubuntu alsa path:*
sudo cp /lib/modules/$( uname -r )/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/sound/alsa-driver/pci/hda

[I]Check the model in your /etc/modprobe.d/alsa-base:
[/I]options snd-hda-intel model=mitac

Seems we both had the same idea :) LOL

---

### Post by RenZO on 2008-05-04
LOL :)

Another question, what about the webcam on this laptop?

---

### Post by PacShady on 2008-05-04
The webcam, as well as the DVB TV tuner card that comes with it (well, it comes with the Medion MD96420, not sure about other laptops with the same chassis) don't work at all as of yet, and since they seem to be less important peripherals in the Linux world right now I don't like the chances of getting them up and running at all in the near future (my webcam on my old laptop, an ASUS A6Jc, still doesn't have any support). And by the time Linux has become popular enough for hardware manufacturers to start paying attention to us, this hardware will be old and out of date anyway :(.

There IS apparently a [third party driver]("http://www.reactivated.net/weblog/") in development for the webcam though, but if it ever gets finished it'll be a miracle. When one person has to take on the responsibility of making a foreign piece of equipment work in Linux in their spare time, it tends to fall into development hell :(.

 I have made bug reports for both though, the webcam bug is [here]("https://bugs.launchpad.net/ubuntu/+bug/215604"), and the DVB TV card is [here]("https://bugs.launchpad.net/ubuntu/+bug/215624"). So far though, they've got no attention.

*sigh* I wish I knew how to program. I'd be glad to do this sort of thing myself if I could, give my own back to the Linux community for all they've done for me :)

---

### Post by MickHardyHeron on 2008-06-28
hello....
thanks for all your solutions
the snd-hda-intel module which is already compiled for 2.6.24-16-generic kernel works very well!!
but when I try to compiled alsa driver with patch for 2.6.24-19-generic kernel, I have this error message :
```
/usr/src/modules/alsa-driver/pci/hda/patch_realtek.c: Dans la fonction «alc880_playback_pcm_open» :
/usr/src/modules/alsa-driver/pci/hda/patch_realtek.c:2322: erreur: trop peu d'arguments pour la fonction «snd_hda_multi_out_analog_open»
make[4]: *** [/usr/src/modules/alsa-driver/pci/hda/patch_realtek.o] Erreur 1
make[3]: *** [/usr/src/modules/alsa-driver/pci/hda] Erreur 2
make[2]: *** [/usr/src/modules/alsa-driver/pci] Erreur 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.24-16-generic »
make: *** [compile] Erreur 2
```
can you help me to correct this problem?

I try to add the "hinfo" argument but the consequence is a kernel panic!!!
can you tell me what I must correct in the patch please?

thx

---

### Post by MickHardyHeron on 2008-06-30
Finally, I found the solution...I don't read very well the previous message about the last kernel of ubuntu with this patch....I worked with official alsa-source of ubuntu while the message, before other mine, explained very well you must use alsa-driver-1.0.16 source and not alsa-source in ubuntu!
thx for all informations here! bye and sorry for my bad report of bug!

---

### Post by PacShady on 2008-07-03
OK, not sure if this is a glitch in my system at all, but it looks like Ubuntu's ALSA driver has been patched in the latest kernel for this card! YAY! Only problem is, if you need all those extra settings that were available for volumes and such using the patch in this thread, might be a good idea to keep using it, as the number of options is greatly shrunk (only about 4 or 5 volume sliders now as opposed to 10 or so).

'Shady

---

### Post by fahdovski on 2008-07-05
i don't have sound on kubuntu 7.1

lspci  :

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

HELP I NEED SOMEBODY   (beatles):guitar:

---

### Post by BacoKarel on 2008-07-14
Thank you guys for making the patch and info on how to use it.

I managed to get my sound working finally with it!

Still no official support (out-of-the-box) for the 82801H (mitec) card?

Kind regards,
Karel

---

### Post by tentotwo on 2008-07-23
Thanks PacShady, the patch works flawlessly on a Dell XPS M1330 running kernel 2.6.24-19-generic (even though I don't have the "ubuntu"-tree in my lib/modules/ directory). Excellent!

---

### Post by Yellow Pasque on 2008-07-23
For those using KDE/Kubuntu, the kmix not working with OSS4 issue has been reported as a bug along with the patch to make it work.
[http://bugs.kde.org/show_bug.cgi?id=166591](http://bugs.kde.org/show_bug.cgi?id=166591)

It looks like ALSA 1.0.17 supports the mitac keyword
> ALC883/888
	  ...
	  mitac		Mitac 8252D
	  ...

---

