---
title: "Soundcard not working anymore"
date: 2010-07-10
forum: Hardware
---

### Post by mdekoning on 2010-07-10
I've installed Kubuntu 10.04 on my new laptop next to the existing Windows 7 and everything seems to be working fine, except for the sound. I've had the problem that the sound of the internal speakers wouldn't mute when plugging in headphones. I've tried to fix it by upgrading to new Alsa drivers, but now my laptop won't recognize the soundcard anymore. Everything is still working perfectly in Windows 7. Can anybody help me fix this?

aplay -l returns:

aplay: device_list:207: no soundcards found...

lspci returns:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by mdekoning on 2010-07-10
Maybe this will help as well.

uname -a returns:

Linux Laptop01 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux

dpkg -l | grep "alsa" returns:

ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-tools                           1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                         0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                 1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 

head -n 1 /proc/asound/card*/codec#* returns:

head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

I hope this helps.

---

### Post by lidex on 2010-07-10
Looks like alsa is borked.
EDIT: Try upgrading via the alsa-upgrade link in my sig.

---

### Post by mdekoning on 2010-07-11
That fixed it, sound is working again. Even better, it also fixed the problem with the internal speakers I was initially trying to fix. The internal speakers now automatically mute whenever a headphone is plugged in. Thanks a lot for helping out.

---

### Post by lidex on 2010-07-11
You're welcome. Would you mark the thread as solved using 'Thread Tools' up top please?

---

