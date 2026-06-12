---
title: "Nvidia GPU Lockup - Window Manager Freezes Randomly, Xorg, 100% CPU, Proprietary Drv"
date: 2017-08-18
forum: Hardware
---

### Post by promet on 2017-08-18
[COLOR=#222222][FONT=Verdana]Hi,[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I'm not a "great" troubleshooter, but I thought I would just mention this, as it was a simple fix for me, but the solution was*very* obscure and challenging for me to locate by just searching UbuntuForums and the web in general.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]There seems to be a certain number of Nvidia GPU users who are having, what appear to be random, "GPU Lockups". After searching around,there are lots of suggestions regarding, nouveau vs. ubuntu-repo-proprietary vs. newest-nvidia-website-proprietary driver search being the cause of the lockups.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Similarly,there are a lot of opinions regarding the compositing function (thatis, turning off composting) of your window manager (compiz, marco, orother, depending on your window management environment) being the culprit and losing composting may fix your issues.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]And,these may be the correct suggestions for many people. It was different for me though. First, here are some of my system details (Iam running the most current proprietary driver for my GTX 750 from the Nvidia website (NVIDIA-Linux-x86_64-384.59) ):[/FONT][/COLOR]

```

[COLOR=#222222][FONT=Verdana]Summary[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-------[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]-Computer-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Processor: 8x AMD FX(tm)-8320 Eight-Core Processor[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Memory: 16332MB (8495MB used)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]OperatingSystem : Ubuntu 16.04.3 LTS[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]UserName : promet (promet)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Date/Time: Fri 18 Aug 2017 08:40:34 PM CDT[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-Display-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Resolution: 1920x1080 pixels[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]OpenGLRenderer : GeForce GTX 750/PCIe/SSE2[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]X11Vendor : The X.Org Foundation[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-Multimedia-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]AudioAdapter : HDA-Intel - HDA ATI SB[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]AudioAdapter : HDA-Intel - HDA NVidia[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-InputDevices-[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]PowerButton[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]PowerButton[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]LogitechUSB Keyboard[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]LogitechUSB Receiver[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]LogitechUSB Keyboard[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]LogitechUSB Receiver[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]AresonUSB Device[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]AresonUSB Device[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]SIwilress mouse & keyboard[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]SIwilress mouse & keyboard[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]EeePC WMI hotkeys[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Front Mic[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Rear Mic[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Line[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Line Out Front[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Line Out Surround[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Line Out CLFE[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Line Out Side[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDAATI SB Front Headphone[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDANVidia HDMI/DP,pcm : 3=[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDANVidia HDMI/DP,pcm : 7=[/FONT][/COLOR]
[COLOR=#222222] [FONT=Verdana]HDANVidia HDMI/DP,pcm : 8=[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-Printers-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Noprinters found[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-SCSIDisks-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ATAADATA SP900[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ATAADATA SP900[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]WDMy Passport 25E1[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]WDSES Device[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]WDCWD50 00BEKT-75KA9T0[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]OperatingSystem[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]----------------[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]-Version-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Kernel: Linux 4.4.0-92-generic (x86_64)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Compiled: #115-Ubuntu SMP Thu Aug 10 09:04:33 UTC 2017[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]CLibrary : Unknown[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]DefaultC Compiler : GNU C Compiler version 5.4.0 20160609 (Ubuntu5.4.0-6ubuntu1~16.04.4) [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Distribution: Ubuntu 16.04.3 LTS[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-CurrentSession-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ComputerName : shivux[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]UserName : promet (promet)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]HomeDirectory : /home/promet[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]DesktopEnvironment : MATE (mate)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]-Misc-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Uptime: 22 hours, 16 minutes[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]LoadAverage : 2.25, 2.13, 2.06[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]KernelModules[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]--------------[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]-LoadedModules-[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]input_leds: Input -&gt; LEDs Bridge[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]joydev: Joystick device interfaces[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]msr: x86 generic MSR driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]xt_multiport: Xtables: multiple port matching for TCP, UDP, UDP-Lite, SCTP andDCCP[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]zram: Compressed RAM Block Device[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]lz4_compress: LZ4 compressor[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]binfmt_misc[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_hda_codec_hdmi: HDMI HD-audio codec[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nvidia_uvm[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]kvm_amd[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]kvm[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]irqbypass: IRQ bypass manager utility module[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]crct10dif_pclmul: T10 DIF CRC calculation accelerated with PCLMULQDQ.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]crc32_pclmul[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_hda_codec_realtek: Realtek HD-audio codec[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ghash_clmulni_intel: GHASH Message Digest Algorithm, acclerated by PCLMULQDQ-NI[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_hda_codec_generic: Generic HD-audio codec parser[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]aesni_intel: Rijndael (AES) Cipher Algorithm, Intel AES-NI instructionsoptimized[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_hda_intel: Intel HDA driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]aes_x86_64: Rijndael (AES) Cipher Algorithm, asm optimized[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]lrw: LRW block cipher mode[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]gf128mul: Functions for multiplying elements of GF(2^128)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]glue_helper[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_hda_codec: HDA codec core[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ablk_helper[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]eeepc_wmi: Eee PC WMI Hotkey Driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]cryptd: Software async crypto daemon[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]asus_wmi: Asus Generic WMI Driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]sparse_keymap: Generic support for sparse keymaps[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_hda_core: HD-audio bus[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]video: ACPI Video Driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]mxm_wmi: MXM WMI Driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_hwdep: Hardware dependent layer[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_pcm: Midlevel PCM code for ALSA.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]serio_raw: Raw serio driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]fam15h_power: AMD Family 15h CPU processor power monitor[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_seq_midi: Advanced Linux Sound Architecture sequencer MIDI synth.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_seq_midi_event: MIDI byte &lt;-&gt; sequencer event coder[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_rawmidi: Midlevel RawMidi code for ALSA.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]edac_mce_amd: AMD MCE decoder[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]edac_core: Core library routines for EDAC reporting[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]k10temp: AMD Family 10h+ CPU core temperature monitor[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_seq: Advanced Linux Sound Architecture sequencer.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_seq_device: ALSA sequencer device management[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd_timer: ALSA timer interface[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]snd: Advanced Linux Sound Architecture driver for soundcards.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]soundcore: Core sound module[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]shpchp: Standard Hot Plug PCI Controller Driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]i2c_piix4: PIIX4 SMBus driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]tpm_infineon: Driver for Infineon TPM SLD 9630 TT 1.1 / SLB 9635 TT 1.2[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]8250_fintek: Fintek F812164 module[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]mac_hid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]wmi: ACPI-WMI Mapping Driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ipt_REJECT: Xtables: packet &quot;rejection&quot; target for IPv4[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_reject_ipv4[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_log_ipv4: Netfilter IPv4 packet logging[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_log_common[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]xt_LOG: Xtables: IPv4/IPv6 packet logging[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]xt_limit: Xtables: rate-limit match[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]xt_tcpudp: Xtables: TCP, UDP and UDP-Lite match[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]xt_addrtype: Xtables: address type match[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_conntrack_ipv4[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_defrag_ipv4[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]xt_conntrack: Xtables: connection tracking state match[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ip6_tables: IPv6 packet filter[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_conntrack_netbios_ns: NetBIOS name service broadcast connection tracking helper[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_conntrack_broadcast[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_nat_ftp: ftp NAT helper[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_nat[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_conntrack_ftp: ftp connection tracking helper[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nf_conntrack[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]iptable_filter: iptables filter table[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ip_tables: IPv4 packet filter[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]x_tables: {ip,ip6,arp,eb}_tables backend module[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]parport_pc: PC-style parallel port driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ppdev[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]lp[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]parport[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]autofs4[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]btrfs[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]xor[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]raid6_pq: RAID6 Q-syndrome calculations[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]dm_mirror: device-mapper mirror target[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]dm_region_hash: device-mapper region hash[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]dm_log: device-mapper dirty region log[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ses: SCSI Enclosure Services (ses) driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]enclosure: Enclosure Services[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]uas[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]usb_storage: USB Mass Storage driver for Linux[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]hid_generic: HID generic driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]usbhid: USB HID core driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]hid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nvidia_drm[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nvidia_modeset[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]nvidia[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]drm_kms_helper: DRM KMS helper[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]psmouse: PS/2 mouse driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]syscopyarea: Generic copyarea (sys-to-sys)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]r8169: RealTek RTL-8169 Gigabit Ethernet driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]sysfillrect: Generic fill rectangle (sys-to-sys)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]mii: MII hardware support library[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]sysimgblt: 1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]fb_sys_fops: Generic file read (fb in system RAM)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]drm: DRM shared core routines[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]ahci: AHCI SATA low-level driver[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]libahci: Common AHCI SATA low-level routines[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]fjes: FUJITSU Extended Socket Network Device Drive[/FONT][/COLOR]

```

[COLOR=#222222][FONT=Verdana]I ran through various ubuntu/proprietary drivers and various composite/non-composite modes, but could not stop these freezes/crashes. Incidentally, these crashes would freeze the window-manager, sometimes the mouse-cursor as well, sometimes the mouse would still move, sometimes not.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]The system would still be running though, and could be ssh-ed into. On connecting via ssh, I learned that these lockups also caused the Xorg process to go to a constant 100% and, also, become "un-killable",which is super annoying. This problem also make the Lightdm service unstoppable, so there was no way to get back to the window manager without rebooting, which required a full-on "REISUB"reboot, also, suuuuper-annoying [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]So the fix for me was adding the "nogpumanager" boot parameter to my /etc/default/grub file, as per the below (always remembering,of course, to run...[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]```
sudo update-grub
```[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]...to get the system to incorporate the change into the system's next grub boot), like so:

[/FONT][/COLOR][IMG]http://imgur.com/a/J0enq[/IMG]
Link to a sample of my [/etc/default/grub file]("http://imgur.com/a/J0enq")

Now this would lead me to believe that something is broken in the way the gpu-manager is interacting with Nvidia cards, at least mine and, at least on 16.04.2. As mentioned before, I don't really have the "chops" to say I know that for sure. Perhaps something for a more skilled user to check out though? At any rate, I hope this will be of use to someone in future.

Cheers,

P 

[IMG]http://imgur.com/a/J0enq[/IMG]

---

### Post by promet on 2017-08-19
Actually, it may be not. After doing all the above and having a "statistically-longer-period-of-non-failure-that-made-me-feel-comfortable-about-claiming-the-issue-as-solved"; I just had two "hard" failures, back-to-back. So...back to the drawing board. Though I do feel that I am on to something. ;) Standby...

---

### Post by promet on 2017-08-25
Just a quick update. After quite a bit of effort. I had reached a point where any combination of kernels and drivers would only get me to the Lightdm login, the keyboard would become unresponsive and the login screen would freeze.

I then, just for kicks, replaced lightdm with gdm3, and now the system boots, logs in and, for the moment, seems to be working fine...so, if you've gone down this particular rabbit hole, hopefully that is helpful.

Best,

---

### Post by humanatix on 2017-11-15
I feel you bro.. N i did managed to recreate the problems many times. After quite *lots* of tries n retries i foung out its due the graphic drivers... lightdm is very shy on using drivers thats not rock solid in its dri connections... n after months of retries finally i got it just right for the hardware im using... and i'm now a happy man :)

---

