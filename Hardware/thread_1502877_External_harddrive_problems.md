---
title: "External harddrive problems"
date: 2010-06-06
forum: Hardware
---

### Post by tbresson on 2010-06-06
Hi.

I have an external USB harddrive. I havn't had any problems with the previous Ubuntu version but I don't know if it's related to that.

When I leave my PC on at night I usually find the OS have forgotten about the device. It's not in Gparted. I have mounted the harddrive to a folder but when I click on it it shows an empty folder.

The mount is done via /etc/fstab 

If I reboot it says the device is not yet ready and asks if I want to wait, continue or do something manually.

I've found out that I turn off the harddrive and on again it becomes available (under a new device name, /sdd instead og /sdc). And I can access the files and folders on the drive.

If I reboot and turn off the device and on again before the boot is complete everything is back to normal.

Any idea on what's going on?

---

### Post by dileepm on 2010-06-06
Hi,

I am not sure if your problem is for any specific reason. But try this procedure in general

[http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html](http://starksolutions.blogspot.com/2010/05/linux-auto-mount-partitions.html)

I assume that external hard drives are considered removable drives (like flash/pen drives)

---

### Post by tbresson on 2010-06-10
I'm not sure that's the issue. But thanks for the reply and the link :)

It's there some kind of system log that explains why the connection to the harddrive was dropped or something like that?

---

### Post by tbresson on 2010-06-15
Let's say I loose the connection to the drive.
Is there any commands or anything like that I can write to check out some sort of logs that'll help find out what happend?

---

### Post by tbresson on 2010-06-22
dmesg said this: (added to main topic)

```
[32243.112055] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[32258.224041] usb 1-1: device descriptor read/64, error -110
[32273.440026] usb 1-1: device descriptor read/64, error -110
[32273.656030] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[32288.768027] usb 1-1: device descriptor read/64, error -110
[32303.984042] usb 1-1: device descriptor read/64, error -110
[32304.200049] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[32309.220081] usb 1-1: device descriptor read/8, error -110
[32314.340096] usb 1-1: device descriptor read/8, error -110
[32314.556032] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[32319.576086] usb 1-1: device descriptor read/8, error -110
[32324.696102] usb 1-1: device descriptor read/8, error -110
[32324.800054] usb 1-1: USB disconnect, address 2
[32324.800381] sd 4:0:0:0: Device offlined - not ready after error recovery
[32324.800598] sd 4:0:0:0: [sdc] Unhandled error code
[32324.800602] sd 4:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[32324.800607] sd 4:0:0:0: [sdc] CDB: Read(10): 28 00 19 54 ab df 00 00 20 00
[32324.800618] end_request: I/O error, dev sdc, sector 424979423
[32325.224727] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #12951553 offset 0
[32325.225217] EXT3-fs error (device sdc1): ext3_get_inode_loc: unable to read inode block - inode=13934618, block=55738370
[32325.225455] ------------[ cut here ]------------
[32325.225465] WARNING: at /build/buildd/linux-2.6.32/fs/buffer.c:1159 mark_buffer_dirty+0x70/0x90()
[32325.225468] Hardware name:  
[32325.225470] Modules linked in: binfmt_misc fbcon tileblit font bitblit softcursor vga16fb vgastate snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq reiserfs radeon snd_timer snd_seq_device ttm drm_kms_helper ppdev snd drm i2c_algo_bit intel_agp parport_pc soundcore snd_page_alloc shpchp agpgart lp parport usbhid hid usb_storage floppy r8169 mii
[32325.225514] Pid: 1590, comm: java Not tainted 2.6.32-22-generic #36-Ubuntu
[32325.225517] Call Trace:
[32325.225526]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
[32325.225530]  [<c022c450>] ? mark_buffer_dirty+0x70/0x90
[32325.225534]  [<c022c450>] ? mark_buffer_dirty+0x70/0x90
[32325.225538]  [<c014c41a>] warn_slowpath_null+0x1a/0x20
[32325.225541]  [<c022c450>] mark_buffer_dirty+0x70/0x90
[32325.225547]  [<c026fd5a>] T.1002+0x4a/0x70
[32325.225551]  [<c026fdeb>] ext3_handle_error+0x6b/0xb0
[32325.225558]  [<c0588f92>] ? printk+0x1d/0x23
[32325.225563]  [<c0270196>] ext3_error+0x56/0x60
[32325.225567]  [<c026752b>] __ext3_get_inode_loc+0x28b/0x2e0
[32325.225571]  [<c0267999>] ext3_get_inode_loc+0x19/0x20
[32325.225575]  [<c02679ca>] ext3_reserve_inode_write+0x2a/0x90
[32325.225579]  [<c0267a5b>] ext3_mark_inode_dirty+0x2b/0x50
[32325.225583]  [<c0267bae>] ext3_dirty_inode+0x4e/0x80
[32325.225589]  [<c0225fd1>] __mark_inode_dirty+0x31/0x180
[32325.225594]  [<c021bf0a>] touch_atime+0xea/0x130
[32325.225598]  [<c0216be9>] vfs_readdir+0xa9/0xb0
[32325.225602]  [<c02168a0>] ? filldir64+0x0/0xf0
[32325.225605]  [<c0216c59>] sys_getdents64+0x69/0xc0
[32325.225610]  [<c01033ec>] syscall_call+0x7/0xb
[32325.225614] ---[ end trace a5c5b40e247fdaa7 ]---
[32325.225626] EXT3-fs error (device sdc1) in ext3_reserve_inode_write: IO failure
[32325.227433] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[32325.318452] EXT3-fs error (device sdc1): ext3_get_inode_loc: unable to read inode block - inode=13934911, block=55738379
[32325.318707] EXT3-fs error (device sdc1) in ext3_reserve_inode_write: IO failure
[32325.319620] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[32325.343613] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934913 offset 0
[32325.412140] usb 1-1: new high speed USB device using ehci_hcd and address 4
[32325.815116] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[32325.856653] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934913 offset 0
[32331.000086] journal_bmap: journal block not found at offset 994 on sdc1
[32331.000094] Aborting journal on device sdc1.
[32340.524048] usb 1-1: device descriptor read/64, error -110
[32345.557665] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934804 offset 0
[32345.589564] ext3_abort called.
[32345.589573] EXT3-fs error (device sdc1): ext3_journal_start_sb: Detected aborted journal
[32345.589577] Remounting filesystem read-only
[32345.630706] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934804 offset 0
[32355.740028] usb 1-1: device descriptor read/64, error -110
[32355.956029] usb 1-1: new high speed USB device using ehci_hcd and address 5
[32371.068032] usb 1-1: device descriptor read/64, error -110
[32386.284025] usb 1-1: device descriptor read/64, error -110
[32386.500051] usb 1-1: new high speed USB device using ehci_hcd and address 6
[32391.521878] usb 1-1: device descriptor read/8, error -110
[32396.640128] usb 1-1: device descriptor read/8, error -110
[32396.856027] usb 1-1: new high speed USB device using ehci_hcd and address 7
[32401.876121] usb 1-1: device descriptor read/8, error -110
[32406.996135] usb 1-1: device descriptor read/8, error -110
[32407.100038] hub 1-0:1.0: unable to enumerate USB device on port 1
[32407.560022] usb 2-1: new full speed USB device using uhci_hcd and address 3
[32421.239203] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[32421.239514] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[32421.239627] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[32422.672026] usb 2-1: device descriptor read/64, error -110
[32437.944026] usb 2-1: device descriptor read/64, error -110
[32438.160031] usb 2-1: new full speed USB device using uhci_hcd and address 4
[32453.272027] usb 2-1: device descriptor read/64, error -110
[32468.488024] usb 2-1: device descriptor read/64, error -110
[32468.704030] usb 2-1: new full speed USB device using uhci_hcd and address 5
[32473.725150] usb 2-1: device descriptor read/8, error -110
[32478.845164] usb 2-1: device descriptor read/8, error -110
[32479.060027] usb 2-1: new full speed USB device using uhci_hcd and address 6
[32484.081161] usb 2-1: device descriptor read/8, error -110
[32489.201173] usb 2-1: device descriptor read/8, error -110
[32489.304276] hub 2-0:1.0: unable to enumerate USB device on port 1
[33500.533710] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[38686.495856] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[39213.570951] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[51241.697846] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[51241.738822] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[51241.751671] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[51241.766956] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #13934597 offset 0
[51255.552032] usb 1-1: new high speed USB device using ehci_hcd and address 8
[51255.686038] usb 1-1: configuration #1 chosen from 1 choice
[51255.687489] scsi5 : SCSI emulation for USB Mass Storage devices
[51255.687704] usb-storage: device found at 8
[51255.687707] usb-storage: waiting for device to settle before scanning
[51260.684348] usb-storage: device scan complete
[51260.684825] scsi 5:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[51260.687953] sd 5:0:0:0: Attached scsi generic sg3 type 0
[51260.690804] sd 5:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[51260.691170] sd 5:0:0:0: [sdd] Write Protect is off
[51260.691174] sd 5:0:0:0: [sdd] Mode Sense: 10 00 00 00
[51260.691177] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[51260.693052] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[51260.693061]  sdd: sdd1
[51260.701670] sd 5:0:0:0: [sdd] Assuming drive cache: write through
[51260.701677] sd 5:0:0:0: [sdd] Attached SCSI disk
[51261.649287] kjournald starting.  Commit interval 5 seconds
[51261.649990] EXT3 FS on sdd1, internal journal
[51261.649994] EXT3-fs: recovery complete.
[51261.650486] EXT3-fs: mounted filesystem with ordered data mode.
[51262.678441] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[51262.678620] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0

```

---

### Post by tbresson on 2010-06-24
*bump*

---

### Post by tbresson on 2010-07-06
Just in case someone casually googles this and wonders if there was any solution to it. There isn't. I havn't found any reason for this happening. I enclined to think it's USB related but I havn't tried opening the external harddrive and putting it in my PC.

---

### Post by twelve17 on 2011-08-04
Hi tbresson,

I am having the same issue under Ubuntu 10.10, kernel 2.6.35-30-generic.  Like you, even if I reboot the computer, it will not recognize the drive.  I have to turn off, unplug and re-plug in the drive in order for it to be recognized again.


What kind of enclosure/drive do you have?  I have a Samsung 1TB Eco-green  drive in a [OWC Mercury Elite-AL]("http://eshop.macsales.com/item/Other%20World%20Computing/MEFW934FWU2K/") enclosure.

Alex

---

### Post by tbresson on 2011-08-04
Mine is: Verbatim SmartDisk Extern Hard Disk 3,5´´ - 500 GB  USB 2.0

I can't remember if I ever solved it but I'm not running my Ubuntu server anymore. I switched to a NAS instead. Funny enough that too seemed to miss the connection to the device aswell, so it might be drive related. 

I tried a diffrent poweroutlet and I reformated the drive and it's been working since.

Hope it helps.

---

### Post by tiocaio on 2011-11-13
I'm with the same problem. I'm using Ubuntu 11.10

---

### Post by yabrembre on 2013-02-17
Hello everyone,

I was having the same problem with an Ubuntu 12.04 and an IceBox USB device.

After googling for a while I suspected it could be a kind of timeout for the usb device so I run this command:

```
while true
do
  touch /USB_disk/.prueba.tmp
  rm /USB_disk/.prueba.tmp
  sleep 300
done
```

After a whole weekend without any problem I add this line to my crontab:

```
*/5 * * * * touch /USB_disk/.prueba.tmp && rm /USB_disk/.prueba.tmp
```

And that's it! It is not very elegant but works fine for me.

Cheers!

---

### Post by tbresson on 2013-02-17
Hi. This is a really old post but I guess since you posted some people are still having these problems. I still own the device but I've had problems with it on both Linux, Windows and my NAS. 

If it's some sort of timeout which I agree it sounds like I'm glad you found a solution for your OS. Personally I'm just gonna try and find a different brand. The amount of space has increased a lot since then anyway :)

---

