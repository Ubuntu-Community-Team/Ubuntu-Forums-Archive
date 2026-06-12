---
title: "No audio in ubuntu 11.04"
date: 2012-03-10
forum: Hardware
---

### Post by zedopipo on 2012-03-10
Hello.
 I'm trying to install ubuntu 11.04  on a fujitsu scenic p300 x100 PC with a Fujitsu D1740 Motherboard (see specs below). This is a PC's who originally was delivered to schools by a government program, and came with an winxp/linux (Alinex 1.0 distro) dual boot system and the sound worked so the sound chip must be supported.
 

 In this install everything works well except the audio.
 To troubleshoot and try to solve the issue, I've done the following:
 Have follow step by step the following troubleshooting guides with no success:
 [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
 [https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)
 

 Run the lspci command witch returns in audio entry:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01), Vendor ID/Device 8086:24c5 and that corresponds to alsa driver intel8x0 according to the [http://www.calel.org/pci-devices/alsa-d... html#Intel]("http://www.calel.org/pci-devices/alsa-device-list.html#Intel"), doc so its seems the sound chip is supported.
 This is a rather confusing situation since both the previous windows installation and the board manual
 mentions an empia emp202 sound chip/codec ([http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/Boards/Motherboards/Fujitsu/D1740/D1740.htm](http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/Boards/Motherboards/Fujitsu/D1740/D1740.htm)).
 Run aplay -l command witch returns: aplay: device_list:240: nenhuma placa de som encontrada...(translation: soundboard not found...).
 Install the packages "libsox-fmt-all" and "paman", Paman is the Pulse Audio Manager to see if with Pulse Audio the sound worked but no luck. Also run the sudo apt-get dist-upgrade to fix possible missing dependencies.
 

 finally I've run the "ALSA Information Script"
 ======================================================
 !!################################
 !!ALSA Information Script v 0.4.60
 !!################################
 

 !!Script ran on: Thu Mar 8 11:51:07 UTC 2012
 

 

 !!Linux Distribution
 !!------------------
 

 Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu
 

 

 !!DMI Information
 !!---------------
 

 Manufacturer: FUJITSU SIEMENS
 Product Name: SCENIC P / SCENICO P
 Product Version:
 

 

 !!Kernel Information
 !!------------------
 

 Kernel release: 2.6.38-13-generic
 Operating System: GNU/Linux
 Architecture: i686
 Processor: i686
 SMP Enabled: Yes
 

 

 !!ALSA Version
 !!------------
 

 Driver version: 1.0.24
 Library version: 1.0.24.1
 Utilities version: 1.0.24.2
 

 

 !!Loaded ALSA modules
 !!-------------------
 

 

 

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
 

 --- no soundcards ---
 

 

 !!PCI Soundcards installed in the system
 !!--------------------------------------
 

 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
 

 

 !!Advanced information - PCI Vendor/Device/Subsystem ID's
 !!--------------------------------------------------------
 

 00:1f.5 0401: 8086:24c5 (rev 01)
 Subsystem: 1734:1058
 

 

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
 

 

 !!ALSA Device nodes
 !!-----------------
 

 crw-rw----+ 1 root audio 116, 1 Mar 8 11:42 /dev/snd/seq
 crw-rw----+ 1 root audio 116, 33 Mar 8 11:42 /dev/snd/timer
 

 

 !!Aplay/Arecord output
 !!------------
 

 APLAY
 

 aplay: device_list:240: no soundcards found...
 

 ARECORD
 

 arecord: device_list:240: no soundcards found...
 

 !!Amixer output
 !!-------------
 

 

 !!Alsactl output
 !!-------------
 

 --startcollapse--
 --endcollapse--
 

 

 !!All Loaded Modules
 !!------------------
 

 Module
 binfmt_misc
 dm_crypt
 ac97_bus
 snd_pcm
 snd_seq_midi
 snd_rawmidi
 snd_seq_midi_event
 snd_seq
 ppdev
 snd_timer
 snd_seq_device
 snd
 psmouse
 parport_pc
 soundcore
 serio_raw
 snd_page_alloc
 shpchp
 lp
 parport
 dm_raid45
 xor
 btrfs
 zlib_deflate
 libcrc32c
 i915
 drm_kms_helper
 drm
 tulip
 i2c_algo_bit
 floppy
 video
 ramzswap
 xvmalloc
 

 

 !!ALSA/HDA dmesg
 !!------------------
 ==============================================
 Furthermore I've checked the soundchip support in ([http://www.linux-drivers.org/audio.html](http://www.linux-drivers.org/audio.html)) and it mentions 82801AA and IHC4, I guess the meaning is: supported since 82801AA so again it seems the intel 82801 chip has some kind of support in linux.
 

 This is the fourth ubuntu or ubuntu based distribution I've installed (Zorin 5.2, CM17 LXDE, ubuntu 11.10 and now 11.04) did not try alinex latest version since the download link was broken, all with the same sound problem and the same diagnostic output.


 I'll Appreciate any help since I want to equip a classroom with fourteen identical pc and isn’t an option to buy sound card to all of them and at this point I'm run out of ideas.
 Best regards
 

 Zedopipo
 ==================================================
 Motherboard Specification
 mPGA478 Socket Intel® Celeron & Pentium® 4
 i845GV Chipset
 400/533/MHz FSB
 2 DIMM Slots (DDRAM)
 184 pin, 2.5V, 64 bit, DDR 200,266,333
 Max memory 2GB
 No ECC Support (unbuffered)
 Integrated i845GV Video Controller
 Integrated Audio Codec - Empia EMP202
 1 x Line In
 1 x Line Out
 1 x Microphone
 ATA 100 IDE Controller
 3 x PCI Slots (32bit)
 4 x USB ports (USB 2.0) 2 rear, 2 front
 Integrated ADMTek AN983B 10/100mbps LAN Controller
 WOL Support

---

