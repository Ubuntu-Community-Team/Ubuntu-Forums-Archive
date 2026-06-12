---
title: "TTYs no longer wake from suspend!"
date: 2009-05-10
forum: Hardware
---

### Post by mrowth on 2009-05-10
It had been working (mostly) for years, and was very stable on 9.04. I still get X/KDE back when I resume from suspend-to-RAM, but the virtual terminals/TTYs/text-mode consoles (whatever the best term is) never quite wake up. I can type into them (blindly), and thus "sudo kdm", "sudo gdm" or "startx" if X isn't running, but in the TTYs the screens (dualhead) stay perfectly dark. (It's not just a blank screen; the LEDs go from green to yellow.)

I'm not currently automatically starting KDM on boot. So I'm not suspecting the nvidia drivers (but nvidia-glx-180 is installed).

I've tried these suspend commands:
sudo pm-suspend
(No output)

sudo s2ram --force --vbe_post/_save/_mode (or all of them)
```
Switching from vt7 to vt1
fbcon fb0 state 1
Calling do_post
fbcon fb0 state 0
switching back to vt7)
```

sudo /etc/acpi/sleep.sh force
```
There is already a pid file /var/run/dhclient.eth0.pid with pid 3069
removed stale PID file                                              
Internet Systems Consortium DHCP Client V3.1.1                      
Copyright 2004-2008 Internet Systems Consortium.                    
All rights reserved.                                                
For info, please visit http://www.isc.org/sw/dhcp/                  

Listening on LPF/eth0/00:11:d8:3a:f6:97
Sending on   LPF/eth0/00:11:d8:3a:f6:97
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
 * Reloading /etc/samba/smb.conf smbd only
No process in pidfile `/var/run/samba/smbd.pid' found running; none killed.
   ...done.
 * Shutting down ALSA...                                                                                              [ OK ]
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
/etc/acpi/resume.d/55-screen.sh: line 6: 16161 Trace/breakpoint trap   vbetool dpms on
ifup: interface eth0 already configured
ifup: interface lo already configured
 * Setting up ALSA...                                                                                                 [ OK ]
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module button not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module button not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module fan not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module thermal not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module fan not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module thermal not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module acpi_sbs not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module ac not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module ac not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module battery not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module battery not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-pata, it will be ignored in a future release.
FATAL: Module acpi_sbs not found.

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
```

dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0
```
method return sender=:1.0 -> dest=:1.50 reply_serial=2
   int32 1)
```

+ whatever it is KDE does when you go to "Leave", then "Sleep". (I wish it would just tell me)

I have a partially-oldish-but-somewhat-evolved desktop machine, ASUS A8V Deluxe mobo, VIA KT800 chipset, Nvidia 7950 GT (AGP, drivers: nvidia-glx-180), Athlon X2 4800+, 3 x 1 GB DDR RAM, Kubuntu 9.04 (32 bit). 

Here's a systemlog. The msp3400 stuff is the ancient Hauppauge WinTV card not working after resume. (But it never has.)

```
May 10 19:43:05 earthworm kernel: [  607.784763] PM: Syncing filesystems ... done.                                                                       
May 10 19:43:05 earthworm kernel: [  607.799425] PM: Preparing system for mem sleep                                                                      
May 10 19:43:05 earthworm kernel: [  607.799430] Freezing user space processes ... (elapsed 0.00 seconds) done.                                          
May 10 19:43:05 earthworm kernel: [  607.800130] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.                                     
May 10 19:43:05 earthworm kernel: [  607.800201] PM: Entering mem sleep                                                                                  
May 10 19:43:05 earthworm kernel: [  607.800213] Suspending console(s) (use no_console_suspend to debug)                                                 
May 10 19:43:05 earthworm kernel: [  607.801771] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  608.296060] sd 2:0:1:0: [sdb] Synchronizing SCSI cache                                                              
May 10 19:43:05 earthworm kernel: [  608.296240] sd 2:0:1:0: [sdb] Stopping disk                                                                         
May 10 19:43:05 earthworm kernel: [  608.718432] sd 2:0:0:0: [sda] Synchronizing SCSI cache                                                              
May 10 19:43:05 earthworm kernel: [  608.718553] sd 2:0:0:0: [sda] Stopping disk                                                                         
May 10 19:43:05 earthworm kernel: [  609.054002] parport_pc 00:07: disabled                                                                              
May 10 19:43:05 earthworm kernel: [  609.054016] ACPI handle has no context!                                                                             
May 10 19:43:05 earthworm kernel: [  609.054027] NVRM: RmPowerManagement: 4                                                                              
May 10 19:43:05 earthworm kernel: [  609.348868] VIA 82xx Audio 0000:00:11.5: PCI INT C disabled                                                         
May 10 19:43:05 earthworm kernel: [  609.364079] ehci_hcd 0000:00:10.4: PCI INT C disabled                                                               
May 10 19:43:05 earthworm kernel: [  609.380040] uhci_hcd 0000:00:10.3: PCI INT B disabled                                                               
May 10 19:43:05 earthworm kernel: [  609.396040] uhci_hcd 0000:00:10.2: PCI INT B disabled                                                               
May 10 19:43:05 earthworm kernel: [  609.412040] uhci_hcd 0000:00:10.1: PCI INT A disabled                                                               
May 10 19:43:05 earthworm kernel: [  609.428039] uhci_hcd 0000:00:10.0: PCI INT A disabled                                                               
May 10 19:43:05 earthworm kernel: [  609.444152] pata_via 0000:00:0f.1: PCI INT A disabled                                                               
May 10 19:43:05 earthworm kernel: [  609.460089] sata_via 0000:00:0f.0: PCI INT B disabled                                                               
May 10 19:43:05 earthworm kernel: [  609.476080] skge eth0: disabling interface                                                                          
May 10 19:43:05 earthworm kernel: [  609.479038] ACPI handle has no context!                                                                             
May 10 19:43:05 earthworm kernel: [  609.479043] ACPI handle has no context!                                                                             
May 10 19:43:05 earthworm kernel: [  609.508038] PM: suspend devices took 1.708 seconds                                                                  
May 10 19:43:05 earthworm kernel: [  609.508230] ACPI: Preparing to enter system sleep state S3                                                          
May 10 19:43:05 earthworm kernel: [  609.508678] Disabling non-boot CPUs ...                                                                             
May 10 19:43:05 earthworm kernel: [  609.612012] CPU 1 is now offline                                                                                    
May 10 19:43:05 earthworm kernel: [  609.612015] SMP alternatives: switching to UP code                                                                  
May 10 19:43:05 earthworm kernel: [  609.766389] CPU0 attaching NULL sched-domain.                                                                       
May 10 19:43:05 earthworm kernel: [  609.766392] CPU1 attaching NULL sched-domain.                                                                       
May 10 19:43:05 earthworm kernel: [  609.766546] CPU0 attaching NULL sched-domain.                                                                       
May 10 19:43:05 earthworm kernel: [  609.766699] CPU1 is down                                                                                            
May 10 19:43:05 earthworm kernel: [  609.766782] Extended CMOS year: 2000                                                                                
May 10 19:43:05 earthworm kernel: [  609.766782] Back to C!                                                                                              
May 10 19:43:05 earthworm kernel: [  609.766782] Extended CMOS year: 2000                                                                                
May 10 19:43:05 earthworm kernel: [  609.766782] pci 0000:00:11.0: Enabled onboard AC97/MC97 devices                                                     
May 10 19:43:05 earthworm kernel: [  609.766782] Enabling non-boot CPUs ...                                                                              
May 10 19:43:05 earthworm kernel: [  609.766782] SMP alternatives: switching to SMP code                                                                 
May 10 19:43:05 earthworm kernel: [  609.924617] Booting processor 1 APIC 0x1 ip 0x6000                                                                  
May 10 19:43:05 earthworm kernel: [  609.766262] Initializing CPU#1                                                                                      
May 10 19:43:05 earthworm kernel: [  609.766262] Calibrating delay using timer specific routine.. 4806.23 BogoMIPS (lpj=9612470)                         
May 10 19:43:05 earthworm kernel: [  609.766262] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)                                       
May 10 19:43:05 earthworm kernel: [  609.766262] CPU: L2 Cache: 1024K (64 bytes/line)                                                                    
May 10 19:43:05 earthworm kernel: [  609.766262] CPU: Physical Processor ID: 0                                                                           
May 10 19:43:05 earthworm kernel: [  609.766262] CPU: Processor Core ID: 1                                                                               
May 10 19:43:05 earthworm kernel: [  610.012149] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ stepping 02                                        
May 10 19:43:05 earthworm kernel: [  610.012217] CPU0 attaching NULL sched-domain.                                                                       
May 10 19:43:05 earthworm kernel: [  610.012410] CPU0 attaching sched-domain:                                                                            
May 10 19:43:05 earthworm kernel: [  610.012413]  domain 0: span 0-1 level CPU                                                                           
May 10 19:43:05 earthworm kernel: [  610.012414]   groups: 0 1                                                                                           
May 10 19:43:05 earthworm kernel: [  610.012418] CPU1 attaching sched-domain:                                                                            
May 10 19:43:05 earthworm kernel: [  610.012420]  domain 0: span 0-1 level CPU                                                                           
May 10 19:43:05 earthworm kernel: [  610.012421]   groups: 1 0                                                                                           
May 10 19:43:05 earthworm kernel: [  610.012665] CPU1 is up                                                                                              
May 10 19:43:05 earthworm kernel: [  610.012668] ACPI: Waking up from system sleep state S3                                                              
May 10 19:43:05 earthworm kernel: [  610.013013] Switched to high resolution mode on CPU 1                                                               
May 10 19:43:05 earthworm kernel: [  610.028147] pci 0000:00:01.0: setting latency timer to 64                                                           
May 10 19:43:05 earthworm kernel: [  610.044056] skge eth0: enabling interface                                                                           
May 10 19:43:05 earthworm kernel: [  610.047077] bttv 0000:00:0e.0: PCI INT A -> Link[LNKD] -> GSI 4 (level, low) -> IRQ 4                               
May 10 19:43:05 earthworm kernel: [  610.047080] bttv0: Can't enable device.                                                                             
May 10 19:43:05 earthworm kernel: [  610.047086] pm_op(): pci_pm_resume+0x0/0x70 returns -5                                                              
May 10 19:43:05 earthworm kernel: [  610.047088] PM: Device 0000:00:0e.0 failed to resume: error -5                                                      
May 10 19:43:05 earthworm kernel: [  610.047108] Bt87x 0000:00:0e.1: PCI INT A -> Link[LNKD] -> GSI 4 (level, low) -> IRQ 4                              
May 10 19:43:05 earthworm kernel: [  610.060041] sata_via 0000:00:0f.0: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11                         
May 10 19:43:05 earthworm kernel: [  610.076017] pata_via 0000:00:0f.1: restoring config space at offset 0xf (was 0x1ff, writing 0x103)                  
May 10 19:43:05 earthworm kernel: [  610.076042] pata_via 0000:00:0f.1: PCI INT A -> Link[LNKA] -> GSI 3 (level, low) -> IRQ 3                           
May 10 19:43:05 earthworm kernel: [  610.092015] uhci_hcd 0000:00:10.0: PCI INT A -> Link[LNKA] -> GSI 3 (level, low) -> IRQ 3                           
May 10 19:43:05 earthworm kernel: [  610.092055] usb usb2: root hub lost power or was reset                                                              
May 10 19:43:05 earthworm kernel: [  610.108014] uhci_hcd 0000:00:10.1: PCI INT A -> Link[LNKA] -> GSI 3 (level, low) -> IRQ 3                           
May 10 19:43:05 earthworm kernel: [  610.108052] usb usb3: root hub lost power or was reset                                                              
May 10 19:43:05 earthworm kernel: [  610.124013] uhci_hcd 0000:00:10.2: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11                         
May 10 19:43:05 earthworm kernel: [  610.124051] usb usb4: root hub lost power or was reset                                                              
May 10 19:43:05 earthworm kernel: [  610.140014] uhci_hcd 0000:00:10.3: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11                         
May 10 19:43:05 earthworm kernel: [  610.140052] usb usb5: root hub lost power or was reset                                                              
May 10 19:43:05 earthworm kernel: [  610.156013] ehci_hcd 0000:00:10.4: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5                           
May 10 19:43:05 earthworm kernel: [  610.172038] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5                     
May 10 19:43:05 earthworm kernel: [  610.172044] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64                                                
May 10 19:43:05 earthworm kernel: [  610.175087] pci 0000:00:11.6: restoring config space at offset 0xf (was 0x300, writing 0x305)                       
May 10 19:43:05 earthworm kernel: [  610.175101] pci 0000:00:11.6: restoring config space at offset 0x4 (was 0x1, writing 0x1001)                        
May 10 19:43:05 earthworm kernel: [  610.175107] pci 0000:00:11.6: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100001)               
May 10 19:43:05 earthworm kernel: [  610.175160] NVRM: RmPowerManagement: 5                                                                              
May 10 19:43:05 earthworm kernel: [  610.316568] ata4.00: ACPI cmd ef/03:44:00:00:00:a0 filtered out                                                     
May 10 19:43:05 earthworm kernel: [  610.364425] ata4.00: configured for UDMA/66                                                                         
May 10 19:43:05 earthworm kernel: [  611.640924] parport_pc 00:07: activated                                                                             
May 10 19:43:05 earthworm kernel: [  611.640996] sd 2:0:0:0: [sda] Starting disk                                                                         
May 10 19:43:05 earthworm kernel: [  611.730813] skge eth0: Link is up at 100 Mbps, full duplex, flow control both                                       
May 10 19:43:05 earthworm kernel: [  615.120011] ata3: link is slow to respond, please be patient (ready=0)                                              
May 10 19:43:05 earthworm kernel: [  617.244346] ata3.01: ACPI cmd ef/03:45:00:00:00:b0 filtered out                                                     
May 10 19:43:05 earthworm kernel: [  617.244348] ata3.01: ACPI cmd ef/03:01:00:00:00:b0 filtered out                                                     
May 10 19:43:05 earthworm kernel: [  617.244494] ata3.01: ACPI cmd c6/00:10:00:00:00:b0 succeeded                                                        
May 10 19:43:05 earthworm kernel: [  617.268338] ata3.00: ACPI cmd ef/03:46:00:00:00:a0 filtered out                                                     
May 10 19:43:05 earthworm kernel: [  617.268340] ata3.00: ACPI cmd ef/03:01:00:00:00:a0 filtered out                                                     
May 10 19:43:05 earthworm kernel: [  617.268527] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded                                                        
May 10 19:43:05 earthworm kernel: [  617.308392] ata3.00: configured for UDMA/133                                                                        
May 10 19:43:05 earthworm kernel: [  617.316362] ata3.01: configured for UDMA/100                                                                        
May 10 19:43:05 earthworm kernel: [  617.364390] ata3.00: configured for UDMA/133                                                                        
May 10 19:43:05 earthworm kernel: [  617.372362] ata3.01: configured for UDMA/100                                                                        
May 10 19:43:05 earthworm kernel: [  617.372365] ata3: EH complete                                                                                       
May 10 19:43:05 earthworm kernel: [  617.397769] sd 2:0:0:0: [sda] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)                               
May 10 19:43:05 earthworm kernel: [  617.397784] sd 2:0:0:0: [sda] Write Protect is off                                                                  
May 10 19:43:05 earthworm kernel: [  617.397786] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                               
May 10 19:43:05 earthworm kernel: [  617.397805] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                 
May 10 19:43:05 earthworm kernel: [  617.397828] sd 2:0:1:0: [sdb] 781422768 512-byte hardware sectors: (400 GB/372 GiB)                                 
May 10 19:43:05 earthworm kernel: [  617.397839] sd 2:0:1:0: [sdb] Write Protect is off                                                                  
May 10 19:43:05 earthworm kernel: [  617.397841] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00                                                               
May 10 19:43:05 earthworm kernel: [  617.397858] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                 
May 10 19:43:05 earthworm kernel: [  617.397877] sd 2:0:0:0: [sda] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)                               
May 10 19:43:05 earthworm kernel: [  617.397887] sd 2:0:0:0: [sda] Write Protect is off                                                                  
May 10 19:43:05 earthworm kernel: [  617.397889] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                               
May 10 19:43:05 earthworm kernel: [  617.397905] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                 
May 10 19:43:05 earthworm kernel: [  617.397924] sd 2:0:1:0: [sdb] 781422768 512-byte hardware sectors: (400 GB/372 GiB)                                 
May 10 19:43:05 earthworm kernel: [  617.397934] sd 2:0:1:0: [sdb] Write Protect is off                                                                  
May 10 19:43:05 earthworm kernel: [  617.397936] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00                                                               
May 10 19:43:05 earthworm kernel: [  617.397953] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                 
May 10 19:43:05 earthworm kernel: [  617.397961] sd 2:0:1:0: [sdb] Starting disk                                                                         
May 10 19:43:05 earthworm kernel: [  618.096011] usb 2-1: reset full speed USB device using uhci_hcd and address 2                                       
May 10 19:43:05 earthworm kernel: [  618.504013] usb 3-2: reset low speed USB device using uhci_hcd and address 2                                        
May 10 19:43:05 earthworm kernel: [  618.815538] PM: resume devices took 8.800 seconds                                                                   
May 10 19:43:05 earthworm kernel: [  618.815544] ------------[ cut here ]------------                                                                    
May 10 19:43:05 earthworm kernel: [  618.815546] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x80/0x90()          
May 10 19:43:05 earthworm kernel: [  618.815547] Component: resume devices                                                                               
May 10 19:43:05 earthworm kernel: [  618.815549] Modules linked in: bridge stp bnep nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs binfmt_misc input_pol ldev video output nls_iso8859_1 nls_cp437 vfat fat dm_crypt lp nvidia(P) snd_via82xx tuner_simple tuner_types gameport snd_bt87x snd_via82xx_modem snd_a c97_codec tuner snd_seq_dummy ac97_bus snd_mpu401_uart snd_pcm_oss snd_seq_oss tvaudio snd_mixer_oss snd_seq_midi snd_seq_midi_event snd_pcm snd_rawmidi  snd_seq shpchp snd_seq_device snd_timer snd soundcore msp3400 snd_page_alloc bttv videodev v4l1_compat ir_common compat_ioctl32 i2c_algo_bit v4l2_commo n videobuf_dma_sg videobuf_core btcx_risc ppdev tveeprom k8temp pcspkr usbhid i2c_viapro amd64_agp agpgart parport_pc parport skge floppy vesafb fbcon t ileblit font bitblit softcursor                                                                                                                          
May 10 19:43:05 earthworm kernel: [  618.815582] Pid: 6547, comm: pm-suspend Tainted: P        W  2.6.28-11-generic #42-Ubuntu                           
May 10 19:43:05 earthworm kernel: [  618.815584] Call Trace:                                                                                             
May 10 19:43:05 earthworm kernel: [  618.815588]  [<c0139ab0>] warn_slowpath+0x60/0x80                                                                   
May 10 19:43:05 earthworm kernel: [  618.815592]  [<c01537fa>] ? down_trylock+0x2a/0x40                                                                  
May 10 19:43:05 earthworm kernel: [  618.815594]  [<c013a10d>] ? try_acquire_console_sem+0xd/0x30                                                        
May 10 19:43:05 earthworm kernel: [  618.815598]  [<c02c7290>] ? kobject_put+0x20/0x50                                                                   
May 10 19:43:05 earthworm kernel: [  618.815603]  [<c0500ac6>] ? printk+0x18/0x1a                                                                        
May 10 19:43:05 earthworm kernel: [  618.815605]  [<c0164fd0>] suspend_test_finish+0x80/0x90                                                             
May 10 19:43:05 earthworm kernel: [  618.815608]  [<c01650a6>] suspend_devices_and_enter+0xc6/0x160                                                      
May 10 19:43:05 earthworm kernel: [  618.815611]  [<c0500ac6>] ? printk+0x18/0x1a                                                                        
May 10 19:43:05 earthworm kernel: [  618.815613]  [<c0165329>] enter_state+0xc9/0x100                                                                    
May 10 19:43:05 earthworm kernel: [  618.815616]  [<c01653dd>] state_store+0x7d/0xc0                                                                     
May 10 19:43:05 earthworm kernel: [  618.815618]  [<c0165360>] ? state_store+0x0/0xc0                                                                    
May 10 19:43:05 earthworm kernel: [  618.815620]  [<c02c7154>] kobj_attr_store+0x24/0x30                                                                 
May 10 19:43:05 earthworm kernel: [  618.815623]  [<c020ab02>] sysfs_write_file+0x92/0xf0                                                                
May 10 19:43:05 earthworm kernel: [  618.815627]  [<c01bdab8>] vfs_write+0x98/0x110                                                                      
May 10 19:43:05 earthworm kernel: [  618.815629]  [<c020aa70>] ? sysfs_write_file+0x0/0xf0                                                               
May 10 19:43:05 earthworm kernel: [  618.815631]  [<c01bdbed>] sys_write+0x3d/0x70                                                                       
May 10 19:43:05 earthworm kernel: [  618.815634]  [<c0103f6b>] sysenter_do_call+0x12/0x2f                                                                
May 10 19:43:05 earthworm kernel: [  618.815636] ---[ end trace 6b9dba5940d6b4c8 ]---                                                                    
May 10 19:43:05 earthworm kernel: [  618.815662] PM: Finishing wakeup.                                                                                   
May 10 19:43:05 earthworm kernel: [  618.815663] Restarting tasks ... <4>msp3400' 1-0040: I/O error #0 (write 0x12/0x00)                                 
May 10 19:43:05 earthworm kernel: [  618.834048] done.                                                                                                   
May 10 19:43:05 earthworm kernel: [  618.861038] msp3400' 1-0040: I/O error #1 (write 0x12/0x00)                                                         
May 10 19:43:05 earthworm kernel: [  618.872511] msp3400' 1-0040: I/O error #2 (write 0x12/0x00)                                                         
May 10 19:43:05 earthworm kernel: [  618.884022] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  618.885327] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  618.885969] msp3400' 1-0040: I/O error #0 (write 0x12/0x07)                                                         
May 10 19:43:05 earthworm kernel: [  618.896510] msp3400' 1-0040: I/O error #1 (write 0x12/0x07)                                                         
May 10 19:43:05 earthworm kernel: [  618.908499] msp3400' 1-0040: I/O error #2 (write 0x12/0x07)                                                         
May 10 19:43:05 earthworm kernel: [  618.920015] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  618.921320] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  618.921959] msp3400' 1-0040: I/O error #0 (write 0x12/0x40)                                                         
May 10 19:43:05 earthworm kernel: [  618.932500] msp3400' 1-0040: I/O error #1 (write 0x12/0x40)                                                         
May 10 19:43:05 earthworm kernel: [  618.944501] msp3400' 1-0040: I/O error #2 (write 0x12/0x40)                                                         
May 10 19:43:05 earthworm kernel: [  618.956013] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  618.957316] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  618.957953] msp3400' 1-0040: I/O error #0 (write 0x12/0x06)                                                         
May 10 19:43:05 earthworm kernel: [  618.968498] msp3400' 1-0040: I/O error #1 (write 0x12/0x06)                                                         
May 10 19:43:05 earthworm kernel: [  618.980501] msp3400' 1-0040: I/O error #2 (write 0x12/0x06)                                                         
May 10 19:43:05 earthworm kernel: [  618.992011] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  618.993387] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  618.994033] msp3400' 1-0040: I/O error #0 (write 0x12/0x01)                                                         
May 10 19:43:05 earthworm kernel: [  619.004512] msp3400' 1-0040: I/O error #1 (write 0x12/0x01)                                                         
May 10 19:43:05 earthworm kernel: [  619.016511] msp3400' 1-0040: I/O error #2 (write 0x12/0x01)                                                         
May 10 19:43:05 earthworm kernel: [  619.028024] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.029329] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.029972] msp3400' 1-0040: I/O error #0 (write 0x12/0x02)                                                         
May 10 19:43:05 earthworm kernel: [  619.040521] msp3400' 1-0040: I/O error #1 (write 0x12/0x02)                                                         
May 10 19:43:05 earthworm kernel: [  619.052498] msp3400' 1-0040: I/O error #2 (write 0x12/0x02)                                                         
May 10 19:43:05 earthworm kernel: [  619.064014] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.065319] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.065963] msp3400' 1-0040: I/O error #0 (write 0x12/0x03)                                                         
May 10 19:43:05 earthworm kernel: [  619.076499] msp3400' 1-0040: I/O error #1 (write 0x12/0x03)                                                         
May 10 19:43:05 earthworm kernel: [  619.097510] msp3400' 1-0040: I/O error #2 (write 0x12/0x03)                                                         
May 10 19:43:05 earthworm kernel: [  619.109012] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.110316] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.110961] msp3400' 1-0040: I/O error #0 (write 0x12/0x04)                                                         
May 10 19:43:05 earthworm kernel: [  619.121496] msp3400' 1-0040: I/O error #1 (write 0x12/0x04)                                                         
May 10 19:43:05 earthworm kernel: [  619.133530] msp3400' 1-0040: I/O error #2 (write 0x12/0x04)                                                         
May 10 19:43:05 earthworm kernel: [  619.145025] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.146467] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.147113] msp3400' 1-0040: I/O error #0 (write 0x12/0x30)                                                         
May 10 19:43:05 earthworm kernel: [  619.157553] msp3400' 1-0040: I/O error #1 (write 0x12/0x30)                                                         
May 10 19:43:05 earthworm kernel: [  619.169536] msp3400' 1-0040: I/O error #2 (write 0x12/0x30)                                                         
May 10 19:43:05 earthworm kernel: [  619.181040] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.182347] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.182990] msp3400' 1-0040: I/O error #0 (write 0x12/0x31)                                                         
May 10 19:43:05 earthworm kernel: [  619.193536] msp3400' 1-0040: I/O error #1 (write 0x12/0x31)                                                         
May 10 19:43:05 earthworm kernel: [  619.205535] msp3400' 1-0040: I/O error #2 (write 0x12/0x31)                                                         
May 10 19:43:05 earthworm kernel: [  619.217014] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.218314] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.218956] msp3400' 1-0040: I/O error #0 (write 0x12/0x32)                                                         
May 10 19:43:05 earthworm kernel: [  619.229525] msp3400' 1-0040: I/O error #1 (write 0x12/0x32)                                                         
May 10 19:43:05 earthworm kernel: [  619.241540] msp3400' 1-0040: I/O error #2 (write 0x12/0x32)                                                         
May 10 19:43:05 earthworm kernel: [  619.253038] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.254346] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.254989] msp3400' 1-0040: I/O error #0 (write 0x12/0x33)                                                         
May 10 19:43:05 earthworm kernel: [  619.265554] msp3400' 1-0040: I/O error #1 (write 0x12/0x33)                                                         
May 10 19:43:05 earthworm kernel: [  619.277507] msp3400' 1-0040: I/O error #2 (write 0x12/0x33)                                                         
May 10 19:43:05 earthworm kernel: [  619.289029] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.290667] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.489516] msp3400' 1-0040: I/O error #0 (write 0x10/0x20)                                                         
May 10 19:43:05 earthworm kernel: [  619.501511] msp3400' 1-0040: I/O error #1 (write 0x10/0x20)                                                         
May 10 19:43:05 earthworm kernel: [  619.513513] msp3400' 1-0040: I/O error #2 (write 0x10/0x20)                                                         
May 10 19:43:05 earthworm kernel: [  619.525018] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.526436] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.625512] msp3400' 1-0040: I/O error #0 (read 0x10/0x7e)                                                          
May 10 19:43:05 earthworm kernel: [  619.637508] msp3400' 1-0040: I/O error #1 (read 0x10/0x7e)                                                          
May 10 19:43:05 earthworm kernel: [  619.649536] msp3400' 1-0040: I/O error #2 (read 0x10/0x7e)                                                          
May 10 19:43:05 earthworm kernel: [  619.661014] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.662324] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.662970] msp3400' 1-0040: I/O error #0 (write 0x12/0x0d)                                                         
May 10 19:43:05 earthworm kernel: [  619.673531] msp3400' 1-0040: I/O error #1 (write 0x12/0x0d)                                                         
May 10 19:43:05 earthworm kernel: [  619.685507] msp3400' 1-0040: I/O error #2 (write 0x12/0x0d)                                                         
May 10 19:43:05 earthworm kernel: [  619.697014] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.698348] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.699057] msp3400' 1-0040: I/O error #0 (write 0x12/0x0e)                                                         
May 10 19:43:05 earthworm kernel: [  619.709503] msp3400' 1-0040: I/O error #1 (write 0x12/0x0e)                                                         
May 10 19:43:05 earthworm kernel: [  619.721505] msp3400' 1-0040: I/O error #2 (write 0x12/0x0e)                                                         
May 10 19:43:05 earthworm kernel: [  619.733016] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:05 earthworm kernel: [  619.734356] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:05 earthworm kernel: [  619.734998] msp3400' 1-0040: I/O error #0 (write 0x12/0x10)                                                         
May 10 19:43:05 earthworm kernel: [  619.745520] msp3400' 1-0040: I/O error #1 (write 0x12/0x10)                                                         
May 10 19:43:06 earthworm kernel: [  619.757538] msp3400' 1-0040: I/O error #2 (write 0x12/0x10)                                                         
May 10 19:43:06 earthworm kernel: [  619.769023] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:06 earthworm kernel: [  619.770458] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:06 earthworm kernel: [  619.771105] msp3400' 1-0040: I/O error #0 (write 0x12/0x00)                                                         
May 10 19:43:06 earthworm kernel: [  619.781517] msp3400' 1-0040: I/O error #1 (write 0x12/0x00)                                                         
May 10 19:43:06 earthworm kernel: [  619.793542] msp3400' 1-0040: I/O error #2 (write 0x12/0x00)                                                         
May 10 19:43:06 earthworm kernel: [  619.805026] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:06 earthworm kernel: [  619.806332] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:06 earthworm kernel: [  619.806974] msp3400' 1-0040: I/O error #0 (write 0x12/0x07)                                                         
May 10 19:43:06 earthworm kernel: [  619.817540] msp3400' 1-0040: I/O error #1 (write 0x12/0x07)                                                         
May 10 19:43:06 earthworm kernel: [  619.830493] msp3400' 1-0040: I/O error #2 (write 0x12/0x07)                                                         
May 10 19:43:06 earthworm kernel: [  619.841019] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:06 earthworm kernel: [  619.842352] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:06 earthworm kernel: [  619.843037] msp3400' 1-0040: I/O error #0 (write 0x12/0x40)                                                         
May 10 19:43:06 earthworm kernel: [  619.853515] msp3400' 1-0040: I/O error #1 (write 0x12/0x40)                                                         
May 10 19:43:06 earthworm kernel: [  619.865518] msp3400' 1-0040: I/O error #2 (write 0x12/0x40)                                                         
May 10 19:43:06 earthworm kernel: [  619.877137] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:06 earthworm kernel: [  619.878537] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:06 earthworm kernel: [  619.879179] msp3400' 1-0040: I/O error #0 (write 0x12/0x06)                                                         
May 10 19:43:06 earthworm kernel: [  619.889588] msp3400' 1-0040: I/O error #1 (write 0x12/0x06)                                                         
May 10 19:43:06 earthworm kernel: [  619.901554] msp3400' 1-0040: I/O error #2 (write 0x12/0x06)                                                         
May 10 19:43:06 earthworm kernel: [  619.913021] msp3400' 1-0040: resetting chip, sound will go off.                                                     
May 10 19:43:06 earthworm kernel: [  619.914378] msp3400' 1-0040: chip reset failed                                                                      
May 10 19:43:06 earthworm kernel: [  619.915020] msp3400' 1-0040: I/O error #0 (write 0x12/0x01)                                                         
May 10 19:43:06 earthworm kernel: [  619.925514] msp3400' 1-0040: I/O error #1 (write 0x12/0x01)
May 10 19:43:06 earthworm kernel: [  619.937547] msp3400' 1-0040: I/O error #2 (write 0x12/0x01)
May 10 19:43:06 earthworm kernel: [  619.949020] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  619.950384] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm kernel: [  619.951052] msp3400' 1-0040: I/O error #0 (write 0x12/0x02)
May 10 19:43:06 earthworm kernel: [  619.961518] msp3400' 1-0040: I/O error #1 (write 0x12/0x02)
May 10 19:43:06 earthworm kernel: [  619.973514] msp3400' 1-0040: I/O error #2 (write 0x12/0x02)
May 10 19:43:06 earthworm kernel: [  619.985025] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  619.986331] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm kernel: [  619.986973] msp3400' 1-0040: I/O error #0 (write 0x12/0x03)
May 10 19:43:06 earthworm kernel: [  619.997513] msp3400' 1-0040: I/O error #1 (write 0x12/0x03)
May 10 19:43:06 earthworm kernel: [  620.011636] msp3400' 1-0040: I/O error #2 (write 0x12/0x03)
May 10 19:43:06 earthworm kernel: [  620.021107] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  620.024236] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm kernel: [  620.024881] msp3400' 1-0040: I/O error #0 (write 0x12/0x04)
May 10 19:43:06 earthworm kernel: [  620.033528] msp3400' 1-0040: I/O error #1 (write 0x12/0x04)
May 10 19:43:06 earthworm kernel: [  620.045595] msp3400' 1-0040: I/O error #2 (write 0x12/0x04)
May 10 19:43:06 earthworm anacron[6849]: Anacron 2.3 started on 2009-05-10
May 10 19:43:06 earthworm anacron[6849]: Will run job `cron.weekly' in 10 min.
May 10 19:43:06 earthworm anacron[6849]: Jobs will be executed sequentially
May 10 19:43:06 earthworm kernel: [  620.057023] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  620.058376] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm kernel: [  620.059072] msp3400' 1-0040: I/O error #0 (write 0x12/0x30)
May 10 19:43:06 earthworm acpid: client 4554[0:0] has disconnected
May 10 19:43:06 earthworm acpid: client 4554[0:0] has disconnected
May 10 19:43:06 earthworm acpid: client connected from 4554[0:0]
May 10 19:43:06 earthworm kernel: [  620.069548] msp3400' 1-0040: I/O error #1 (write 0x12/0x30)
May 10 19:43:06 earthworm kernel: [  620.081585] msp3400' 1-0040: I/O error #2 (write 0x12/0x30)
May 10 19:43:06 earthworm kernel: [  620.093016] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  620.094496] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm kernel: [  620.095043] msp3400' 1-0040: I/O error #0 (write 0x12/0x31)
May 10 19:43:06 earthworm kernel: [  620.105608] msp3400' 1-0040: I/O error #1 (write 0x12/0x31)
May 10 19:43:06 earthworm kernel: [  620.117535] msp3400' 1-0040: I/O error #2 (write 0x12/0x31)
May 10 19:43:06 earthworm kernel: [  620.129022] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  620.130426] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm kernel: [  620.130912] msp3400' 1-0040: I/O error #0 (write 0x12/0x32)
May 10 19:43:06 earthworm kernel: [  620.159241] msp3400' 1-0040: I/O error #1 (write 0x12/0x32)
May 10 19:43:06 earthworm kernel: [  620.170423] msp3400' 1-0040: I/O error #2 (write 0x12/0x32)
May 10 19:43:06 earthworm kernel: [  620.181031] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  620.183429] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm kernel: [  620.184169] msp3400' 1-0040: I/O error #0 (write 0x12/0x33)
May 10 19:43:06 earthworm kernel: [  620.193801] msp3400' 1-0040: I/O error #1 (write 0x12/0x33)
May 10 19:43:06 earthworm kernel: [  620.205780] msp3400' 1-0040: I/O error #2 (write 0x12/0x33)
May 10 19:43:06 earthworm kernel: [  620.217017] msp3400' 1-0040: resetting chip, sound will go off.
May 10 19:43:06 earthworm kernel: [  620.219232] msp3400' 1-0040: chip reset failed
May 10 19:43:06 earthworm acpid: client connected from 4554[0:0]
```

I only installed acpid and acpi-support and powersaved and some dependencies because I hoped they'd help, but they didn't, and I hadn't used them before either. Powersaved only conflicts with KDE's PowerDevil.

---

### Post by mrowth on 2009-05-11
As of now it's working again. Can't say I did anything except give up. I hope it's not spuriously malfunctioning hardware. :confused:
Edit: Must be one of those services I'm not running in runlevel 2 but in rl 3.

---

