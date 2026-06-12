---
title: "Lenovo Y700"
date: 2016-12-30
forum: Hardware
---

### Post by uberalex88 on 2016-12-30
I was using a Dell Inspiron Laptop and with the hardware in there, pretty much everything including the fans were detected and usable.  I got this computer as a Christmas present and I am testing compatibility of Ubuntu 16.10 on this laptop.  Drivers didn't seem like a problem.  Bluetooth is inaccessible at the moment but i don't need that right now.  However when I was playing a game, my temps on some components was fairly close to 180 and i didn't feel any airflow coming from the fans.  
So I installed hard info to give a look at if the laptop sensors were picking up the fans at all.  Under sensors I didn't see anything.

So I did an export of the hardinfo for this laptop.

```


Computer
********


Summary
-------

-Computer-
Processor        : 8x Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz
Memory        : 7998MB (1470MB used)
Operating System        : Ubuntu 16.10
User Name        : alex (Alex)
Date/Time        : Fri 30 Dec 2016 03:52:24 PM CST
-Display-
Resolution        : 1360x768 pixels
OpenGL Renderer        : GeForce GTX 960M/PCIe/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 Video Bus
 ETPS/2 Elantech Touchpad
 Ideapad extra buttons
 HDA Intel PCH Mic
 HDA Intel PCH Headphone
 HDA Intel PCH HDMI/DP,pcm        : 3=
 HDA Intel PCH HDMI/DP,pcm        : 7=
 HDA Intel PCH HDMI/DP,pcm        : 8=
 Lenovo EasyCamera
 PixArt USB Optical Mouse
-Printers-
No printers found
-SCSI Disks-
ATA ST1000LM035-1RK1

Operating System
----------------

-Version-
Kernel        : Linux 4.8.0-32-generic (x86_64)
Compiled        : #34-Ubuntu SMP Tue Dec 13 14:30:43 UTC 2016
C Library        : GNU C Library version (Ubuntu GLIBC 2.24-3ubuntu2) 2.24 (unstable)
Default C Compiler        : GNU C Compiler version 6.2.0 20161005 (Ubuntu 6.2.0-5ubuntu12) 
Distribution        : Ubuntu 16.10
-Current Session-
Computer Name        : GamerAlex-LPT
User Name        : alex (Alex)
Home Directory        : /home/alex
Desktop Environment        : Unity (ubuntu)
-Misc-
Uptime        : 8 hours, 26 minutes
Load Average        : 0.11, 0.27, 0.30

Kernel Modules
--------------

-Loaded Modules-
binfmt_misc
rfcomm        : Bluetooth RFCOMM ver 1.11
bbswitch        : Toggle the discrete graphics card
cmac        : CMAC keyed hash algorithm
bnep        : Bluetooth BNEP ver 1.3
nvidia_uvm
nls_iso8859_1
arc4        : ARC4 Cipher Algorithm
iwlmvm        : The new Intel(R) wireless AGN driver for Linux
mac80211        : IEEE 802.11 subsystem
uvcvideo        : USB Video Class driver
videobuf2_vmalloc        : vmalloc memory handling routines for videobuf2
videobuf2_memops        : common memory handling routines for videobuf2
videobuf2_v4l2        : Driver helper framework for Video for Linux 2
videobuf2_core        : Media buffer core framework
videodev        : Device registrar for Video4Linux drivers v2
media        : Device node registration for media drivers
snd_hda_codec_hdmi        : HDMI HD-audio codec
snd_hda_codec_realtek        : Realtek HD-audio codec
snd_hda_codec_generic        : Generic HD-audio codec parser
snd_hda_intel        : Intel HDA driver
snd_hda_codec        : HDA codec core
snd_hda_core        : HD-audio bus
snd_hwdep        : Hardware dependent layer
snd_pcm        : Midlevel PCM code for ALSA.
intel_rapl        : Driver for Intel RAPL (Running Average Power Limit)
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
x86_pkg_temp_thermal        : X86 PKG TEMP Thermal Driver
kvm_intel
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_seq_device        : ALSA sequencer device management
kvm
hci_uart        : Bluetooth HCI UART driver ver 2.3
iwlwifi        : Intel(R) Wireless WiFi driver for Linux
btusb        : Generic Bluetooth USB driver ver 0.8
btrtl        : Bluetooth support for Realtek devices ver 0.1
snd_timer        : ALSA timer interface
irqbypass        : IRQ bypass manager utility module
btqca        : Bluetooth support for Qualcomm Atheros family ver 0.1
btbcm        : Bluetooth support for Broadcom devices ver 0.1
btintel        : Bluetooth support for Intel devices ver 0.1
crct10dif_pclmul        : T10 DIF CRC calculation accelerated with PCLMULQDQ.
crc32_pclmul
bluetooth        : Bluetooth Core ver 2.21
cfg80211        : wireless configuration support
ghash_clmulni_intel        : GHASH Message Digest Algorithm, acclerated by PCLMULQDQ-NI
aesni_intel        : Rijndael (AES) Cipher Algorithm, Intel AES-NI instructions optimized
cdc_acm        : USB Abstract Control Model driver for USB modems and ISDN adapters
mei_me        : Intel(R) Management Engine Interface
snd        : Advanced Linux Sound Architecture driver for soundcards.
aes_x86_64        : Rijndael (AES) Cipher Algorithm, asm optimized
lrw        : LRW block cipher mode
glue_helper
ablk_helper
soundcore        : Core sound module
cryptd        : Software async crypto daemon
intel_cstate
mei        : Intel(R) Management Engine Interface
input_leds        : Input -&gt; LEDs Bridge
joydev        : Joystick device interfaces
intel_rapl_perf
ideapad_laptop        : IdeaPad ACPI Extras
shpchp        : Standard Hot Plug PCI Controller Driver
tpm_crb        : TPM2 Driver
mac_hid
sparse_keymap        : Generic support for sparse keymaps
intel_lpss_acpi        : Intel LPSS ACPI driver
intel_lpss        : Intel LPSS core driver
serio_raw        : Raw serio driver
wmi        : ACPI-WMI Mapping Driver
acpi_pad        : ACPI Processor Aggregator Driver
coretemp        : Intel Core temperature monitor
parport_pc        : PC-style parallel port driver
ppdev
lp
parport
ip_tables        : IPv4 packet filter
x_tables        : {ip,ip6,arp,eb}_tables backend module
autofs4
hid_generic        : HID generic driver
usbhid        : USB HID core driver
i915        : Intel Graphics
nvidia_drm
nvidia_modeset
psmouse        : PS/2 mouse driver
i2c_algo_bit        : I2C-Bus bit-banging algorithm
drm_kms_helper        : DRM KMS helper
nvme
nvme_core
syscopyarea        : Generic copyarea (sys-to-sys)
nvidia
sysfillrect        : Generic fill rectangle (sys-to-sys)
sysimgblt        : 1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)
r8169        : RealTek RTL-8169 Gigabit Ethernet driver
sdhci_pci        : Secure Digital Host Controller Interface PCI driver
fb_sys_fops        : Generic file read (fb in system RAM)
mii        : MII hardware support library
sdhci        : Secure Digital Host Controller Interface core driver
drm        : DRM shared core routines
ahci        : AHCI SATA low-level driver
libahci        : Common AHCI SATA low-level routines
pinctrl_sunrisepoint        : Intel Sunrisepoint PCH pinctrl/GPIO driver
video        : ACPI Video Driver
i2c_hid        : HID over I2C core driver
pinctrl_intel        : Intel pinctrl/GPIO core driver
hid
fjes        : FUJITSU Extended Socket Network Device Driver

Boots
-----

-Boots-
Fri Dec 30 07:25        : 44..8.0-32-generic|still
Thu Dec 29 19:12        : 44..8.0-22-generic|-
Thu Dec 29 17:47        : 44..8.0-22-generic|-
Thu Dec 29 14:42        : 44..8.0-22-generic|-
Thu Dec 29 14:11        : 44..8.0-22-generic|-

Languages
---------

-Available Languages-
en_AG        : English language locale for Antigua and Barbuda
en_AG.utf8        : English language locale for Antigua and Barbuda
en_AU.utf8        : English locale for Australia
en_BW.utf8        : English locale for Botswana
en_CA.utf8        : English locale for Canada
en_DK.utf8        : English locale for Denmark
en_GB.utf8        : English locale for Britain
en_HK.utf8        : English locale for Hong Kong
en_IE.utf8        : English locale for Ireland
en_IL        : English locale for Israel
en_IL.utf8        : English locale for Israel
en_IN        : English language locale for India
en_IN.utf8        : English language locale for India
en_NG        : English locale for Nigeria
en_NG.utf8        : English locale for Nigeria
en_NZ.utf8        : English locale for New Zealand
en_PH.utf8        : English language locale for Philippines
en_SG.utf8        : English language locale for Singapore
en_US.utf8        : English locale for the USA
en_ZA.utf8        : English locale for South Africa
en_ZM        : English locale for Zambia
en_ZM.utf8        : English locale for Zambia
en_ZW.utf8        : English locale for Zimbabwe

Filesystems
-----------

-Mounted File Systems-
udev    /dev    0.00 % (3.8 GiB of 3.8 GiB)    
tmpfs    /run    1.26 % (771.3 MiB of 781.1 MiB)    
/dev/sda4    /    15.29 % (373.5 GiB of 440.9 GiB)    
tmpfs    /dev/shm    0.00 % (3.8 GiB of 3.8 GiB)    
tmpfs    /run/lock    0.08 % (5.0 MiB of 5.0 MiB)    
tmpfs    /sys/fs/cgroup    0.00 % (3.8 GiB of 3.8 GiB)    
/dev/nvme0n1p1    /boot/efi    12.37 % (224.3 MiB of 256.0 MiB)    
tmpfs    /run/user/1000    0.02 % (780.9 MiB of 781.1 MiB)    

Display
-------

-Display-
Resolution        : 1360x768 pixels
Vendor        : The X.Org Foundation
Version        : 1.18.4
-Monitors-
Monitor 0        : 1360x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
NV-CONTROL
NV-GLX
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
-OpenGL-
Vendor        : NVIDIA Corporation
Renderer        : GeForce GTX 960M/PCIe/SSE2
Version        : 4.5.0 NVIDIA 367.57
Direct Rendering        : Yes

Environment Variables
---------------------

-Environment Variables-
CLUTTER_IM_MODULE        : xim
XDG_GREETER_DATA_DIR        : /var/lib/lightdm-data/alex
TERM        : xterm-256color
SHELL        : /bin/bash
VTE_VERSION        : 4402
SSH_AGENT_LAUNCHER        : gnome-keyring
QT_LINUX_ACCESSIBILITY_ALWAYS_ON        : 1
WINDOWID        : 65011718
UPSTART_SESSION        : unix:abstract=/com/ubuntu/upstart-session/1000/12311
GTK_MODULES        : gail:atk-bridge
USER        : alex
LS_COLORS        : rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
QT_ACCESSIBILITY        : 1
XDG_SESSION_PATH        : /org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH        : /org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK        : /run/user/1000/keyring/ssh
DEFAULTS_PATH        : /usr/share/gconf/ubuntu.default.path
XDG_CONFIG_DIRS        : /etc/xdg/xdg-ubuntu:/usr/share/upstart/systemd-session:/usr/share/upstart/xdg:/etc/xdg
PATH        : /home/alex/bin:/home/alex/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
DESKTOP_SESSION        : ubuntu
QT_IM_MODULE        : ibus
XDG_SESSION_TYPE        : x11
PWD        : /home/alex
XMODIFIERS        : @im=ibus
LANG        : en_US.UTF-8
GDM_LANG        : en_US
MANDATORY_PATH        : /usr/share/gconf/ubuntu.mandatory.path
IM_CONFIG_PHASE        : 1
COMPIZ_CONFIG_PROFILE        : ubuntu
GDMSESSION        : ubuntu
GTK2_MODULES        : overlay-scrollbar
HOME        : /home/alex
SHLVL        : 2
LANGUAGE        : en_US
GNOME_DESKTOP_SESSION_ID        : this-is-deprecated
XDG_SESSION_DESKTOP        : ubuntu
LOGNAME        : alex
XDG_DATA_DIRS        : /usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
QT4_IM_MODULE        : xim
DBUS_SESSION_BUS_ADDRESS        : unix:path=/run/user/1000/bus
LESSOPEN        : | /usr/bin/lesspipe %s
MANAGERPID        : 12221
JOURNAL_STREAM        : 8:79219
XDG_RUNTIME_DIR        : /run/user/1000
DISPLAY        : :0
XDG_CURRENT_DESKTOP        : Unity
GTK_IM_MODULE        : ibus
LESSCLOSE        : /usr/bin/lesspipe %s %s
XAUTHORITY        : /home/alex/.Xauthority
COLORTERM        : truecolor
_        : /usr/bin/hardinfo

Users
-----

-Users-
root        : root
daemon        : daemon
bin        : bin
sys        : sys
sync        : sync
games        : games
man        : man
lp        : lp
mail        : mail
news        : news
uucp        : uucp
proxy        : proxy
www-data        : www-data
backup        : backup
list        : Mailing List Manager
irc        : ircd
gnats        : Gnats Bug-Reporting System (admin)
nobody        : nobody
systemd-timesync        : systemd Time Synchronization
systemd-network        : systemd Network Management
systemd-resolve        : systemd Resolver
systemd-bus-proxy        : systemd Bus Proxy
syslog
_apt
messagebus
usermetrics        : User Metrics
uuidd
rtkit        : RealtimeKit
avahi-autoipd        : Avahi autoip daemon
dnsmasq        : dnsmasq
usbmux        : usbmux daemon
lightdm        : Light Display Manager
whoopsie
geoclue
kernoops        : Kernel Oops Tracking Daemon
speech-dispatcher        : Speech Dispatcher
nm-openvpn        : NetworkManager OpenVPN
clickpkg
avahi        : Avahi mDNS daemon
pulse        : PulseAudio daemon
colord        : colord colour management daemon
saned
hplip        : HPLIP system user
alex        : Alex
easytether        : easytether
nvidia-persistenced        : NVIDIA Persistence Daemon

Devices
*******


Processor
---------

-Processors-
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 899.94MHz
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 899.94MHz
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 900.73MHz
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 899.94MHz
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 1155.43MHz
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 903.43MHz
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 899.94MHz
Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz        : 899.94MHz

Memory
------

-Memory-
Total Memory        : 7998196 kB
Free Memory        : 5778452 kB
MemAvailable        : 6456268 kB
Buffers        : 52512 kB
Cached        : 835048 kB
Cached Swap        : 0 kB
Active        : 1415564 kB
Inactive        : 520564 kB
Active(anon)        : 978768 kB
Inactive(anon)        : 87500 kB
Active(file)        : 436796 kB
Inactive(file)        : 433064 kB
Unevictable        : 32 kB
Mlocked        : 32 kB
Virtual Memory        : 7812092 kB
Free Virtual Memory        : 7812092 kB
Dirty        : 196 kB
Writeback        : 0 kB
AnonPages        : 1003944 kB
Mapped        : 320616 kB
Shmem        : 17680 kB
Slab        : 123188 kB
SReclaimable        : 66800 kB
SUnreclaim        : 56388 kB
KernelStack        : 9424 kB
PageTables        : 33088 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 11811188 kB
Committed_AS        : 4289292 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 0 kB
VmallocChunk        : 0 kB
HardwareCorrupted        : 0 kB
AnonHugePages        : 169984 kB
ShmemHugePages        : 0 kB
ShmemPmdMapped        : 0 kB
CmaTotal        : 0 kB
CmaFree        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 219408 kB
DirectMap2M        : 4847616 kB
DirectMap1G        : 4194304 kB

PCI Devices
-----------

-PCI Devices-
Host bridge        : Intel Corporation Skylake Host Bridge/DRAM Registers (rev 07)
PCI bridge        : Intel Corporation Skylake PCIe Controller (x16) (rev 07) (prog-if 00 [Normal decode])
VGA compatible controller        : Intel Corporation HD Graphics 530 (rev 06) (prog-if 00 [VGA controller])
USB controller        : Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31) (prog-if 30 [XHCI])
Communication controller        : Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
SATA controller        : Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31) (prog-if 01 [AHCI 1.0])
PCI bridge        : Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1) (prog-if 00 [Normal decode])
ISA bridge        : Intel Corporation Sunrise Point-H LPC Controller (rev 31)
Memory controller        : Intel Corporation Sunrise Point-H PMC (rev 31)
Audio device        : Intel Corporation Sunrise Point-H HD Audio (rev 31)
SMBus        : Intel Corporation Sunrise Point-H SMBus (rev 31)
3D controller        : NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
SD Host controller        : O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01) (prog-if 01)
Network controller        : Intel Corporation Wireless 8260 (rev 3a)
Ethernet controller        : Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
Non-Volatile memory controller        : Samsung Electronics Co Ltd Device a804 (prog-if 02 [NVM Express])

USB Devices
-----------


Printers
--------

-Printers-
No printers found

Battery
-------

-No batteries-
No batteries found on this system

Sensors
-------

-Cooling Fans-
-Temperatures-
-Voltage Values-

Input Devices
-------------

-Input Devices-
 Lid Switch
 Power Button
 Sleep Button
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 Video Bus
 ETPS/2 Elantech Touchpad
 Ideapad extra buttons
 HDA Intel PCH Mic
 HDA Intel PCH Headphone
 HDA Intel PCH HDMI/DP,pcm        : 3=
 HDA Intel PCH HDMI/DP,pcm        : 7=
 HDA Intel PCH HDMI/DP,pcm        : 8=
 Lenovo EasyCamera
 PixArt USB Optical Mouse

Storage
-------

-SCSI Disks-
ATA ST1000LM035-1RK1

DMI
---

-BIOS-
Date        : 09/19/2016
Vendor        : LENOVO
Version        : CDCN53WW
-Board-
Name        : Allsparks 5A
Vendor        : LENOVO

Resources
---------

-I/O Ports-
<tt>0000-0000 </tt>        : PCI Bus 0000:00
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>0000-0000 </tt>        : PCI Bus 0000:00
<tt>0000-0000 </tt>        : PCI Bus 0000:00
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>      0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>  0000-0000 </tt>        : pnp 00:02
<tt>    0000-0000 </tt>        : pnp 00:02
<tt>      0000-0000 </tt>        : pnp 00:02
-Memory-
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>      00000000-00000000 </tt>        : mmc0
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>      00000000-00000000 </tt>        : mmc0
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>      00000000-00000000 </tt>        : mmc0
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>      00000000-00000000 </tt>        : mmc0
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>      00000000-00000000 </tt>        : mmc0
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>      00000000-00000000 </tt>        : mmc0
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>    00000000-00000000 </tt>        : PNP0103:00
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>  00000000-00000000 </tt>        : Kernel bss
<tt>00000000-00000000 </tt>        : RAM buffer
-DMA-
<tt> 4</tt>        : cascade

Network
*******


Interfaces
----------

-Network Interfaces-
lo    1.13MiB    1.13MiB    127.0.0.1    
tun-easytether    0.40MiB    0.03MiB    192.168.117.0    
enp9s0    0.00MiB    0.00MiB        
wlp8s0    0.00MiB    0.00MiB        

IP Connections
--------------

-Connections-
127.0.0.53:53        0.0.0.0:*    udp    
127.0.0.1:631    LISTEN    0.0.0.0:*    tcp    
0.0.0.0:5355        0.0.0.0:*    udp    
192.168.117.0:49192    ESTABLISHED    94.125.182.252:6697    tcp    
192.168.117.0:47672    ESTABLISHED    74.125.232.241:443    tcp    
192.168.117.0:52484    ESTABLISHED    74.125.21.120:443    tcp    
::1:631    LISTEN    :::*    tcp6    
:::5355        :::*    udp6    
0.0.0.0:631        0.0.0.0:*    udp    
0.0.0.0:5353        0.0.0.0:*    udp    
0.0.0.0:5355        0.0.0.0:*    udp    
0.0.0.0:36600        0.0.0.0:*    udp    
127.0.0.53:53        0.0.0.0:*    udp    
:::5353        :::*    udp6    
:::5355        :::*    udp6    
:::40695        :::*    udp6    

Routing Table
-------------

-IP routing table-
0.0.0.0 / 192.168.117.1    0.0.0.0    UG    tun-easytether    
169.254.0.0 / 0.0.0.0    255.255.0.0    U    tun-easytether    
192.168.117.0 / 0.0.0.0    255.255.255.254    U    tun-easytether    

ARP Table
---------

-ARP Table-

DNS Servers
-----------

-Name servers-
192.168.117.1
127.0.0.53

Statistics
----------

-IP-
17417        : Incoming packets delivered
0        : Incoming packets discarded
0        : Incoming packets discarded
17417        : Incoming packets delivered
16352        : Requests sent out
80        : Outgoing packets dropped
19        : Dropped because of missing route
-ICMP-
160        : ICMP messages received
0        : ICMP messages failed
161        : ICMP messages sent
0        : ICMP messages failed
-ICMPMSG-
-TCP-
10019        : Active connections openings
0        : Bad segments received.
9730        : Failed connection attempts
13        : Connection resets received
3        : Connections established
26446        : Segments received
25392        : Segments send out
2        : Segments retransmited
0        : Bad segments received.
9813        : Resets sent
-UDP-
225        : Packets received
161        : Packets to unknown port received.
0        : Send buffer errors
397        : Packets sent
0        : Send buffer errors
0        : Send buffer errors
-UDPLITE-
-TCPEXT-
116        : TCP sockets finished time wait in fast timer
188        : Delayed acks sent
3857        : Packet headers predicted
920        : Acknowledgments not containing data payload received
1190        : Predicted acknowledgments
2        : Congestion windows recovered without slow start after partial ack
1        : Connections reset due to early user close
-IPEXT-

Shared Directories
------------------

-SAMBA-
Cannot open /etc/samba/smb.conf
-NFS-

Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>    900 MHz    1.331    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    26.1876862    
PowerPC 740/750 (280.00MHz)    (null)    172.816713    

CPU CryptoHash
--------------

-CPU CryptoHash-
<big><b>This Machine</b></big>    900 MHz    871.837    

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>    900 MHz    1.412    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    8.1375674    
PowerPC 740/750 (280.00MHz)    (null)    58.07682    

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>    900 MHz    0.457    

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>    900 MHz    0.753    

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>    900 MHz    3.063    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    40.8816714    
PowerPC 740/750 (280.00MHz)    (null)    161.312647    

```

If someone could glance this over and give me an idea on how to configure Ubuntu to use the fans, I would appreciate it.

---

### Post by uberalex88 on 2017-01-03
Okay so i did some digging. It seems that the current linux insttall cannot manage the fans so BIOS is handling the fans.  The fan speed is very minimal at best.  When I got the laptop, in Windows i had an option to turn on "Extreme Cooling" before going into a game.  I'm how to do something similar under ubuntu.

---

### Post by uberalex88 on 2017-01-07
Okay if anyone gets a Lenovo Ideapad and the fan cooling isnt working that great, go back into windows and reflash the bios.  Some Ideapad machines also have a bios configured specific for Linux use and others will have different versions to choose from.  What I ended up doing was trying some other bios versions that Lenovo provides. Also certain Nvidia drivers that I have tried ends up causing the GPU to overheat more than others.  So if the version you are using is causing too much heat, use a different version.

---

### Post by uberalex88 on 2017-01-07
Another thing that i was reading about people who got the newer Idepad laptops is that their battery would not completely charge.  This is due to that when you first got the computer, it is recommended for the laptop to only charge to about 60% so when you are using it for gaming and leaving it plugged in for extended periods of time, it won't ruin the battery life of the laptop.  This is configured within the Lenovo Settings app in Windows by going to Power -> Conservation Mode.  Honestly it would have been nice if Lenovo made access to this setting within the BIOS as well but the didn't.

---

### Post by uberalex88 on 2017-01-09
Okay so if you have an Lenovo Ideapad it is a known issue that in Linux the that the PCIe harddrive that it comes with gets really hot.  I have looked at other linux distros and also tried the latest 4.91 kernels and there really hasn't been a fix yet for this.  So what I did is I went to go get a precision kit since I didn't have my other one to open up the laptop.  For help with this I found a video for the Y700 that was the most helpful and after I had it opened I remove the hard drive in the bottom left.  Since with my purchase it already had a SSD already installed in the laptop so I am just using the one SSD now that it came with.  

I highly recommend removing this hard drive if your Ideapad is overheating as it can later lead to completely wrecking the hard drive and possibly the laptop.

I also recommend getting some sort of cooling pad for this laptop.  Even something as simple as the one I'm using is a good start. 

Update:  Another thing I have done is I went to the upstream kernel page and installed the 4.9.1 kernel.  I got that running with the NVIDIA 375 driver (by using the nvidia ppa)

---

### Post by uberalex88 on 2017-01-11
So I had some free time today and I popped the PCIe hard drive back into the laptop to do some tests.  I ended up finding a setup where I can utilize the 1GB drive and 128 GB SSD that was included in the laptop.  I have a script running that checks the hard drive temp periodically and I copied WoW (40 GB) from my external to the hard drive . installed some stuff while that was going, opened up libre office while that was happening, and even ran GIMP with some large images.  The temp has stayed between 107 F and 111F and the laptop to the touch is cooler.

Heres how I allocated the disks.

[[IMG]http://i.imgur.com/YiKJiqhm.png[/IMG]log]("http://imgur.com/YiKJiqh")

**UPDATE: ** Okay I let my computer IDLE and i took a nap just to see what happens on my temp monitor.  It seems the highest temp the hard drives go so far is 45 C which is warm but isn't as hot as when I first was setting up Ubuntu 16.10 on this laptop.
to 
**WHAT I DID:**
The Lenovo Ideapad Y700-15ISK i got came with the OEM product key for Windows 10 integrated into the the computer.  So....
[LIST=1]
[*]I had my Windows 10 downloaded through Microsoft's website and used WinUSB (fork) to put it onto a USB 
[*]I verified that my primary drive was using the GPT using Gparted from the Ubuntu 16.10 and wiped iti 
[*]I went into BIOS (F2 at startup) and I went to the last tab to load the defaults for EUFI.  I went ahead and let it turn secure boot back on. 
[*]I then booted the Windows install and click custom and then click next to let the Windows installer create the partitions automatically 
[*]After install I went into BIOS and enabled the feature for BIOS flashing to previous BIOS. 
[*] Within Windows iI went to Lenovo website and downloaded both BIOS options. 
[*]I first flashed the CDCN35WW (then tested under the Ubuntu install) then I flashed the CDCN53WW BIOS. 
[*]When I got back into Windows  I used disk management to shrink the Windows partition. (Right click+START -> Disk  Management) I made Windows only 30 GB on my 128 SSD. 
[*]I then went back into BIOS and turned secure boot off and on that same page turned off Intel Platform Trust Technology. 
[*]Then I booted the Ubuntu 16.10 installer, connected to the Internet, clicked install and checked both installing updates while installing and for the hardware drivers, flash, etc... 
[*]I clicked manual installation 
[*]On the 128 SSD, i created a 8000 M swap. 
[*]On the same SSD, I created a EXT4 partition, left the size alone, and mounted that to / 
[*]On the other hard drive, I selected it and clicked new partition table. 
[*]Then on that drive, I created a EXT4 partition, left the size alone, and mounted that to /home 
[*]I then changed GRUB to install to the partition where I mounted to / 
[*]I did the rest of the install as I normally would. 
[*]After install, i changed the BIOS UFI boot order to boot Ubuntu 
[*]In Ubuntu I ran my updates and installed drivers. 
[*]I then installed lm-sensors (sudo apt install lm-sensors) and then setup (sudo sensors-detect) and  then said yes to everything. 
[/LIST]

I guess when I first installed Ubuntu 16.10 on here, wiping the drives clean was a bad idea unlike when I installed Ubuntu on the Dell Insprion 16.  So with this laptop, I am leaving Windows on to maintain the BIOS and also it allows me to use Lenovo Settings to manage some BIOS features as well.  So with that being said, hardware compatibility with 16.10 works better than when I attempted to do an install in 16.04.1.

---

### Post by mörgæs on 2017-01-16
Thanks for the guide. 
If you post a brief summary in the [compatibility list]("https://ubuntuforums.org/showthread.php?t=1543006") (possibly linking to this thread) there is a better chance that people will find it.

---

### Post by uberalex88 on 2017-01-17
Yes, that is more so useful for people that ended up wiping all of the partitions / changing the partition table.  I also found out in the latest kernel for Ubuntu 16.10, it actually loads an ideapad kernel module in conjunction with the thinkpad kernel module which I didn't see get loaded on Ubuntu 16.04.1.  More than likely when the devs use the newer stable kernel in the .2, it will load the kernel module.

Another thing I'm looking at tonight before I do anything is what happens when the install is only on the PCIe drive.

---

### Post by uberalex88 on 2017-01-18
Okay with Ubuntu 16.10 completely using the PCIe drive, i have let the temperature script run for a while, while I engaged in different activities on the laptop.  The only thing I haven't really done is open a 3D game (which will naturally put out more heat anyways).

With general use of like copying files, opening programs, saving files, and copying large files onto the Ubuntu installation, temperature for the drives fluncuate between 39 C and 45 C between both hard drives.

However what I did differently is switch from using laptop-mode-tools to using TLP with its default configuration after install and it allowed the drives to get cooler WITHOUT using an external fan.

[B]Point of This Thread

[/B]When I first got this Lenovo Y700-15ISK, when i , tas testing Ubuntu I ended up wiping my drives and installed Ubuntu.  When I first got it installed, the part of the laptop where the PCIe drive was got way to warm for my comfort so when I went onto the Internet, I was reading how people with this laptop were experiencing problems with the hard drives connected to the PCIe slot on this laptop getting extremely hot.  If you only have one drive in this laptop and you can only install to the PCIe drive, i guess thess temperature ranges should be manageable considering I don't know how hot is hot for people that reported problems for they didn't post any temperature readings.

I would assume that if you have the opportunity and have two drives in your Y700, it might work better to designate the installation onto the SSD drive and then setup the PCIe drive and mount it outside the typical files system.

I did do all of these tests using the main Unity based Ubuntu 16.10 even though my preference would be Ubuntu Mate.

---

