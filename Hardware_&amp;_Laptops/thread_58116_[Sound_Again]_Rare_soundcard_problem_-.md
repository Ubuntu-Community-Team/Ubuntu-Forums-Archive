---
title: "[Sound Again] Rare soundcard problem -"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by ILs on 2005-08-18
Greetings. I'm ILs :)

Ubuntu is a great distro (for a so compact one).
But there's just one major issue that gives me sleepless nights. My overall computer knowledge is ok, but my Linux expirience doesn't seem to be efficient enough to handle this one.

Probably it's neither my nor Ubuntu's fault.

The problem is that my Soundcard is a rare one:

Terratec SixPack 5.1+

I have tried following distributions and sound functioned properly at:
1) Mandrake Linux 10.1 - my first system, sound works when I changed "cs46xx" driver to "snd-cs46xx" in Hardware Manager
2) Fedora Core 4 - second one, sound works only when I use commercial version of OSS,

... and now it's Ubuntu with no sound at all.



_Technical Data_

1. When my system boots up some error messages come up. If your really need them - I can try to find them, but that's a bit tricky because my bootlogd fails to start.
Generaly, it's something like: "Failed to configure sound with cs46xx: Sound device is not found or busy"

2. Results of *lsmod | grep snd*

```

root@localhost:~ # lsmod|grep snd
snd_opl3_lib           10112  0
snd_hwdep               9220  1 snd_opl3_lib
snd_cs4236_lib         16000  0
snd_mpu401_uart         7168  0
snd_cs4231_lib         24832  1 snd_cs4236_lib
snd_cs46xx             80328  0
snd_rawmidi            22944  2 snd_mpu401_uart,snd_cs46xx
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd_ac97_codec         64608  1 snd_cs46xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  5 snd_cs4236_lib,snd_cs4231_lib,snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50276  13 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_cs4231_lib,snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  3 snd_cs4231_lib,snd_cs46xx,snd_pcm
gameport                4608  1 snd_cs46xx

```


3. Results of 
```
root@localhost:~ # lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:09.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:0a.0 Unknown mass storage controller: ALi Corporation: Unknown device 5281 (rev a1)
0000:00:0a.1 Unknown mass storage controller: ALi Corporation: Unknown device 5228 (rev c6)
0000:00:0b.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

```


4. I have tried to disble acpi for pci during booting and through the */boot/config* file - doesn't work.

5. Tried to disable sound modules, incl. ESD - it doesn't helps much.

6. Tried to change driver names at the */boot/config*

7. Errors from *amixer*
```
root@localhost:~ # amixer
amixer: Mixer attach default error: No such device
root@localhost:~ # amixer controls
amixer: Control default open error: No such device


```
 

8. Errors from *alsamixer*
```
alsamixer: function snd_ctl_open failed for default: No such device
root@localhost:~ #

```

9. I've also tried to install the commercial OSS, but it won't install because of the running sound modules. When I disable modules it fails during the post-installation process.


10. Errors from bootlog

```

Thu Aug 18 22:44:33 2005: ^[[A^[[1G ^[[31m*^[[39;49m^[[74G[^[[31mfail^[[39;49m]
Thu Aug 18 22:44:33 2005: FATAL: Error inserting snd_cs[xxxx] (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs[xxxx]/snd-cs[xxxx].ko): No such device
Thu Aug 18 22:44:34 2005: FATAL: Error running install command for snd_[drivername]
...
Thu Aug 18 22:44:35 2005:  * Setting up ALSA...
Thu Aug 18 22:44:36 2005: \007Invalid card number.
Thu Aug 18 22:44:36 2005: Usage: amixer <options> command
Thu Aug 18 22:44:36 2005: Available options:
Thu Aug 18 22:44:36 2005:   -h,--help       this help
Thu Aug 18 22:44:36 2005:   -c,--card N     select the card
Thu Aug 18 22:44:36 2005:   -D,--device N   select the device, default 'default'
Thu Aug 18 22:44:36 2005:   -d,--debug      debug mode
Thu Aug 18 22:44:36 2005:   -v,--version    print version of this program
Thu Aug 18 22:44:36 2005:   -q,--quiet      be quiet
Thu Aug 18 22:44:36 2005:   -i,--inactive   show also inactive controls
Thu Aug 18 22:44:36 2005: Available commands:
Thu Aug 18 22:44:36 2005:   scontrols       show all mixer simple controls
Thu Aug 18 22:44:36 2005:   scontents
Thu Aug 18 22:44:36 2005:   sset sID P      set contents for one mixer simple control
Thu Aug 18 22:44:36 2005:   sget sID        get contents for one mixer simple control
Thu Aug 18 22:44:36 2005:   controls        show all controls for given card
Thu Aug 18 22:44:36 2005:   contents        show contents of all controls for given card
Thu Aug 18 22:44:36 2005:   cset cID P      set control contents for one control
Thu Aug 18 22:44:36 2005:   cget cID        get control contents for one control
Thu Aug 18 22:44:36 2005: \007Invalid card number.

```



I'm really stuck here :) Hope you can help me.
Thanks.


p.s.: It took me some time to figure out, but it seems like if my system loads a ISA-driver instead of the PCI version.

An IRQ conflict? Wrong driver? soundsystem didn't recognize the card??


Some information from HWINFO
```
19: PCI 09.0: 0401 Multimedia audio controller
  [Created at pci.244]
  Unique ID: WL76.N2X2teUpZ00
  SysFS ID: /devices/pci0000:00/0000:00:09.0
  SysFS BusID: 0000:00:09.0
  Hardware Class: sound
  Model: "TERRATEC CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]"
  Vendor: pci 0x1013 "Cirrus Logic"
  Device: pci 0x6003 "CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]"
  SubVendor: pci 0x153b "TERRATEC Electronic GmbH"
  SubDevice: pci 0x1136
  Revision: 0x01
  Driver: "cs46xx"
  Memory Range: 0xf0102000-0xf0102fff (rw,non-prefetchable)
  Memory Range: 0xf0000000-0xf00fffff (rw,non-prefetchable)
  IRQ: 10 (8443 events)
  Driver Info #0:
    Driver Status: cs46xx is active
    Driver Activation Cmd: "modprobe cs46xx"
  Driver Info #1:
    Driver Info: snd-cs46xx
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by ILs on 2005-08-19
> **ILs]Greetings. I'm ILs :)

Ubuntu is a great distro (for a so compact one).
But there's just one major issue that gives me sleepless nights. My overall computer knowledge is ok, but my Linux expirience doesn't seem to be efficient enough to handle this one.

Probably it's neither my nor Ubuntu's fault.

The problem is that my Soundcard is a rare one:

Terratec SixPack 5.1+

I have tried following distributions and sound functioned properly at:
1) Mandrake Linux 10.1 - my first system, sound works when I changed "cs46xx" driver to "snd-cs46xx" in Hardware Manager
2) Fedora Core 4 - second one, sound works only when I use commercial version of OSS,

... and now it's Ubuntu with no sound at all.



_Technical Data_

1. When my system boots up some error messages come up. If your really need them - I can try to find them, but that's a bit tricky because my bootlogd fails to start.
Generaly, it's something like: "Failed to configure sound with cs46xx: Sound device is not found or busy"

2. Results of *lsmod | grep snd*

```

root@localhost:~ # lsmod|grep snd
snd_opl3_lib           10112  0
snd_hwdep               9220  1 snd_opl3_lib
snd_cs4236_lib         16000  0
snd_mpu401_uart         7168  0
snd_cs4231_lib         24832  1 snd_cs4236_lib
snd_cs46xx             80328  0
snd_rawmidi            22944  2 snd_mpu401_uart,snd_cs46xx
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd_ac97_codec         64608  1 snd_cs46xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  5 snd_cs4236_lib,snd_cs4231_lib,snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50276  13 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_cs4231_lib,snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  3 snd_cs4231_lib,snd_cs46xx,snd_pcm
gameport                4608  1 snd_cs46xx

```


3. Results of 
```
root@localhost:~ # lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:09.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:0a.0 Unknown mass storage controller: ALi Corporation: Unknown device 5281 (rev a1)
0000:00:0a.1 Unknown mass storage controller: ALi Corporation: Unknown device 5228 (rev c6)
0000:00:0b.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

```


4. I have tried to disble acpi for pci during booting and through the */boot/config* file - doesn't work.

5. Tried to disable sound modules, incl. ESD - it doesn't helps much.

6. Tried to change driver names at the */boot/config*

7. Errors from *amixer*
```
root@localhost:~ # amixer
amixer: Mixer attach default error: No such device
root@localhost:~ # amixer controls
amixer: Control default open error: No such device


```
 

8. Errors from *alsamixer*
```
alsamixer: function snd_ctl_open failed for default: No such device
root@localhost:~ #

```

9. I've also tried to install the commercial OSS, but it won't install because of the running sound modules. When I disable modules it fails during the post-installation process.


10. Errors from bootlog

```

Thu Aug 18 22:44:33 2005: ^[[A^[[1G ^[[31m*^[[39 said:**
> 
Thu Aug 18 22:44:33 2005: FATAL: Error inserting snd_cs[xxxx] (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs[xxxx]/snd-cs[xxxx].ko): No such device
Thu Aug 18 22:44:34 2005: FATAL: Error running install command for snd_[drivername]
...
Thu Aug 18 22:44:35 2005:  * Setting up ALSA...
Thu Aug 18 22:44:36 2005: \007Invalid card number.
Thu Aug 18 22:44:36 2005: Usage: amixer <options> command
Thu Aug 18 22:44:36 2005: Available options:
Thu Aug 18 22:44:36 2005:   -h,--help       this help
Thu Aug 18 22:44:36 2005:   -c,--card N     select the card
Thu Aug 18 22:44:36 2005:   -D,--device N   select the device, default 'default'
Thu Aug 18 22:44:36 2005:   -d,--debug      debug mode
Thu Aug 18 22:44:36 2005:   -v,--version    print version of this program
Thu Aug 18 22:44:36 2005:   -q,--quiet      be quiet
Thu Aug 18 22:44:36 2005:   -i,--inactive   show also inactive controls
Thu Aug 18 22:44:36 2005: Available commands:
Thu Aug 18 22:44:36 2005:   scontrols       show all mixer simple controls
Thu Aug 18 22:44:36 2005:   scontents
Thu Aug 18 22:44:36 2005:   sset sID P      set contents for one mixer simple control
Thu Aug 18 22:44:36 2005:   sget sID        get contents for one mixer simple control
Thu Aug 18 22:44:36 2005:   controls        show all controls for given card
Thu Aug 18 22:44:36 2005:   contents        show contents of all controls for given card
Thu Aug 18 22:44:36 2005:   cset cID P      set control contents for one control
Thu Aug 18 22:44:36 2005:   cget cID        get control contents for one control
Thu Aug 18 22:44:36 2005: \007Invalid card number.

```



I'm really stuck here :) Hope you can help me.
Thanks.


p.s.: It took me some time to figure out, but it seems like if my system loads a ISA-driver instead of the PCI version.

An IRQ conflict? Wrong driver? soundsystem didn't recognize the card??


Some information from HWINFO
```
19: PCI 09.0: 0401 Multimedia audio controller
  [Created at pci.244]
  Unique ID: WL76.N2X2teUpZ00
  SysFS ID: /devices/pci0000:00/0000:00:09.0
  SysFS BusID: 0000:00:09.0
  Hardware Class: sound
  Model: "TERRATEC CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]"
  Vendor: pci 0x1013 "Cirrus Logic"
  Device: pci 0x6003 "CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]"
  SubVendor: pci 0x153b "TERRATEC Electronic GmbH"
  SubDevice: pci 0x1136
  Revision: 0x01
  Driver: "cs46xx"
  Memory Range: 0xf0102000-0xf0102fff (rw,non-prefetchable)
  Memory Range: 0xf0000000-0xf00fffff (rw,non-prefetchable)
  IRQ: 10 (8443 events)
  Driver Info #0:
    Driver Status: cs46xx is active
    Driver Activation Cmd: "modprobe cs46xx"
  Driver Info #1:
    Driver Info: snd-cs46xx
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
 I have fixed the sound and it's ok now. 

But the most idiotic thing, as it seems to me, is that is I had to remove GDM, UBUNTU-DESKTOP, UBUNTU-BASE just to install a newer version of ALSA Drivers, Tools and Libraries.

Why can't I update ALSA 1.0.8 to 1.0.9b through the Synaptic?

---

