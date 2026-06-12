---
title: "Nvidia GT220 &amp; Audio Device  &quot;0be2&quot;"
date: 2009-11-05
forum: Hardware
---

### Post by darkscout on 2009-11-05
I just bought an OEM GT220 on eBay, it is the PCI version of the GT216. It's also the highest end [VDPAU Feature Set C]("http://en.wikipedia.org/wiki/VDPAU") chip available for the desktop. I've seen numerous references to it including an audio decoder on board (instead of having SPDIF in).

Sure enough it shows up:
```
> 03:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
```However linux has no clue what it is and ALSA doesn't know how to use it. Does anyone have any patches or hacks to get this working?

I currently have
```
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)

```On board, but without getting the '0be2' working I can't get audio out via HDMI.

---

### Post by darkshadow on 2009-11-05
I feel your pain I have a GTS 250M and can't get the hdmi audio working because I can't get the audio device working. Although mine is 0be4. Hopefully they are close enough that drivers can be made for both of us easily.

---

### Post by jocefus on 2009-11-07
I have read someone got it to work with aplay, as in speaker test. However, still no sound. I have geforce 210 with this device:
 
02:00.1 **[COLOR=#ff0000]Audio[/COLOR]** **[COLOR=#ff0000]device[/COLOR]**: nVidia Corporation **[COLOR=#ff0000]Device[/COLOR]** 0be3 (rev a1)

It shows no kernel modules or drivers loaded for this device, and aplay of course doesn't see it.
 
This is the forum where I was reading:
 
[http://www.nvnews.net/vbulletin/showthread.php?t=140264](http://www.nvnews.net/vbulletin/showthread.php?t=140264)

---

### Post by darkscout on 2009-11-13
Anyone making any headway?

---

### Post by jstapels on 2009-11-14
I'm in the same boat as everyone else. Hopefully someone gets this working soon in ALSA.

```
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GT 220] (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
```

---

### Post by sherl0k on 2009-11-17
could you please paste the outputs of your aplay -l and aplay -L ?

---

### Post by jstapels on 2009-11-17
> **sherl0k said:**
> could you please paste the outputs of your aplay -l and aplay -L ?

Sure, not a problem. I'm running Karmic with the latest nvidia drivers from the nvidia-vdpau PPA. I haven't tried the latest ALSA dev nor any of the GT 220 patches floating around.

```
jstapels@media:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
jstapels@media:~$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```

It's a P55 chipset on the MB, so I assume everything is from that.

---

### Post by syoung on 2009-11-19
Chiming in to say that I'm also experiencing the same issue with a GT 220 in 9.10 and the 190.32 drivers.

---

### Post by David Grigor on 2009-12-03
I just installed a asus gt220 last night which also has the native hdmi sound builtin.  Hindsight, you probably better off choosing a 220 that uses the spdif jumper to supply sound to the hdmi. 

aplay -l only shows the onboard sound devices. 

The video works like a champ on the highest vdpau interlace settings which I'm very pleased with compared to the onboard 8200 it replaced.  


What commands are you using to see this ? 

01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

So I can check to see if I at least get that far as well.

---

### Post by jstapels on 2009-12-03
> **David Grigor said:**
> What commands are you using to see this ? 

01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

So I can check to see if I at least get that far as well.

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
```

---

### Post by commander_tux on 2009-12-07
[http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21](http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21)
> ALSA: hda - Support NVIDIA 8 channel HDMI audi 

Looks like support comes in ALSA 1.0.21, whereas the default Karmic repositories are sitting at 1.0.20. Things should be working soon enough.

---

### Post by QuanTime on 2009-12-07
ubuntu 9.10 x64, laptop with nvidia GT 220M 1gb gfx and audio.

System -> Administration -> Hardware Drivers

NVIDIA Accelerated gfx drivers (Version 185) (Reccomended)

Just installed that propietry driver, fixed all my issues.
Hope your solution is as easy.

---

### Post by David Grigor on 2009-12-07
> **commander_tux said:**
> [http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21](http://www.alsa-project.org/main/index.php/Changes_v1.0.20_v1.0.21)


Looks like support comes in ALSA 1.0.21, whereas the default Karmic repositories are sitting at 1.0.20. Things should be working soon enough.

One of the first things I did was update to alsa 1.0.21 and alsaconf still doesn't recognize the sound yet.

If you choose a gt220 card that uses spdif jumper from your motherboard to supply the sound for hdmi you would be good to go.

---

### Post by novellahub on 2009-12-07
> **David Grigor said:**
> One of the first things I did was update to alsa 1.0.21 and alsaconf still doesn't recognize the sound yet.

If you choose a gt220 card that uses spdif jumper from your motherboard to supply the sound for hdmi you would be good to go.

Where would you find a GT220 card with the SPDIF onboard?  My understanding is the GT series of cards no longer offers this as a option.  The only Nvidia 8000 and 9000 series of cards have the SPDIF capability.

---

### Post by jstapels on 2009-12-07
> **novellahub said:**
> Where would you find a GT220 card with the SPDIF onboard?  My understanding is the GT series of cards no longer offers this as a option.  The only Nvidia 8000 and 9000 series of cards have the SPDIF capability.

I believe some manufacturers still included the passthrough as an option, although it may have only been for the prerelease review boards.

Phoronix mentioned a passthrough in their [review](http://www.phoronix.com/scan.php?page=article&item=nvidia_gt_220&num=1) of the GT220.

---

### Post by darkshadow on 2009-12-18
These audio devices are supported in the new Alsa 1.0.22, I have not got to try them yet since I am waiting for a ppa to compile them.

---

### Post by novellahub on 2009-12-18
Alsa Changelog:

[http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22](http://www.alsa-project.org/main/index.php/Changes_v1.0.21_v1.0.22)

> 
HDA Intel driver

    ALSA: hda - Add PCI IDs for Nvidia G2xx-series 


Hopefully the ALSA upgrade scripts will be modified shortly.  I have ran the script in the past with success.

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by jstapels on 2009-12-18
I saw the release news on Phoronix, will post my results as soon as I get my ALSA updates.

---

### Post by darkshadow on 2009-12-18
I tried manually compiling and my results are mixed. with 0be4

The good: lshw shows that my hdmi is now claimed by the module

The bad: "aplay -l" and every other thing I could think of no longer list any devices. Even my built in sound card that worked before is missing.

I have went back to repo software until someone better compile it. Even though I did not notice any problems especially with alsa-driver which is the most important.

cat /proc/asound/version does show me at 1.0.22

---

### Post by David Grigor on 2009-12-18
Awesome news about 1.022. I was imagining it would take much longer to get it supported. 

Leaving for Christmas holidy but will upgrade it as soon as I get back and give it a try.

---

### Post by darkshadow on 2009-12-18
I gave it another try but got the same results. It is strange that it broke my built in that worked before.


$ sudo lshw -C multimedia -numeric
 *-multimedia
      description: Audio device
      product: nVidia Corporation [10DE:BE4]
      vendor: nVidia Corporation [10DE]
      physical id: 0.1
      bus info: pci@0000:01:00.1
      version: a1
      width: 32 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list
      configuration: driver=HDA Intel latency=0
      resources: irq:38 memory:cdefc000-cdefffff
 *-multimedia
      description: Audio device
      product: 5 Series/3400 Series Chipset High Definition Audio [8086:3B56]
      vendor: Intel Corporation [8086]
      physical id: 1b
      bus info: pci@0000:00:1b.0
      version: 05
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress bus_master cap_list
      configuration: driver=HDA Intel latency=0
      resources: irq:36 memory:f0800000-f0803fff
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.
Compiled on Dec 18 2009 for kernel 2.6.31-17-generic (SMP).
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
$

---

### Post by moonshine2b1 on 2009-12-18
sorry i like only ati chip it is the best

---

### Post by darkscout on 2009-12-20
> **moonshine2b1 said:**
> sorry i like only ati chip it is the best

How's that VDPAU and CUDA running on ATI chips? I heard ATI finally got their crap out for Linux but 

-

Showing up as a device now under lspci, but not aplay.

[PHP]
03:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GT 220] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device 069a
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at ce000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at c0000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

03:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: nVidia Corporation Device 069a
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 5
    Region 0: Memory at faffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
[/PHP]

---

### Post by darkshadow on 2009-12-20
I got mine to show up in aplay using the following patch on the source. It ended up showing and alsamixer has a control for it. (just spdif) but I could not get any sound to come out from my receiver. Sound preferences only give me a stereo output option for it.

I still can't get my built in to work, which uses the same module so they must of broke something generic.

[http://article.gmane.org/gmane.linux.alsa.devel/69250](http://article.gmane.org/gmane.linux.alsa.devel/69250)

---

### Post by Henk Poley on 2009-12-24
I've compiled ALSA 1.0.22 using: [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Don't hear a peep in MythTV though. Tried it to ALSA:hdmi and ALSA:Default as sound output device.

Also, `aplay -L` only shows the null device (no sound)

My hardware:
```
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GT 220] (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
```

After re-enabling onboard sound even that doesn't show up after alsaconf configured it, and alsamixer doesn't show any controls for both cards. Back to 1.0.20 we go.

After installing linux-backports-modules-alsa-2.6.31-16-generic & linux-backports-modules-alsa-karmic-generic sound seems to work again with the card on my motherboard. Except still no sound in MythTV.

Trying if `sudo aptitude reinstall linux-image-2.6.31-16-generic` fixes the problem.

Oh joy, my TV suppresses analog audio when the card supplies audio over HDMI or DVI. Just tested it with music on my iPhone.

---

### Post by jstapels on 2009-12-24
> **Henk Poley said:**
> Oh joy, my TV suppresses analog audio when the card supplies audio over HDMI or DVI. Just tested it with music on my iPhone.

I had the same problem with I tried using a DVI cable with analog audio. The TV would ignore the analog audio and try to use the (dead) audio signal. To get around this I created a custom EDID file to tell Nvidia the TV doesn't support audio, which in turn prevents the driver from sending a signal.

Do a google search, there's a couple of How-To's out there. If you get stuck let me know and I can help you out. The basic approach is:

[LIST=1]
[*]Use nvidia-settings to grab your current EDID.
[*]Hexedit out the advanced config blocks.
[*]Recalculate the checksum, and update the hex file with it.
[*]Reference the custom EDID from xorg.conf (eg. Option         "CustomEDID" "DFP-0:/etc/X11/samsung71f.bin")
[/LIST]

---

### Post by Henk Poley on 2009-12-24
I'll try your hack soon jstapels. For the moment -pss, it's christmas eve- I run over VGA @ 1360x768@60Hz, but with VDPAU :-)

Edit: also tried the most recent ALSA snapshot, still both my onboard and GT220 audio are not recognised.

---

### Post by darkshadow on 2009-12-24
You can get the latest snapshot to work? Whenever I try it I get a error about the snd module loading a duplicate symbol (gcd) that is already owned by the kernel.

It is driving me crazy since I really need hdmi audio for Christmas day or I will have to use Windows which is not setup with a lot of other stuff I need.

---

### Post by MaxCarnage on 2009-12-24
Howdy,

This is hopefully the right thread for this. 

This afternoon I bought a GeForce GT 220 after being unable to get WoW running on my old ATI card. Everything seemed to be working when I realized that my sound was no longer playing at all. I looked at the default sound controller in the panel and there was no hardware present. The output was set to "Dummy Output". I did a an lspci | grep Audio and the results are below:

> lspci -v | grep Audio
02:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

Note that the on-board HDA device is no longer listed. An aplay -l reveals that no devices are found at all. When I go to alsamixer, however, it seems to see my HDA device:

>  Card: HDA NVidia

I ran a script to update to ALSA 1.0.22 and it seems to have worked successfully:

> cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.
Compiled on Dec 24 2009 for kernel 2.6.31-16-generic (SMP).

When I run sudo alsaconfig it sees my new video card but not the HDA device as far as I can see. I have tried various things to troubleshoot the issue, including uninstalling the video drivers and booting into the 2.6.31-14 kernel, but the HDA device will simply not show up in the lspci. I am at a complete loss as to how to get my audio back.

---

### Post by darkshadow on 2009-12-25
I have the same problem with 1.0.22 both my hdmi and built-in don't work.

Going back to 1.0.21 fixes the built-in (no support for the hdmi) since they seem to of totally broke snd-hda-intel in the latest release.

A easy way is to reinstall all the alsa packages and linux-image which will give you 1.0.20

Or just install linux-backports-modules-alsa-karmic-generic which installs 1.0.21 to a separate place that get priority when loading modules if it exists.

---

### Post by MaxCarnage on 2009-12-25
> **darkshadow said:**
> I have the same problem with 1.0.22 both my hdmi and built-in don't work.

Going back to 1.0.21 fixes the built-in (no support for the hdmi) since they seem to of totally broke snd-hda-intel in the latest release.

A easy way is to reinstall all the alsa packages and linux-image which will give you 1.0.20

Or just install linux-backports-modules-alsa-karmic-generic which installs 1.0.21 to a separate place that get priority when loading modules if it exists.

I'll definitely give that a shot, as I am not concerned about the HDMI audio.

---

### Post by MaxCarnage on 2009-12-25
Simply installing the backports didn't work, so I purged ALSA and removed the backports and am now running the ALSA script to install 1.0.21. I am pretty sure that's what I had on here before, but we'll see if that re-enables my on-board sound card.

---

### Post by Henk Poley on 2009-12-25
> **darkshadow said:**
> You can get the latest snapshot to work? Whenever I try it I get a error about the snd module loading a duplicate symbol (gcd) that is already owned by the kernel.
Same thing. Though I just use VGA now (1360x786@60Hz not 1080p :-() + analog audio

---

### Post by Henk Poley on 2009-12-25
> **darkshadow said:**
> A easy way is to reinstall all the alsa packages and linux-image which will give you 1.0.20
Yes, that's the way. Full walkthrough:
```
$ dpkg -l | grep linux-image-`uname -r`
ii  linux-image-2.6.31-16-generic                  2.6.31-16.53                                               Linux kernel image for version 2.6.31 on x86/x86_64
$ sudo aptitude reinstall linux-image-2.6.31-16-generic
[blahblah]
$ dpkg -l | grep alsa-
ii  alsa-base                                      1.0.20+dfsg-1ubuntu5                                       ALSA driver configuration files
ii  alsa-utils                                     1.0.20-2ubuntu6                                            ALSA utilities
$ sudo aptitude reinstall alsa-base  alsa-utils
[blahblah]
$ dpkg -l | grep libasound
ii  libasound2                                     1.0.20-3ubuntu6                                            shared library for ALSA applications
ii  libasound2-dev                                 1.0.20-3ubuntu6                                            shared library for ALSA applications -- development files
$ sudo aptitude reinstall libasound2 libasound2-dev
[blahblah]
```

---

### Post by MaxCarnage on 2009-12-25
> **Henk Poley said:**
> Yes, that's the way. Full walkthrough:
```
$ dpkg -l | grep linux-image-`uname -r`
ii  linux-image-2.6.31-16-generic                  2.6.31-16.53                                               Linux kernel image for version 2.6.31 on x86/x86_64
$ sudo aptitude reinstall linux-image-2.6.31-16-generic
[blahblah]
$ dpkg -l | grep alsa-
ii  alsa-base                                      1.0.20+dfsg-1ubuntu5                                       ALSA driver configuration files
ii  alsa-utils                                     1.0.20-2ubuntu6                                            ALSA utilities
$ sudo aptitude reinstall alsa-base  alsa-utils
[blahblah]
$ dpkg -l | grep libasound
ii  libasound2                                     1.0.20-3ubuntu6                                            shared library for ALSA applications
ii  libasound2-dev                                 1.0.20-3ubuntu6                                            shared library for ALSA applications -- development files
$ sudo aptitude reinstall libasound2 libasound2-dev
[blahblah]
```

Thanks for that; unfortunately it made no difference. I am starting to feel like I'm hitting a brick wall; is a wipe-and-reload worth a shot? I don't know what else to do here.

---

### Post by Henk Poley on 2009-12-25
Sound over HDMI with GT220 will not work for the forseeable time (I don't expect it before jan 1st.). You could try getting other sound devices working and using that.

---

### Post by MaxCarnage on 2009-12-25
> **Henk Poley said:**
> Sound over HDMI with GT220 will not work for the forseeable time (I don't expect it before jan 1st.). You could try getting other sound devices working and using that.

That's what I've been trying to do, and now I feel kind of stupid.

I booted into a Live CD to see if it would be any different and it was not. Then I realized that I made a major hardware change to my computer yesterday (new video card) and never checked the BIOS settings. My video adapter was set to PCI, not PCI-E, and the on-board audio was set to Automatic. I changed it to Enabled and booted into my OS and wa-la; audio has been restored.

Good luck to you guys trying to get HDMI audio working; 1.0.22 sees the audio device but doesn't seem able to use it.

---

### Post by gaelfx on 2010-01-13
I just built a handy-dandy new box and threw in a Gigabyte GV-N220OC - 1GI (I remember the name due to repeated searches for it on a Chinese website), which features the GT220 chipset, so I wanna throw my two cents in on this subject.

First, there is no SPDIF in on the card, and I'm fairly certain that this is not available on any of the GT series chipsets as I've looked at quite a few in the shops around here and none of them seem to have that, though a couple did have connectors for extra power.

Second, I took my box to one of the local TV stores (they were impressed by the Compiz Desktop effects making the windows jiggle like jello), but were confused, like me, by the fact that there was no audio with the video. I had downloaded (with a borrowed monitor) the nVidia 190.53 driver, which is the one recommended on the site and installed it fine, so the video on the 47" LED I was testing out worked fine, the only issue was the audio.

Third, this issue has been brought up on the nvnews forums and someone claimed that HDMI audio is not supported by Linux yet, which I can't testify to in any way whatsoever, but it does seem that this is not a problem localized to Ubuntu.

Since I haven't bought the TV yet and I had to return the borrowed display, I have no way of checking all the useful hardware info at the moment, but I do remember lspci returning the nVidia audio device with the 0be2 at the end of it, but I seem to recall that the Realtek onboard audio chipset was not displayed in lspci, which seemed strange to me considering I could plug in headphones (into the front or back) and they seemed to work. I would really like to see audio working through HDMI, but as I plan on buying a receiver and hooking up a nice sound system, I suppose it is not necessary. It would just be a LOT more convenient for me as it would eliminate one extra set of wires running into the receiver. Has everyone given up on this for now? Has anyone tried the beta drivers for the card (I believe it was 195.30)? Has anyone ever gotten lspci to identify both onboard audio AND nVidia audio at the same time? It seems like this problem should be solvable, it just feels like I'm missing a small detail about how the set up should work.

---

### Post by gaelfx on 2010-01-13
I found a *bit* of useful information on this problem:

[http://mailman.alsa-project.org/pipermail/alsa-devel/2009-December/024231.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-December/024231.html)

It seems that nVidia is working on this problem, though I looked into the month of January as well and it seems there has been no activity on it as of yet. Might be worth paying attention to this, although whether or not it ends up in the new driver is probably an entirely different question.

---

### Post by jstapels on 2010-01-13
> **gaelfx said:**
> Has anyone ever gotten lspci to identify both onboard audio AND nVidia audio at the same time? It seems like this problem should be solvable, it just feels like I'm missing a small detail about how the set up should work.

I have a different Gigabyte MB, but as I posted in my earlier post:

```

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)

```

So my system is aware of both the onboard Intel audio and the nVidia audio device. Could it be that your onboard is on the USB instead of the PCI bus? Check lsusb and see if it shows up there.

---

### Post by gaelfx on 2010-01-13
I'll have to wait til I can find another screen to use with it before I can check that, though I don't think it would be listed on USB since it's in the PCIE slot. I'll report back here once I find out, thanks for the idea.

---

### Post by jstapels on 2010-01-14
> **gaelfx said:**
> I'll have to wait til I can find another screen to use with it before I can check that, though I don't think it would be listed on USB since it's in the PCIE slot. I'll report back here once I find out, thanks for the idea.

Your onboard audio is in your PCIE slot? I'm sorry, I guess I misunderstood your original question...

---

### Post by gaelfx on 2010-01-14
No, it's totally my fault, I completely misunderstood your question because I wasn't paying close enough attention. I meant the graphics card is in the PCI-E slot and that IT'S onboard audio chip shouldn't show up on lsusb, but now that I've had some caffeine, I know to tell you that I can't recall if the Realtek onboard audio is connected through a USB interface. Maybe I'll try plugging in the box to my network and then try to SSH in to get the info, then I'll actually answer your question. Sorry about that, against doctor's orders, I sometimes use computers without thinking.

---

### Post by gaelfx on 2010-01-19
Ok, I finall got the TV to test out on, and lspci does list both audio components, I simply didn't notice before because I wasn't grepping. aplay -L, on the other hand, only seems to recognize the various methods of output for the Realtek onboard audio. Using separate speakers, the audio is fine and everything, but a bit of an inconvenience for obvious reasons. I guess we'll just have to hold tight while nVidia works their magic on the new drivers.

---

### Post by jammen33 on 2010-01-19
i also have a gt220 and cannot get the audio to work

i installed the beta drivers from nvidia (195.30 BETA) and no change; so i guess we just have to keep waiting.

---

### Post by gaelfx on 2010-01-20
Yeah, I would suggest waiting until the list of changes under tha beta drivers on nVidia's website actually say something regarding HDMI audio. You can also try checking the alsa mailing lists, but it looks like any questions that go in there never get a reply. I put a question into nVidia's support site, but so far no response, and that was about two days ago now. Just hold tight though, I really do think SOMEONE is working on this, maybe they're just too busy to actually tell anyone about the headway they are (or aren't) making with it.

---

### Post by TycoonX on 2010-02-05
Hi,

Any news regarding this issue?
I have just mistakenly bought a GeForce 210, since i missed this thread

I have the same problem as everyone, should i get this card replaced? any hope?

please help

---

### Post by dborn on 2010-02-06
Sorry I can't offer any help (I wish I could) but I'm with you on this. I have a MythTV setup (more than $1000 invested) sitting idle waiting for this issue to be resolved. So count me as interested too... :-/

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4771](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4771)

This issue is opened and considered "minor" (not to me!) and remains unresolved. No new update since 1 month now.

Sigh...

---

### Post by TycoonX on 2010-02-07
I've managed to output audio over HDMI with my GeForce 210.

Refer to this thread:
[http://xbmc.org/forum/showthread.php?p=502129#post502129](http://xbmc.org/forum/showthread.php?p=502129#post502129)

---

### Post by PlantHead on 2010-02-16
GT 220.
Followed the wiki article in the above post and I now have sound through my HDMI port.

Link to wiki
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)

---

### Post by a-user on 2010-02-23
i managed to get sound over my hdmi of my gt220 too BUT neither flash videos within browser nor the xbmc menu sounds get over it.

so i have sound from every source over the hdmi except flash videos movie sounds in ff and the xbmc menu sounds. especially the one with flash is very anoying.

additionally i observed a strange thing: if i disable the onbord sound (i have onbord + the gt220) i dont get any sound at all. but the pulseaudio controls tell me i have sound. everything plays and tells me that i should here something but it is nothing to hear. only if i activated also the onbord sound in the bios.

but if i have both activated the module for the onbord sound seems to crash everytime i try to use the onbord sound - not that i want it, but i tried it.

anybody have sound ober the gt220 hdmi AND have sound in firefox from flash movies?

---

### Post by novellahub on 2010-03-12
> **a-user said:**
> i managed to get sound over my hdmi of my gt220 too BUT neither flash videos within browser nor the xbmc menu sounds get over it.

so i have sound from every source over the hdmi except flash videos movie sounds in ff and the xbmc menu sounds. especially the one with flash is very anoying.

additionally i observed a strange thing: if i disable the onbord sound (i have onbord + the gt220) i dont get any sound at all. but the pulseaudio controls tell me i have sound. everything plays and tells me that i should here something but it is nothing to hear. only if i activated also the onbord sound in the bios.

but if i have both activated the module for the onbord sound seems to crash everytime i try to use the onbord sound - not that i want it, but i tried it.

anybody have sound ober the gt220 hdmi AND have sound in firefox from flash movies?

I believe you need to do the following:

Navigate to System > Preferences > Sound  

In the hardware tab choose HDMI out for the hardware profile.

---

### Post by a-user on 2010-03-15
ofcourse i already did that or otherwise i wouldn't had system sounds and sound rfom other application as i already said.

edit: oh and when i disabled the onbord sound i repeated the settings but dont have anysound although the system tools tell me it is being played over hdmi.

---

### Post by darkshadow on 2010-04-17
CONFIRMED WORKING

I have just successfully got HDMI audio working on my 0be4 video card.

I used the newly released Alsa 1.0.23 version

A caveat is that it did not work over Pulse Audio though even though it showed up as a choice I only ever got random "pops" out of the speakers, and was stereo only.

My working steps

Must have video out over HDMI at the same time (cloned output worked for me)
I used this command to get it working

mplayer video.mkv -ao alsa:device=plughw=1.3

Second test
speaker-test -c2 -D plughw:1,3

---

### Post by darkshadow on 2010-04-17
I did a little more testing and came across a bug. I recommend using 1,9 instead of 1,3 it turns out you have to use 1,9 first after every boot to initialize the others (1,3 + 1,7 + 1,8)

It would be easier to just always use 1,9 then trying to do it first then switch to another. 

I have found no difference between the four devices other then that.

---

### Post by darkshadow on 2010-04-17
One more update:
Pulse Audio does work if you use mplayer to start 1,9 first (after every boot)
I am trying to find a way to force Pulse to just default to 1,9

Also good news I got full 5.1 surround when using ac3/dts passthrough (which is 99% of the time you need it anyway)

So the best command for movies with mplayer now is
mplayer -ao alsa:device=plughw=1.9 -afm hwac3 video.mkv

---

### Post by novellahub on 2010-04-22
> **darkshadow said:**
> One more update:
Pulse Audio does work if you use mplayer to start 1,9 first (after every boot)
I am trying to find a way to force Pulse to just default to 1,9

Also good news I got full 5.1 surround when using ac3/dts passthrough (which is 99% of the time you need it anyway)

So the best command for movies with mplayer now is
mplayer -ao alsa:device=plughw=1.9 -afm hwac3 video.mkv

To enable pulse audio on boot, try doing these instructions:

[XBMC Pulse Audio Link](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240#PulseAudio_Configuration)

---

### Post by ngupta on 2010-05-07
I got GeForce 210 working with Karmic Koala 9.10. Both video and audio works over HDMI. See my response here:

[http://ubuntuforums.org/showthread.php?p=9257882#post9257882](http://ubuntuforums.org/showthread.php?p=9257882#post9257882)

---

### Post by Marktrix on 2010-05-25
x

---

### Post by jay214128 on 2010-05-31
> **novellahub said:**
> I believe you need to do the following:

Navigate to System > Preferences > Sound  

In the hardware tab choose HDMI out for the hardware profile.

When I do that, I don't get an HDMI choice to select.  Only the motherboard analog and digital devices (IEC958).  How do I get the GT220 HDMI audio device to show up?  This is with a new install of 10.04 LTS.

---

### Post by novellahub on 2010-05-31
> **jay214128 said:**
> When I do that, I don't get an HDMI choice to select.  Only the motherboard analog and digital devices (IEC958).  How do I get the GT220 HDMI audio device to show up?  This is with a new install of 10.04 LTS.

I had to update ALSA first.  

[ALSA Upgrade Script](http://ubuntuforums.org/showthread.php?p=6589810)

I posted more detail in my blog link below.

---

### Post by a-user on 2010-06-01
i observed a strange behaviour with (i guess) that new alsa. if im using the sound device for several hourse, say playing music, it then stops. trying to restart the sond file or a video file results in a freeze of the playersoftware.

first i thought it has something to do with compize cause it went up to 100% cpu usuage. and when i killed compiz it wokred again. but same happens without compize.

this is only observable if you play something for more than 2 hours.

i will try again the older 1.0.22.1 alsa drivers.

---

### Post by jay214128 on 2010-06-14
> **novellahub said:**
> I had to update ALSA first.  

[ALSA Upgrade Script](http://ubuntuforums.org/showthread.php?p=6589810)


I followed the alsa upgrade instructions and now I get an HDMI audio device.  The output of aplay -l:

[FONT="Fixedsys"]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/FONT]

The output of cat /proc/asound/cards:

[FONT="Fixedsys"]0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbff8000 irq 32
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfaffc000 irq 16[/FONT]


When I run speaker-test -Dplughw:1,3 -c2, I get no sound.  The test appears to be running, though.  I checked alsa-mixer, but there is no HDMI device listed there to unmute.

What should I check next?

---

### Post by jaakan on 2010-07-01
you don't need to update alsa to get it working with 10.04.


[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/550655]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/550655")

Here is how I got my gt220 before my motherboard/cpu went up.



```
    
 -- at command line

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa

 -- then 

install linux-alsa-driver-modules-2.6.xx-xx( matches your kernel )

 -- at command line

sudo vim /etc/modprobe.d/sound.conf

-- add the following for NV GT220 -- "aplay -l" will tell you which of the following to use

options snd-hda-intel enable_msi=0 probe_mask=0xfff2 # if your device is 0,3

or 

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2 # if your device is 1,3

or

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xffff,0xfff2 # if your device is 2,3


-- save and reboot

-- then do the following -- I used 1,3 because I used 2 audio outout devices at the time, you might need to use 0,3 or 2,3 etc...

aplay -D plughw:1,3 /usr/share/sounds/alsa/Noise.wav
speaker-test -Dhdmi:NVidia_1 -c6
```

---

### Post by jay214128 on 2010-07-01
I have not gotten past step 2.  I'm a noob at this.

I successfully added the "ppa:ubuntu-audio-dev/ppa" PPA.

I am unable to do the next step (install linux-alsa-driver-modules-2.6.xx-xx( matches your kernel )).  What command do I use here?  I tried many incantations of 'apt-get install' and apt could not find the matching package.

The instructions then say to edit the /etc/modprobe.d/sound.conf file.  I don't have this file on my system.  There is an /etc/modprobe.d/asound.conf file (I think that is what it was called), but no sound.conf.  Am I supposed to create this file?  Did you mean the asound.conf file instead?

My GT220 will end up being card 1, since card 0 is the onboard audio device (analog & SPDIF), as indicated by 'aplay -l'.

Jay

---

### Post by jaakan on 2010-07-01
> **jay214128 said:**
> I have not gotten past step 2.  I'm a noob at this.

I successfully added the "ppa:ubuntu-audio-dev/ppa" PPA.

I am unable to do the next step (install linux-alsa-driver-modules-2.6.xx-xx( matches your kernel )).  What command do I use here?  I tried many incantations of 'apt-get install' and apt could not find the matching package.

The instructions then say to edit the /etc/modprobe.d/sound.conf file.  I don't have this file on my system.  There is an /etc/modprobe.d/asound.conf file (I think that is what it was called), but no sound.conf.  Am I supposed to create this file?  Did you mean the asound.conf file instead?

My GT220 will end up being card 1, since card 0 is the onboard audio device (analog & SPDIF), as indicated by 'aplay -l'.

Jay

run "uname -a" to get the currently installed/active kernel
for me it's "linux-image-2.6.32-23-generic" 

open up "synaptic" , System > Admin... > Synaptic Package Manager  

and do a search for "2.6.32" 

now look for 

linux-alsa-driver-modules-2.6.32-23 

if it is there install it.

the current version of linux-alsa-driver-modules as of me typing is 13 hours old ( -22 and not -23 ) so you need to wait a day or two for the matching version to show up

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+packages](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa/+packages)

you could always 

install "linux-image-2.6.32-22-generic" + "linux-alsa-driver-modules-2.6.32-22"
and remove linux-image-2.6.32-23-generic until -23 comes out

hope that helps
Jaakan

---

### Post by jaakan on 2010-07-01
you will need to create the .conf file 

"sudo gedit /etc/modprobe.d/sound.conf" 
gedit will be easier for you to use than vim

I use both but mostly vim at work.


in your case you would add only the following to that file 

```
options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
```

---

### Post by jay214128 on 2010-07-16
Thanks, jaakan.  I have had some mixed results.  After creating the sound.conf file, and rebooting, I could then get speaker-test to play sound via HDMI (yeah).  I also needed to unmute the HDMI audio device (card 1) in alsamixer.  I had to use F6 to select card 1 for it to even show up.

I still had only analog sound from the system and my applications.  I tried to run the System->Preferences->Default Sound Card to select the HDMI audio as my default sound card, but this application no longer runs.  It tries to start (shows up for about 10 seconds in the task bar) but then exits.  Is this expected?

A few reboots (days) later, I discovered that HDMI sound was working for some of my applications (vlc, mplayer, movieplayer), but still only analog for the system sounds.

Today I booted up and no sound at all.  I checked alsamixer and the HDMI audio (card 1) was muted again.  I unmuted it and rebooted.  This restored the HDMI audio for my appliations (vlc, etc.), but still no system sounds (not even analog anymore).  Is there a way to get the system sounds to also use HDMI?

---

### Post by hth0923 on 2010-07-30
> **jaakan said:**
> you don't need to update alsa to get it working with 10.04.


[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/550655](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/550655)

Here is how I got my gt220 before my motherboard/cpu went up.



```
    
 -- at command line

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa

 -- then 

install linux-alsa-driver-modules-2.6.xx-xx( matches your kernel )

 -- at command line

sudo vim /etc/modprobe.d/sound.conf

-- add the following for NV GT220 -- "aplay -l" will tell you which of the following to use

options snd-hda-intel enable_msi=0 probe_mask=0xfff2 # if your device is 0,3

or 

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2 # if your device is 1,3

or

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xffff,0xfff2 # if your device is 2,3


-- save and reboot

-- then do the following -- I used 1,3 because I used 2 audio outout devices at the time, you might need to use 0,3 or 2,3 etc...

aplay -D plughw:1,3 /usr/share/sounds/alsa/Noise.wav
speaker-test -Dhdmi:NVidia_1 -c6
```

Hi Mate, 

You make me SAY YEAH!!!! you are simply fantastic!!! :guitar::guitar:

Many thanks for your brief and meaningful post. it helps straight away. it works specularly.

Best Regard,
hth0923

---

### Post by Soorma on 2010-08-28
> **jay214128 said:**
> Thanks, jaakan.  I have had some mixed results.  After creating the sound.conf file, and rebooting, I could then get speaker-test to play sound via HDMI (yeah).  I also needed to unmute the HDMI audio device (card 1) in alsamixer.  I had to use F6 to select card 1 for it to even show up.

I still had only analog sound from the system and my applications.  I tried to run the System->Preferences->Default Sound Card to select the HDMI audio as my default sound card, but this application no longer runs.  It tries to start (shows up for about 10 seconds in the task bar) but then exits.  Is this expected?

A few reboots (days) later, I discovered that HDMI sound was working for some of my applications (vlc, mplayer, movieplayer), but still only analog for the system sounds.

Today I booted up and no sound at all.  I checked alsamixer and the HDMI audio (card 1) was muted again.  I unmuted it and rebooted.  This restored the HDMI audio for my appliations (vlc, etc.), but still no system sounds (not even analog anymore).  Is there a way to get the system sounds to also use HDMI?


I'm almost in the same boat with this, sound works on vlc , mplayer etc but no sound when i try to run boxee, xbmc or browse youtube ,google vidoes etc ...  can anyone help me with this please?

Thanks

---

