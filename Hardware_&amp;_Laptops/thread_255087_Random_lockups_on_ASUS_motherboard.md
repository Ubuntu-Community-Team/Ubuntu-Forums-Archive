---
title: "Random lockups on ASUS motherboard"
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by lpsavoie on 2006-09-10
Hi,

I have been experiencing random lockups in the last few months. I am running Kubuntu Dapper 6.06, although I observed those problems as well when I used Debian testing/unstable. Sometimes, even when the computer is under no particular load, it freezes completely : the mouse and the display lock up, and sound repeats the same second-long segment ad infinitum. The logs show no particular signs of the freezes. It is getting problematic as it seems to damage my partitions, even though they are all journalled (3 ReiserFS partitions and an EXT3) - I recently got an error 16 from GRUB, signaled the root FS was badly corrupted.

AMD Athlon XP 2500+
ASUS a7v8x-x : onboard LAN and sound. VIA KM400 chipset. BIOS 1013 (latest one)
NVidia GeForce 4 MX 440 (using the non-free nvidia driver, I need 3d acceleration)
Creative Labs SoundBlaster Live!
512 MB of RAM (non-ECC, tested extensively with memtest86+)
2 hard drives : 1 Maxtor 6Y080L0 (80 gb, UDMA6, SMART)
1 Fujitsu MPF3204AT (20 gb, UDMA4, SMART)
2 optical drives : 1 TDK VeloCD CDRW401240B
1 Sony CDU4821
A floppy drive

lspci :
> 0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:0e.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

lsmod :
```
Module                  Size  Used by
vmnet                  40676  13
vmmon                 117612  0
binfmt_misc            13192  1
rfcomm                 44244  0
l2cap                  29184  5 rfcomm
bluetooth              54244  4 rfcomm,l2cap
ppdev                  10052  0
cpufreq_powersave       2240  0
cpufreq_stats           6912  0
cpufreq_userspace       6816  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
freq_table              5152  1 cpufreq_stats
tc1100_wmi              7172  0
video                  16644  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
container               4928  0
button                  6992  0
pcc_acpi               12736  0
sony_acpi               5900  0
ac                      5508  1 acpi_sbs
dev_acpi               11652  0
hotkey                 11812  0
ext3                  148296  1
jbd                    65684  1 ext3
nls_cp437               6208  1
ntfs                  114288  1
ipv6                  287456  32
af_packet              25224  2
dm_mod                 63640  1
md_mod                 76244  0
it87                   22436  0
hwmon_vid               3200  1 it87
eeprom                  7824  0
i2c_isa                 5504  1 it87
lp                     12612  0
tsdev                   8320  0
pcspkr                  2564  0
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
analog                 12960  0
psmouse                40132  0
serio_raw               8132  0
floppy                 65924  0
snd_emu10k1_synth       8384  0
snd_emux_synth         40320  1 snd_emu10k1_synth
i2c_viapro              9364  0
via_rhine              25988  0
snd_seq_virmidi         8640  1 snd_emux_synth
snd_seq_midi_emul       8000  1 snd_emux_synth
via_ircc               32660  0
mii                     6528  1 via_rhine
snd_seq_dummy           4164  0
snd_seq_oss            37632  0
snd_seq_midi            9888  0
snd_seq_midi_event      8064  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
irda                  217980  1 via_ircc
emu10k1_gp              4224  0
crc_ccitt               2496  1 irda
via_agp                10560  1
snd_seq                58832  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           133476  4 snd_emu10k1_synth
snd_rawmidi            27552  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         99296  1 snd_emu10k1
snd_ac97_bus            2688  1 snd_ac97_codec
gameport               17032  3 analog,emu10k1_gp
nvidia               4553140  12
agpgart                37072  2 via_agp,nvidia
i2c_core               23168  6 i2c_acpi_ec,it87,eeprom,i2c_isa,i2c_viapro,nvidia
snd_pcm_oss            56352  0
snd_mixer_oss          20800  1 snd_pcm_oss
snd_pcm                96772  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9548  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              27204  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11592  2 snd_emu10k1,snd_pcm
snd_util_mem            5184  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10272  2 snd_emux_synth,snd_emu10k1
snd                    60068  18 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              11040  1 snd
shpchp                 49312  0
pci_hotplug            30916  1 shpchp
evdev                  10432  1
joydev                 10688  0
usbhid                 42912  0
reiserfs              284400  3
ide_generic             1792  0
ehci_hcd               36104  0
uhci_hcd               35472  0
usbcore               138948  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36228  0
cdrom                  41504  1 ide_cd
ide_disk               19520  8
generic                 5444  0
via82cxxx               9988  0 [permanent]
thermal                14088  0
processor              27208  1 thermal
fan                     5124  0
capability              5256  0
commoncap               7616  1 capability
vga16fb                14344  1
vgastate               10304  1 vga16fb
fbcon                  44640  72
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit
```

sensors output :
> it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.65 V  (min =  +1.42 V, max =  +1.57 V)   ALARM
VCore 2:   +0.00 V  (min =  +2.40 V, max =  +2.61 V)   ALARM
+3.3V:     +6.69 V  (min =  +3.14 V, max =  +3.46 V)   ALARM
+5V:       +4.92 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.48 V  (min = +11.39 V, max = +12.61 V)
-12V:     -27.36 V  (min = -12.63 V, max = -11.41 V)   ALARM
-5V:      -13.64 V  (min =  -5.26 V, max =  -4.77 V)   ALARM
Stdby:     +5.08 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +4.08 V
fan1:     3183 RPM  (min =    0 RPM, div = 2)
M/B Temp:    +55°C  (low  =   +15°C, high =   +40°C)   sensor = thermistor
CPU Temp:    +40°C  (low  =   +15°C, high =   +45°C)   sensor = thermistor


lshw :
```

minastirith
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: A7V8X-X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS A7V8X-X ACPI BIOS Revision 1013 (09/02/2004)
          size: 64KB
          capacity: 192KB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp
     *-cpu
          description: CPU
          product: AMD Athlon(TM) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: SOCKET A
          size: 1833MHz
          capacity: 2250MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 512KB
             capacity: 8MB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 512MB
          capacity: 3GB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DDR 1
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DDR 2
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DDR 3
     *-pci
          description: Host bridge
          product: VT8377 [KT400/KT600 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: f8000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 440 AGP 8x]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a2
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:ee000000-eeffffff iomemory:f0000000-f7ffffff irq:177
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: e
             bus info: pci@00:0e.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=EMU10K1_Audigy
             resources: ioport:d800-d81f irq:185
        *-input
             description: Input device controller
             product: SB Live! MIDI/Game Port
             vendor: Creative Labs
             physical id: e.1
             bus info: pci@00:0e.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Emu10k1_gameport
             resources: ioport:d400-d407
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d000-d01f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-k7 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Human interface device
                   product: Twin USB Joystick
                   vendor: Personal Communication Systems, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.06
                   capabilities: usb-1.00
                   configuration: driver=usbhid maxpower=500mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b800-b81f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-k7 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:b400-b41f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-k7 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ed800000-ed8000ff irq:169
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-k7 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:b000-b00f irq:255
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: Maxtor 6Y080L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: YAR41BW0
                   serial: Y2MGR7PE
                   size: 76GB
                   capacity: 76GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma6 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 19GB
                      capabilities: primary
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 46GB
                      capabilities: extended partitioned partitioned:extended
                 *-volume:2
                      description: HPFS/NTFS partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 10024MB
                      capabilities: primary bootable
              *-disk:1
                   description: ATA Disk
                   product: FUJITSU MPF3204AT
                   vendor: Fujitsu
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: 0028
                   serial: 05041042
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.1,1
                      logical name: /dev/hdb1
                      capacity: 19GB
                      capabilities: primary
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: CD-R/CD-RW writer
                   product: TDK CDRW401240B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: Z7SB
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
              *-cdrom:1
                   description: IDE CD-ROM
                   product: SONY CD-ROM CDU4821
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: S0.P
                   serial: MT1198-B Firmware
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:0c:6e:23:b5:2b
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=192.168.0.100 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:a800-a8ff iomemory:ed000000-ed0000ff irq:193
```

---

### Post by dickohead on 2006-09-10
I've had similar issues using Linux distributions before, after a clean install the partitions get errors and defects in them for no apparent reason. the best thing to do is get hold of another hard drive, remove your current one and test with that. If the problems come back... it's not the HDD!

---

### Post by flibble on 2006-09-10
heya :)

helpful of you to post the info re your computer and what you've tried before :)

It might be the harddrive, can't rule anything out at this stage, but I don't think a dodgy drive would lock up the kernel or get you into a loop with the soundcard.

One thing I notice is that the temperature from the sensors output seems quite high (m/b = 55C, cpu = 40C). Was the machine under unusual load when you pasted those numbers? If the box was mainly idle then perhaps the cpu or the northbridge or some other controller, even ram, is overheating and crashing the machine once it gets under load.

Another thought: have you tried running from a livecd for a while? That ought to rule out the possibility it's the harddrive, since the livecd will run without accessing the drives (unless you tell it to...). You could boot from the livecd then do: ```
sudo mount -a
``` so that no harddrive partition is mounted.

---

### Post by lpsavoie on 2006-09-11
> **flibble said:**
> heya :)

helpful of you to post the info re your computer and what you've tried before :)

It might be the harddrive, can't rule anything out at this stage, but I don't think a dodgy drive would lock up the kernel or get you into a loop with the soundcard.

One thing I notice is that the temperature from the sensors output seems quite high (m/b = 55C, cpu = 40C). Was the machine under unusual load when you pasted those numbers? If the box was mainly idle then perhaps the cpu or the northbridge or some other controller, even ram, is overheating and crashing the machine once it gets under load.

Another thought: have you tried running from a livecd for a while? That ought to rule out the possibility it's the harddrive, since the livecd will run without accessing the drives (unless you tell it to...). You could boot from the livecd then do: ```
sudo mount -a
``` so that no harddrive partition is mounted.
Well, maybe it's a heat problem, but it would be weird since I have two fans (the PSU fan and another one - the case is quite cheap though)

---

### Post by Dogmeat on 2006-09-12
Interesting. I also have an ASUS board (A8V-Deluxe 2) and that happened to me these days. I'm running Dapper Xubuntu amd64.
This happened frequently when I was listening to a radio on Firefox through mplayer-plug-in after I installed a flash wrapper. It would lock up every hour or so after turning the radio on.

Another thing I remember is I was back from a suspend with the NVIDIA drivers.

Were you by chance doing any of those things?

For some odd reason, suspend to ram sometimes works for me, sometimes it doesn't, when it doesn't it will sometimes lock up at the bios screen and I have to power cycle (i mean physically removing the power cord and reattaching it)

But back to topic..

Then again, my hard drive is dying. I moved the partition away from the problem areas recently. These lockups are probably because of the drive, I just wanted to rule out the other things to make sure it's the drive.

Maybe your drive is dying too.
To check the health of your drive, get smartmontools from synaptic too and run sudo smartctl --all /dev/hda

Some things to try:
Booting from the live cd and do a forced fsck on all your partitions. Then boot from it again, and reinstall linux-image-2.6.15 from synaptic and other kernel packages (except headers and source). Or try installing an alternative kernel.

After I did this the lockups mostly gone. Except for once, when I was listening to web radio for about an hour it froze again :(

I stopped listening to it for a few days and no freezes. I'm listening now to see if it's related and will crash the system again.

---

### Post by djSeverin on 2006-09-13
My advice for any complete system lock fault is to start with the Memory Test found in the GRUB boot menu. 

When the machine first boots up, press ESC and you'll get a menu with your current kernel, old kernels and the memory test.

If it dies doing the memory test, suspect the power supply...

---

### Post by Dogmeat on 2006-09-13
You may be right, I measured the 3.3v line with a voltmeter. In the mobo connector it said 3.14v, and in the auxiliary connector 3.17v, is that low enough that it would cause random lockups and reboots? 
By the way the ram works at 2.7v. This is probably a stupid question, but can that lower voltage be causing an overall 3.3v drop?

Today I got a few more lockups, this time I could move the mouse, and the radio station kept playing in the background, but the system wasn't responding to keyboard and mouse buttons. 

In this case which one do you think is more likely the culprit: a bad hard drive or the low psu voltage?

By the way yesterday I got another random reboot in another operating system. I guess i'll leave memtest running for a few hours, if I don't get a reboot I can safely assume it's not the hard drive causing the reboots.

---

### Post by Dogmeat on 2006-09-13
I have some interesting results. Memtest ran for 5 straight hours with no problems. Then I rebooted, and 5 minutes later I had a frozen system. I got several random lockups/reboots after this. One of these times even X logged me off, saying there was a problem with the file SecurityPolicy (this MUST be hard drive related! or so I thought...)

I decided to go to a live cd to rule out the hard drive once and for all. It takes a while
 to boot so I went to make some food. When I come back, the system appeared to be up and running on the default ubuntu desktop. Surprise surprise, the system was frozen. From the live cd.

A simple question: can a dying hard drive simply freeze the whole system, even if running from a live cd? Should I try the live cd with the hard drive physically disconnected from the board? I'm stumped.

---

### Post by lpsavoie on 2006-09-13
Well, you could try it. I haven't been using supsend myself, although I listen to music a lot on my computer. I'm using older PCI cards to offload some work off the motherboard (it has an integrated sound card and Ethernet, like every mobo nowadays). It hasn't crashed yet, but then again, it gave me another error 16 ... even though it hadn't frozen recently (since the last time it did it). So I force-fscked all my partitions ... again. I'll try smartmontools though, thanks for the tip !

---

### Post by lpsavoie on 2006-09-13
Oh yeah, here's the output of smartcl --all /dev/hda ... it's pretty hard to understand :|

```
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax Plus 9 family
Device Model:     Maxtor 6Y080L0
Serial Number:    Y2MGR7PE
Firmware Version: YAR41BW0
User Capacity:    81ý64ý02ý36 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Wed Sep 13 23:47:57 2006 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 241) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  37) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   224   224   063    Pre-fail  Always       -       10874
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       1041
  5 Reallocated_Sector_Ct   0x0033   253   253   063    Pre-fail  Always       -       0
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   249   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   250   241   187    Pre-fail  Always       -       61496
  9 Power_On_Minutes        0x0032   235   235   000    Old_age   Always       -       927h+58m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   249   249   000    Old_age   Always       -       1584
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       40
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       14096
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   240   000    Old_age   Always       -       177
202 TA_Increase_Count       0x000a   253   210   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       13
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   191   191   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
Warning: ATA error count 103 inconsistent with error log pointer 5

ATA Error Count: 103 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 103 occurred at disk power-on lifetime: 1383 hours (57 days + 15 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7f 52 03 e0  Error: UNC 8 sectors at LBA = 0x0003527f = 217727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 7f 52 03 e0 08      21:44:09.168  READ DMA
  c8 00 08 7f 52 03 e0 08      21:44:08.128  READ DMA
  c8 00 08 7f 52 03 e0 08      21:44:07.088  READ DMA
  ca 00 08 8f 15 40 e2 08      21:44:07.056  WRITE DMA
  ca 00 08 bf 09 18 e0 08      21:44:07.056  WRITE DMA

Error 102 occurred at disk power-on lifetime: 1383 hours (57 days + 15 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7f 52 03 e0  Error: UNC 8 sectors at LBA = 0x0003527f = 217727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 7f 52 03 e0 08      21:44:08.128  READ DMA
  c8 00 08 7f 52 03 e0 08      21:44:07.088  READ DMA
  ca 00 08 8f 15 40 e2 08      21:44:07.056  WRITE DMA
  ca 00 08 bf 09 18 e0 08      21:44:07.056  WRITE DMA
  ca 00 08 3f 00 04 e0 08      21:44:07.056  WRITE DMA

Error 101 occurred at disk power-on lifetime: 1383 hours (57 days + 15 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7f 52 03 e0  Error: UNC 8 sectors at LBA = 0x0003527f = 217727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 7f 52 03 e0 08      21:44:07.088  READ DMA
  ca 00 08 8f 15 40 e2 08      21:44:07.056  WRITE DMA
  ca 00 08 bf 09 18 e0 08      21:44:07.056  WRITE DMA
  ca 00 08 3f 00 04 e0 08      21:44:07.056  WRITE DMA
  ca 00 08 bf 00 00 e0 08      21:44:07.056  WRITE DMA

Error 100 occurred at disk power-on lifetime: 1383 hours (57 days + 15 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7f 52 03 e0  Error: UNC 8 sectors at LBA = 0x0003527f = 217727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 7f 52 03 e0 08      21:44:06.032  READ DMA
  ca 00 40 df 88 00 e0 08      21:44:06.016  WRITE DMA
  ca 00 10 6f 4d 05 e0 08      21:44:06.016  WRITE DMA
  ca 00 08 7f f5 04 e0 08      21:44:06.016  WRITE DMA
  ca 00 08 1f 70 15 e0 08      21:44:06.016  WRITE DMA

Error 99 occurred at disk power-on lifetime: 1383 hours (57 days + 15 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7f 52 03 e0  Error: UNC 8 sectors at LBA = 0x0003527f = 217727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 7f 52 03 e0 08      21:44:04.976  READ DMA
  c8 00 08 7f 52 03 e0 08      21:44:03.920  READ DMA
  c8 00 08 7f 52 03 e0 08      21:44:02.880  READ DMA
  ca 00 08 6f 41 40 e2 08      21:44:02.864  WRITE DMA
  ca 00 08 df 03 14 e2 08      21:44:02.864  WRITE DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      2777         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by DFreeze on 2006-09-27
I just stumbled on this thread while searching for the exact same symptoms. Unfortunately I can't give you a solution, since I'm looking for one myself. My system also locks up often. Sometimes I have one hour of uptime, sometimes, the bootup doesn't even finish and even worse, sometimes I don't even get visuals when powering up (although, always when rebooting, never on a cold boot).

I've checked my memory (memtest86, one module at a time, swapping modules, anything I could think of), replaced my CPU fan and PSU, added an extra case fan to rule out the temperature possibility completely but nothing seems to help.

Just yesterday I flashed my BIOS to the most recent version, but I got a hardlock still. Mostly the lockups occur when in GNOME, but after the first freeze, often I can't get it back in full GNOME again before it freezes on me. 

I pulled out and reinserted the nVidia 440MX and the memory modules more times than I can remember, but that doesn't fix the problem. Only when the screen stays blank after a lockup, I can fiddle the nVidia or the memory a little to get my visuals back.

Anyway, a lot of similarities. I suspect the MoBo first of all. I've checked it for leaking capacitors, but none to be seen. Maybe a tiny crack in one of the signalling paths or something. Or broken soldering in the AGP or DDR slots. If you find anything, please don't forget to post back here. I'll do the same!

AMD 2100+
Soltek SL75-DRV5 ("rev. T1.8")
nVidia 440MX
3x256 MB DDR (noname-ish)
Soundblaster Live!
3COM 10/100 ethernet
Conceptronics FireWire PCI-card
ASUS PSU (450W)

---

### Post by DFreeze on 2006-09-29
Update: it's definately a broken signal path or soldering. Bending my MoBo forward and holding it there (piece of paper) results in a stable computer for two days now (whereas two hours was exceptionally long, before).

Don't know if this is of any help to you, but at least in my case I know what to do: buy a new MoBo, and do it real soon ;)

---

### Post by mgmiller on 2006-10-02
One possibility is microscopic oxidation/corrosion on the connectors for your RAM, video card, etc. (even if they are gold plated!) Go to a local Radio Shack and get their deoxit progold kit.  Radio Shack part No. 640-4338.  Use it to clean & treat all the contacts and sockets for memory and video card, etc.  See if that doesn't do the trick.  I have a Dell notebook that drove me crazy with lockups and weird behavior until I did this trick on the keyboard plug inside the case.  I have also fixed problems on desktop units by doing the RAM and RAM sockets with this kit.  Good luck.

---

