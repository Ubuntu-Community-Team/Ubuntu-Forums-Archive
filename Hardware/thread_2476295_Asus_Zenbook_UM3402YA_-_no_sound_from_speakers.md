---
title: "Asus Zenbook UM3402YA - no sound from speakers"
date: 2022-06-22
forum: Hardware
---

### Post by nikola-jandik-seznam on 2022-06-22
helllo, here is some new sound chip CS35L41 from cirrus logic, last hw from them was vga in isa slot :-) now its 

headphones sound - ok

 hdmi sound - ok

 bluetooth sound - ok after patching kernel 

```
Starting the Ubuntu Forums 'system-info' Report: 2022-06-22  14:24:18 CEST (+0200)
    Part of the Ama-gi Project
    Version: 01.00-19, Script Date: 2022.06.21

---------------------------------------------------------------
Main Complaint: basic
Problem Description:  no sound on speakers
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: AMD Ryzen 5 5625U with Radeon Graphics
    Vendor: Advanced Micro Devices [AMD]
    Physical id: 18
    Bus info: cpu@0
    Version: 25.80.0
    Serial: [REMOVED]
    Slot: FP6
    Size: 2075MHz
    Capacity: 2301MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
        syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good 
        nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq 
        monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c 
        rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 
        3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb 
        bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba ibrs 
        ibpb stibp vmmcall fsgsbase bmi1 avx2 smep bmi2 erms invpcid cqm rdt_a 
        rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves 
        cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf 
        xsaveerptr rdpru wbnoinvd cppc arat npt lbrv svm_lock nrip_save 
        tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold 
        avic v_vmsave_vmload vgif v_spec_ctrl umip pku ospke vaes vpclmulqdq 
        rdpid overflow_recov succor smca fsrm cpufreq
    Configuration: cores=6 enabledcores=6 microcode=173015052 
        threads=12

computer
    Description: Notebook
    Product: Zenbook UM3402YA_UM3402YA
    Vendor: ASUSTeK COMPUTER INC.
    Version: 1.0
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-3.3.0 dmi-3.3.0 smp vsyscall32
    Configuration:
        boot=normal
        chassis=notebook
        family=Zenbook
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends International, LLC.
Bios Version:        UM3402YA.303
Bios Release:        5.19
Board Vendor:        ASUSTeK COMPUTER INC.
Board Name:          UM3402YA
Board Version:       1.0
Board Serial:        N309NBLP000ZW6MB
Board Asset Tag:     ATN12345678901234567

Current boot mode:   UEFI Firmware mode
   --- SecureBoot Status from 'mokutil':
SecureBoot disabled


---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:            15Gi       2.9Gi       9.8Gi       102Mi       2.4Gi        11Gi
Swap:          2.0Gi          0B       2.0Gi

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500
    inet [REMOVED]
    inet6 [REMOVED]

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 500

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: gandalf-Zenbook-UM3402YA-UM3402YA


---------- Storage Controller Information From 'lspci':
03:00.0 Non-Volatile memory controller: Intel Corporation Device f1aa (rev 03) (prog-if 02 [NVM Express])
    Subsystem: Intel Corporation Device 390f
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort+ <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 64
    NUMA node: 0
    IOMMU group: 11
    Region 0: Memory at fcd00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable+ 64bit+
        Address: 0000000000000000  Data: 0000
        Masking: 00000000  Pending: 00000000
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 512 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+ SlotPowerLimit 75.000W
        DevCtl:    CorrErr+ NonFatalErr+ FatalErr+ UnsupReq+
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop- FLReset-
            MaxPayload 512 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 8GT/s, Width x4, ASPM L1, Exit Latency L1 <8us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp+
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes, Disabled- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s (downgraded), Width x4 (ok)
            TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+ NROPrPrP- LTR+
             10BitTagComp- 10BitTagReq- OBFF Not Supported, ExtFmt- EETLPPrefix-
             EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
             FRS- TPHComp- ExtTPHComp-
             AtomicOpsCap: 32bit- 64bit- 128bitCAS-
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR+ OBFF Disabled,
             AtomicOpsCtl: ReqEn-
        LnkCap2: Supported Link Speeds: 2.5-8GT/s, Crosslink- Retimer- 2Retimers- DRS-
        LnkCtl2: Target Link Speed: 8GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+ EqualizationPhase1+
             EqualizationPhase2+ EqualizationPhase3+ LinkEqualizationRequest-
             Retimer- 2Retimers- CrosslinkRes: unsupported
    Capabilities: [b0] MSI-X: Enable+ Count=16 Masked-
        Vector table: BAR=0 offset=00002000
        PBA: BAR=0 offset=00002100
    Capabilities: [100 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr+
        AERCap:    First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
            MultHdrRecCap- MultHdrRecEn- TLPPfxPres- HdrLogCap-
        HeaderLog: 00000000 00000000 00000000 00000000
    Capabilities: [158 v1] Alternative Routing-ID Interpretation (ARI)
        ARICap:    MFVC- ACS-, Next Function: 0
        ARICtl:    MFVC- ACS-, Function Group: 0
    Capabilities: [168 v1] Secondary PCI Express
        LnkCtl3: LnkEquIntrruptEn- PerformEqu-
        LaneErrStat: 0
    Capabilities: [188 v1] Single Root I/O Virtualization (SR-IOV)
        IOVCap:    Migration-, Interrupt Message Number: 000
        IOVCtl:    Enable- Migration- Interrupt- MSE- ARIHierarchy+
        IOVSta:    Migration-
        Initial VFs: 8, Total VFs: 8, Number of VFs: 0, Function Dependency Link: 00
        VF offset: 1, stride: 1, Device ID: 2265
        Supported Page Size: 00000553, System Page Size: 00000001
        Region 0: Memory at 00000000fcd04000 (64-bit, non-prefetchable)
        VF Migration: offset: 00000000, BIR: 0
    Capabilities: [1c8 v1] Latency Tolerance Reporting
        Max snoop latency: 1048576ns
        Max no snoop latency: 1048576ns
    Capabilities: [1d0 v1] L1 PM Substates
        L1SubCap: PCI-PM_L1.2+ PCI-PM_L1.1+ ASPM_L1.2+ ASPM_L1.1+ L1_PM_Substates+
              PortCommonModeRestoreTime=10us PortTPowerOnTime=80us
        L1SubCtl1: PCI-PM_L1.2- PCI-PM_L1.1- ASPM_L1.2- ASPM_L1.1-
               T_CommonMode=0us LTR1.2_Threshold=0ns
        L1SubCtl2: T_PwrOn=10us
    Kernel driver in use: nvme
    Kernel modules: nvme


---------- File system specs from 'df -h':
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p5 ext4  336G  268G   52G  84% /
/dev/nvme0n1p1 vfat   96M   33M   64M  34% /boot/efi

---------- Disk/Partition Information From 'fdisk':

Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: INTEL SSDPEKNU512GZ                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 04E7575A-C879-43B8-B09A-8A3AC81C013A

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     206847    204800   100M EFI System
/dev/nvme0n1p2    206848     239615     32768    16M Microsoft reserved
/dev/nvme0n1p3    239616  282173439 281933824 134.4G Microsoft basic data
/dev/nvme0n1p4 998973440 1000212479   1239040   605M Windows recovery environment
/dev/nvme0n1p5 282173440  998973439 716800000 341.8G Linux filesystem

Partition table entries are not in disk order.


---------- Disk/Partition Information From 'lsblk':
NAME          SIZE FSTYPE   LABEL MOUNTPOINT                         MODEL
nvme0n1     476.9G                                                   INTEL SSDPEKNU512GZ
|-nvme0n1p1   100M vfat           /boot/efi                          
|-nvme0n1p2    16M                                                   
|-nvme0n1p3 134.4G ntfs                                              
|-nvme0n1p4   605M ntfs                                              
`-nvme0n1p5 341.8G ext4           /                                  
   ------- 'lsblk' information continued ...
NAME        HOTPLUG PARTUUID                             UUID
nvme0n1           0                                      
|-nvme0n1p1       0 bc1639bd-be80-413c-bc02-d6fb0ac257c7 E6A5-9D09
|-nvme0n1p2       0 e5d547c3-0f17-495e-8762-e403a5ff1335 
|-nvme0n1p3       0 51589b59-56b9-4caa-be00-752bc3f44bf3 CEBCA80BBCA7EC61
|-nvme0n1p4       0 aedbfd81-7abd-4f5b-9594-a8408f833c44 1E22D66122D63E09
`-nvme0n1p5       0 d7230f7f-497f-40cd-8424-794dc839f08a be4c2ec4-4999-400f-9290-a4c4d23be5a4

---------- Mount Details of '/etc/fstab':
UUID=be4c2ec4-4999-400f-9290-a4c4d23be5a4 /               ext4    errors=remount-ro 0       1
UUID=E6A5-9D09  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

---------- Current Mount Details of 'mount':
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p5 on / type ext4 (rw,relatime,errors=remount-ro)

---------- USB Information from 'lsusb -t -v':
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 3: Dev 2, If 0, Class=Wireless, Driver=btusb, 480M
        ID 13d3:3568 IMC Networks 
    |__ Port 3: Dev 2, If 1, Class=Wireless, Driver=btusb, 480M
        ID 13d3:3568 IMC Networks 
    |__ Port 3: Dev 2, If 2, Class=Wireless, Driver=, 480M
        ID 13d3:3568 IMC Networks 
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 10000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 2: Dev 2, If 0, Class=Vendor Specific Class, Driver=, 12M
        ID 04f3:0c6e Elan Microelectronics Corp. 
    |__ Port 3: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
        ID 13d3:5463 IMC Networks 
    |__ Port 3: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
        ID 13d3:5463 IMC Networks 
    |__ Port 3: Dev 3, If 2, Class=Application Specific Interface, Driver=, 480M
        ID 13d3:5463 IMC Networks 

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: Barcelo
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: /dev/fb0
       version: c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=2880,1800
       resources: 
           irq:55 
           memory:d0000000-dfffffff 
           memory:e0000000-e01fffff 
           ioport:f000(size=256) 
           memory:fcc00000-fcc7ffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 16 x 16, current 1680 x 1050, maximum 32767 x 32767
XWAYLAND0 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 300mm x 190mm
The Current Session Type is: wayland 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru-olive-dark'
The Current Virtual TTY's being used are:
    TTY#    Used By
    tty2    gdm-wayland-ses
    tty2    gnome-session-b
    pts/0    bash
    pts/0    system-info
    pts/0    system-info
    pts/0    sed
    pts/0    system-info
    pts/0    ps
    pts/0    awk

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://cz.archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://cz.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
deb http://cz.archive.ubuntu.com/ubuntu/ jammy universe
deb http://cz.archive.ubuntu.com/ubuntu/ jammy-updates universe
deb http://cz.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://cz.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
deb http://cz.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu jammy-security multiverse
deb http://cz.archive.ubuntu.com/ubuntu/ jammy-proposed restricted main universe multiverse

Sources List from SourcesD:
/etc/apt/sources.list.d/owncloud.list.save:
File had no entries.
/etc/apt/sources.list.d/savoury1-ubuntu-gimp-jammy.list.save:
File had no entries.
/etc/apt/sources.list.d/teamviewer.list:
deb https://linux.teamviewer.com/deb stable main
/etc/apt/sources.list.d/megasync.list:
deb [signed-by=/usr/share/keyrings/meganz-archive-keyring.gpg] https://mega.nz/linux/repo/xUbuntu_22.04/ ./
/etc/apt/sources.list.d/teamviewer.list.save:
deb https://linux.teamviewer.com/deb stable main
/etc/apt/sources.list.d/owncloud.list:
File had no entries.
/etc/apt/sources.list.d/megasync.list.save:
deb [signed-by=/usr/share/keyrings/meganz-archive-keyring.gpg] https://mega.nz/linux/repo/xUbuntu_22.04/ ./
/etc/apt/sources.list.d/savoury1-ubuntu-gimp-jammy.list:
File had no entries.

---------- Other Details from 'Various':
The current kernel version is:       5.18.2 
The current release description is:  Ubuntu 22.04 LTS 
Original Installation Date:          2022-06-08+00:02:51 
Original Installation Media: Ubuntu 22.04 LTS "Jammy Jellyfish" - Release amd64 (20220419)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.40.42
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.39.40
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.37.39
For HWE Package: linux-image-generic-hwe-22.04, Kernel Version: 5.15.0.25.27

   --- HWE Package Status from 'dpkg':
Package linux-generic-hwe-22.04 is installed.

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
amber
bison
btop
build-essential
chromium-browser
fakeroot
filezilla
flex
gimp
git
gnome-shell-extension-manager
gnome-shell-extensions
gnome-tweaks
gparted
guymager
htop
hunspell-en-au
hunspell-en-ca
hunspell-en-gb
hunspell-en-za
hyphen-en-ca
hyphen-en-gb
i2c-tools
iftop
iotop
libelf-dev
libglade2-dev
libglib2.0-dev
libgtk2.0-dev
libncurses-dev
libreoffice-help-cs
libreoffice-help-en-gb
libreoffice-l10n-cs
libreoffice-l10n-en-gb
libreoffice-l10n-en-za
libssl-dev
libx11-dev
linux-headers-5.18.2
linux-headers-5.18.3
linux-image-5.18.2
linux-image-5.18.2-dbg
linux-image-5.18.3
linux-image-5.18.3-dbg
lvm2
manpages-dev
manpages-posix-dev
mc
megasync
minecraft-launcher
mythes-en-au
notecase-pro
owncloud-client
p7zip-full
p7zip-rar
pavucontrol
powertop
python3-libevdev
radeontop
teamviewer
testdisk
thunderbird-locale-cs
thunderbird-locale-en-gb
ubuntu-restricted-extras
vlc
whois

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
gandalf  tty2         Jun 22 13:36 (tty2)

The User running this script was: gandalf
uid=1000(gandalf)
gid=1000(gandalf)
groups=1000(gandalf),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
122(lpadmin),134(lxd),135(sambashare)

The 'system-info' script was booted from an installed system.

The 'system-info' script was run locally on the system

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-5.18.2.cert root=UUID=be4c2ec4-4999-400f-9290-a4c4d23be5a4 ro quiet splash vt.handoff=7

---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    pastebinit

*** End Of Report ***
```

---

