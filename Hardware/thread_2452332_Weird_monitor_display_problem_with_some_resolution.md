---
title: "Weird monitor display problem with some resolutions"
date: 2020-10-20
forum: Hardware
---

### Post by hoijtink on 2020-10-20
Hi all, i need some help here :( Thank you in advance for reading it and advising on it ;)

 I have a weird problem with some of the resolutons using my Samsung TV UE500NU7100 ... it is a 4K TV. My system is a freshly installed and newly build system. Its hardware is an AORUS Pro Wifi Mini ITX board using a AMD 3400G APU with 32GB of Corsair Vengeance memory at 2633 Mhz. The motherboard has support for multiple displays, but i only have one connected, the mentioned Samsung TV using HDMI. Nothing is overclocked. A screenshot taken by LUBUNTU Tools do not show any problem, however, i have taken a photo from the TV directly to show the problem as it appears on the TV itself. I can still use the system, it is not unresponsive or anything like that, it just shows the weird problem on the TV. The problem does not appear on all flavors of Ubuntu, it does on Lubuntu and Xubuntu, but not on MX Linux. I have tested latest mainstream kernel as well, the problem remains.

But the incorrect output is only visible with 1600x???, 1300x??? and 1400x??? resolutions, higher resolutions and lower resolutions are ok.


```
product: X570 I AORUS PRO WIFI (Default string)
vendor: Gigabyte Technology Co., Ltd.
version: -CF
serial: Default string
width: 64 bits
capabilities:
    SMBIOS version 3.2.0,
    DMI version 3.2.0,
    Symmetric Multi-Processing,
    32-bit processes
configuration:
    boot: normal
    chassis: desktop
    family: X570 MB
    sku: Default string
    uuid: 1802C003-4D04-0305-5306-D20700080009


-Memory-

MemTotal    Total Memory    30822676 KiB    
MemFree    Free Memory    27217832 KiB    
MemAvailable        28097828 KiB    
Buffers        69940 KiB    
Cached        1261576 KiB    
SwapCached    Cached Swap    0 KiB    
Active        610876 KiB    
Inactive        2600952 KiB    
Active(anon)        2632 KiB    
Inactive(anon)        2009788 KiB    
Active(file)        608244 KiB    
Inactive(file)        591164 KiB    
Unevictable        80 KiB    
Mlocked        80 KiB    
SwapTotal    Virtual Memory    4095996 KiB    
SwapFree    Free Virtual Memory    4095996 KiB    
Dirty        4 KiB    
Writeback        0 KiB    
AnonPages        1880552 KiB    
Mapped        545868 KiB    
Shmem        132104 KiB    
KReclaimable        79956 KiB    
Slab        179508 KiB    
SReclaimable        79956 KiB    
SUnreclaim        99552 KiB    
KernelStack        16320 KiB    
PageTables        25388 KiB    
NFS_Unstable        0 KiB    
Bounce        0 KiB    
WritebackTmp        0 KiB    
CommitLimit        19507332 KiB    
Committed_AS        6730964 KiB    
VmallocTotal        -1 KiB    
VmallocUsed        38832 KiB    
VmallocChunk        0 KiB    
Percpu        25088 KiB    
HardwareCorrupted        0 KiB    
AnonHugePages        0 KiB    
ShmemHugePages        0 KiB    
ShmemPmdMapped        0 KiB    
FileHugePages        0 KiB    
FilePmdMapped        0 KiB    
HugePages_Total        0    
HugePages_Free        0    
HugePages_Rsvd        0    
HugePages_Surp        0    
Hugepagesize        2048 KiB    
Hugetlb        0 KiB    
DirectMap4k        329800 KiB    
DirectMap2M        3807232 KiB    
DirectMap1G        27262976 KiB    

-PCI Devices-
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Root Complex
IOMMU        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 IOMMU
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 PCIe GPP Bridge [6:0] (prog-if 00 [Normal decode])
Host bridge        : Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A (prog-if 00 [Normal decode])
SMBus        : Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
ISA bridge        : Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 0
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 1
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 2
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 3
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 4
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 5
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 6
Host bridge        : Advanced Micro Devices, Inc. [AMD] Raven/Raven2 Device 24: Function 7
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Matisse Switch Upstream (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Matisse PCIe GPP Bridge (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Matisse PCIe GPP Bridge (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Matisse PCIe GPP Bridge (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Matisse PCIe GPP Bridge (prog-if 00 [Normal decode])
PCI bridge        : Advanced Micro Devices, Inc. [AMD] Matisse PCIe GPP Bridge (prog-if 00 [Normal decode])
Ethernet controller        : Intel Corporation I211 Gigabit Network Connection (rev 03)
Network controller        : Intel Corporation Wi-Fi 6 AX200 (rev 1a)

-USB Devices-
Linux Foundation 3.0 root hub
Linux Foundation 2.0 root hub
Linux Foundation 3.0 root hub
Logitech, Inc. Unifying Receiver
Genesys Logic, Inc. Hub
USB usb keyboard
Chicony Electronics Co., Ltd wired mouse
Linux Foundation 2.0 root hub
Linux Foundation 3.0 root hub
Alcor Micro Corp. Flash Drive
Linux Foundation 2.0 root hub
Linux Foundation 3.0 root hub
Intel Corp.
Integrated Technology Express, Inc. ITE Device(8595)
Linux Foundation 2.0 root hub

-Display-
Resolution        : 1920x1080 pixels
Vendor        : The X.Org Foundation
Version        : 1.20.8
Current Display Name        : :0.0
-Monitors-
Monitor 0        : 1920x1080 pixels
-OpenGL-
Vendor        : X.Org
Renderer        : AMD RAVEN (DRM 3.39.0, 5.9.1-050901-generic, LLVM 10.0.0)
Version        : 4.6 (Compatibility Profile) Mesa 20.0.8
Direct Rendering        : Yes
-Extensions-
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
DRI3
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
Present
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
default screen number:    0

-Loaded Modules-
hid_sony
ff_memless        : Force feedback support for memoryless devices
hidp        : Bluetooth HIDP ver 1.2
ccm        : Counter with CBC MAC
rfcomm        : Bluetooth RFCOMM ver 1.11
cmac        : CMAC keyed hash algorithm
algif_hash
algif_skcipher
af_alg
bnep        : Bluetooth BNEP ver 1.3
binfmt_misc
nls_iso8859_1
btusb        : Generic Bluetooth USB driver ver 0.8
snd_hda_codec_realtek        : Realtek HD-audio codec
snd_hda_codec_generic        : Generic HD-audio codec parser
btrtl        : Bluetooth support for Realtek devices ver 0.1
ledtrig_audio        : LED trigger for audio mute control
snd_hda_codec_hdmi        : HDMI HD-audio codec
iwlmvm        : The new Intel(R) wireless AGN driver for Linux
btbcm        : Bluetooth support for Broadcom devices ver 0.1
snd_hda_intel        : Intel HDA driver
btintel        : Bluetooth support for Intel devices ver 0.1
snd_intel_dspcfg        : Intel DSP config driver
mac80211        : IEEE 802.11 subsystem
snd_hda_codec        : HDA codec core
bluetooth        : Bluetooth Core ver 2.22
snd_hda_core        : HD-audio bus
joydev        : Joystick device interfaces
input_leds        : Input -> LEDs Bridge
libarc4
ecdh_generic        : ECDH generic algorithm
ecc
edac_mce_amd        : AMD MCE decoder
snd_hwdep        : Hardware dependent layer
snd_pcm        : Midlevel PCM code for ALSA.
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
iwlwifi        : Intel(R) Wireless WiFi driver for Linux
snd_seq_midi_event        : MIDI byte <-> sequencer event coder
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq        : Advanced Linux Sound Architecture sequencer.
k10temp        : AMD Family 10h+ CPU core temperature monitor
kvm
snd_seq_device        : ALSA sequencer device management
snd_timer        : ALSA timer interface
cfg80211        : wireless configuration support
snd        : Advanced Linux Sound Architecture driver for soundcards.
ccp        : AMD Secure Processor driver
soundcore        : Core sound module
mac_hid
rapl
efi_pstore        : EFI variable backend for pstore
wmi_bmof        : WMI embedded Binary MOF driver
sch_fq_codel        : Fair Queue CoDel discipline
parport_pc        : PC-style parallel port driver
ppdev
lp
parport
ip_tables        : IPv4 packet filter
x_tables        : {ip,ip6,arp,eb}_tables backend module
autofs4
btrfs
blake2b_generic        : BLAKE2b generic implementation
xor
raid6_pq        : RAID6 Q-syndrome calculations
libcrc32c        : CRC32c (Castagnoli) calculations
dm_mirror        : device-mapper mirror target
dm_region_hash        : device-mapper region hash
dm_log        : device-mapper dirty region log
hid_logitech_hidpp
hid_logitech_dj
hid_generic        : HID generic driver
usbhid        : USB HID core driver
hid
uas
usb_storage        : USB Mass Storage driver for Linux
amdgpu        : AMD GPU
iommu_v2
gpu_sched        : DRM GPU scheduler
ttm        : TTM memory manager subsystem (for DRM device)
drm_kms_helper        : DRM KMS helper
syscopyarea        : Generic copyarea (sys-to-sys)
sysfillrect        : Generic fill rectangle (sys-to-sys)
sysimgblt        : 1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)
crct10dif_pclmul        : T10 DIF CRC calculation accelerated with PCLMULQDQ.
crc32_pclmul
fb_sys_fops        : Generic file read (fb in system RAM)
ghash_clmulni_intel        : GHASH hash function, accelerated by PCLMULQDQ-NI
cec        : Device node registration for cec drivers
aesni_intel        : Rijndael (AES) Cipher Algorithm, Intel AES-NI instructions optimized
rc_core
crypto_simd
cryptd        : Software async crypto daemon
glue_helper
igb        : Intel(R) Gigabit Ethernet Network Driver
drm        : DRM shared core routines
dca
i2c_piix4        : PIIX4 SMBus driver
ahci        : AHCI SATA low-level driver
xhci_pci        : xHCI PCI Host Controller Driver
i2c_algo_bit        : I2C-Bus bit-banging algorithm
xhci_pci_renesas
libahci        : Common AHCI SATA low-level routines
wmi        : ACPI-WMI Mapping Driver
video        : ACPI Video Driver
```

---

### Post by hoijtink on 2020-10-21
I was able to fix this by doing the following:

In Synaptic removed/added the packages:

    xserver-xorg-video-vesa       (Install)
    xserver-xorg-video-radeon   (Mark for Complete Removal)
    xserver-xorg-video-amdgpu (Mark for Complete Removal)

Reboot In Synaptic removed/added the packages:

    xserver-xorg-video-radeon
    xserver-xorg-video-radeon-hwe-18.04

The problem appeared to have been caused(?) by the 'xserver-xorg-video-amdgpu' package. _I am unsure what this package does or if it is needed at all, maybe someone can clarify._

As a side effect of doing these steps new/different display resolutions with according refresh rates have become available, some of which work, and some of which don't (black screen /unsupported message on tv). One weird one that actually works is 1440x810 119.9Hz ... notice the refresh rate, but the display panel on TVs can vary even within the same model. So that mode might not work on other NU7100 TVs, and others might that do might not work here.

I also tried the shell command 'xrandr -q' which should query and list the supported modes, but some of the ones listed by that tool, like 2880x1620 59.96Hz in my, failed anyway when i tried to apply to test. So i guess this is not entirely reliable too.

_Maybe there is a gui-tool to easily create/modify Display profiles/settings ?_ For now, i hope this helps others troubleshoot Display problems.

As i side note, this all started out because i knew from different distribution that the 1600x900 60Hz Display setting should work without problems, then ran into the weird screen, and tried to fix that. The reason for that that this is a 55" screen, so the text is quite unreadable at high resolutions and the 1600x900 resolution was most appealing to me for readability of text. xrandr says something about scaling, but as i don't know how that works or how it is to be (permanently) implemented i left it at that. _Maybe someone can explain :)_ This journey was not meant to make non-supported resolutions work on the TV   :popcorn:

---

### Post by hoijtink on 2020-11-01
Continuing this ordeal:

The login screen was still in 4K resolution and thus being too small to read without a microscope. Browsing all over the internet, Ubuntu/Linux forums, and what not while being guided to sddm, Xorg, and whatever else i came across, i finally was able to solve this problem. An exact answer was nowhere to be found, but i ended up reading the last post by 'intelligent_cat' o [https://www.reddit.com/r/kde/comments/5th4po/sddm_looks_tiny_on_login_on_hidpi_screen/](https://www.reddit.com/r/kde/comments/5th4po/sddm_looks_tiny_on_login_on_hidpi_screen/), which gave me a clue on how to fix this.

As he, i created/edited '**/etc/X11/xorg.conf.d/90-monitor.conf**' and it looks like this:

```

Section "Monitor"
     Identifier      "<default monitor>"
     Option "PreferredMode" "1400x1050"
EndSection
```


I choose that resolution because its highest refresh rate (70 Hz) was working on my 4K TV, as it seems to default to that. Other resolutions, like the one i liked 1680x1050 caused a 'Not supported' message on my 4K TV, as said, because the refresh rate could not be handled. In your case, i suggest switching resolutions using the Display tool in Settings until you find one that works without altering the refresh rate, and use that as your setting. It is only used for the login screen, and after that the started session will reset the screen resolution to whatever you set it to in the Display tool from Settings. This was the easiest solution i could find. 

If anything goes wrong, use CTRL+ALT+F2 to open a terminal window, that will allow you to login and alter/delete the created config file after which you can reboot.

I hope this helps others too.

I still would like to have human readable boot/kernal messages, but i don't think there is an easy way to change that to a lower resolution, and from what i have seen on forums so far people either don't know or don't care to answer on that, besides commenting on reading the syslog after boot. But i personally think the boot logo just hides things that might go wrong during boot and/or cause slow bootup, so i rather like seeing the messages during boot. I appreciate to be proven wrong on that ;)

---

### Post by guiverc on 2020-11-01
Well done, and thanks for sharing.

(*I concur on the boot logo hiding problems, and I don't mind the boot messages, but yeah I'm told they're seen as scary for most users.*)

---

### Post by hoijtink on 2020-11-01
Thanks,

And to continue....

After more and more and more searching, got pointed to Kernel Mode Setting (KMS), UEFI / EDID BOOT, and found [https://www.suse.com/support/kb/doc/?id=000018747](https://www.suse.com/support/kb/doc/?id=000018747) ... 

I added the line, but it did not solve the problem. However, if you run into boot problems you can add nomodeset to the linux startup from the Grub menu (press e to edit), this will disable the resoluton switching by the kernel allowing you to read the messages. This however also disables regular resolutions, so this won't be something you want to do permanently.

I someone has comments on a more usefull way to change the kernel parameters so that is accepts the video= option?

---

### Post by hoijtink on 2020-11-01
**READ CAREFULLY BEFORE DOING ANYTHING**

Finally found the solution i think, i tried several things, but at least it works for me now... but be carefull here !

Using GRUB-CUSTOMIZER (editing config files directly is a bit tricky) i changed the line at the bottom starting with 'linux    '

The 'nosplash', 'modeset=0', and 'video=800x600' were changed by me. You can use a higher resolution if you want, 1024x768 or 1280x1024 might be good candidates, which worked too for me, if you monitor supports those. The 'nosplash' hides the graphic boot-logo screen so you can see the messages during bootup. The modeset=0 seems to prevent the KMS to switch resolutions, but modeset=1 also works on my end, any higher seems to be ignored. I am unsure what exactly the different modesets are supposed to be. **Do not touch anything else though, cause you might end up with an unbootable system.** The '/boot/vmlinuz*' is the kernel, and you are probably using a different version. the 'root=* ro' refers to your root filesystem. CERTAINLY DO NOT CHANGE THOSE....

```

*linux    ..... *  **nosplash modeset=0  video=800x600** *....*

```

I needed **both** the **modeset** and the **video** parameter to get this to work correctly. So now my system boots the desired resolution with human reable text on a 4K HD TV, and also when i use CTRL+ALT+F2 to open a shell it uses the same human readable resolution. If you like the bootup logo to be displayed, just keep splash instead of nosplash, then you can press ESC during the bootup to display the messages if you think anything is wrong. It will still show the resulotion you set.

Hoping this helps someone....

---

### Post by hoijtink on 2020-11-15
After upgrading to 20.04.1 the resolution of the Login page was wrong again. I managed to force it by editing '**/usr/share/sddm/scripts/Xsetup**' and adding:

```

# Use fixed resolution for Greeter/Login screen
/usr/bin/xrandr -s 1280x1024

```

---

### Post by CatKiller on 2020-11-15
> **hoijtink said:**
> The modeset=0 seems to prevent the KMS to switch resolutions, but modeset=1 also works on my end, any higher seems to be ignored. I am unsure what exactly the different modesets are supposed to be.

That setting turns kernel mode setting on or off.

---

