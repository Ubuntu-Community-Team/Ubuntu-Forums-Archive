---
title: "Audio detected but mute (i can't hear a sound) after reboot, Ubuntu 10.04 Pulseaudio"
date: 2010-11-21
forum: Hardware
---

### Post by sberla54 on 2010-11-21
Hi everybody.

I'm having a bad problem with my audio: the audio device get detected, it seems like working but i can't hear a sound.
Everything worked well, then i rebooted and after the reboot the audio started to have this problem.

I've already posted my problem on the italian forum but it seems like nobody can help me: [http://forum.ubuntu-it.org/index.php/topic,425500.0.html](http://forum.ubuntu-it.org/index.php/topic,425500.0.html)

I use the integrated audio device of my motherboard.

I'm using Ubuntu 10.04 with 2.6.32 kernel.
I've tried with the base kernel of Ubuntu 10.04 too, the 2.6.31...

I've had this same problem with the 10.04 just installed (and after some reboots) but deleting the .pulse folder everything came back to work. This time the problem remains.
If i delete che .pulse folder, than i disconnect and reconnect, the sound card isn't detected anymore and going to Preferences > Sound i get the error "Waiting for answer from audio server" (or something like that...i'm translating from italian...).

I've already looked at a lot of forum's posts and howto, just like these one:
[http://www.lffl.org/2010/03/risolvere-il-problema-audio-su-ubuntu.html](http://www.lffl.org/2010/03/risolvere-il-problema-audio-su-ubuntu.html)
[http://www.lffl.org/2010/05/risolvere-il-problema-audio-su-ubuntu.html](http://www.lffl.org/2010/05/risolvere-il-problema-audio-su-ubuntu.html)
[http://forum.ubuntu-it.org/index.php/topic,169204.0.html](http://forum.ubuntu-it.org/index.php/topic,169204.0.html)
[http://forum.ubuntu-it.org/index.php/topic,400313.msg3118363.html](http://forum.ubuntu-it.org/index.php/topic,400313.msg3118363.html)
(always in italian).

Summarizing, that's what i've tried to do:
```

sudo /sbin/alsa force-reload
sudo dpkg-reconfigure alsa-base
sudo alsa-utils reset

```and

```

sudo add-apt-repository ppa:ubuntu-audio-dev && sudo apt-get update && sudo apt-get dist-upgrade 

```But it had been unusefull....

I've tried alsamixer too, naturally, but it seems rightly configured, with volumes up, and set on the "ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)" device.

Here there are some outputs that can be usefull:
```

root@neuromante:~# lspci | grep -i audio 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

``````

root@neuromante:~# cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 892

```I don't know why it finds 2 audio device...

```

sberla54@neuromante:~$ lspci -k
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
    Kernel driver in use: ohci_hcd
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
04:00.0 IDE interface: VIA Technologies, Inc. PATA IDE Host Controller
    Kernel driver in use: pata_via
    Kernel modules: pata_via
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Kernel driver in use: r8169
    Kernel modules: r8169

``````

sberla54@neuromante:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: SB [HDA ATI SB], dispositivo 0: HDA Generic [HDA Generic]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

``````

sberla54@neuromante:~$ pulseaudio
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="2" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
E: socket-server.c: bind(): Indirizzo già in uso
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Inizializzazione del demone non riuscita.

``````

sberla54@neuromante:~$ pulseaudio --dump-conf
### Lettura dal file di configurazione: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-0.9.21/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = auto
log-level = notice
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 8
default-fragment-size-msec = 10
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 1000000

```I'm wondering it could be a problem of mis-detected hardware...as you may see, there are 2 detected audio device, but only one should be the right one.

So, i've installe Pulseaudio device chooser ([http://0pointer.de/lennart/projects/padevchooser/](http://0pointer.de/lennart/projects/padevchooser/)) with:
```

apt-get install padevchooser

```and tried to set as Sink:
alsa-output.pci-0000-00_14.2.analog-stereo

and as default source:
alsa-input.pci-0000-00_14.2.analog-stereo

but i just got the following error: Failed to connect stream: Entità inesistente (failed to connect to stream, not existing entity).

Maybe the problem is that Pulseaudio says:
```

E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="2" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""):

```and it's trying to use the device "pci-0000_01_00.1", that is the "01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)", when the right device should be instead the "0000-00_14.2", that is the "00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)".

Am i right?
Could it be that the cause of my problem?

It seems like a common problem with Ubuntu 10.04....

I don't want to upgrade (or reinstall) to 10.10, because i wanted to keep the LTS version, because i just want a stable and working Linux system and i don't want to upgrade every 6 months....

If i don't find a fix for this matter, by the way, i'm worried that i'll have to reinstall the 10.04....and i'm really sick for that....

It's so a silly problem, because before the reboot everything worked well for months and now i can't make my audio work....it makes no sense at all...

Have you got any suggestion?

Is there a way to staticly configure Pulseaudio, just like it used to be with Alsa?
Or, is there a way to blacklist the second audio device, so i can try both one by one, looking for the right one?

Could it be usefull to reinstall Pulseaudio? 
I haven't done it so far, because it wanted to remove "ubuntu-desktop" too, and i was afraid that it could cause some major problems...

I hope you could help me.
I'm getting mad from all the week end on this problem and i really don't know how to fix it.

Thank you.

---

### Post by sberla54 on 2010-11-21
I've just red this post too:
[http://ubuntuforums.org/showthread.php?t=1088978](http://ubuntuforums.org/showthread.php?t=1088978)

And this howto:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

And this guide too:
[http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html](http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html)

I've upgraded to latest alsa driver with this script: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

And now i've got these drivers:
```

sberla54@neuromante:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Nov 22 2010 for kernel 2.6.32-25-generic (SMP).

```but nothing is changed...i still can't hear a sound...i just have a more complete management of my audio device...

Before i had tried with the upgrade guide of this post: [http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html](http://black-pixel.net/alc892realtek-id-892-on-mint-linuxubuntu.html)
but i had some compiling/installation problems...

I can't find my codec (ALC892) in the howto [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ....but it seems supported by the alsa version 1.0.23 i've just installed...

By the way, i've looked on DistroWatch ([http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)) and i've seen Ubuntu 10.10 has alsa 1.0.23 so i've tried it live but i can't hear a sound even with it...i have the same problem...applications seems to work ok but everything's mute.

I can't even hear a sound with the 10.04, by the way....

I'm sure it's not an hardware problem of my sound cases...i've already tried with the headphones connected to the output port of my audio device...
I'll try with windows too, but i'm sure...they were working until yesterday morning...before this damned reboot...

It makes no sense at all...what am i supposed to do? Change distribution? Come back to Windows? 

At least 10.10 should work fine...but it seems not...

My motherboard isn't even so new...i suppose a lot of people must have my same audio device and my same audio codec, Realtec ALC892....

Have you got any idea?

If i can't fix, i think i'll try to install Ubuntu 10.10...maybe once installed the audio will work....

---

### Post by sberla54 on 2010-11-23
I keep on answering by myself :)

I think i've solved my problem...
It seems like it was a some kind of temporary hardware block.
When i turned off the pc (no, i hadn't did it before, i just rebooted it a lot of time...) and kept it of for a couple of minutes, then turned it on again, the sound came back....
I didn't changed drivers or configurations since my last reboot...

To be more accurate, that's what i did:
- Turned off the pc
- Rebooted to Ubuntu 10.10 live cd
- Noticed that this time with Ubuntu 10.10 live the audio worked (it didn't worked on the tests i did before...)
- Rebooted to the installed Ubuntu 10.04
- The audio worked well.

So, i don't think it was a software matter, but i'm not sure of it.

Anyway, the only thing that i did was upgrading Alsa to 1.0.23 using the Alsa Upgrade Script: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
Nothing else.

Those are my actual configurations and outputs, and they seems to me the same that before the switch off of the pc:

```

sberla54@neuromante:~$ pactl stat
Attualmente in uso: 73 blocchi contenenti 423,0 KiB byte in totale.
Allocati durante l'intera esecuzione: 1006000 blocchi contenenti 1,6 GiB byte in totale.
Dimensione della cache dei campioni: 0 B
Nome utente: sberla54
Nome host: neuromante
Nome server: pulseaudio
Versione server: 0.9.21-63-gd3efa-dirty
Specifica campionamento predefinita: s16le ch 2 44100 Hz
Mappa canale predefinita: front-left,front-right
Sink predefinito: ladspa_output.mbeq_1197.mbeq
Sorgente predefinita: alsa_input.usb-046d_09a4_9FA84940-02-U0x46d0x9a4.analog-mono
Cookie: ba3fde5d

```

```

sberla54@neuromante:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC892

```

```

sberla54@neuromante:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: SB [HDA ATI SB], dispositivo 0: ALC892 Analog [ALC892 Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: SB [HDA ATI SB], dispositivo 1: ALC892 Digital [ALC892 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 7: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 8: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 9: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```

```

sberla54@neuromante:~$ lspci -k
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
    Kernel driver in use: ohci_hcd
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
04:00.0 IDE interface: VIA Technologies, Inc. PATA IDE Host Controller
    Kernel driver in use: pata_via
    Kernel modules: pata_via
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Kernel driver in use: r8169
    Kernel modules: r8169

```

```

Module                  Size  Used by
btrfs                 480919  0 
zlib_deflate           21834  1 btrfs
crc32c                  2983  1 
libcrc32c               1244  1 btrfs
ufs                    73778  0 
qnx4                    7736  0 
hfsplus                77801  0 
hfs                    47269  0 
minix                  29315  0 
ntfs                   97936  0 
vfat                   10866  0 
msdos                   7936  0 
fat                    55350  2 vfat,msdos
jfs                   184803  0 
xfs                   542514  0 
exportfs                4202  1 xfs
reiserfs              243856  0 
snd_hda_codec_nvhdmi    14218  4 
binfmt_misc             7960  1 
snd_hda_codec_realtek   297355  1 
snd_usb_audio         101635  2 
snd_usbmidi_lib        19945  1 snd_usb_audio
snd_seq_dummy           1878  0 
snd_seq_oss            31522  0 
snd_hda_intel          23768  6 
snd_hda_codec          99419  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6938  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            40601  0 
snd_seq_midi            5733  0 
snd_mixer_oss          16474  1 snd_pcm_oss
snd_rawmidi            23225  2 snd_usbmidi_lib,snd_seq_midi
snd_pcm                88173  5 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57588  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   6375  0 
uvcvideo               62595  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11764  1 videodev
snd_timer              23053  2 snd_pcm,snd_seq
snd_seq_device          7112  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usblp                  12407  0 
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
parport_pc             29958  1 
asus_atk0110           10033  0 
psmouse                64576  0 
serio_raw               4918  0 
i2c_piix4               9639  0 
snd                    72231  32 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_seq_dummy,snd_seq_oss,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_seq_midi,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
edac_core              45423  0 
xhci                   41830  0 
edac_mce_amd            9278  0 
nvidia              10832442  76 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8628  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41084  0 
hid                    83472  1 usbhid
ohci1394               30260  0 
usb_storage            49961  1 
ieee1394               94771  1 ohci1394
pata_via                9072  0 
r8169                  39650  0 
pata_atiixp             4209  0 
mii                     5237  1 r8169
ahci                   37870  5 

```

I saved configurations and output of Ubuntu 10.10 live too...if i'd ever need em to replicate them on Ubuntu 10.04:

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

```
```

ubuntu@ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC892

```
```

ubuntu@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

```
```

ubuntu@ubuntu:~$ lspci -k
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: ASUSTeK Computer Inc. Device 843e
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 841b
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 8443
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ohci_hcd
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: ASUSTeK Computer Inc. Device 8443
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
    Subsystem: Device 1acc:31d3
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: Device 1acc:31d3
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8413
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
    Subsystem: ASUSTeK Computer Inc. Device 8374
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394
04:00.0 IDE interface: VIA Technologies, Inc. PATA IDE Host Controller
    Subsystem: ASUSTeK Computer Inc. Device 838f
    Kernel driver in use: pata_via
    Kernel modules: pata_via
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8432
    Kernel driver in use: r8169
    Kernel modules: r8169

```
```

ubuntu@ubuntu:~$ lspci | grep -i audio 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```
```

ubuntu@ubuntu:~$ pulseaudio --dump-conf
### Lettura dal file di configurazione: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-0.9.21/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = auto
log-level = notice
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 8
default-fragment-size-msec = 10
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 1000000

```
```

ubuntu@ubuntu:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: SB [HDA ATI SB], dispositivo 0: ALC892 Analog [ALC892 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: SB [HDA ATI SB], dispositivo 1: ALC892 Digital [ALC892 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 7: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 8: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 9: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```
```

ubuntu@ubuntu:~$ dpkg -l | grep alsa
ii  alsa-base                            1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-utils                           1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  bluez-alsa                           4.69-0ubuntu2                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.30-2                                       GStreamer plugin for ALSA

```
```

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
lp                      7342  0 
dm_crypt               11385  0 
snd_hda_codec_nvhdmi    12879  4 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  4 
snd_usb_audio          86704  1 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  2 snd_usb_audio,snd_hda_codec
snd_pcm                71475  4 snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        17413  1 snd_usb_audio
usblp                  10651  0 
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
snd_timer              19067  2 snd_pcm,snd_seq
parport_pc             26058  1 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
parport                31492  3 lp,ppdev,parport_pc
i2c_piix4               8635  0 
videodev               43098  1 uvcvideo
asus_atk0110           11423  0 
psmouse                59033  0 
snd                    49006  20 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hwdep,snd_pcm,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                 2607  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
soundcore                880  1 snd
xhci_hcd               51737  0 
squashfs               25209  1 
aufs                  152358  5268 
nls_cp437               4931  1 
isofs                  30022  1 
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
usbhid                 36882  0 
hid                    67742  1 usbhid
nouveau               516971  2 
ttm                    56633  1 nouveau
drm_kms_helper         30200  1 nouveau
drm                   168054  4 nouveau,ttm,drm_kms_helper
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci
usb_storage            40172  1 
crc_itu_t               1383  1 firewire_core
agpgart                32011  2 ttm,drm
i2c_algo_bit            5168  1 nouveau
ahci                   19013  0 
r8169                  36489  0 
mii                     4425  1 r8169
libahci                21667  3 ahci
pata_atiixp             3288  1 
pata_via                7300  0 

```
```

root@ubuntu:~# pactl stat
Attualmente in uso: 2 blocchi contenenti 81,2 KiB byte in totale.
Allocati durante l'intera esecuzione: 10646 blocchi contenenti 203,3 MiB byte in totale.
Dimensione della cache dei campioni: 17,2 KiB
Nome utente: ubuntu
Nome host: ubuntu
Nome server: pulseaudio
Versione server: 0.9.21-63-gd3efa-dirty
Specifica campionamento predefinita: s16le ch 2 44100 Hz
Mappa canale predefinita: front-left,front-right
Sink predefinito: alsa_output.pci-0000_00_14.2.analog-stereo
Sorgente predefinita: alsa_input.pci-0000_00_14.2.analog-stereo

```

Summarizing, if anyone read this and have similar problems:
- I think it was a temporary hardware block. I turned off the pc for a couple of minutes and when i turned it on again the audio came back. I didn't worked just rebooting...
- My audio card is a SBx00 Azalia (Intel HDA) with Realtec ALC892 codec that isn't really well supported by alsa and kernel
- I upgraded from alsa 1.0.22 (default of Ubuntu 10.04) to alsa 1.0.23 (default of Ubuntu 10.10) using Alsa Upgrade Script: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
- Probably, installing Ubuntu 10.10 it would have a way better support for those audio cards.
- Other tests, like removing and reinstall alsa 1.0.22, deleting .pulse folders, creating a brand new user, checking audio groups etc had been useless. 

I really hope all these information would be usefull to someone else with audio cards and problems similar to mine.

If my problem would come back, i'll update the topic :)

See ya soon.

---

### Post by spiderwort on 2011-01-22
> I think i've solved my problem...
It seems like it was a some kind of temporary hardware block.
When i turned off the pc (no, i hadn't did it before, i just rebooted it a lot of time...) and kept it of for a couple of minutes, then turned it on again, the sound came back....
I didn't changed drivers or configurations since my last reboot...

Thank you sberla54!!!

I've been banging my head on this all day ](*,) 

Followed your advice to SHUT DOWN....waited a couple minutes....booted back up to beautiful sound.

:D

---

### Post by sberla54 on 2011-01-23
I'm glad i helped you :)
This is a really weird problem :)

Talking about my system, i'm keeping on trying to permanently upgrade to Alsa 1.0.23, because sometimes, randomly, when i reboot it come back to 1.0.22 :)

See ya!

---

