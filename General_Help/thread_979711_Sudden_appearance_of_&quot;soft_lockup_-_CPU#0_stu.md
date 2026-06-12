---
title: "Sudden appearance of &quot;soft lockup - CPU#0 stuck for 11s&quot;-induced freezes"
date: 2008-11-12
forum: General Help
---

### Post by rahaydenuk on 2008-11-12
Hi,

This morning my computer had frozen when I came to use it and I had to hard-reboot. On checking the syslog when it rebooted, I saw:

```
Nov 12 04:33:11 richardh kernel: [488420.581953] BUG: soft lockup - CPU#0 stuck for 11s! [cron:6473]
Nov 12 04:33:11 richardh kernel: [488420.581960] CPU 0:
Nov 12 04:33:11 richardh kernel: [488420.581962] Modules linked in: nls_iso8859_1 nls_cp437 joydev hci_usb vmnet(P) vmmon(P) ip6table_filter iptable_raw xt_comment xt_policy xt_multiport ipt_ULOG ipt_TTL ipt_ttl ipt_TOS ipt_tos ipt_SAME ipt_REJECT ipt_REDIRECT ipt_recent ipt_owner ipt_NETMAP ipt_MASQUERADE ipt_LOG ipt_iprange ipt_ECN ipt_ecn ipt_CLUSTERIP ipt_ah ipt_addrtype nf_nat_tftp nf_nat_snmp_basic nf_nat_sip nf_nat_pptp nf_nat_proto_gre nf_nat_irc nf_nat_h323 nf_nat_ftp nf_nat_amanda nf_conntrack_amanda nf_conntrack_tftp nf_conntrack_sip nf_conntrack_proto_sctp nf_conntrack_pptp nf_conntrack_proto_gre nf_conntrack_netlink nf_conntrack_netbios_ns nf_conntrack_irc nf_conntrack_h323 nf_conntrack_ftp xt_tcpmss xt_pkttype xt_physdev xt_NFQUEUE xt_NFLOG xt_MARK xt_mark xt_mac xt_limit xt_length xt_helper xt_hashlimit ip6_tables xt_dccp xt_conntrack xt_connmark xt_CLASSIFY xt_tcpudp xt_state iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle nfnetlink iptable_filter ip_tables x_tables nvidia(P) lirc
Nov 12 04:33:11 richardh kernel: mceusb2(F) usbhid lirc_dev evdev
Nov 12 04:33:11 richardh kernel: [488420.582038] Pid: 6473, comm: cron Tainted: PF       2.6.24.3 #1
Nov 12 04:33:11 richardh kernel: [488420.582040] RIP: 0010:[_spin_lock+7/16]  [_spin_lock+7/16] _spin_lock+0x7/0x10
Nov 12 04:33:11 richardh kernel: [488420.582048] RSP: 0018:ffff810121579e50  EFLAGS: 00000282
Nov 12 04:33:11 richardh kernel: [488420.582050] RAX: 0000302d37343238 RBX: 0000000001200011 RCX: 0000000000000000
Nov 12 04:33:11 richardh kernel: [488420.582052] RDX: 0000000000000000 RSI: ffff81012141e7c8 RDI: ffff81012f959b87
Nov 12 04:33:11 richardh kernel: [488420.582055] RBP: 0000001a000204d0 R08: ffff810005b08a98 R09: 0000000000000000
Nov 12 04:33:11 richardh kernel: [488420.582057] R10: 0000000000002da0 R11: ffffffff803d8cc0 R12: ffff81011d56b900
Nov 12 04:33:11 richardh kernel: [488420.582060] R13: ffff810121536900 R14: 00002ac830819000 R15: 00002ac830819000
Nov 12 04:33:11 richardh kernel: [488420.582063] FS:  00002ac830817b80(0000) GS:ffffffff80a40000(0000) knlGS:00000000f6ed76b0
Nov 12 04:33:11 richardh kernel: [488420.582065] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov 12 04:33:11 richardh kernel: [488420.582067] CR2: 00002aaaabd4d128 CR3: 00000001215dc000 CR4: 00000000000006e0
Nov 12 04:33:11 richardh kernel: [488420.582070] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 12 04:33:11 richardh kernel: [488420.582072] DR3: 0000000000000000 DR6: 00000000ffff4ff0 DR7: 0000000000000400
Nov 12 04:33:11 richardh kernel: [488420.582074]
Nov 12 04:33:11 richardh kernel: [488420.582075] Call Trace:
Nov 12 04:33:11 richardh kernel: [488420.582081]  [copy_process+2215/5040] copy_process+0x8a7/0x13b0
Nov 12 04:33:11 richardh kernel: [488420.582097]  [system_call+126/131] system_call+0x7e/0x83
Nov 12 04:33:11 richardh kernel: [488420.582100]  [do_fork+72/672] do_fork+0x48/0x2a0
Nov 12 04:33:11 richardh kernel: [488420.582108]  [ptregscall_common+103/176] ptregscall_common+0x67/0xb0
Nov 12 04:33:11 richardh kernel: [488420.582122]
```

And then it repeats every ~11s (which makes sense given the error line) for just over an hour, at which point the log goes dead up to when it is rebooted.

The first line of the error suggests it originates in a instance of cron (PID 6473). I download email from a POP account every 3 minutes with a cronjob so this is not unfeasible.

The last thing I did to change the configuration of this machine was over a week ago now, when I simply added a new wireless keyboard and mouse. I did not have to install any new drivers for this, it was picked up immediately by Ubuntu. Furthermore, this PC has been fine for this entire period, it has been on the entire time without a single crash and high usage levels a lot of the time. So this has just come out of the blue.

It seems to be running OK at the moment (for about 3.5 hours), but I'm at work now so have not been using it particularly heavily (not that it was under heavy usage when it died this morning).

Does anyone have any idea what's going on? I don't know where to start... surely this shouldn't happen?

Thanks,

Richard.

---

