---
title: "Audio over HDMI for M4A78-EM"
date: 2009-06-17
forum: Hardware
---

### Post by DrWarm on 2009-06-17
Just trying to install the linux drivers that came in the CD with the motherboard because I can't get sound over the HDMI working, but I get this output:

> root@user-htpc:/home/user/Drivers/Audio/alsa-1.0.18rc3# ./install.sh
Checking old driver...
You have already install the driver.
Continue?
1) OK,exiting.
2) Still continue...
#? 2
OK,continuing...
I'll help you to install the alsa driver now.

First, check if you are using root account.
OK,go on.
Second, please make sure you have installed the kernel source.
You haven't installed the kernel source.


So now I tried to install the kernel source, I saw many places that you can just do:
```
sudo apt-get install linux-tree
```
but I get this output:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-tree

Then I tried: ```
uname -r
``` which gave: 
> 2.6.28-11-generic

So then I did:
```
sudo apt-get source linux-image-2.6.28-11-generic
```

But after this finished it still said it couldn't find the source. Is this even what I'm supposed to be doing!?!

Sorry I'm a bit lost, and can't seem to find any more info about this mobo, as it's fairly new.

---

### Post by MMoudry on 2009-06-18
What distribution are you using? There is no package called linux-tree. [http://packages.ubuntu.com/](http://packages.ubuntu.com/) I belive you need the linux headers package called linux-headers-xxxxxxxx where xxxxxx is the version of your kernel.

I am thinking about buying the same motherboard for my HTPC, the only problem is the level of support for XvBA for ATI chips in MythTV. How is it going so far under linux apart from the problem you are experiencing?

---

### Post by Lampi on 2009-06-18
@DrWarm: are you 100% sure alsa in jaunty is unable to use your onboard hdmi?

Please attach output of "aplay -l" - then you can try to play a file using the hdmi device. Chances are good alsa in jaunty s new enough.

---

### Post by DrWarm on 2009-06-18
Here's the output of "aplay -l":

> reuben@reuben-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Not sure what that means though haha!

The version of Alsa on the CD is (unsure what's included with Jaunty):
> alsa-1.0.18rc3

> 
What distribution are you using? There is no package called linux-tree. [http://packages.ubuntu.com/](http://packages.ubuntu.com/) I belive you need the linux headers package called linux-headers-xxxxxxxx where xxxxxx is the version of your kernel.

I tried this first, but it says I already have that package, so that's why I tried everything else!

> I am thinking about buying the same motherboard for my HTPC, the only problem is the level of support for XvBA for ATI chips in MythTV. How is it going so far under linux apart from the problem you are experiencing?

Not sure what test you want me to do, but when I installed mythbuntu 9.04 (64bit) I had to do it with open-source drivers initially. When it installed I could then use the closed source ones, and video playback everything seems fine. Although I don't have a blu-ray player to test playback of that or anything.

Hopefully that's more information you guys can use!!!

---

### Post by DrWarm on 2009-06-23
Someone told me to have a go installing OSS instead of using ALSA as he had a similar mobo, but I couldn't get this to work either. In the OSSXMIX GUI i can see the lights for the volume level moving up and down when playing a video in VLC, but no sound is coming through!

Here's my output of "ossmix":
> Selected mixer 0/High Definition Audio 0x10ec0887
Known controls are:
jack.green.mode <mix2|mix3|mix4|mix5|mix8|input> (currently mix2)
jack.green [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.green.mute ON|OFF (currently OFF)
jack.black.mode <mix2|mix3|mix4|mix5|mix8|input> (currently mix4)
jack.black [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.black.mute ON|OFF (currently OFF)
jack.orange.mode <mix2|mix3|mix4|mix5|mix8|input> (currently mix3)
jack.orange [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.orange.mute ON|OFF (currently OFF)
jack.gray.mode <mix2|mix3|mix4|mix5|mix8|input> (currently mix8)
jack.gray [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.gray.mute ON|OFF (currently OFF)
jack.pink.mode <mix2|mix3|mix4|mix5|mix8|input> (currently mix2)
jack.pink [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.pink.mute ON|OFF (currently OFF)
jack.fp-pink.mode <mix2|mix3|mix4|mix5|mix8|input> (currently mix2)
jack.fp-pink [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.fp-pink.mute ON|OFF (currently OFF)
jack.blue.mode <mix2|mix3|mix4|mix5|mix8|input> (currently input)
jack.blue [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.blue.mute ON|OFF (currently OFF)
jack.fp-green.mode <mix2|mix3|mix4|mix5|mix8|input> (currently mix2)
jack.fp-green [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.fp-green.mute ON|OFF (currently OFF)
record.mix7.mute.mic ON|OFF (currently OFF)
record.mix7.mute.fp-mic ON|OFF (currently OFF)
record.mix7.mute.linein ON|OFF (currently OFF)
record.mix7.mute.fp-headphone ON|OFF (currently OFF)
record.mix7.mute.green ON|OFF (currently OFF)
record.mix7.mute.black ON|OFF (currently OFF)
record.mix7.mute.orange ON|OFF (currently OFF)
record.mix7.mute.gray ON|OFF (currently OFF)
record.mix7.mute.mix1 ON|OFF (currently OFF)
record.mix7 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
record.mix6.mute.mic ON|OFF (currently OFF)
record.mix6.mute.fp-mic ON|OFF (currently OFF)
record.mix6.mute.linein ON|OFF (currently OFF)
record.mix6.mute.fp-headphone ON|OFF (currently OFF)
record.mix6.mute.green ON|OFF (currently OFF)
record.mix6.mute.black ON|OFF (currently OFF)
record.mix6.mute.orange ON|OFF (currently OFF)
record.mix6.mute.gray ON|OFF (currently OFF)
record.mix6.mute.mix1 ON|OFF (currently OFF)
record.mix6 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.fp-mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.fp-headphone [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.green [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.black [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.orange [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.gray [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mix1 <mic|fp-mic|linein> (currently mic)
misc.pcm1-mute ON|OFF (currently OFF)
misc.mix1-mute1 ON|OFF (currently OFF)
misc.mix21 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mix22 <pcm1|mix1> (currently pcm1)
misc.pcm2-mute ON|OFF (currently OFF)
misc.mix1-mute2 ON|OFF (currently OFF)
misc.mix31 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mix32 <pcm2|mix1> (currently pcm2)
misc.pcm3-mute ON|OFF (currently OFF)
misc.mix1-mute3 ON|OFF (currently OFF)
misc.mix41 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mix42 <pcm3|mix1> (currently pcm3)
misc.pcm4-mute ON|OFF (currently OFF)
misc.mix1-mute4 ON|OFF (currently OFF)
misc.mix51 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mix52 <pcm4|mix1> (currently pcm4)
misc.pcm5-mute ON|OFF (currently OFF)
misc.mix1-mute5 ON|OFF (currently OFF)
misc.mix81 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mix82 <pcm5|mix1> (currently pcm5)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 25.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm9 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm11 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm12 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)

And the output of "ossinfo -v3":
> Version info: OSS 4.1 (b 1052/200903240621) (0x00040100) 
Platform: Linux/x86_64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (reuben-htpc)

Number of audio devices:	9
Number of audio engines:	13
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=327643 (370661)
    HD Audio controller ATI HD Audio
    Vendor ID    0x10024383
    Subvendor ID 0x1043837b
     Codec  0: Unknown (0x10ec0887/0x1043837b)
 2: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio 0x10ec088 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCI837b1043-0000:00:14.2-mx01
    Device priority: 10


Audio devices
HD Audio play pcm1                /dev/oss/oss_hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 0/HD Audio play pcm1
                     Available for use 
      Engine      2: 9/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      3: 10/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      4: 11/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      5: 12/HD Audio play pcm1 (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm2                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/HD Audio play pcm2
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm3                /dev/oss/oss_hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/HD Audio play pcm3
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/HD Audio play pcm4
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm5                /dev/oss/oss_hdaudio0/pcm4  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 4/HD Audio play pcm5
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdifout1           /dev/oss/oss_hdaudio0/spdout0  (device index 5)
    Legacy device /dev/dsp5
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 5/HD Audio play spdifout1
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,88200,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdifout2           /dev/oss/oss_hdaudio0/spdout1  (device index 6)
    Legacy device /dev/dsp6
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 6/HD Audio play spdifout2
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_AC3		- AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au07
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,88200,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix7                 /dev/oss/oss_hdaudio0/pcmin0  (device index 7)
    Legacy device /dev/dsp7
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 7/HD Audio rec mix7
                     Available for use 
      Engine      2: 9/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      3: 10/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      4: 11/HD Audio play pcm1 (vmix)
                     Available for use 
      Engine      5: 12/HD Audio play pcm1 (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au08
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix6                 /dev/oss/oss_hdaudio0/pcmin1  (device index 8)
    Legacy device /dev/dsp8
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 8/HD Audio rec mix6
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE	- 16 bit signed little endian
      AFMT_S32_LE	- 32 bit signed little endian
    Device handle: PCI837b1043-0000:00:14.2-au09
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

Any ideas?

---

### Post by MMoudry on 2009-06-24
beats me, is the audio coming through on the other ports?

---

### Post by DrWarm on 2009-06-25
Yeh it's coming out fine through the others (headphone on front and green on the back). The only thing is when no sound is playing there's this high pitched noise which is a bit weird!

---

### Post by MMoudry on 2009-06-25
After through searching it looks like audio is not supported over HDMI under linux at this time.

See this thread that treats exactly your problem : [http://www.nvnews.net/vbulletin/showthread.php?t=97993](http://www.nvnews.net/vbulletin/showthread.php?t=97993)

**However** there is supposed to be a patch for ALSA to enable audio over HDMI. See here :
[http://www.phoronix.com/scan.php?page=article&item=773&num=4](http://www.phoronix.com/scan.php?page=article&item=773&num=4)

If you need help patching and recompiling ALSA I'd be glad to help.

Other than that you might have to find an alternate 'hardware' solution. ie. Audio + DVI -> HDMI

More Info:
[http://www.phoronix.com/scan.php?page=article&item=773&num=1](http://www.phoronix.com/scan.php?page=article&item=773&num=1)
[http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_hdmi&num=1)

---

### Post by DrWarm on 2009-06-25
You can definately get Audio over HDMI with some motherboards like [here]("http://ubuntuforums.org/showthread.php?t=1147977") (most of those links were from 2007), just unable to get it with mine. I'll try updating ALSA to the latest (even though I just removed it and replaced with OSS!).

I think it's mainly because it's not a feature of RadeonHD yet, which is a bit annoying that so many people are having trouble with it.

I'll have another go on the weekend.

---

### Post by Divider on 2009-06-25
Are you using the Radeon HDMI 2 DVI dongle or are you attempting to use the onboard hdmi for your motherboard.

I have a M4A78 Pro with onboard HDMI, it showed up after i installed my Catalyst for the radeon 4870.

---

### Post by DrWarm on 2009-06-25
No just using straight HDMI cable from HDMI output of motherboard to HDMI in of TV.

Can you explain what you mean by: > it showed up after i installed my Catalyst for the radeon 4870. 

How did you install the catalyst, just go enable propriety drivers? 

And where did it 'show up'?? In alsamixxer or whatever?

---

