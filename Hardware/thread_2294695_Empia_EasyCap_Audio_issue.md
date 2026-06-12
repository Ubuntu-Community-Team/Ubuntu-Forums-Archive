---
title: "Empia EasyCap Audio issue"
date: 2015-09-12
forum: Hardware
---

### Post by uniquegodwin on 2015-09-12
[COLOR=#111111][FONT=Ubuntu]Can someone help me with fixing the audio issue with Empia EasyCap?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have seen the thread here([http://ubuntuforums.org/showthread.php?t=1642985](http://ubuntuforums.org/showthread.php?t=1642985)) but their solution does not seem to work for me.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This wiki [here]("http://linuxtv.org/wiki/index.php/Easycap") also claims that audio works for this device. But it does not work for me.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The audio and video drivers are successfully installed. I can see the audio device as USB 2861 Analog device on the mixer. I see the volume bars enabled.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But, there is no sound passing in through it. It's just pure silence through the USB 2861 Analog input device even though I've plugged in amplified sound into the white and red cables.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I would appreciate any help.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-09-12
Open Pulseaudio Volume Control (presuming you are using Ubuntu) or install it if you don't have it. Get some music playing (an audio stream). Click the playback tab. See anything? Check the output tab. See anything? Don't forget to scroll down. If you see something, try changing the device in PAVControl to the correct one. 

You are saying you have an audio signal coming into your computer via USB from the Ezycap. Are you also getting a picture? Has it scanned any stations? Do you know you are actually getting a signal through from the Ezycap? The mixer is software or hardware?

Please give more detail of your setup. See third link in my signature. :)

PS: The info on the link you gave is incredibly old in software terms. It wouldn't work.

PPS: Could you also turn off machine, unplug USB dongle, boot machine, once at a desktop put USB in, and before doing anything else, open a terminal and:

```
dmesg
```

Post the last part of the result that concerns the Ezycap.

---

### Post by uniquegodwin on 2015-09-13
HI Bucky,

Thanks for your reply.
Yes I am getting video signal through easycap and I am able to view it through "mplayer tv:// -tv device=/dev/video0:input=1"
There's no problem with the video. Video works fine through mplayer. In the above command,I'm not playing the audio.But,even if I include the audio parameters, I can't hear audio. Let me explain more about what's happening with the audio .....

Here are the things I've tried related to the audio :

```

-desktop:~$ ls /dev/aud*
/dev/audio  /dev/audio1


-desktop:~$ ls /dev/*dsp*
/dev/adsp  /dev/dsp  /dev/dsp1

-desktop:~$ aplay /dev/audio1
Playing raw data '/dev/audio1' : Unsigned 8 bit, Rate 8000 Hz, Mono
underrun!!! (at least 440.851 ms long)


-desktop:~$ aplay /dev/dsp1
Playing raw data '/dev/dsp1' : Unsigned 8 bit, Rate 8000 Hz, Mono
underrun!!! (at least 421.054 ms long)
underrun!!! (at least 449.809 ms long)


-desktop:~$ arecord test.wav
Recording WAVE 'test.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono



```


WHen I play the wave recorded through arecord, it is blank ie no sound, just silence.

To clear, all your doubts, here's screenshots of all those screens :


[[IMG]http://s11.postimg.org/h53ivdfhr/2861_input.png[/IMG]]("http://postimg.org/image/h53ivdfhr/") [[IMG]http://s11.postimg.org/pbvimy5kf/mix_configuration.png[/IMG]]("http://postimg.org/image/pbvimy5kf/") [[IMG]http://s11.postimg.org/tv7r8gnfz/output_audio_from_youtube.png[/IMG]]("http://postimg.org/image/tv7r8gnfz/")

[[IMG]http://s11.postimg.org/c8zw3ofcf/playback.png[/IMG]]("http://postimg.org/image/c8zw3ofcf/") [[IMG]http://s11.postimg.org/sy1bzlbxr/recording.png[/IMG]]("http://postimg.org/image/sy1bzlbxr/") [[IMG]http://s11.postimg.org/r7iay3uen/Sound_prefs.png[/IMG]]("http://postimg.org/image/r7iay3uen/")





Output of arecord -l

```

-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: U0xeb1a0x2861 [USB Device 0xeb1a:0x2861], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```



 As you can see below, there seems to be an Empia audio device  installed but when I plug in real audio, what comes inside the PC is  silence.

Here's the DMESG output : 

```

-desktop:~$ sudo dmesg
[  415.402210] usb 1-1.2: new high-speed USB device number 5 using dwc_otg
[  415.490399] usb 1-1.2: New USB device found, idVendor=eb1a, idProduct=2861
[  415.490418] usb 1-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  415.565595] media: Linux media interface: v0.10
[  415.581891] Linux video capture interface: v2.00
[  415.599773] em28xx: New device   @ 480 Mbps (eb1a:2861, interface 0, class 0)
[  415.599795] em28xx: Video interface 0 found: isoc
[  415.600059] em28xx: chip ID is em2860
[  415.694212] em2860 #0: board has no eeprom
[  415.754126] em2860 #0: No sensor detected
[  415.764347] em2860 #0: found i2c device @ 0x4a on bus 0 [saa7113h]
[  415.788084] em2860 #0: Your board has no unique USB ID.
[  415.788097] em2860 #0: A hint were successfully done, based on i2c devicelist hash.
[  415.788104] em2860 #0: This method is not 100% failproof.
[  415.788111] em2860 #0: If the board were missdetected, please email this log to:
[  415.788117] em2860 #0:     V4L Mailing List  <linux-media@vger.kernel.org>
[  415.788124] em2860 #0: Board detected as EM2860/SAA711X Reference Design
[  415.866033] em2860 #0: Identified as EM2860/SAA711X Reference Design (card=19)
[  415.866046] em2860 #0: analog set to isoc mode.
[  415.866276] em28xx audio device (eb1a:2861): interface 1, class 1
[  415.866334] em28xx audio device (eb1a:2861): interface 2, class 1
[  415.866472] usbcore: registered new interface driver em28xx
[  415.904788] em2860 #0: Registering V4L2 extension
[  415.910656] usbcore: registered new interface driver snd-usb-audio
[  416.302512] saa7115 2-0025: saa7113 found @ 0x4a (em2860 #0)
[  417.070298] em2860 #0: Config register raw data: 0x10
[  417.094144] em2860 #0: AC97 vendor ID = 0x414c4760
[  417.106155] em2860 #0: AC97 features = 0x0000
[  417.106167] em2860 #0: Unknown AC97 audio processor detected!
[  419.498562] em2860 #0: V4L2 video device registered as video0
[  419.498579] em2860 #0: V4L2 VBI device registered as vbi0
[  419.498589] em2860 #0: V4L2 extension successfully initialized
[  419.498597] em28xx: Registered (Em28xx v4l2 Extension) extension
[  419.523464] em2860 #0: Registering snapshot button...
[  419.523834] input: em28xx snapshot button as /devices/platform/bcm2708_usb/usb1/1-1/1-1.2/input/input3
[  419.524116] em2860 #0: Remote control support is not available for this card.
[  419.524127] em28xx: Registered (Em28xx Input Extension) extension



```


Hope this helps you see what I see. Please help me..

Thanks

---

### Post by Yellow Pasque on 2015-09-13
Check that it's not muted:
```
v4l2-ctl --all     #make sure mute=0, install v4l-utils paackage if this command is not found
alsamixer   #use F6 to change card if needed
```

If that doesn't work, maybe alsa info will shed some light (or not): [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by uniquegodwin on 2015-09-13
HI,
Thanks for the reply.

Here's the output of  v4l2-ctl --all


```

-desktop:~$ v4l2-ctl --all
Driver Info (not using libv4l2):
    Driver name   : em28xx
    Card type     : EM2860/SAA711X Reference Design
    Bus info      : usb-bcm2708_usb-1.2
    Driver version: 3.18.11
    Capabilities  : 0x85220011
        Video Capture
        VBI Capture
        Audio
        Read/Write
        Streaming
        Extended Pix Format
        Device Capabilities
    Device Caps   : 0x05220001
        Video Capture
        Audio
        Read/Write
        Streaming
        Extended Pix Format
Priority: 2
Video input : 0 (S-Video: ok)
Audio input : 0 (Television)
Video Standard = 0x000000ff
    PAL-B/B1/G/H/I/D/D1/K
Format Video Capture:
    Width/Height  : 720/576
    Pixel Format  : 'YUYV'
    Field         : Interlaced
    Bytes per Line: 1440
    Size Image    : 829440
    Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
    Flags         : 
Streaming Parameters Video Capture:
    Frames per second: 25.000 (25/1)
    Read buffers     : 4

User Controls

                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=-128 max=127 step=1 default=0 value=0 flags=slider
                         volume (int)    : min=0 max=31 step=1 default=31 value=31 flags=slider
                           mute (bool)   : default=1 value=1
                    red_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                   blue_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                      sharpness (int)    : min=0 max=15 step=1 default=0 value=0 flags=slider
                     chroma_agc (bool)   : default=1 value=1 flags=update
                    chroma_gain (int)    : min=0 max=127 step=1 default=40 value=15 flags=inactive, slider, volatile
                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=-128 max=127 step=1 default=0 value=0 flags=slider
                         volume (int)    : min=0 max=31 step=1 default=31 value=31 flags=slider
                           mute (bool)   : default=1 value=1
                    red_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                   blue_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                      sharpness (int)    : min=0 max=15 step=1 default=0 value=0 flags=slider
                     chroma_agc (bool)   : default=1 value=1 flags=update
                    chroma_gain (int)    : min=0 max=127 step=1 default=40 value=15 flags=inactive, slider, volatile



```

In alsamixer, Pressing F6 and selecting USB 2861 says that this sound device has no playback controls.

Please advise..

THanks.

---

### Post by Yellow Pasque on 2015-09-13
> mute (bool)   : default=1 value=1

```
v4l2-ctl -c mute=0    #use sudo if it complains about access/permissions
```

---

### Post by uniquegodwin on 2015-09-14
Even after executing v4l2-ctl -c mute=0  , I still get just silence through the audio device when I record something using arecord. No sound is coming in through the USB sound device
The audio cables are still plugged in to the device. Please have no doubt that I have thoroughly checked the cable connections.

[[IMG]http://s4.postimg.org/4uihry3d5/Screenshot_Volume_Control.jpg[/IMG]]("http://postimg.org/image/4uihry3d5/")[[IMG]http://s23.postimg.org/wlndq8lvb/Screenshot_Volume_Control_1.jpg[/IMG]]("http://postimg.org/image/wlndq8lvb/")

Please help.

Thanks.


Output of v4l2-ctl --all again if this might help :

```

-desktop:~$ v4l2-ctl --all
Driver Info (not using libv4l2):
    Driver name   : em28xx
    Card type     : EM2860/SAA711X Reference Design
    Bus info      : usb-bcm2708_usb-1.4
    Driver version: 3.18.17
    Capabilities  : 0x85220011
        Video Capture
        VBI Capture
        Audio
        Read/Write
        Streaming
        Extended Pix Format
        Device Capabilities
    Device Caps   : 0x05220001
        Video Capture
        Audio
        Read/Write
        Streaming
        Extended Pix Format
Priority: 2
Video input : 0 (S-Video: ok)
Audio input : 0 (Television)
Video Standard = 0x000000ff
    PAL-B/B1/G/H/I/D/D1/K
Format Video Capture:
    Width/Height  : 720/576
    Pixel Format  : 'YUYV'
    Field         : Interlaced
    Bytes per Line: 1440
    Size Image    : 829440
    Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
    Flags         : 
Streaming Parameters Video Capture:
    Frames per second: 25.000 (25/1)
    Read buffers     : 4

User Controls

                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=-128 max=127 step=1 default=0 value=0 flags=slider
                         volume (int)    : min=0 max=31 step=1 default=31 value=31 flags=slider
                           mute (bool)   : default=1 value=0
                    red_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                   blue_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                      sharpness (int)    : min=0 max=15 step=1 default=0 value=0 flags=slider
                     chroma_agc (bool)   : default=1 value=1 flags=update
                    chroma_gain (int)    : min=0 max=127 step=1 default=40 value=15 flags=inactive, slider, volatile
                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=-128 max=127 step=1 default=0 value=0 flags=slider
                         volume (int)    : min=0 max=31 step=1 default=31 value=31 flags=slider
                           mute (bool)   : default=1 value=0
                    red_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                   blue_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                      sharpness (int)    : min=0 max=15 step=1 default=0 value=0 flags=slider
                     chroma_agc (bool)   : default=1 value=1 flags=update
                    chroma_gain (int)    : min=0 max=127 step=1 default=40 value=15 flags=inactive, slider, volatile



```

---

### Post by Yellow Pasque on 2015-09-14
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by uniquegodwin on 2015-09-15
HI Temujin,

Here's the output of that command :

```

!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Tue Sep 15 12:47:20 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 15.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.04" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      
Product Name:      
Product Version:   
Firmware Version:  


!!Kernel Information
!!------------------

Kernel release:    3.18.0-25-rpi2
Operating System:  GNU/Linux
Architecture:      armv7l
Processor:         armv7l
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.18.0-25-rpi2
Library version:    1.0.28
Utilities version:  1.0.28


!!Loaded ALSA modules
!!-------------------

snd_bcm2835
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [ALSA           ]: bcm2835 - bcm2835 ALSA
                      bcm2835 ALSA
 1 [U0xeb1a0x2861  ]: USB-Audio - USB Device 0xeb1a:0x2861
                      USB Device 0xeb1a:0x2861 at usb-bcm2708_usb-1.4, high speed


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------



!!Modprobe options (Sound related)
!!--------------------------------

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

!!Module: snd_bcm2835
    force_bulk : N

!!Module: snd_usb_audio
    autoclock : Y
    device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
    ignore_ctl_error : N
    index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!USB Mixer information
!!---------------------
--startcollapse--

USB Mixer: usb_id=0xeb1a2861, ctrlif=1, ctlerr=0
Card: USB Device 0xeb1a:0x2861 at usb-bcm2708_usb-1.4, high speed
  Unit: 2
    Control: name="Line Capture Volume", index=0
    Info: id=2, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=-4096, max=4096, dBmin=-1600, dBmax=1600
  Unit: 2
    Control: name="Line Capture Switch", index=0
    Info: id=2, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  2 Jan  1  1970 /dev/snd/controlC0
crw-rw----  1 root audio 116,  5 Sep 15 18:11 /dev/snd/controlC1
crw-rw----  1 root audio 116,  3 Sep 15 18:15 /dev/snd/pcmC0D0p
crw-rw----  1 root audio 116,  4 Jan  1  1970 /dev/snd/pcmC0D1p
crw-rw----  1 root audio 116,  6 Sep 15 18:11 /dev/snd/pcmC1D0c
crw-rw----  1 root audio 116,  1 Jan  1  1970 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jan  1  1970 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Sep 15 18:11 .
drwxr-xr-x 4 root root 220 Sep 15 18:11 ..
lrwxrwxrwx 1 root root  12 Sep 15 18:11 usb-eb1a_2861-01 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 15 18:11 .
drwxr-xr-x 4 root root 220 Sep 15 18:11 ..
lrwxrwxrwx 1 root root  12 Sep 15 18:11 platform-bcm2708_usb-usb-0:1.4:1.1 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: ALSA [bcm2835 ALSA], device 0: bcm2835 ALSA [bcm2835 ALSA]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: U0xeb1a0x2861 [USB Device 0xeb1a:0x2861], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [ALSA]

Card hw:0 'ALSA'/'bcm2835 ALSA'
  Mixer name    : 'Broadcom Mixer'
  Components    : ''
  Controls      : 6
  Simple ctrls  : 1
Simple mixer control 'PCM',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback -10239 - 400
  Mono: Playback -1986 [78%] [-19.86dB] [on]

!!-------Mixer controls for card 1 [U0xeb1a0x2861]

Card hw:1 'U0xeb1a0x2861'/'USB Device 0xeb1a:0x2861 at usb-bcm2708_usb-1.4, high speed'
  Mixer name    : 'USB Mixer'
  Components    : 'USBeb1a:2861'
  Controls      : 3
  Simple ctrls  : 1
Simple mixer control 'Line',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 16
  Mono: Capture 16 [100%] [16.00dB] [on]


!!Alsactl output
!!--------------

--startcollapse--
state.ALSA {
    control.1 {
        iface MIXER
        name 'PCM Playback Volume'
        value -1986
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '-10239 - 400'
            dbmin -9999999
            dbmax 400
            dbvalue.0 -1986
        }
    }
    control.2 {
        iface MIXER
        name 'PCM Playback Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'PCM Playback Route'
        value 0
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 2'
        }
    }
    control.4 {
        iface PCM
        name 'IEC958 Playback Default'
        value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write'
            type IEC958
            count 1
        }
    }
    control.5 {
        iface PCM
        name 'IEC958 Playback Con Mask'
        value '0200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access read
            type IEC958
            count 1
        }
    }
    control.6 {
        iface PCM
        name 'IEC958 Playback PCM Stream'
        value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
        comment {
            access 'read write inactive'
            type IEC958
            count 1
        }
    }
}
state.U0xeb1a0x2861 {
    control.1 {
        iface PCM
        name 'Capture Channel Map'
        value.0 0
        value.1 0
        comment {
            access read
            type INTEGER
            count 2
            range '0 - 36'
        }
    }
    control.2 {
        iface MIXER
        name 'Line Capture Switch'
        value true
        comment {
            access 'read write'
            type BOOLEAN
            count 1
        }
    }
    control.3 {
        iface MIXER
        name 'Line Capture Volume'
        value 16
        comment {
            access 'read write'
            type INTEGER
            count 1
            range '0 - 16'
            dbmin -1600
            dbmax 1600
            dbvalue.0 1600
        }
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
em28xx_rc
rc_core
saa7115
em28xx_v4l
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
snd_usb_audio
snd_hwdep
snd_usbmidi_lib
em28xx
tveeprom
v4l2_common
videodev
media
cfg80211
rfkill
binfmt_misc
cpufreq_stats
joydev
evdev
hid_generic
dm_multipath
scsi_dh
snd_soc_bcm2708_i2s
regmap_mmio
snd_soc_core
snd_compress
snd_pcm_dmaengine
spi_bcm2708
i2c_bcm2708
bcm2708_rng
snd_bcm2835
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
snd
fuse


!!ALSA/HDA dmesg
!!--------------

[  896.025398] em2860 #0: Registering V4L2 extension
[  896.032538] usbcore: registered new interface driver snd-usb-audio
[  896.427509] saa7115 2-0025: saa7113 found @ 0x4a (em2860 #0)




```

Alternatively, it's also uploaded here : [http://www.alsa-project.org/db/?f=b81896d545eb9579c1adb74764222353630086b6](http://www.alsa-project.org/db/?f=b81896d545eb9579c1adb74764222353630086b6)

Please advise what could be wrong. Really need help...

THanks

---

### Post by Yellow Pasque on 2015-09-15
It looks good to me in terms of volumes being set sufficiently and not muted. Sorry, but I'm personally out of ideas on this one. The only thing I came across in googling is that the message "Unknown AC97 audio processor detected!" may cause issues. I didn't see any way to change that though.

---

### Post by Dominique_De_Munck on 2016-05-20
Hello

I lost some time with the audio too, but got it working.

I guess the main issue is that the mute on the capture device is set to "on" by default, regardless of the alsamixer settings, as can be seen by the command:

>> v4l2-ctl -l -d /dev/video1

User Controls


                     brightness (int)    : min=0 max=255 step=1 default=128 value=128 flags=slider
                       contrast (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                     saturation (int)    : min=0 max=127 step=1 default=64 value=64 flags=slider
                            hue (int)    : min=-128 max=127 step=1 default=0 value=0 flags=slider
                         volume (int)    : min=0 max=31 step=1 default=31 value=31 flags=slider
                           mute (bool)   : default=1 value=1
                    red_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                   blue_balance (int)    : min=-48 max=48 step=1 default=0 value=0 flags=slider
                      sharpness (int)    : min=0 max=15 step=1 default=0 value=0 flags=slider
                     chroma_agc (bool)   : default=1 value=1 flags=update
                    chroma_gain (int)    : min=0 max=127 step=1 default=40 value=106 flags=inactive, slider, volatile

Set it to Off with the command:

>> v4l2-ctl -c mute=0 -d /dev/video1

Then I can record video & audio with the following command (using ffmpeg 3.0.2)
/usr/local/bin/ffmpeg -f v4l2 -s 720x576  -i /dev/video1 -f alsa -ac 2 -i hw:1 out.mpg

You can view with mplayer using a command like:
mplayer tv:// -tv driver=v4l2:width=720:height=576:device=/dev/video1:input=0:fps=25:norm=PAL:alsa:adevice=hw.2:audiorate=48000:forceaudio:amode=1:immediatemode=0Also, you might load the alsa module first as is indicated on this site:
[https://www.linuxtv.org/wiki/index.php/TerraTec_Grabby](https://www.linuxtv.org/wiki/index.php/TerraTec_Grabby)

And maybe this module insert (for my card Grabby) had something to do with it:

modprobe em28xx card=68

([http://tomoyo.osdn.jp/cgi-bin/lxr/source/Documentation/video4linux/CARDLIST.em28xx](http://tomoyo.osdn.jp/cgi-bin/lxr/source/Documentation/video4linux/CARDLIST.em28xx) )

---

