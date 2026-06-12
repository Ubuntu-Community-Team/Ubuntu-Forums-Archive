---
title: "No sound on Compaq Presario 2700 with Ubuntu 10.10"
date: 2010-10-16
forum: Hardware
---

### Post by kshawkeye on 2010-10-16
Hey, I have been trying to solve this issue for a while now, following others guides, trying other suggestions, yet nothing has fixed my problem yet.

I have a Compaq Presario 2700 with a fresh install of Ubuntu 10.10. The sound works on my headphones, when plugged into the headphone jack. When the headphones are unplugged and the sound is meant to come from the speakers, none does. I have all volumes on alsamixer turned up, and Ubuntu 10.10 says that it is recognizing my sound card.

Any help would be great, thanks.

---

### Post by kshawkeye on 2010-12-02
Sill have this issue on latest Ubuntu, any ideas?

---

### Post by mastablasta on 2010-12-02
assuming speakers work normally under another OS, i would say that somehow your speakers output is actualy recognised as one and only speakers line out. the other line out (for built in speakers is just not recognised).
 
you would need to check the configuration files for that.
 
long shot but is the sound card propperly configured in ALSA?

---

### Post by lidex on 2010-12-02
> **kshawkeye said:**
> Sill have this issue on latest Ubuntu, any ideas?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by kshawkeye on 2010-12-03
Followed those steps but I cant find the link that would lead you to the info it uploaded. Here it what it says.

I tried sudo as well but still no link.

> wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2010-12-03 02:09:54--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org]("http://www.alsa-project.org")... 212.20.107.51
Connecting to [www.alsa-project.org|212.20.107.51|:80]("http://www.alsa-project.org%7C212.20.107.51%7C:80")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2010-12-03 02:09:54--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to [www.alsa-project.org:80]("http://www.alsa-project.org:80").
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,026      85.3K/s   in 0.3s    

2010-12-03 02:09:55 (85.3 KB/s) - `alsa-info.sh' saved [27026]

ALSA Information Script v 0.4.59
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

Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : y
Uploading information to [www.alsa-project.org]("http://www.alsa-project.org") ...  Done!

Your ALSA information is located at 
Please inform the person helping you.

[QUOTE="mastablasta"]long shot but is the sound card propperly configured in ALSA?[/QUOTE]No idea, how would I check that?

---

### Post by mastablasta on 2010-12-03
You can do it like this:
 
```
[FONT=Courier New]sudo alsaconf[/FONT]
```
 
also on a side not i think your post is  missing the link to the site where result from the script were put.
 
> Your ALSA information is located at 


---

### Post by kshawkeye on 2010-12-03
sudo alsaconf turns up with:

> sudo alsaconf
[sudo] password for kyle: 
sudo: alsaconf: command not found

[QUOTE="mastablasta"]also on a side not i think your post is  missing the link to the site where result from the script were put.[/QUOTE]

That's what I said here:

[QUOTE="kshawkeye"]Followed those steps but I cant find the link that would lead you to the info it uploaded. Here it what it says.

I tried sudo as well but still no link.[/QUOTE]

Thats a direct copy from the terminal, I didn't remove the link, it didn't supply me with one.

---

### Post by kshawkeye on 2010-12-04
Am I doing something wrong? Any new ideas?

---

### Post by lidex on 2010-12-04
Try that script again and if it doesn't work now use the other option to save locally. It will end up in your /tmp directory.
Just copy-and-paste into a post in between code tags.

---

### Post by kshawkeye on 2010-12-06
Still couldn't get it to upload. Here it is:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Dec  6 06:03:30 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Compaq
Product Name:      Presario 2720US 470028-365    


!!Kernel Information
!!------------------

Kernel release:    2.6.35-23-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with AD1886 at irq 5


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:2485 (rev 01)
    Subsystem: 0e11:007b


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
    ac97_clock : 0
    ac97_quirk : (null)
    buggy_irq : N
    buggy_semaphore : N
    enable : N
    id : (null)
    index : -1
    joystick : 0
    spdif_aclink : 0
    xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1886

PCI Subsys Vendor: 0x0e11
PCI Subsys Device: 0x007b

Flags: 0
Capabilities     : -headphone out-
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : Analog Devices Phat Stereo

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=0 DSA=0 SPDIF VRA
Extended status  : SPDIF=6/9 SPDIF VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=44.1kHz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0410
0:02 = 0303
0:04 = 0404
0:06 = 801f
0:08 = 0000
0:0a = 8000
0:0c = 8008
0:0e = 8008
0:10 = 8808
0:12 = 0808
0:14 = 8808
0:16 = 8808
0:18 = 0808
0:1a = 0000
0:1c = 8707
0:1e = 0000
0:20 = 0000
0:22 = 000b
0:24 = 0000
0:26 = 800f
0:28 = 0005
0:2a = 0025
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 0824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0010
0:74 = 1000
0:76 = 0404
0:78 = ac44
0:7a = ac44
0:7c = 4144
0:7e = 5361
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Dec  6 00:55 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Dec  6 00:55 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Dec  6 00:55 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Dec  6 00:55 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116, 3 Dec  6 00:55 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Dec  6 00:55 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec  6 00:55 .
drwxr-xr-x 3 root root 180 Dec  6 00:55 ..
lrwxrwxrwx 1 root root  12 Dec  6 00:55 pci-0000:00:1f.5 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 1: Intel ICH - MIC ADC [Intel 82801CA-ICH3 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [I82801CAICH3]

Card hw:0 'I82801CAICH3'/'Intel 82801CA-ICH3 with AD1886 at irq 5'
  Mixer name    : 'Analog Devices AD1886'
  Components    : 'AC97a:41445361'
  Controls      : 38
  Simple ctrls  : 24
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 60 [95%] [-4.50dB] [on]
  Front Right: Playback 60 [95%] [-4.50dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 59 [94%] [0.00dB] [on]
  Front Right: Playback 59 [94%] [0.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 11 [73%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 11 [73%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [off] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [off] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [off] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 7 [47%] [10.50dB] [off]
  Front Right: Capture 7 [47%] [10.50dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.I82801CAICH3 {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 63'
        comment.dbmin -9450
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 60
        value.1 60
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Headphone Playback Switch'
        value true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 63'
        comment.dbmin -8850
        comment.dbmax 600
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 59
        value.1 59
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Mono Playback Switch'
        value false
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Mono Playback Volume'
        value 0
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Beep Playback Switch'
        value false
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        comment.dbmin -4500
        comment.dbmax 0
        iface MIXER
        name 'Beep Playback Volume'
        value 15
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value false
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 23
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value false
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value 23
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value false
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 23
        value.1 23
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Playback Switch'
        value true
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Playback Volume'
        value.0 23
        value.1 23
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Playback Switch'
        value false
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Video Playback Volume'
        value.0 23
        value.1 23
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Playback Switch'
        value false
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 23
        value.1 23
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
    }
    control.24 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 2
        comment.item.0 Mic
        comment.item.1 CD
        comment.item.2 Video
        comment.item.3 Aux
        comment.item.4 Line
        comment.item.5 Mix
        comment.item.6 'Mix Mono'
        comment.item.7 Phone
        iface MIXER
        name 'Capture Source'
        value.0 Mic
        value.1 Mic
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Capture Switch'
        value false
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 7
        value.1 7
    }
    control.27 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'pre 3D'
        comment.item.1 'post 3D'
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value false
    }
    control.29 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.30 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.31 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Center'
        value 11
    }
    control.32 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Depth'
        value 11
    }
    control.33 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.34 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.35 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0082000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.36 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.37 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        iface MIXER
        name 'IEC958 Playback AC97-SPSA'
        value 3
    }
    control.38 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value false
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
radeon
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm
snd_seq_midi
ttm
snd_rawmidi
joydev
drm_kms_helper
snd_seq_midi_event
pcmcia
snd_seq
snd_timer
snd_seq_device
drm
yenta_socket
ppdev
intel_agp
pcmcia_rsrc
snd
psmouse
pcmcia_core
i2c_algo_bit
soundcore
video
serio_raw
parport_pc
snd_page_alloc
shpchp
agpgart
output
lp
parport
firewire_ohci
e100
floppy
firewire_core
crc_itu_t
mii


!!ALSA/HDA dmesg
!!------------------



```

---

### Post by lidex on 2010-12-06
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-intel8x0 index=0 ac97_quirk=3 enable=1
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by kshawkeye on 2010-12-06
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
options snd-intel8x0 index=0 ac97_quirk=3 enable=1
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Thanks for the help but still only have sound through the headphone jack. All alsamixer levels are turned up and the sound options are set correctly.

---

### Post by kshawkeye on 2010-12-09
Is there anything else? I would really like to get this fixed.

---

### Post by kshawkeye on 2010-12-13
Any ideas?

---

### Post by retroman2128 on 2010-12-22
I have a Presario 2715US laptop with exactly the same thing going on. I've tried everything I can find. I'd like to see if there is a solution out there. The only thing I've run across is at this website: [http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

I've tried to install this but it doesn't want to finish building and leaves me with an error every time. I'm not much of a developer nor a linux expert so I am stuck where I'm at. Maybe someone will be able to take this idea and run with it?

Below is what I get when trying to install their source package. I am attaching the log file it says to check. Maybe someone out there can make heads or tails of it!

Thanks!!
Noah


> $ sudo dpkg -i alsa-driver-linuxant_1.0.23.1_all.deb 
Selecting previously deselected package alsa-driver-linuxant.
(Reading database ... 120573 files and directories currently installed.)
Unpacking alsa-driver-linuxant (from alsa-driver-linuxant_1.0.23.1_all.deb) ...
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-24-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.5888.log
dpkg: error processing alsa-driver-linuxant (--install):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 alsa-driver-linuxant


---

### Post by kshawkeye on 2011-01-02
Glad I'm not alone, I will try and compile it and see if I can do any better, in the mean time I am open to any other ideas.

---

### Post by lidex on 2011-01-02
For compiling, make sure you have these installed:
```
sudo apt-get install build-essential linux-headers-`uname -r` checkinstall
```

---

### Post by kshawkeye on 2011-01-03
I installed the compiled version and it didn't fix it.

---

### Post by lidex on 2011-01-03
Can you run alsa-info again to see where we are?

---

### Post by kshawkeye on 2011-01-05
> upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Wed Jan  5 07:02:58 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Compaq
Product Name:      Presario 2720US 470028-365    


!!Kernel Information
!!------------------

Kernel release:    2.6.35-24-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_intel8x0


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [I82801CAICH3   ]: ICH - Intel 82801CA-ICH3
                      Intel 82801CA-ICH3 with AD1886 at irq 5


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1f.5 0401: 8086:2485 (rev 01)
    Subsystem: 0e11:007b


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-intel8x0: index=0 ac97_quirk=3 enable=1
snd-hda-intel: model=hp-m4
snd-hda-intel: enable_msi=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_intel8x0
    ac97_clock : 0
    ac97_quirk : 3
    buggy_irq : N
    buggy_semaphore : N
    enable : Y
    id : (null)
    index : 0
    joystick : 0
    spdif_aclink : 0
    xbox : N


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Analog Devices AD1886

PCI Subsys Vendor: 0x0e11
PCI Subsys Device: 0x007b

Flags: 0
Capabilities     : -headphone out-
DAC resolution   : 16-bit
ADC resolution   : 16-bit
3D enhancement   : Analog Devices Phat Stereo

Current setup
Mic gain         : +20dB [+20dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : on
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=0 DSA=0 SPDIF VRA
Extended status  : SPDIF=6/9 SPDIF VRA
PCM front DAC    : 44100Hz
PCM ADC          : 44100Hz
SPDIF Control    : Consumer PCM Category=0x2 Generation=1 Rate=44.1kHz



AD18XX configuration
Unchained        : 0x1000,0x0000,0x0000
Chained          : 0x0000,0x0000,0x0000

0:00 = 0410
0:02 = 0000
0:04 = 0404
0:06 = 801f
0:08 = 0000
0:0a = 0000
0:0c = 0008
0:0e = 0048
0:10 = 0808
0:12 = 0808
0:14 = 0808
0:16 = 0808
0:18 = 0808
0:1a = 0000
0:1c = 8707
0:1e = 0000
0:20 = 2000
0:22 = 000b
0:24 = 0000
0:26 = 800f
0:28 = 0005
0:2a = 0025
0:2c = ac44
0:2e = 0000
0:30 = 0000
0:32 = ac44
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 0824
0:3c = 0000
0:3e = 0000
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0000
0:4e = 0000
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0000
0:6e = 0000
0:70 = 0000
0:72 = 0010
0:74 = 1000
0:76 = 0404
0:78 = ac44
0:7a = ac44
0:7c = 4144
0:7e = 5361
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 7 Jan  5 01:55 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 6 Jan  5 01:55 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 5 Jan  5 01:55 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 4 Jan  5 01:55 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116, 3 Jan  5 01:55 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jan  5 01:55 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jan  5 01:55 .
drwxr-xr-x 3 root root 180 Jan  5 01:55 ..
lrwxrwxrwx 1 root root  12 Jan  5 01:55 pci-0000:00:1f.5 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 1: Intel ICH - MIC ADC [Intel 82801CA-ICH3 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [I82801CAICH3]

Card hw:0 'I82801CAICH3'/'Intel 82801CA-ICH3 with AD1886 at irq 5'
  Mixer name    : 'Analog Devices AD1886'
  Components    : 'AC97a:41445361'
  Controls      : 38
  Simple ctrls  : 24
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [on]
  Front Right: Playback 63 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 59 [94%] [0.00dB] [on]
  Front Right: Playback 59 [94%] [0.00dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 11 [73%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 11 [73%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [on]
  Front Right: Playback 23 [74%] [0.00dB] [on]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [on]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 23 [74%] [0.00dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 3 [100%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 15 [100%] [0.00dB] [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 7 [47%] [10.50dB] [off]
  Front Right: Capture 7 [47%] [10.50dB] [off]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.I82801CAICH3 {
    control.1 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Playback Switch'
        value true
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 63'
        comment.dbmin -9450
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value.0 63
        value.1 63
    }
    control.3 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Headphone Playback Switch'
        value true
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 63'
        comment.dbmin -8850
        comment.dbmax 600
        iface MIXER
        name 'Headphone Playback Volume'
        value.0 59
        value.1 59
    }
    control.5 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Mono Playback Switch'
        value false
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Mono Playback Volume'
        value 0
    }
    control.7 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Beep Playback Switch'
        value true
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        comment.dbmin -4500
        comment.dbmax 0
        iface MIXER
        name 'Beep Playback Volume'
        value 15
    }
    control.9 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Playback Switch'
        value true
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Playback Volume'
        value 23
    }
    control.11 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Playback Switch'
        value true
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Playback Volume'
        value 23
    }
    control.13 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value true
    }
    control.14 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Playback Switch'
        value true
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Playback Volume'
        value.0 23
        value.1 23
    }
    control.16 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Playback Switch'
        value true
    }
    control.17 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Playback Volume'
        value.0 23
        value.1 23
    }
    control.18 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Playback Switch'
        value true
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Video Playback Volume'
        value.0 23
        value.1 23
    }
    control.20 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Playback Switch'
        value true
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Playback Volume'
        value.0 23
        value.1 23
    }
    control.22 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PCM Playback Switch'
        value true
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'PCM Playback Volume'
        value.0 23
        value.1 23
    }
    control.24 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 2
        comment.item.0 Mic
        comment.item.1 CD
        comment.item.2 Video
        comment.item.3 Aux
        comment.item.4 Line
        comment.item.5 Mix
        comment.item.6 'Mix Mono'
        comment.item.7 Phone
        iface MIXER
        name 'Capture Source'
        value.0 Mic
        value.1 Mic
    }
    control.25 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Capture Switch'
        value false
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 15'
        comment.dbmin 0
        comment.dbmax 2250
        iface MIXER
        name 'Capture Volume'
        value.0 7
        value.1 7
    }
    control.27 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'pre 3D'
        comment.item.1 'post 3D'
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
    }
    control.28 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name '3D Control - Switch'
        value true
    }
    control.29 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.30 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.31 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Center'
        value 11
    }
    control.32 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        iface MIXER
        name '3D Control - Depth'
        value 11
    }
    control.33 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Con Mask'
        value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.34 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Pro Mask'
        value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.35 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Default'
        value '0082000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.36 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'IEC958 Playback Switch'
        value true
    }
    control.37 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 3'
        iface MIXER
        name 'IEC958 Playback AC97-SPSA'
        value 3
    }
    control.38 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value false
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
arc4
radeon
snd_intel8x0
rt73usb
snd_ac97_codec
ac97_bus
rt2500usb
rt2x00usb
snd_pcm
rt2x00lib
ttm
snd_seq_midi
led_class
mac80211
snd_rawmidi
drm_kms_helper
snd_seq_midi_event
joydev
snd_seq
pcmcia
snd_timer
snd_seq_device
drm
ppdev
cfg80211
yenta_socket
intel_agp
parport_pc
pcmcia_rsrc
video
snd
psmouse
pcmcia_core
output
i2c_algo_bit
serio_raw
soundcore
snd_page_alloc
shpchp
agpgart
lp
parport
firewire_ohci
e100
floppy
firewire_core
mii
crc_itu_t


!!ALSA/HDA dmesg
!!------------------




It still gave me to URL for the upload.

---

### Post by kshawkeye on 2011-01-05
Now I have a bigger problem because I removed those drivers that I previously installed to try and fix the problem. Now I have no devices under the hardware tab of sound preferences, it's just a red box. Ive tried:

```

sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get check
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update

```

And still no drivers, yet the alsa drivers are still installed (at least I think they are, I only removed the ones that I installed in one of the previous posts).

Any ideas how to fix this, AND the main problem?

---

### Post by lidex on 2011-01-05
Remove all the entries you added to alsa-base.conf
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Re-install alsa:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
Reset pulse:
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
Now post these outputs:
```
aplay -l
```
```
dmesg | grep -C1 -E 'ALSA|HDA|AC97|sound|hda.codec|snd-intel8x0'
```

---

### Post by kshawkeye on 2011-01-05
The reinstall said:

> 
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.35-24-generic"


Resetting pulse said:

> 
rm: cannot remove `/home/kyle/.asound*': No such file or directory


and:

> 
rm: cannot remove `/etc/asound.conf': No such file or directory


After the reboot I did have the hardware listed, but the original problem still is there.

The output of aplay -l is:

> **** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And the output of dmesg | grep -C1 -E 'ALSA|HDA|AC97|sound|hda.codec|snd-intel8x0' is nothing at all?

---

### Post by lidex on 2011-01-05
OK. Now add this back to alsa-base.conf - only this:
```
options snd-intel8x0 index=0 ac97_quirk=3 enable=1
```
Reboot. Try using 0,1 or 2 for the quirk if that doesn't work.

BTW those linuxant drivers are for conexant codec chips which you do not have.

---

### Post by kshawkeye on 2011-01-05
Added the line, 0-3 quirk changed nothing, I did reboot every time I changed the value as well.

---

### Post by lidex on 2011-01-05
Ok. Try it this way instead:
```
options snd-intel8x0 ac97_quirk=3
```

---

### Post by kshawkeye on 2011-01-06
Nope, still didn't work, and I saw a message that read something like "could not apply quirk 3 (-2)" or something along those lines, I only saw it for a moment because it flashed up on boot, and I don't know how to check the error log or something similar where I could find it.

---

### Post by torstenian on 2011-03-09
I have this exact same issue. Please let me know if you managed to fix it.:p

---

### Post by torstenian on 2011-03-10
I finally gave up on ALSA on the old Presario and installed OSS instead. Worked right off the bat.
I used this guide for help: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
):P

---

### Post by fredko on 2011-11-06
Unfortunately I have exactly the same problem on my Compaq Presario 2701EA. Please tell me if somebody has ready a fix for it.

---

### Post by erkaan on 2012-08-05
> **torstenian said:**
> I finally gave up on ALSA on the old Presario and installed OSS instead. Worked right off the bat.
I used this guide for help: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
):P

This is the right solution. :popcorn: OSS works perfectly while ALSA fails on my own old Presario 2700 boosted by the powerful Linux Mint 13 XFCE. Nice stuff for trashware fans :guitar:

---

### Post by UnixMan2 on 2012-08-16
I guess it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/846615](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/846615)

> **erkaan said:**
> This is the right solution. :popcorn: OSS works perfectly while ALSA fails on my own old Presario 2700 boosted by the powerful Linux Mint 13 XFCE. Nice stuff for trashware fans :guitar:
Tried on my 2701EA, with (L)Ubuntu 10.04 LTS. Indeed OSS4 successfully enables the speakers, but it screw-up the sound: output is very distorted and with "wrong pitch". :(

Any idea about how to fix that? (maybe a newver version of OSS4?)


For the moment, back to ALSA with the suspend/hibernate workaround.

edit: solved problem with OSS4. Now it works fine! :)

Problem is, the system widely depends on ALSA and various apps does not work / have problems with OSS4. :-(

---

