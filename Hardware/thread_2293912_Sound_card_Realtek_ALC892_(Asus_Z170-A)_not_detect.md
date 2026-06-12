---
title: "Sound card Realtek ALC892 (Asus Z170-A) not detected, &quot;failed to add i915_bpo ...&quot;"
date: 2015-09-08
forum: Hardware
---

### Post by goutnet on 2015-09-08
Hi,

I am currently installing a new setup as my old decided to die a week ago, it is based on a MB from ASUS Z170-A ([specs here]("https://www.asus.com/Motherboards/Z170-A/specifications/")), after installing kubuntu 15.04 no big deals (little stuff to fix only), my only concern is about the sound though. I also have an nvidia 770GTX installed, and only the HDMI driver seems to be detected.

I am having a strange time figuring out the problem here:

- When I first installed, the sound card was detected, but not playing any sound (tried to activate it in amixer/kmix whatever, changing the outputs, but nothing)

after some meddling with different sw (not sure which), the sound card is now not detected anymore:

```
[FONT=courier new]# cat /proc/asound/cards[/FONT]
[FONT=courier new] 1 [NVidia         ]: HDA-Intel - HDA NVidia[/FONT]
[FONT=courier new]                      HDA NVidia at 0xdf080000 irq 17[/FONT]

```

what freaks me out is this:

```
# tree /proc/asound -L 2
/proc/asound
[COLOR=#ff0000][B]&#9500;&#9472;&#9472; card0
[/B][/COLOR]&#9500;&#9472;&#9472; card1
&#9474;   &#9500;&#9472;&#9472; codec#0
&#9474;   &#9500;&#9472;&#9472; eld#0.0
&#9474;   &#9500;&#9472;&#9472; eld#0.1
&#9474;   &#9500;&#9472;&#9472; eld#0.2
&#9474;   &#9500;&#9472;&#9472; eld#0.3
&#9474;   &#9500;&#9472;&#9472; id
&#9474;   &#9500;&#9472;&#9472; pcm3p
&#9474;   &#9500;&#9472;&#9472; pcm7p
&#9474;   &#9500;&#9472;&#9472; pcm8p
&#9474;   &#9492;&#9472;&#9472; pcm9p
&#9500;&#9472;&#9472; cards
&#9500;&#9472;&#9472; devices
&#9500;&#9472;&#9472; hwdep
&#9500;&#9472;&#9472; modules
&#9500;&#9472;&#9472; NVidia -> card1
&#9500;&#9472;&#9472; oss
&#9474;   &#9500;&#9472;&#9472; devices
&#9474;   &#9492;&#9472;&#9472; sndstat
&#9500;&#9472;&#9472; pcm
&#9500;&#9472;&#9472; seq
&#9474;   &#9500;&#9472;&#9472; clients
&#9474;   &#9500;&#9472;&#9472; drivers
&#9474;   &#9500;&#9472;&#9472; queues
&#9474;   &#9492;&#9472;&#9472; timer
&#9500;&#9472;&#9472; timers
&#9492;&#9472;&#9472; version



```

(there is a card0, but empty :/)

The card is still seen from the PCI bus:

```

# lspci | grep -i audio
[COLOR=#ff0000][B]00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
[/B][/COLOR]01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)

```

worse, it seems to be grabbed by the correct driver (relevant part of lspci -vv)

```

[COLOR=#ff0000]**00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)**
[/COLOR]        Subsystem: ASUSTeK Computer Inc. Device 8698
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at df240000 (64-bit, non-prefetchable) [size=16K]
        Region 4: Memory at df220000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
[COLOR=#ff0000]**        Kernel driver in use: snd_hda_intel**
[/COLOR]
```


indeed, the driver is loaded (snd_hda_intel), but for some reason the snd_hda_codec_realtek is not loaded… When I load it ```
modprobe snd_hda_codec_realtek
``` (just to see), it loads but it does not detect anything…

I initially thought that maybe the nvidia blob was to culprit, and tried to use nouveau (after rebooting off course), but no success here …

Even more strange, when I boot the Kubuntu 15.04, the card gets correctly detected (although still no sound, but at least it is shown in the list).

Digging a bit more into the messages, I found this:

```

[    4.122341] [drm] Initialized drm 1.1.0 20060810
[    4.136722] snd_hda_intel 0000:01:00.1: Disabling MSI
[    4.136726] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    4.151458] [COLOR=#ff0000]**snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)**[/COLOR]
[    4.154576] nvidia: module license 'NVIDIA' taints kernel.

```

(which does not appear in the kubuntu cd boot, based on 3.19.0.15-generic only a stone throw away from my installed version  3.19.0-26-generic). It also seem to imply that nvidia blob would be innocent (since loaded after the error message is thrown)

The only similar issue I could google is this one [http://www.linuxmintusers.de/index.php?topic=28788.0](http://www.linuxmintusers.de/index.php?topic=28788.0) (German speaking, I don't personally speak German, but luckily google translate does ;))

At this point I am a bit stuck (and out of time to be frank, since sound is not a critical part of my setup, I am more or less checking that on my limited free time).

I did not check (yet) on the driver code (which is my only available next step unless anybody could give me a pointer here).



Digging a bit in the archives, it seems that the [latter]("https://launchpad.net/ubuntu/+source/linux/3.19.0-26.28") includes [this patch]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1473547") which might be related:

> 
[COLOR=#333333][FONT=monospace]ALSA: hda/realtek - Add a fixup for another Acer Aspire 9420
[/FONT][/COLOR]

(again not looked at the code yet ... I am not really familiar with alsa code yet ...)

Anybody an idea before I fire my gVim here?

---

### Post by Yellow Pasque on 2015-09-08
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by goutnet on 2015-09-08
Awesome, upgrading ALSA solved it, thanks!

---

### Post by vpiercy on 2015-12-02
Update: Fixed by changing the line-in access for the headphones from front to the back of the PC. @@   See [https://rog.asus.com/forum/showthread.php?59557-Asus-G751JY-No-sound-on-Linux-Mint-17-1-Cinnamon&p=487281&viewfull=1#post487281](https://rog.asus.com/forum/showthread.php?59557-Asus-G751JY-No-sound-on-Linux-Mint-17-1-Cinnamon&p=487281&viewfull=1#post487281)  Comment #2 by kmROGFAN.

Having sound will sure help keep me working in Linux!


---
Darn. I appreciate the documentation here. Didn't work for me. I have no sound on an ASUS Z170. My command line outputs are similar to goutnet's, but not as dire (no missing "card 0"). I tried the ALSA upgrade and applied it to my Ubuntu 15.10 install. No go. I'll keep researching, but any suggestions would be wonderful. 

> van@Ubuntu-15:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf240000 irq 134
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdf080000 irq 17


van@Ubuntu-15:~$ tree /proc/asound -L 2
/proc/asound
&#9500;&#9472;&#9472; card0
&#9474;   &#9500;&#9472;&#9472; codec#0
&#9474;   &#9500;&#9472;&#9472; id
&#9474;   &#9500;&#9472;&#9472; pcm0c
&#9474;   &#9500;&#9472;&#9472; pcm0p
&#9474;   &#9500;&#9472;&#9472; pcm1p
&#9474;   &#9492;&#9472;&#9472; pcm2c
&#9500;&#9472;&#9472; card1
&#9474;   &#9500;&#9472;&#9472; codec#0
&#9474;   &#9500;&#9472;&#9472; eld#0.0
&#9474;   &#9500;&#9472;&#9472; eld#0.1
&#9474;   &#9500;&#9472;&#9472; eld#0.2
&#9474;   &#9500;&#9472;&#9472; eld#0.3
&#9474;   &#9500;&#9472;&#9472; id
&#9474;   &#9500;&#9472;&#9472; pcm3p
&#9474;   &#9500;&#9472;&#9472; pcm7p
&#9474;   &#9500;&#9472;&#9472; pcm8p
&#9474;   &#9492;&#9472;&#9472; pcm9p
&#9500;&#9472;&#9472; cards
&#9500;&#9472;&#9472; devices
&#9500;&#9472;&#9472; hwdep
&#9500;&#9472;&#9472; modules
&#9500;&#9472;&#9472; NVidia -> card1
&#9500;&#9472;&#9472; oss
&#9474;   &#9500;&#9472;&#9472; devices
&#9474;   &#9492;&#9472;&#9472; sndstat
&#9500;&#9472;&#9472; PCH -> card0
&#9500;&#9472;&#9472; pcm
&#9500;&#9472;&#9472; seq
&#9474;   &#9500;&#9472;&#9472; clients
&#9474;   &#9500;&#9472;&#9472; drivers
&#9474;   &#9500;&#9472;&#9472; queues
&#9474;   &#9492;&#9472;&#9472; timer
&#9500;&#9472;&#9472; timers
&#9492;&#9472;&#9472; version

14 directories, 21 files


van@Ubuntu-15:~$ lspci | grep -i audio
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)


van@Ubuntu-15:~$ uname -r
4.2.0-19-generic

---

### Post by subbabble on 2016-01-19
Hello,

I have a z170-A too, but I still can't get any sound. 

My Ubuntu version is 14.04.3 by default, but I followed this to upgrade kernel to vivid : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Upgrading to Vivid allowed me to have a working ethernet port (good thing I have a Wi-fi PCI card).
Then I upgraded DKMS with those instructions : [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
My current DKMS build is with this version oem-audio-hda-daily-lts-vivid-dkms_0.201601190701~ubuntu14.04.1_all.deb

Still this is what I get from dmesg :
> 
[   12.225231] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   12.225233] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.225234] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.225235] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   12.225236] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[   12.225237] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   12.225238] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   12.225239] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   12.225239] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   12.236749] snd_hda_intel 0000:00:1f.3: control 0:0:0:SPDIF Phantom Jack:0 is already present
[   12.236787] snd_hda_codec_realtek: probe of hdaudioC0D0 failed with error -16
[   12.237601] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   12.237603] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.237604] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.237605] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   12.237606] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[   12.237606] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   12.237608] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   12.237608] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   12.237609] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   12.249077] snd_hda_intel 0000:00:1f.3: control 0:0:0:SPDIF Phantom Jack:0 is already present
[   12.249114] snd_hda_codec_realtek: probe of hdaudioC0D0 failed with error -16
[   12.250301] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   12.250303] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.250304] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.250305] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   12.250306] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[   12.250307] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   12.250308] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[   12.250309] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[   12.250310] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[   12.261801] snd_hda_intel 0000:00:1f.3: control 0:0:0:SPDIF Phantom Jack:0 is already present
[   12.261834] snd_hda_codec_realtek: probe of hdaudioC0D0 failed with error -16
[   12.262839] snd_hda_codec_generic hdaudioC0D0: autoconfig for Generic: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   12.262841] snd_hda_codec_generic hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.262842] snd_hda_codec_generic hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.262843] snd_hda_codec_generic hdaudioC0D0:    mono: mono_out=0x0
[   12.262844] snd_hda_codec_generic hdaudioC0D0:    dig-out=0x11/0x1e
[   12.262844] snd_hda_codec_generic hdaudioC0D0:    inputs:
[   12.262846] snd_hda_codec_generic hdaudioC0D0:      Front Mic=0x19
[   12.262846] snd_hda_codec_generic hdaudioC0D0:      Rear Mic=0x18
[   12.262847] snd_hda_codec_generic hdaudioC0D0:      Line=0x1a
[   12.273129] snd_hda_intel 0000:00:1f.3: control 0:0:0:SPDIF Phantom Jack:0 is already present
[   12.273169] snd_hda_codec_generic: probe of hdaudioC0D0 failed with error -16
[   12.273172] hdaudio hdaudioC0D0: Unable to bind the codec


Would it help if I upgraded to Ubuntu 15.04 or 15.10 instead of trying with only Ubuntu 14.04?

Edit : installing 15.10 was enough to get both ethernet card and sound working.

---

### Post by john541 on 2016-04-04
> **subbabble said:**
> Hello,

I have a z170-A too, but I still can't get any sound. 

My Ubuntu version is 14.04.3 by default, but I followed this to upgrade kernel to vivid : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Upgrading to Vivid allowed me to have a working ethernet port (good thing I have a Wi-fi PCI card).
Then I upgraded DKMS with those instructions : [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
My current DKMS build is with this version oem-audio-hda-daily-lts-vivid-dkms_0.201601190701~ubuntu14.04.1_all.deb

Still this is what I get from dmesg :


Would it help if I upgraded to Ubuntu 15.04 or 15.10 instead of trying with only Ubuntu 14.04?

Edit : installing 15.10 was enough to get both ethernet card and sound working.



I have the same problem.  I have a Z170-A and I have no sound or ethernet.  I had to use an old dusty wifi card from my old PC to get on the Internet to troubleshoot.  I have Ubuntu 14.04

$ uname -r
3.13.0-83-generic



$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


How can I get my onboard ethernet and audio over hdmi to work?

---

### Post by john541 on 2016-04-04
fixed it by entering this command in terminal, although now I have wifi  and ethernet I don't have any network indicator in the upper panel, but  one of the network connections must be working for me to be able to post  this!



sudo apt-get install --install-recommends  linux-generic-lts-wily xserver-xorg-core-lts-wily xserver-xorg-lts-wily  xserver-xorg-video-all-lts-wily xserver-xorg-input-all-lts-wily  libwayland-egl1-mesa-lts-wily




this updates things to a new kernel, fyi

---

### Post by antriana81 on 2016-10-11
It worked. Thank you :D

---

