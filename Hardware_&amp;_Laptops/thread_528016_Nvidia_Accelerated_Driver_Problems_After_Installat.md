---
title: "Nvidia Accelerated Driver Problems After Installation"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by nadalizadeh on 2007-08-17
I've moved from fedora 6 to feisty.:guitar:
then I installed the Nvidia accelerated graphics driver. (I've tested both Nvidia's provided and the ubuntu  compiled one)

Intel Celeron 1700MHz / Nvidia Geforce FX 5200 / 512 MB Ram

When I switch from nv driver to nvidia, glxinfo says that i have acceleration but I have several problems.:(
1. Some portions of application windows like qt-designer will not redraw automatically or correclty.
    (for example i've problem while dragging a window under the other panels and get it out again)
2. I've have a system freeze while opening a PDF file with evince or KPDF (I don't have such effect on fedora) I think my evince/kpdf subsystem should have serios problems. May be they are both using a buggy gv.
3. I wonder that I don't have problems with heavy memory use programs like firefox.
4. I can succesfully enable compiz effects. Without any problem.
5. I've a accidentally Xorg restart or even system reboot while working with QT Assistant.
   A Kernel Page Fault occurs,, this is the kernel log
   (first page fault for Xorg, second for assistant)
](*,)
```
Aug 17 10:33:54 Tux3 kernel: [   49.049344] nvidia: module license 'NVIDIA' taints kernel.
Aug 17 10:33:54 Tux3 kernel: [   49.323978] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 17 10:33:54 Tux3 kernel: [   49.324998] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
Aug 17 10:33:54 Tux3 kernel: [   49.761705] fuse init (API version 7.8)
Aug 17 10:33:54 Tux3 kernel: [   49.873146] lp: driver loaded but no devices found
Aug 17 10:33:54 Tux3 kernel: [   50.075807] it87: Found IT8705F chip at 0x290, revision 2
Aug 17 10:33:54 Tux3 kernel: [   50.210632] Adding 666656k swap on /dev/disk/by-uuid/ccff8c7d-3e74-494f-aa0f-a70abddb6879.  Priority:-1 extents:1 across:666656k
Aug 17 10:33:54 Tux3 kernel: [   50.475682] EXT3 FS on hda1, internal journal
Aug 17 10:33:54 Tux3 kernel: [   59.824598] kjournald starting.  Commit interval 5 seconds
Aug 17 10:33:54 Tux3 kernel: [   59.828800] EXT3 FS on hda3, internal journal
Aug 17 10:33:54 Tux3 kernel: [   59.828816] EXT3-fs: mounted filesystem with ordered data mode.
Aug 17 10:33:54 Tux3 kernel: [   60.062306] kjournald starting.  Commit interval 5 seconds
Aug 17 10:33:54 Tux3 kernel: [   60.062572] EXT3 FS on hda8, internal journal
Aug 17 10:33:54 Tux3 kernel: [   60.062586] EXT3-fs: mounted filesystem with ordered data mode.
Aug 17 10:33:55 Tux3 kernel: [   62.582501] NET: Registered protocol family 17
Aug 17 10:33:55 Tux3 kernel: [   69.725021] No dock devices found.
Aug 17 10:33:55 Tux3 kernel: [   69.862675] ibm_acpi: ec object not found
Aug 17 10:33:55 Tux3 kernel: [   70.051553] Using specific hotkey driver
Aug 17 10:33:55 Tux3 kernel: [   70.169027] input: Power Button (FF) as /class/input/input4
Aug 17 10:33:55 Tux3 kernel: [   70.169789] ACPI: Power Button (FF) [PWRF]
Aug 17 10:33:55 Tux3 kernel: [   70.209338] input: Power Button (CM) as /class/input/input5
Aug 17 10:33:55 Tux3 kernel: [   70.210091] ACPI: Power Button (CM) [PWRB]
Aug 17 10:33:55 Tux3 kernel: [   70.227192] input: Sleep Button (CM) as /class/input/input6
Aug 17 10:33:55 Tux3 kernel: [   70.227981] ACPI: Sleep Button (CM) [SLPB]
Aug 17 10:33:55 Tux3 kernel: [   70.448541] pcc_acpi: loading...
Aug 17 10:33:55 Tux3 kernel: [   79.982297] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug 17 10:33:55 Tux3 kernel: [   79.982335] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug 17 10:33:55 Tux3 kernel: [   79.982404] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Aug 17 10:50:36 Tux3 kernel: [ 1081.589948] spurious 8259A interrupt: IRQ7.
Aug 17 11:33:53 Tux3 sensord: Chip: it87-isa-0290
Aug 17 11:33:53 Tux3 sensord: Adapter: ISA adapter
Aug 17 11:33:53 Tux3 sensord:   VCore 1: +1.74 V (min = +0.00 V, max = +4.08 V)
Aug 17 11:33:53 Tux3 sensord:   VCore 2: +2.54 V (min = +0.00 V, max = +4.08 V)
Aug 17 11:33:53 Tux3 sensord:   +3.3V: +3.15 V (min = +0.00 V, max = +4.08 V)
Aug 17 11:33:53 Tux3 sensord:   +5V: +5.05 V (min = +0.00 V, max = +6.85 V)
Aug 17 11:33:53 Tux3 sensord:   +12V: +11.97 V (min = +0.00 V, max = +16.32 V)
Aug 17 11:33:53 Tux3 sensord:   -12V: -19.26 V (min = -27.36 V, max = +3.93 V)
Aug 17 11:33:53 Tux3 sensord:   -5V: +3.20 V (min = -13.64 V, max = +4.03 V)
Aug 17 11:33:53 Tux3 sensord:   Stdby: +5.11 V (min = +0.00 V, max = +6.85 V)
Aug 17 11:33:53 Tux3 sensord:   fan1: 2766 RPM (min = 0 RPM, div = 7)
Aug 17 11:33:53 Tux3 sensord:   fan2: 0 RPM (min = 0 RPM, div = 7)
Aug 17 11:33:53 Tux3 sensord:   fan3: 0 RPM (min = 0 RPM, div = 7)
Aug 17 11:33:53 Tux3 sensord:   M/B Temp: 40 C (min = -1 C, max = 127 C)
Aug 17 11:33:53 Tux3 sensord:   CPU Temp: 39 C (min = -1 C, max = 127 C)
Aug 17 11:33:53 Tux3 sensord:   Temp3: 31 C (min = -1 C, max = 127 C)
Aug 17 11:36:45 Tux3 gconfd (root-5037): Received signal 15, shutting down cleanly
Aug 17 11:36:45 Tux3 gconfd (root-5037): Exiting
Aug 17 11:36:45 Tux3 gdm[4854]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Aug 17 11:36:47 Tux3 kernel: [ 3850.481591] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug 17 11:36:47 Tux3 kernel: [ 3850.481628] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug 17 11:36:47 Tux3 kernel: [ 3850.481697] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Aug 17 11:39:40 Tux3 gdm[7340]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Aug 17 11:39:44 Tux3 gdm[7350]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Aug 17 11:39:48 Tux3 gdm[7360]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Aug 17 11:39:48 Tux3 gdm[4841]: deal_with_x_crashes: Running the XKeepsCrashing script
Aug 17 11:40:31 Tux3 kernel: [ 4074.781163] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug 17 11:40:31 Tux3 kernel: [ 4074.781200] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug 17 11:40:31 Tux3 kernel: [ 4074.781269] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Aug 17 11:40:58 Tux3 gdm[4841]: Failed to start X server several times in a short time period; disabling display :0
Aug 17 11:41:04 Tux3 gdm[7454]: GDM already running. Aborting!
Aug 17 11:41:09 Tux3 kernel: [ 4112.589091] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug 17 11:41:09 Tux3 kernel: [ 4112.589128] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug 17 11:41:09 Tux3 kernel: [ 4112.589196] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Aug 17 11:41:17 Tux3 gconfd (root-7524): starting (version 2.18.0.1), pid 7524 user 'root'
Aug 17 11:41:17 Tux3 gconfd (root-7524): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 17 11:41:17 Tux3 gconfd (root-7524): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug 17 11:41:17 Tux3 gconfd (root-7524): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 17 11:41:17 Tux3 gconfd (root-7524): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 17 11:41:17 Tux3 gconfd (root-7524): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 17 11:41:21 Tux3 gconfd (root-7524): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 0
Aug 17 11:43:47 Tux3 kernel: [ 4270.165324] BUG: unable to handle kernel paging request at virtual address f3110cf8
Aug 17 11:43:47 Tux3 kernel: [ 4270.165349]  printing eip:
Aug 17 11:43:47 Tux3 kernel: [ 4270.165351] c014ca4e
Aug 17 11:43:47 Tux3 kernel: [ 4270.165355] *pde = 00000000
Aug 17 11:43:47 Tux3 kernel: [ 4270.165366] Oops: 0002 [#1]
Aug 17 11:43:47 Tux3 kernel: [ 4270.165370] Modules linked in: speedstep_lib cpufreq_stats cpufreq_userspace cpufreq_conservative cpufreq_powersave cpufreq_ondemand freq_table dev_acpi sony_acpi tc1100_wmi pcc_acpi video asus_acpi button sbs container backlight i2c_ec battery dock ac af_packet quota_v2 nls_iso8859_1 nls_cp437 vfat fat it87 hwmon_vid i2c_isa eeprom parport_pc lp parport fuse nvidia(P) joydev snd_via82xx gameport snd_pcm_oss snd_mixer_oss snd_via82xx_modem snd_ac97_codec ac97_bus snd_pcm snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_viapro rtc via_ircc pcspkr usbhid hid irda snd i2c_core via_agp snd_page_alloc soundcore agpgart crc_ccitt shpchp pci_hotplug evdev tsdev ipv6 ext3 jbd mbcache ide_cd cdrom ide_disk floppy ehci_hcd via_rhine mii uhci_hcd via82cxxx generic ata_generic libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Aug 17 11:43:47 Tux3 kernel: [ 4270.165481] CPU:    0
Aug 17 11:43:47 Tux3 kernel: [ 4270.165483] EIP:    0060:[activate_page+62/160]    Tainted: P      VLI
Aug 17 11:43:47 Tux3 kernel: [ 4270.165485] EFLAGS: 00213082   (2.6.20-15-386 #2)
Aug 17 11:43:47 Tux3 kernel: [ 4270.165510] EIP is at activate_page+0x3e/0xa0
Aug 17 11:43:47 Tux3 kernel: [ 4270.165515] eax: c03920a4   ebx: c1110cd8   ecx: c111b998   edx: f3110cf8
Aug 17 11:43:47 Tux3 kernel: [ 4270.165519] esi: c1110cc0   edi: dfbd7f60   ebp: b62c7000   esp: dfbd7eec
Aug 17 11:43:47 Tux3 kernel: [ 4270.165523] ds: 007b   es: 007b   ss: 0068
Aug 17 11:43:47 Tux3 kernel: [ 4270.165528] Process Xorg (pid: 7464, ti=dfbd6000 task=d70f6030 task.ti=dfbd6000)
Aug 17 11:43:47 Tux3 kernel: [ 4270.165531] Stack: c1110cc0 cbca50a0 c014cefd 000000c9 c015e796 00000002 dfbd7f60 c1110cc0 
Aug 17 11:43:47 Tux3 kernel: [ 4270.165541]        c0395a80 00000000 00000000 c015234c 08ed4067 00000008 c0105685 000d0000 
Aug 17 11:43:47 Tux3 kernel: [ 4270.165550]        00000000 000d0000 b701f3e4 b62c7000 d2edee48 dcb0e3c0 00000b1c ccf08b60 
Aug 17 11:43:47 Tux3 kernel: [ 4270.165559] Call Trace:
Aug 17 11:43:47 Tux3 kernel: [ 4270.165577]  [mark_page_accessed+45/64] mark_page_accessed+0x2d/0x40
Aug 17 11:43:47 Tux3 kernel: [ 4270.165590]  [shmem_nopage+102/160] shmem_nopage+0x66/0xa0
Aug 17 11:43:47 Tux3 kernel: [ 4270.165625]  [__handle_mm_fault+300/2448] __handle_mm_fault+0x12c/0x990
Aug 17 11:43:47 Tux3 kernel: [ 4270.165646]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Aug 17 11:43:47 Tux3 kernel: [ 4270.165729]  [do_page_fault+296/1520] do_page_fault+0x128/0x5f0
Aug 17 11:43:47 Tux3 kernel: [ 4270.165750]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Aug 17 11:43:47 Tux3 kernel: [ 4270.165803]  [do_page_fault+0/1520] do_page_fault+0x0/0x5f0
Aug 17 11:43:47 Tux3 kernel: [ 4270.165818]  [error_code+116/128] error_code+0x74/0x80
Aug 17 11:43:47 Tux3 kernel: [ 4270.165864]  [__unix_find_socket_byname+3/112] __unix_find_socket_byname+0x3/0x70
Aug 17 11:43:47 Tux3 kernel: [ 4270.165912]  =======================
Aug 17 11:43:47 Tux3 kernel: [ 4270.165914] Code: 00 00 00 00 90 8b 06 a8 20 74 64 8b 06 a8 40 75 5e c1 ea 1e 8b 4e 18 69 c2 44 01 00 00 8d 5e 18 8b 53 04 05 60 1f 39 c0 89 51 04 <89> 0a c7 43 04 00 02 20 00 c7 46 18 00 01 10 00 83 a8 e4 00 00 
Aug 17 11:43:47 Tux3 kernel: [ 4270.165949] EIP: [activate_page+62/160] activate_page+0x3e/0xa0 SS:ESP 0068:dfbd7eec
Aug 17 11:43:47 Tux3 kernel: [ 4270.165959]  <1>BUG: unable to handle kernel paging request at virtual address f3110cf8
Aug 17 11:43:47 Tux3 kernel: [ 4270.474553]  printing eip:
Aug 17 11:43:47 Tux3 kernel: [ 4270.474560] c014ca4e
Aug 17 11:43:47 Tux3 kernel: [ 4270.474563] *pde = 00000000
Aug 17 11:43:47 Tux3 kernel: [ 4270.474574] Oops: 0002 [#2]
Aug 17 11:43:47 Tux3 kernel: [ 4270.474580] Modules linked in: speedstep_lib cpufreq_stats cpufreq_userspace cpufreq_conservative cpufreq_powersave cpufreq_ondemand freq_table dev_acpi sony_acpi tc1100_wmi pcc_acpi video asus_acpi button sbs container backlight i2c_ec battery dock ac af_packet quota_v2 nls_iso8859_1 nls_cp437 vfat fat it87 hwmon_vid i2c_isa eeprom parport_pc lp parport fuse nvidia(P) joydev snd_via82xx gameport snd_pcm_oss snd_mixer_oss snd_via82xx_modem snd_ac97_codec ac97_bus snd_pcm snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_viapro rtc via_ircc pcspkr usbhid hid irda snd i2c_core via_agp snd_page_alloc soundcore agpgart crc_ccitt shpchp pci_hotplug evdev tsdev ipv6 ext3 jbd mbcache ide_cd cdrom ide_disk floppy ehci_hcd via_rhine mii uhci_hcd via82cxxx generic ata_generic libata scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Aug 17 11:43:47 Tux3 kernel: [ 4270.474691] CPU:    0
Aug 17 11:43:47 Tux3 kernel: [ 4270.474692] EIP:    0060:[activate_page+62/160]    Tainted: P      VLI
Aug 17 11:43:47 Tux3 kernel: [ 4270.474694] EFLAGS: 00010082   (2.6.20-15-386 #2)
Aug 17 11:43:47 Tux3 kernel: [ 4270.474726] EIP is at activate_page+0x3e/0xa0
Aug 17 11:43:47 Tux3 kernel: [ 4270.474731] eax: c03920a4   ebx: c1110cd8   ecx: c111b998   edx: f3110cf8
Aug 17 11:43:47 Tux3 kernel: [ 4270.474735] esi: c1110cc0   edi: b6d47000   ebp: c1110cc0   esp: ca05bed4
Aug 17 11:43:47 Tux3 kernel: [ 4270.474739] ds: 007b   es: 007b   ss: 0068
Aug 17 11:43:47 Tux3 kernel: [ 4270.474745] Process assistant (pid: 7837, ti=ca05a000 task=ca0e3030 task.ti=ca05a000)
Aug 17 11:43:47 Tux3 kernel: [ 4270.474748] Stack: c1110cc0 cabff51c c014cefd 00000020 c0151b43 00000000 b6d4dfff 00000000 
Aug 17 11:43:47 Tux3 kernel: [ 4270.474757]        d2edfba8 ca05bf54 00000000 00000001 b6d4e000 ccb27b6c cb323900 c041c35c 
Aug 17 11:43:47 Tux3 kernel: [ 4270.474766]        00000000 ffffff37 00000000 ccb27b6c 0008cfda b6d4e000 00000000 ca05bf54 
Aug 17 11:43:47 Tux3 kernel: [ 4270.474774] Call Trace:
Aug 17 11:43:47 Tux3 kernel: [ 4270.474791]  [mark_page_accessed+45/64] mark_page_accessed+0x2d/0x40
Aug 17 11:43:47 Tux3 kernel: [ 4270.474802]  [unmap_vmas+1011/1296] unmap_vmas+0x3f3/0x510
Aug 17 11:43:47 Tux3 kernel: [ 4270.474896]  [exit_mmap+95/208] exit_mmap+0x5f/0xd0
Aug 17 11:43:47 Tux3 kernel: [ 4270.474936]  [mmput+34/112] mmput+0x22/0x70
Aug 17 11:43:47 Tux3 kernel: [ 4270.474957]  [do_exit+237/1920] do_exit+0xed/0x780
Aug 17 11:43:47 Tux3 kernel: [ 4270.474980]  [tasklet_action+67/144] tasklet_action+0x43/0x90
Aug 17 11:43:47 Tux3 kernel: [ 4270.474992]  [__do_softirq+82/160] __do_softirq+0x52/0xa0
Aug 17 11:43:47 Tux3 kernel: [ 4270.475035]  [do_group_exit+36/112] do_group_exit+0x24/0x70
Aug 17 11:43:47 Tux3 kernel: [ 4270.475045]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Aug 17 11:43:47 Tux3 kernel: [ 4270.475091]  [__unix_find_socket_byname+3/112] __unix_find_socket_byname+0x3/0x70
Aug 17 11:43:47 Tux3 kernel: [ 4270.475139]  =======================
Aug 17 11:43:47 Tux3 kernel: [ 4270.475141] Code: 00 00 00 00 90 8b 06 a8 20 74 64 8b 06 a8 40 75 5e c1 ea 1e 8b 4e 18 69 c2 44 01 00 00 8d 5e 18 8b 53 04 05 60 1f 39 c0 89 51 04 <89> 0a c7 43 04 00 02 20 00 c7 46 18 00 01 10 00 83 a8 e4 00 00 
Aug 17 11:43:47 Tux3 kernel: [ 4270.475178] EIP: [activate_page+62/160] activate_page+0x3e/0xa0 SS:ESP 0068:ca05bed4
Aug 17 11:43:47 Tux3 kernel: [ 4270.475187]  <1>Fixing recursive fault but reboot is needed!
Aug 17 11:43:47 Tux3 kernel: [ 4270.475277] BUG: scheduling while atomic: assistant/0x00000001/7837
Aug 17 11:43:47 Tux3 kernel: [ 4270.475296]  [schedule+1113/1408] __sched_text_start+0x459/0x580
Aug 17 11:43:47 Tux3 kernel: [ 4270.475364]  [cfq_free_io_context+47/96] cfq_free_io_context+0x2f/0x60
Aug 17 11:43:47 Tux3 kernel: [ 4270.475400]  [do_exit+1837/1920] do_exit+0x72d/0x780
Aug 17 11:43:47 Tux3 kernel: [ 4270.475439]  [printk+27/32] printk+0x1b/0x20
Aug 17 11:43:47 Tux3 kernel: [ 4270.475471]  [die+551/560] die+0x227/0x230
Aug 17 11:43:47 Tux3 kernel: [ 4270.475529]  [do_page_fault+753/1520] do_page_fault+0x2f1/0x5f0
Aug 17 11:43:47 Tux3 kernel: [ 4270.475589]  [do_page_fault+0/1520] do_page_fault+0x0/0x5f0
Aug 17 11:43:47 Tux3 kernel: [ 4270.475601]  [error_code+116/128] error_code+0x74/0x80
Aug 17 11:43:47 Tux3 kernel: [ 4270.475650]  [activate_page+62/160] activate_page+0x3e/0xa0
Aug 17 11:43:47 Tux3 kernel: [ 4270.475672]  [mark_page_accessed+45/64] mark_page_accessed+0x2d/0x40
Aug 17 11:43:47 Tux3 kernel: [ 4270.475682]  [unmap_vmas+1011/1296] unmap_vmas+0x3f3/0x510
Aug 17 11:43:47 Tux3 kernel: [ 4270.475773]  [exit_mmap+95/208] exit_mmap+0x5f/0xd0
Aug 17 11:43:47 Tux3 kernel: [ 4270.475811]  [mmput+34/112] mmput+0x22/0x70
Aug 17 11:43:47 Tux3 kernel: [ 4270.475823]  [do_exit+237/1920] do_exit+0xed/0x780
Aug 17 11:43:47 Tux3 kernel: [ 4270.475842]  [tasklet_action+67/144] tasklet_action+0x43/0x90
Aug 17 11:43:47 Tux3 kernel: [ 4270.475855]  [__do_softirq+82/160] __do_softirq+0x52/0xa0
Aug 17 11:43:47 Tux3 kernel: [ 4270.475897]  [do_group_exit+36/112] do_group_exit+0x24/0x70
Aug 17 11:43:47 Tux3 kernel: [ 4270.475909]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Aug 17 11:43:47 Tux3 kernel: [ 4270.475949]  [__unix_find_socket_byname+3/112] __unix_find_socket_byname+0x3/0x70
Aug 17 11:43:47 Tux3 kernel: [ 4270.475991]  =======================
Aug 17 11:43:47 Tux3 gconfd (root-7524): Received signal 15, shutting down cleanly
Aug 17 11:43:47 Tux3 gconfd (root-7524): Exiting
Aug 17 11:43:47 Tux3 gdm[7461]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Aug 17 11:43:49 Tux3 kernel: [ 4272.138931] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Aug 17 11:43:49 Tux3 kernel: [ 4272.138968] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Aug 17 11:43:49 Tux3 kernel: [ 4272.139037] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

```

---

### Post by dabl on 2007-08-17
Have you ever tried to let the Nvidia driver write your xorg.conf file?  I don't know that this will solve anything, but it's something you could try.  The basic console command is ```
sudo nvidia-xconfig
```

If you're wanting glx enabled for the Compiz/Beryl stuff, then it's ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

:)

---

### Post by nadalizadeh on 2007-08-17
Yes, I've tried it, No difference.

In addition uname output is :
Linux NorthPole 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux
:confused:
In addition I've tested 2.6.20-15-generic kernel.

---

### Post by enigma_0Z on 2007-10-15
Same issue. perhaps a bug in the nvidia driver?

---

