---
title: "Sony VGN-TZ190N No Sound"
date: 2013-05-22
forum: Hardware
---

### Post by ErroneousRex on 2013-05-22
Hey guys,

I've tried a number of things based on what I've found on this site but to no avail. Basically, I cannot get Ubuntu to detect the soundcard.

Running Ubuntu 12.04, driver support from Sony is only for Vista (gross), I'll post the results of aplay -l and lspci:

```
zac@zac-laptop:~$ sudo aplay -l
[sudo] password for zac: 
aplay: device_list:252: no soundcards found...

```
and
```
zac@zac-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
09:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
09:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
09:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
```

I'll be much abliged to any help I can get!

Thanks,
-Z

EDIT:

So I have already gone through the sound troubleshooting Procedure and I hit some roadblocks. Alsamixer does not seem to work. Just crashes. Here are the results of the lines the procedure asks me to post.

```
zac@zac-laptop:~$ wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
--2013-05-22 18:14:42--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org (www.alsa-project.org)... 77.48.224.243
Connecting to www.alsa-project.org (www.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh [following]
--2013-05-22 18:14:43--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;hb=refs/heads/build;f=alsa/utils/alsa-info.sh
Resolving git.alsa-project.org (git.alsa-project.org)... 77.48.224.243
Connecting to git.alsa-project.org (git.alsa-project.org)|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,791       126K/s   in 0.2s    

2013-05-22 18:14:45 (126 KB/s) - `alsa-info.sh' saved [27791]

ALSA Information Script v 0.4.62
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

See './alsa-info.sh --help' for command line options.

/sbin/alsactl: save_state:1580: No soundcards found...
cat: /tmp/alsa-info.SwvfQ2TjyI/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=a9f6dfd5bc50511e9df4e58cfc22ecb575ac0b9d

Please inform the person helping you.
```


```
zac@zac-laptop:~$ bash alsa-info.sh --stdout
/sbin/alsactl: save_state:1580: No soundcards found...
cat: /tmp/alsa-info.cHtiSyuFan/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.62
!!################################

!!Script ran on: Thu May 23 01:19:42 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 12.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"


!!DMI Information
!!---------------

Manufacturer:      Sony Corporation
Product Name:      VGN-TZ190N
Product Version:   J002LE5M
Firmware Version:  R0052N7


!!Kernel Information
!!------------------

Kernel release:    3.2.0-43-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25


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


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
    Subsystem: 104d:900e


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
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  1 May 22 18:12 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 May 22 18:12 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:252: no soundcards found...

ARECORD

arecord: device_list:252: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
tpm_infineon
joydev
snd_hda_intel
snd_hda_codec
arc4
snd_hwdep
snd_pcm
uvcvideo
option
videodev
pcmcia
snd_seq_midi
usb_wwan
iwl4965
usbserial
snd_rawmidi
snd_seq_midi_event
psmouse
yenta_socket
pcmcia_rsrc
snd_seq
r592
serio_raw
snd_timer
snd_seq_device
pcmcia_core
memstick
bnep
btusb
rfcomm
sony_laptop
tpm_tis
bluetooth
iwl_legacy
parport_pc
mac80211
ppdev
snd
mac_hid
soundcore
cfg80211
snd_page_alloc
coretemp
binfmt_misc
lp
parport
usb_storage
i915
firewire_ohci
firewire_core
drm_kms_helper
crc_itu_t
drm
sky2
i2c_algo_bit
video


!!ALSA/HDA dmesg
!!--------------

[   14.007451] init: failsafe main process (804) killed by TERM signal
[   14.019286] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.019405] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   14.019466] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   14.027018] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
--
[   14.036390] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.041695] hda-intel: no codecs found!
[   14.041818] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[   14.043694] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7

```

Here is the output to Step 4

```
zac@zac-laptop:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo alsa force-reload; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version 1.0.24.
--- no soundcards ---
  1:        : sequencer
 33:        : timer
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for zac: 
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/zac/.asound*': No such file or directory
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://security.ubuntu.com precise-security Release              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://ppa.launchpad.net precise Release                         
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex           
Ign http://archive.canonical.com precise/partner TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources           
Hit http://us.archive.ubuntu.com precise/universe Sources             
Hit http://us.archive.ubuntu.com precise/multiverse Sources           
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Ign http://archive.canonical.com precise/partner Translation-en_US    
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Ign http://archive.canonical.com precise/partner Translation-en       
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:3 http://us.archive.ubuntu.com precise-updates/main Sources [384 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Get:4 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]                                                                       
Get:5 http://us.archive.ubuntu.com precise-updates/universe Sources [87.9 kB]                                                                         
Get:6 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]                                                                       
Get:7 http://us.archive.ubuntu.com precise-updates/main i386 Packages [626 kB]                                                                        
Get:8 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]                                                                 
Get:9 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [205 kB]                                                                    
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]                                                                
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                                                                                
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                          
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                          
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                                                                            
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                                                          
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                                                                    
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                                                    
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                                                      
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                                                                  
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                            
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                                                            
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                                                              
Fetched 1,388 kB in 22s (62.7 kB/s)                                                                                                                   
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
H/W path               Device      Class       Description
==========================================================
                                   system      Notebook
/0                                 bus         VAIO
/0/0                               memory      111KiB BIOS
/0/4                               processor   Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz
/0/4/5                             memory      32KiB L1 cache
/0/4/6                             memory      2MiB L2 cache
/0/4/0.1                           processor   Logical CPU
/0/4/0.2                           processor   Logical CPU
/0/a                               memory      2GiB System Memory
/0/a/0                             memory      2GiB SODIMM DDR
/0/a/1                             memory      SODIMM [empty]
/0/1                               processor   
/0/1/0.1                           processor   Logical CPU
/0/1/0.2                           processor   Logical CPU
/0/100                             bridge      Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
/0/100/2                           display     Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
/0/100/2.1                         display     Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
/0/100/1b                          multimedia  N10/ICH 7 Family High Definition Audio Controller
/0/100/1c                          bridge      N10/ICH 7 Family PCI Express Port 1
/0/100/1c/0            eth0        network     88E8055 PCI-E Gigabit Ethernet Controller
/0/100/1c.1                        bridge      N10/ICH 7 Family PCI Express Port 2
/0/100/1c.1/0          wlan0       network     PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
/0/100/1c.2                        bridge      N10/ICH 7 Family PCI Express Port 3
/0/100/1c.3                        bridge      N10/ICH 7 Family PCI Express Port 4
/0/100/1d                          bus         N10/ICH 7 Family USB UHCI Controller #1
/0/100/1d.1                        bus         N10/ICH 7 Family USB UHCI Controller #2
/0/100/1d.2                        bus         N10/ICH 7 Family USB UHCI Controller #3
/0/100/1d.3                        bus         N10/ICH 7 Family USB UHCI Controller #4
/0/100/1d.7                        bus         N10/ICH 7 Family USB2 EHCI Controller
/0/100/1e                          bridge      82801 Mobile PCI Bridge
/0/100/1e/4                        bridge      RL5c476 II
/0/100/1e/4.1                      bus         R5C832 IEEE 1394 Controller
/0/100/1e/4.4                      generic     R5C592 Memory Stick Bus Host Adapter
/0/100/1f                          bridge      82801GBM (ICH7-M) LPC Interface Bridge
/0/100/1f.1            scsi0       storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.1/0.0.0      /dev/sda    disk        32GB MCBOE32GQAPQ
/0/100/1f.1/0.0.0/1    /dev/sda1   volume      29GiB EXT4 volume
/0/100/1f.1/0.0.0/2    /dev/sda2   volume      1329MiB Extended partition
/0/100/1f.1/0.0.0/2/5  /dev/sda5   volume      1329MiB Linux swap / Solaris partition
/0/100/1f.3                        bus         N10/ICH 7 Family SMBus Controller
/0/2                   scsi2       storage     
/0/2/0.0.0             /dev/cdrom  disk        DVD-RAM UJ-852S
total 0
drwxr-xr-x   2 root root       80 May 22 18:12 .
crw-rw---T+  1 root audio 116, 33 May 22 18:12 timer
crw-rw---T+  1 root audio 116,  1 May 22 18:12 seq
drwxr-xr-x  16 root root     4300 May 22 18:27 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
09:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
09:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
09:04.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 054c:02d5 Sony Corp. 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 005: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 005 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 006: ID 1410:2120 Novatel Wireless 
Bus 001 Device 007: ID 044e:300d Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
/sbin/alsactl
Specified filename /dev/dsp does not exist.
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [c00f6ba0] f6ba0
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.008000] calibrate_delay_direct() ignoring timer_rate as we had a TSC wrap around start=4291876711 >=post_end=6485280
[    0.179676] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.196384] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.196384] HEST: Table not found.
[    0.248621] pnp: PnP ACPI: found 12 devices
[    0.291043] audit: initializing netlink socket (disabled)
[    0.291064] type=2000 audit(1369271562.284:1): initialized
[    0.351036] ERST: Table is not found!
[    0.715688] isapnp: No Plug & Play device found
[    1.022203] Fixed MDIO Bus: probed
[    1.022776] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.040318] hub 1-0:1.0: USB hub found
[    1.040972] hub 2-0:1.0: USB hub found
[    1.041528] hub 3-0:1.0: USB hub found
[    1.042077] hub 4-0:1.0: USB hub found
[    1.042622] hub 5-0:1.0: USB hub found
[    1.063145] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.740735] hub 1-6:1.0: USB hub found
[   12.590124] lp: driver loaded but no devices found
[   13.025900] type=1400 audit(1369271575.461:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=613 comm="apparmor_parser"
[   13.026775] type=1400 audit(1369271575.461:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=613 comm="apparmor_parser"
[   13.027245] type=1400 audit(1369271575.461:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=613 comm="apparmor_parser"
[   13.266867] yenta_cardbus 0000:09:04.0: CardBus bridge found [104d:900e]
[   13.317423] type=1400 audit(1369271575.753:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=640 comm="apparmor_parser"
[   13.318141] leds_ss4200: no LED devices found
[   13.318513] type=1400 audit(1369271575.753:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=640 comm="apparmor_parser"
[   13.394499] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: excluding 0x5000-0x50ff 0x5400-0x54ff
[   13.436664] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc100000-0xfc1fffff: excluding 0xfc100000-0xfc10ffff
[   13.436698] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   13.539683] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
[   13.541809] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   13.542168] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   13.732546] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   13.737128] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   13.738432] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.739496] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   13.754188] iwl4965 0000:03:00.0: loaded firmware version 228.61.2.24
[   13.761413] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xdc000-0xfffff
[   13.761475] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   13.761534] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   13.761590] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.019286] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.019405] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   14.019466] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   14.041695] hda-intel: no codecs found!
[   14.041818] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[   14.401773] type=1400 audit(1369271576.837:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=935 comm="apparmor_parser"
[   14.402631] type=1400 audit(1369271576.837:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=935 comm="apparmor_parser"
[   14.403103] type=1400 audit(1369271576.837:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=935 comm="apparmor_parser"
[   14.409382] type=1400 audit(1369271576.845:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=934 comm="apparmor_parser"
[   14.428104] type=1400 audit(1369271576.865:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=938 comm="apparmor_parser"
[   14.847681] init: alsa-restore main process (999) terminated with status 19
[   16.719565] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[  217.938770] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
[  557.258271] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
sudo: /etc/init.d/sl-modem-daemon: command not found
    Release Date: 07/11/2007
    Manufacturer: Sony Corporation
    Product Name: VGN-TZ190N
    Serial Number: 28203730-3000598
    Manufacturer: Sony Corporation
    Product Name: VAIO                            
    Serial Number: N/A                             
    Manufacturer: Sony Corporation
    Serial Number: J002LE5M
    Manufacturer: GenuineIntel
    Serial Number: N/A
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Manufacturer: Not Specified
    Serial Number: Not Specified
snd_seq_dummy          12686  0 
snd_hda_intel          32719  0 
snd_hda_codec         109562  1 snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
usb_wwan               19779  1 option
usbserial              37173  2 option,usb_wwan
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  17948  2 
bluetooth             158479  23 bnep,btusb,rfcomm
snd                    62218  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
usb_storage            39646  0 
aplay: device_list:252: no soundcards found...
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
  *-multimedia UNCLAIMED  
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fc540000-fc543fff


```

---

