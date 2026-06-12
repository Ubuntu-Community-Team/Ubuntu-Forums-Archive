---
title: "Natty EXT-4 filesystem errors"
date: 2011-04-22
forum: Hardware
---

### Post by seanlano on 2011-04-22
I am using Natty beta 2 amd64, and for testing purposes I have a link set up to my /home partition (sda6) from my Maverick installation. Whenever I run Transmission (which access files on the separate /home partition) it begins to perform verification on my torrent files. After a few minutes the display changes to a list of error messages at a tty terminal, mentioning something about a filesystem error. This is the output that is shown:

```
[  858.450366] EXT4-fs error (device sda6): ext4_ext_search_left:1248: inode #302149: comm flush-8:0: ix (2144256) != EXT_FIRST_INDEX (0) (depth 1)!
[  858.450379] EXT4-fs (sda6): delayed block allocation failed for inode 302149 at logical offset 2144415 with max blocks 85 with error -5
[  858.450382] EXT4-fs (sda6): This should not happen!! Data will be lost
[  858.450384] 
[  858.451825] EXT4-fs error (device sda6): ext4_ext_search_left:1248: inode #302149: comm flush-8:0: ix (2144256) != EXT_FIRST_INDEX (0) (depth 1)!
[  858.451835] EXT4-fs (sda6): delayed block allocation failed for inode 302149 at logical offset 2144415 with max blocks 85 with error -5
[  858.451839] EXT4-fs (sda6): This should not happen!! Data will be lost
[  858.451840] 
[  858.451875] ------------[ cut here ]------------
[  858.451917] kernel BUG at /build/buildd/linux-2.6.38/fs/ext4/inode.c:2188!
[  858.451964] invalid opcode: 0000 [#1] SMP 
[  858.452002] last sysfs file: /sys/devices/system/cpu/cpu1/cache/index2/shared_cpu_map
[  858.452048] CPU 1 
[  858.452064] Modules linked in: btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs parport_pc ppdev snd_hda_codec_conexant joydev binfmt_misc arc4 rfcomm iwl3945 thinkpad_acpi snd_hda_intel iwlcore sco snd_hda_codec bnep snd_hwdep snd_pcm snd_seq_midi snd_rawmidi l2cap snd_seq_midi_event mac80211 snd_seq i915 btusb snd_timer pcmcia snd_seq_device r852 sm_common nand yenta_socket pcmcia_rsrc nand_ids nand_ecc drm_kms_helper bluetooth psmouse cfg80211 drm pcmcia_core serio_raw snd mtd snd_page_alloc i2c_algo_bit soundcore nvram video lp parport usbhid hid firewire_ohci firewire_core sdhci_pci sdhci crc_itu_t ahci tg3 libahci
[  858.452705] 
[  858.452721] Pid: 1068, comm: flush-8:0 Not tainted 2.6.38-8-generic #42-Ubuntu LENOVO 8932A47/8932A47
[  858.452798] RIP: 0010:[<ffffffff8120264f>]  [<ffffffff8120264f>] ext4_da_block_invalidatepages.clone.39+0x13f/0x150
[  858.452865] RSP: 0018:ffff88006a7299a0  EFLAGS: 00010246
[  858.452898] RAX: 0100000000000024 RBX: 000000000020b8f3 RCX: 000000000000000e
[  858.452939] RDX: 000000000000000e RSI: 000000000000000e RDI: ffffea0000ca10e8
[  858.452980] RBP: ffff88006a729a60 R08: 0000000000000001 R09: 0000000000000001
[  858.453020] R10: ffffea0000ca10f0 R11: ffff8800235319e0 R12: ffff88005eafd7b8
[  858.453060] R13: ffffea00011adf00 R14: ffff88006c782400 R15: 0000000000000000
[  858.453101] FS:  0000000000000000(0000) GS:ffff88007f500000(0000) knlGS:0000000000000000
[  858.453157] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  858.453191] CR2: 00007f47953db751 CR3: 0000000001a03000 CR4: 00000000000006e0
[  858.453232] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  858.453273] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  858.453314] Process flush-8:0 (pid: 1068, threadinfo ffff88006a728000, task ffff88006b410000)
[  858.453361] Stack:
[  858.453377]  0000000000000020 0000000e6a729a00 000000000000000e fffffffb00000000
[  858.453438]  ffffea00011adf00 ffffea00011adf38 ffffea0000eef1f0 ffffea0000eef228
[  858.453501]  ffffea0000f36300 ffffea0000f36338 ffffea0000f27b90 ffffea0000f27bc8
[  858.453565] Call Trace:
[  858.453588]  [<ffffffff81208d3b>] mpage_da_map_and_submit+0x25b/0x440
[  858.453627]  [<ffffffff812097a6>] ext4_da_writepages+0x336/0x630
[  858.453673]  [<ffffffff81117151>] do_writepages+0x21/0x40
[  858.453707]  [<ffffffff8118b5df>] writeback_single_inode+0x9f/0x240
[  858.453744]  [<ffffffff8118b9cb>] writeback_sb_inodes+0xcb/0x160
[  858.453788]  [<ffffffff8118bc1b>] writeback_inodes_wb+0x10b/0x1c0
[  858.453825]  [<ffffffff8118c04e>] wb_writeback+0x37e/0x490
[  858.453868]  [<ffffffff815c2e6f>] ? _raw_spin_lock_irqsave+0x2f/0x40
[  858.453916]  [<ffffffff81074fdb>] ? lock_timer_base.clone.20+0x3b/0x70
[  858.453960]  [<ffffffff8118c381>] wb_do_writeback+0x221/0x230
[  858.453995]  [<ffffffff8118c412>] bdi_writeback_thread+0x82/0x260
[  858.454033]  [<ffffffff8118c390>] ? bdi_writeback_thread+0x0/0x260
[  858.454075]  [<ffffffff810877e6>] kthread+0x96/0xa0
[  858.454106]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[  858.454142]  [<ffffffff81087750>] ? kthread+0x0/0xa0
[  858.454185]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[  858.456314] Code: 85 ff 74 0c 48 8d bd 50 ff ff ff e8 1c 65 f1 ff 4c 39 eb 0f 83 1b ff ff ff 48 81 c4 98 00 00 00 5b 41 5c 41 5d 41 5e 41 5f c9 c3 <0f> 0b 0f 0b 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 89 e5 
[  858.460990] RIP  [<ffffffff8120264f>] ext4_da_block_invalidatepages.clone.39+0x13f/0x150
[  858.461773]  RSP <ffff88006a7299a0>
[  858.527146] ---[ end trace 8e0fb5a5f109d656 ]---
```



I'm not really sure what this means, but it sounds pretty serious. Is this a problem with the Natty kernel? Or is it a hard drive problem? 

After I see the error message I can press Ctrl+Alt+F7 to get back to the graphical environment, but Transmission is permanently frozen and cannot be killed. I also cannot read from the partition at all. I then cannot properly shut down the computer, I have to do a hard reset.


I ran (from single-user mode, with sda6 unmounted) ```
fsck.ext4 /dev/sda6 -c
```to check for bad blocks, but none were found. Fsck reports no problems with the filesystem.

---

### Post by seanlano on 2011-04-23
I managed to get through the check for each of the files in Transmission. But after I left it running for a while it happened again. I guess this would indicate that there is not one specific area of the disk that causes the crash, but it is a more general problem. I also ran Transmission from the Maverick partition and there were no problems at all. So I don't think there is a physical problem with my disk, and it works fine in Maverick, so there must be some software problem in Natty. I'll try re-installing the kernel and see if that helps.

---

### Post by seanlano on 2011-04-23
OK, I just tried running Transmission for a longer time. This time I was using Maverick. I got a similar error: 

```
[  559.913021] EXT4-fs error (device sda6): ext4_ext_search_left: inode #302149: (comm flush-8:0) ix (2403008) != EXT_FIRST_INDEX (0) (depth 1)!
[  559.919960] EXT4-fs (sda6): delayed block allocation failed for inode 302149 at logical offset 2403279 with max blocks 257 with error -5
[  559.919971] This should not happen!!  Data will be lost
[  590.320548] EXT4-fs error (device sda6): ext4_ext_search_left: inode #302149: (comm flush-8:0) ix (2403008) != EXT_FIRST_INDEX (0) (depth 1)!
[  590.326464] EXT4-fs (sda6): delayed block allocation failed for inode 302149 at logical offset 2403023 with max blocks 205 with error -5
[  590.326472] This should not happen!!  Data will be lost
[  620.590474] EXT4-fs error (device sda6): ext4_ext_search_left: inode #302149: (comm flush-8:0) ix (2529487) != EXT_FIRST_INDEX (0) (depth 1)!
[  620.590778] EXT4-fs (sda6): delayed block allocation failed for inode 302149 at logical offset 2529743 with max blocks 84 with error -5
[  620.590790] This should not happen!!  Data will be lost
```

The computer didn't crash in the same way, but it looks like the same problem. So this means then that it isn't a Natty issue. It is definitely something to do with the filesystem on sda6. It looks like the common theme is a problem with inode 302149. I have no idea what that even means.

Does this mean a hardware failure? Should I replace the hard drive? Or does it need re-formatting or something?

---

### Post by RoundSparrow on 2011-06-27
I've hit this same bug in EXT4 on a newly formatted USB 1.5TB Seagate drive.

```

[  924.942217] ------------[ cut here ]------------
[  924.944908] kernel BUG at /build/buildd/linux-2.6.38/fs/ext4/inode.c:2188!
[  924.946319] invalid opcode: 0000 [#1] SMP 
[  924.947714] last sysfs file: /sys/devices/system/cpu/cpu7/cache/index2/shared_cpu_map
[  924.949104] CPU 2 
[  924.949117] Modules linked in: xts gf128mul cryptd aes_x86_64 aes_generic parport_pc ppdev dm_crypt binfmt_misc joydev snd_hda_codec_hdmi snd_hda_codec_idt arc4 rfcomm snd_hda_intel snd_hda_codec snd_hwdep snd_pcm sco iwlagn snd_seq_midi bnep hp_wmi l2cap sparse_keymap snd_rawmidi iwlcore snd_seq_midi_event snd_seq snd_timer snd_seq_device mac80211 snd btusb bluetooth uvcvideo psmouse videodev v4l2_compat_ioctl32 serio_raw xhci_hcd rts_pstor(C) cfg80211 soundcore snd_page_alloc hp_accel lis3lv02d input_polldev lp parport dm_raid45 xor btrfs zlib_deflate libcrc32c usb_storage uas i915 radeon ttm drm_kms_helper drm ahci r8169 libahci i2c_algo_bit video
[  924.959802] 
[  924.961381] Pid: 2009, comm: flush-8:16 Tainted: G         C  2.6.38-8-generic #42-Ubuntu Hewlett-Packard HP Pavilion dv6 Notebook PC/1657
[  924.964714] RIP: 0010:[<ffffffff8120264f>]  [<ffffffff8120264f>] ext4_da_block_invalidatepages.clone.39+0x13f/0x150
[  924.966479] RSP: 0018:ffff8801b9967880  EFLAGS: 00010246
[  924.968230] RAX: 0200000000000024 RBX: 00000000000007ff RCX: 000000000000000e
[  924.969998] RDX: 000000000000000e RSI: 000000000000000e RDI: ffffea000457e8a8
[  924.971761] RBP: ffff8801b9967940 R08: 0000000000000001 R09: 0000000000000001
[  924.973523] R10: ffffea000457e8b0 R11: ffff880067e26f18 R12: ffff880017de0cd8
[  924.975295] R13: ffffea000457b150 R14: ffff8801b9941c00 R15: ffff8801b9967ab0
[  924.977070] FS:  0000000000000000(0000) GS:ffff88009cc80000(0000) knlGS:0000000000000000
[  924.978859] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  924.980634] CR2: 00007fffd503afe0 CR3: 0000000001a03000 CR4: 00000000000406e0
[  924.982429] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  924.984227] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  924.986014] Process flush-8:16 (pid: 2009, threadinfo ffff8801b9966000, task ffff8801a394adc0)
[  924.987820] Stack:
[  924.989612]  ffff880100000020 0000000eb99678e0 000000000000000e ffffffe200000000
[  924.991466]  ffffea000457b150 ffffea000457b188 ffffea000457b1c0 ffffea000457b1f8
[  924.993328]  ffffea000457b230 ffffea000457b268 ffffea000457b2a0 ffffea000457b2d8
[  924.995158] Call Trace:
[  924.996959]  [<ffffffff81208d3b>] mpage_da_map_and_submit+0x25b/0x440
[  924.998785]  [<ffffffff812dfe2d>] ? radix_tree_gang_lookup_tag_slot+0x8d/0xd0
[  925.000631]  [<ffffffff81208f8d>] mpage_add_bh_to_extent+0x6d/0xf0
[  925.002479]  [<ffffffff81209102>] __mpage_da_writepage+0xf2/0x190
[  925.004322]  [<ffffffff8120935b>] write_cache_pages_da+0x1bb/0x2d0
[  925.006149]  [<ffffffff81209786>] ext4_da_writepages+0x316/0x630
[  925.007964]  [<ffffffff81117151>] do_writepages+0x21/0x40
[  925.009771]  [<ffffffff8118b5df>] writeback_single_inode+0x9f/0x240
[  925.011580]  [<ffffffff8118b9cb>] writeback_sb_inodes+0xcb/0x160
[  925.013380]  [<ffffffff8118be54>] wb_writeback+0x184/0x490
[  925.015176]  [<ffffffff815c2e6f>] ? _raw_spin_lock_irqsave+0x2f/0x40
[  925.016979]  [<ffffffff81074fdb>] ? lock_timer_base.clone.20+0x3b/0x70
[  925.018784]  [<ffffffff811166aa>] ? determine_dirtyable_memory+0x1a/0x30
[  925.020596]  [<ffffffff8118c213>] wb_do_writeback+0xb3/0x230
[  925.022406]  [<ffffffff8118c412>] bdi_writeback_thread+0x82/0x260
[  925.024202]  [<ffffffff8118c390>] ? bdi_writeback_thread+0x0/0x260
[  925.025983]  [<ffffffff810877e6>] kthread+0x96/0xa0
[  925.027742]  [<ffffffff8100ce24>] kernel_thread_helper+0x4/0x10
[  925.029493]  [<ffffffff81087750>] ? kthread+0x0/0xa0
[  925.031217]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
[  925.032928] Code: 85 ff 74 0c 48 8d bd 50 ff ff ff e8 1c 65 f1 ff 4c 39 eb 0f 83 1b ff ff ff 48 81 c4 98 00 00 00 5b 41 5c 41 5d 41 5e 41 5f c9 c3 <0f> 0b 0f 0b 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 89 e5 
[  925.036517] RIP  [<ffffffff8120264f>] ext4_da_block_invalidatepages.clone.39+0x13f/0x150
[  925.038256]  RSP <ffff8801b9967880>
[  925.046191] ---[ end trace a3a1d8fb286a727b ]---

```

Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by seanlano on 2011-06-27
I found that it wasn't a Natty-specific issue. Despite my previous comments, it did occur in Lucid too. I'm pretty sure it was because of a slightly corrupted file that Transmission was trying to read. I don't think crashing the entire system is the correct procedure for the kernel to deal with this, but I managed to fix the problem by deleting the affected files (which thankfully I had back-up copies of). 

I ran ```
find / -inum XXXXXX -print
``` to find the file, where XXXXXX was 302149 in my case. In the error report you posted, I think the inode number is actually above the ```
[  924.942217] ------------[ cut here ]------------
``` part. In my case it looked like this: ```
[  858.450366] EXT4-fs error (device sda6): ext4_ext_search_left:1248: inode #302149: comm flush-8:0: ix (2144256) != EXT_FIRST_INDEX (0) (depth 1)!
[  858.450379] EXT4-fs (sda6): delayed block allocation failed for inode 302149 at logical offset 2144415 with max blocks 85 with error -5
[  858.450382] EXT4-fs (sda6): This should not happen!! Data will be lost
[  858.450384] 
[  858.451825] EXT4-fs error (device sda6): ext4_ext_search_left:1248: inode #302149: comm flush-8:0: ix (2144256) != EXT_FIRST_INDEX (0) (depth 1)!
[  858.451835] EXT4-fs (sda6): delayed block allocation failed for inode 302149 at logical offset 2144415 with max blocks 85 with error -5
[  858.451839] EXT4-fs (sda6): This should not happen!! Data will be lost
[  858.451840] 
[  858.451875] ------------[ cut here ]------------
```

Hopefully you can find the file, and if you're lucky it won't be anything important. I'm not sure what to do if you can't just delete it. Try copying it first I guess, although that will probably just cause the crash again. 

Hope this help a bit.

---

