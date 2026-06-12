---
title: "My Sound Card Stopped Working - Message: Dummy Output"
date: 2014-12-03
forum: Hardware
---

### Post by gilberto-olimpio on 2014-12-03
[FONT=arial][COLOR=#333333]Hello guys

I'm using Ubuntu 14.04 LTS, and suddenly my sound stopped working! When I go to sound settings appears that my sound card is a dummy output - just like that! Use a Dell Latitude 3440 without HDMI and Nvidia video card, which could be the case of problems too Do sound tests and nothing happens![/COLOR]
[COLOR=#333333]The only thing I did differently was to use a 4G modem. Is he wrong? Some kind of conflict?[/COLOR]
[COLOR=#333333]Already performed several steps to address this problem including this [Link]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") and to no avail.[/COLOR]
[COLOR=#333333]When I try to run the "alsamixer" says the directory is invalid! But I could run the following command and analyze the parameters: sudo gedit /etc/modprobe.d/alsa-base.conf - but the mixer command does not work![/COLOR]
[COLOR=#333333]I believe that I should reinstall the sound card but I can not do this procedure! Can anyone help me?[/COLOR]
[COLOR=#333333]My lspci -v output (I dont see my pci sound card!):
[/COLOR][/FONT][INDENT][FONT=arial]00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09) Subsystem: Dell Device 0606 Flags: bus master, fast devsel, latency 0 Capabilities:
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller]) Subsystem: Dell Device 0607 Flags: bus master, fast devsel, latency 0, IRQ 58 Memory at f7400000 (64-bit, non-prefetchable) [size=4M] Memory at d0000000 (64-bit, prefetchable) [size=256M] I/O ports at f000 [size=64] Expansion ROM at [disabled] Capabilities: Kernel driver in use: i915
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04) Subsystem: Dell Device 0606 Flags: bus master, fast devsel, latency 0, IRQ 60 Memory at f7a05000 (64-bit, non-prefetchable) [size=32] Capabilities: Kernel driver in use: mei_me
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4) (prog-if 00 [Normal decode]) Flags: bus master, fast devsel, latency 0 Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 I/O behind bridge: 00002000-00002fff Memory behind bridge: cf200000-cf3fffff Prefetchable memory behind bridge: 00000000cf400000-00000000cf5fffff Capabilities: Kernel driver in use: pcieport
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4) (prog-if 00 [Normal decode]) Flags: bus master, fast devsel, latency 0 Bus: primary=00, secondary=06, subordinate=06, sec-latency=0 Memory behind bridge: f7900000-f79fffff Capabilities: Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4) (prog-if 00 [Normal decode]) Flags: bus master, fast devsel, latency 0 Bus: primary=00, secondary=07, subordinate=07, sec-latency=0 I/O behind bridge: 0000e000-0000efff Memory behind bridge: f7800000-f78fffff Capabilities: Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4) (prog-if 00 [Normal decode]) Flags: bus master, fast devsel, latency 0 Bus: primary=00, secondary=08, subordinate=08, sec-latency=0 I/O behind bridge: 0000d000-0000dfff Memory behind bridge: f6000000-f70fffff Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff Capabilities: Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04) (prog-if 20 [EHCI]) Subsystem: Dell Device 0606 Flags: bus master, medium devsel, latency 0, IRQ 23 Memory at f7a03000 (32-bit, non-prefetchable) [size=1K] Capabilities: Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04) Subsystem: Dell Device 0606 Flags: bus master, medium devsel, latency 0 Capabilities: Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0]) Subsystem: Dell Device 0606 Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 56 I/O ports at f0b0 [size=8] I/O ports at f0a0 [size=4] I/O ports at f090 [size=8] I/O ports at f080 [size=4] I/O ports at f060 [size=32] Memory at f7a02000 (32-bit, non-prefetchable) [size=2K] Capabilities: Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04) Subsystem: Dell Device 0606 Flags: medium devsel, IRQ 5 Memory at f7a01000 (64-bit, non-prefetchable) [size=256] I/O ports at f040 [size=32]
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01) Subsystem: Dell Device 020c Flags: bus master, fast devsel, latency 0, IRQ 18 Memory at f7900000 (64-bit, non-prefetchable) [size=512K] Expansion ROM at f7980000 [disabled] [size=64K] Capabilities: Kernel driver in use: ath9k
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10) Subsystem: Dell Device 0606 Flags: bus master, fast devsel, latency 0, IRQ 57 I/O ports at e000 [size=256] Memory at f7804000 (64-bit, non-prefetchable) [size=4K] Memory at f7800000 (64-bit, non-prefetchable) [size=16K] Capabilities: Kernel driver in use: r8169
08:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1) Subsystem: Dell Device 0607 Flags: bus master, fast devsel, latency 0, IRQ 59 Memory at f6000000 (32-bit, non-prefetchable) [size=16M] Memory at e0000000 (64-bit, prefetchable) [size=256M] Memory at f0000000 (64-bit, prefetchable) [size=32M] I/O ports at d000 [size=128] Expansion ROM at f7000000 [disabled] [size=512K] Capabilities: Kernel driver in use: nouveau
[/FONT][/INDENT]
[FONT=arial][COLOR=#333333]After I run de command line:[/COLOR][/FONT][INDENT][FONT=arial]wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[/FONT][/INDENT]
[FONT=arial][COLOR=#333333]**Result:**[/COLOR][/FONT][INDENT][FONT=arial]upload=true&script=true&cardinfo= !!################################ !!ALSA Information Script v 0.4.64 !!################################
!!Script ran on: Sun Nov 30 08:27:33 UTC 2014
!!Linux Distribution !!------------------
Ubuntu 14.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.1 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
!!DMI Information !!---------------
Manufacturer: Dell Inc. Product Name: Latitude 3440 Product Version: Not Specified Firmware Version: A09
!!Kernel Information !!------------------
Kernel release: 3.13.0-40-generic Operating System: GNU/Linux Architecture: x86_64 Processor: x86_64 SMP Enabled:
Yes
!!ALSA Version !!------------
Driver version: Library version: 1.0.27.2 Utilities version: 1.0.27.2
!!Loaded ALSA modules !!-------------------
!!Sound Servers on this system !!----------------------------
Pulseaudio: Installed - Yes (/usr/bin/pulseaudio) Running - Yes
!!Soundcards recognised by ALSA !!-----------------------------
!!PCI Soundcards installed in the system !!--------------------------------------
!!Advanced information - PCI Vendor/Device/Subsystem ID's !!-------------------------------------------------------
!!Modprobe options (Sound related) !!--------------------------------
snd_atiixp_modem: index=-2 snd_intel8x0m: index=-2 snd_via82xx_modem: index=-2 snd_usb_audio: index=-2 snd_usb_caiaq: index=-2 snd_usb_ua101: index=-2 snd_usb_us122l: index=-2 snd_usb_usx2y: index=-2 snd_cmipci: mpu_port=0x330 fm_port=0x388 snd_pcsp: index=-2 snd_usb_audio: index=-2
!!Loaded sound module options !!---------------------------
!!ALSA Device nodes !!-----------------
crw-rw---- 1 root audio 116, 1 Nov 29 21:55 /dev/snd/seq crw-rw---- 1 root audio 116, 33 Nov 29 21:55 /dev/snd/timer
!!Aplay/Arecord output !!--------------------
APLAY
aplay: device_list:268: no soundcards found...
ARECORD
arecord: device_list:268: no soundcards found...
!!Amixer output !!-------------
!!Alsactl output !!--------------
--startcollapse-- --endcollapse--
!!All Loaded Modules !!------------------
Module ctr ccm bbswitch rfcomm bnep binfmt_misc uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev nvidia dell_wmi sparse_keymap mxm_wmi dell_laptop dcdbas intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm arc4 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd ath9k joydev ath9k_common ath9k_hw serio_raw lpc_ich ath ath3k btusb bluetooth mac80211 cfg80211 mei_me mei wmi mac_hid parport_pc ppdev lp parport i915 psmouse i2c_algo_bit ahci drm_kms_helper r8169 libahci drm mii video
!!ALSA/HDA dmesg !!--------------

[/FONT][/INDENT]
[FONT=arial]In ubuntu boot show the message: restore sound card state[B] [fail]

[/B][/FONT]
[FONT=arial][COLOR=#333333]Regards! Giba[/COLOR][/FONT]

---

