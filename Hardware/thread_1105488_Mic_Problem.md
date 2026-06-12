---
title: "Mic Problem"
date: 2009-03-24
forum: Hardware
---

### Post by williamson389 on 2009-03-24
I have never gotten my mic to work, and to be honest never noticed but i recently installed skype to talk with a friend in germany.  The more i mess around with it the more it irritates me, so anyhelp would be greatly appreciated.  i have a Acer Aspire 5100, running 64-bit hardy.  i dont know the command to list the hardware, but it is just the internal mic packaged with the laptop.

The mic wont record anything and the computer freaks out when i hit test for capture under System-preferences-sound. 

 I have already tried adjusting pulseaudio and nothing worked.  (sorry to say this but after tinkering around with pulse audio, Skype wont connect to the test call it just says audio capture problem.
~Thanks~

---

### Post by teaker1s on 2009-03-25
```
sudo lshw
```
or pci
```
 sudo lspci -v
```
usb
```
lsusb
```

possibly you have ICH7 Family sound, if you have, you may find that 

```
sudo gedit /etc/modprobe.d/alsa-base
```

then try only one of these lines to the end and save file reboot

> options snd-hda-intel model=acer-aspire
or
> options snd-hda-intel model=acer
or
> options snd-hda-intel model=auto

also in sound control you will have to select either internal or exteral mic option
If none work then just remove the line and save.

---

### Post by williamson389 on 2009-03-25
this is what lshw states, forgive me im still pretty new.  I cannot tell what identifies the mic.

bill-laptop               
    description: Notebook
    product: Aspire 5100
    vendor: Acer
    version: V2.73
    serial: LXAX90X009710058551601
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=0 uuid=62356339-3064-3331-3761-0016D4CA3C95
  *-core
       description: Motherboard
       product: Navarro
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAX90X009710058551601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V2.73 (01/23/2007)
          size: 109KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology MK-36
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: Engineering Sample
          slot: Socket M2/S1G1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good pni cx16 lahf_lm svm extapic cr8_legacy cpufreq
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 2GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS485 [Radeon Xpress 1100 IGP]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wifi0
                version: 01
                serial: 00:19:7d:f0:3a:49
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-pci:2
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: ST9120822AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AL
                serial: 5MA11GKW
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c4e06dc9
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 727dee4d-cc9f-42f5-8e78-98fdcdedfabc
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-21 22:58:28 filesystem=ext3 modified=2009-03-24 23:52:33 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-03-23 20:04:20 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 4690MiB
                   capacity: 4690MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4690MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 83
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T10N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PP02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:06:01.0
                logical name: eth0
                version: 10
                serial: 00:16:d4:ca:3c:95
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=138.87.189.138 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
           *-system
                description: SD Host controller
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 maxlatency=72 mingnt=32 module=sdhci
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
           *-memory:2
                description: FLASH memory
                product: SD/MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm cap_list
                configuration: driver=sdhci latency=0 maxlatency=72 mingnt=32 module=sdhci
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 1
          bus info: usb@3:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: TD Classic 003B
             vendor: Memorex
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: PMAP
             size: 490MiB (513MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 490MiB (513MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=7eca5b1f
              *-volume
                   description: Windows FAT volume
                   vendor: *5>+kIHC
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/TravelDrive
                   version: FAT16
                   serial: 5f40-3344
                   size: 489MiB
                   capacity: 489MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=TravelDrive mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: PANASONIC
       vendor: PANASONIC
       physical id: 1
       slot: 1st Battery
       capacity: 3900mWh
       configuration: voltage=14.8V
As for gedit, the final one is already listed(options snd-hda-intel model=auto)
and i am lost by what you mean in sound control. under system-pref-sound  i can switch between pulseaudio and alsa under capture, but i do not think that is what you mean.

Sorry for not understanding, and thanks alot for your help.

---

### Post by teaker1s on 2009-03-25
> description: Audio device
product: IXP SB4x0 High Definition Audio Controller
vendor: ATI Technologies Inc
physical id: 14.2
bus info: pci@0000:00:14.2
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: driver=HDA Intel latency=64 module=snd_hda_intel

you are using snd_hda as I suspected, if you delete
> options snd-hda-intel model=auto and put
```
options snd-hda-intel model=acer-aspire 
``` save file reboot

What you are doing is getting ubuntu to try to find your physical hardware by helping it with a known profile.

Open volume control, select device as" hda intel alsa mixer" MAKE SURE options you select internal mic and recording you unmute the microphone.

for sound testing
Applications>Sound & Video>Sound Recorder
record and play back-can you hear sound?
if not try

```
options snd-hda-intel model=acer
```

---

### Post by williamson389 on 2009-03-25
Thanks for clearing that up, but still have a couple problems.

I changed through gedit to "options snd-hda-intel model=acer-aspire",  but in volume control the only listed devices are HDA ATI SB, and ALC883 with other variations followed by Pulseaudio mixer and OSS Mixer.
I went with the Alsamixer (HDA ATI SB) but when i tested it in sound recorder, the program froze and i had to force quit.
I didnt try the other option listed
options snd-hda-intel model=acer
Any ideas?

---

### Post by teaker1s on 2009-03-26
No problem, the reason this gets a little confusing is the HDA sound is manufactured by various people. as you select a different device you are in fact connecting to the same device but in a different way.

example you can connect to your sound device with either ALSA or OSS software element

Try HDA ATI SB as this is the hardware name first, if not try the other devices listed-it's about finding a method that both works and gives you the sound sliders and switch options you require.

I'm sorry that Sound recorder is playing up, I too have had problems with it in the past, will think of an alternative and post

---

### Post by williamson389 on 2009-03-26
i tried all the options in choose device, then tested them out with skype.  i dont think it was a good way to check it though.  I tried to check under sound preferences, i tested the capture, and it froze again.  before the program froze a window popped up with (Failed to construct test pipeline for gconfaudiosrc! and some more errors

---

### Post by teaker1s on 2009-03-26
we could use audacity as a sound recorder-more complicated but if the basic sound recorder freezes.

Terminal
```
sudo apt-get install audacity
```

Will appear under Applications>Sound & Video>Audacity

---

### Post by williamson389 on 2009-03-27
Good news and bad news-
i installed audacity but that froze up.  I switched the gedit to options snd-hda-intel model=acer, and i was getting response from the mic.  Audacity and Sound recorder both will work and not freeze up. Thanks! 

There is only two problems.  Audacity&#347; input meter measured the microphones input at first.  it was extremly high and didnt variate much.  It did not record anything however. Now it doesnt even measure it on the input meter.
Also the mic&#347; feedback is coming out through my tiny little speakers plugged into the headphone jack.  If i turn the volume way up i can hear the feedback, tapping, and some version of my voice in the left speaker. I was tinkering around under volume control, and everything is unmuted.  in options both of my input sources say Mic, not front mic or line.  I feel like its gonna be an simple configuration from here
Thanks,
Edit:  also what did you mean by {in sound control you will have to select either internal or exteral mic option
If none work then just remove the line and save}

---

### Post by teaker1s on 2009-03-27
you may want to try 
```
options snd-hda-intel model=acer-aspire
```

I'm sorry this is trial and error, internal mic is set via the volume icon on desktop.

you will also find under the voulume icon depending which hardware device you choose that recording mic and mic boost will need adjusting to get a suitable compromise.

---

### Post by dondrup on 2009-03-29
hello, i have similar machine - eMachines are made by acer i believe:
 description: Portable Computer
    product: eMachines D620
    vendor: eMachines
    version: 0100
with a similar problem but no crashing in skype or sound recorder. just lack of input. skype even recognizes input, however nothing is recorded in test call. front mic does work. i have opened volume control and selected mic instead of front mic [front mic records even when just mic is selected]. here's my audio specs:
 description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel

i tried putting:

options snd-hda-intel model=eMachines

after the specs as above were shown but the response is:

bash: options: command not found

thanks for the help if you have time.

---

### Post by daury on 2009-03-29
Hi all,

i have the same aforementioned problem with the mic. I got an Acer Aspire 5100 two years ago, sound recording never worked :(
The output of "sudo lshw" is the same as displayed previously by the other guy. I changed the line "options snd-hda-intel ..." (/etc/modprob.d/alsa-base) in "... model=acer", "=acer-aspire", "...model=auto" and i even removed that line (everytime saving and rebooting), but still i cannot record anything (usign both sound record and audacity). Any clue?
I need skype to work...don't want windows becoz of this problem!
thank you a lot!
Daniele

PS i can hear my voice when i speak to the mic, but no recording :(

---

### Post by teaker1s on 2009-03-29
Hi the reason it gets confusing is the recording output settings may not be as expected- if you can hear yourself then it would suggest the sound element is working any the recording element is set to the wrong configuration. 

Secondly hda_intel is a basic starting point, the sound software can only respond to known profiles- different computers that are not in the known profile list may respond to another manufacturers profile if the hardware is the same.

[http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

[http://ubuntuforums.org/showthread.php?t=342681]("http://ubuntuforums.org/showthread.php?t=342681")

---

