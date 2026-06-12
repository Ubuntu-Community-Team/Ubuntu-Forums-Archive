---
title: "Audio problem after upgrading"
date: 2011-05-04
forum: Hardware
---

### Post by Ryuky on 2011-05-04
Hey! I'm new in this forum.
Yesterday I upgraded Ubuntu from 10.04 to 10.10 and audio didn't worked. Then I upgraded it to 11.04 (don't tell me why...I don't know!).
Audio stil don't work: i tried to run mp3 files, videos from my hdd and videos from youtube but I can't hear anything.

The speaker icon on the top right of the screen hasn't got no volume and by clicking on it appears "Label Empty" and bar when I usually set the volume is disabled.

I tried to click "Audio preferences" but it runs a window that say "Waiting for an sound system reponse" and after a few minutes it doesn't change.

I tried to switch off and on the speakers and then to put out and in the 1/8" jack in the rear computer panel but nothing changes.

I also tried to restart my computer twice, unsuccesfully.

Can someone help me, please?

I'm not english so, excuse me for my mistakes :)

---

### Post by mörgæs on 2011-05-04
Hi, welcome to the fora.

Here is some advice:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by lidex on 2011-05-04
Try purging your old pulse config files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by Ryuky on 2011-05-05
@mörgæs: i tried the live cd but i don't know how to listen to something! I can't see youtube videos because flash 10 is missing and i can't listen to mop3 files because there is no music player.

How con i try to test the audio?

@lidex: thank you! i removed ~/.pulse and ~/.pulse-cookie but when I tried to remove ~/.asound*  and /etc/asound.conf a message appeard: the file or directory doesn't exist

Is it the same or it's a problem?

---

### Post by Ryuky on 2011-05-06
someone can help me, please?

---

### Post by lidex on 2011-05-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Ryuky on 2011-05-07
this is what I found:
```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Sat May  7 14:41:41 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      MICRO-STAR INTERNATIONAL CO., LTD
Product Name:      MS-7253
Product Version:   1.0


!!Kernel Information
!!------------------

Kernel release:    2.6.38-9-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xdfefc000 irq 25


!!PCI Soundcards installed in the system
!!--------------------------------------

02:00.1 Audio device: ATI Technologies Inc RV710/730
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

02:00.1 0403: 1002:aa38
	Subsystem: 174b:aa38
--
80:01.0 0403: 1106:3288 (rev 10)
	Subsystem: 1462:7253


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

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  4 May  7 16:39 /dev/snd/controlC0
crw-rw----  1 root audio 116,  3 May  7 16:39 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  2 May  7 16:39 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116,  1 May  7 16:39 /dev/snd/seq
crw-rw----  1 root audio 116, 33 May  7 16:39 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 May  7 16:39 .
drwxr-xr-x 3 root root 160 May  7 16:39 ..
lrwxrwxrwx 1 root root  12 May  7 16:39 pci-0000:02:00.1 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xdfefc000 irq 25'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.HDMI {
	control.1 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
nfsd
lockd
nfs_acl
auth_rpcgss
sunrpc
exportfs
vesafb
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
joydev
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
ppdev
snd_seq
usbhid
usblp
snd_timer
hid
psmouse
snd_seq_device
snd
fglrx
serio_raw
i2c_viapro
k8temp
parport_pc
soundcore
snd_page_alloc
shpchp
lp
parport
usb_storage
uas
via_rhine
floppy
sata_via
pata_via


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   16.049463] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   16.234458] HDA Intel 0000:02:00.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[   16.234512] HDA Intel 0000:02:00.1: setting latency timer to 64
[   16.234521] HDA Intel 0000:02:00.1: PCI: Disallowing DAC for device
[   16.259107] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.259116] ------------[ cut here ]------------
--
[   16.259129] Hardware name: MS-7253
[   16.259130] Modules linked in: snd_hda_codec_hdmi snd_hda_intel( ) snd_hda_codec snd_hwdep snd_pcm joydev snd_seq_midi snd_rawmidi snd_seq_midi_event ppdev snd_seq usbhid usblp snd_timer hid psmouse snd_seq_device snd fglrx(P) serio_raw i2c_viapro k8temp parport_pc soundcore snd_page_alloc shpchp lp parport usb_storage uas via_rhine floppy sata_via pata_via
[   16.259160] Pid: 445, comm: modprobe Tainted: P            2.6.38-9-generic #43-Ubuntu
--
[   16.259185]  [<c128fda7>] ? pci_ioremap_bar 0x57/0x60
[   16.259197]  [<f817a7cc>] ? azx_create 0x330/0x71a [snd_hda_intel]
[   16.259203]  [<f817aded>] ? azx_probe 0xa4/0x20f [snd_hda_intel]
[   16.259207]  [<c1292317>] ? local_pci_probe 0x47/0xb0
--
[   16.259256]  [<c12928b5>] ? __pci_register_driver 0x45/0xb0
[   16.259262]  [<f81ae017>] ? alsa_card_azx_init 0x17/0x1000 [snd_hda_intel]
[   16.259266]  [<c1001255>] ? do_one_initcall 0x35/0x170
[   16.259271]  [<f81ae000>] ? alsa_card_azx_init 0x0/0x1000 [snd_hda_intel]
[   16.259276]  [<c108898b>] ? sys_init_module 0xdb/0x230
--
[   16.259284] ---[ end trace e42a9faf2f21cf0c ]---
[   16.259286] hda-intel: ioremap error
[   16.259295] HDA Intel 0000:80:01.0: PCI INT A disabled
[   16.307267] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
--
[   28.771492] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.697567] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   35.728084] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0



```


What do I  have to do now?

---

### Post by Ryuky on 2011-05-08
can you help me lidex? i don't know what I have to do!

---

### Post by lidex on 2011-05-08
Your alsa install is not recognizing your onboard audio? Do you have it disabled in bios?

---

### Post by Ryuky on 2011-05-09
no, I don't think so.

I have 2 hdd, the first one runs ubuntu and the second one wuns windows XP. With windows I can hear everything (music, videos, youtube,...). I open the BIOS to change the os but I've never changed anything about sound or whatever.

If you tell me how do I have to check in the BIOS I'll check and say you

---

### Post by lidex on 2011-05-10
Alsa is only seeing your hdmi. Are you using hdmi in windows?
Follow the link in my sig for the alsa upgrade script.

---

### Post by Ryuky on 2011-05-10
can you help me, please?
what can I do?

---

### Post by Ryuky on 2011-05-10
I don't know. I can see ATI High Definition Audio Device and Realtek High Definition Output.

I'll try to upgrade.

---

### Post by Ryuky on 2011-06-09
well, I'm sorry but I worked hard for weeks so I didn't do anything since today.
I installed successfully als 1.0.24 but when i wrote
```
script -a -c "./AlsaUpgrade-1.0.24-2.sh -d" /tmp/Alsa_1.0.24-2_upgrade_download.log
```
appeared an error message (it's in italian, so i'll try to translate it as much correct as i can) "The file or directory doesn't exist"
then I tried
```
cat /proc/asound/version
```
```
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Jun  9 2011 for kernel 2.6.38-10-generic (SMP).

```
(i think it's ok, isn't it?)
then i tried to type aplay but
```
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:660: errore aprendo l'audio: File o directory non esistente

```

Can you help me again?
I don't have to work for a week, so i'll reply as fast as i can

---

### Post by lidex on 2011-06-09
As far as debugging that script, I can't really help. We can take a look at your alsa install as it now stands, and go from there.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by mastablasta on 2011-06-10
from a live CD you can play .ogg files. [http://en.wikipedia.org/wiki/Ogg](http://en.wikipedia.org/wiki/Ogg)
 
you can also install restricted extras to play mp3 and youtube but the install will be lost on reboot.
 
check the alsamixer that volume is up.
 
also if you failed to install alsa via script then there is a PPA you can use or you can also do it manually. but you will still have to add the PPA later on so it updates on kernel update.
 
Here is the link for manual ALSA upgrade/reinstall: 
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
you can copy paste the commands in terminal.

---

### Post by Ryuky on 2011-06-10
@lidex

this is what i found:
```
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Jun 10 14:24:17 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      MICRO-STAR INTERNATIONAL CO., LTD
Product Name:      MS-7253
Product Version:   1.0


!!Kernel Information
!!------------------

Kernel release:    2.6.38-10-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


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

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xdfefc000 irq 25


!!PCI Soundcards installed in the system
!!--------------------------------------

02:00.1 Audio device: ATI Technologies Inc RV710/730
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

02:00.1 0403: 1002:aa38
	Subsystem: 174b:aa38
--
80:01.0 0403: 1106:3288 (rev 10)
	Subsystem: 1462:7253


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

!!Module: snd_hda_intel
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 1
     0x02
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  4 Jun 10  2011 /dev/snd/controlC0
crw-rw----  1 root audio 116,  3 Jun 10  2011 /dev/snd/hwC0D0
crw-rw----  1 root audio 116,  2 Jun 10 16:18 /dev/snd/pcmC0D3p
crw-rw----  1 root audio 116,  1 Jun 10  2011 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jun 10  2011 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Jun 10  2011 .
drwxr-xr-x 3 root root 160 Jun 10  2011 ..
lrwxrwxrwx 1 root root  12 Jun 10  2011 pci-0000:02:00.1 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xdfefc000 irq 25'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100100'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!-------------

--startcollapse--
state.HDMI {
	control.1 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
vesafb
snd_hda_codec_hdmi
nfsd
lockd
nfs_acl
auth_rpcgss
snd_hda_intel
sunrpc
exportfs
snd_hda_codec
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
snd_page_alloc
ppdev
joydev
fglrx
psmouse
parport_pc
serio_raw
k8temp
shpchp
i2c_viapro
lp
parport
usbhid
hid
usb_storage
uas
floppy
sata_via
via_rhine
pata_via


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[   22.536759] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   22.551551] HDA Intel 0000:02:00.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[   22.551612] HDA Intel 0000:02:00.1: setting latency timer to 64
[   22.551623] HDA Intel 0000:02:00.1: PCI: Disallowing DAC for device
[   22.575479] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
--
[   22.628841] NFSD: starting 90-second grace period
[   22.677897] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.677906] ------------[ cut here ]------------
--
[   22.677916] Hardware name: MS-7253
[   22.677918] Modules linked in: snd_hda_codec_hdmi nfsd lockd nfs_acl auth_rpcgss snd_hda_intel( ) sunrpc exportfs snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc ppdev joydev fglrx(P) psmouse parport_pc serio_raw k8temp shpchp i2c_viapro lp parport usbhid hid usb_storage uas floppy sata_via via_rhine pata_via
[   22.677951] Pid: 479, comm: modprobe Tainted: P            2.6.38-10-generic #44-Ubuntu
--
[   22.677975]  [<c128ff77>] ? pci_ioremap_bar 0x57/0x60
[   22.677983]  [<f81dd820>] ? azx_probe 0x3b4/0xb3f [snd_hda_intel]
[   22.677988]  [<c102d978>] ? default_spin_lock_flags 0x8/0x10
--
[   22.678050]  [<c1292a85>] ? __pci_register_driver 0x45/0xb0
[   22.678056]  [<f81ff017>] ? alsa_card_azx_init 0x17/0x1000 [snd_hda_intel]
[   22.678060]  [<c1001255>] ? do_one_initcall 0x35/0x170
[   22.678065]  [<f81ff000>] ? alsa_card_azx_init 0x0/0x1000 [snd_hda_intel]
[   22.678070]  [<c1088afb>] ? sys_init_module 0xdb/0x230
--
[   22.678076] ---[ end trace a4fa0f1e3e466d13 ]---
[   22.678079] ALSA hda_intel.c:2543: ioremap error
[   22.678090] HDA Intel 0000:80:01.0: PCI INT A disabled
[   22.918405] vesafb: framebuffer at 0xc0000000, mapped to 0xf8700000, using 5824k, total 5824k
--
[   25.824642] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   29.033953] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   30.507792] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0



```

@mastablasta
i tried to open the alsamixer and this is what i saw:
[[IMG]http://img62.imageshack.us/img62/52/aslamixer.png[/IMG]](http://img62.imageshack.us/i/aslamixer.png/)


The link for manual ALSA upgrade/install is for 10.04, can I use it with 11.04?

---

### Post by lidex on 2011-06-11
Looks very similar to this:
[http://ubuntuforums.org/showthread.php?t=1593095](http://ubuntuforums.org/showthread.php?t=1593095)

---

### Post by williamlofton on 2011-06-11
I am a novice, just switching from windows, actually stumbled on ubuntu and now love it, but like i said novice, I install from live cd to ver. 10.10 , everything was wonderful, was learning the system slowly but then I upgraded to 11.04 and now i have no audio, not sure where to go or what to do, make sure you understand i am a professional chef, not a programmer or anything close, and i could definately use some help, i downloaded the 10.10 manual and am reading it now but would like to have music from my laptop in the mean time , thanks ahead of time, i am looking forward to this new adventure

---

### Post by Ryuky on 2011-06-11
Thank you lidex, i'll read it but, there are 11 pages, so i think to finish it tomorrow or the day after.
probably i'll reply here i'll found errors

---

### Post by mörgæs on 2011-06-12
> **williamlofton said:**
> I am a novice, just switching from windows, actually stumbled on ubuntu and now love it, but like i said novice, I install from live cd to ver. 10.10 , everything was wonderful, was learning the system slowly but then I upgraded to 11.04 and now i have no audio, not sure where to go or what to do, make sure you understand i am a professional chef, not a programmer or anything close, and i could definately use some help, i downloaded the 10.10 manual and am reading it now but would like to have music from my laptop in the mean time , thanks ahead of time, i am looking forward to this new adventure

Hi, welcome to the fora. 

11.04 has its share of problems, so if you are a beginner I would advice you to stay with 10.10 for as long as it is supported (that is, until april 2012).

---

