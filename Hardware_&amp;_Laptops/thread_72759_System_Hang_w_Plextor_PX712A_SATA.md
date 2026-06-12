---
title: "System Hang w/ Plextor PX712A SATA"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by pm124493 on 2005-10-07
I am using Kubuntu 5.04 with K3B. K3B detects the Plextor drive as a DVDR, CDRW drive correctly. If I insert a blank disc or cdrecord -scanbus the system will hang.
Any clues what might cause this?
ASUS P4S800D-X, P4 2.53, DDR400 1Gb, Nvidia 6600GT OC
SIS5513: chipset revision 1
SIS5513: not 100%% native mode: will probe irqs later
SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
hda: Maxtor 6Y080L0, ATA DISK drive
hdb: Maxtor 6Y080L0, ATA DISK drive
ata1: dev 0 ATA, max UDMA/133, 240121728 sectors:
ata1(0): applying bridge limits
ata1: dev 0 configured for UDMA/100
scsi0 : sata_sis
NET: Registered protocol family 17
ata2: dev 0 ATAPI, max UDMA/33
ata2(0): applying bridge limits
ata2: dev 0 configured for UDMA/33
scsi1 : sata_sis
Vendor: ATA       Model: Maxtor 6Y120L0    Rev: YAR4
Type:   Direct-Access                      ANSI SCSI revision: 05
PLEXTOR   Model: DVDR   PX-712A    Rev: 1.07
Type:   CD-ROM                             ANSI SCSI revision: 05
SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
SCSI device sda: drive cache: write back
sda: 240121728 512-byte hdwr sectors (122942 MB)
sda: drive cache: write back
/dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 5
-------------The following came out of kernel log -----------------------------------

Oct  7 07:35:18 localhost exiting on signal 15
Oct  7 07:35:19 localhost syslogd 1.4.1#16ubuntu6: restart.
Oct  7 07:39:14 localhost kernel: Device sr0 not ready.
Oct  7 07:53:07 localhost kernel: Device sr0 not ready.
Oct  7 07:53:07 localhost last message repeated 2 times
Oct  7 07:53:35 localhost kernel: cdrom: This disc doesn't have any tracks I recognize!
Oct  7 07:54:43 localhost kernel: ------------[ cut here ]------------
Oct  7 07:54:43 localhost kernel: PREEMPT 
Oct  7 07:54:43 localhost kernel: Modules linked in: proc_intf cpufreq_powersave cpufreq_userspace cpufreq_ondemand freq_table video battery container button pcc_acpi sony_acpi ac ipv6 usblp joydev sg ohci1394 sd_mod sr_mod af_packet tsdev sata_sis libata sis900 usbhid ohci_hcd usbcore snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug sis_agp floppy pcspkr rtc nls_cp437 ntfs evdev md dm_mod capability commoncap nvidia agpgart sbp2 scsi_mod ieee1394 psmouse mousedev parport_pc lp parport ide_cd cdrom reiserfs ext2 ext3 jbd mbcache ide_generic ide_disk sis5513 ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Oct  7 07:54:43 localhost kernel: CPU:    0
Oct  7 07:54:43 localhost kernel: EIP:    0060:[pg0+945378055/1069941760]    Tainted: P      VLI
Oct  7 07:54:43 localhost kernel: EFLAGS: 00010046   (2.6.10-5-686) 
Oct  7 07:54:43 localhost kernel: EIP is at scsi_put_command+0xb6/0xc3 [scsi_mod]
Oct  7 07:54:43 localhost kernel: eax: f3f25800   ebx: f5716090   ecx: 00000000   edx: f5716090
Oct  7 07:54:43 localhost kernel: esi: f3b20000   edi: f5716080   ebp: f427d000   esp: f3b21e6c
Oct  7 07:54:43 localhost kernel: ds: 007b   es: 007b   ss: 0068
Oct  7 07:54:43 localhost kernel: Process scsi_eh_1 (pid: 4733, threadinfo=f3b20000 task=c19460a0)
Oct  7 07:54:43 localhost kernel: Stack: f5716080 f3b21e94 00000286 f3f25800 f715cb30 f3b20000 f5716080 00000282 
Oct  7 07:54:43 localhost kernel:        f8938617 f5716080 c1b29178 f893872e f5716080 00000001 00000000 f715cb30 
Oct  7 07:54:43 localhost kernel:        f5716080 00000000 c1b29178 f5716080 f89389fc f5716080 00000001 00000000 
Oct  7 07:54:43 localhost kernel: Call Trace:
Oct  7 07:54:43 localhost kernel:  [pg0+945399319/1069941760] scsi_next_command+0x19/0x29 [scsi_mod]
Oct  7 07:54:43 localhost kernel:  [pg0+945399598/1069941760] scsi_end_request+0xc5/0xe2 [scsi_mod]
Oct  7 07:54:43 localhost kernel:  [pg0+945400316/1069941760] scsi_io_completion+0x114/0x4b3 [scsi_mod]
Oct  7 07:54:43 localhost kernel:  [__call_console_drivers+85/87] __call_console_drivers+0x55/0x57
Oct  7 07:54:43 localhost kernel:  [pg0+949784839/1069941760] rw_intr+0x67/0x1b9 [sr_mod]
Oct  7 07:54:43 localhost kernel:  [pg0+945380620/1069941760] scsi_finish_command+0x85/0xd9 [scsi_mod]
Oct  7 07:54:43 localhost kernel:  [vprintk+267/357] vprintk+0x10b/0x165
Oct  7 07:54:43 localhost kernel:  [pg0+950012992/1069941760] atapi_qc_complete+0x2f/0xac [libata]
Oct  7 07:54:43 localhost kernel:  [printk+23/27] printk+0x17/0x1b
Oct  7 07:54:43 localhost kernel:  [pg0+950001698/1069941760] ata_qc_complete+0x3a/0xc0 [libata]
Oct  7 07:54:43 localhost kernel:  [pg0+950001042/1069941760] ata_qc_timeout+0x97/0x144 [libata]
Oct  7 07:54:43 localhost kernel:  [pg0+950009601/1069941760] ata_scsi_error+0x1a/0x2f [libata]
Oct  7 07:54:43 localhost kernel:  [pg0+950009575/1069941760] ata_scsi_error+0x0/0x2f [libata]
Oct  7 07:54:43 localhost kernel:  [pg0+945396578/1069941760] scsi_error_handler+0xb7/0x169 [scsi_mod]
Oct  7 07:54:43 localhost kernel:  [pg0+945396395/1069941760] scsi_error_handler+0x0/0x169 [scsi_mod]
Oct  7 07:54:43 localhost kernel:  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Oct  7 07:54:43 localhost kernel: Code: 24 83 c4 10 5b 5e 5f 5d e9 18 5c 8d c7 e8 8c 7f 95 c7 eb cb 89 47 10 89 58 04 31 ff 89 53 04 89 5d 0c eb ab e8 75 7f 95 c7 eb 96 <0f> 0b 24 01 23 dc 93 f8 e9 70 ff ff ff 57 56 53 83 ec 18 8b 5c 
Oct  7 07:54:43 localhost kernel:  <6>note: scsi_eh_1[4733] exited with preempt_count 1:confused:

---

### Post by pm124493 on 2005-10-08
After reading the status reports on SATA, I have come to the conclusion that Linux in not ready for prime time. When a company produces a product it ensures drivers are available for the market and the market is Windows. Linux is not where they are going to make a profit.
If you use Linux you need to ensure your system is two or more years old to be safe and have the proper support. This is not Linux fault. Commerical developers are in it for the money. 
I am concerned that the answer to new interfaces seems to be emulate it with  SCSI. Native IDE drivers do not exist. 
Chao:(

---

