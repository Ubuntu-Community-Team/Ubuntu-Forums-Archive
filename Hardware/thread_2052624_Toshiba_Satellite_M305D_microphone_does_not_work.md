---
title: "Toshiba Satellite M305D microphone does not work"
date: 2012-09-03
forum: Hardware
---

### Post by sb92075 on 2012-09-03
```

Your ALSA information is located at 
[http://www.alsa-project.org/db/?f=0f41a979305501ca12e18d1a50547d9ed692c6fe](http://www.alsa-project.org/db/?f=0f41a979305501ca12e18d1a50547d9ed692c6fe)

bcm@bcm-laptop:~$ sudo dmidecode -t bios
[sudo] password for bcm: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: TOSHIBA
	Version: V2.20  
	Release Date: 10/01/2008
	Address: 0xE47B0
	Runtime Size: 112720 bytes
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		IEEE 1394 boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x000C, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		enUS
		jaJP
		frFR
	Currently Installed Language: enUS

bcm@bcm-laptop:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: TOSHIBA
	Product Name: Satellite M305D
	Version: Not Applicable                  
	Serial Number: 78217689W

Handle 0x0009, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: ATI RS780M

bcm@bcm-laptop:~$ uname -a
Linux bcm-laptop 2.6.32-42-generic #95-Ubuntu SMP Wed Jul 25 15:56:09 UTC 2012 x86_64 GNU/Linux
bcm@bcm-laptop:~$ 

bcm@bcm-laptop:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-hda-intel model=6stack-dig
options snd-hda-intel model=toshiba
bcm@bcm-laptop:~$ sudo vi /etc/modprobe.d/alsa-base.conf
bcm@bcm-laptop:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-hda-intel model=toshiba
bcm@bcm-laptop:~$ 

bcm@bcm-laptop:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bcm@bcm-laptop:~$ sudo dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
bcm@bcm-laptop:~$ sudo dpkg -l | grep "pulse"
ii  gstreamer0.10-pulseaudio             0.10.21-1ubuntu3                                GStreamer plugin for PulseAudio
ii  libcanberra-pulse                    0.22-1ubuntu2                                   PulseAudio backend for libcanberra
ii  libpulse-browse0                     1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries (zeroconf suppor
ii  libpulse-mainloop-glib0              1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries (glib support)
ii  libpulse0                            1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio client libraries
ii  libsdl1.2debian-pulseaudio           1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and Pulse
ii  pulseaudio                           1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio sound server
ii  pulseaudio-esound-compat             1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 PulseAudio ESD compatibility layer
ii  pulseaudio-module-bluetooth          1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Bluetooth module for PulseAudio sound server
ii  pulseaudio-module-gconf              1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 GConf module for PulseAudio sound server
ii  pulseaudio-module-x11                1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 X11 module for PulseAudio sound server
ii  pulseaudio-module-zeroconf           1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Zeroconf module for PulseAudio sound server
ii  pulseaudio-utils                     1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Command line tools for the PulseAudio sound 
ii  vlc-plugin-pulse                     1.0.6-1ubuntu1.8                                PulseAudio plugin for VLC
bcm@bcm-laptop:~$ sudo head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20561 (Hermosa)
bcm@bcm-laptop:~$ 


```
FWIW - all "Mute" box are not checked; AFAIK.

Let me know if anyone needs more or different details

---

