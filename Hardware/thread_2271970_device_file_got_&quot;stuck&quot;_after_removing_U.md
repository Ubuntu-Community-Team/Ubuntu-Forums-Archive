---
title: "device file got &quot;stuck&quot; after removing USB drive"
date: 2015-04-03
forum: Hardware
---

### Post by stlu on 2015-04-03
Using Ubuntu 12.04 LTS.

What happened:  I removed a USB hard drive that used to be /dev/sdc.  I then connected a new drive, that was assigned /dev/sdc.  But now, I cannot mount the partition in the new drive.

Even when that drive is removed, the file /dev/sdc1 still exists.

This feels like something got "stuck" and the kernel still thinks that the original drive is connected?

I imagine a reboot will fix this, otherwise I will post more later.

```
(from dmesg)

[1297108.444587] ------------[ cut here ]------------
[1297108.444603] WARNING: at /build/buildd/linux-3.2.0/fs/sysfs/dir.c:481 sysfs_
add_one+0xb3/0xf0()
[1297108.444609] Hardware name: eM355
[1297108.444613] sysfs: cannot create duplicate filename '/dev/block/8:33'
[1297108.444618] Modules linked in: bnep rfcomm bluetooth parport_pc ppdev snd_h
da_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm uvcvideo snd_seq_
midi arc4 nfsd snd_rawmidi videodev ath9k joydev snd_seq_midi_event binfmt_misc 
nfs mac80211 snd_seq lockd fscache auth_rpcgss ath9k_common nfs_acl ath9k_hw snd
_timer acer_wmi snd_seq_device i915 snd psmouse sparse_keymap sunrpc ath drm_kms
_helper soundcore serio_raw mac_hid cfg80211 drm snd_page_alloc i2c_algo_bit vid
eo wmi lp parport atl1c usb_storage
[1297108.444712] Pid: 26601, comm: kworker/u:1 Tainted: G        W    3.2.0-76-g
eneric #111-Ubuntu
[1297108.444718] Call Trace:
[1297108.444730]  [<c104b992>] warn_slowpath_common+0x72/0xa0
[1297108.444740]  [<c1199003>] ? sysfs_add_one+0xb3/0xf0
[1297108.444747]  [<c1199003>] ? sysfs_add_one+0xb3/0xf0
[1297108.444755]  [<c104ba63>] warn_slowpath_fmt+0x33/0x40
[1297108.444763]  [<c1199003>] sysfs_add_one+0xb3/0xf0
[1297108.444772]  [<c119984d>] sysfs_do_create_link+0xed/0x1d0
[1297108.444781]  [<c1199947>] sysfs_create_link+0x17/0x20
[1297108.444790]  [<c1368c2e>] device_add+0x17e/0x380
[1297108.444800]  [<c1371c39>] ? device_pm_init+0x49/0x70
[1297108.444808]  [<c119005a>] add_partition+0x28a/0x3f0
[1297108.444816]  [<c11903ee>] rescan_partitions+0x22e/0x320
[1297108.444826]  [<c1167367>] __blkdev_get+0x327/0x400
[1297108.444834]  [<c1167487>] blkdev_get+0x47/0x180
[1297108.444841]  [<c13677c4>] ? put_device+0x14/0x20
[1297108.444850]  [<c1290e23>] register_disk+0x143/0x160
[1297108.444859]  [<c128ff12>] ? blk_register_region+0x32/0x40
[1297108.444867]  [<c128f6c0>] ? disk_map_sector_rcu+0xc0/0xc0
[1297108.444875]  [<c1290ee7>] add_disk+0xa7/0x210
[1297108.444883]  [<c128f6c0>] ? disk_map_sector_rcu+0xc0/0xc0
[1297108.444890]  [<c128fd40>] ? get_disk+0xc0/0xc0
[1297108.444900]  [<c13a0f9f>] sd_probe_async+0xff/0x1b0
[1297108.444908]  [<c1027908>] ? default_spin_lock_flags+0x8/0x10
[1297108.444918]  [<c1071f19>] async_run_entry_fn+0x69/0x170
[1297108.444927]  [<c1065a70>] process_one_work+0x120/0x3a0
[1297108.444936]  [<c105aa88>] ? mod_timer+0x118/0x280
[1297108.444944]  [<c10666c4>] worker_thread+0x124/0x2d0
[1297108.444953]  [<c10665a0>] ? manage_workers.isra.29+0x110/0x110
[1297108.444961]  [<c106a52d>] kthread+0x6d/0x80
[1297108.444969]  [<c106a4c0>] ? flush_kthread_worker+0x80/0x80
[1297108.444978]  [<c158477e>] kernel_thread_helper+0x6/0x10
[1297108.444984] ---[ end trace a252b94df4b812b8 ]---
[1297108.445000]  sdc: p1 could not be added: 17

```

---

### Post by Bashing-om on 2015-04-03
stlu; Hello;

What results re-connecting the original drive, and in terminal attempting to UN-mount it ?
```

sudo umount /dev/sdc1

```
(might have to look for the assigned mount point if that is ineffective)
failing to UN-mount ; what returns :
Might get some useful information to see what the system thinks is mounted:
```

mount
cat /proc/mounts

```
Look for a 'lock' :
```

fuser -m /dev/sdc1

```
For an instance, to find out which process is keeping the device busy.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

