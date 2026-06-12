---
title: "while using skype my computer hangs up - Thinkpad x230"
date: 2014-01-22
forum: Hardware
---

### Post by shizow on 2014-01-22
I run kubuntu 13.10 with the latest updates on thinkpad x230. in the last 2 weeks my computer hang up 6-8 times. Here i found an error in syslog.
what could it be? it seems like it only hangs up while I use skype video and not all the time, I make a lot of skype calls sometime up to 1 hour, and it breaks just somewhere in the middle

UPDATE: I just read here that it could be only that the X system hangs up when skype hangs up and freezes the whole computer, that sounds reasonable to me
[http://ubuntuforums.org/showthread.php?t=2200305](http://ubuntuforums.org/showthread.php?t=2200305)
UPDATE2: Now the xserver crashed when i watched a youtube video

Jan 21 12:46:13 turnon kernel: [ 4031.812509] BUG: unable to handle kernel paging request at fffff7ffa01f3a68
Jan 21 12:46:13 turnon kernel: [ 4031.812587] IP: [<ffffffff811f8e20>] compat_sys_ioctl+0xb0/0x300
Jan 21 12:46:13 turnon kernel: [ 4031.812650] PGD 0 
Jan 21 12:46:13 turnon kernel: [ 4031.812671] Oops: 0000 [#1] SMP 
Jan 21 12:46:13 turnon kernel: [ 4031.812703] Modules linked in: vmnet(OF) vmw_vsock_vmci_transport vsock vmw_vmci vmmon(OF) parport_pc ppdev joydev arc4 iwldvm mac80211 x86_pkg_temp_thermal i
ntel_powerclamp coretemp kvm uvcvideo bnep videobuf2_vmalloc rfcomm videobuf2_memops btusb videobuf2_core videodev bluetooth microcode snd_hda_codec_hdmi snd_hda_codec_realtek psmouse serio_ra
w snd_hda_intel iwlwifi snd_hda_codec cfg80211 snd_hwdep thinkpad_acpi nvram lpc_ich snd_pcm snd_seq_midi snd_seq_midi_event snd_page_alloc mei_me snd_rawmidi mei binfmt_misc snd_seq snd_seq_d
evice snd_timer snd tpm_tis soundcore mac_hid lp parport ext2 xts gf128mul dm_crypt crct10dif_pclmul i915 crc32_pclmul ghash_clmulni_intel cryptd i2c_algo_bit e1000e ahci drm_kms_helper sdhci_
pci libahci drm sdhci ptp pps_core wmi video
Jan 21 12:46:13 turnon kernel: [ 4031.813711] CPU: 3 PID: 3077 Comm: skype Tainted: GF          O 3.11.0-15-generic #23-Ubuntu
Jan 21 12:46:13 turnon kernel: [ 4031.813775] Hardware name: LENOVO 2324BY9/2324BY9, BIOS G2ET82WW (2.02 ) 09/11/2012
Jan 21 12:46:13 turnon kernel: [ 4031.813828] task: ffff8803b2deddc0 ti: ffff880404986000 task.ti: ffff880404986000
Jan 21 12:46:13 turnon kernel: [ 4031.813880] RIP: 0010:[<ffffffff811f8e20>]  [<ffffffff811f8e20>] compat_sys_ioctl+0xb0/0x300
Jan 21 12:46:13 turnon kernel: [ 4031.813948] RSP: 0018:ffff880404987f40  EFLAGS: 00210282
Jan 21 12:46:13 turnon kernel: [ 4031.813985] RAX: fffff7ffa01f3a20 RBX: 00000000c2c45512 RCX: 0000000000000001
Jan 21 12:46:13 turnon kernel: [ 4031.814033] RDX: 00000000e02fdbd0 RSI: 00000000c2c45512 RDI: ffff880406bcfd00
Jan 21 12:46:13 turnon kernel: [ 4031.814082] RBP: ffff880404987f78 R08: ffff880406bcfd38 R09: 00000000e02fdb98
Jan 21 12:46:13 turnon kernel: [ 4031.814131] R10: 00000000f5a3c430 R11: 0000000000000000 R12: 00000000e02fdbd0
Jan 21 12:46:13 turnon kernel: [ 4031.814184] R13: 0000000000000044 R14: 0000000000000001 R15: ffff880406bcfd00
Jan 21 12:46:13 turnon kernel: [ 4031.814234] FS:  0000000000000000(0000) GS:ffff88041e2c0000(0063) knlGS:00000000e50feb40
Jan 21 12:46:13 turnon kernel: [ 4031.814288] CS:  0010 DS: 002b ES: 002b CR0: 0000000080050033
Jan 21 12:46:13 turnon kernel: [ 4031.814328] CR2: fffff7ffa01f3a68 CR3: 0000000406d92000 CR4: 00000000001407e0
Jan 21 12:46:13 turnon kernel: [ 4031.814376] Stack:
Jan 21 12:46:13 turnon kernel: [ 4031.814391]  0000000000000000 00000001fffffff5 0000000000000044 0000000000000000
Jan 21 12:46:13 turnon kernel: [ 4031.814448]  0000000000000000 0000000000000000 0000000000000000 00000000e02fdb98
Jan 21 12:46:13 turnon kernel: [ 4031.814530]  ffffffff816f8eec 0000000000000000 0000000000000000 0000000000000000
Jan 21 12:46:13 turnon kernel: [ 4031.814623] Call Trace:
Jan 21 12:46:13 turnon kernel: [ 4031.814660]  [<ffffffff816f8eec>] sysenter_dispatch+0x7/0x21
Jan 21 12:46:13 turnon kernel: [ 4031.814720] Code: 87 0e 02 00 00 8d 43 ff 83 f8 01 77 11 49 8b 47 20 0f b7 00 66 25 00 f0 66 3d 00 80 74 3b 49 8b 47 28 48 85 c0 0f 84 aa 00 00 00 <48> 8b 48 
48 48 85 c9 74 1e 4c 89 e2 89 de 4c 89 ff ff d1 3d fd 
Jan 21 12:46:13 turnon kernel: [ 4031.814962] RIP  [<ffffffff811f8e20>] compat_sys_ioctl+0xb0/0x300
Jan 21 12:46:13 turnon kernel: [ 4031.815009]  RSP <ffff880404987f40>
Jan 21 12:46:13 turnon kernel: [ 4031.815034] CR2: fffff7ffa01f3a68
Jan 21 12:46:13 turnon kernel: [ 4031.825018] ---[ end trace fb6815ab432c262e ]---

---

