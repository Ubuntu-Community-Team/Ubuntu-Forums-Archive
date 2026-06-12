---
title: "dmraid 10.04 stability issues, wifi crashes, kernel held back"
date: 2010-08-22
forum: Hardware
---

### Post by santana on 2010-08-22
Hi folks,

regrettably this is going to be a long post, I think the issues are interrelated. Installing on fake-raid with dmraid has always frozen my kernel and apt refuses to update the kernel even though a number of updated kernel are available. 


After upgrade to 10.04, my 2 drive raid 0 dmraid/fake-raid Asus G50VT notebook system is unstable. However 9.10 was rock solid the entire time I had it. I have two major issues after 10.04 upgrade described below. At least the second will be fixed by upgrading the kernel.  I tried to force it and the system was unusable after, I ended up doing a complete reinstall. 

***Why does having dmraid freeze the kernel?***
***How to update the kernel without hosing the system?***

**1)**
with 10.04, I am experiencing periodic crash that causes file system to be remounted read only and shortly after system crash brings machine down. During reboot, fsk detects errors, fixing gets me back up.

here is a bit of info that I was able to harvest from dmesg:

```
[ 6928.011402] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 6928.011413] ata5.00: failed command: FLUSH CACHE EXT
[ 6928.011428] ata5.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 6928.011431]          res 40/00:00:00:aa:22/00:00:00:00:00/40 Emask 0x4 (timeout)
[ 6928.011438] ata5.00: status: { DRDY }
[ 6928.011447] ata5: hard resetting link
[ 6928.360059] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 6928.433733] ata5.00: configured for UDMA/133
[ 6928.433743] ata5.00: device reported invalid CHS sector 0
[ 6928.433755] end_request: I/O error, dev sdb, sector 0
[ 6928.433788] ata5: EH complete
[ 6928.438644] Aborting journal on device dm-1-8.
[ 6928.439880] EXT4-fs error (device dm-1) in ext4_reserve_inode_write: Journal has aborted
[ 6928.439888] EXT4-fs (dm-1): Remounting filesystem read-only
```

**2)**
After 10.04 install wifi doesn't work. was fine in 09.10

chip:

```
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

kernel:

```
Linux g50vt 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
```


I harvested this info from dmesg:

```
[  110.519586] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  110.900959] r8169: eth0: link down
[  110.902345] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  111.100912] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  113.124741] wlan0: direct probe to AP 00:02:6f:5c:d9:05 (try 1)
[  113.127884] wlan0: direct probe responded
[  113.127892] wlan0: authenticate with AP 00:02:6f:5c:d9:05 (try 1)
[  113.129820] wlan0: authenticated
[  113.129854] wlan0: associate with AP 00:02:6f:5c:d9:05 (try 1)
[  113.130488] wlan0: deauthenticating from 00:02:6f:5c:d9:05 by local choice (reason=3)
[  113.130552] wlan0: direct probe to AP 00:02:6f:5c:d9:05 (try 1)
[  113.134418] wlan0: RX AssocResp from 00:02:6f:5c:d9:05 (capab=0x401 status=0 aid=4)
[  113.134424] wlan0: associated
[  113.135943] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  113.137950] ------------[ cut here ]------------
[  113.137967] WARNING: at /build/buildd/linux-2.6.32/kernel/softirq.c:143 local_bh_enable_ip+0x7b/0xa0()
[  113.137973] Hardware name: G50VT
[  113.137978] Modules linked in: arc4 snd_hda_codec_nvhdmi snd_hda_codec_realtek joydev rfcomm snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer sco ath9k snd_seq_device snd fbcon tileblit font bitblit softcursor video output mac80211 asus_laptop asus_oled(C) uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 bridge stp bnep l2cap btusb bluetooth sdhci_pci sdhci nvidia(P) vga16fb vgastate ath psmouse intel_agp cfg80211 led_class serio_raw soundcore snd_page_alloc lp parport dm_raid45 usbhid hid xor ohci1394 r8169 ieee1394 mii ahci
[  113.138103] Pid: 1686, comm: iwconfig Tainted: P         C 2.6.32-21-generic #32-Ubuntu
[  113.138109] Call Trace:
[  113.138122]  [<ffffffff81066d0b>] warn_slowpath_common+0x7b/0xc0
[  113.138130]  [<ffffffff81066d64>] warn_slowpath_null+0x14/0x20
[  113.138138]  [<ffffffff8106de4b>] local_bh_enable_ip+0x7b/0xa0
[  113.138148]  [<ffffffff81540e69>] _spin_unlock_bh+0x19/0x20
[  113.138172]  [<ffffffffa0dca955>] ath_tx_node_cleanup+0x185/0x1b0 [ath9k]
[  113.138191]  [<ffffffffa0dc4d77>] ath9k_sta_notify+0x57/0xb0 [ath9k]
[  113.138212]  [<ffffffffa0cfc89c>] __sta_info_unlink+0x15c/0x1f0 [mac80211]
[  113.138230]  [<ffffffffa0cfc96d>] sta_info_unlink+0x3d/0x60 [mac80211]
[  113.138252]  [<ffffffffa0d04e96>] ieee80211_set_disassoc+0x1b6/0x220 [mac80211]
[  113.138273]  [<ffffffffa0d051c1>] ieee80211_mgd_deauth+0x111/0x120 [mac80211]
[  113.138295]  [<ffffffffa0d0a7de>] ieee80211_deauth+0x1e/0x20 [mac80211]
[  113.138319]  [<ffffffffa00e8f4e>] __cfg80211_mlme_deauth+0xee/0x130 [cfg80211]
[  113.138340]  [<ffffffffa00ec709>] __cfg80211_disconnect+0x159/0x1d0 [cfg80211]
[  113.138351]  [<ffffffff811120b5>] ? unmap_page_range+0x1c5/0x2a0
[  113.138370]  [<ffffffffa00f039f>] cfg80211_mgd_wext_siwap+0x12f/0x250 [cfg80211]
[  113.138380]  [<ffffffff81520fc0>] ? ioctl_private_call+0x0/0xa0
[  113.138399]  [<ffffffffa00ee8a5>] cfg80211_wext_siwap+0xc5/0xd0 [cfg80211]
[  113.138407]  [<ffffffff81520c40>] ioctl_standard_call+0x60/0xd0
[  113.138417]  [<ffffffff8145ed30>] ? __dev_get_by_name+0xa0/0xc0
[  113.138425]  [<ffffffff81520be0>] ? ioctl_standard_call+0x0/0xd0
[  113.138432]  [<ffffffff815203b9>] wireless_process_ioctl+0xe9/0x170
[  113.138440]  [<ffffffff81520be0>] ? ioctl_standard_call+0x0/0xd0
[  113.138448]  [<ffffffff815204b1>] wext_ioctl_dispatch+0x71/0xb0
[  113.138455]  [<ffffffff81520fc0>] ? ioctl_private_call+0x0/0xa0
[  113.138463]  [<ffffffff81520626>] wext_handle_ioctl+0x46/0x90
[  113.138471]  [<ffffffff8145ffc3>] dev_ioctl+0x423/0x430
[  113.138480]  [<ffffffff810f3b47>] ? unlock_page+0x27/0x30
[  113.138487]  [<ffffffff81111e29>] ? __do_fault+0x439/0x500
[  113.138497]  [<ffffffff8144a3bd>] sock_ioctl+0x9d/0x280
[  113.138507]  [<ffffffff81152a92>] vfs_ioctl+0x22/0xa0
[  113.138518]  [<ffffffff812b746a>] ? __up_read+0x9a/0xc0
[  113.138525]  [<ffffffff81152d41>] do_vfs_ioctl+0x81/0x380
[  113.138535]  [<ffffffff8108999e>] ? up_read+0xe/0x10
[  113.138545]  [<ffffffff81543838>] ? do_page_fault+0x158/0x3b0
[  113.138553]  [<ffffffff811530c1>] sys_ioctl+0x81/0xa0
[  113.138564]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[  113.138571] ---[ end trace a670c40ef6332d47 ]---
[  113.170171] wlan0: deauthenticating from 00:02:6f:5c:d9:05 by local choice (reason=3)
[  113.170249] wlan0: direct probe to AP 00:02:6f:5c:d9:05 (try 1)
[  113.173979] wlan0: direct probe responded
[  113.173986] wlan0: authenticate with AP 00:02:6f:5c:d9:05 (try 1)
[  113.176148] wlan0: authenticated
[  113.176181] wlan0: associate with AP 00:02:6f:5c:d9:05 (try 1)
[  113.179389] wlan0: RX AssocResp from 00:02:6f:5c:d9:05 (capab=0x401 status=0 aid=4)
[  113.179396] wlan0: associated
[  113.200584] wlan0: deauthenticating from 00:02:6f:5c:d9:05 by local choice (reason=3)
[  113.201639] type=1503 audit(1281811316.180:12):  operation="open" pid=1687 parent=1675 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[  123.590121] wlan0: no IPv6 routers present 
```

I have spent a lot of time upgrading to 10.04 and dual booting the system with vista 64. I am forced to use vista whenever I am away from home to get usable wifi. Unfortunately Vista 64 is more stable than ubuntu 10.04. Any one can help?

---

### Post by ronparent on 2010-08-22
What method are you using to install 10.04 to the raid?

---

### Post by santana on 2010-09-04
When I installed Ubunut, I used the procedure in the ubuntu fake raid how to [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). Because I am dual booting, I did not let the installer install grub, I installed Grub 2 from the live cd after the install. That used to be necessary, not sure if it is still so, but it works.

Unfortunately with wifi not working is a major issue, and I had to make the hard call to ditch ubuntu for now.
 
I have just installed fedora 13, and it was flawless, ubiquity handled the fake raid seamlessly, no need to install grub after the fact.

An unexpected but pleasant side effect of switching to Fedora is that KDE4 integration seems to be **much** better in fedora than in Kubuntu. 

I still view Fedora as bloatware and much prefer apt to yum and Ubuntu's minimalist mo, but I'm finding Fedora is just plain better in two very important ways:
1) KDE integration
2) out of the box support for Fake Raid.

Come on Ubuntu get your act together!

---

### Post by ronparent on 2010-09-05
Something I had not noted before. The nomenclature for a device named dm-1 isn't implemented until 10.10 (Maverick). It refers to a raid symolic link - I don't know which one (that may depend on the specific kernel installed). The net affect may be if you think you are updating 10.04 and 10.10 kernels are creeping in, that may account for freezing. It may be advisable for you to do a clean install of either one of them. The current beta release of 10.10 appears to improve functionality using raid, but, is not yet advised for production machines.

---

