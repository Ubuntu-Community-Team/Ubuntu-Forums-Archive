---
title: "Kubuntu 9.10 on hp DV6 no sound at all"
date: 2010-01-16
forum: Hardware
---

### Post by Evita on 2010-01-16
Hello there,
first I have to say that I'm completely new to linux,

I recently installed kubuntu 9.10 on a Hewlett packard pavilion dv6 1201 au,
and I get no sound at all.
As far as I understand,I installed alsamixer,since it appears in the konsole and it's not muted but still I have no sound.

Any help please?? :(

---

### Post by Evita on 2010-01-16
specs are  Product Number  VH069PA#ABJ 
  Microprocessor  2.1GHz AMD Sempron Processor for Notebook PCs SI-42 
  Microprocessor Cache  512KB L2 Cache
  Memory  1024 MB
  Memory Max  8192 MB
  Video Graphics  ATI Radeon HD 3200 Graphics with 64MB Display Cache Memory
  Hard Drive  250G (7200RPM)
  Multimedia Drive  LightScribe SuperMulti 8X DVD±RW with Double Layer Support 
  Display  16.0" Diagonal High Definition HP Brightview Display (1366x768) 
  Network Card  Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
  Wireless Connectivity  802.11bg
  Sound  Altec Lansing Speakers

SRS Premium Sound
  Keyboard  101 key compatible Full size keyboard with integrated numeric keypad
  Pointing Device  Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad
  External Ports
  4 USB 2.0
HDMI Version 1.3b
eSATA + USB 2.0
VGA
RJ-45
Expansion Port 3
2 Headphone out
Microphone in
Consumer IR
  Security
  Kensington MicroSaver lock slot
Power-on password
  Power
  ACADPT 65W dv6-10 
6 Cell

---

### Post by pi/roman on 2010-01-16
Are those speakers external or onboard?

Would you be able to upload a copy of asound.state which should be in /var/lib/alsa/asound.state?
This terminal command should make a copy in your home folder to make it easier:
sudo cp /var/lib/alsa/asound.state ~/

---

### Post by Evita on 2010-01-16
thank you for replying!

I get this list, 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

on running the sudo cp /var/lib/alsa/asound.state ~/
 I get nothing :(

---

### Post by Evita on 2010-01-16
eva-laptop:~$ /var/lib/alsa/asound.state
bash: /var/lib/alsa/asound.state: Permission denied

I got this!

---

### Post by pi/roman on 2010-01-16
Sorry maybe I should have noted in more detail.

If the command worked "sudo cp /var/lib/alsa/asound.state ~/" you should now have a copy of asound.state in your home older although it may appear as though nothing happens.  So when you make a reply and add an attachment (which is by using the paperclip icon in the reply window) and then hit browse it should browse into your home folder and the asound.state file should be in there from the previous command.  Then highlight it, click open then click upload.

---

### Post by pi/roman on 2010-01-16
If the file is not there then type "sudo find /var -name asound.state" in a terminal and see what comes up.

---

### Post by Evita on 2010-01-16
for some reason I cant upload it,is says "invalid file".I'm sorry that I'm completely clueless!I just don't wanna go back to windows...
I'm pasting it if that works 
 
state.SB {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 15
		value.1 15
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 15
		value.1 15
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Import0 Mux Capture Switch'
		value.0 false
		value.1 false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Import0 Mux Capture Volume'
		value.0 31
		value.1 31
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Import1 Mux Capture Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Import1 Mux Capture Volume'
		value.0 31
		value.1 31
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC0 Capture Switch'
		value.0 false
		value.1 false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'DAC0 Capture Volume'
		value.0 30
		value.1 30
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'DAC1 Capture Switch'
		value.0 false
		value.1 false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'DAC1 Capture Volume'
		value.0 31
		value.1 31
	}
	control.13 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Front Playback Volume'
		value.0 52
		value.1 52
	}
	control.14 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
	}
	control.15 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Mic In'
		comment.item.1 'Line In'
		iface MIXER
		name 'Mic Jack Mode'
		value 'Mic In'
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Beep Playback Switch'
		value false
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		comment.dbmin -1800
		comment.dbmax 0
		iface MIXER
		name 'PC Beep Playback Volume'
		value 0
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 52
		value.1 52
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
	}
	control.20 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		value.0 3
		value.1 3
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Mux Capture Volume'
		index 1
		value.0 3
		value.1 3
	}
	control.22 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 Mixer
		comment.item.2 'Digital Mic 1'
		iface MIXER
		name 'Digital Input Source'
		value 'Digital Mic 1'
	}
	control.23 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Analog Inputs'
		comment.item.1 Mixer
		comment.item.2 'Digital Mic 1'
		iface MIXER
		name 'Digital Input Source'
		index 1
		value 'Analog Inputs'
	}
	control.24 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'Digital Playback'
		comment.item.1 'Analog Mux 1'
		comment.item.2 'Analog Mux 2'
		iface MIXER
		name 'IEC958 Playback Source'
		value 'Digital Playback'
	}
	control.25 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.26 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.27 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.29 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
	}
	control.30 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 52
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.32 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 204
		value.1 204
	}
	control.33 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 96
		value.1 96
	}
}
state.HDMI {
	control.1 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.2 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.3 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
}

---

### Post by pi/roman on 2010-01-16
From terminal you can type "alsamixer" to bring up volume controls and make sure master pcm and IEC958 playback are all assigned a fairly high level and they are not muted.
Check to see if there is an external switch and if so and you have no external speakers go ahead and press M to mute it.

---

### Post by pi/roman on 2010-01-16
I have a problem that there is no sound from my speakers if the headphones are muted so you may want to check those too.  Press M to mute/unmute and arrow keys to change volume.

---

### Post by Evita on 2010-01-16
everything on alsamixer is supposed to be at loud levels.I have alsamixer 1.0.20,is this supposed to be the one for my card?I can't find the exact match on the list

---

### Post by pi/roman on 2010-01-16
1.0.2 is the correct version.

Can you enter "amixer scontents" in a terminal and post the output?

---

### Post by Evita on 2010-01-17
this is the output!
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

---

### Post by pi/roman on 2010-01-17
That is strange. I was expecting to see a lot more mixer controls. Hopefully someone more qualified can help you because it is beyond my ability. I would probably have you compile the new alsa driver but that would be too risky because you most likely would have errors and I probably would not know how to fix them. There is another thread with a DV6 with no sound that has been noted as solved here: [http://ubuntuforums.org/showthread.php?t=1353277](http://ubuntuforums.org/showthread.php?t=1353277)
I will continue to look for a solution and let you know if I find anything.

---

### Post by Evita on 2010-01-18
Thank you,I hope to fix it..Do you think reinstalling kubuntu will make any change?

---

### Post by pi/roman on 2010-01-18
I think first I would make sure the system is updated, I use "update manager" on the gnome desktop but I don't know if that is the same on KDE.  Then if still no sound then I would try the solutions by [Sxeptomaniac]("http://ubuntuforums.org/member.php?u=93360") in this thread: [http://ubuntuforums.org/showthread.php?t=1353277.]("http://ubuntuforums.org/showthread.php?t=1353277") Then try any other solutions listed in that thread.

As a last resort I would try to upgrade ALSA.  There is a simple method here: [http://www.webupd8.org/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html](http://www.webupd8.org/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html)
Notice the warning with this "[COLOR=#FF0000]**only upgrade if you are experiencing sound issues"**[/COLOR][COLOR=#FF0000]**[COLOR=Black][FONT=Verdana] [/FONT][/COLOR]**[/COLOR]because it may screw things up.  If so, it would probably be necessary to reinstall then.
[INDENT][COLOR=#FF0000]****[/COLOR][/INDENT]

---

### Post by pi/roman on 2010-01-19
If you are still working on this could you show the output of the following commands?

lspci -v | grep -i audio
sudo cat /etc/modprobe.d/alsa-base.*

amixer -c 1
amixer -c 0

Hopefully one of the amixer commands will return more controls than IEC958.

---

### Post by Evita on 2010-01-19
on typing 
lspci -v | grep -i audio
 sudo cat /etc/modprobe.d/alsa-base.*
 
 amixer -c 1
 amixer -c 0

I got these:


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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

---

### Post by Manyette on 2010-01-19
I have an HP Laptop also, and this thread solved the problem for me
[http://ubuntuforums.org/showthread.php?t=1341751&highlight=HP+G71+Sound+Problem](http://ubuntuforums.org/showthread.php?t=1341751&highlight=HP+G71+Sound+Problem)

---

### Post by pi/roman on 2010-01-19
Hopefully the method there will fix it, but I am curious did these 3 commands not return anything?

lspci -v | grep -i audio
 amixer -c 1
 amixer -c 0

If not could you try:
lspci -v | grep -i HDA

---

### Post by Evita on 2010-01-21
Thank you everyone,I actually reinstalled 9.10 one more time (no sound still) and then installed 

[B]sudo apt-get install linux-backports-modules-alsa-karmic-generic
[/B]

and there was sound!!But still,no sound on skype or the microphone.Any ideas?

---

