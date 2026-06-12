---
title: "New computer - no sound"
date: 2023-08-01
forum: Hardware
---

### Post by txtinman on 2023-08-01
I recently purchased a mini pc computer with Windows 11 installed. I installed Ubutu along side Win11 and dual boot. When in Windows the sound plays through the speakers plugged into the headphone jack on the PC and also from the monitor I'm using if I choose it. When running Ubuntu I get no sound from the speakers and I don't even get the option of playing thru the monitor. I've tried a few fixes by installing pulseaudio and configuring it, but no joy. If anyone can help please do. It will be appreciated.

Here is my system info: 

```
Starting the Ubuntu Forums 'system-info' Report: 2023-08-01  13:05:34 CDT (-0500)
	Part of the Ama-gi Project
	Version: 02.00-08, Script Date: 2023.05.24

---------------------------------------------------------------
Main Complaint: sound does not work
Problem Description:  no sound
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: Intel(R) Core(TM) i7-10810U CPU @ 1.10GHz
    Vendor: Intel Corp.
    Physical id: 48
    Bus info: cpu@0
    Version: 6.166.0
    Serial: [REMOVED]
    Slot: U3E1
    Size: 2365MHz
    Capacity: 4900MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse 
        sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art 
        arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid 
        aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 
        sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt 
        tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch 
        cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced 
        tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 
        avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt 
        xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify 
        hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
    Configuration: cores=6 enabledcores=6 microcode=244 threads=12

computer
    Description: Desktop Computer
    Product: (Default string)
    Vendor: Default string
    Version: Default string
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-3.2.0 dmi-3.2.0 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        family=Default string
        sku=Default string
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends Inc.
Bios Version:        CK12V101
Bios Release:        5.17
Board Vendor:        
Board Name:          
Board Version:       Default string
Board Serial:        Default string
Board Asset Tag:     Default string

Current boot mode:   UEFI Firmware mode
   --- SecureBoot Status from 'mokutil':
SecureBoot disabled
Platform is in Setup Mode


---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:           15855        3090       10555         759        3296       12765
Swap:           1906           0        1906

---------- Swap Information:
  --- Info from 'fstab'
# swap was on /dev/sda6 during installation
UUID=13adb9ff-d1b0-474f-903f-0f7a26045877 none            swap    sw              0       0

  --- Info from '/proc/swaps'
Filename				Type		Size		Used		Priority
/dev/sda6                               partition	1952764		0		-2

  --- System Swapiness Settings
Valid swappiness settings are from 10 - 60 . 
Current setting in '/proc/sys/vm/swappiness': 60 
Current configuration setting in '/etc/sysctl.conf file: 


---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000

For more detailed wireless information, get and run the script at https://github.com/UbuntuForums/wireless-info 

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: ubuntu-kde


---------- Storage Controller Information From 'lspci':
00:17.0 SATA controller: Intel Corporation Comet Lake SATA AHCI Controller (prog-if 01 [AHCI 1.0])
	DeviceName: Onboard - SATA
	Subsystem: Intel Corporation Comet Lake SATA AHCI Controller
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 125
	Memory at b1314000 (32-bit, non-prefetchable) [size=8K]
	Memory at b1320000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 5090 [size=8]
	I/O ports at 5080 [size=4]
	I/O ports at 5060 [size=32]
	Memory at b131f000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Kernel driver in use: ahci
	Kernel modules: ahci


---------- File system specs from 'df -h':
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda5      ext4  115G   12G   97G  11% /
/dev/sda1      vfat   96M   61M   36M  63% /boot/efi
/dev/sda7      ext4   76G   17G   56G  23% /home

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: FPT330M8SSD512G 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F7334934-C40D-4888-9029-A8FC502B0559

Device         Start        End   Sectors   Size Type
/dev/sda1       2048     206847    204800   100M EFI System
/dev/sda2     206848     239615     32768    16M Microsoft reserved
/dev/sda3     239616  588974079 588734464 280.7G Microsoft basic data
/dev/sda4  998576128 1000214527   1638400   800M Windows recovery environment
/dev/sda5  588974080  833114111 244140032 116.4G Linux filesystem
/dev/sda6  833114112  837019647   3905536   1.9G Linux swap
/dev/sda7  837019648  998574079 161554432    77G Linux filesystem

Partition table entries are not in disk order.


---------- Disk/Partition Information From 'lsblk':
NAME     SIZE FSTYPE   LABEL    MOUNTPOINT                   MODEL
sda    476.9G                                                FPT330M8SSD512G
|_sda1   100M vfat     SYSTEM   /boot/efi                    
|_sda2    16M                                                
|_sda3 280.7G ntfs     Windows                               
|_sda4   800M ntfs     Recovery                              
|_sda5 116.4G ext4              /                            
|_sda6   1.9G swap              [SWAP]                       
|_sda7    77G ext4              /home                        
   ------- 'lsblk' information continued ...
NAME   HOTPLUG PARTUUID                             UUID
sda          0                                      
|_sda1       0 b9799250-dbe4-4d09-8efd-65db6d926aa1 A055-BD23
|_sda2       0 3a1895f6-e53a-46cf-83c7-b1a62f8c8f88 
|_sda3       0 47122016-c818-40ce-a711-1a6f4836346c B4E6566DE6562FBA
|_sda4       0 7f74531f-c997-453f-a454-b64fd5684320 40CE56BECE56AC42
|_sda5       0 528f2e5d-acff-47da-98d0-40c36b4d6970 56688efd-97dd-4b7d-ad14-c50e39304701
|_sda6       0 0c90bc63-3b46-4e7b-b0cf-6890c08e85e7 13adb9ff-d1b0-474f-903f-0f7a26045877
|_sda7       0 6efb3736-d3f2-42f7-a15b-fb6befcf86e2 b26db837-a89e-4d4e-8af7-55f459a50894

----------  BTRFS Information:
There are no BTRFS vdev's present.

----------  LVM2 Information:
There are no LVM2 volumes present.

----------  mdadm RAID Information:
No active md devices present.
---------- Mount Details of '/etc/fstab':
UUID=56688efd-97dd-4b7d-ad14-c50e39304701 /               ext4    errors=remount-ro 0       1
UUID=A055-BD23  /boot/efi       vfat    umask=0077      0       1
UUID=b26db837-a89e-4d4e-8af7-55f459a50894 /home           ext4    defaults        0       2
UUID=13adb9ff-d1b0-474f-903f-0f7a26045877 none            swap    sw              0       0

---------- Current Mount Details of 'mount':
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda5 on /var/snap/firefox/common/host-hunspell type ext4 (ro,noexec,noatime,errors=remount-ro)
/dev/sda7 on /home type ext4 (rw,relatime)

For more detailed disk Information, please run the 'boot-info' script 
from: (STABLE) https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair 

---------- USB Information from 'lsusb -t -v':
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 3: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        ID 046d:c534 Logitech, Inc. Unifying Receiver
    |__ Port 3: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        ID 046d:c534 Logitech, Inc. Unifying Receiver
    |__ Port 7: Dev 3, If 0, Class=Wireless, Driver=btusb, 12M
        ID 0bda:b85b Realtek Semiconductor Corp. 
    |__ Port 7: Dev 3, If 1, Class=Wireless, Driver=btusb, 12M
        ID 0bda:b85b Realtek Semiconductor Corp. 

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Comet Lake UHD Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: 
           irq:127 
           memory:b0000000-b0ffffff 
           memory:a0000000-afffffff 
           ioport:5000(size=64) 
           memory:c0000-dffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: KDE 
The Current Desktop Session is: plasma 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 16384 x 16384
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
The Current Session Type is: x11 
The Current Display Manager is: 
The Current Desktop Theme: 'Breeze'
The Current Virtual TTY's being used are:
	TTY#	Used By
	tty1	Xorg
	pts/1	bash
	pts/1	system-info
	pts/1	system-info
	pts/1	sed
	pts/1	system-info
	pts/1	ps
	pts/1	awk

---------- Sound Device Information From 'lspci':
00:1f.3 Multimedia audio controller: Intel Corporation Comet Lake PCH-LP cAVS
	DeviceName: Onboard - Sound
	Subsystem: Intel Corporation Comet Lake PCH-LP cAVS
	Flags: bus master, fast devsel, latency 32, IRQ 131
	Memory at b1310000 (64-bit, non-prefetchable) [size=16K]
	Memory at b1000000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [80] Vendor Specific Information: Len=14 <?>
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: sof-audio-pci-intel-cnl
	Kernel modules: snd_hda_intel, snd_sof_pci_intel_cnl


For more detailed audio information, get and run the script at: http://www.alsa-project.org/alsa-info.sh 

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://us.archive.ubuntu.com/ubuntu/ lunar main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lunar-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lunar universe
deb http://us.archive.ubuntu.com/ubuntu/ lunar-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ lunar multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lunar-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lunar-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lunar-security main restricted
deb http://security.ubuntu.com/ubuntu lunar-security universe
deb http://security.ubuntu.com/ubuntu lunar-security multiverse

Sources List from SourcesD:

---------- KeyMap and Locale Information from from various sources:
   --- Keymap Info from 'setxkbmap' ----
rules:      evdev
model:      pc104
layout:     us

   --- Locale Info from 'localectl' ----
System Locale: LANG=en_US.UTF-8
    VC Keymap: (unset)
   X11 Layout: us
    X11 Model: pc105

---------- Other Details from 'Various':
The current kernel version is:       6.2.0-26-generic 
    --- Operating System Release Description --- 
The current release description is:  Ubuntu 23.04 

Original Installation Date:          2023-07-21+13:17:06 
Original Installation Media: Kubuntu 23.04 "Lunar Lobster" - Release amd64 (20230414.1)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

   --- Hardware Enablement Stack (HWE) Informationt:
These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 6.2.0.26.26
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 6.2.0.20.20

   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-22.04 was not detected. Please check 
kernel version to verify range

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
gnucash
gramps
keepassxc
kio-gdrive
overgrive
pavucontrol
pulseaudio
thunar
thunderbird-locale-en

   --- Installed Snap Package List:
bare
core22
firefox
gnome-42-2204
gtk-common-themes
snapd

   --- Installed Flatpak Package List:
Flatpak is not installed

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
txtinman tty1         Aug  1 09:16 (:0)

The User running this script was: txtinman
uid=1000(txtinman)
gid=1000(txtinman)
groups=1000(txtinman),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
100(users),119(lpadmin),129(sambashare)

The 'system-info' script was booted from an installed system

The 'system-info' script seems to be running locally

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=56688efd-97dd-4b7d-ad14-c50e39304701 ro quiet splash vt.handoff=7

---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    curl

*** End Of Report ***

```

---

