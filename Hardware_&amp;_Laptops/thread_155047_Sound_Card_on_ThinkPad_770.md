---
title: "Sound Card on ThinkPad 770"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by Video Toaster on 2006-04-04
Hi everyone,

Two days ago I installed Ubuntu on an old ThinkPad 770.  Everything now seems to be working except for sound (haven't tried infrared yet, but I suspect that doesn't work either).  I've searched all over the Internet and have found quite a few pages, but my level of understanding of Linux doesn't seem to match the information and it seems everything I try just makes the problem worse.  It also seems that many of the pages I've found are for different versions of the Linux kernel or something, as they refer to modules.conf, a configuration file I do not have on this computer.

I did manage to get ALSA to recognize the sound card ONCE, but I don't know how.  Also, even though it was recognized and I was able to use the Volume Control, no sound was ever played.  System sounds didn't work and Rhythmbox simply stayed at 0:00 when I tried to play a CD.  Right now it is not recognized at all - the card appears in Device Manager with the correct name, but it does not show up as a sound card.  ALSA doesn't recognize it at all.

As of right now, I have "snd-cs4236" in /etc/modules and the followoing in /etc/modprobe.d/sound:

```
alias char-major-116 snd
alias snd-card-0 snd-card-cs4236
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
options snd snd_major=116 snd_cards_limit=1
options snd-card-cs4236 snd_id=card1 snd_index=0 snd_isapnp=0 snd_port=0x530 snd_cport=0x538 snd_dma1=1 snd_dma2=3 snd_irq=5
```

However, I have no idea if ANY of that is correct (including the kernel module), as web sites contradicted each other.

Running dmesg after bootup gave me the following:
```
[14142.951688] cs: IO port probe 0xc00-0xcf7: clean.
[14142.953861] cs: IO port probe 0xa00-0xaff: clean.
[14142.954707] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[14142.960727] pcmcia: registering new device pcmcia1.0
[14142.975024] ts: Compaq touchscreen protocol output
[14144.441889] airo:  Probing for PCI adapters
[14144.444942] airo:  Finished probing for PCI adapters
[14145.650562] airo: cmd= 111
[14145.650844] airo: status= 7f11
[14145.651089] airo: Rsp0= 2
[14145.651334] airo: Rsp1= 0
[14145.651563] airo: Rsp2= 0
[14145.651790] airo: Doing fast bap_reads
[14145.857364] airo: MAC enabled eth0 0:d:65:ca:40:aa
[14145.858295] eth0: index 0x05: Vcc 5.0, Vpp 5.0, irq 3, io 0x0100-0x013f
[14146.231619] Setting key 0
[14147.899940] lp0: using parport0 (interrupt-driven).
[14148.255916] snd: Unknown parameter `snd_major'
[14148.279262] snd_timer: Unknown symbol snd_info_register
[14148.279892] snd_timer: Unknown symbol snd_info_create_module_entry
[14148.280442] snd_timer: Unknown symbol snd_info_free_entry
[14148.281114] snd_timer: Unknown symbol snd_iprintf
[14148.281746] snd_timer: Unknown symbol snd_ecards_limit
[14148.282386] snd_timer: Unknown symbol snd_oss_info_register
[14148.282864] snd_timer: Unknown symbol snd_unregister_device
[14148.283336] snd_timer: Unknown symbol snd_device_new
[14148.284489] snd_timer: Unknown symbol snd_info_unregister
[14148.284969] snd_timer: Unknown symbol snd_register_device
[14148.442783] snd: Unknown parameter `snd_major'
[14148.450042] snd_timer: Unknown symbol snd_info_register
[14148.450673] snd_timer: Unknown symbol snd_info_create_module_entry
[14148.451225] snd_timer: Unknown symbol snd_info_free_entry
[14148.451904] snd_timer: Unknown symbol snd_iprintf
[14148.452540] snd_timer: Unknown symbol snd_ecards_limit
[14148.453180] snd_timer: Unknown symbol snd_oss_info_register
[14148.453658] snd_timer: Unknown symbol snd_unregister_device
[14148.454131] snd_timer: Unknown symbol snd_device_new
[14148.455284] snd_timer: Unknown symbol snd_info_unregister
[14148.455763] snd_timer: Unknown symbol snd_register_device
[14148.495382] snd_pcm: Unknown symbol snd_info_register
[14148.496022] snd_pcm: Unknown symbol snd_info_create_module_entry
[14148.496529] snd_pcm: Unknown symbol snd_timer_notify
[14148.497116] snd_pcm: Unknown symbol snd_timer_interrupt
[14148.497594] snd_pcm: Unknown symbol snd_info_free_entry
[14148.498250] snd_pcm: Unknown symbol snd_info_get_str
[14148.499517] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[14148.499974] snd_pcm: Unknown symbol snd_card_file_add
[14148.500508] snd_pcm: Unknown symbol snd_iprintf
[14148.501034] snd_pcm: Unknown symbol snd_major
[14148.502140] snd_pcm: Unknown symbol snd_unregister_device
[14148.502755] snd_pcm: Unknown symbol snd_timer_new
[14148.503212] snd_pcm: Unknown symbol snd_device_new
[14148.504014] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[14148.504925] snd_pcm: Unknown symbol snd_info_create_card_entry
[14148.505383] snd_pcm: Unknown symbol snd_power_wait
[14148.506165] snd_pcm: Unknown symbol snd_device_free
[14148.506957] snd_pcm: Unknown symbol snd_card_file_remove
[14148.507779] snd_pcm: Unknown symbol snd_info_unregister
[14148.508266] snd_pcm: Unknown symbol snd_device_register
[14148.508743] snd_pcm: Unknown symbol snd_register_device
[14148.509201] snd_pcm: Unknown symbol snd_info_get_line
[14148.690336] snd_cs4231_lib: Unknown symbol snd_ctl_add
[14148.690833] snd_cs4231_lib: Unknown symbol snd_pcm_new
[14148.691308] snd_cs4231_lib: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[14148.691794] snd_cs4231_lib: Unknown symbol snd_timer_interrupt
[14148.692316] snd_cs4231_lib: Unknown symbol snd_pcm_set_sync
[14148.692795] snd_cs4231_lib: Unknown symbol snd_dma_pointer
[14148.693253] snd_cs4231_lib: Unknown symbol snd_ctl_new1
[14148.693763] snd_cs4231_lib: Unknown symbol snd_pcm_lib_malloc_pages
[14148.694238] snd_cs4231_lib: Unknown symbol snd_pcm_lib_ioctl
[14148.694711] snd_cs4231_lib: Unknown symbol release_and_free_resource
[14148.695171] snd_cs4231_lib: Unknown symbol snd_dma_disable
[14148.695653] snd_cs4231_lib: Unknown symbol snd_pcm_lib_free_pages
[14148.696114] snd_cs4231_lib: Unknown symbol snd_card_set_generic_pm_callback
[14148.696595] snd_cs4231_lib: Unknown symbol snd_pcm_set_ops
[14148.697066] snd_cs4231_lib: Unknown symbol snd_timer_new
[14148.697543] snd_cs4231_lib: Unknown symbol snd_pcm_hw_constraint_list
[14148.698004] snd_cs4231_lib: Unknown symbol snd_device_new
[14148.698499] snd_cs4231_lib: Unknown symbol snd_pcm_suspend_all
[14148.699110] snd_cs4231_lib: Unknown symbol snd_pcm_lib_preallocate_free_for_all
[14148.699593] snd_cs4231_lib: Unknown symbol snd_device_free
[14148.700049] snd_cs4231_lib: Unknown symbol snd_pcm_period_elapsed
[14148.700885] snd_cs4231_lib: Unknown symbol snd_dma_program
[14148.745862] NET: Registered protocol family 17
[14148.775526] snd_seq_device: Unknown symbol snd_info_register
[14148.776004] snd_seq_device: Unknown symbol snd_info_create_module_entry
[14148.776505] snd_seq_device: Unknown symbol snd_info_free_entry
[14148.776986] snd_seq_device: Unknown symbol snd_seq_root
[14148.777547] snd_seq_device: Unknown symbol snd_iprintf
[14148.778134] snd_seq_device: Unknown symbol snd_device_new
[14148.778639] snd_seq_device: Unknown symbol snd_info_unregister
[14148.812087] snd_rawmidi: Unknown symbol snd_info_register
[14148.812727] snd_rawmidi: Unknown symbol snd_seq_device_new
[14148.813254] snd_rawmidi: Unknown symbol snd_info_free_entry
[14148.813828] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[14148.814317] snd_rawmidi: Unknown symbol snd_register_oss_device
[14148.814843] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[14148.815300] snd_rawmidi: Unknown symbol snd_card_file_add
[14148.815844] snd_rawmidi: Unknown symbol snd_iprintf
[14148.816327] snd_rawmidi: Unknown symbol snd_major
[14148.817056] snd_rawmidi: Unknown symbol snd_oss_info_register
[14148.817537] snd_rawmidi: Unknown symbol snd_unregister_device
[14148.818130] snd_rawmidi: Unknown symbol snd_device_new
[14148.818623] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[14148.819295] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[14148.819842] snd_rawmidi: Unknown symbol snd_device_free
[14148.820297] snd_rawmidi: Unknown symbol snd_card_file_remove
[14148.820820] snd_rawmidi: Unknown symbol snd_info_unregister
[14148.821277] snd_rawmidi: Unknown symbol snd_device_register
[14148.821753] snd_rawmidi: Unknown symbol snd_register_device
[14148.848594] snd_mpu401_uart: Unknown symbol snd_rawmidi_receive
[14148.849292] snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_ack
[14148.849794] snd_mpu401_uart: Unknown symbol release_and_free_resource
[14148.850257] snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_peek
[14148.850765] snd_mpu401_uart: Unknown symbol snd_rawmidi_new
[14148.851385] snd_mpu401_uart: Unknown symbol snd_rawmidi_set_ops
[14148.851971] snd_mpu401_uart: Unknown symbol snd_device_free
[14148.862884] snd_cs4236_lib: Unknown symbol snd_cs4231_info_single
[14148.863398] snd_cs4236_lib: Unknown symbol snd_ctl_add
[14148.863872] snd_cs4236_lib: Unknown symbol snd_cs4231_put_single
[14148.864353] snd_cs4236_lib: Unknown symbol snd_ctl_new1
[14148.864811] snd_cs4236_lib: Unknown symbol snd_cs4231_create
[14148.865265] snd_cs4236_lib: Unknown symbol snd_cs4236_ext_out
[14148.865758] snd_cs4236_lib: Unknown symbol snd_cs4231_mce_up
[14148.866219] snd_cs4236_lib: Unknown symbol snd_cs4231_chip_id
[14148.866697] snd_cs4236_lib: Unknown symbol snd_cs4231_mce_down
[14148.867155] snd_cs4236_lib: Unknown symbol snd_cs4231_out
[14148.867646] snd_cs4236_lib: Unknown symbol snd_cs4231_get_double
[14148.868105] snd_cs4236_lib: Unknown symbol snd_cs4236_ext_in
[14148.868583] snd_cs4236_lib: Unknown symbol snd_cs4231_in
[14148.869041] snd_cs4236_lib: Unknown symbol snd_cs4231_get_single
[14148.869646] snd_cs4236_lib: Unknown symbol snd_cs4231_put_double
[14148.870105] snd_cs4236_lib: Unknown symbol snd_cs4231_pcm
[14148.870583] snd_cs4236_lib: Unknown symbol snd_device_free
[14148.871042] snd_cs4236_lib: Unknown symbol snd_pcm_hw_constraint_ratnums
[14148.871523] snd_cs4236_lib: Unknown symbol snd_cs4231_info_double
[14148.899840] snd_hwdep: Unknown symbol snd_info_register
[14148.900466] snd_hwdep: Unknown symbol snd_info_create_module_entry
[14148.900948] snd_hwdep: Unknown symbol snd_info_free_entry
[14148.901508] snd_hwdep: Unknown symbol snd_unregister_oss_device
[14148.901993] snd_hwdep: Unknown symbol snd_register_oss_device
[14148.902485] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[14148.902943] snd_hwdep: Unknown symbol snd_card_file_add
[14148.903431] snd_hwdep: Unknown symbol snd_iprintf
[14148.903900] snd_hwdep: Unknown symbol snd_major
[14148.904619] snd_hwdep: Unknown symbol snd_unregister_device
[14148.905090] snd_hwdep: Unknown symbol snd_device_new
[14148.905579] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[14148.906186] snd_hwdep: Unknown symbol snd_card_file_remove
[14148.906670] snd_hwdep: Unknown symbol snd_info_unregister
[14148.907131] snd_hwdep: Unknown symbol snd_register_device
[14148.931820] snd_opl3_lib: Unknown symbol snd_seq_device_new
[14148.932343] snd_opl3_lib: Unknown symbol snd_timer_interrupt
[14148.932868] snd_opl3_lib: Unknown symbol release_and_free_resource
[14148.933358] snd_opl3_lib: Unknown symbol snd_hwdep_new
[14148.933952] snd_opl3_lib: Unknown symbol snd_timer_new
[14148.934432] snd_opl3_lib: Unknown symbol snd_device_new
[14148.935152] snd_opl3_lib: Unknown symbol snd_device_free
[14148.956898] snd_cs4236: Unknown symbol snd_card_register
[14148.957393] snd_cs4236: Unknown symbol snd_card_free
[14148.958057] snd_cs4236: Unknown symbol snd_opl3_create
[14148.958961] snd_cs4236: Unknown symbol snd_card_new
[14148.959604] snd_cs4236: Unknown symbol snd_cs4236_pcm
[14148.960055] snd_cs4236: Unknown symbol release_and_free_resource
[14148.960533] snd_cs4236: Unknown symbol snd_cs4236_mixer
[14148.961072] snd_cs4236: Unknown symbol snd_cs4236_create
[14148.961548] snd_cs4236: Unknown symbol snd_card_set_generic_dev
[14148.962006] snd_cs4236: Unknown symbol snd_card_disconnect
[14148.962848] snd_cs4236: Unknown symbol snd_mpu401_uart_new
[14148.963327] snd_cs4236: Unknown symbol snd_card_free_in_thread
[14148.963811] snd_cs4236: Unknown symbol snd_opl3_hwdep_new
[14148.964495] snd_cs4236: Unknown symbol snd_cs4231_timer
[14149.446037] Adding 200772k swap on /dev/hda5.  Priority:-1 extents:1 across:200772k
[14149.696743] EXT3 FS on hda1, internal journal
[14150.753780] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[14150.753854] md: bitmap version 4.39
[14154.670041] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[14155.924630] NET: Registered protocol family 10
[14155.925899] lo: Disabled Privacy Extensions
[14155.927521] IPv6 over IPv4 tunneling driver
[14156.807670] cdrom: open failed.
[14166.509173] eth0: no IPv6 routers present
[14193.739899] serial8250: too much work for irq4
[14235.159654] IBM machine detected. Enabling interrupts during APM calls.
[14235.161443] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[14237.497835] Non-volatile memory driver v1.2
[14237.553919] input: /usr/sbin/thinkpad-keys as /class/input/input3
[14242.009470] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[14242.009529] hdc: drive_cmd: error=0x04 { AbortedCommand }
[14242.009557] ide: failed opcode was: 0xec
[14242.380841] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[14242.380930] hdc: drive_cmd: error=0x04 { AbortedCommand }
[14242.380959] ide: failed opcode was: 0xec
[14243.572131] Bluetooth: Core ver 2.8
[14243.572173] NET: Registered protocol family 31
[14243.572196] Bluetooth: HCI device and connection manager initialized
[14243.572269] Bluetooth: HCI socket layer initialized
[14243.794329] Bluetooth: L2CAP ver 2.8
[14243.794365] Bluetooth: L2CAP socket layer initialized
[14243.821367] Bluetooth: RFCOMM socket layer initialized
[14243.821547] Bluetooth: RFCOMM TTY layer initialized
[14243.821574] Bluetooth: RFCOMM ver 1.7

```

Sadly, I have no idea what any of that means, either.

Does anyone else here on the forum have any idea what I might be doing wrong?  Thanks in advance!

---

### Post by FarEast on 2006-04-08
Hi;) ,

Please alter the /etc/modprove.d/sound as follows.
Keep other lines as they are.

alias snd-card-0 snd-card-cs4236
[COLOR="Green"]alias snd-card-0 snd-cs4236[/COLOR]

options snd-card-cs4236 snd_id=card1 snd_index=0 snd_isapnp=0 snd_port=0x530 snd_cport=0x538 snd_dma1=1 snd_dma2=3 snd_irq=5

[COLOR="Green"]options snd-cs4236 id=card1 index=0 isapnp=0 port=0x530 cport=0x538 dma1=1 dma2=3 irq=5[/COLOR]

If it is not successful, give a try:
[http://ubuntuforums.org/showthread.php?t=156975](http://ubuntuforums.org/showthread.php?t=156975)

---

### Post by Video Toaster on 2006-04-09
> **FarEast]Hi said:**
> alias snd-card-0 snd-cs4236[/COLOR]

options snd-card-cs4236 snd_id=card1 snd_index=0 snd_isapnp=0 snd_port=0x530 snd_cport=0x538 snd_dma1=1 snd_dma2=3 snd_irq=5

[COLOR="Green"]options snd-cs4236 id=card1 index=0 isapnp=0 port=0x530 cport=0x538 dma1=1 dma2=3 irq=5[/COLOR]

If it is not successful, give a try:
[http://ubuntuforums.org/showthread.php?t=156975](http://ubuntuforums.org/showthread.php?t=156975)
Hey, thanks for the help!  :-)

---

