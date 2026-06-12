---
title: "RTL8188CE y Ubuntu 11.10 no se llevan bien ¿o sí? ¿cómo hago?"
date: 2011-11-27
forum: Hardware
---

### Post by LisaSimpson on 2011-11-27
No puedo configurar el wifi de la notebook... hice todo lo que dicen en todos los foros y no me da resultado, les paso la info de la compu a ver si pueden ayudarme por favor:

sudo lspci

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
07:00.0 [COLOR="Blue"]Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)[/COLOR]
0d:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 5986:0182 Acer, Inc 
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120

sudo lshw
patryhec-twh              
    description: Notebook
    product: TWH (HuronRiver_CRB)
    vendor: Quanta
    version: TBD
    serial: 123456789
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook family=Intel_Mobile sku=HuronRiver_CRB uuid=88888888-8887-8888-8888-878888888888
  *-core
       description: Motherboard
       product: TWH
       vendor: Quanta
       physical id: 0
       version: TBD
       serial: QTFB6BX1230110
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: QR151
          date: 02/01/2011
          size: 1MiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: H6428U61F9333G
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
             product: BKH200SO25608-1333
             physical id: 2
             serial: 07000000
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
          vendor: Intel Corp.
          physical id: 29
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
          slot: CPU1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2b
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 2c
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 2d
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
     *-cache
          description: L1 cache
          physical id: 2a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:c4404000-c440400f
        *-usb:0
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c440a000-c440a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:42 memory:c4400000-c4403fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:c3400000-c43fffff ioport:c0400000(size=16777216)
           *-network DISABLED
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: 68:a3:c4:e4:53:c9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-13-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 ioport:2000(size=256) memory:c3400000-c3403fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:c2400000-c33fffff ioport:c1400000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8151 v2.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:0d:00.0
                logical name: eth0
                version: c0
                serial: e8:9a:8f:41:f9:aa
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=10.0.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:43 memory:c2400000-c243ffff ioport:1000(size=128)
        *-usb:1
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:c4409000-c44093ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:40 ioport:3098(size=8) ioport:30bc(size=4) ioport:3090(size=8) ioport:30b8(size=4) ioport:3060(size=32) memory:c4408000-c44087ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HN-M500M
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2AR1
                serial: S2R7J9AB510860
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003a208
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 770c4a90-8479-47e6-9674-db87c32501fe
                   size: 462GiB
                   capacity: 462GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-11-21 20:03:15 filesystem=ext4 lastmountpoint=/ modified=2011-11-21 20:41:39 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-11-27 00:57:24 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3018MiB
                   capacity: 3018MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3018MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW DVRTD10RS
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c4406000-c44060ff ioport:3040(size=32)
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: Battery 0
       slot: Fake

sudo lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  4 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
arc4                   12529  2 
rtl8192ce             141566  0 
rtlwifi               117772  1 rtl8192ce
mac80211              448163  2 rtl8192ce,rtlwifi
cfg80211              198044  2 rtlwifi,mac80211
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
mxm_wmi                12979  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 47198  0 
hid                    95463  1 usbhid
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
serio_raw              13166  0 
i915                  566711  3 
wmi                    19256  1 mxm_wmi
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci


Yo bajé el controlador desde la página de Realtek y para mi kernel 3.0.0_13-generic me dice que es este: 92ce_se_de_linux_mac80211_0004.0816.2011.tar.gz

¿será que debo bajar otro controlador?, no sé dónde encontrar otro...
¿Alguien podría ayudarme por favor?

Patricia Sartor (alias LisaSimpson)
de San Lorenzo, Santa Fe
no tengo muchos ubuntureros cerca...

---

### Post by guillermolisi on 2011-11-27
Leyendo sobre el tema vi que, ademas del tarball con el driver de Realtek, hay que instalar el paquete build-essential para que la compilacion de los fuentes del driver funcione sin problemas.

Tambien encontre [informacion de Debian]("http://wiki.debian.org/rtl819x#Wheezy") donde mencionan instalar firmware privativo de Realtek (pagina en Ingles).

Por lo que veo en la salida de tu "lspci" hay una cuestion de firmware pendiente de resolucion ya que figura como N/A (Not Available) que significa No Disponible.

Hay varios casos de exito en UbuntuForums que han logrado hacer funcionar esta placa en distintas maquinas, tanto con 11.04 como con 11.10.

---

### Post by LisaSimpson on 2011-11-27
ya las probé todas, incluida la que recomienda la propia realtek y no sé si hago algo mal...
intentaré por n-ésima vez, ¿será que el driver que yo bajé no es para la v.1?, por allí vi que alguien, con otro wifi tuvo ese problema, se había bajado algo para una v.2 y necesitaba la v.1 ¿cómo puedo saberlo en el caso del driver que bajé?

---

### Post by guillermolisi on 2011-11-28
> *-network DISABLED
description: Wireless interface
product: RTL8188CE 802.11b/g/n WiFi Adapter
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:07:00.0
logical name: wlan0
[COLOR="DarkRed"]version: 01[/COLOR]
serial: 68:a3:c4:e4:53:c9
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-13-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:16 ioport:2000(size=256) memory:c3400000-c3403fff

Si esa no es la version interna del driver de Realtek, o de la placa, entonces sugiero buscar dentro del tarball ya que suele haber uno o dos archivos con info tecnica del software empaquetado.

Por otro lado, esta encendida la antena de la maquina ?

---

### Post by LisaSimpson on 2011-11-28
me fijaré en el tarball, que no sé qué es pero me imagino que es el archivo que bajé ¿es así?

y sí, está encendida la antena, se enciende con fn-f2 y no importa si la enciendo o la apago, no la toma de ninguna manera :(

---

### Post by guillermolisi on 2011-11-28
> **LisaSimpson said:**
> me fijaré en el tarball, que no sé qué es pero me imagino que es el archivo que bajé ¿es así?

y sí, está encendida la antena, se enciende con fn-f2 y no importa si la enciendo o la apago, no la toma de ninguna manera :(

Los archivos "tar" o "tar.xx" donde xx indica el algoritmo de compresion aplicado, se llaman en la jerga "tarballs".

---

### Post by LisaSimpson on 2011-11-28
El tarball tiene un archivo Kconfig que dice:

----------------------------------------------------
config RTL8192CE
	tristate "Realtek RTL8192CE/RTL8188CE Wireless Network Adapter"
	depends on MAC80211 && PCI && EXPERIMENTAL
	select FW_LOADER
	select RTLWIFI
	---help---
	This is the driver for Realtek RTL8192CE/RTL8188CE 802.11n PCIe
	wireless network adapters.

	If you choose to build it as a module, it will be called rtl8192ce

config RTL8192DE
        tristate "Realtek RTL8192DE Wireless Network Adapter"
        depends on MAC80211 && PCI && EXPERIMENTAL
        select FW_LOADER
        select RTLWIFI
        ---help---
        This is the driver for Realtek RTL8192DE 802.11n PCIe
        wireless network adapters.

        If you choose to build it as a module, it will be called rtl8192de

config RTL8192SE
        tristate "Realtek RTL8192SE Wireless Network Adapter"
        depends on MAC80211 && PCI && EXPERIMENTAL
        select FW_LOADER
        select RTLWIFI
        ---help---
        This is the driver for Realtek RTL8192SE 802.11n PCIe
        wireless network adapters.

        If you choose to build it as a module, it will be called rtl8192se

config RTLWIFI
	tristate
	depends on RTL8192CE || RTL8192DE || RTL8192SE
	default m
-----------------------------------------------------
¿sirve esto de algo? porque no sé qué hacer con esta info :confused:

---

### Post by LisaSimpson on 2011-11-28
y tiene un Readme que dice esto:
-------------------
Release Date: 2011-03-29, ver 0003
Realtek Linux mac80211 based driver:
   --This driver supports follwing RealTek PCIE Wireless LAN NICs:
	RTL8188CE/RTL8192CE
	RTL8191SE/RTL8192SE
	RTL8192DE

   --This driver supports follwing Linux OS:
 	Fedora Core
	Debian
	Mandriva
	Open SUSE
	Gentoo
	MeeGo
	android 2.2 (froyo-x86), etc.

   --This driver supports follwing kernel versions:
	1) kernel version >=2.6.35
	   you can build & install drvier use II. 


	2) kernel version [2.6.24, 2.6.34]
	   you can build & install drvier use III. 


========================================================================================
		I. Component 
========================================================================================
The driver is composed of several parts:
	1. Firmare to make nic work
           1.1 firmare/rtlwifi

	2. Module source code
	   2.1 ./*
	   2.2 rtl8192ce
	   2.2 rtl8192se
	   2.2 rtl8192de
	
	3. Script to build the modules
	   3.1 Makefile 

	4. compat-wireless
	   4.1 compat-wireless*.tar.bz2
	   4.2 compat

========================================================================================
		II. Compile & Installation & uninstall
========================================================================================
You can enter top-level directory of driver and execute follwing command to
Compile, Installation, or uninstall the driver:

	1. Change to Super User
	   sudo su

	2. Compile driver from the source code 
	   make

	3. Install the driver to the kernel
	   make install
	   reboot

	4. uninstall driver
	   make uninstall

========================================================================================
		III. Compile & Installation & uninstall [2.6.24, 2.6.34]
========================================================================================
We don't support kernel 2.6.24-2.6.34 directly, Because there are
lots of issues in mac80211 from kernel 2.6.24-2.6.34,
So we suggest you to use the latest kernel >= 2.6.35.

but if you want to use our driver in an old kernel,
you can use compat-wireless. this methord can support all kernel
versions higher than 2.6.24, and you can use all functions
of our driver like you use it in the latest kernel version.

You can get more informations of compat-wireless from:
[http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)

you should use the following commands to Compile, Installation, or uninstall the driver:

	1. Change to Super User
	   sudo su

	2. install compat-wireless driver
	   ./compat/script/compat-install.sh
		 
	3. reboot
	   reboot

	4. uninstall driver
	   ./compat/script/compat-uninstall.sh

	5. you can get more information form follwing webset for how to use compat-wireless:
	   [http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)
	   
NOTICE:
	1. Maybe you can not use other vendors wireless after you install compat wireless,
	   in this situation, you can uninstall compat-wireless use step 4 to recover it.

	2. This install methord can support all versions of kernel, not just 2.6.24-2.6.34,
	   you can also use it in the kernel higher than 2.6.35.
========================================================================================
				IV. Start Up Wireless
========================================================================================
You can use two methord to start up wireless:

	1. Install driver like II. and reboot OS, Wireless will be brought 
	   up by GUI, such as NetworkManager

	2. If Wireless is not brought up by GUI, you can use: 
	   ifconfig wlan0 up 

	   Note: some times when you have two wireless NICs on your computer,
		 interface "wlan0" may be changed to "wlan1" or "wlan2", etc. 
		 So before "ifconfig wlan0 up", you can use "iwconfig" to check
		 which interface our NIC is.

	   Note: Don't try to down driver by "ifconfig wlan0 down" when 
		 NetworkManager id opened, because NetworkManager will up
		 driver automatically. 

========================================================================================
				V. Wireless UI & NetworkManager 
========================================================================================
	1. All latest distributions have UI & NetworkManager to like with AP.
	   And it's more easy to link with AP than commandline,
	   So we suggest you use UI to link with AP.

	2. Don't try to like with AP use commandline with UI or NetworkManager opened.

	3. If you still used commandline to link with AP, Please check if
	   NetworkManager & wpa_supplicant is killed by follwing command:

		ps -x | grep NetworkManager
		ps -x | grep wpa_supplicant

	4. Follwing commandlines(V-VII) are all used under Linux without UI. 

========================================================================================
				VI. Set wireless lan MIBs  
========================================================================================
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

	1. Current driver supports "iwlist" to show the device status of nic

	   iwlist wlan0 [parameters]

	   you can use follwing parameters:

        	parameter explaination      	[parameters]    
       		-----------------------     	-------------   
        	Show available chan and freq	freq / channel  
        	Show and Scan BSS and IBSS 	scan[ning]          
        	Show supported bit-rate         rate / bit[rate]        

	   For example:
		iwlist wlan0 channel
		iwlist wlan0 scan
		iwlist wlan0 rate

	2. Driver also supports "iwconfig", manipulate driver private ioctls, 
	   to set MIBs.

	   iwconfig wlan0 [parameters] [val]

	   you can use follwing parameters:

	   parameter explaination      [parameters]        [val] constraints
        	-----------------------     -------------        ------------------
        	Connect to AP by address    ap              	[mac_addr]
        	Set the essid, join (I)BSS  essid             	[essid]
        	Set operation mode          mode                {Managed|Ad-hoc}
        	Set keys and security mode  key/enc[ryption]    {N|open|restricted|off}

	   For example:
		iwconfig wlan0 ap XX:XX:XX:XX:XX:XX
		iwconfig wlan0 essid "ap_name"
		iwconfig wlan0 mode Ad-hoc
		iwconfig wlan0 essid "name" mode Ad-hoc
		iwconfig wlan0 key 0123456789 [2] open
		iwconfig wlan0 key off
		iwconfig wlan0 key restricted [3] 0123456789
        	iwconfig wlan0 key s:12345

	   Note: There are two types of key, "hex" code or "ascii" code. "hex" code
	        only contains hexadecimal characters, "ascii" code is consist of 
                "ascii" characters. Assume the "hex" code key is "0123456789", you 
                are suggested to use command like this "iwconfig wlan0 key 0123456789". 
                Assume the "ascii" code key is "12345", you should enter command 
                like this "iwconfig wlan0 key s:12345".

           Note: Better to set these MIBS without GUI such as NetworkManager and be 
	        sure that our nic has been brought up before these settings. WEP key
	        index 2-4 is not supportted by NetworkManager.

========================================================================================
				VII. Getting IP address (For OS without UI) 
========================================================================================
Before transmit/receive data, you should obtain an IP address use one of
the follwing method: 

	1. static IP address:

		ifconfig wlan0 IP_ADDRESS

	2. dynamic IP address using DHCP:
	   	
		dhclient wlan0
		

========================================================================================
				VIII. WPAPSK/WPA2PSK (For OS without UI) 
========================================================================================
Wpa_supplicant helps you to link with WPA/WPA2(include WPA Enterprise) AP, 
in Linux with NetworkManger & UI, UI will help you to link with AP, 
But if there is no UI & Networkmanger in your Linux, you can use 
follwing method to link with WPA/WPA2 AP. 
	
	1. we suppose that your Linux have installed wpa_supplicant & 
	   kernel build with WIRELESS_EXT, In fact, lots of distributions
	   have done like this.

	   But if some distribution not install wpa_supplicant,
	   please download wpa_supplicant from webset and install it.

	2. Edit wpa1.conf to set up SSID and its passphrase.
	   For example, the following setting in "wpa1.conf" 
	   means SSID to join is "BufAG54_Ch6" and its 
	   passphrase is "87654321".

	   network={
			ssid="BufAG54_Ch6"
			#scan_ssid=1 //see note 3
			proto=WPA
			key_mgmt=WPA-PSK
			pairwise=CCMP TKIP
			group=CCMP TKIP WEP104 WEP40
			psk="87654321"
			priority=2
		  }

	   You can download wpa_supplicant and read wpa_supplicant.conf 
	   for more examples.

	3. Execute WPA supplicant:

	   wpa_supplicant -D wext -c wpa1.conf -i wlan0 

	4. To see detailed description for driver interface and wpa_supplicant, 
	   please type: 

	   man wpa_supplicant
----------------------------------------

---

### Post by LisaSimpson on 2011-11-28
Hice lo que dice en el punto II:
[COLOR="Blue"]1. Change to Super User
sudo su

2. Compile driver from the source code 
make

3. Install the driver to the kernel
make install
reboot[/COLOR]

menos esto porque en muchos foros veo que no desinstalan

4. uninstall driver
make uninstall

y luego, no entiendo más nada...
sólo tengo estos datos, quizás sirvan para algo:

-------------------------
root@patryhec-TWH:/home/patryhec# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

root@patryhec-TWH:/home/patryhec# iwlist wlan0 channel
wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
root@patryhec-TWH:/home/patryhec# iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

root@patryhec-TWH:/home/patryhec# iwlist wlan0 rate
wlan0     unknown bit-rate information.
-----------------------------------

---

### Post by guillermolisi on 2011-11-28
Si tenes Network Manager en el escritorio, fijate si podes activar la antena.

Si no, en una terminal/consola ingresa lo que dice el punto > 2. If Wireless is not brought up by GUI, you can use: 
ifconfig wlan0 up asi levantas (habilitas logicamente) la interfaz inalambrica.

Proba y mostra que te devuelve como resultado de ese comando.

---

### Post by LisaSimpson on 2011-11-28
Usé la terminal, me dio esto:
--------------
root@patryhec-TWH:/home/patryhec# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
--------------
hice fn-f2 por las dudas
y volvió lo mismo...

---

### Post by LisaSimpson on 2011-11-28
si hago: rfkill list wifi 0 me da esto:
-----------------
root@patryhec-TWH:/home/patryhec# rfkill list wifi
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by LisaSimpson on 2011-11-28
Y haciendo esto:
----------------
root@patryhec-TWH:/home/patryhec# rfkill unblock0
Usage:	rfkill [options] command
Options:
	--version	show version (0.4-1 (Ubuntu))
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
root@patryhec-TWH:/home/patryhec# rfkill list wifi
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
-------------
no parece modificar nada...
a ver, reinicio por las dudas

---

### Post by LisaSimpson on 2011-11-28
nada nuevo pasa...

---

### Post by LisaSimpson on 2011-11-28
¿tendré un conflicto con el bluetooth?, ¿cómo saberlo?

---

### Post by LisaSimpson on 2011-11-28
oh oh...

----------
patryhec@patryhec-TWH:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
patryhec@patryhec-TWH:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Permiso denegado
patryhec@patryhec-TWH:~$ sudo su
root@patryhec-TWH:/home/patryhec# if config wlan0 up
---------------
y se queda ahí sin más...

---

### Post by LisaSimpson on 2011-11-28
esto tampoco funciona:

[http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

----------------------------
sudo apt-get install build-essential linux-headers-`uname -r`
cd /usr/src
sudo tar xzvf /home/patryhec/92ce_se_de_linux_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011
sudo cp -rf firmware/rtlwifi /lib/firmware
sudo make
sudo cp rtl8192ce/rtl8192ce.ko /lib/modules/`uname -r`/kernel/drivers/net/
sudo depmod -a

rebootear
--------------------------

vuelve a darme:

root@patryhec-TWH:/home/patryhec# rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
root@patryhec-TWH:/home/patryhec# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
:confused:

---

### Post by LisaSimpson on 2011-11-28
usar ndiswrapper es muy loco????
tengo esta guía:
[http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper](http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper)

bajaré los drivers para windows desde aquí:

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2721](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2721)

(los de linux están aquí:
[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722) )

y ahora probaré

---

### Post by LisaSimpson on 2011-11-28
ndiswrapper tampoco anda

---------------
root@patryhec-TWH:/home/patryhec# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
          Encryption key: off
          Power Management: on

---

### Post by guillermolisi on 2011-11-29
O esta apagada y por alguna razon fisica no se enciende o directamente no funciona, a lo cual va la pregunta del millon: En otro sistema operativo, funciona la conexion inalambrica de esa maquina ?

---

### Post by LisaSimpson on 2011-11-29
en el windows 7 hp que traía funcionaba, ahora no...
leí que podía ser una incompatibilidad con el bluetooth ¿puede ser así?
le di mil vueltas a la máquina intentando encontrar un botón físico que esté movido y que no me da señal de wifi pero no encuentro nada de nada...
esta experiencia, como tantas otras sirve para aprender muchas cosas pero ¿es que no encontraré la solución?
con el broadcom de la netbook hace dos años me pasó algo parecido pero esperé y el propio ubuntu me ofreció controladores, pero no sé qué le pasa a esta compu y los que me la vendieron de ubuntu no saben nada de nada :(

---

### Post by guillermolisi on 2011-11-29
Para mi va mas alla de que sea Ubuntu o Windows. Para mi es problema de hardware y hasta que no tengas la certeza de que esa placa funciona, podes intentar lo que quieras pero sin exito.

Es lo primero que intentaria verificar antes de seguir haciendo pruebas con Linux (Ubuntu o el que sea).

Por que ahora con Windows original de la maquina no funciona mas ?

Lo de la incompatibilidad con Bluetooth no me parece que siga una logica razonable (aunque todo puede ser, hoy por hoy).

---

### Post by LisaSimpson on 2011-11-29
el windows 7 que traía lo borré, no usamos windows en casa, sólo lo probé para ver si todo funcionaba y le instalé el ubuntu ocupando todo el disco, por eso no tengo más windows...
ahora no estoy en casa, esta noche probaré con un disco de arranque de ultimate, una distribución que trae controladores y quizás tenga el de este wifi... hasta esta noche no puedo hacer más pruebas

---

### Post by guillermolisi on 2011-11-29
Ah, o sea que hasta ese momento con Win7 funcionaba bien. Ok. ahora hay que ver porque la maquina mantiene apagada la antena (RFkill).

---

### Post by LisaSimpson on 2011-11-29
voy a "killear" una señal inalámbrica si no logramos hacerla funcionar... no puede ser, me llevó 5 años convencer a mi marido que se pase al linux, se animó a destruir el windows 7 y ahora no puedo conectar el wifi... esto es una vergüenza, por favor, a todos los dioses del ubuntu ¿cómo hago para invocarlos? [-o<

---

### Post by guillermolisi on 2011-11-29
> **LisaSimpson said:**
> Y haciendo esto:
----------------
root@patryhec-TWH:/home/patryhec# rfkill unblock0
Usage:	rfkill [options] command
Options:
	--version	show version (0.4-1 (Ubuntu))
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
root@patryhec-TWH:/home/patryhec# rfkill list wifi
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
-------------
no parece modificar nada...
a ver, reinicio por las dudas
Proba ```
sudo rfkill unblock all
``` en una terminal/consola y conta que paso.

---

### Post by juancarlospaco on 2011-11-29
Hola...
Yo probaria reiniciar, ingresar en la BIOS, 
Deshabilitar la Gestion Avanzada de Energia y 
buscar si tiene para Encender la Wifi desde la BIOS,
guardar esas configuraciones, reiniciar, y probar de nuevo.

:)

---

### Post by LisaSimpson on 2011-11-29
cuando llegue a casa probaré y les cuento qué pasa... pero desde ya les digo que el rfkill unblock all ya lo hice ayer y no pasó nada...
probaré lo que sugiere Juan Carlos, mmm... no veo la hora de llegar para ver si eso anda... esto es una novela, vea el próximo capítulo y se enterará cómo prosigue... en unas horitas nomás, hasta prontoooooooo):P)

---

### Post by guillermolisi on 2011-11-29
> **LisaSimpson said:**
> ... pero desde ya les digo que el rfkill unblock all ya lo hice ayer y no pasó nada...


Estas escondiendo informacion y eso desorienta a quienes te ayudan :)

Lo hiciste como superusuario o como usuario normal (con sudo o sin sudo) ?

Despues de ese comando hay que ingresar "ifconfig -a" para ver que resultado dio.

---

### Post by LisaSimpson on 2011-11-29
Comento lo realizado:
- Probé con Ultimate 2.8 que es Ubuntu 10.10 más controladores, una distribución que suelen usar quienes quieren probar Ubuntu con más programas que los mínimos que traen los live cd de Ubuntu.
RESULTADO: nada, el Ultimate 2.8 ni siquiera me detectó la red ethernet, o sea, no tiene cargados los controladores para el hardware de esta compu...

- Volví a instalar el controlador que había bajado para que se anule lo realizado con el controlador de windows

- Fui al Bios, el wifi está "enabled", también el bluetooth, desabilité este último para ver si era un conflicto entre ambos, encendí y no, entré al Bios y volví a habilitar el bluetooth.

- Entrando como root (como se advierte en lo que copio), ejecuté:

root@patryhec-TWH:/home/patryhec# rfkill list wifi
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

root@patryhec-TWH:/home/patryhec# rfkill unblock all
root@patryhec-TWH:/home/patryhec# ifconfig -a
eth0      Link encap:Ethernet  direcciónHW e8:9a:8f:41:f9:aa  
          Direc. inet:10.0.0.3  Difus.:10.0.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::ea9a:8fff:fe41:f9aa/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:11269 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:10898 errores:0 perdidos:0 overruns:0 carrier:1
          colisiones:0 long.colaTX:1000 
          Bytes RX:9072306 (9.0 MB)  TX bytes:1526319 (1.5 MB)
          Interrupción:42 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:46 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:46 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:7525 (7.5 KB)  TX bytes:7525 (7.5 KB)

wlan0     Link encap:Ethernet  direcciónHW 68:a3:c4:e4:53:c9  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

------------
CONCLUSIÓN: Todo está como era entonces...:-k  
Sólo me queda esperar el milagro de que los que más saben de Ubuntu desarrollen algo que me sirva para instalar como instalé el controlador del wifi de la netbook que también es propietario pero que cuando pude hacerlo desde controladores propietarios (dentro del sistema) no tuve más problemas... Señores ubuntureros experimentados, por favor [-o<  jijijijijiji

---

### Post by LisaSimpson on 2011-11-29
Los datos de la notebook son:
EUROCASE Sandy Bridge
Intel I3 2310 (2,1 GHz)
3GB DDR3
15,6"
DVD+RW/Webcam/WiFi/HDMI/3USB/Lector de Tarjetas/Bluetooth

Mientras podemos conectar el wifi de la notebook, ¿qué antenita wifi usb me conviene comprar que sirva para ubuntu?

---

### Post by LisaSimpson on 2011-11-29
Otra opción es que pueda conseguir los parámetros y configure manualmente el wifi en editar conexiones / inalámbrica / añadir
¿podrá funcionar eso?
Cuando consulto en Sistema / Controladores de redes inalámbricas me dice:
Controladores de Windows actualmente instalados: net8192ce
Hardware presente: sí
y me ofrece instalar controlador nuevo o eliminar controlador, configurar red o sea, hacerlo en forma manual... 
Eso es lo que me llevó a pensar en esa posibilidad.

Es mi tarea para mañana, hasta lueguitoooooooooo :KS

---

### Post by guillermolisi on 2011-11-30
Repeti el ```
sudo rfkill list wifi
``` despues de haber emitido el ```
sudo rfkill unblock all
``` porque lo ultimo que surge del "ifconfig -a" es que wlan0 esta siendo reconocida, solo que habria que activarla con ```
sudo ifconfig wlan0 up
```
La unica duda que tengo ahora es si esta situacion se da porque esta con ndiswrapper o con el driver nativo de Realtek para Linux.

Otra cosa que se me ocurrio es que hay algunos BIOS, como en el caso de uno que viene con las Dell Inspiron 1521, que habilitan alternativamente una interface de red u otra. Es decir, si detectan que la red cableada esta conectada no habilitan la wifi. Asi que por las dudas, probaria la inalambrica con el cable de red desconectado, si es que aun no hiciste esta prueba.

A todo esto, que dice NetworkManager en su icono en la barra del escritorio ? Ve alguna red inalambrica como para activar despues del "rfkill unblock all" ?

---

### Post by LisaSimpson on 2011-11-30
cuando llegue a casa probaré...
tatata tammmmmm
:KS

---

### Post by LisaSimpson on 2011-11-30
Investigaciones del día:
- la gente de Eurocase confirmó que el mismo botón fn-f2 habilita en windows el bluetooth y el wifi, dando mensajes en pantalla sobre cuál de ambos está habilitado, si se aprieta fn-f2 una vez o dos o tres o cuatro veces habilita o desabilita ambos mecanismos, probaMos con Ubuntu y no, no sirve ni una vez, ni dos, ni tres, ni cuatro toques a fn-f2. Quedaron en investigar y llamarnos, es un paso...
Me parece que la cosa pasa por ahí, cuando nos llamen o nosotros llamemos nuevamente les pediré los parámetros para configurar el wifi desde "editar conexiones / inalámbrica"

Me da mucha pena porque estoy pensando en volver a poner un w7 otra vez... para que conviva con Ubuntu ¿tengo alguna otra opción antes que revivir al monstruo destruido? :confused:

---

### Post by LisaSimpson on 2011-11-30
Guillermo, hice lo que sugerís sobre probar la inalámbrica con el cable de red desconectado y nada... todo sigue igual "la red inalámbrica está desactivada por el interruptor físico" :-k

---

### Post by guillermolisi on 2011-11-30
> **LisaSimpson said:**
> Investigaciones del día:
- la gente de Eurocase confirmó que el mismo botón fn-f2 habilita en windows el bluetooth y el wifi, dando mensajes en pantalla sobre cuál de ambos está habilitado, si se aprieta fn-f2 una vez o dos o tres o cuatro veces habilita o desabilita ambos mecanismos, probaMos con Ubuntu y no, no sirve ni una vez, ni dos, ni tres, ni cuatro toques a fn-f2. Quedaron en investigar y llamarnos, es un paso...
Me parece que la cosa pasa por ahí, cuando nos llamen o nosotros llamemos nuevamente les pediré los parámetros para configurar el wifi desde "editar conexiones / inalámbrica"

Me da mucha pena porque estoy pensando en volver a poner un w7 otra vez... para que conviva con Ubuntu ¿tengo alguna otra opción antes que revivir al monstruo destruido? :confused:
Si, siempre hay una alternativa y en este caso seria utilizar una antena USB hasta que la gente de Eurocase (que en realidad usan hardware Chino generico) se expida sobre el funcionamiento de la combinacion de Fn+F2.

Si queres ir por este lado, cualquier dongle USB TP-Link, Encore, Linksys o similar (porque en realidad lo que mas importa es que chip inalambrico utiliza) deberia funcionar con 11.10

Edit:

Congratulations !!

You have reach a kernel upstream bug !! :)

Look at this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/882779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/882779)

El ultimo mensaje reportado dice que encontraron una forma de resolver temporalmente el tema:

Con Windows y el paquete que administra las teclas especiales de la maquina, habilitaron nuevamente la antena incorporada, apagaron la maquina y el BIOS retuvo el estado de encendido de forma tal que cuando iniciaron con Ubuntu la antena ya no estaba apagada electricamente (y por lo tanto no hizo falta accionar Fn+F2)

---

### Post by LisaSimpson on 2011-11-30
Conclusión temporaria: debo reinstalar windows y luego ubuntu sin matar al windows... :(
Wifi atenta contra la utilización de linux como único sistema operativo, grrrrr [-(

(Mientras estoy bajando el Linux Mint "Lisa" a ver si se comporta mejor, prefiero otro linux y no windows, a pesar de las discusiones que me genera este problema con mi marido y sus ganas de retornar al windows... ya se entusiamó con volverlo a instalar... ¿por qué me pasa esto a mí, eh?)

---

### Post by guillermolisi on 2011-11-30
La proxima vez que quieras comprar una maquina, probala antes con un pendrive en modo Live y fijate que cosas funcionan y cuales no. Es la mejor forma de evitar de entrada estos inconvenientes.

Igualmente hay casos mucho peores que este porque la solucion es mucho mas compleja y no esta vinculada con el kernel ni con un fabricante como Realtek.

---

### Post by LisaSimpson on 2011-12-01
A mí me gustan los desafíos, si hubiera llevado mi pendrive de arranque para probar la compu, en su momento tampoco hubiera comprado la netbook, o la otra notebook, porque por ejemplo una notebook MSI no me reconocía la placa de sonido, cosa que solucioné rápidamente googleando y colocando el controlador propietario que corresponde...

Además, me parece interesante despertar las neuronas de los fabricantes de productos y hacerles ver que la vida no es sólo windows, por ejemplo Eurocase trabaja instalando un linux en sus netbooks, lástima que sea el Rxart que es muy limitado y no tiene facilidad de actualizaciones, por lo que se te queda rápidamente viejita... pero el tema es interesante ya que uno de los muchachos del servicio técnico de Eurocase, Sandro, nos dijo telefónicamente que preguntará en la casa de ensamble de las máquinas si han instalado Rxart en alguna de las E3 smart (que es la nuestra), ya que si así fuera, entonces estaríamos más cerca de solucionar el bug que descubrimos tantos usuarios ubuntureros que estamos con wifi a puro RTL8188CE.

¿Vos decís que los muchachos de GNU/Linux Ubuntu y Realtek intentarán solucionar el bug pronto?
Yo espero que sí.
Muchos saludos y ¡gracias por el aguante!

---

### Post by guillermolisi on 2011-12-01
> **LisaSimpson said:**
> A mí me gustan los desafíos, si hubiera llevado mi pendrive de arranque para probar la compu, en su momento tampoco hubiera comprado la netbook, o la otra notebook, porque por ejemplo una notebook MSI no me reconocía la placa de sonido, cosa que solucioné rápidamente googleando y colocando el controlador propietario que corresponde...

Además, me parece interesante despertar las neuronas de los fabricantes de productos y hacerles ver que la vida no es sólo windows, por ejemplo Eurocase trabaja instalando un linux en sus netbooks, lástima que sea el Rxart que es muy limitado y no tiene facilidad de actualizaciones, por lo que se te queda rápidamente viejita... pero el tema es interesante ya que uno de los muchachos del servicio técnico de Eurocase, Sandro, nos dijo telefónicamente que preguntará en la casa de ensamble de las máquinas si han instalado Rxart en alguna de las E3 smart (que es la nuestra), ya que si así fuera, entonces estaríamos más cerca de solucionar el bug que descubrimos tantos usuarios ubuntureros que estamos con wifi a puro RTL8188CE.

¿Vos decís que los muchachos de GNU/Linux Ubuntu y Realtek intentarán solucionar el bug pronto?
Yo espero que sí.
Muchos saludos y ¡gracias por el aguante!
RxArt es peor que Windows porque tomaron codigo abierto GPL, lo modificaron y lo cerraron.

El bug esta confirmado pero como esta relacionado con drivers hay que esperar a que la gente que trabaja el kernel Linux incluya la solucion. Hasta la version estable vigente del kernel, sigue sin estar arreglado (3.1.3-1).

Igualmente me suscribi al bug para saber como evoluciona.

---

### Post by LisaSimpson on 2011-12-03
Coincido con la opinión sobre RxArt, a mi criterio es una violación a las libertades del GNU, por lo que me alegré enormemente cuando vi que las netbooks de Conectar Igualdad de este año salen con Ubuntu.
Quedaremos a la espera de novedades kernelianas entonces... ¡¡¡¡mil veces gracias!!!! sin la ayuda de este foro no hubiera podido nunca saber qué sucedía con este driver y supongo que muchos otros tampoco, sabiendo lo que pasa podemos solucionarlo y evitar retornar al sistema de Bill jejeje :lolflag:

---

### Post by LisaSimpson on 2011-12-11
Según los comentarios de [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/882779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/882779)
hay algunas novedades pero no las entiendo:
---------------------------------------------------------
Sourcerer (pg-futureware) wrote on 2011-12-08:

I have analyzed the HotKey Driver for Windows now. It seems, that it contains 2 parts:
HotKeyOSD.exe captures the keyboard event for FN+F2, and then sends a Windows Message to NButilps.exe, which then activates/deactivates the WLAN.
In the MMKEYBD.CFG, I found the Key#10 line, which is responsible for the WLAN. (Deactivating this line invalidated the FN+F2 function)
[Common HotKey Hook for WinNT]

Key Count = 11

Key #0 = 0,B3,22,1,1,0604,Play/Pause

Key #1 = 0,B2,24,1,1,0602,Stop

Key #2 = 0,B1,10,1,1,0611,Previous

Key #3 = 0,B0,19,1,1,0610,Next Track

Key #4 = 1,AD,20,1,1,0500,Mute

Key #5 = 1,AF,30,1,1,0501,Volume Up

Key #6 = 1,AE,2E,1,1,0502,Volume Down

Key #7 = 0,90,45,1,1,9001,NumLock

Key #8 = 0,91,46,0,0,9002,ScrollLock

Key #9 = 0,14,3A,0,0,9003,CapsLock

Key #10 = 1,FF,70,1,1,F900,Communication Key (WLAN-RFKILL)


According to the comments in the NButilps.exe, it was developed by Dritek ([www.dritek.com.tw](www.dritek.com.tw)) specially for Quanta
-------------------------------------------

El tema es que dice:

Affects: linux (Ubuntu)
Status:  Triaged
Importance: Medium
Assigned to:  Unassigned
Milestone			
¿si no está asignado a nadie y la importancia es media, cuánto tardarán en arreglar el tema?
y otra cosa que me llama la atención de los comentarios es esto:

----------------
Sourcerer (pg-futureware) wrote on 2011-10-27:

I can reproduce it on Linux version 3.1.0-030100rc10-generic (root@gomeisa) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #201110200610 SMP Thu Oct 20 10:20:00 UTC 2011
----------------
yo tengo 3.0.0-13-generic ¿cómo consigo la 3.1.0-030100rc10-generic?

Perdón por tantas preguntas, pero sólo se aprende investigando, leyendo y preguntando a expertos...
Gracias desde ya
Patry 

PS: por aquí llueve, elijan una peli para mirar, el pororó se los regalo, aquí va: :popcorn:

---

### Post by guillermolisi on 2011-12-11
Basicamente dice que la solucion seria provista por los desarrolladores del kernel Linux (Kernel Linux upstream).
Igualmente eso no quita que alguien como el que hizo el comentario que citas, termine modificando el driver original y logre, a partir de sus investigaciones, proveer algo que habilite el accionamiento de las teclas para apagado y encendido de la antena.

Cuanto puede demorar esto ? No hay ninguna regla, receta o pauta. Puede que nunca o puede que, a raiz de que cada vez haya mas maquinas con esta antena inalabrica y este probema de encendido/apagado, resuelvan cambiarle la prioridad. Basicamente la importancia se la dara la cantidad de casos que confirmen no solamente la existencia del bug sino tambien que hay mucha gente usando ese adaptador de red, con lo cual deberan darle la prioridad que merece (para que no los insulten) :)

---

### Post by LisaSimpson on 2011-12-11
Hice la prueba con el kernel 3.1.0-030100-generic (ahora volví al 3.0.0-14-generic) pero tampoco soluciona nada...
de todos modos esa persona que decía que lo había solucionado hablaba del 3.1.0-030100rc10-generic  y no lo encontré... pero no creo que arregle nada de nada...
en fin, sé que hay varias marcas con este dispositivo, he visto Lenovo, DELL, MSI (por suerte la MSI que tenemos no usa este wifi), entre otras marcas... con lo que pronto será un tema constante, espero que se solucione pronto.

Gracias por el acompañamiento... :KS

---

### Post by guillermolisi on 2011-12-11
El reporter del comentario que citaste no dice haberlo resuelto con esa version de kernel sino, por el contrario, dice haber verificado que con esa version tambien falla, por lo tanto le sugieren agregar la etiqueta de kerner-upstream al reporte original del bug asi la gente de Ubuntu lo pasa a quien corresponda via bugzilla (o como sea que lo hagan ahora) ya que en las ultimas versiones de kernel el problema sigue vigente.

---

### Post by LisaSimpson on 2012-01-07
Encontré esto en una lista de correos sobre linux:
--------------------------------
This collection of patches does additional cleanups on the rtlwifi family.
Included are some new checks for allocation failures, removal of some dead code, and updating of the copyright date.

These patches should be applied after the two series of cleanups by Joe Perches
([http://marc.info/?l=linux-wireless&m=132573516421817&w=2](http://marc.info/?l=linux-wireless&m=132573516421817&w=2) and
[http://marc.info/?l=linux-wireless&m=132588359201755&w=2](http://marc.info/?l=linux-wireless&m=132588359201755&w=2))

and the fix for crashes in rtl8192se caused by memory allocation failures
([http://marc.info/?l=linux-wireless&m=132573199321141&w=2](http://marc.info/?l=linux-wireless&m=132573199321141&w=2)).

Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---

Larry Finger (8):
 rtlwifi: rtl8192c_common: rtl8192de: Check for allocation failures
 rtl8192cu: Remove dead code never selected
 rtlwifi: Update copyright dates
 rtl8192c_common: Update copyright dates
 rtl8192ce: Update copyright dates
 rtl8192cu: Update copyright dates
 rtl8192de: Update copyright dates
 rtl8192se: Update copyright dates

 drivers/net/wireless/rtlwifi/base.c                |    2 +-
 drivers/net/wireless/rtlwifi/base.h                |    2 +-
 drivers/net/wireless/rtlwifi/cam.c                 |    2 +-
 drivers/net/wireless/rtlwifi/cam.h                 |    2 +-
 drivers/net/wireless/rtlwifi/core.c                |    2 +-
 drivers/net/wireless/rtlwifi/core.h                |    2 +-
 drivers/net/wireless/rtlwifi/debug.c               |    2 +-
 drivers/net/wireless/rtlwifi/debug.h               |    2 +-
 drivers/net/wireless/rtlwifi/efuse.c               |    2 +-
 drivers/net/wireless/rtlwifi/efuse.h               |    2 +-
 drivers/net/wireless/rtlwifi/pci.c                 |    4 +-
 drivers/net/wireless/rtlwifi/pci.h                 |    2 +-
 drivers/net/wireless/rtlwifi/ps.c                  |    2 +-
 drivers/net/wireless/rtlwifi/ps.h                  |    2 +-
 drivers/net/wireless/rtlwifi/rc.c                  |    2 +-
 drivers/net/wireless/rtlwifi/rc.h                  |    2 +-
 drivers/net/wireless/rtlwifi/regd.c                |    2 +-
 drivers/net/wireless/rtlwifi/regd.h                |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/dm_common.c  |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/dm_common.h  |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c  |    4 +-
 drivers/net/wireless/rtlwifi/rtl8192c/fw_common.h  |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/main.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/phy_common.c |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/phy_common.h |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/def.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/dm.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/dm.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/hw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/hw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/led.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/led.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/phy.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/phy.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/reg.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/rf.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/rf.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/sw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/sw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/table.c     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/table.h     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/trx.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/trx.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/def.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/dm.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/dm.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/hw.c        |  172 +-------------------
 drivers/net/wireless/rtlwifi/rtl8192cu/hw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/led.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/led.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/mac.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/mac.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/phy.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/phy.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/reg.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/rf.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/rf.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/sw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/sw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/table.c     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/table.h     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/trx.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/trx.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/def.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/dm.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/dm.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/fw.c        |   16 ++-
 drivers/net/wireless/rtlwifi/rtl8192de/fw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/hw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/hw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/led.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/led.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/phy.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/phy.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/reg.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/rf.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/rf.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/sw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/sw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/table.c     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/table.h     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/trx.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/trx.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/def.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/dm.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/dm.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/fw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/fw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/hw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/hw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/led.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/led.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/phy.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/phy.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/reg.h       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/rf.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/rf.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/sw.c        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/sw.h        |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/table.c     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/table.h     |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/trx.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/trx.h       |    2 +-
 drivers/net/wireless/rtlwifi/usb.c                 |   14 +-
 drivers/net/wireless/rtlwifi/usb.h                 |    2 +-
 drivers/net/wireless/rtlwifi/wifi.h                |    2 +-
 106 files changed, 126 insertions(+), 286 deletions(-)
---------------------
¿Me servirá algo de esto? ¿qué significa todo esto que dice aquí?
Yo tengo mi Ubuntu reinstalado de cero, o sea que todo eso que instalé antes ya no está... ¿por donde empiezo?

---

### Post by LisaSimpson on 2012-01-07
En otro mensaje, a continuación del anterior dice esto:


In [https://bugzilla.redhat.com/show_bug.cgi?id=771656](https://bugzilla.redhat.com/show_bug.cgi?id=771656), a kernel bug was
triggered due to a failed skb allocation that was not checked. This event
lead to an audit of all memory allocations in the complete rtlwifi family
of drivers. This patch fixes the rest.

Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
Cc: Stable <stable@vger.kernel.org>
---
---
 drivers/net/wireless/rtlwifi/pci.c                |    2 ++
 drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c |    2 ++
 drivers/net/wireless/rtlwifi/rtl8192de/fw.c       |   14 +++++++++-----
 drivers/net/wireless/rtlwifi/usb.c                |   12 +++++++-----
 4 files changed, 20 insertions(+), 10 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/pci.c b/drivers/net/wireless/rtlwifi/pci.c
index 74d8fbf..ed6f6a9 100644
--- a/drivers/net/wireless/rtlwifi/pci.c
+++ b/drivers/net/wireless/rtlwifi/pci.c
@@ -652,6 +652,8 @@ static void _rtl_receive_one(struct ieee80211_hw *hw, struct sk_buff *skb,
               return;

       uskb = dev_alloc_skb(skb->len + 128);
+       if (!uskb)
+               return;         /* exit if allocation failed */
       memcpy(IEEE80211_SKB_RXCB(uskb), &rx_status, sizeof(rx_status));
       pdata = (u8 *)skb_put(uskb, skb->len);
       memcpy(pdata, skb->data, skb->len);
diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c b/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c
index 1eae3ba..e9e9c26 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c
@@ -785,6 +785,8 @@ void rtl92c_set_fw_rsvdpagepkt(struct ieee80211_hw *hw, bool dl_finished)


       skb = dev_alloc_skb(totalpacketlen);
+       if (!skb)
+               return;
       memcpy((u8 *) skb_put(skb, totalpacketlen),
              &reserved_page_packet, totalpacketlen);

diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/fw.c b/drivers/net/wireless/rtlwifi/rtl8192de/fw.c
index 94f5b7d..da58ca4 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/fw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/fw.c
@@ -756,12 +756,16 @@ void rtl92d_set_fw_rsvdpagepkt(struct ieee80211_hw *hw, bool dl_finished)
                     "rtl92d_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL",
                     u1RsvdPageLoc, 3);
       skb = dev_alloc_skb(totalpacketlen);
-       memcpy((u8 *) skb_put(skb, totalpacketlen), &reserved_page_packet,
-               totalpacketlen);
-       rtstatus = _rtl92d_cmd_send_packet(hw, skb);
+       if (!skb) {
+               dlok = false;
+       } else {
+               memcpy((u8 *) skb_put(skb, totalpacketlen),
+                       &reserved_page_packet, totalpacketlen);
+               rtstatus = _rtl92d_cmd_send_packet(hw, skb);

-       if (rtstatus)
-               dlok = true;
+               if (rtstatus)
+                       dlok = true;
+       }
       if (dlok) {
               RT_TRACE(rtlpriv, COMP_POWER, DBG_LOUD,
                        "Set RSVD page location to Fw\n");
diff --git a/drivers/net/wireless/rtlwifi/usb.c b/drivers/net/wireless/rtlwifi/usb.c
index 6ae1b21..4db06f6 100644
--- a/drivers/net/wireless/rtlwifi/usb.c
+++ b/drivers/net/wireless/rtlwifi/usb.c
@@ -520,12 +520,14 @@ static void _rtl_usb_rx_process_noagg(struct ieee80211_hw *hw,
                       u8 *pdata;

                       uskb = dev_alloc_skb(skb->len + 128);
-                       memcpy(IEEE80211_SKB_RXCB(uskb), &rx_status,
-                              sizeof(rx_status));
-                       pdata = (u8 *)skb_put(uskb, skb->len);
-                       memcpy(pdata, skb->data, skb->len);
+                       if (uskb) {     /* drop packet on allocation failure */
+                               memcpy(IEEE80211_SKB_RXCB(uskb), &rx_status,
+                                      sizeof(rx_status));
+                               pdata = (u8 *)skb_put(uskb, skb->len);
+                               memcpy(pdata, skb->data, skb->len);
+                               ieee80211_rx_irqsafe(hw, uskb);
+                       }
                       dev_kfree_skb_any(skb);
-                       ieee80211_rx_irqsafe(hw, uskb);
               } else {
                       dev_kfree_skb_any(skb);
               }

---

### Post by LisaSimpson on 2012-01-07
y este otro:


The original driver contained some conditional code that was not selected,
but was not deleted in case it would be used later. That code can now be
removed.

Reported-by: Joe Perches <joe@perches.com>
Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---
---
 drivers/net/wireless/rtlwifi/rtl8192cu/hw.c |  170 ---------------------------
 1 files changed, 0 insertions(+), 170 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c b/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c
index 516cf1b..51b7aa1 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c
@@ -339,144 +339,8 @@ static void _rtl92cu_read_board_type(struct ieee80211_hw *hw, u8 *contents)
       if (IS_HIGHT_PA(rtlefuse->board_type))
               rtlefuse->external_pa = 1;
       pr_info("Board Type %x\n", rtlefuse->board_type);
-
-#ifdef CONFIG_ANTENNA_DIVERSITY
-       /* Antenna Diversity setting. */
-       if (registry_par->antdiv_cfg == 2) /* 2: From Efuse */
-               rtl_efuse->antenna_cfg = (contents[EEPROM_RF_OPT1]&0x18)>>3;
-       else
-               rtl_efuse->antenna_cfg = registry_par->antdiv_cfg; /* 0:OFF, */
-
-       pr_info("Antenna Config %x\n", rtl_efuse->antenna_cfg);
-#endif
-}
-
-#ifdef CONFIG_BT_COEXIST
-static void _update_bt_param(_adapter *padapter)
-{
-       struct btcoexist_priv    *pbtpriv = &(padapter->halpriv.bt_coexist);
-       struct registry_priv    *registry_par = &padapter->registrypriv;
-       if (2 != registry_par->bt_iso) {
-               /* 0:Low, 1:High, 2:From Efuse */
-               pbtpriv->BT_Ant_isolation = registry_par->bt_iso;
-       }
-       if (registry_par->bt_sco == 1) {
-               /* 0:Idle, 1:None-SCO, 2:SCO, 3:From Counter, 4.Busy,
-                * 5.OtherBusy */
-               pbtpriv->BT_Service = BT_OtherAction;
-       } else if (registry_par->bt_sco == 2) {
-               pbtpriv->BT_Service = BT_SCO;
-       } else if (registry_par->bt_sco == 4) {
-               pbtpriv->BT_Service = BT_Busy;
-       } else if (registry_par->bt_sco == 5) {
-               pbtpriv->BT_Service = BT_OtherBusy;
-       } else {
-               pbtpriv->BT_Service = BT_Idle;
-       }
-       pbtpriv->BT_Ampdu = registry_par->bt_ampdu;
-       pbtpriv->bCOBT = _TRUE;
-       pbtpriv->BtEdcaUL = 0;
-       pbtpriv->BtEdcaDL = 0;
-       pbtpriv->BtRssiState = 0xff;
-       pbtpriv->bInitSet = _FALSE;
-       pbtpriv->bBTBusyTraffic = _FALSE;
-       pbtpriv->bBTTrafficModeSet = _FALSE;
-       pbtpriv->bBTNonTrafficModeSet = _FALSE;
-       pbtpriv->CurrentState = 0;
-       pbtpriv->PreviousState = 0;
-       pr_info("BT Coexistance = %s\n",
-               (pbtpriv->BT_Coexist == _TRUE) ? "enable" : "disable");
-       if (pbtpriv->BT_Coexist) {
-               if (pbtpriv->BT_Ant_Num == Ant_x2)
-                       pr_info("BlueTooth BT_Ant_Num = Antx2\n");
-               else if (pbtpriv->BT_Ant_Num == Ant_x1)
-                       pr_info("BlueTooth BT_Ant_Num = Antx1\n");
-               switch (pbtpriv->BT_CoexistType) {
-               case BT_2Wire:
-                       pr_info("BlueTooth BT_CoexistType = BT_2Wire\n");
-                       break;
-               case BT_ISSC_3Wire:
-                       pr_info("BlueTooth BT_CoexistType = BT_ISSC_3Wire\n");
-                       break;
-               case BT_Accel:
-                       pr_info("BlueTooth BT_CoexistType = BT_Accel\n");
-                       break;
-               case BT_CSR_BC4:
-                       pr_info("BlueTooth BT_CoexistType = BT_CSR_BC4\n");
-                       break;
-               case BT_CSR_BC8:
-                       pr_info("BlueTooth BT_CoexistType = BT_CSR_BC8\n");
-                       break;
-               case BT_RTL8756:
-                       pr_info("BlueTooth BT_CoexistType = BT_RTL8756\n");
-                       break;
-               default:
-                       pr_info("BlueTooth BT_CoexistType = Unknown\n");
-                       break;
-               }
-               pr_info("BlueTooth BT_Ant_isolation = %d\n",
-                       pbtpriv->BT_Ant_isolation);
-               switch (pbtpriv->BT_Service) {
-               case BT_OtherAction:
-                       pr_info("BlueTooth BT_Service = BT_OtherAction\n");
-                       break;
-               case BT_SCO:
-                       pr_info("BlueTooth BT_Service = BT_SCO\n");
-                       break;
-               case BT_Busy:
-                       pr_info("BlueTooth BT_Service = BT_Busy\n");
-                       break;
-               case BT_OtherBusy:
-                       pr_info("BlueTooth BT_Service = BT_OtherBusy\n");
-                       break;
-               default:
-                       pr_info("BlueTooth BT_Service = BT_Idle\n");
-                       break;
-               }
-               pr_info("BT_RadioSharedType = 0x%x\n",
-                       pbtpriv->BT_RadioSharedType);
-       }
 }

-#define GET_BT_COEXIST(priv) (&priv->bt_coexist)
-
-static void _rtl92cu_read_bluetooth_coexistInfo(struct ieee80211_hw *hw,
-                                               u8 *contents,
-                                               bool bautoloadfailed);
-{
-       HAL_DATA_TYPE   *pHalData = GET_HAL_DATA(Adapter);
-       bool isNormal = IS_NORMAL_CHIP(pHalData->VersionID);
-       struct btcoexist_priv    *pbtpriv = &pHalData->bt_coexist;
-       u8      rf_opt4;
-
-       _rtw_memset(pbtpriv, 0, sizeof(struct btcoexist_priv));
-       if (AutoloadFail) {
-               pbtpriv->BT_Coexist = _FALSE;
-               pbtpriv->BT_CoexistType = BT_2Wire;
-               pbtpriv->BT_Ant_Num = Ant_x2;
-               pbtpriv->BT_Ant_isolation = 0;
-               pbtpriv->BT_RadioSharedType = BT_Radio_Shared;
-               return;
-       }
-       if (isNormal) {
-               if (pHalData->BoardType == BOARD_USB_COMBO)
-                       pbtpriv->BT_Coexist = _TRUE;
-               else
-                       pbtpriv->BT_Coexist = ((PROMContent[EEPROM_RF_OPT3] &
-                                             0x20) >> 5); /* bit[5] */
-               rf_opt4 = PROMContent[EEPROM_RF_OPT4];
-               pbtpriv->BT_CoexistType = ((rf_opt4&0xe)>>1); /* bit [3:1] */
-               pbtpriv->BT_Ant_Num = (rf_opt4&0x1); /* bit [0] */
-               pbtpriv->BT_Ant_isolation = ((rf_opt4&0x10)>>4); /* bit [4] */
-               pbtpriv->BT_RadioSharedType = ((rf_opt4&0x20)>>5); /* bit [5] */
-       } else {
-               pbtpriv->BT_Coexist = (PROMContent[EEPROM_RF_OPT4] >> 4) ?
-                                      _TRUE : _FALSE;
-       }
-       _update_bt_param(Adapter);
-}
-#endif
-
 static void _rtl92cu_read_adapter_info(struct ieee80211_hw *hw)
 {
       struct rtl_priv *rtlpriv = rtl_priv(hw);
@@ -552,10 +416,6 @@ static void _rtl92cu_read_adapter_info(struct ieee80211_hw *hw)
               }
       }
       _rtl92cu_read_board_type(hw, hwinfo);
-#ifdef CONFIG_BT_COEXIST
-       _rtl92cu_read_bluetooth_coexistInfo(hw, hwinfo,
-                                           rtlefuse->autoload_failflag);
-#endif
 }

 static void _rtl92cu_hal_customized_behavior(struct ieee80211_hw *hw)
@@ -1107,34 +967,6 @@ static void _InitPABias(struct ieee80211_hw *hw)
       }
 }

-static void _InitAntenna_Selection(struct ieee80211_hw *hw)
-{
-#ifdef CONFIG_ANTENNA_DIVERSITY
-       struct rtl_priv *rtlpriv = rtl_priv(hw);
-       struct rtl_hal *rtlhal = rtl_hal(rtl_priv(hw));
-       struct rtl_phy *rtlphy = &(rtlpriv->phy);
-
-       if (pHalData->AntDivCfg == 0)
-               return;
-
-       if (rtlphy->rf_type == RF_1T1R) {
-               rtl_write_dword(rtlpriv, REG_LEDCFG0,
-                               rtl_read_dword(rtlpriv,
-                               REG_LEDCFG0)|BIT(23));
-               rtl_set_bbreg(hw, rFPGA0_XAB_RFPARAMETER, BIT(13), 0x01);
-               if (rtl_get_bbreg(hw, RFPGA0_XA_RFINTERFACEOE, 0x300) ==
-                   Antenna_A)
-                       pHalData->CurAntenna = Antenna_A;
-               else
-                       pHalData->CurAntenna = Antenna_B;
-       }
-#endif
-}
-
-static void _dump_registers(struct ieee80211_hw *hw)
-{
-}
-
 static void _update_mac_setting(struct ieee80211_hw *hw)
 {
       struct rtl_priv *rtlpriv = rtl_priv(hw);
@@ -1205,10 +1037,8 @@ int rtl92cu_hw_init(struct ieee80211_hw *hw)
       }
       _rtl92cu_hw_configure(hw);
       _InitPABias(hw);
-       _InitAntenna_Selection(hw);
       _update_mac_setting(hw);
       rtl92c_dm_init(hw);
-       _dump_registers(hw);
       return err;
 }

---

### Post by LisaSimpson on 2012-01-07
y este más:


Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---
---
 drivers/net/wireless/rtlwifi/base.c  |    2 +-
 drivers/net/wireless/rtlwifi/base.h  |    2 +-
 drivers/net/wireless/rtlwifi/cam.c   |    2 +-
 drivers/net/wireless/rtlwifi/cam.h   |    2 +-
 drivers/net/wireless/rtlwifi/core.c  |    2 +-
 drivers/net/wireless/rtlwifi/core.h  |    2 +-
 drivers/net/wireless/rtlwifi/debug.c |    2 +-
 drivers/net/wireless/rtlwifi/debug.h |    2 +-
 drivers/net/wireless/rtlwifi/efuse.c |    2 +-
 drivers/net/wireless/rtlwifi/efuse.h |    2 +-
 drivers/net/wireless/rtlwifi/pci.c   |    2 +-
 drivers/net/wireless/rtlwifi/pci.h   |    2 +-
 drivers/net/wireless/rtlwifi/ps.c    |    2 +-
 drivers/net/wireless/rtlwifi/ps.h    |    2 +-
 drivers/net/wireless/rtlwifi/rc.c    |    2 +-
 drivers/net/wireless/rtlwifi/rc.h    |    2 +-
 drivers/net/wireless/rtlwifi/regd.c  |    2 +-
 drivers/net/wireless/rtlwifi/regd.h  |    2 +-
 drivers/net/wireless/rtlwifi/usb.c   |    2 +-
 drivers/net/wireless/rtlwifi/usb.h   |    2 +-
 drivers/net/wireless/rtlwifi/wifi.h  |    2 +-
 21 files changed, 21 insertions(+), 21 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/base.c b/drivers/net/wireless/rtlwifi/base.c
index 4f9676b..2bed01f 100644
--- a/drivers/net/wireless/rtlwifi/base.c
+++ b/drivers/net/wireless/rtlwifi/base.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/base.h b/drivers/net/wireless/rtlwifi/base.h
index a7595e2..9ebfdf8 100644
--- a/drivers/net/wireless/rtlwifi/base.h
+++ b/drivers/net/wireless/rtlwifi/base.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/cam.c b/drivers/net/wireless/rtlwifi/cam.c
index cbf5e3c..8fd820d 100644
--- a/drivers/net/wireless/rtlwifi/cam.c
+++ b/drivers/net/wireless/rtlwifi/cam.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/cam.h b/drivers/net/wireless/rtlwifi/cam.h
index c62da4e..35e0008 100644
--- a/drivers/net/wireless/rtlwifi/cam.h
+++ b/drivers/net/wireless/rtlwifi/cam.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/core.c b/drivers/net/wireless/rtlwifi/core.c
index ab6a406..d6e37e6 100644
--- a/drivers/net/wireless/rtlwifi/core.c
+++ b/drivers/net/wireless/rtlwifi/core.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/core.h b/drivers/net/wireless/rtlwifi/core.h
index f02824a..a45c389 100644
--- a/drivers/net/wireless/rtlwifi/core.h
+++ b/drivers/net/wireless/rtlwifi/core.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * Tmis program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/debug.c b/drivers/net/wireless/rtlwifi/debug.c
index 579a05e..0564655 100644
--- a/drivers/net/wireless/rtlwifi/debug.c
+++ b/drivers/net/wireless/rtlwifi/debug.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * Tmis program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/debug.h b/drivers/net/wireless/rtlwifi/debug.h
index b024c23..83d1d7b 100644
--- a/drivers/net/wireless/rtlwifi/debug.h
+++ b/drivers/net/wireless/rtlwifi/debug.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * Tmis program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/efuse.c b/drivers/net/wireless/rtlwifi/efuse.c
index a079a31..b24cbe6 100644
--- a/drivers/net/wireless/rtlwifi/efuse.c
+++ b/drivers/net/wireless/rtlwifi/efuse.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * Tmis program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/efuse.h b/drivers/net/wireless/rtlwifi/efuse.h
index 164daba..2bdea9a 100644
--- a/drivers/net/wireless/rtlwifi/efuse.h
+++ b/drivers/net/wireless/rtlwifi/efuse.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/pci.c b/drivers/net/wireless/rtlwifi/pci.c
index ed6f6a9..aafbe2d 100644
--- a/drivers/net/wireless/rtlwifi/pci.c
+++ b/drivers/net/wireless/rtlwifi/pci.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/pci.h b/drivers/net/wireless/rtlwifi/pci.h
index ebe0b42..99d81ed 100644
--- a/drivers/net/wireless/rtlwifi/pci.h
+++ b/drivers/net/wireless/rtlwifi/pci.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/ps.c b/drivers/net/wireless/rtlwifi/ps.c
index a36dc3d..b151266 100644
--- a/drivers/net/wireless/rtlwifi/ps.c
+++ b/drivers/net/wireless/rtlwifi/ps.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/ps.h b/drivers/net/wireless/rtlwifi/ps.h
index 84628e60..1357856 100644
--- a/drivers/net/wireless/rtlwifi/ps.h
+++ b/drivers/net/wireless/rtlwifi/ps.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rc.c b/drivers/net/wireless/rtlwifi/rc.c
index 4f560d6..c66f08a 100644
--- a/drivers/net/wireless/rtlwifi/rc.c
+++ b/drivers/net/wireless/rtlwifi/rc.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rc.h b/drivers/net/wireless/rtlwifi/rc.h
index 4afa2c2..4d61761 100644
--- a/drivers/net/wireless/rtlwifi/rc.h
+++ b/drivers/net/wireless/rtlwifi/rc.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/regd.c b/drivers/net/wireless/rtlwifi/regd.c
index c263df2..c1608cd 100644
--- a/drivers/net/wireless/rtlwifi/regd.c
+++ b/drivers/net/wireless/rtlwifi/regd.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/regd.h b/drivers/net/wireless/rtlwifi/regd.h
index d231189..70ef2f4 100644
--- a/drivers/net/wireless/rtlwifi/regd.h
+++ b/drivers/net/wireless/rtlwifi/regd.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/usb.c b/drivers/net/wireless/rtlwifi/usb.c
index 4db06f6..78194e3 100644
--- a/drivers/net/wireless/rtlwifi/usb.c
+++ b/drivers/net/wireless/rtlwifi/usb.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2011  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/usb.h b/drivers/net/wireless/rtlwifi/usb.h
index d2a63fb..cdad7c2 100644
--- a/drivers/net/wireless/rtlwifi/usb.h
+++ b/drivers/net/wireless/rtlwifi/usb.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2011  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/wifi.h b/drivers/net/wireless/rtlwifi/wifi.h
index 115969d..72770c6 100644
--- a/drivers/net/wireless/rtlwifi/wifi.h
+++ b/drivers/net/wireless/rtlwifi/wifi.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as

---

### Post by LisaSimpson on 2012-01-07
Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---
 drivers/net/wireless/rtlwifi/rtl8192c/dm_common.c  |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/dm_common.h  |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c  |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/fw_common.h  |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/main.c       |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/phy_common.c |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192c/phy_common.h |    2 +-
 7 files changed, 7 insertions(+), 7 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.c b/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.c
index bf94cbf..cb5535c 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.h b/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.h
index b9736d3..2178e37 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/dm_common.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c b/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c
index e9e9c26..75be221 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.h b/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.h
index cec5a3a..780ea5b 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/fw_common.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/main.c b/drivers/net/wireless/rtlwifi/rtl8192c/main.c
index 605ff19..8ae65b5 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/main.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/main.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.c b/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.c
index 25bde96..22e998d 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.h b/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.h
index 9a264c0..cec10d6 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192c/phy_common.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as

---

### Post by LisaSimpson on 2012-01-07
Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---
 drivers/net/wireless/rtlwifi/rtl8192ce/def.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/dm.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/dm.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/hw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/hw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/led.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/led.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/phy.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/phy.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/reg.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/rf.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/rf.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/sw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/sw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/table.c |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/table.h |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/trx.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192ce/trx.h   |    2 +-
 18 files changed, 18 insertions(+), 18 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/def.h b/drivers/net/wireless/rtlwifi/rtl8192ce/def.h
index 9fc804d..04c3aef 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/def.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/def.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/dm.c b/drivers/net/wireless/rtlwifi/rtl8192ce/dm.c
index 6730e68..27b3af8 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/dm.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/dm.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/dm.h b/drivers/net/wireless/rtlwifi/rtl8192ce/dm.h
index 07dd955..26747fa 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/dm.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/dm.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/hw.c b/drivers/net/wireless/rtlwifi/rtl8192ce/hw.c
index 971bd29..c5aced4 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/hw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/hw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/hw.h b/drivers/net/wireless/rtlwifi/rtl8192ce/hw.h
index 07dbe3e..52a3aea 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/hw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/hw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/led.c b/drivers/net/wireless/rtlwifi/rtl8192ce/led.c
index 09758f4..8283e9b 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/led.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/led.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/led.h b/drivers/net/wireless/rtlwifi/rtl8192ce/led.h
index 7dfccea..c576106 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/led.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/led.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/phy.c b/drivers/net/wireless/rtlwifi/rtl8192ce/phy.c
index 03ee82e..c64daf2 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/phy.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/phy.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/phy.h b/drivers/net/wireless/rtlwifi/rtl8192ce/phy.h
index be2c92a..d5e3b70 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/phy.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/phy.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/reg.h b/drivers/net/wireless/rtlwifi/rtl8192ce/reg.h
index ba5ff04..43806d9 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/reg.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/reg.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/rf.c b/drivers/net/wireless/rtlwifi/rtl8192ce/rf.c
index 5ef9604..69d720d 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/rf.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/rf.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/rf.h b/drivers/net/wireless/rtlwifi/rtl8192ce/rf.h
index 39ff036..6c8d56e 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/rf.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/rf.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/sw.c b/drivers/net/wireless/rtlwifi/rtl8192ce/sw.c
index 425387a..2d72c95 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/sw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/sw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/sw.h b/drivers/net/wireless/rtlwifi/rtl8192ce/sw.h
index b7dc326..d2367a5 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/sw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/sw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/table.c b/drivers/net/wireless/rtlwifi/rtl8192ce/table.c
index ba938b9..752f943 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/table.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/table.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/table.h b/drivers/net/wireless/rtlwifi/rtl8192ce/table.h
index 3a6e8b6..8b79161 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/table.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/table.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/trx.c b/drivers/net/wireless/rtlwifi/rtl8192ce/trx.c
index 41b54d5..d59f12c 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/trx.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/trx.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192ce/trx.h b/drivers/net/wireless/rtlwifi/rtl8192ce/trx.h
index c8977a5..efb9ab2 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192ce/trx.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192ce/trx.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as

---

### Post by LisaSimpson on 2012-01-07
Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---
 drivers/net/wireless/rtlwifi/rtl8192se/def.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/dm.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/dm.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/fw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/fw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/hw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/hw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/led.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/led.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/phy.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/phy.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/reg.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/rf.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/rf.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/sw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/sw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/table.c |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/table.h |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/trx.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192se/trx.h   |    2 +-
 20 files changed, 20 insertions(+), 20 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/def.h b/drivers/net/wireless/rtlwifi/rtl8192se/def.h
index c6c0448..d1b0a1e 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/def.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/def.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/dm.c b/drivers/net/wireless/rtlwifi/rtl8192se/dm.c
index 4a5e3a9..fbabae1 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/dm.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/dm.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/dm.h b/drivers/net/wireless/rtlwifi/rtl8192se/dm.h
index 9051a55..e1b19a6 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/dm.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/dm.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/fw.c b/drivers/net/wireless/rtlwifi/rtl8192se/fw.c
index 2a9699f..595ecd22 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/fw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/fw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/fw.h b/drivers/net/wireless/rtlwifi/rtl8192se/fw.h
index 74cc503..babe85d 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/fw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/fw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/hw.c b/drivers/net/wireless/rtlwifi/rtl8192se/hw.c
index b03001b..625c9eb 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/hw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/hw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/hw.h b/drivers/net/wireless/rtlwifi/rtl8192se/hw.h
index 6160a9b..1886c26 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/hw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/hw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/led.c b/drivers/net/wireless/rtlwifi/rtl8192se/led.c
index 1a6b0ca..ef4211b 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/led.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/led.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/led.h b/drivers/net/wireless/rtlwifi/rtl8192se/led.h
index 8cce387..2182dbe 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/led.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/led.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/phy.c b/drivers/net/wireless/rtlwifi/rtl8192se/phy.c
index e24dbb3..adfac56 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/phy.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/phy.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/phy.h b/drivers/net/wireless/rtlwifi/rtl8192se/phy.h
index 37e504a..ac03877 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/phy.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/phy.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/reg.h b/drivers/net/wireless/rtlwifi/rtl8192se/reg.h
index 11f125c..84d1181 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/reg.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/reg.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/rf.c b/drivers/net/wireless/rtlwifi/rtl8192se/rf.c
index 8966b73..46be4cc 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/rf.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/rf.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/rf.h b/drivers/net/wireless/rtlwifi/rtl8192se/rf.h
index 3843baa..8a29eb9 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/rf.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/rf.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/sw.c b/drivers/net/wireless/rtlwifi/rtl8192se/sw.c
index 098c8a1..ca4b6fe 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/sw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/sw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/sw.h b/drivers/net/wireless/rtlwifi/rtl8192se/sw.h
index fc4eb28..2eb8886 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/sw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/sw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/table.c b/drivers/net/wireless/rtlwifi/rtl8192se/table.c
index 154185b..f1a73f7 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/table.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/table.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/table.h b/drivers/net/wireless/rtlwifi/rtl8192se/table.h
index b4ed6d9..2feb73b 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/table.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/table.h
@@ -1,5 +1,5 @@
 /******************************************************************************
- * Copyright(c) 2008 - 2010 Realtek Corporation. All rights reserved.
+ * Copyright(c) 2008 - 2012 Realtek Corporation. All rights reserved.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/trx.c b/drivers/net/wireless/rtlwifi/rtl8192se/trx.c
index 5dbb326..e58b80f 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/trx.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/trx.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192se/trx.h b/drivers/net/wireless/rtlwifi/rtl8192se/trx.h
index 05862c5..011e7b0 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192se/trx.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192se/trx.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as

---

### Post by LisaSimpson on 2012-01-07
Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---
 drivers/net/wireless/rtlwifi/rtl8192de/def.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/dm.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/dm.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/fw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/fw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/hw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/hw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/led.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/led.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/phy.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/phy.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/reg.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/rf.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/rf.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/sw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/sw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/table.c |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/table.h |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/trx.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192de/trx.h   |    2 +-
 20 files changed, 20 insertions(+), 20 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/def.h b/drivers/net/wireless/rtlwifi/rtl8192de/def.h
index 9463047..eafdf76 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/def.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/def.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/dm.c b/drivers/net/wireless/rtlwifi/rtl8192de/dm.c
index 32537c4..181ed6f 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/dm.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/dm.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/dm.h b/drivers/net/wireless/rtlwifi/rtl8192de/dm.h
index 6935465..91030ec 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/dm.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/dm.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/fw.c b/drivers/net/wireless/rtlwifi/rtl8192de/fw.c
index da58ca4..b59de75 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/fw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/fw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/fw.h b/drivers/net/wireless/rtlwifi/rtl8192de/fw.h
index 0c4d489..1ffacdd 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/fw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/fw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/hw.c b/drivers/net/wireless/rtlwifi/rtl8192de/hw.c
index 88b4d07..265cea3 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/hw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/hw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/hw.h b/drivers/net/wireless/rtlwifi/rtl8192de/hw.h
index ad44ffa..7c9f7a2 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/hw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/hw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/led.c b/drivers/net/wireless/rtlwifi/rtl8192de/led.c
index f2358f2..76a57ae 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/led.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/led.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/led.h b/drivers/net/wireless/rtlwifi/rtl8192de/led.h
index 57f4a3c..a29df30 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/led.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/led.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/phy.c b/drivers/net/wireless/rtlwifi/rtl8192de/phy.c
index f27acc7..9581a19 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/phy.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/phy.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/phy.h b/drivers/net/wireless/rtlwifi/rtl8192de/phy.h
index a52c824..f074952 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/phy.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/phy.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/reg.h b/drivers/net/wireless/rtlwifi/rtl8192de/reg.h
index 131acc3..9bc4623 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/reg.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/reg.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/rf.c b/drivers/net/wireless/rtlwifi/rtl8192de/rf.c
index 2e174f4..ff34d2d 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/rf.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/rf.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/rf.h b/drivers/net/wireless/rtlwifi/rtl8192de/rf.h
index 74b9cfc..0fe1a48 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/rf.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/rf.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/sw.c b/drivers/net/wireless/rtlwifi/rtl8192de/sw.c
index 020e4e5..ca8f2df 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/sw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/sw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/sw.h b/drivers/net/wireless/rtlwifi/rtl8192de/sw.h
index c95e47d..0e6035b 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/sw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/sw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/table.c b/drivers/net/wireless/rtlwifi/rtl8192de/table.c
index bad7f94..8ea6f52 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/table.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/table.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/table.h b/drivers/net/wireless/rtlwifi/rtl8192de/table.h
index 93f30ca..8b724a8 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/table.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/table.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/trx.c b/drivers/net/wireless/rtlwifi/rtl8192de/trx.c
index 8f487ed..9aacd2f 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/trx.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/trx.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192de/trx.h b/drivers/net/wireless/rtlwifi/rtl8192de/trx.h
index 4d55d0b..0dc736c 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192de/trx.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192de/trx.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as

---

### Post by LisaSimpson on 2012-01-07
Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
---
 drivers/net/wireless/rtlwifi/rtl8192cu/def.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/dm.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/dm.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/hw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/hw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/led.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/led.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/mac.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/mac.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/phy.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/phy.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/reg.h   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/rf.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/rf.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/sw.c    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/sw.h    |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/table.c |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/table.h |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/trx.c   |    2 +-
 drivers/net/wireless/rtlwifi/rtl8192cu/trx.h   |    2 +-
 20 files changed, 20 insertions(+), 20 deletions(-)

diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/def.h b/drivers/net/wireless/rtlwifi/rtl8192cu/def.h
index d097efb..f916555 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/def.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/def.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/dm.c b/drivers/net/wireless/rtlwifi/rtl8192cu/dm.c
index c0016f3..6fd39ea 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/dm.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/dm.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/dm.h b/drivers/net/wireless/rtlwifi/rtl8192cu/dm.h
index 7f966c6..d947e7d 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/dm.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/dm.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c b/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c
index 51b7aa1..048d686 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/hw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/hw.h b/drivers/net/wireless/rtlwifi/rtl8192cu/hw.h
index 32f85cb..f41a3aa 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/hw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/hw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/led.c b/drivers/net/wireless/rtlwifi/rtl8192cu/led.c
index 65fd044..75a2deb 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/led.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/led.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/led.h b/drivers/net/wireless/rtlwifi/rtl8192cu/led.h
index decaee4..0f37227 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/led.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/led.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/mac.c b/drivers/net/wireless/rtlwifi/rtl8192cu/mac.c
index 060ed5f..d028f6f 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/mac.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/mac.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/mac.h b/drivers/net/wireless/rtlwifi/rtl8192cu/mac.h
index 626d88e..bf53652 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/mac.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/mac.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/phy.c b/drivers/net/wireless/rtlwifi/rtl8192cu/phy.c
index e7ea2ba..8ac3bcc 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/phy.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/phy.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/phy.h b/drivers/net/wireless/rtlwifi/rtl8192cu/phy.h
index ff81a61..42b0686 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/phy.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/phy.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/reg.h b/drivers/net/wireless/rtlwifi/rtl8192cu/reg.h
index 7f1be61..8b81465 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/reg.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/reg.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/rf.c b/drivers/net/wireless/rtlwifi/rtl8192cu/rf.c
index e132cb3..780c0d9 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/rf.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/rf.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/rf.h b/drivers/net/wireless/rtlwifi/rtl8192cu/rf.h
index 500a209..090fd33 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/rf.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/rf.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/sw.c b/drivers/net/wireless/rtlwifi/rtl8192cu/sw.c
index e6d45eb..269a725 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/sw.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/sw.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/sw.h b/drivers/net/wireless/rtlwifi/rtl8192cu/sw.h
index 43b1177..a1310ab 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/sw.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/sw.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/table.c b/drivers/net/wireless/rtlwifi/rtl8192cu/table.c
index d57ef5e..966be51 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/table.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/table.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation.
+ * Copyright(c) 2009-2012  Realtek Corporation.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/table.h b/drivers/net/wireless/rtlwifi/rtl8192cu/table.h
index c3d5cd8..4b020e9 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/table.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/table.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/trx.c b/drivers/net/wireless/rtlwifi/rtl8192cu/trx.c
index e34344e..bde3589 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/trx.c
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/trx.c
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as
diff --git a/drivers/net/wireless/rtlwifi/rtl8192cu/trx.h b/drivers/net/wireless/rtlwifi/rtl8192cu/trx.h
index 53de5f6..332b06e 100644
--- a/drivers/net/wireless/rtlwifi/rtl8192cu/trx.h
+++ b/drivers/net/wireless/rtlwifi/rtl8192cu/trx.h
@@ -1,6 +1,6 @@
 /******************************************************************************
 *
- * Copyright(c) 2009-2010  Realtek Corporation. All rights reserved.
+ * Copyright(c) 2009-2012  Realtek Corporation. All rights reserved.
 *
 * This program is free software; you can redistribute it and/or modify it
 * under the terms of version 2 of the GNU General Public License as

---

### Post by LisaSimpson on 2012-01-07
Yo no sé cuánto puede ayudar esto, pero como no soy la única persona con este problema, alguien que pueda leer y dar significado a esos códigos sería excelente para ayudarnos a los que somos más usuarios que programadores...
Un abrazo desde ya y espero que se solucione en algún momento el tema del RTL8188CE

---

### Post by euzkoarima on 2012-01-09
Lo que copiaste es una serie de patchs (parches) que arreglan algunos bugs (no se si incluyen el que te afecta).
Eso si, son parches para el código fuente, hay que tener todo el entorno de desarrollo instalado, aplicar los parches, compilar, e instalar.

Supongo que si esto anda, el tiempo que falta para que eso salga en binario (ya compilado) debería ser poco (yo esperaría a eso).

Saludos,
Eduardo

---

### Post by guillermolisi on 2012-01-12
Segun [esta nota publicada en Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=MTA0MTM"), en la version 3.3 del kernel Linux estaria solucionada la regresion que genero el problema de administracion de energia defectuosa.

---

### Post by LisaSimpson on 2012-01-13
En contacto con Larry Finger que escribe esos patch me dijo que no se aplican específicamente al 8188ce pero que teníamos que ver si alguna rutina hacía funcionar la combinación fn-f2 y para ello me pidió que probara esto:

root@patryhec-TWH:/home/patryhec# modprobe -v wmi
root@patryhec-TWH:/home/patryhec# modprobe -rv wmi
FATAL: Module wmi is in use.

ante esto me dice:
Your results indicate that wmi is loaded, and that something else is using it. That is why you could not unload it.

Please send me the output of 'lsmod'.

root@patryhec-TWH:/home/patryhec# lsmod
Module                  Size  Used by
nvram                  14413  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
arc4                   12529  2 
snd_hda_intel          33390  4 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
uvcvideo               72711  0 
mxm_wmi                12979  0 
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 mxm_wmi
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
psmouse                73882  0 
rtlwifi               110972  1 rtl8192ce
serio_raw              13166  0 
mac80211              462092  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 rtlwifi,mac80211
i915                  566827  4 
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42558  1 i915
drm                   236290  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
mei                    41480  0 
soundcore              12680  1 snd
lp                     17799  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 
root@patryhec-TWH:/home/patryhec# 

Pareciera que además de modificar el kernel hay que hacer funcionar el fn-f2 que no quiere funcionar... estamos en este punto ahora... les paso esta data por si le sirve a alguien o a alguien se le ocure algo. Llegué a esta gente a través del mailing list "linux-wireless@vger.kernel.org".

---

