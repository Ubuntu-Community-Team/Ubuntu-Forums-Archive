---
title: "Kernel oops after reboot"
date: 2016-01-30
forum: Hardware
---

### Post by DigiAngel on 2016-01-30
So this is interesting...box has been running fine and after a reboot a php cron job is now dying:

cronjob
```
Cron <root@gateway>   [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime)
```

Kernel oops:
```
Jan 30 10:39:02 gateway kernel: [ 8832.434898] BUG: unable to handle kernel NULL pointer dereference at 00000011
Jan 30 10:39:02 gateway kernel: [ 8832.436004] IP: [<c11cca2a>] show_map_vma+0x3a/0x280
Jan 30 10:39:02 gateway kernel: [ 8832.436004] *pdpt = 000000003314f001 *pde = 0000000000000000 
Jan 30 10:39:02 gateway kernel: [ 8832.436004] Oops: 0000 [#5] SMP 
Jan 30 10:39:02 gateway kernel: [ 8832.436004] Modules linked in: nfnetlink_log bluetooth nfnetlink_queue nfnetlink xt_iprange xt_mark xt_NFQUEUE ipt_MASQUERADE xt_REDIRECT ipt_REJECT xt_helper xt_conntrack ts_bm xt_string xt_LOG iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack iptable_filter xfrm_user xfrm4_tunnel tunnel4 ipcomp xfrm_ipcomp esp4 ah4 af_key xfrm_algo xt_TCPMSS xt_tcpmss xt_tcpudp iptable_mangle ip_tables x_tables pppoe pppox xfs libcrc32c adm1021 nouveau b43 snd_hda_codec_realtek snd_hda_intel mxm_wmi snd_hda_codec wmi bcma ttm coretemp snd_hwdep mac80211 snd_pcm kvm_intel drm_kms_helper hid_generic hid_appleir snd_page_alloc snd_seq_midi drm kvm applesmc snd_seq_midi_event snd_rawmidi cfg80211 input_polldev i2c_algo_bit snd_seq usbhid ssb_hcd snd_seq_device snd_timer firewire_sbp2 asix hid snd usbnet isight_firmware mii lpc_ich soundcore shpchp apple_bl video mac_hid lp parport firewire_ohci firewire_core ssb sky2 pata_acpi crc_itu_t
Jan 30 10:39:02 gateway kernel: [ 8832.436004] CPU: 0 PID: 7416 Comm: lsof Tainted: G      D W     3.13.0-76-generic #120-Ubuntu
Jan 30 10:39:02 gateway kernel: [ 8832.436004] Hardware name: Apple Computer, Inc. iMac6,1/Mac-F4218FC8, BIOS     IM61.88Z.0093.B07.0706281250 06/28/07
Jan 30 10:39:02 gateway kernel: [ 8832.436004] task: f60d6800 ti: c86e0000 task.ti: c86e0000
Jan 30 10:39:02 gateway kernel: [ 8832.436004] EIP: 0060:[<c11cca2a>] EFLAGS: 00010202 CPU: 0
Jan 30 10:39:02 gateway kernel: [ 8832.436004] EIP is at show_map_vma+0x3a/0x280
Jan 30 10:39:02 gateway kernel: [ 8832.436004] EAX: 08100071 EBX: c0097e40 ECX: 00000001 EDX: 00000001
Jan 30 10:39:02 gateway kernel: [ 8832.436004] ESI: ce7f33c0 EDI: 00000001 EBP: c86e1f14 ESP: c86e1ea0
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jan 30 10:39:02 gateway kernel: [ 8832.436004] CR0: 80050033 CR2: 00000011 CR3: 36af3000 CR4: 000007f0
Jan 30 10:39:02 gateway kernel: [ 8832.436004] Stack:
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  ce7f33c0 c1859770 b48e6000 b4918000 00000072 0000002d 00000078 00000070
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  00000000 00000000 00000008 00000001 00490aa6 f2411a00 00000001 f3a2afc0
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  c0097180 00000008 b4918000 00000001 00000000 00000000 00490aa6 b48e6000
Jan 30 10:39:02 gateway kernel: [ 8832.436004] Call Trace:
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  [<c11cd661>] show_pid_map+0x21/0x60
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  [<c1199894>] seq_read+0x204/0x360
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  [<c1199690>] ? seq_lseek+0x190/0x190
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  [<c117a998>] vfs_read+0x78/0x140
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  [<c117b109>] SyS_read+0x49/0x90
Jan 30 10:39:02 gateway kernel: [ 8832.436004]  [<c16675cd>] sysenter_do_call+0x12/0x12
Jan 30 10:39:02 gateway kernel: [ 8832.436004] Code: 7a 54 89 c6 8b 42 20 89 d3 85 ff 89 4d c4 89 45 c8 8b 46 50 8b 40 04 89 45 c0 8b 42 2c 0f 84 56 01 00 00 8b 52 58 85 d2 0f 45 fa <8b> 4f 10 8b 51 1c 8b 49 28 8b 52 08 89 4d e4 31 c9 89 55 f0 8b
Jan 30 10:39:02 gateway kernel: [ 8832.436004] EIP: [<c11cca2a>] show_map_vma+0x3a/0x280 SS:ESP 0068:c86e1ea0
Jan 30 10:39:02 gateway kernel: [ 8832.436004] CR2: 0000000000000011
Jan 30 10:39:02 gateway kernel: [ 8832.482871] ---[ end trace f7fc470cbf3a5ca0 ]---

```

Box is x86 running Ubuntu 14.04.  Last apt-get was:
```
Start-Date: 2016-01-28  06:02:29
Commandline: apt-get dist-upgrade
Upgrade: apache2-bin:i386 (2.4.7-1ubuntu4.8, 2.4.7-1ubuntu4.9), libcurl3:i386 (7.35.0-1ubuntu2.5, 7.35.0-1ubuntu2.6), curl:i386 (7.35.0-1ubuntu2.5, 7.35.0-1ubuntu2.6), apache2-mpm-prefork:i386 (2.4.7-1ubuntu4.8, 2.4.7-1ubuntu4.9), libcurl3-gnutls:i386 (7.35.0-1ubuntu2.5, 7.35.0-1ubuntu2.6), apache2-data:i386 (2.4.7-1ubuntu4.8, 2.4.7-1ubuntu4.9), apache2:i386 (2.4.7-1ubuntu4.8, 2.4.7-1ubuntu4.9), libcurl4-openssl-dev:i386 (7.35.0-1ubuntu2.5, 7.35.0-1ubuntu2.6)
End-Date: 2016-01-28  06:03:13

```

Anyone else seeing this?  Also, posting in hardware since it appears to be a CPU thing..please let me know if this wasn't the right spot.  Thank you.

---

