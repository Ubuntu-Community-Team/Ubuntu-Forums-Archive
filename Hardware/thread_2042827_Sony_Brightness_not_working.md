---
title: "Sony Brightness not working"
date: 2012-08-15
forum: Hardware
---

### Post by MRCRUSHER on 2012-08-15
Solution: a workaround that could solve the problem which is [http://ubuntuforums.org/showpost.php...6&postcount=54]("http://ubuntuforums.org/showpost.php?p=12183956&postcount=54")

I used to have brightness control working on Ubuntu 10.04 but after upgrade to 12.04, my brightness control does not work. When I press Fn+F5 and Fn+F6 the brightness bar changes but the actual brightness does not change at all. 

Here is the output from several commands:
$ **cat /proc/cmdline**
```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=36f3940a-e8b4-4fe2-884c-9101d21781f4 ro quiet splash nomodeset video=uvesafb:mode_option=1024x768-8,mtrr=3,scroll=ywrap vt.handoff=7
```$ **sudo lspci -vnn | grep -A12 VGA**
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:820f]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Kernel driver in use: nvidia
```$ **ls /sys/class/backlight**
```
sony
```$ **lsmod**
```
Module                  Size  Used by
dm_crypt               22528  0 
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
nvidia              10962290  33 
joydev                 17393  0 
snd_hda_codec_realtek   174222  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
pcmcia                 39791  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                   12473  2 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
iwl3945                73111  0 
iwl_legacy             71134  1 iwl3945
mac80211              436455  2 iwl3945,iwl_legacy
tifm_7xx1              12937  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
btusb                  17912  2 
soundcore              14635  1 snd
tifm_core              15040  1 tifm_7xx1
psmouse                87213  0 
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sony_laptop            39681  0 
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
bluetooth             158438  23 rfcomm,bnep,btusb
mac_hid                13077  0 
sonypi                 19573  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
uvesafb                28403  1 
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49545  0 
video                  19068  0 
usb_storage            39646  0 
```$ **sudo dmidecode -s system-manufacturer**
```
Sony Corporation
```$ **sudo dmidecode -s system-product-name**
```
VGN-C23S_L
```content of [B]/etc/default/grub
[/B]```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=6
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-8,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by coffeecat on 2012-08-15
Welcome to the forum.

I see that you have a nvidia GPU and you are using the proprietary nvidia driver. One of the fixes in this post should help:

[http://ubuntuforums.org/showpost.php?p=11613896&postcount=7](http://ubuntuforums.org/showpost.php?p=11613896&postcount=7)

The first fix - the line in /etc/X11/xorg.conf - works for me in my Sony Vaio, albeit a different model from yours.

---

### Post by MRCRUSHER on 2012-08-15
Dear coffeecat,

Thank you for your suggestion. I have already tried to put the 
```
Option "RegistryDwords" "EnableBrightnessControl=1"
``` in /etc/X11/xorg.conf and restart but it does not work.

I just tried to put 

```
acpi_backlight=vendor
```in /etc/default/grub, run 
$ **sudo update-grub **
restart and run 
$ **cat /proc/cmdline**
and get 
```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=36f3940a-e8b4-4fe2-884c-9101d21781f4 ro acpi_backlight=vendor quiet splash nomodeset video=uvesafb:mode_option=1024x768-8,mtrr=3,scroll=ywrap acpi_backlight=vendor vt.handoff=7

```and still it does not work yet.
I will try 
- **acpi_osi=Linux**
- **acpi_osi=**
- [B]acpi_osi=Linux acpi_backlight=vendor

[/B]

---

### Post by MRCRUSHER on 2012-08-15
Update:
I tried all three of following:
- **acpi_osi=Linux**
- **acpi_osi=**
- [B]acpi_osi=Linux acpi_backlight=vendor
[/B]in /etc/default/grub as 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-8,mtrr=3,scroll=ywrap acpi_osi=Linux"
``````
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset  video=uvesafb:mode_option=1024x768-8,mtrr=3,scroll=ywrap acpi_osi="
``````
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset  video=uvesafb:mode_option=1024x768-8,mtrr=3,scroll=ywrap acpi_osi=Linux  acpi_backlight=vendor"
```and none of them is working.

---

### Post by MRCRUSHER on 2012-08-17
I still need help on this. Thank you.

---

### Post by Marric on 2012-08-17
maybe this thread will help you
[http://ubuntuforums.org/showthread.php?t=2042459](http://ubuntuforums.org/showthread.php?t=2042459)

---

### Post by MRCRUSHER on 2012-08-17
I read and tried but it still not working. When I call the command

```
sudo setpci -s "00:02.0" F4.B=35
```I get 

setpci: Warning: No devices selected for "F4.B=35"

So I guess that I should change "00:02.0" to "01:00.0" because my graphic card is 

```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1) (prog-if 00 [VGA controller])
```

But it still does not work.

---

### Post by Marric on 2012-08-17
what is the output of
```
lspci
```

---

### Post by MRCRUSHER on 2012-08-17
Here is the output of **lspci**:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by Marric on 2012-08-17
your integrated graphics controller does not show up.  It's probably disabled in the bios. Try to activate it there (both cards).
Please output
```
lsmod | grep i915
```

---

### Post by MRCRUSHER on 2012-08-17
lsmod | grep i915

does not output anything.

---

### Post by Marric on 2012-08-17
ok, did you check the bios?

---

### Post by MRCRUSHER on 2012-08-17
I went to the BIOS and does not see any option to enable both graphic and integrated graphic card. I think there is only graphic card which is nVidia GeForce Go 7400 in my notebook.

---

### Post by Marric on 2012-08-17
Install this to have the up-to-date nvidia drivers
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current 
```
then update and upgrade

In the grub remove nomodeset

---

### Post by Marric on 2012-08-17
Your Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT does have an integrated graphics controller.

---

### Post by MRCRUSHER on 2012-08-17
Just want to give you some info. I just tried to put Ubuntu 10.10 CD and boot with the CD. I choose "try without install" and I am able to use brightness control there.

Now I am back to Ubuntu 12.04 and installing nVidia-current and do update and upgrade and will remove the "nomodeset" from grub. Then will tell you the result.

---

### Post by Marric on 2012-08-17
If
```
lspci
```
still does not show the other (00:02.0) VGA then do```

sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by MRCRUSHER on 2012-08-17
I am still not able to use the brightness control in Ubuntu 12.04. :(

---

### Post by Marric on 2012-08-17
what is the output of lspci ?

---

### Post by MRCRUSHER on 2012-08-17
lspci still does not show the other (00:02.0) VGA

I will do 

```
sudo rm /etc/X11/xorg.conf 
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64  
sudo dpkg-reconfigure xserver-xorg
``` and let you know.

---

### Post by MRCRUSHER on 2012-08-17
Since I am not running 64-bit, there are no following package

libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64

So I use libgl1-mesa-glx libgl1-mesa-dri instead.

I do
```
sudo rm /etc/X11/xorg.conf  
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg
```But lspci still does not show the other (00:02.0) VGA and I still could not control the brightness.

---

### Post by MRCRUSHER on 2012-08-17
Here is the output of lspci.

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by NikTh on 2012-08-17
Hi , 
what is the output of 
```
apt-cache policy nvidia-current 
lsmod 
ls /sys/class/backlight/*/
dmesg
```
**Tip:** To provide a full output of dmesg you can enable unlimited scrolling in terminal with Edit > Profiles > Edit > Scrolling > tick Unlimited.

Thanks

---

### Post by Marric on 2012-08-17
Did you reboot?

What computer are you using?

---

### Post by MRCRUSHER on 2012-08-17
Here is the output of **apt-cache policy nvidia-current **
```
 nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup2
  Candidate: 302.17-0ubuntu1~precise~xup2
  Version table:
 *** 302.17-0ubuntu1~precise~xup2 0
        500 [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1.1 0
        500 [http://mirror1.ku.ac.th/ubuntu/](http://mirror1.ku.ac.th/ubuntu/) precise-updates/restricted i386 Packages
        500 [http://mirror1.ku.ac.th/ubuntu/](http://mirror1.ku.ac.th/ubuntu/) precise-security/restricted i386 Packages
     295.40-0ubuntu1 0
        500 [http://mirror1.ku.ac.th/ubuntu/](http://mirror1.ku.ac.th/ubuntu/) precise/restricted i386 Packages
```$ lsmod 
```
Module                  Size  Used by
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22528  0 
binfmt_misc            17292  1 
joydev                 17393  0 
nvidia               9874792  33 
pcmcia                 39791  0 
psmouse                87213  0 
arc4                   12473  2 
btusb                  17912  2 
tifm_7xx1              12937  0 
serio_raw              13027  0 
bluetooth             158438  23 rfcomm,bnep,btusb
tifm_core              15040  1 tifm_7xx1
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
sony_laptop            39681  0 
iwl3945                73111  0 
iwl_legacy             71134  1 iwl3945
snd_hda_codec_realtek   174222  1 
mac80211              436455  2 iwl3945,iwl_legacy
mac_hid                13077  0 
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sonypi                 19573  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
uvesafb                28403  1 
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
video                  19068  0 
sky2                   49545  0 
usb_storage            39646  0 
```$ ls /sys/class/backlight/*/
```
actual_brightness  bl_power  brightness  max_brightness  power  subsystem  type  uevent

```$ dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-29-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 (Ubuntu 3.2.0-29.46-generic 3.2.24)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe90000 (usable)
[    0.000000]  BIOS-e820: 000000007fe90000 - 000000007fe98000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe98000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Sony Corporation VGN-C23S_L/VAIO, BIOS R0080J4 12/19/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fe90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2047M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] found SMP MP-table at [c00f71a0] f71a0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35a38000 - 36d14000
[    0.000000] ACPI: RSDP 000f70d0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 7fe904eb 00050 (v01   Sony     VAIO 20061219 PTL  00000000)
[    0.000000] ACPI: FACP 7fe97c9a 00084 (v02   Sony     VAIO 20061219 PTL  0000005A)
[    0.000000] ACPI: DSDT 7fe91df7 05EA3 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.000000] ACPI: FACS 7fe98fc0 00040
[    0.000000] ACPI: APIC 7fe97d1e 00068 (v01   Sony     VAIO 20061219 PTL  0000005A)
[    0.000000] ACPI: HPET 7fe97d86 00038 (v01   Sony     VAIO 20061219 PTL  0000005A)
[    0.000000] ACPI: MCFG 7fe97dbe 0003C (v01   Sony     VAIO 20061219 PTL  0000005A)
[    0.000000] ACPI: SLIC 7fe97dfa 00176 (v01   Sony     VAIO 20061219 PTL  01000000)
[    0.000000] ACPI: APIC 7fe97f70 00068 (v01   Sony     VAIO 20061219 PTL  00000000)
[    0.000000] ACPI: BOOT 7fe97fd8 00028 (v01   Sony     VAIO 20061219 PTL  00000001)
[    0.000000] ACPI: SSDT 7fe9161d 007DA (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.000000] ACPI: SSDT 7fe90b16 0028F (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.000000] ACPI: SSDT 7fe90a75 000A1 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.000000] ACPI: SSDT 7fe9053b 0053A (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe90
[    0.000000] On node 0 totalpages: 523807
[    0.000000] free_area_init_node: node 0, pgdat c1822e80, node_mem_map f4a38200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294276 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77d7000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519713
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=36f3940a-e8b4-4fe2-884c-9101d21781f4 ro acpi_osi=Linux quiet splash video=uvesafb:mode_option=1024x768-8,mtrr=3,scroll=ywrap acpi_backlight=vendor vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8382464 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fe90)
[    0.000000] Memory: 2040372k/2095680k available (5615k kernel code, 54856k reserved, 2765k data, 712k init, 1186376k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1830000 - 0xc18e2000   ( 712 kB)
[    0.000000]       .data : 0xc157be04 - 0xc182f580   (2765 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157be04   (5615 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.612 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.22 BogoMIPS (lpj=6650448)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004038] Security Framework initialized
[    0.004061] AppArmor: AppArmor initialized
[    0.004063] Yama: becoming mindful.
[    0.004136] Mount-cache hash table entries: 512
[    0.004314] Initializing cgroup subsys cpuacct
[    0.004323] Initializing cgroup subsys memory
[    0.004334] Initializing cgroup subsys devices
[    0.004337] Initializing cgroup subsys freezer
[    0.004340] Initializing cgroup subsys blkio
[    0.004349] Initializing cgroup subsys perf_event
[    0.004379] Disabled fast string operations
[    0.004386] CPU: Physical Processor ID: 0
[    0.004389] CPU: Processor Core ID: 0
[    0.004393] mce: CPU supports 6 MCE banks
[    0.004404] CPU0: Thermal monitoring enabled (TM2)
[    0.004409] using mwait in idle threads.
[    0.008045] ACPI: Core revision 20110623
[    0.016035] ftrace: allocating 25891 entries in 51 pages
[    0.020064] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024328] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.064031] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 02
[    0.068003] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f44ea000 soft=f44ec000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.156049] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156101] Brought up 2 CPUs
[    0.156104] Total of 2 processors activated (6650.25 BogoMIPS).
[    0.157734] devtmpfs: initialized
[    0.157734] EVM: security.selinux
[    0.157734] EVM: security.SMACK64
[    0.157734] EVM: security.capability
[    0.157734] PM: Registering ACPI NVS region at 7fe98000 (425984 bytes)
[    0.157734] print_constraints: dummy: 
[    0.157734] RTC time:  8:37:37, date: 08/18/12
[    0.157734] NET: Registered protocol family 16
[    0.157734] Trying to unpack rootfs image as initramfs...
[    0.157799] EISA bus registered
[    0.160028] ACPI: bus type pci registered
[    0.160123] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.160127] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.160130] PCI: Using MMCONFIG for extended config space
[    0.160133] PCI: Using configuration type 1 for base access
[    0.172138] bio: create slab <bio-0> at 0
[    0.172254] ACPI: Added _OSI(Module Device)
[    0.172258] ACPI: Added _OSI(Processor Device)
[    0.172261] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172265] ACPI: Added _OSI(Processor Aggregator Device)
[    0.172268] ACPI: Added _OSI(Linux)
[    0.174151] ACPI: EC: Look up EC in DSDT
[    0.292287] ACPI: SSDT 7fe91300 00240 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.292757] ACPI: Dynamic OEM Table Load:
[    0.292762] ACPI: SSDT   (null) 00240 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.293180] ACPI: SSDT 7fe90da5 004C9 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.293622] ACPI: Dynamic OEM Table Load:
[    0.293627] ACPI: SSDT   (null) 004C9 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.296262] ACPI: SSDT 7fe91540 000DD (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.296718] ACPI: Dynamic OEM Table Load:
[    0.296723] ACPI: SSDT   (null) 000DD (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.296859] ACPI: SSDT 7fe9126e 00092 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.297304] ACPI: Dynamic OEM Table Load:
[    0.297309] ACPI: SSDT   (null) 00092 (v01   Sony     VAIO 20061219 PTL  20050624)
[    0.496731] ACPI: Interpreter enabled
[    0.496731] ACPI: (supports S0 S3 S4 S5)
[    0.496731] ACPI: Using IOAPIC for interrupt routing
[    0.513750] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.520116] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.521934] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.521934] HEST: Table not found.
[    0.521934] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.521934] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.521934] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.521934] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.521934] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.521934] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.521934] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.521934] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.521934] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.521934] pci 0000:00:00.0: [8086:27a0] type 0 class 0x000600
[    0.521934] pci 0000:00:01.0: [8086:27a1] type 1 class 0x000604
[    0.521934] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.521934] pci 0000:00:01.0: PME# disabled
[    0.521934] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.521934] pci 0000:00:1b.0: reg 10: [mem 0xd2300000-0xd2303fff 64bit]
[    0.521965] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.521971] pci 0000:00:1b.0: PME# disabled
[    0.522006] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.522131] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.522137] pci 0000:00:1c.0: PME# disabled
[    0.522178] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.524114] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.524121] pci 0000:00:1c.1: PME# disabled
[    0.524158] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.524283] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.524289] pci 0000:00:1c.2: PME# disabled
[    0.524327] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.524454] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.524460] pci 0000:00:1c.3: PME# disabled
[    0.524498] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.524561] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    0.524610] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.524674] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    0.524724] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.524788] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
[    0.524838] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.524901] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
[    0.524963] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.524990] pci 0000:00:1d.7: reg 10: [mem 0xd2304000-0xd23043ff]
[    0.525112] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.525119] pci 0000:00:1d.7: PME# disabled
[    0.525150] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.525259] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.525386] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.525394] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.525466] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.525485] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.525500] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.525514] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.525528] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.525542] pci 0000:00:1f.1: reg 20: [io  0x1880-0x188f]
[    0.525597] pci 0000:00:1f.2: [8086:27c4] type 0 class 0x000101
[    0.525621] pci 0000:00:1f.2: reg 10: [io  0x18c8-0x18cf]
[    0.525635] pci 0000:00:1f.2: reg 14: [io  0x18ac-0x18af]
[    0.525649] pci 0000:00:1f.2: reg 18: [io  0x18c0-0x18c7]
[    0.525663] pci 0000:00:1f.2: reg 1c: [io  0x18a8-0x18ab]
[    0.525677] pci 0000:00:1f.2: reg 20: [io  0x18b0-0x18bf]
[    0.525691] pci 0000:00:1f.2: reg 24: [mem 0xd2304400-0xd23047ff]
[    0.525744] pci 0000:00:1f.2: PME# supported from D3hot
[    0.525750] pci 0000:00:1f.2: PME# disabled
[    0.525772] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.525855] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.525973] pci 0000:01:00.0: [10de:01d8] type 0 class 0x000300
[    0.525992] pci 0000:01:00.0: reg 10: [mem 0xd1000000-0xd1ffffff]
[    0.526013] pci 0000:01:00.0: reg 14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.526033] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd0ffffff 64bit]
[    0.526059] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.526139] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.526152] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.526159] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd1ffffff]
[    0.526165] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.526270] pci 0000:02:00.0: [11ab:4351] type 0 class 0x000200
[    0.526305] pci 0000:02:00.0: reg 10: [mem 0xc8000000-0xc8003fff 64bit]
[    0.526324] pci 0000:02:00.0: reg 18: [io  0x2000-0x20ff]
[    0.526493] pci 0000:02:00.0: supports D1 D2
[    0.526496] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.526503] pci 0000:02:00.0: PME# disabled
[    0.526524] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.526538] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.526544] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.526551] pci 0000:00:1c.0:   bridge window [mem 0xc8000000-0xc9ffffff]
[    0.526561] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.526633] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.526639] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.526645] pci 0000:00:1c.1:   bridge window [mem 0xca000000-0xcbffffff]
[    0.526655] pci 0000:00:1c.1:   bridge window [mem 0xc2000000-0xc3ffffff 64bit pref]
[    0.526832] pci 0000:06:00.0: [8086:4222] type 0 class 0x000280
[    0.526891] pci 0000:06:00.0: reg 10: [mem 0xcc000000-0xcc000fff]
[    0.527326] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.527341] pci 0000:06:00.0: PME# disabled
[    0.527413] pci 0000:06:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.527454] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.527460] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.527467] pci 0000:00:1c.2:   bridge window [mem 0xcc000000-0xcdffffff]
[    0.527477] pci 0000:00:1c.2:   bridge window [mem 0xc4000000-0xc5ffffff 64bit pref]
[    0.527548] pci 0000:00:1c.3: PCI bridge to [bus 08-09]
[    0.527554] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.527561] pci 0000:00:1c.3:   bridge window [mem 0xce000000-0xcfffffff]
[    0.527571] pci 0000:00:1c.3:   bridge window [mem 0xc6000000-0xc7ffffff 64bit pref]
[    0.527632] pci 0000:0a:03.0: [104c:8039] type 2 class 0x000607
[    0.527662] pci 0000:0a:03.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.527710] pci 0000:0a:03.0: supports D1 D2
[    0.527713] pci 0000:0a:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.527721] pci 0000:0a:03.0: PME# disabled
[    0.527749] pci 0000:0a:03.1: [104c:803a] type 0 class 0x000c00
[    0.527779] pci 0000:0a:03.1: reg 10: [mem 0xd2005000-0xd20057ff]
[    0.527796] pci 0000:0a:03.1: reg 14: [mem 0xd2000000-0xd2003fff]
[    0.527913] pci 0000:0a:03.1: supports D1 D2
[    0.527916] pci 0000:0a:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.527923] pci 0000:0a:03.1: PME# disabled
[    0.527953] pci 0000:0a:03.2: [104c:803b] type 0 class 0x000180
[    0.527981] pci 0000:0a:03.2: reg 10: [mem 0xd2004000-0xd2004fff]
[    0.528119] pci 0000:0a:03.2: supports D1 D2
[    0.528122] pci 0000:0a:03.2: PME# supported from D0 D1 D2 D3hot
[    0.528129] pci 0000:0a:03.2: PME# disabled
[    0.528207] pci 0000:00:1e.0: PCI bridge to [bus 0a-0b] (subtractive decode)
[    0.528217] pci 0000:00:1e.0:   bridge window [mem 0xd2000000-0xd20fffff]
[    0.528227] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.528231] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.528293] pci_bus 0000:0b: [bus 0b-0e] partially hidden behind transparent bridge 0000:0a [bus 0a-0b]
[    0.528335] pci_bus 0000:00: on NUMA node 0
[    0.528341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.528606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.528831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.528964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.529093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.529225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.529461] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.530012]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.530152]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x00
[    0.530155] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.543201] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.543276] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.543347] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.543420] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.543494] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.543569] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.543647] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[    0.543723] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 11 12 14 15)
[    0.543919] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.543927] vgaarb: loaded
[    0.543929] vgaarb: bridge control possible 0000:01:00.0
[    0.544156] i2c-core: driver [aat2870] using legacy suspend method
[    0.544158] i2c-core: driver [aat2870] using legacy resume method
[    0.544294] SCSI subsystem initialized
[    0.544383] libata version 3.00 loaded.
[    0.544463] usbcore: registered new interface driver usbfs
[    0.544482] usbcore: registered new interface driver hub
[    0.544523] usbcore: registered new device driver usb
[    0.544685] PCI: Using ACPI for IRQ routing
[    0.556376] PCI: pci_cache_line_size set to 64 bytes
[    0.556531] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.556535] reserve RAM buffer: 000000007fe90000 - 000000007fffffff 
[    0.556724] NetLabel: Initializing
[    0.556728] NetLabel:  domain hash size = 128
[    0.556730] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.556746] NetLabel:  unlabeled traffic allowed by default
[    0.556834] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.556843] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.556850] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.564122] Switching to clocksource hpet
[    0.575852] AppArmor: AppArmor Filesystem Enabled
[    0.575899] pnp: PnP ACPI init
[    0.575926] ACPI: bus type pnp registered
[    0.586012] pnp 00:00: [bus 00-ff]
[    0.586017] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.586020] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.586024] pnp 00:00: [io  0x0d00-0xffff window]
[    0.586027] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.586031] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.586034] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.586037] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.586040] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.586044] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.586047] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.586050] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.586054] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.586057] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.586060] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.586068] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.586071] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.586074] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.586078] pnp 00:00: [mem 0x80000000-0xfebfffff window]
[    0.586081] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.586200] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.586216] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.586219] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.586222] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.586225] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.586228] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.586231] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.586234] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.586326] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.586330] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.586334] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.586338] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.586342] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.586346] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.586350] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.586355] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.586638] pnp 00:02: [io  0x0000-0x001f]
[    0.586642] pnp 00:02: [io  0x0081-0x0091]
[    0.586645] pnp 00:02: [io  0x0093-0x009f]
[    0.586648] pnp 00:02: [io  0x00c0-0x00df]
[    0.586651] pnp 00:02: [dma 4]
[    0.586718] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.586731] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.586798] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.586880] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.586952] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.586969] pnp 00:05: [io  0x00f0]
[    0.586983] pnp 00:05: [irq 13]
[    0.587051] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.587083] pnp 00:06: [io  0x002e-0x002f]
[    0.587086] pnp 00:06: [io  0x0061]
[    0.587089] pnp 00:06: [io  0x0063]
[    0.587092] pnp 00:06: [io  0x0065]
[    0.587095] pnp 00:06: [io  0x0067]
[    0.587098] pnp 00:06: [io  0x0070]
[    0.587100] pnp 00:06: [io  0x0080]
[    0.587103] pnp 00:06: [io  0x0092]
[    0.587106] pnp 00:06: [io  0x00b2-0x00b3]
[    0.587109] pnp 00:06: [io  0x0680-0x06ff]
[    0.587112] pnp 00:06: [io  0x0800-0x080f]
[    0.587115] pnp 00:06: [io  0x1000-0x107f]
[    0.587118] pnp 00:06: [io  0x1180-0x11bf]
[    0.587121] pnp 00:06: [io  0x1640-0x164f]
[    0.587124] pnp 00:06: [io  0xfe00-0xfe7f]
[    0.587126] pnp 00:06: [io  0xfe80-0xfeff]
[    0.587242] system 00:06: [io  0x0680-0x06ff] has been reserved
[    0.587246] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.587250] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.587254] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.587258] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.587262] system 00:06: [io  0xfe00-0xfe7f] has been reserved
[    0.587266] system 00:06: [io  0xfe80-0xfeff] has been reserved
[    0.587271] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.587294] pnp 00:07: [io  0x0070-0x0077]
[    0.587302] pnp 00:07: [irq 8]
[    0.587371] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.587392] pnp 00:08: [io  0x0060]
[    0.587395] pnp 00:08: [io  0x0064]
[    0.587402] pnp 00:08: [irq 1]
[    0.587471] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.587488] pnp 00:09: [irq 12]
[    0.587562] pnp 00:09: Plug and Play ACPI device, IDs SNY9001 PNP0f13 (active)
[    0.587595] pnp: PnP ACPI: found 10 devices
[    0.587598] ACPI: ACPI bus type pnp unregistered
[    0.587604] PnPBIOS: Disabled by ACPI PNP
[    0.625124] PCI: max bus depth: 2 pci_try_num: 3
[    0.625216] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.625224] pci 0000:00:1e.0: BAR 13: assigned [io  0x6000-0x6fff]
[    0.625229] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.625233] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.625239] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd1ffffff]
[    0.625244] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.625251] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.625256] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.625264] pci 0000:00:1c.0:   bridge window [mem 0xc8000000-0xc9ffffff]
[    0.625271] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.625281] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.625285] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.625293] pci 0000:00:1c.1:   bridge window [mem 0xca000000-0xcbffffff]
[    0.625300] pci 0000:00:1c.1:   bridge window [mem 0xc2000000-0xc3ffffff 64bit pref]
[    0.625309] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.625314] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.625322] pci 0000:00:1c.2:   bridge window [mem 0xcc000000-0xcdffffff]
[    0.625328] pci 0000:00:1c.2:   bridge window [mem 0xc4000000-0xc5ffffff 64bit pref]
[    0.625338] pci 0000:00:1c.3: PCI bridge to [bus 08-09]
[    0.625342] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.625350] pci 0000:00:1c.3:   bridge window [mem 0xce000000-0xcfffffff]
[    0.625357] pci 0000:00:1c.3:   bridge window [mem 0xc6000000-0xc7ffffff 64bit pref]
[    0.625369] pci 0000:0a:03.0: BAR 0: assigned [mem 0x84000000-0x84000fff]
[    0.625377] pci 0000:0a:03.0: BAR 0: set to [mem 0x84000000-0x84000fff] (PCI address [0x84000000-0x84000fff])
[    0.625382] pci 0000:0a:03.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.625387] pci 0000:0a:03.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.625390] pci 0000:0a:03.0: BAR 14: assigned [io  0x6000-0x60ff]
[    0.625394] pci 0000:0a:03.0: BAR 13: assigned [io  0x6400-0x64ff]
[    0.625398] pci 0000:0a:03.0: CardBus bridge to [bus 0b-0e]
[    0.625401] pci 0000:0a:03.0:   bridge window [io  0x6400-0x64ff]
[    0.625408] pci 0000:0a:03.0:   bridge window [io  0x6000-0x60ff]
[    0.625415] pci 0000:0a:03.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.625422] pci 0000:0a:03.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.625430] pci 0000:00:1e.0: PCI bridge to [bus 0a-0b]
[    0.625434] pci 0000:00:1e.0:   bridge window [io  0x6000-0x6fff]
[    0.625442] pci 0000:00:1e.0:   bridge window [mem 0xd2000000-0xd20fffff]
[    0.625448] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.625484] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.625490] pci 0000:00:01.0: setting latency timer to 64
[    0.625505] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.625512] pci 0000:00:1c.0: setting latency timer to 64
[    0.625522] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.625528] pci 0000:00:1c.1: setting latency timer to 64
[    0.625545] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.625551] pci 0000:00:1c.2: setting latency timer to 64
[    0.625565] pci 0000:00:1c.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.625572] pci 0000:00:1c.3: setting latency timer to 64
[    0.625580] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.625588] pci 0000:00:1e.0: setting latency timer to 64
[    0.625598] pci 0000:0a:03.0: enabling device (0000 -> 0003)
[    0.625605] pci 0000:0a:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.625616] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.625620] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.625624] pci_bus 0000:01: resource 1 [mem 0xd0000000-0xd1ffffff]
[    0.625628] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.625631] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.625635] pci_bus 0000:02: resource 1 [mem 0xc8000000-0xc9ffffff]
[    0.625638] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.625642] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.625645] pci_bus 0000:04: resource 1 [mem 0xca000000-0xcbffffff]
[    0.625649] pci_bus 0000:04: resource 2 [mem 0xc2000000-0xc3ffffff 64bit pref]
[    0.625652] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.625656] pci_bus 0000:06: resource 1 [mem 0xcc000000-0xcdffffff]
[    0.625659] pci_bus 0000:06: resource 2 [mem 0xc4000000-0xc5ffffff 64bit pref]
[    0.625663] pci_bus 0000:08: resource 0 [io  0x5000-0x5fff]
[    0.625666] pci_bus 0000:08: resource 1 [mem 0xce000000-0xcfffffff]
[    0.625669] pci_bus 0000:08: resource 2 [mem 0xc6000000-0xc7ffffff 64bit pref]
[    0.625673] pci_bus 0000:0a: resource 0 [io  0x6000-0x6fff]
[    0.625676] pci_bus 0000:0a: resource 1 [mem 0xd2000000-0xd20fffff]
[    0.625680] pci_bus 0000:0a: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.625683] pci_bus 0000:0a: resource 4 [io  0x0000-0xffff]
[    0.625686] pci_bus 0000:0a: resource 5 [mem 0x00000000-0xffffffff]
[    0.625690] pci_bus 0000:0b: resource 0 [io  0x6400-0x64ff]
[    0.625693] pci_bus 0000:0b: resource 1 [io  0x6000-0x60ff]
[    0.625696] pci_bus 0000:0b: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.625700] pci_bus 0000:0b: resource 3 [mem 0x88000000-0x8bffffff]
[    0.625765] NET: Registered protocol family 2
[    0.625866] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.626258] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.626857] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.627157] TCP: Hash tables configured (established 131072 bind 65536)
[    0.627160] TCP reno registered
[    0.627164] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.627177] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.627296] NET: Registered protocol family 1
[    0.627364] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.627389] pci 0000:00:1d.0: PCI INT A disabled
[    0.627400] pci 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.627422] pci 0000:00:1d.1: PCI INT B disabled
[    0.627433] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.627455] pci 0000:00:1d.2: PCI INT C disabled
[    0.627466] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.627488] pci 0000:00:1d.3: PCI INT D disabled
[    0.627501] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.627539] pci 0000:00:1d.7: PCI INT A disabled
[    0.627574] pci 0000:01:00.0: Boot video device
[    0.627603] PCI: CLS 64 bytes, default 64
[    0.627611] Simple Boot Flag at 0x36 set to 0x1
[    0.628240] audit: initializing netlink socket (disabled)
[    0.628260] type=2000 audit(1345279057.624:1): initialized
[    0.662019] highmem bounce pool size: 64 pages
[    0.662027] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.673228] VFS: Disk quotas dquot_6.5.2
[    0.673330] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.674187] fuse init (API version 7.17)
[    0.674325] msgmni has been set to 1667
[    0.674774] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.674810] io scheduler noop registered
[    0.674813] io scheduler deadline registered
[    0.674823] io scheduler cfq registered (default)
[    0.675018] pcieport 0000:00:01.0: setting latency timer to 64
[    0.675064] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.675138] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.675200] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.675299] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.675361] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.675459] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.675521] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.675621] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.675683] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.675826] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.675869] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.676030] intel_idle: MWAIT substates: 0x22220
[    0.676033] intel_idle: does not run on family 6 model 15
[    0.676751] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.677552] ACPI: AC Adapter [ADP1] (on-line)
[    0.677668] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.678394] ACPI: Lid Switch [LID0]
[    0.678463] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.678470] ACPI: Power Button [PWRB]
[    0.684196] Monitor-Mwait will be used to enter C-1 state
[    0.692134] Monitor-Mwait will be used to enter C-2 state
[    0.692149] Marking TSC unstable due to TSC halts in idle
[    0.692160] ACPI: acpi_idle registered with cpuidle
[    0.705281] ACPI: Invalid active0 threshold
[    0.706060] thermal LNXTHERM:00: registered as thermal_zone0
[    0.706064] ACPI: Thermal Zone [TZ00] (64 C)
[    0.706945] ACPI: Invalid active0 threshold
[    0.707636] thermal LNXTHERM:01: registered as thermal_zone1
[    0.707639] ACPI: Thermal Zone [TZ01] (64 C)
[    0.707670] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.707684] ACPI: Battery Slot [BAT0] (battery present)
[    0.707773] ERST: Table is not found!
[    0.707776] GHES: HEST is not enabled!
[    0.707903] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.708180] isapnp: Scanning for PnP cards...
[    0.727179] Freeing initrd memory: 19312k freed
[    0.768915] ACPI: Battery Slot [BAT0] (battery present)
[    1.062041] isapnp: No Plug & Play device found
[    1.116592] Linux agpgart interface v0.103
[    1.119339] brd: module loaded
[    1.120646] loop: module loaded
[    1.120885] ata_piix 0000:00:1f.1: version 2.13
[    1.120905] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.120959] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.121467] scsi0 : ata_piix
[    1.121605] scsi1 : ata_piix
[    1.122172] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    1.122176] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    1.122220] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.122231] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
[    1.122243] ata2: port disabled--ignoring
[    1.276045] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.276491] scsi2 : ata_piix
[    1.276616] scsi3 : ata_piix
[    1.277186] ata3: SATA max UDMA/133 cmd 0x18c8 ctl 0x18ac bmdma 0x18b0 irq 19
[    1.277190] ata4: SATA max UDMA/133 cmd 0x18c0 ctl 0x18a8 bmdma 0x18b8 irq 19
[    1.277862] Fixed MDIO Bus: probed
[    1.277899] tun: Universal TUN/TAP device driver, 1.6
[    1.277902] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.277987] PPP generic driver version 2.4.2
[    1.278161] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.278185] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.278204] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.278209] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.278284] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.278313] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.278327] ehci_hcd 0000:00:1d.7: debug port 1
[    1.282206] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.282227] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd2304000
[    1.284525] ata1.00: ATAPI: QSI DVD-RAM SDW-086, ES72, max UDMA/33
[    1.296020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.296214] hub 1-0:1.0: USB hub found
[    1.296221] hub 1-0:1.0: 8 ports detected
[    1.296349] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.296372] uhci_hcd: USB Universal Host Controller Interface driver
[    1.296397] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.296407] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.296412] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.296485] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.296517] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    1.296709] hub 2-0:1.0: USB hub found
[    1.296716] hub 2-0:1.0: 2 ports detected
[    1.296816] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.296828] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.296832] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.296903] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.296946] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[    1.297142] hub 3-0:1.0: USB hub found
[    1.297148] hub 3-0:1.0: 2 ports detected
[    1.297249] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.297260] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.297264] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.297330] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.297374] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    1.297580] hub 4-0:1.0: USB hub found
[    1.297585] hub 4-0:1.0: 2 ports detected
[    1.297681] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.297692] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.297696] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.297767] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.297810] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    1.297996] hub 5-0:1.0: USB hub found
[    1.298002] hub 5-0:1.0: 2 ports detected
[    1.298174] usbcore: registered new interface driver libusual
[    1.298247] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.302469] ata1.00: configured for UDMA/33
[    1.304213] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.304220] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.304487] mousedev: PS/2 mouse device common for all mice
[    1.304780] rtc_cmos 00:07: RTC can wake from S4
[    1.304945] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.304986] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.304992] scsi 0:0:0:0: CD-ROM            QSI      DVD-RAM SDW-086  ES72 PQ: 0 ANSI: 5
[    1.305127] device-mapper: uevent: version 1.0.3
[    1.305230] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.305296] EISA: Probing bus 0 at eisa.0
[    1.305304] Cannot allocate resource for EISA slot 1
[    1.305308] Cannot allocate resource for EISA slot 2
[    1.305311] Cannot allocate resource for EISA slot 3
[    1.305315] Cannot allocate resource for EISA slot 4
[    1.305318] Cannot allocate resource for EISA slot 5
[    1.305321] Cannot allocate resource for EISA slot 6
[    1.305333] EISA: Detected 0 cards.
[    1.305347] cpufreq-nforce2: No nForce2 chipset.
[    1.305445] cpuidle: using governor ladder
[    1.305586] cpuidle: using governor menu
[    1.305590] EFI Variables Facility v0.08 2004-May-17
[    1.305979] TCP cubic registered
[    1.306167] NET: Registered protocol family 10
[    1.307053] NET: Registered protocol family 17
[    1.307059] Registering the dns_resolver key type
[    1.307088] Using IPI No-Shortcut mode
[    1.307305] PM: Hibernation image not present or could not be loaded.
[    1.307321] registered taskstats version 1
[    1.311640] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.312397] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.312401] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.312589] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.312792] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.321920]   Magic number: 8:791:624
[    1.322043] rtc_cmos 00:07: setting system clock to 2012-08-18 08:37:38 UTC (1345279058)
[    1.322566] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.322569] EDD information not available.
[    1.440414] ata3.00: ATA-8: SAMSUNG HM321HI, 2AJ10001, max UDMA/133
[    1.440422] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.448423] ata3.00: configured for UDMA/133
[    1.448705] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HM321HI  2AJ1 PQ: 0 ANSI: 5
[    1.448989] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.449058] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.449083] sd 2:0:0:0: [sda] Write Protect is off
[    1.449087] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.449119] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.520710]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.521720] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.608054] usb 1-6: new high-speed USB device number 2 using ehci_hcd
[    1.806315] Initializing USB Mass Storage driver...
[    1.806472] scsi4 : usb-storage 1-6:1.0
[    1.806576] usbcore: registered new interface driver usb-storage
[    1.806579] USB Mass Storage support registered.
[    2.156061] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    2.813352] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
[    2.814397] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.866319] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    5.468153] Freeing unused kernel memory: 712k freed
[    5.468607] Write protecting the kernel text: 5616k
[    5.468679] Write protecting the kernel read-only data: 2324k
[    5.493495] udevd[105]: starting version 175
[    5.569973] sky2: driver version 1.30
[    5.570027] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.570048] sky2 0000:02:00.0: setting latency timer to 64
[    5.570088] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    5.570214] sky2 0000:02:00.0: irq 45 for MSI/MSI-X
[    5.571038] sky2 0000:02:00.0: eth0: addr 00:13:a9:a7:41:1f
[    5.638497] firewire_ohci 0000:0a:03.1: enabling device (0000 -> 0002)
[    5.638509] firewire_ohci 0000:0a:03.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.692091] firewire_ohci: Added fw-ohci device 0000:0a:03.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    6.192288] firewire_core: created device fw0: GUID 080046030252adf1, S400
[    6.277975] uvesafb: NVIDIA Corporation, G72 Board - sms30   , Chip Rev   , OEM: NVIDIA, VBE v3.0
[    6.287340] uvesafb: protected mode interface info at c000:d370
[    6.287343] uvesafb: pmi: set display start = c00cd3a6, set palette = c00cd410
[    6.287346] uvesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    6.288826] uvesafb: VBIOS/hardware doesn't support DDC transfers
[    6.288829] uvesafb: no monitor limits have been set, default refresh rate will be used
[    6.289061] uvesafb: scrolling: ywrap using protected mode interface, yres_virtual=6144
[    6.293382] Console: switching to colour frame buffer device 128x48
[    6.293415] uvesafb: framebuffer at 0xb0000000, mapped to 0xf8200000, using 6144k, total 65536k
[    6.293418] fb0: VESA VGA frame buffer device
[    6.474918] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   24.338981] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.361959] udevd[382]: starting version 175
[   24.408669] lp: driver loaded but no devices found
[   24.410935] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   24.411027] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[   24.411176] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   24.411181] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   24.411183] sonypi: device allocated minor is 57
[   24.411264] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input3
[   24.411437] input: Sony Vaio Keys as /devices/platform/sonypi/input/input4
[   24.476223] sonypi command failed at /build/buildd/linux-3.2.0/drivers/char/sonypi.c : sonypi_call1 (line 654)
[   24.516564] sonypi command failed at /build/buildd/linux-3.2.0/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   24.557261] sonypi command failed at /build/buildd/linux-3.2.0/drivers/char/sonypi.c : sonypi_call2 (line 667)
[   24.597997] sonypi command failed at /build/buildd/linux-3.2.0/drivers/char/sonypi.c : sonypi_call1 (line 654)
[   24.612178] Adding 4088504k swap on /dev/sda6.  Priority:-1 extents:1 across:4088504k 
[   24.623228] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.623298] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   24.623336] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   24.624270] cfg80211: Calling CRDA to update world regulatory domain
[   24.689283] hda_codec: ALC262: SKU not ready 0x411111f0
[   24.689367] hda_codec: ALC262: BIOS auto-probing.
[   24.713174] type=1400 audit(1345253881.887:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=548 comm="apparmor_parser"
[   24.713755] type=1400 audit(1345253881.887:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
[   24.714085] type=1400 audit(1345253881.887:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=548 comm="apparmor_parser"
[   24.723959] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   24.724117] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   24.727934] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   24.727939] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   24.728048] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.728065] iwl3945 0000:06:00.0: setting latency timer to 64
[   24.796812] intel_rng: FWH not detected
[   24.801980] sony_laptop: Sony Notebook Control Driver v0.6
[   24.813983] leds_ss4200: no LED devices found
[   24.823916] yenta_cardbus 0000:0a:03.0: CardBus bridge found [104d:820f]
[   24.823943] yenta_cardbus 0000:0a:03.0: Using CSCINT to route CSC interrupts to PCI
[   24.823947] yenta_cardbus 0000:0a:03.0: Routing CardBus interrupts to PCI
[   24.823955] yenta_cardbus 0000:0a:03.0: TI: mfunc 0x01121b22, devctl 0x64
[   24.851272] Bluetooth: Core ver 2.16
[   24.851368] NET: Registered protocol family 31
[   24.851372] Bluetooth: HCI device and connection manager initialized
[   24.851376] Bluetooth: HCI socket layer initialized
[   24.851379] Bluetooth: L2CAP socket layer initialized
[   24.851387] Bluetooth: SCO socket layer initialized
[   24.852807] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   24.852914] iwl3945 0000:06:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   24.852919] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945BG
[   24.853074] iwl3945 0000:06:00.0: irq 47 for MSI/MSI-X
[   24.853237] Registered led device: phy0-led
[   24.853281] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   24.856117] usbcore: registered new interface driver btusb
[   24.867527] nvidia: module license 'NVIDIA' taints kernel.
[   24.867532] Disabling lock debugging due to kernel taint
[   24.881113] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   24.890024] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   25.020229] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27/SNY5001:00/input/input7
[   25.020548] input: Sony Vaio Jogdial as /devices/virtual/input/input8
[   25.056717] yenta_cardbus 0000:0a:03.0: ISA IRQ mask 0x04f8, PCI irq 16
[   25.056724] yenta_cardbus 0000:0a:03.0: Socket status: 30000006
[   25.056730] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   25.056742] yenta_cardbus 0000:0a:03.0: pcmcia: parent PCI bridge window: [io  0x6000-0x6fff]
[   25.056746] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x6fff: excluding 0x6000-0x60ff 0x6400-0x64ff
[   25.063519] yenta_cardbus 0000:0a:03.0: pcmcia: parent PCI bridge window: [mem 0xd2000000-0xd20fffff]
[   25.063523] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd2000000-0xd20fffff: excluding 0xd2000000-0xd200ffff
[   25.063542] yenta_cardbus 0000:0a:03.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   25.063546] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   25.110260] tifm_7xx1 0000:0a:03.2: enabling device (0000 -> 0002)
[   25.110272] tifm_7xx1 0000:0a:03.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   25.200919] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   25.315033] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   25.315038] cfg80211: World regulatory domain updated:
[   25.315041] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.315045] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.315049] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.315052] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.315056] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.315059] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.348856] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   25.350862] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   25.351705] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   25.352429] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   25.353206] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xdc000-0xfffff
[   25.353250] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   25.353291] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   25.353328] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   25.358912] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.358925] nvidia 0000:01:00.0: setting latency timer to 64
[   25.358932] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   25.360663] NVRM: loading NVIDIA UNIX x86 Kernel Module  302.17  Tue Jun 12 18:37:51 PDT 2012
[   25.361475]  clean.
[   25.554886] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   25.571439] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   26.648226] init: failsafe main process (807) killed by TERM signal
[   26.740762] ppdev: user-space parallel port driver
[   26.753461] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.753466] Bluetooth: BNEP filters: protocol multicast
[   26.767182] Bluetooth: RFCOMM TTY layer initialized
[   26.767190] Bluetooth: RFCOMM socket layer initialized
[   26.767192] Bluetooth: RFCOMM ver 1.11
[   26.821145] type=1400 audit(1345253883.995:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=896 comm="apparmor_parser"
[   26.823663] type=1400 audit(1345253883.995:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=896 comm="apparmor_parser"
[   26.893789] type=1400 audit(1345253884.067:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=924 comm="apparmor_parser"
[   26.895783] type=1400 audit(1345253884.067:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=925 comm="apparmor_parser"
[   26.900906] type=1400 audit(1345253884.075:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=926 comm="apparmor_parser"
[   26.905310] type=1400 audit(1345253884.079:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=926 comm="apparmor_parser"
[   26.905647] type=1400 audit(1345253884.079:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=926 comm="apparmor_parser"
[   26.980457] sky2 0000:02:00.0: eth0: enabling interface
[   26.980748] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.981531] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.011968] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
[   27.122285] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.122939] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.194852] init: gdm main process (1020) killed by TERM signal
[   29.685853] NVRM: Your system is not currently configured to drive a VGA console
[   29.685862] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   29.685865] NVRM: requires the use of a text-mode VGA console. Use of other console
[   29.685869] NVRM: drivers including, but not limited to, vesafb, may result in
[   29.685872] NVRM: corruption and stability problems, and is not supported.
[   36.438375] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[   36.440114] wlan0: authenticated
[   36.440417] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[   36.443158] wlan0: RX AssocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[   36.443163] wlan0: associated
[   36.444669] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  147.895526] show_signal_msg: 39 callbacks suppressed
[  147.895532] nvclock[2167]: segfault at 17ff ip 0804cd62 sp bfc8a724 error 4 in nvclock[8048000+1e000]
[  148.279691] nvclock[2176]: segfault at 17ff ip 0804cd62 sp bfa904e4 error 4 in nvclock[8048000+1e000]
[  148.532285] nvclock[2192]: segfault at 17ff ip 0804cd62 sp bfc56884 error 4 in nvclock[8048000+1e000]
[  148.847547] nvclock[2208]: segfault at 17ff ip 0804cd62 sp bfffd2e4 error 4 in nvclock[8048000+1e000]
[  149.064567] nvclock[2220]: segfault at 17ff ip 0804cd62 sp bfdb15f4 error 4 in nvclock[8048000+1e000]
[  149.274197] nvclock[2234]: segfault at 17ff ip 0804cd62 sp bfdf84d4 error 4 in nvclock[8048000+1e000]
[  149.474570] nvclock[2244]: segfault at 17ff ip 0804cd62 sp bfe78874 error 4 in nvclock[8048000+1e000]
[  149.689390] nvclock[2260]: segfault at 17ff ip 0804cd62 sp bf979a84 error 4 in nvclock[8048000+1e000]
[  149.843146] nvclock[2264]: segfault at 17ff ip 0804cd62 sp bfbe6b74 error 4 in nvclock[8048000+1e000]
[  150.010498] nvclock[2270]: segfault at 17ff ip 0804cd62 sp bf9ec504 error 4 in nvclock[8048000+1e000]
[  153.765473] show_signal_msg: 5 callbacks suppressed
[  153.765479] nvclock[2316]: segfault at 17ff ip 0804cd62 sp bfd7c674 error 4 in nvclock[8048000+1e000]
[  154.039663] nvclock[2334]: segfault at 17ff ip 0804cd62 sp bff52234 error 4 in nvclock[8048000+1e000]
[  154.274136] nvclock[2343]: segfault at 17ff ip 0804cd62 sp bff0db64 error 4 in nvclock[8048000+1e000]
[  154.549277] nvclock[2357]: segfault at 17ff ip 0804cd62 sp bf978d34 error 4 in nvclock[8048000+1e000]
[  154.766483] nvclock[2369]: segfault at 17ff ip 0804cd62 sp bffb27b4 error 4 in nvclock[8048000+1e000]
[  154.956997] nvclock[2380]: segfault at 17ff ip 0804cd62 sp bff1df34 error 4 in nvclock[8048000+1e000]
[  155.151682] nvclock[2393]: segfault at 17ff ip 0804cd62 sp bf834ac4 error 4 in nvclock[8048000+1e000]
[  155.370625] nvclock[2404]: segfault at 17ff ip 0804cd62 sp bfc0c9a4 error 4 in nvclock[8048000+1e000]
[  155.593928] nvclock[2419]: segfault at 17ff ip 0804cd62 sp bfc20a34 error 4 in nvclock[8048000+1e000]
[  155.776965] nvclock[2429]: segfault at 17ff ip 0804cd62 sp bfca92e4 error 4 in nvclock[8048000+1e000]
[  159.169486] show_signal_msg: 15 callbacks suppressed
[  159.169492] nvclock[2613]: segfault at 17ff ip 0804cd62 sp bfe427e4 error 4 in nvclock[8048000+1e000]
[  159.322020] nvclock[2617]: segfault at 17ff ip 0804cd62 sp bf899594 error 4 in nvclock[8048000+1e000]
[  159.469442] nvclock[2621]: segfault at 17ff ip 0804cd62 sp bfbe43b4 error 4 in nvclock[8048000+1e000]
[  159.615308] nvclock[2625]: segfault at 17ff ip 0804cd62 sp bf96b224 error 4 in nvclock[8048000+1e000]
[  159.758989] nvclock[2629]: segfault at 17ff ip 0804cd62 sp bfe2ef94 error 4 in nvclock[8048000+1e000]
[  159.903406] nvclock[2633]: segfault at 17ff ip 0804cd62 sp bf8cbc34 error 4 in nvclock[8048000+1e000]
[  160.047066] nvclock[2637]: segfault at 17ff ip 0804cd62 sp bfbe2d24 error 4 in nvclock[8048000+1e000]
[  226.350336] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[  226.384150] cfg80211: All devices are disconnected, going to restore regulatory settings
[  226.384160] cfg80211: Restoring regulatory settings
[  226.384180] cfg80211: Calling CRDA to update world regulatory domain
[  226.394673] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  226.394681] cfg80211: World regulatory domain updated:
[  226.394686] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  226.394693] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  226.394700] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  226.394706] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  226.394712] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  226.394718] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  227.466885] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[  227.468644] wlan0: authenticated
[  227.469072] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[  227.471829] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[  227.471836] wlan0: associated
[  271.554320] nvclock[2643]: segfault at 17ff ip 0804cd62 sp bfb292f4 error 4 in nvclock[8048000+1e000]
[  272.105800] nvclock[2653]: segfault at 17ff ip 0804cd62 sp bfc6b5f4 error 4 in nvclock[8048000+1e000]
[  272.314035] nvclock[2663]: segfault at 17ff ip 0804cd62 sp bfc74a94 error 4 in nvclock[8048000+1e000]
[  272.517535] nvclock[2673]: segfault at 17ff ip 0804cd62 sp bf97c094 error 4 in nvclock[8048000+1e000]
[  272.723487] nvclock[2683]: segfault at 17ff ip 0804cd62 sp bfd42964 error 4 in nvclock[8048000+1e000]
[  272.953195] nvclock[2693]: segfault at 17ff ip 0804cd62 sp bf8bc6f4 error 4 in nvclock[8048000+1e000]
[  273.212749] nvclock[2709]: segfault at 17ff ip 0804cd62 sp bfe3e6f4 error 4 in nvclock[8048000+1e000]
[  273.390461] nvclock[2719]: segfault at 17ff ip 0804cd62 sp bffcf524 error 4 in nvclock[8048000+1e000]
[  273.658103] nvclock[2723]: segfault at 17ff ip 0804cd62 sp bfebb0a4 error 4 in nvclock[8048000+1e000]
[  273.925984] nvclock[2739]: segfault at 17ff ip 0804cd62 sp bf809844 error 4 in nvclock[8048000+1e000]
[  288.141857] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[  288.156142] cfg80211: All devices are disconnected, going to restore regulatory settings
[  288.156152] cfg80211: Restoring regulatory settings
[  288.156171] cfg80211: Calling CRDA to update world regulatory domain
[  288.166800] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  288.166808] cfg80211: World regulatory domain updated:
[  288.166813] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  288.166820] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  288.166827] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  288.166833] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  288.166839] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  288.166844] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  289.238590] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[  289.240387] wlan0: authenticated
[  289.240769] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[  289.243483] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[  289.243489] wlan0: associated
[  618.061901] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[  618.096179] cfg80211: All devices are disconnected, going to restore regulatory settings
[  618.096189] cfg80211: Restoring regulatory settings
[  618.096209] cfg80211: Calling CRDA to update world regulatory domain
[  618.106433] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  618.106441] cfg80211: World regulatory domain updated:
[  618.106445] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  618.106453] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  618.106459] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  618.106466] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  618.106472] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  618.106477] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  619.178875] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[  619.180729] wlan0: authenticated
[  619.181147] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[  619.184081] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[  619.184093] wlan0: associated
[  729.632725] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[  729.672325] cfg80211: All devices are disconnected, going to restore regulatory settings
[  729.672334] cfg80211: Restoring regulatory settings
[  729.672342] cfg80211: Calling CRDA to update world regulatory domain
[  729.682461] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  729.682469] cfg80211: World regulatory domain updated:
[  729.682474] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  729.682481] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  729.682487] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  729.682493] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  729.682499] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  729.682505] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  730.750483] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[  730.752506] wlan0: authenticated
[  730.752902] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[  730.755730] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[  730.755737] wlan0: associated
[  849.163896] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[  849.204174] cfg80211: All devices are disconnected, going to restore regulatory settings
[  849.204184] cfg80211: Restoring regulatory settings
[  849.204203] cfg80211: Calling CRDA to update world regulatory domain
[  849.214584] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  849.214592] cfg80211: World regulatory domain updated:
[  849.214597] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  849.214604] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  849.214610] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  849.214617] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  849.214623] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  849.214629] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  850.282470] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[  850.284211] wlan0: authenticated
[  850.284460] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[  850.287239] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[  850.287247] wlan0: associated
[  969.711053] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[  969.752157] cfg80211: All devices are disconnected, going to restore regulatory settings
[  969.752167] cfg80211: Restoring regulatory settings
[  969.752188] cfg80211: Calling CRDA to update world regulatory domain
[  969.762348] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  969.762356] cfg80211: World regulatory domain updated:
[  969.762360] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  969.762367] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  969.762374] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  969.762380] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  969.762386] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  969.762392] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  970.838478] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[  970.840321] wlan0: authenticated
[  970.840704] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[  970.843479] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[  970.843487] wlan0: associated
[ 1089.262208] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1089.300202] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1089.300212] cfg80211: Restoring regulatory settings
[ 1089.300220] cfg80211: Calling CRDA to update world regulatory domain
[ 1089.310712] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1089.310720] cfg80211: World regulatory domain updated:
[ 1089.310725] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1089.310732] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1089.310739] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1089.310745] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1089.310750] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1089.310756] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1090.378561] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1090.380402] wlan0: authenticated
[ 1090.380785] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1090.383614] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1090.383621] wlan0: associated
[ 1208.803262] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1208.832173] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1208.832182] cfg80211: Restoring regulatory settings
[ 1208.832202] cfg80211: Calling CRDA to update world regulatory domain
[ 1208.842404] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1208.842412] cfg80211: World regulatory domain updated:
[ 1208.842416] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1208.842424] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1208.842430] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1208.842436] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1208.842442] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1208.842448] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1209.910932] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1209.912751] wlan0: authenticated
[ 1209.913023] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1209.915762] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1209.915769] wlan0: associated
[ 1329.333600] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1329.368163] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1329.368173] cfg80211: Restoring regulatory settings
[ 1329.368195] cfg80211: Calling CRDA to update world regulatory domain
[ 1329.378715] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1329.378723] cfg80211: World regulatory domain updated:
[ 1329.378727] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1329.378735] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1329.378741] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1329.378747] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1329.378753] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1329.378759] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1330.447107] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1330.449032] wlan0: authenticated
[ 1330.449391] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1330.452185] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1330.452192] wlan0: associated
[ 1448.874750] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1448.912199] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1448.912208] cfg80211: Restoring regulatory settings
[ 1448.912216] cfg80211: Calling CRDA to update world regulatory domain
[ 1448.922503] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1448.922511] cfg80211: World regulatory domain updated:
[ 1448.922515] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1448.922523] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1448.922529] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1448.922535] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1448.922541] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1448.922547] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1449.990475] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1449.992314] wlan0: authenticated
[ 1449.992705] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1449.995493] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1449.995499] wlan0: associated
[ 1569.398767] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1569.440137] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1569.440150] cfg80211: Restoring regulatory settings
[ 1569.440170] cfg80211: Calling CRDA to update world regulatory domain
[ 1569.450476] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1569.450484] cfg80211: World regulatory domain updated:
[ 1569.450488] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1569.450496] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1569.450502] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1569.450509] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1569.450515] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1569.450521] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1570.518501] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1570.520288] wlan0: authenticated
[ 1570.520675] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1570.523474] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1570.523481] wlan0: associated
[ 1688.949931] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1688.984139] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1688.984148] cfg80211: Restoring regulatory settings
[ 1688.984167] cfg80211: Calling CRDA to update world regulatory domain
[ 1688.994338] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1688.994345] cfg80211: World regulatory domain updated:
[ 1688.994350] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1688.994357] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1688.994363] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1688.994369] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1688.994375] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1688.994381] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1690.066584] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1690.068416] wlan0: authenticated
[ 1690.068803] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1690.071579] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1690.071586] wlan0: associated
[ 1809.477216] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1809.512145] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1809.512155] cfg80211: Restoring regulatory settings
[ 1809.512175] cfg80211: Calling CRDA to update world regulatory domain
[ 1809.522828] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1809.522836] cfg80211: World regulatory domain updated:
[ 1809.522840] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1809.522847] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1809.522854] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1809.522860] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1809.522866] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1809.522871] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1810.595906] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1810.597822] wlan0: authenticated
[ 1810.598057] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1810.600883] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1810.600888] wlan0: associated
[ 1929.018336] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 1929.060214] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1929.060224] cfg80211: Restoring regulatory settings
[ 1929.060245] cfg80211: Calling CRDA to update world regulatory domain
[ 1929.070465] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1929.070473] cfg80211: World regulatory domain updated:
[ 1929.070477] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1929.070485] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1929.070491] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1929.070498] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1929.070504] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1929.070510] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1930.130619] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 1930.132450] wlan0: authenticated
[ 1930.132836] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 1930.135593] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=3)
[ 1930.135600] wlan0: associated
[ 2049.568966] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 2049.604212] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2049.604222] cfg80211: Restoring regulatory settings
[ 2049.604230] cfg80211: Calling CRDA to update world regulatory domain
[ 2049.614364] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2049.614372] cfg80211: World regulatory domain updated:
[ 2049.614377] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2049.614384] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2049.614390] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2049.614396] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2049.614402] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2049.614408] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2050.682847] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 2050.684667] wlan0: authenticated
[ 2050.685053] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 2050.687880] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=2)
[ 2050.687888] wlan0: associated
[ 2169.108581] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 2169.144236] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2169.144245] cfg80211: Restoring regulatory settings
[ 2169.144266] cfg80211: Calling CRDA to update world regulatory domain
[ 2169.154356] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2169.154363] cfg80211: World regulatory domain updated:
[ 2169.154368] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2169.154375] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2169.154382] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2169.154388] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2169.154394] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2169.154399] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2170.226797] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 2170.228618] wlan0: authenticated
[ 2170.229006] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 2170.231835] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=2)
[ 2170.231842] wlan0: associated
[ 2289.655721] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 2289.696169] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2289.696178] cfg80211: Restoring regulatory settings
[ 2289.696198] cfg80211: Calling CRDA to update world regulatory domain
[ 2289.706442] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2289.706449] cfg80211: World regulatory domain updated:
[ 2289.706454] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2289.706461] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2289.706468] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2289.706474] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2289.706480] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2289.706486] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2290.774486] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 2290.776592] wlan0: authenticated
[ 2290.776871] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 2290.779577] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=2)
[ 2290.779585] wlan0: associated
[ 2409.196837] wlan0: deauthenticated from c8:6c:87:f2:17:50 (Reason: 3)
[ 2409.236162] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2409.236172] cfg80211: Restoring regulatory settings
[ 2409.236180] cfg80211: Calling CRDA to update world regulatory domain
[ 2409.246548] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2409.246556] cfg80211: World regulatory domain updated:
[ 2409.246561] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2409.246568] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2409.246575] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2409.246581] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2409.246586] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2409.246592] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2410.314549] wlan0: authenticate with c8:6c:87:f2:17:50 (try 1)
[ 2410.316289] wlan0: authenticated
[ 2410.316673] wlan0: associate with c8:6c:87:f2:17:50 (try 1)
[ 2410.319412] wlan0: RX ReassocResp from c8:6c:87:f2:17:50 (capab=0x411 status=0 aid=2)
[ 2410.319419] wlan0: associated

```

---

### Post by MRCRUSHER on 2012-08-17
> **Marric said:**
> Did you reboot?

What computer are you using?

Yes, I reboot every time I did as you suggested.

My computer is Sony VGN-C23S/L

---

### Post by Marric on 2012-08-17
Maybe found a solution for you here [http://ubuntuforums.org/showthread.php?t=1966635](http://ubuntuforums.org/showthread.php?t=1966635) .

---

### Post by Marric on 2012-08-17
With your computer it is not possible to switch cards. It's the one or the other.
There are lots of brightness issues out there with Sony laptops.
Just try the link above and tell us if it worked out for you.

---

### Post by MRCRUSHER on 2012-08-17
OK. Thank you very much. I will try and let you know if it works or not.

---

### Post by MRCRUSHER on 2012-08-17
This is one of the solution I tried before and it did not work out for me. :(

---

### Post by Marric on 2012-08-17
When you used this
```
sudo setpci -s "01:00.0" F4.B=10
sudo setpci -s "01:00.0" F4.B=80
```
was there any difference?

---

### Post by MRCRUSHER on 2012-08-18
Sorry that get back to you a bit late.

When I tried both command, the brightness is the same (at the highest level). I do not notice any difference.

---

### Post by Marric on 2012-08-18
Did you already try xbacklight ?

```
sudo apt-get install xbacklight
```

then us it with
```
xbacklight -dec 10
```
```
xbacklight -inc 10
```

---

### Post by NikTh on 2012-08-18
Hi ,

this is from your dmesg results .. 

```
[   24.411027] sonypi: please try the sony-laptop module instead and  report failures, see also  http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
``` 
and this is your problem. I don't know if is difficult or not to solve this or if anyone can solve this. 

You can try to solve it following the page that dmesg provide [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers) and you will understand the nature of the problem. 

Another workaround might be to change the brightness with echo command , but before this , I want one more result
```
cat /sys/class/backlight/brightness
cat /sys/class/backlight/max_brightness
``` 
Thanks

---

### Post by MRCRUSHER on 2012-08-18
> **Marric said:**
> Did you already try xbacklight ?

```
sudo apt-get install xbacklight
```then us it with
```
xbacklight -dec 10
``````
xbacklight -inc 10
```
I have tried xbacklight but it still does not work.

---

### Post by MRCRUSHER on 2012-08-18
> **NikTh said:**
> Hi ,

this is from your dmesg results .. 

```
[   24.411027] sonypi: please try the sony-laptop module instead and  report failures, see also  http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
```and this is your problem. I don't know if is difficult or not to solve this or if anyone can solve this. 

You can try to solve it following the page that dmesg provide [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers]("http://www.linux.it/%7Emalattia/wiki/index.php/Sony_drivers") and you will understand the nature of the problem. 

Another workaround might be to change the brightness with echo command , but before this , I want one more result
```
cat /sys/class/backlight/brightness
cat /sys/class/backlight/max_brightness
```Thanks
Here is the result:

$ cat /sys/class/backlight/sony/brightness 
0

$ cat /sys/class/backlight/sony/max_brightness 
7

$ cat /sys/class/backlight/sony/actual_brightness 
0

I will try to install sony-laptop module and will report the result.

---

### Post by MRCRUSHER on 2012-08-18
I have "sony_laptop" module installed by checking with this command:

$ lsmod |grep sony
```
sony_laptop            39681  0 
sonypi                 19573  0 

```

Is it the same module as "sony-laptop"?

---

### Post by NikTh on 2012-08-18
Hi , 
yes its the same. I think you don't need to install anything. 

Try this commands and see if brightness changed 
```
sudo -i 
echo 3 > /sys/class/backlight/sony/brightness
exit
```You can also try this commands 
```
sudo -i 
echo 3 > /sys/class/backlight/sony/actual_brightness
exit
```Always use **exit** command if you login as root with** sudo -i** command. It is dangerous to stay logged in shell like root.

Thanks

---

### Post by MRCRUSHER on 2012-08-18
I did this command
```
sudo -i  
echo 3 > /sys/class/backlight/sony/brightness 
exit
```and nothing change.
I also tried
```
sudo -i  
echo 3 > /sys/class/backlight/sony/actual_brightness 
exit
```I got permission denied

---

### Post by NikTh on 2012-08-19
Hi , 
please open a terminal and try this ..
```
sudo modprobe -r -f -v sonypi 
sudo modprobe -r -f -v sony-laptop  
sudo modprobe sony-laptop kbd_backlight=1
``` 

and see if backlight works with keys combination. 
If not , try to modprobe the sonypi also .. 
```
sudo modprobe sonypi
``` 
Thanks

---

### Post by MRCRUSHER on 2012-08-19
I have blacklisted sonypi but still no luck on the brightness control.

---

### Post by MRCRUSHER on 2012-08-19
I don't know if this would help you to figure it out the solution for me or not. I use the following command:

$ ls -al /sys/class/backlight/
total 0
drwxr-xr-x  2 root root 0 Aug 20  2012 .
drwxr-xr-x 47 root root 0 Aug 20  2012 ..
lrwxrwxrwx  1 root root 0 Aug 19 20:56 sony -> ../../devices/virtual/backlight/sony

The sony is point to virtual device instead of the actual pci device (the video card). When I boot with Ubuntu 10.10 CD and choose try without install, I saw 2 folders in the /sys/class/backlight/ which are "nv_backlight" and "sony". The nv_backlight point to the pci device and sony point to the virtual device. When I press Fn+F5 and Fn+F6 to change the brightness, it works and the "actual_brightness" in the "nv_backlight" changes. So how to make the nv_backlight appear in the /sys/class/backlight/ in Ubuntu 12.04?

---

### Post by NikTh on 2012-08-19
Hey , 
I edited  my post (#40) , take a look again. 
Thanks

---

### Post by MRCRUSHER on 2012-08-19
> **NikTh said:**
> Hi , 
please open a terminal and try this ..
```
sudo modprobe -r -f -v sonypi 
sudo modprobe -r -f -v sony-laptop  
sudo modprobe sony-laptop kbd_backlight=1
```and see if backlight works with keys combination. 
If not , try to modprobe the sonypi also .. 
```
sudo modprobe sonypi
```Thanks

I have tried these (without reboot). The brightness control is still not working.

---

### Post by NikTh on 2012-08-19
Hi , 
ok this is my last idea... (for now)

we will blacklist sonypi module and we force modprobe the sony-laptop module with parm of kbd_backlight. 

```
echo 'blacklist sonypi' | sudo tee -a /etc/modprobe.d/blacklist.conf
```then 
```
gksudo gedit /etc/rc.local
``` and _before **exit 0**_ add these lines with same order
```
modprobe -r -f sony-laptop
modprobe sony-laptop kbd_backlight=1
```reboot and open a terminal to check the modules 
```
lsmod | grep sony
```Thanks

---

### Post by MRCRUSHER on 2012-08-19
> **NikTh said:**
> Hi , 
ok this is my last idea... (for now)

we will blacklist sonypi module and we force modprobe the sony-laptop module with parm of kbd_backlight. 

```
echo 'blacklist sonypi' | sudo tee -a /etc/modprobe.d/blacklist.conf
```then 
```
gksudo gedit /etc/rc.local
``` and _before **exit 0**_ add these lines with same order
```
modprobe -r -f sony-laptop
modprobe sony-laptop kbd_backlight=1
```reboot and open a terminal to check the modules 
```
lsmod | grep sony
```Thanks

I follow your suggestion. After reboot, 

$ lsmod | grep sony
```
sony_laptop            39681  0 
sonypi                 19573  0 

```There are both sonypi and sony-laptop module loaded.

I check the blacklist.conf, there is blacklist sonypi at the end.

$ cat /etc/modprobe.d/blacklist.conf
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist sonypi


```

I forget to inform you that the brightness control is still not working.

---

### Post by NikTh on 2012-08-19
Ok , so lets try this... 

remove all lines and add a single line. 
```
gksudo gedit /etc/rc.local
```rc.local must looks like this..
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
(sleep 10 ; modprobe -rf sonypi ; modprobe -rf sony-laptop ; modprobe sony-laptop kbd_backlight=1) & 
exit 0
```reboot and wait 10 seconds after login and then give the result again.. 
```
lsmod | grep sony
```or check the Fn keys. 
Thanks

---

### Post by MRCRUSHER on 2012-08-19
$ lsmod | grep sony
```

sony_laptop            39681  0 
```

OK. Now there is only "sony_laptop". However, the function key still could not change the brightness.

---

### Post by NikTh on 2012-08-19
Ok , now we succeed with modules.. try again the parms in grub , as you did 

acpi_osi= 
or
acpi_osi=Linux
or
acpi_backlight=vendor 
or even 
acpi_osi="Windows 2006" (with quotes) or without quotes. 

Take a look at here --> [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

there are many parms you can add in grub for this propose (backlight) . 
You can try them separately or even mixed up (2 parms together).
Hopefully something will work. 
Thanks

---

### Post by MRCRUSHER on 2012-08-19
I tried to edit /etc/default/grub with the suggested parameters. I tried 1 param and 2 params (mixing acpi_osi with acpi_backlight=vendor). However, I still could not control brightness.

Each time, I do "sudo update-grub" and reboot.

---

### Post by NikTh on 2012-08-19
Hi , 
I thought if we rmmod the sonypi (problematic module according dmesg) and modprobe the sony-laptop module with parm of kbd_backlight , the Fn keys could work. 
```
modinfo sony-laptop | grep kbd
``` for more info. 

I don't know what to suggest now , except to try different parms in grub . 
Maybe another idea could be to install the old kernel from the Ubuntu release where Fn keys worked ? 
Or try the newest release of Ubuntu 12.10 from a Live Usb . Includes kernel 3.5 with lot of changes. 
Get the iso from here --> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and try to see if works.
Its better to move on (with a newer kernel) instead to move back with an older. 
Thanks

---

### Post by MRCRUSHER on 2012-08-19
[COLOR=Black]Thank you very much, NikTh and Marric for all the help to solve my brightness problem. I tried to make Live USB and boot with it but it seems that my notebook could not boot from USB (even I change the boot order to boot from USB first).
[/COLOR]

---

### Post by NikTh on 2012-08-20
Hi , 
CD maybe ? Try CD instead of Usb. We want only to test the newer kernel with your Graphics. 
If you cannot boot with anyway  , then we can proceed with the newest mainline Kernel installation to your system and see how its going.
Thanks

---

### Post by fleurdeau on 2012-08-20
Hi,

Thanks a lot for this thread very interesting. I'm in the same case of Mrcrusher with a Sony Vaio VGN-SZ1M and ubuntu 12.04, gnome classic3.4.2, Nvidia GeForce7400 : I've tested ALL these propositions and, bad luck, anyone is good for me. 

For months, I'm looking for a solution... but not. So, I've wrote a workaround using nvidia-settings and his configuration  file [FONT=Courier New] ~/.nvidia-settings-rc[/FONT] : a script change values of RGB brightness and contrast in this file and reload it by the [FONT=Courier New]nvidia-settings -l[/FONT] command.

This script is launched by Fn hotkeys and, after some acpid modifications, I'm able to control brightness with Fn keys. Youpi !

So, if you want to test this solution :

1/ Edit a script /etc/acpi/nvidia-brightness-updown.sh with your favourite editor in root mode :
[FONT=Courier New]sudo vi /etc/acpi/nvidia-brightness-updown.sh
[/FONT]
2/ Copy and paste :


[FONT=Courier New]#!/bin/bash
# nvidia-brightness-updown.sh
#
# Brightness control for VAIO_SZ1M sony laptop with nvida GeForce Go7400
#
# Read file ~/.nvidia-settings-rc, read actuals RGB Brightness values 
# and rewrite these values more or less one step 

function usage()
{
  echo "Usage : nvidia-brightness-updown.sh step"
  echo "Up or down brightness value by "step" of nvidia card"
  echo ""
  echo "Brightness is controlled by RGB values (range -1.0 to +1.0) in the"
  echo "nvidia-settings utility config file, ~/.nvidia-settings-rc"
  echo ""
  echo "Sample : "
  echo "nvidia-brightness-updown.sh -0.1"
  echo "       Down brightness of 0.1 relative value"
  echo "nvidia-brightness-updown.sh 0.1"
  echo "       Up brightness of 0.1 relative value"
}

if [ $# -ne 1 ]; then
  usage
  exit 1
fi

STEP=$1
NVIDIA_CFG=~/.nvidia-settings-rc

if [ ! -f $NVIDIA_CFG ]; then
  echo "Rebuild ~/.nvidia-settings-rc file..."
  nvidia-settings -r
  echo "Done"
fi

function updown()
{
  RGB=$1
  Line=`grep $RGB $NVIDIA_CFG`
  Value=`echo $Line | cut -d\= -f2`
  Value=`echo $Value + $STEP | bc`
  if [ `echo "$Value > 1.0" | bc` -eq 1 ]; then
    Value=1.000000
  fi;
  if [ `echo "$Value < -1.0" | bc` -eq 1 ]; then
    Value=-1.000000
  fi;
  NewLine=`grep "$RGB" $NVIDIA_CFG | cut -d\= -f1`"="$Value
  sed --in-place=.bak "s#$Line#$NewLine#" $NVIDIA_CFG 

}

updown RedBrightness
updown GreenBrightness
updown BlueBrightness
updown RedContrast
updown GreenContrast
updown BlueContrast

nvidia-settings -l
exit 0
[/FONT]
3/ Save and make it executable
[FONT=Courier New]sudo chmod a+x /etc/acpi/nvidia-brightness-updown.sh
[/FONT]
4/ Edit the two handlers of hotkeys events and modify them like this :
[FONT=Courier New]sudo vi /etc/acpi/events/sony-brightness-up
[/FONT]
[FONT=Courier New]# /etc/acpi/events/sony-brightness-up
event=sony/hotkey SPIC 00000001 00000011
action=/etc/acpi/nvidia-brightness-updown.sh 0.1
[/FONT]
and 

[FONT=Courier New]sudo vi /etc/acpi/events/sony-brightness-down

# /etc/acpi/events/sony-brightness-down
event=sony/hotkey (SPIC|SNC) 00000001 00000010
action=/etc/acpi/nvidia-brightness-updown.sh -0.1
[/FONT]
It should be sufficient, but not... For reasons out of my mind, acpid daemon don't capture this events, but acpid in command line yes... If someone could explain this, I will be happy !

So, the next workaround :

5 / Remove acpid service by simply renaming /etc/init/acpid.conf
[FONT=Courier New]sudo mv /etc/init/acpid.conf /etc/init/acpid.conf.noservice
[/FONT]
This should immediately stop acpid daemon (if not, kill it ! [FONT=Courier New]stop acpid[/FONT]) and should not reload it after reboot.

6 / Use Outil System -> Preferences -> applications au démarrage of gnome to start acpid (I let you translate menus in your system language...) :
Add a new application named acpid for instance and with [FONT=Courier New]/usr/sbin/acpid[/FONT] in the command line.

7 / Setuid root /usr/sbin/acpid :
[FONT=Courier New]sudo chmod u+s /usr/sbin/acpid
[/FONT]
8 / Reboot (or kill all acpid processus and restart X only)

This method is not really "in the state of the art", but, on my machine, that works !
One bug today : you need to kill all acpid processus before restart X for brightness control to work. Don't ask me why, even by testing presence of /var/run/acpid.pid before launching a new acpid command, it don't work... Here too, if somebody have a explanation... But it's ok with hibernation and sleeping, cool !

Hope this will be useful.

---

### Post by Marric on 2012-08-20
Salut fleurdeau et bienvenue au forum. Bon travail. I hope this will help mrcrusher after all.

---

### Post by MRCRUSHER on 2012-08-20
Thank you very much, fleurdeau. Your solution seem to work on my computer. I am now able to control the brightness.

NikTh, if you want to test the new kernel with my graphic card, I am happy to do that. The Ubuntu 12.10 is a little big for CD because on the [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/), it said that:

Warning: This image is oversized (which is a bug) and will not fit onto a standard 703MiB CD. However, you may still test it using a DVD, a USB drive, or a virtual machine.

So I will burn it on the DVD rather than using USB.

Again, thank you very much for all the help, NikTh, Marric, and fleurdeau.

---

### Post by NikTh on 2012-08-21
Hi , 
very good workaround @fleurdeau , but this is not a solution . We want to make the brightness keys to work without scripts or hacks. 
@MRCRUSHER it will be good to open a bug with your problem, an offer to Free Software to help developers solve this. 
Yes burn the .iso of 12.10   to a DVD and test it , if problem exists then mention that too , in your bug report. 
Glad you found at least a workaround to your problem (thanks to @fleurdeau) 
Thanks

---

### Post by MRCRUSHER on 2012-08-21
I just notice that when I lower the brightness as fleurdeau suggest, the mouse cursor is still very bright at the maximum brightness. So this is not actually solution but the work around.

So should I change the topic back to unsolved?

NikTh, I will try the Ubuntu 12.10 and let you know.

---

### Post by coffeecat on 2012-08-21
> **MRCRUSHER said:**
> 
NikTh, I will try the Ubuntu 12.10 and let you know.

For your own peace of mind, I suggest you delay that for a while! :wink: At the moment using the proprietary nvidia driver is broken in 12.10. For more details see here:

[http://ubuntuforums.org/showthread.php?t=2043695](http://ubuntuforums.org/showthread.php?t=2043695)

12.10 is unusable on my (different) Sony Vaio just now. The proprietary nvidia driver causes me to go into the endless login loop and with the open source nouveau driver, the desktop flickers and is unusable. And I've lost brightness control! :) 

Give it a week or so, and keep an eye on the Quantal testing forum, and it will probably be worth while trying 12.10 once this issue has been resolved.

---

### Post by MRCRUSHER on 2012-08-21
Thank you, coffeecat. I will wait for a while and will try Ubuntu 12.10 later or when it is released in October. 

So should I change the title of this topic back to unsolved? Because the current solution is the workaround but not the actual solution.

---

### Post by coffeecat on 2012-08-21
> **MRCRUSHER said:**
> So should I change the title of this topic back to unsolved? Because the current solution is the workaround but not the actual solution.

That's your choice, and you're very welcome to mark this thread as solved or not depending on whether you would like to see more suggestions.

Sometimes you'll only ever get a workaround rather than a true solution with some hardware. There is such a huge variety of hardware out there, that it is amazing that so much works out of the box anyway. Unfortunately Sony seems to use a number of different implementations for its function keys. For my first Vaio (2004 or thereabouts) I had to use an ugly hack to get the Fn keys to work at all. With my second (about 2009) the Fn keys worked out of the box with every version of Ubuntu that I tried - except 10.10 for some reason. And with my current Vaio with nvidia graphics, only the brightness keys don't work, but that is partially solved with the "fix" I posted earlier, and I'm sorry to hear it didn't work with your machine. Even that fix is partially unsatisfactory. The brightness setting is not remembered between reboots, although I confess I haven't had the energy to try to hunt down a solution to that as well, so the fix I use is really only a workaround.

---

### Post by NikTh on 2012-08-21
Hi , 
if you want , edit your first post and linked this workaround (here is the link [http://ubuntuforums.org/showpost.php?p=12183956&postcount=54](http://ubuntuforums.org/showpost.php?p=12183956&postcount=54) ) cuz its difficult for someone to find it .. 60 answers in here. 
Thanks

---

### Post by MRCRUSHER on 2012-08-21
OK, done. Thank you for suggestion.

---

### Post by souri on 2012-09-04
> **Marric said:**
> your integrated graphics controller does not show up.  It's probably disabled in the bios. Try to activate it there (both cards).
Please output
```
lsmod | grep i915
```


I am using the following command and it i s working for me:
xrandr --output LVDS1 --brightness 0.8

---

