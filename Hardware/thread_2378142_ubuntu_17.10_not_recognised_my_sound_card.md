---
title: "ubuntu 17.10 not recognised my sound card"
date: 2017-11-20
forum: Hardware
---

### Post by volkanadana on 2017-11-20
```
vgs@vgs-N360:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful
vgs@vgs-N360:~$ lspci | grep Audio
vgs@vgs-N360:~$ lspci | grep Audio
vgs@vgs-N360:~$ sudo lspci | grep Audio
[sudo] password for vgs: 
vgs@vgs-N360:~$ grep "Codec:" /proc/asound/card*/codec*
grep: /proc/asound/card*/codec*: Böyle bir dosya ya da dizin yok
vgs@vgs-N360:~$ lsmod | grep snd
snd_soc_sst_bytcr_rt5640    24576  0
snd_soc_rt5670        131072  0
snd_soc_rt5645        147456  0
snd_soc_rt5640        118784  1 snd_soc_sst_bytcr_rt5640
snd_soc_tlv320aic31xx    49152  0
snd_intel_sst_acpi     16384  1
snd_intel_sst_core     77824  1 snd_intel_sst_acpi
snd_soc_sst_atom_hifi2_platform   102400  1 snd_intel_sst_core
snd_soc_sst_match      16384  2 snd_soc_sst_bytcr_rt5640,snd_intel_sst_acpi
snd_soc_rl6231         16384  3 snd_soc_rt5670,snd_soc_rt5640,snd_soc_rt5645
snd_soc_core          229376  6 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_soc_rt5640,snd_soc_tlv320aic31xx,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645
snd_hdmi_lpe_audio     24576  3
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm                98304  10 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_hdmi_lpe_audio,snd_pcm_dmaengine,snd_soc_rt5640,snd_soc_tlv320aic31xx,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  14 snd_compress,snd_seq,snd_hdmi_lpe_audio,snd_timer,snd_soc_sst_atom_hifi2_platform,snd_rawmidi,snd_seq_device,snd_soc_core,snd_pcm
soundcore              16384  1 snd
```

Hi,
I installed ubuntu 17.10, but it didn't recognised my sound card. no sound from the speakers and 
the sound output device appears to be an analog device.

```
aplay -l
**** PLAYBACK Donan&#305;m Ayg&#305;tlar&#305;n&#305;n Listesi ****
kart 0: Audio [Intel HDMI/DP LPE Audio], ayg&#305;t 0: HdmiLpeAudio [Intel HDMI/DP LPE Audio]
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0
kart 0: Audio [Intel HDMI/DP LPE Audio], ayg&#305;t 1: HdmiLpeAudio [Intel HDMI/DP LPE Audio]
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0
kart 1: bytcrrt5640 [bytcr-rt5640], ayg&#305;t 0: Baytrail Audio (*) []
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0
kart 1: bytcrrt5640 [bytcr-rt5640], ayg&#305;t 1: Deep-Buffer Audio (*) []
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0


```
sorry to my english. .
I did a lot of research but I could not find a solution

---

### Post by Yellow Pasque on 2017-11-21
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by attobot on 2017-11-22
Does this output any sound? 
**aplay -D sysdefault /usr/share/sounds/alsa/Side_Right.wav -vv **

Is there any error when you start pulseaudio?
** start-pulseaudio-x11**

---

### Post by gordintoronto on 2017-11-22
There's no need to use grep with lspci.

---

### Post by Yellow Pasque on 2017-11-23
> **gordintoronto said:**
> There's no need to use grep with lspci.

I think the OP was trying to filter out non sound devices, but it didn't work because s/he's using a different language.

---

### Post by volkanadana on 2017-11-24
> **attobot said:**
> Does this output any sound? 
**aplay -D sysdefault /usr/share/sounds/alsa/Side_Right.wav -vv **

Is there any error when you start pulseaudio?
** start-pulseaudio-x11**

there wasn't any sound. It said:
```

vgs@vgs-N360:~$  aplay -D sysdefault /usr/share/sounds/alsa/Side_Right.wav -vv 
ALSA lib pcm.c:2495:(snd_pcm_open_noupdate) Unknown PCM sysdefault
aplay: main:788: audio open error: No such file or directory
vgs@vgs-N360:~$ 
vgs@vgs-N360:~$ start-pulseaudio-x11
Connection failure: Connection terminated
vgs@vgs-N360:~$ start-pulseaudio-x11
vgs@vgs-N360:~$ start-pulseaudio-x11
vgs@vgs-N360:~$ 




```

---

### Post by volkanadana on 2017-11-24
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

I did it and 
terminal command output is below:
```

vgs@vgs-N360:~$  cd ~/
vgs@vgs-N360:~$   wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2017-11-25 01:28:04--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;f=alsa-info/alsa-info.sh [following]
--2017-11-25 01:28:04--  http://git.alsa-project.org/?p=alsa-utils.git;a=blob_plain;f=alsa-info/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: ‘alsa-info.sh’

alsa-info.sh            [ <=>                ]  28,03K  --.-KB/s    in 0,08s   

2017-11-25 01:28:05 (364 KB/s) - ‘alsa-info.sh’ saved [28707]

ALSA Information Script v 0.4.64
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=260e0507941c8037c15969abc88b302ab96fe951

Please inform the person helping you.



```

---

### Post by Yellow Pasque on 2017-11-24
The information in your first post shows:
```
kart 1: bytcrrt5640 [bytcr-rt5640], ayg&#305;t 0: Baytrail Audio (*) []
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0
kart 1: bytcrrt5640 [bytcr-rt5640], ayg&#305;t 1: Deep-Buffer Audio (*) []
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0
```

But this card did not show up in the alsa information you just gave us ( [http://www.alsa-project.org/db/?f=260e0507941c8037c15969abc88b302ab96fe951](http://www.alsa-project.org/db/?f=260e0507941c8037c15969abc88b302ab96fe951) )

I am not sure at what point you added these lines:
```
snd_hda_intel: model=byt-rt5640
snd_hda_intel: model=chtrt5645

```

```
!!ALSA Version
!!------------

Driver version:     k4.13.0-16-generic
Library version:    1.0.14
Utilities version:  1.1.3
```

You also have an extremely old version of ALSA library (libasound2 package). I am not sure when or how you did this.

---

### Post by volkanadana on 2017-11-27
I reinstalled ubuntu 17.10 and I did commands in the terminal again. New outputs are below. No sound is  on my all in one laptop still.
```

vg@vg-N360:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful
vg@vg-N360:~$ lspci | grep Audio
vg@vg-N360:~$ sudo lspci | grep Audio
[sudo] password for vg: 
vg@vg-N360:~$ grep "Codec:" /proc/asound/card*/codec*
grep: /proc/asound/card*/codec*: No such file or directory
vg@vg-N360:~$  lsmod | grep snd
snd_soc_sst_bytcr_rt5640    24576  0
snd_soc_rt5670        131072  0
snd_soc_rt5645        147456  0
snd_intel_sst_acpi     16384  1
snd_intel_sst_core     77824  1 snd_intel_sst_acpi
snd_soc_rt5640        118784  1 snd_soc_sst_bytcr_rt5640
snd_soc_sst_atom_hifi2_platform   102400  1 snd_intel_sst_core
snd_soc_tlv320aic31xx    49152  0
snd_soc_sst_match      16384  2 snd_soc_sst_bytcr_rt5640,snd_intel_sst_acpi
snd_soc_rl6231         16384  3 snd_soc_rt5670,snd_soc_rt5640,snd_soc_rt5645
snd_hdmi_lpe_audio     24576  2
snd_soc_core          229376  6 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_soc_rt5640,snd_soc_tlv320aic31xx,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm                98304  9 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_hdmi_lpe_audio,snd_pcm_dmaengine,snd_soc_rt5640,snd_soc_tlv320aic31xx,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645,snd_soc_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  13 snd_compress,snd_seq,snd_hdmi_lpe_audio,snd_timer,snd_soc_sst_atom_hifi2_platform,snd_rawmidi,snd_seq_device,snd_soc_core,snd_pcm
soundcore              16384  1 snd
vg@vg-N360:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audio [Intel HDMI/DP LPE Audio], device 0: HdmiLpeAudio [Intel HDMI/DP LPE Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audio [Intel HDMI/DP LPE Audio], device 1: HdmiLpeAudio [Intel HDMI/DP LPE Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
vg@vg-N360:~$  aplay -D sysdefault /usr/share/sounds/alsa/Side_Right.wav -vv 
Playing WAVE '/usr/share/sounds/alsa/Side_Right.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
Plug PCM: Route conversion PCM (sformat=S16_LE)
  Transformation table:
    0 <- 0
    1 <- 0
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
  tstamp_type  : MONOTONIC
  period_step  : 1
  avail_min    : 6000
  period_event : 0
  start_threshold  : 24000
  stop_threshold   : 24000
  silence_threshold: 0
  silence_size : 0
  boundary     : 6755399441055744000
Slave: Hardware PCM card 0 'Intel HDMI/DP LPE Audio' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 24000
  period_size  : 6000
  period_time  : 125000
  tstamp_mode  : NONE
  tstamp_type  : MONOTONIC
  period_step  : 1
  avail_min    : 6000
  period_event : 0
  start_threshold  : 24000
  stop_threshold   : 24000
  silence_threshold: 0
  silence_size : 0
  boundary     : 6755399441055744000
  appl_ptr     : 0
  hw_ptr       : 0
########                 +                         | 48%underrun!!! (at least 0,007 ms long)
Status:
  state       : XRUN
  trigger_time: 3567.270319252
  tstamp      : 0.000000
  delay       : 0
  avail       : 0
  avail_max   : 0
#######################  +                         | 48%underrun!!! (at least 0,004 ms long)
Status:
  state       : XRUN
  trigger_time: 3567.274863442
  tstamp      : 0.000000
  delay       : 0
  avail       : 0
  avail_max   : 0
#                        +                         | 48%
vg@vg-N360:~$ start-pulseaudio-x11
Failure: Module initialisation failed
vg@vg-N360:~$ sudo start-pulseaudio-x11
No protocol specified
xcb_connection_has_error() returned true
Home directory not accessible: Permission denied
Connection failure: Connection refused
pa_context_connect() failed: Connection refused



```

My several outputs are in this link:
[https://paste.ubuntu.com/26059507/](https://paste.ubuntu.com/26059507/)

Sorry to my english:P

---

### Post by Yellow Pasque on 2017-11-27
The sound codec is still not showing up. Relevant dmesg errors:
```
[   10.692941] bytcr_rt5640 bytcr_rt5640: ASoC: CODEC DAI rt5640-aif1 not registered
[   10.692952] bytcr_rt5640 bytcr_rt5640: devm_snd_soc_register_card failed -517
```

I am puzzled why it showed up in your original post, but not on fresh install.
I don't know what to suggest, other than trying the latest kernel 4.15.x

---

### Post by volkanadana on 2017-11-27
How can I try the latest kernel 4.15.x???

---

### Post by volkanadana on 2017-12-01
unfortunately, I updated my kernel 4.15 but ubuntu didn't recognise my sound card.. :KS

my alsa information-script is below:
> 
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Fri Dec  8 21:24:33 UTC 2017


!!Linux Distribution
!!------------------

Ubuntu 17.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 17.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 17.10" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=artful


!!DMI Information
!!---------------

Manufacturer:      CASPER BILGISAYAR
Product Name:      N360
Product Version:   CASPER BILGISAYAR
Firmware Version:  5.6.5
Board Vendor:      CASPER BILGISAYAR
Board Name:        N360


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/10EC5640:00/status 	 15
/sys/bus/acpi/devices/80860F0A:00/status 	 15
/sys/bus/acpi/devices/80860F0A:01/status 	 15
/sys/bus/acpi/devices/80860F14:00/status 	 15
/sys/bus/acpi/devices/80860F14:02/status 	 15
/sys/bus/acpi/devices/80860F28:00/status 	 15
/sys/bus/acpi/devices/80860F41:00/status 	 15
/sys/bus/acpi/devices/80860F41:01/status 	 15
/sys/bus/acpi/devices/80860F41:02/status 	 15
/sys/bus/acpi/devices/80860F41:03/status 	 15
/sys/bus/acpi/devices/80860F41:04/status 	 15
/sys/bus/acpi/devices/FTSC1000:00/status 	 15
/sys/bus/acpi/devices/INT0002:00/status 	 15
/sys/bus/acpi/devices/INT3396:00/status 	 15
/sys/bus/acpi/devices/INT33BB:00/status 	 15
/sys/bus/acpi/devices/INT33F4:00/status 	 15
/sys/bus/acpi/devices/INT33FC:00/status 	 15
/sys/bus/acpi/devices/INT33FC:01/status 	 15
/sys/bus/acpi/devices/INT33FC:02/status 	 15
/sys/bus/acpi/devices/INT33FE:00/status 	 15
/sys/bus/acpi/devices/INT3400:00/status 	 15
/sys/bus/acpi/devices/INT3401:00/status 	 15
/sys/bus/acpi/devices/INT3403:02/status 	 15
/sys/bus/acpi/devices/INT3403:03/status 	 15
/sys/bus/acpi/devices/INT3403:04/status 	 15
/sys/bus/acpi/devices/INT3403:06/status 	 15
/sys/bus/acpi/devices/INT3403:07/status 	 15
/sys/bus/acpi/devices/INT3403:08/status 	 15
/sys/bus/acpi/devices/INT3406:00/status 	 15
/sys/bus/acpi/devices/INT3407:00/status 	 15
/sys/bus/acpi/devices/INT3407:01/status 	 15
/sys/bus/acpi/devices/INT3407:02/status 	 15
/sys/bus/acpi/devices/INTCFD9:00/status 	 15
/sys/bus/acpi/devices/INTL9C60:00/status 	 15
/sys/bus/acpi/devices/INTL9C60:01/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:01/status 	 1
/sys/bus/acpi/devices/LNXPOWER:02/status 	 1
/sys/bus/acpi/devices/LNXPOWER:03/status 	 2
/sys/bus/acpi/devices/LNXPOWER:04/status 	 2
/sys/bus/acpi/devices/MSFT0101:00/status 	 15
/sys/bus/acpi/devices/OBDA8723:00/status 	 15
/sys/bus/acpi/devices/OVTI2680:00/status 	 15
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0501:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:01/status 	 31
/sys/bus/acpi/devices/PNP0C0D:00/status 	 15
/sys/bus/acpi/devices/PNP0C0F:00/status 	 9
/sys/bus/acpi/devices/PNP0C0F:01/status 	 9
/sys/bus/acpi/devices/PNP0C0F:02/status 	 9
/sys/bus/acpi/devices/PNP0C0F:03/status 	 9
/sys/bus/acpi/devices/PNP0C0F:04/status 	 9
/sys/bus/acpi/devices/PNP0C0F:05/status 	 9
/sys/bus/acpi/devices/PNP0C0F:06/status 	 9
/sys/bus/acpi/devices/PNP0C0F:07/status 	 9
/sys/bus/acpi/devices/SMO8500:00/status 	 15
/sys/bus/acpi/devices/device:0a/status 	 15
/sys/bus/acpi/devices/device:0f/status 	 15
/sys/bus/acpi/devices/device:32/status 	 15
/sys/bus/acpi/devices/device:33/status 	 15


!!Kernel Information
!!------------------

Kernel release:    4.15.0-999-lowlatency
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.15.0-999-lowlatency
Library version:    1.1.3
Utilities version:  1.1.3


!!Loaded ALSA modules
!!-------------------

snd_hdmi_lpe_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Audio          ]: HdmiLpeAudio - Intel HDMI/DP LPE Audio
                      Intel HDMI/DP LPE Audio


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------



!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hdmi_lpe_audio
	id : (null)
	index : -1


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  2 Dec  8 23:42 /dev/snd/controlC0
crw-rw----  1 root audio 116,  3 Dec  9 00:12 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  4 Dec  8 23:42 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  1 Dec  8 23:42 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Dec  8 23:42 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec  8 23:42 .
drwxr-xr-x 3 root root 160 Dec  8 23:42 ..
lrwxrwxrwx 1 root root  12 Dec  8 23:42 pci-0000:00:02.0-platform-hdmi-lpe-audio -> ../controlC0


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Audio [Intel HDMI/DP LPE Audio], device 0: HdmiLpeAudio [Intel HDMI/DP LPE Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audio [Intel HDMI/DP LPE Audio], device 1: HdmiLpeAudio [Intel HDMI/DP LPE Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Audio]

Card hw:0 'Audio'/'Intel HDMI/DP LPE Audio'
  Mixer name	: ''
  Components	: ''
  Controls      : 10
  Simple ctrls  : 0


!!Alsactl output
!!--------------

--startcollapse--
state.Audio {
	control.1 {
		iface PCM
		name 'IEC958 Playback Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface PCM
		name 'IEC958 Playback Default'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.3 {
		iface PCM
		name ELD
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read volatile'
			type BYTES
			count 128
		}
	}
	control.4 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access read
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.5 {
		iface CARD
		name 'HDMI/DP,pcm=0 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 1
		name 'IEC958 Playback Mask'
		value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.7 {
		iface PCM
		device 1
		name 'IEC958 Playback Default'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.8 {
		iface PCM
		device 1
		name ELD
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read volatile'
			type BYTES
			count 128
		}
	}
	control.9 {
		iface PCM
		device 1
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access read
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.10 {
		iface CARD
		name 'HDMI/DP,pcm=1 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
btrfs
zstd_compress
xor
raid6_pq
ufs
qnx4
hfsplus
hfs
minix
ntfs
msdos
jfs
xfs
libcrc32c
cmdlinepart
intel_spi_platform
intel_spi
spi_nor
joydev
mtd
axp288_fuel_gauge
axp288_charger
extcon_axp288
axp288_adc
axp20x_pek
gpio_keys
intel_rapl
intel_soc_dts_thermal
intel_powerclamp
coretemp
nls_iso8859_1
kvm_intel
kvm
irqbypass
snd_hdmi_lpe_audio
punit_atom_debug
snd_pcm
crct10dif_pclmul
crc32_pclmul
snd_seq_midi
snd_seq_midi_event
ghash_clmulni_intel
snd_rawmidi
pcbc
aesni_intel
snd_seq
aes_x86_64
crypto_simd
glue_helper
cryptd
intel_cstate
snd_seq_device
snd_timer
input_leds
r8723bs
hid_multitouch
snd
mei_txe
mei
soundcore
lpc_ich
cfg80211
mac_hid
dw_dmac
kxcjk_1013
dw_dmac_core
tpm_crb
soc_button_array
industrialio_triggered_buffer
processor_thermal_device
dptf_power
int3406_thermal
kfifo_buf
int3400_thermal
intel_soc_dts_iosf
int3403_thermal
int340x_thermal_zone
axp20x_i2c
acpi_thermal_rel
pwm_lpss_platform
axp20x
pwm_lpss
intel_int0002_vgpio
industrialio
8250_dw
intel_cht_int33fe
acpi_pad
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
hid_generic
usbhid
i915
mmc_block
i2c_algo_bit
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
drm
video
i2c_hid
hid
sdhci_acpi
sdhci


!!ALSA/HDA dmesg
!!--------------

[    6.649709] i2c_hid i2c-FTSC1000:00: failed to change power setting.
[    6.804374] input: Intel HDMI/DP LPE Audio HDMI/DP,pcm=0 as /devices/pci0000:00/0000:00:02.0/hdmi-lpe-audio/sound/card0/input7
[    6.804578] input: Intel HDMI/DP LPE Audio HDMI/DP,pcm=1 as /devices/pci0000:00/0000:00:02.0/hdmi-lpe-audio/sound/card0/input8
[    7.058780] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().





---

### Post by claydoh on 2017-12-19
What device do you have? These 2-in-1s often run Intel Atom/Baytrail or other systems with the entire thing all on one chip - including sound. The have notoriously poor to non-existent sound support, but some specific devices do have working audio with tweaks and workarounds.

---

