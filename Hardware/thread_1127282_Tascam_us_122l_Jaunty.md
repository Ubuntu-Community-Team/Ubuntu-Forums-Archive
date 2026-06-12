---
title: "Tascam us 122l Jaunty"
date: 2009-04-16
forum: Hardware
---

### Post by Conq321 on 2009-04-16
I've been looking forward for the jaunty release because of the support for the tascam us 122l USB sound card. Today i decided to give it a go... 

"asoundconf list"
--> outputs my onboard card M5455 and the US122L

In my mixer, however, the tascam card does not show up. Tried to make it default via asound-gtk, where it was listed, but that does not change a thing. Several reboots.

Any help/ideas on this?

---

### Post by dleuschke on 2009-04-16
i've been trying to get my us-144 to work under the jaunty beta as well.  i had read that the 2.6.28 kernel had native support and understood that to mean i could just plug it in and it would work.  apparently not.

sorry i dont have any answers, but i second your post.

---

### Post by Earl_Maroon on 2009-04-25
I had believed that my US-122L would have worked straight away too.

I have no idea where to start in trying to make this work. The thing is, the ALSA wiki still doesn't show the US-122L as supported...

---

### Post by gorean on 2009-04-27
My problem is even though the system sees my Tascam us-122l and loads the module alsa does not so pulse does not (I think).
Jack lists it but won't use it. I get [Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server]
Seems to me it should work.
I have given some thought to an .asoundrc file but your supposed to use the result of aplay -l to get the names to use and that returns
no reference to that Tascam.
Stopping and restarting alsa and pulseaudio seem to make no difference as well as having it plugged in on start up or plugging it in later.
I must have missed something, any help would be appreciated.  I really need to do some recording.

Ubuntu 9.04
2.6.28-11-generic

I give you the output of
asoundconf list
lspci
lsusb
cat /proc/asound/cards
cat /proc/asound/modules
aplay -l
arecord -l
jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
sudo jackd -dalsa -dusb_stream:0 -r44100 -p64 -n2


:~$ asoundconf list
Names of available sound cards:
ICH5
US122L


james@jaunty:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)


james@jaunty:~$ lsusb
Bus 001 Device 003: ID 0644:800e TEAC Corp. 
Bus 001 Device 002: ID 04b8:0007 Seiko Epson Corp. Printer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


james@jaunty:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC655 at irq 17
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/003)

james@jaunty:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_usb_us122l


james@jaunty:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


james@jaunty:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


james@jaunty:~$ jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210902848, from thread -1210902848] (1: Operation not permitted)
cannot create engine


james@jaunty:~$ sudo jackd -dalsa -dusb_stream:0 -r44100 -p64 -n2
[sudo] password for james: 
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... usb_stream:0|usb_stream:0|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:0
control open "usb_stream:0" (No such file or directory)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM usb_stream:0
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM usb_stream:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa

---

### Post by veganbikepunk on 2009-04-30
i'm having very similar problems to gorean.  the only exception is 

```
odb@ubuntu:~$ jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... usb_stream:0|usb_stream:0|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL usb_stream:0
control open "usb_stream:0" (No such file or directory)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM usb_stream:0
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM usb_stream:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa

```
and
```
odb@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


other than that, our outputs are identical.

---

### Post by federicobriata on 2009-04-30
> **gorean said:**
> My problem is even though the system sees my Tascam us-122l and loads the module alsa does not so pulse does not (I think).
Jack lists it but won't use it. I get [Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server]
Seems to me it should work.
I have given some thought to an .asoundrc file but your supposed to use the result of aplay -l to get the names to use and that returns
no reference to that Tascam.
Stopping and restarting alsa and pulseaudio seem to make no difference as well as having it plugged in on start up or plugging it in later.
I must have missed something, any help would be appreciated.  I really need to do some recording.

Ubuntu 9.04
2.6.28-11-generic


james@jaunty:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC655 at irq 17
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/003)

james@jaunty:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_usb_us122l

james@jaunty:~$ jackd -RP50 -dalsa -dusb_stream:0 -r44100 -p64 -n2
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210902848, from thread -1210902848] (1: Operation not permitted)
cannot create engine



Hi, thanks to Pax to point me this new thread! 

James, I'll answer only to you because you give enough output to find a mistake...

have you read this?
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_3_-_set_alsa](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux#step_3_-_set_alsa)

I see that your tascam is recognized as number 1

so check what is inside ~/.asoundrc

than
jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2

do not use :0 if your tascam is recognized as number 1!!!!

be also sure that in /etc/modprobe.d/alsa-base

you got
options snd-usb-us122l index=-2

@Earl_Maroon

google is your friend.
there is a wiki, you can start from this
[http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)

if you need more, there is older thread on ubuntuforums.

Finally with Ubuntu 9.04 there is no need to patch and compile anything!!!!

---

### Post by passonno on 2009-05-06
Actually, with a Tascam US122, nothing has changed, and I must do it the hard way.  Was it decided to only support the relatively newer 122L?

---

### Post by u3000 on 2009-05-11
I had the same error messages as as Gorean, followed the instructions of federicobriata and the jack server is now working.

What i did, step by step:

$ cat /proc/asound/modules
 0 snd_intel8x0
_* 1 snd_usb_us122l*_

$ cat ~/.asoundrc **(missing file in my system)**
pcm.!usb_stream {
    @args [ CARD ]
    @args.CARD {
        type string
_*        default "1"*_
    }

    type usb_stream

    card $CARD
}

$ cat /etc/modprobe.d/_*alsa-base.conf*_ | grep us122**  (mind the .conf suffix!!!)**
options snd-usb-us122l index=-2

$ aplay -MDusb_stream:1 -fS24_3LE -r44100 -c2 -twav --period-size=640 ~/test.wav
worked well!

$ jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2
worked as well, and this never worked before!

I opend jack controll via the applications/multimedia menu and copied the settings of the last command given.

Thanks a lot federicobriata!

---

### Post by jhardydj on 2009-09-17
*bump* for some help please!

i have been struggling trying to get this going.. i will post all my alsa info below.  One thing i would like to note .. my dmesg just shows device found and set to address 3 etc in ubuntu , but in mandriva , Iget a full description of the device found (both default installs), would this be something in my kernel config? could someone who has a working us-122l send me their .config for me to have a gander?  anyhow, here is my config files, maybe someone can look them over.. 

Also, when booting system , if my tascam is plugged in , my mouse is frozen.  so i need to unplug and plug it back in when booted. 

thank you!


```
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Fri Sep 18 00:19:41 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu karmic (development branch) \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu karmic (development branch)"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.31-rc9-withless01
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_usb_us122l


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/004)


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------



!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10
snd-usb-us122l: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_usb_us122l
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116, 6 Sep 17 17:11 /dev/snd/controlC1
crw-rw----  1 root audio 116, 4 Sep 17 17:16 /dev/snd/hwC1D0
crw-rw----  1 root audio 116, 5 Sep 17 17:11 /dev/snd/midiC1D0
crw-rw----  1 root audio 116, 3 Sep 17 17:11 /dev/snd/seq
crw-rw----  1 root audio 116, 2 Sep 17 17:11 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Sep 17 17:11 .
drwxr-xr-x 4 root root 180 Sep 17 17:11 ..
lrwxrwxrwx 1 root root  12 Sep 17 17:11 usb-TASCAM_US-122L_no_serial_number-01 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Sep 17 17:11 .
drwxr-xr-x 4 root root 180 Sep 17 17:11 ..
lrwxrwxrwx 1 root root  12 Sep 17 17:11 pci-0000:00:1d.7-usb-0:4:1.1 -> ../controlC1


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

# The usb_stream plugin configuration

pcm.!usb_stream {
	@args [ CARD ]
	@args.CARD {
		type string
		default "1"
	}

	type usb_stream

	card $CARD
}


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:244: snd_ctl_pcm_next_device
**** List of PLAYBACK Hardware Devices ****

ARECORD

arecord: device_list:244: snd_ctl_pcm_next_device
**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [US122L]

Card hw:1 'US122L'/'TASCAM US-122L (644:800e if 0 at 001/004)'
  Mixer name	: ''
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0


!!Alsactl output
!!-------------

--startcollapse--
state.US122L {
	control {
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_usb_us122l
snd_usb_lib
snd_hwdep
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
usbhid
binfmt_misc
arc4
ecb
rt2500pci
rt2x00pci
rt2x00lib
led_class
input_polldev
mac80211
cfg80211
eeprom_93cx6
atl2
asus_atk0110
serio_raw
fbcon
tileblit
font
bitblit
softcursor
i915
drm
i2c_algo_bit
video
output
intel_agp
agpgart


!!ALSA/HDA dmesg
!!------------------





```

---

### Post by kurt. on 2010-02-20
my first post in this forum. hi everyone.
sorry for that i m not helping much in this post but asking for help as well.

i am using ubuntu karmic 9.10 and try to get the tascam us-144 to work.

i downloaded the us-122l firmware, upgraded alsa with the script i found [here]("http://ubuntuforums.org/showthread.php?p=6589810") and did

```
kurt@kurt-laptop:~$ sudo modprobe snd-usb-audio
kurt@kurt-laptop:~$ echo -n 0000:00:1d.7 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind
```after that and a plug-out-plug-in-again, the us-144 was recognized as us-122l, which was my intention:

```
kurt@kurt-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7ff8000 irq 31
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800f if 0 at 008/008)
kurt@kurt-laptop:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l
```i created the .asoundrc file like u3000 did and the alsa-base.conf is the same as well, but jackd seems to ignore that:

```
kurt@kurt-laptop:~$ sudo jackd -RP50 -dalsa -dusb_stream:1 -r44100 -p64 -n2no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... usb_stream:1|usb_stream:1|64|2|44100|0|0|nomon|swmeter|-|32bit
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL usb_stream:1
control open "usb_stream:1" (No such file or directory)
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
Couldn't configure usb_stream
: Invalid argument
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
```the test with aplay is not working either, but thats maybe a different problem:

```
kurt@kurt-laptop:~$ aplay -MDusb_stream:1 -fS24_3LE -r44100 -c2 -twav --period-size=640 ~/testing.wav
Warning: format is changed to S16_LE
Playing WAVE '/home/kurt/testing.wav' : Signed 16 bit Little Endian, Rate 11025 Hz, Mono
aplay: set_params:990: Sample format non available
Available formats:
- S24_3LE

```i see the tascam in qjackctl ---> connections only under alsa as 

        20:TASCAM US-122L
  --->       0:TASCAM US-122L MIDI 1

but i can't connect it.

qjackctl 'messages' output:
```

 p, li { white-space: pre-wrap; }  15:29:46.230 /usr/bin/jackd -R -dalsa -dhw:1 -r44100 -p1024 -n2
 15:29:46.233 JACK was started with PID=2622.
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 SSE2 detected
 apparent rate = 44100
 creating alsa driver ... hw:1|hw:1|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:1
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 cannot load driver module alsa
 15:29:46.279 JACK was stopped successfully.
 15:29:46.279 Post-shutdown script...
 15:29:46.279 killall jackd
 15:29:46.432 ALSA connection change.
 jackd: no process found
 15:29:46.688 Post-shutdown script terminated with exit status=256.
 15:29:48.438 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```auszug aus dmesg:
```
[  249.795296] ehci_hcd 0000:00:1d.7: remove, state 1
[  249.795310] usb usb2: USB disconnect, address 1
[  249.795313] usb 2-5: USB disconnect, address 2
[  249.877131] ehci_hcd 0000:00:1d.7: USB bus 2 deregistered
[  249.877217] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[  250.160090] usb 8-1: new full speed USB device using uhci_hcd and address 6
[  250.311865] usb 8-1: not running at top speed; connect to a high speed hub
[  250.436934] usb 8-1: configuration #1 chosen from 1 choice
[  250.445887] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[  250.469945] input: CNF7129 as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input10
[  250.592542] usb 8-2: new full speed USB device using uhci_hcd and address 7
[  265.710082] usb 8-2: device descriptor read/64, error -110
[  273.560148] hub 8-0:1.0: unable to enumerate USB device on port 2
[  277.070116] usb 8-2: new full speed USB device using uhci_hcd and address 8
[  277.216426] usb 8-2: not running at top speed; connect to a high speed hub
[  277.243535] usb 8-2: configuration #1 chosen from 1 choice
[  278.730661] usbcore: registered new interface driver snd-usb-us122l
[ 2216.940044] CE: hpet increasing min_delta_ns to 15000 nsec
[ 3876.029937] usbcore: registered new interface driver snd-usb-audio

```help is very much appreciated.

thanks

---

