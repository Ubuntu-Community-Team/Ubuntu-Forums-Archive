---
title: "Hardware and kernel issues"
date: 2024-08-31
forum: Hardware
---

### Post by hbbco on 2024-08-31
My computer is a DESKTOP with:[INDENT]Processor : Intel(R) Core(TM) i7-6700 CPU @ 3.40GHz
    Memory : 65785MB (4829MB used)
    Computer type : Desktop PC
    Operating system : Ubuntu 22.04.4 LTS
    -Display-
        Resolution : 1600x900 pixels
        OpenGL renderer : AMD CEDAR (DRM 2.50.0 / 5.15.0-119-generic, LLVM 15.0.7)
    X11 provider : The X.Org Foundation
    Motherboard:
        1.0/MSI B150A GAMING PRO (MS-7978)
    uname -r
    5.15.0-119-generic
[/INDENT]
     SCSI Disks:[INDENT]ATA CT1000MX500SSD1
        ATA KINGSTON SA400S3
        ATA WDC WD10EZEX-75W
        ATAPI iHAS124   F
        ATA TOSHIBA MQ01ABD1
        ATA Samsung SSD 850
[/INDENT]
     Loaded kernel modules:[INDENT]tcp_diag
        udp_diag
        inet_diag
        nvme_fabrics
        nvme_core
        ntfs3        : ntfs3 read/write filesystem
        ccm        : Counter with CBC MAC
        snd_seq_dummy        : ALSA sequencer MIDI-through client
        snd_hrtimer        : ALSA hrtimer backend
        rfcomm        : Bluetooth RFCOMM ver 1.11
        cmac        : CMAC keyed hash algorithm
        bnep        : Bluetooth BNEP ver 1.3
        8021q
        garp
        mrp
        stp
        llc        : LLC IEEE 802.2 core support
        intel_rapl_msr        : Driver for Intel RAPL (Running Average Power Limit) control via MSR interface
        mei_hdcp        : MEI HDCP
        ip6t_REJECT        : Xtables: packet &quot;rejection&quot; target for IPv6
        nf_reject_ipv6
        xt_hl        : Xtables: Hoplimit/TTL field match
        ip6_tables        : IPv6 packet filter
        intel_rapl_common        : Intel Runtime Average Power Limit (RAPL) common code
        ip6t_rt        : Xtables: IPv6 Routing Header match
        intel_tcc_cooling        : TCC offset cooling device Driver
        x86_pkg_temp_thermal        : X86 PKG TEMP Thermal Driver
        intel_powerclamp        : Package Level C-state Idle Injection for Intel CPUs
        coretemp        : Intel Core temperature monitor
        kvm_intel
        ipt_REJECT        : Xtables: packet &quot;rejection&quot; target for IPv4
        kvm
        nf_reject_ipv4
        xt_LOG        : Xtables: IPv4/IPv6 packet logging
        crct10dif_pclmul        : T10 DIF CRC calculation accelerated with PCLMULQDQ.
        nf_log_syslog        : Netfilter syslog packet logging
        ghash_clmulni_intel        : GHASH hash function, accelerated by PCLMULQDQ-NI
        xt_comment        : Xtables: No-op match which can be tagged with a comment
        sha256_ssse3        : SHA256 Secure Hash Algorithm, Supplemental SSE3 accelerated
        xt_multiport        : Xtables: multiple port matching for TCP, UDP, UDP-Lite, SCTP and DCCP
        sha1_ssse3        : SHA1 Secure Hash Algorithm, Supplemental SSE3 accelerated
        aesni_intel        : Rijndael (AES) Cipher Algorithm, Intel AES-NI instructions optimized
        crypto_simd
        cryptd        : Software async crypto daemon
        nft_limit        : nftables limit expression support
        rapl
        intel_cstate
        xt_limit        : Xtables: rate-limit match
        snd_hda_codec_realtek        : Realtek HD-audio codec
        xt_addrtype        : Xtables: address type match
        snd_hda_codec_generic        : Generic HD-audio codec parser
        intel_wmi_thunderbolt        : Intel WMI Thunderbolt force power driver
        ledtrig_audio        : LED trigger for audio mute control
        xt_tcpudp        : Xtables: TCP, UDP and UDP-Lite match
        xt_conntrack        : Xtables: connection tracking state match
        snd_hda_codec_hdmi        : HDMI HD-audio codec
        nf_conntrack
        joydev        : Joystick device interfaces
        nf_defrag_ipv6
        snd_hda_intel        : Intel HDA driver
        mxm_wmi        : MXM WMI Driver
        nf_defrag_ipv4
        snd_intel_dspcfg        : Intel DSP config driver
        nft_compat        : x_tables over nftables support
        snd_intel_sdw_acpi        : Intel Soundwire ACPI helpers
        iwlmvm        : The new Intel(R) wireless AGN driver for Linux
        nft_counter        : nftables counter rule support
        snd_hda_codec        : HDA codec core
        mac80211        : IEEE 802.11 subsystem
        snd_hda_core        : HD-audio bus
        libarc4
        ee1004        : Driver for EE1004-compliant DDR4 SPD EEPROMs
        snd_hwdep        : Hardware dependent layer
        btusb        : Generic Bluetooth USB driver ver 0.8
        input_leds        : Input -&gt; LEDs Bridge
        snd_pcm        : Midlevel PCM code for ALSA.
        btrtl        : Bluetooth support for Realtek devices ver 0.1
        btbcm        : Bluetooth support for Broadcom devices ver 0.1
        snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
        snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
        btintel        : Bluetooth support for Intel devices ver 0.1
        iwlwifi        : Intel(R) Wireless WiFi driver for Linux
        nf_tables
        snd_rawmidi        : Midlevel RawMidi code for ALSA.
        libcrc32c        : CRC32c (Castagnoli) calculations
        bluetooth        : Bluetooth Core ver 2.22
        radeon        : ATI Radeon
        nfnetlink        : Netfilter messages via netlink socket
        ecdh_generic        : ECDH generic algorithm
        cfg80211        : wireless configuration support
        ecc
        snd_seq        : Advanced Linux Sound Architecture sequencer.
        binfmt_misc
        sch_fq_codel        : Fair Queue CoDel discipline
        drm_ttm_helper        : DRM gem ttm helpers
        ttm        : TTM memory manager subsystem (for DRM device)
        drm_kms_helper        : DRM KMS helper
        cec        : Device node registration for cec drivers
        snd_seq_device        : ALSA sequencer device management
        rc_core
        snd_timer        : ALSA timer interface
        i2c_algo_bit        : I2C-Bus bit-banging algorithm
        fb_sys_fops        : Generic file read (fb in system RAM)
        snd        : Advanced Linux Sound Architecture driver for soundcards.
        syscopyarea        : Generic copyarea (sys-to-sys)
        mei_me        : Intel(R) Management Engine Interface
        sysfillrect        : Generic fill rectangle (sys-to-sys)
        soundcore        : Core sound module
        sysimgblt        : 1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)
        mei        : Intel(R) Management Engine Interface
        intel_pch_thermal        : Intel PCH Thermal driver
        mac_hid
        acpi_pad        : ACPI Processor Aggregator Driver
        cuse        : Character device in Userspace
        isgx        : Intel SGX Driver
        msr        : x86 generic MSR driver
        parport_pc        : PC-style parallel port driver
        ppdev
        lp
        drm        : DRM shared core routines
        parport
        efi_pstore        : EFI variable backend for pstore
        ip_tables        : IPv4 packet filter
        x_tables        : {ip,ip6,arp,eb}_tables backend module
        autofs4
        hid_generic        : HID generic driver
        usbhid        : USB HID core driver
        hid
        crc32_pclmul
        e1000e        : Intel(R) PRO/1000 Network Driver
        i2c_i801        : I801 SMBus driver
        i2c_smbus        : SMBus protocol extensions support
        ahci        : AHCI SATA low-level driver
        xhci_pci        : xHCI PCI Host Controller Driver
        libahci        : Common AHCI SATA low-level routines
        xhci_pci_renesas
        wmi        : ACPI-WMI Mapping Driver
        video        : ACPI Video Driver
[/INDENT]
     USB DEVICES:[INDENT]VIA Labs, Inc. VL813 Hub
        Linux Foundation 3.0 root hub
        Linux Foundation 2.0 root hub
        Linux Foundation 3.0 root hub
        Huasheng Electronics USB2.0 HUB
        VIA Labs, Inc. Hub
        Linux Foundation 2.0 root hub
        Linux Foundation 3.0 root hub
        Intel Corp. AX200 Bluetooth
        Sunplus Innovation Technology Inc. Optical Mouse
        Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
        VIA Labs, Inc. VL813 Hub
        Linux Foundation 2.0 root hub
[/INDENT]
     Network Interfaces:[INDENT]lo    5,12MiB    5,12MiB    127.0.0.1    
        enp0s31f6    0,00MiB    0,00MiB        
        wlp2s0    26,53MiB    6,75MiB    192.168.68.106    
[/INDENT]
 
I have been having several problems at boot time for several months now. 
Sometimes the logical interface names do not work, despite the existence of a file in the /etc/udev/rules.d folder named 70-persistent-net.rules whose content is:
[INDENT]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*",
    ATTR{address}=="08:9d:f4:13:8b:7a", ATTR{dev_id}=="0x0", ATTR{type}=="1",
    KERNEL=="wlan*", NAME="wlp2s0"
[/INDENT]
 
And the logical name of the interface ends with wlan0

Another problem that appears occasionally at startup is the mounting of several hard drives of the hdd and sdd types, which is done with the following instruction named disks_mount.sh that is in the folder /home/hugo/.SCRIPT and whose content is:
[INDENT]#!/bin/bash
# Mount KINGSTON SA400S37960G (SBFKZ1.3) Backup
udisksctl mount --block-device /dev/sdb1
# Mount WDC WD10EZEX-75WN4A1 (13057113) Winery
udisksctl mount --block-device /dev/sdc1
# Mount WDC WD10EZEX-75WN4A1 (13057113) Javi
udisksctl mount --block-device /dev/sdc2
# Mount TOSHIBA MQ01ABD100 (AX1P1A) backup 
udisksctl mount --block-device /dev/sdd1 
# Mount TOSHIBA MQ01ABD100 (AX1P1A) Multi 
udisksctl mount --block-device /dev/sdd2 
# Mount Samsung SSD 850 EVO 250GB (EMT01B6Q) 
udisksctl mount --block-device /dev/sde1 --filesystem-type ntfs
[/INDENT]
 
The problem is that the sdd that should be mounted on /dev/sde1 sometimes fails and when investigating the why, the report is as if the cable that connects it to the motherboard was bad; this cable was changed, and the problem occasionally appears.

The two problems described above are ALWAYS SOLVED with A BOOTING, NOT WITH A REBOOT.

I use a USB microphone which almost always fails when connected to the USB port.
The command
dmesg -W
in that case gives the following output:

    dmesg -W[INDENT][ 6725.617065] usb 3-1.4: reset high-speed USB device number 3 using xhci_hcd
        [ 6725.932952] usb 3-1.4: USB disconnect, device number 3
        [ 6725.933531] usb 3-1.4-port4: attempt power cycle
        [ 6725.933549] usb 3-1.4-port4: failed to disable port power
        [ 6726.012638] usb 3-1.4: new high-speed USB device number 8 using xhci_hcd
        [ 6726.113386] usb 3-1.4: New USB device found, idVendor=214b, idProduct=7250, bcdDevice= 1.00
        [ 6726.113401] usb 3-1.4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
        [ 6726.113408] usb 3-1.4: Product: USB2.0 HUB
        [ 6726.114555] hub 3-1.4:1.0: USB hub found
        [ 6726.114612] hub 3-1.4:1.0: 4 ports detected
        [ 6726.400576] usb 3-1.4.4: new full-speed USB device number 9 using xhci_hcd
        [ 6726.514905] usb 3-1.4.4: New USB device found, idVendor=2e3c, idProduct=4444, bcdDevice= 2.00
        [ 6726.514919] usb 3-1.4.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
        [ 6726.514926] usb 3-1.4.4: Product: LCS_USB_Audio
        [ 6726.514931] usb 3-1.4.4: Manufacturer: AOKEO
        [ 6726.514936] usb 3-1.4.4: SerialNumber: 000001760000
        [ 6726.545072] mc: Linux media interface: v0.10
        [ 6726.969312] usb 3-1.4.4: 1:1: cannot get freq at ep 0x82
        [ 6726.981185] usbcore: registered new interface driver snd-usb-audio
        [ 6727.290259] usb 3-1.4.4: 1:1: cannot get freq at ep 0x82
        [ 6727.583264] usb 3-1.4.4: 1:1: cannot get freq at ep 0x82
[/INDENT]
         
Sometimes with this the microphone does not mount or fails, the vast majority of the time the microphone works. 

The same thing happens with HDDs that I mount to make backups of information. Many times the HDD LEDs indicate that they are receiving power but they do not mount, other times they do mount correctly.

My guess is that there is apparently a problem with the way the kernel modules are loaded (their sequence and speed) and that the problems with the USB ports originate from the electrical current that the devices require. Any thoughts on this?

---

