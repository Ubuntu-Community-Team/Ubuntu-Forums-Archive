---
title: "how to unload a sound module"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by Depressed Man on 2007-07-09
From poking around (after trying to get sound working correctly after a suspend) I somehow figured this out.

vforviktor@vendetta-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
vforviktor@vendetta-laptop:~$ 


Is the STAC92xx Analog my sound module?

If yes, then I just need to add it to this part right?

```
See this part of /etc/default/acpi-support:

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
Module=STAC92xx Analog
```

---

### Post by kidders on 2007-07-10
Hi there,

If you don't recognise your sound card driver in **lsmod**, you could use **cat /proc/asound/modules** instead. Kernel module names are *always* single, lower case words.

I've never tried what you're doing, but it strikes me that you may need to unload a bit more than just the top level driver. You see, loading a sound card driver usually causes a chain of dependent kernel modules to load as well. Some (or all) of these may need to be unloaded/reloaded for your sound to behave itself, depending on which one of them is causing you problems.

Having said that, my advice would be to try your sound card driver on its own first. If there's no improvement, you might think about trying the blunderbuss approach!

---

### Post by Depressed Man on 2007-07-10
Hmm..

It seems my sound module is actually snd_hda_intel. But it seems the STAC92xx Analog is the driver.

Edit: adding snd_hda_intel didn't work. :(

---

### Post by kidders on 2007-07-10
> **Depressed Man said:**
> It seems my sound module is actually snd_hda_intel. But it seems the STAC92xx Analog is the driver.snd_hda_intel *is* an audio driver. "STAC92xx Analog" isn't really anything ... maybe just a description of your hardware.

What sorts of MODULES=" ... " lists have you tried so far?

---

### Post by Depressed Man on 2007-07-11
Just the hda_sound_intel one and the STAC one. There isn't anything else listed in my /proc/asound/modules

---

### Post by kidders on 2007-07-11
Hmm... that's what I suspected might happen. Looks like you may have to list more (if not all) of your audio-related kernel modules, as I mentioned earlier.

---

### Post by Depressed Man on 2007-07-12
Ok, I did a find for modules.. but which ones are my sound modules? 

```
/lib/modules/2.6.20-16-generic/kernel/fs/isofs/isofs.ko
/lib/modules/2.6.20-16-generic/kernel/fs/binfmt_aout.ko
/lib/modules/2.6.20-16-generic/kernel/fs/autofs
/lib/modules/2.6.20-16-generic/kernel/fs/autofs/autofs.ko
/lib/modules/2.6.20-16-generic/kernel/fs/udf
/lib/modules/2.6.20-16-generic/kernel/fs/udf/udf.ko
/lib/modules/2.6.20-16-generic/kernel/fs/ext2
/lib/modules/2.6.20-16-generic/kernel/fs/ext2/ext2.ko
/lib/modules/2.6.20-16-generic/kernel/fs/configfs
/lib/modules/2.6.20-16-generic/kernel/fs/configfs/configfs.ko
/lib/modules/2.6.20-16-generic/kernel/net
/lib/modules/2.6.20-16-generic/kernel/net/llc
/lib/modules/2.6.20-16-generic/kernel/net/llc/llc2.ko
/lib/modules/2.6.20-16-generic/kernel/net/sunrpc
/lib/modules/2.6.20-16-generic/kernel/net/sunrpc/sunrpc.ko
/lib/modules/2.6.20-16-generic/kernel/net/sunrpc/auth_gss
/lib/modules/2.6.20-16-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_spkm3.ko
/lib/modules/2.6.20-16-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko
/lib/modules/2.6.20-16-generic/kernel/net/sunrpc/auth_gss/auth_rpcgss.ko
/lib/modules/2.6.20-16-generic/kernel/net/packet
/lib/modules/2.6.20-16-generic/kernel/net/packet/af_packet.ko
/lib/modules/2.6.20-16-generic/kernel/net/x25
/lib/modules/2.6.20-16-generic/kernel/net/x25/x25.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipx
/lib/modules/2.6.20-16-generic/kernel/net/ipx/ipx.ko
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/bnep
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/bnep/bnep.ko
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/hidp
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/hidp/hidp.ko
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/cmtp
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/cmtp/cmtp.ko
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/sco.ko
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/bluetooth.ko
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/l2cap.ko
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/rfcomm
/lib/modules/2.6.20-16-generic/kernel/net/bluetooth/rfcomm/rfcomm.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/softmac
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/lib/modules/2.6.20-16-generic/kernel/net/wanrouter
/lib/modules/2.6.20-16-generic/kernel/net/wanrouter/wanrouter.ko
/lib/modules/2.6.20-16-generic/kernel/net/802
/lib/modules/2.6.20-16-generic/kernel/net/802/p8023.ko
/lib/modules/2.6.20-16-generic/kernel/net/econet
/lib/modules/2.6.20-16-generic/kernel/net/econet/econet.ko
/lib/modules/2.6.20-16-generic/kernel/net/8021q
/lib/modules/2.6.20-16-generic/kernel/net/8021q/8021q.ko
/lib/modules/2.6.20-16-generic/kernel/net/appletalk
/lib/modules/2.6.20-16-generic/kernel/net/appletalk/appletalk.ko
/lib/modules/2.6.20-16-generic/kernel/net/irda
/lib/modules/2.6.20-16-generic/kernel/net/irda/irnet
/lib/modules/2.6.20-16-generic/kernel/net/irda/irnet/irnet.ko
/lib/modules/2.6.20-16-generic/kernel/net/irda/irlan
/lib/modules/2.6.20-16-generic/kernel/net/irda/irlan/irlan.ko
/lib/modules/2.6.20-16-generic/kernel/net/irda/irda.ko
/lib/modules/2.6.20-16-generic/kernel/net/irda/ircomm
/lib/modules/2.6.20-16-generic/kernel/net/irda/ircomm/ircomm.ko
/lib/modules/2.6.20-16-generic/kernel/net/irda/ircomm/ircomm-tty.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched
/lib/modules/2.6.20-16-generic/kernel/net/sched/em_cmp.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/cls_rsvp6.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/em_meta.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_cbq.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_dsmark.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/em_text.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_tbf.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_prio.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_ingress.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_htb.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/em_u32.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/cls_basic.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/em_nbyte.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_hfsc.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/cls_fw.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/cls_u32.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/cls_route.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_atm.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_red.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/cls_tcindex.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/cls_rsvp.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_netem.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_teql.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_gred.ko
/lib/modules/2.6.20-16-generic/kernel/net/sched/sch_sfq.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/xfrm6_mode_tunnel.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/tunnel6.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/xfrm6_mode_ro.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/ip6_tunnel.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/esp6.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/xfrm6_tunnel.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/ipv6.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/xfrm6_mode_transport.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/ipcomp6.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6table_filter.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6table_raw.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_ah.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_rt.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6_tables.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_ipv6header.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_frag.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_hl.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_eui64.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_hbh.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6_queue.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/nf_conntrack_ipv6.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6table_mangle.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_REJECT.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_HL.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_LOG.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/netfilter/ip6t_owner.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/sit.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/xfrm6_mode_beet.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv6/ah6.ko
/lib/modules/2.6.20-16-generic/kernel/net/rose
/lib/modules/2.6.20-16-generic/kernel/net/rose/rose.ko
/lib/modules/2.6.20-16-generic/kernel/net/decnet
/lib/modules/2.6.20-16-generic/kernel/net/decnet/decnet.ko
/lib/modules/2.6.20-16-generic/kernel/net/decnet/netfilter
/lib/modules/2.6.20-16-generic/kernel/net/decnet/netfilter/dn_rtmsg.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge
/lib/modules/2.6.20-16-generic/kernel/net/bridge/bridge.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_limit.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_redirect.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_among.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebtable_broute.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_ulog.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_vlan.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebtables.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_stp.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_pkttype.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_802_3.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_arpreply.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_arp.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebtable_filter.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_snat.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebtable_nat.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_ip.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_dnat.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_log.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_mark_m.ko
/lib/modules/2.6.20-16-generic/kernel/net/bridge/netfilter/ebt_mark.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_h323.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_multiport.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_hashlimit.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_amanda.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nfnetlink.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_state.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_ftp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_tftp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_quota.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_sctp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_helper.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_realm.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nfnetlink_queue.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_statistic.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_conntrack.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_comment.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_pptp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_string.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_netbios_ns.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_mark.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_SECMARK.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nfnetlink_log.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_limit.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_proto_sctp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_MARK.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_CLASSIFY.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_proto_gre.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_dccp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_NFLOG.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_esp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_irc.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_netlink.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_length.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/x_tables.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/nf_conntrack_sip.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_CONNSECMARK.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_tcpmss.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_NFQUEUE.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_physdev.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_pkttype.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_mac.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_DSCP.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_connmark.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_tcpudp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_dscp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_connbytes.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_policy.ko
/lib/modules/2.6.20-16-generic/kernel/net/netrom
/lib/modules/2.6.20-16-generic/kernel/net/netrom/netrom.ko
/lib/modules/2.6.20-16-generic/kernel/net/key
/lib/modules/2.6.20-16-generic/kernel/net/key/af_key.ko
/lib/modules/2.6.20-16-generic/kernel/net/ax25
/lib/modules/2.6.20-16-generic/kernel/net/ax25/ax25.ko
/lib/modules/2.6.20-16-generic/kernel/net/rxrpc
/lib/modules/2.6.20-16-generic/kernel/net/rxrpc/rxrpc.ko
/lib/modules/2.6.20-16-generic/kernel/net/lapb
/lib/modules/2.6.20-16-generic/kernel/net/lapb/lapb.ko
/lib/modules/2.6.20-16-generic/kernel/net/atm
/lib/modules/2.6.20-16-generic/kernel/net/atm/br2684.ko
/lib/modules/2.6.20-16-generic/kernel/net/atm/lec.ko
/lib/modules/2.6.20-16-generic/kernel/net/atm/mpoa.ko
/lib/modules/2.6.20-16-generic/kernel/net/atm/pppoatm.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ah4.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/tunnel4.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/xfrm4_mode_beet.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/esp4.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/xfrm4_mode_transport.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ip_gre.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipip.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipcomp.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/xfrm4_tunnel.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/arptable_filter.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/arpt_mangle.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_h323.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_TCPMSS.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_TTL.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_ftp.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/iptable_nat.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_owner.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_LOG.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_tos.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/iptable_raw.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_ECN.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_addrtype.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_tftp.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_amanda.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_TOS.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_proto_gre.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ip_tables.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_ah.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_NETMAP.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_recent.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_REJECT.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/iptable_filter.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_pptp.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_MASQUERADE.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_irc.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_snmp_basic.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_REDIRECT.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ip_queue.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat_sip.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_nat.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/arp_tables.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_CLUSTERIP.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_ttl.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/iptable_mangle.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_ecn.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_ULOG.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_SAME.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/nf_conntrack_ipv4.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/netfilter/ipt_iprange.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_wlc.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_wrr.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_rr.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_nq.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_lblcr.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_lblc.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_ftp.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_sh.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_sed.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_lc.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/ipvs/ip_vs_dh.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/tcp_probe.ko
/lib/modules/2.6.20-16-generic/kernel/net/ipv4/xfrm4_mode_tunnel.ko
/lib/modules/2.6.20-16-generic/kernel/net/tipc
/lib/modules/2.6.20-16-generic/kernel/net/tipc/tipc.ko
/lib/modules/2.6.20-16-generic/kernel/net/xfrm
/lib/modules/2.6.20-16-generic/kernel/net/xfrm/xfrm_user.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_diag.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_ipv4.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_probe.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/dccp_ccid3.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/dccp_ccid2.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/lib
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/lib/dccp_tfrc_lib.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_ipv6.ko
/lib/modules/2.6.20-16-generic/kernel/net/core
/lib/modules/2.6.20-16-generic/kernel/net/core/pktgen.ko
/lib/modules/2.6.20-16-generic/kernel/net/sctp
/lib/modules/2.6.20-16-generic/kernel/net/sctp/sctp.ko
/lib/modules/2.6.20-16-generic/kernel/arch
/lib/modules/2.6.20-16-generic/kernel/arch/i386
/lib/modules/2.6.20-16-generic/kernel/arch/i386/crypto
/lib/modules/2.6.20-16-generic/kernel/arch/i386/crypto/twofish-i586.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/crypto/aes-i586.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/scx200.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/microcode.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/longhaul.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/longrun.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/gx-suspmod.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-smi.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-lib.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/cpufreq-nforce2.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k6.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-ich.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/p4-clockmod.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k7.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpuid.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/apm.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/msr.ko
/lib/modules/2.6.20-16-generic/kernel/arch/i386/oprofile
/lib/modules/2.6.20-16-generic/kernel/arch/i386/oprofile/oprofile.ko
/lib/modules/2.6.20-16-generic/kernel/lib
/lib/modules/2.6.20-16-generic/kernel/lib/ts_fsm.ko
/lib/modules/2.6.20-16-generic/kernel/lib/libcrc32c.ko
/lib/modules/2.6.20-16-generic/kernel/lib/reed_solomon
/lib/modules/2.6.20-16-generic/kernel/lib/reed_solomon/reed_solomon.ko
/lib/modules/2.6.20-16-generic/kernel/lib/crc16.ko
/lib/modules/2.6.20-16-generic/kernel/lib/zlib_deflate
/lib/modules/2.6.20-16-generic/kernel/lib/zlib_deflate/zlib_deflate.ko
/lib/modules/2.6.20-16-generic/kernel/lib/crc-ccitt.ko
/lib/modules/2.6.20-16-generic/kernel/lib/ts_kmp.ko
/lib/modules/2.6.20-16-generic/kernel/lib/ts_bm.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu
/lib/modules/2.6.20-16-generic/kernel/ubuntu/mactel
/lib/modules/2.6.20-16-generic/kernel/ubuntu/mactel/appleir.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/mactel/applesmc.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/zd1211rw
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/zd1211rw/zd1211rw-mac80211.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/prism2
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/prism2/prism2_pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/prism2/prism2_plx.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/prism2/p80211
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/prism2/p80211/p80211.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/prism2/prism2_usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl818x
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl818x/r818x.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/at76
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/fsam7400.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/acx
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/acx/acx.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2400
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2400/rt2400.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/adm8211
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/adm8211/adm8211.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/p54
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/p54/prism54common.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/p54/prism54pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/p54/prism54usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/bcm43xx
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/bcm43xx/bcm43xx-mac80211.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/iwlwifi
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/iwlwifi/iwlwifi.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/lmpcm_usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/acerhk.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/pbe5.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/cloop.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_dectlk.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_acntsa.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_spkout.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_apollo.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakupmain.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_bns.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_decext.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_acntpc.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_decpc.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_sftsyn.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_keyhelp.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_audptr.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_txprt.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_keypc.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_ltlk.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/speakup/speakup_dtlk.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/nozomi.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/snd-bt-sco.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/crc-itu-t.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/eeprom_93cx6.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/av5100.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/dm-bbr.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/ssb
/lib/modules/2.6.20-16-generic/kernel/ubuntu/ssb/ssb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/block
/lib/modules/2.6.20-16-generic/kernel/ubuntu/block/gnbd.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/gfs
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/gfs/gfs.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/asfs
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/asfs/asfs.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/squashfs
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/squashfs/squashfs.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/dazuko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/dazuko/dazuko.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/unionfs
/lib/modules/2.6.20-16-generic/kernel/ubuntu/fs/unionfs/unionfs.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/acpi
/lib/modules/2.6.20-16-generic/kernel/ubuntu/acpi/dev_acpi.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/acpi/tc1100-wmi.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/acpi/sony_acpi.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/acpi/pcc_acpi.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/rtl_ieee80211
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/wireless
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/wireless/cfg80211.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/ipg
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/ipg/ipg.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/atl1
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/atl1/atl1.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/mac80211
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/mac80211/rc80211_simple.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/mac80211/mac80211.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv/ivtv-fb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv/ivtv.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ivtv/saa717x.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/gspcav1
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/gspcav1/gspca.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ov511
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/ov511/ov511.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/quickcam
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/quickcam/quickcam.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/usbvideo
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.20-16-generic/modules.isapnpmap
/lib/modules/2.6.20-16-generic/modules.ccwmap
/lib/modules/2.6.20-16-generic/modules.alias
/lib/modules/2.6.20-16-generic/volatile
/lib/modules/2.6.20-16-generic/volatile/nvidia_new.ko
/lib/modules/2.6.20-16-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.20-16-generic/volatile/nvidia.ko
/lib/modules/2.6.20-16-generic/volatile/fxusb.ko
/lib/modules/2.6.20-16-generic/volatile/fglrx.ko
/lib/modules/2.6.20-16-generic/volatile/fcusb.ko
/lib/modules/2.6.20-16-generic/volatile/fcpci.ko
/lib/modules/2.6.20-16-generic/volatile/fcdslusba.ko
/lib/modules/2.6.20-16-generic/volatile/fcdslusb2.ko
/lib/modules/2.6.20-16-generic/volatile/fcdslusb.ko
/lib/modules/2.6.20-16-generic/volatile/fcdslslusb.ko
/lib/modules/2.6.20-16-generic/volatile/fcdslsl.ko
/lib/modules/2.6.20-16-generic/volatile/fcdsl2.ko
/lib/modules/2.6.20-16-generic/volatile/fcdsl.ko
/lib/modules/2.6.20-16-generic/volatile/ath_hal.ko
/lib/modules/2.6.20-16-generic/volatile/.mounted
find: *.ko: No such file or directory
vforviktor@vendetta-laptop:~$ 

```

Is it the ones with the /speakup?

---

### Post by kidders on 2007-07-13
Speakup is a synthesizer for blind users, afaik. The best place to look for modules you might be interested in unloading is in the output of **lsmod** (ie the list of loaded modules).

---

### Post by Depressed Man on 2007-07-13
Ok, here's the output of my lsmod. 

```
Module                  Size  Used by
snd_rtctimer            4384  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               6784  1 ecb
ieee80211_crypt_wep     6144  1 
af_packet              23816  4 
ipv6                  268960  10 
binfmt_misc            12680  1 
uinput                 10240  0 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
i915                   24448  8 
drm                    81044  9 i915
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
sonypi                 23196  0 
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
video                  16388  0 
sbs                    15652  0 
button                  8720  0 
ac                      6020  0 
dock                   10268  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
battery                10756  0 
container               5248  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
fuse                   46612  3 
r5u870                 71620  0 
video_buf              26116  1 r5u870
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
joydev                 10816  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
pcmcia                 39212  0 
ipw3945               118816  1 
snd_seq_oss            32896  0 
uvcvideo               42500  0 
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
videodev               28160  2 r5u870,uvcvideo
v4l1_compat            15236  3 r5u870,uvcvideo,videodev
v4l2_common            25216  3 r5u870,uvcvideo,videodev
tifm_7xx1               8704  0 
tifm_core              11140  1 tifm_7xx1
psmouse                38920  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               7940  0 
intel_agp              25244  1 
agpgart                35400  3 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  4 
usb_storage            72256  0 
libusual               17936  1 usb_storage
ata_piix               15492  3 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
e100                   36232  0 
mii                     6528  1 e100
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  7 r5u870,uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

My first guess is anything with snd is a sound module. But any other help would be appreciated.

---

### Post by kidders on 2007-07-13
Yeah, I *think* that would cover them all.

---

### Post by Depressed Man on 2007-07-14
Ok, here's my new list. 

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="snd_hda_intel" snd_rtctimer snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd snd_seq_device snd_page_alloc
```

But should I put quotes between each snd_etc..?

---

### Post by IntuitiveNipple on 2007-07-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/100114](https://bugs.launchpad.net/ubuntu/+bug/100114) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Are you having problems with static and looping playback after resuming from suspend? If so, Willem and I got to the root of the bug and published a patch last week:

[Bug #100114: snd-hda-intel: distorted sound after resume, until the module is reloaded](https://bugs.launchpad.net/ubuntu/+bug/100114).

You won't need to add any entries to **/etc/default/acpi-support** in addition to this fix.

If you're using Feisty 32-bit 2.6.20-16-generic then instead of having to build the modules you can download the attachment I've made to this post which contains the binary modules with my fix applied, and as a bonus the script I used during testing to load/unload all sound modules.

You many need to close the volume control and any other audio applications or utilities in order to successfully unload the sound drivers.

To install the attached kernel modules:
```
$ cd ~
$ mkdir snd-hda-intel
$ cd snd-hda-intel
$ mkdir backup
$ wget http://ubuntuforums.org/attachment.php?attachmentid=38193&d=1184446052
$ tar -xjvf snd-hda-intel-2.6.20-16-generic-resume-fix.tar.bz2
$ sudo ./snd.sh unload
$ sudo mv /lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-*.ko ./backup/
$ sudo mv ./snd-hda-*.ko /lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/
$ sudo depmod -a
$ sudo ./snd.sh load

```

---

### Post by Depressed Man on 2007-07-14
Yes I am! Though I need to unload these modules

Unloading...
FATAL: Module snd_hda_intel is in use.
FATAL: Module snd_hda_codec is in use.
FATAL: Module snd_pcm is in use.
FATAL: Module snd_timer is in use.
FATAL: Module snd_page_alloc is in use.
FATAL: Module snd is in use.


sudo modprobe -r nameofmodule right to unload?

Edit: After closing the sound control it worked.

Though now suspend doesn't work properly? Before I could tell it to suspend and it would power off waiting for me to power it back on to work. Now the screen just goes black but after a while, the log in screen to log me back into my session pops up. The power never turns off.

Edit2: After a reboot, it works! Thank You. Thanks to you, I can now use Ubuntu on my laptop close to full time (before I couldn't since I need to save energy between classes).

---

