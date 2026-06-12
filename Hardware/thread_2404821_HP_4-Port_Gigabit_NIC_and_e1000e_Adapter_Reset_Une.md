---
title: "HP 4-Port Gigabit NIC and e1000e: Adapter Reset Unexpectedly"
date: 2018-10-29
forum: Hardware
---

### Post by GraysonPeddie on 2018-10-29
[SIZE=6]Issue:[/SIZE]

Had to reboot my server a couple of times due to HP 4-port Network Card shutting down randomly. I had to reboot about 4 or 5 times tonight and last Friday night, I rebooted my server about 10 times.

[SIZE=6]Error message:[/SIZE]

e1000e 0000:0x:00.x: Reset adapter unexpectly

[SIZE=6]Steps to reproduce:[/SIZE]

My HP 4-Port Gigabit NIC shuts down at random. That's easy for me to reproduce regardless of whether my server is running idle or if I'm watching Netflix or stream YouTube videos.

[SIZE=6]Things I've tried:[/SIZE]

[LIST]
[*]Grub: pcie_aspm=off (although it does not look like grub-mkconfig has appended the command line when I do an update and I've rebooted)
[*][FONT=Courier New]sudo ethtool -K enp3s0f0 gso off gro off tso off[/FONT] (that didn't work for me for all four interfaces)
[/LIST]

[SIZE=6]Server specs:[/SIZE]

[LIST]
[*]ASRock AM1H-ITX
[*]AMD Athlon 5350 APU
[*]12GB RAM
[*]128GB SSD
[*]2TB Hard Drive
[*][HP 4-Port Gigabit NIC](https://www.amazon.com/gp/product/B000P0NX3G/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1)
```
grayson@home-server:~$ lspci | grep Intel
03:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
03:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
04:00.0 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
04:00.1 Ethernet controller: Intel Corporation 82571EB Gigabit Ethernet Controller (Copper) (rev 06)
```
[/LIST]

[SIZE=6]Ubuntu/Kernel version:[/SIZE]

Ubuntu 18.04
4.15.0-36-generic

(Had to reboot to get the kernel version due to "adapter reset unexpectedly" message.)

[SIZE=6]Network configuration (Relevant?):[/SIZE]

```
[grayson@acer-laptop Videos]$ cat netplan_ubuntuserver.yaml 
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp6s0:
            dhcp4: false
        enp3s0f1:
            dhcp4: false
        enp4s0f0:
            dhcp4: false
        enp4s0f1:
            dhcp4: false
    bridges:
      br0:
        interfaces:
        - enp4s0f1
        dhcp4: false
        addresses:
        - 172.20.0.1/27
        gateway4: 172.20.0.2
        nameservers:
          addresses:
          - 172.20.0.3
          - 127.0.0.1
          search:
          - graysonpeddie.lan
      br10:
        interfaces:
        - enp4s0f0
        - vlan10
        dhcp4: false
        addresses:
        - 172.20.0.33/27
        nameservers:
          addresses:
          - 172.20.0.3
          - 127.0.0.1
          search:
          - graysonpeddie.lan
      br20:
        interfaces:
        - enp3s0f1
        dhcp4: false
        addresses:
        - 172.20.0.65/27
        nameservers:
          addresses:
          - 172.20.0.3
          - 127.0.0.1
          search:
          - graysonpeddie.lan
      br30:
        interfaces:
        - vlan30
        dhcp4: false
        addresses:
        - 172.20.0.97/27
        nameservers:
          addresses:
          - 172.20.0.3
          - 127.0.0.1
          search:
          - graysonpeddie.lan
    vlans:
      vlan10:
        id: 10
        link: enp4s0f1
      vlan30:
        id: 30
        link: enp4s0f1
    version: 2
```

[SIZE=6]Logs (/var/log/syslog):[/SIZE]

```
Oct 29 00:58:38 home-server kernel: [ 3076.063130] e1000e 0000:04:00.0 enp4s0f0: Reset adapter unexpectedly
Oct 29 00:58:38 home-server kernel: [ 3076.063464] br10: port 1(enp4s0f0) entered disabled state
Oct 29 00:58:38 home-server systemd-networkd[913]: enp4s0f0: Lost carrier
Oct 29 00:58:39 home-server systemd-networkd[913]: br10: Lost carrier
Oct 29 00:59:36 home-server systemd[1]: Created slice User Slice of grayson.
Oct 29 00:59:36 home-server systemd[1]: Starting User Manager for UID 1000...
Oct 29 00:59:36 home-server systemd[1]: Started Session 2 of user grayson.
Oct 29 00:59:38 home-server systemd[9127]: Listening on GnuPG cryptographic agent and passphrase cache.
Oct 29 00:59:38 home-server systemd[9127]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Oct 29 00:59:38 home-server systemd[9127]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Oct 29 00:59:38 home-server systemd[9127]: Reached target Timers.
Oct 29 00:59:38 home-server systemd[9127]: Reached target Paths.
Oct 29 00:59:38 home-server systemd[9127]: Listening on GnuPG network certificate management daemon.
Oct 29 00:59:38 home-server systemd[9127]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Oct 29 00:59:38 home-server systemd[9127]: Reached target Sockets.
Oct 29 00:59:38 home-server systemd[9127]: Reached target Basic System.
Oct 29 00:59:38 home-server systemd[9127]: Reached target Default.
Oct 29 00:59:38 home-server systemd[9127]: Startup finished in 74ms.
Oct 29 00:59:38 home-server systemd[1]: Started User Manager for UID 1000.
Oct 29 01:00:37 home-server systemd[1]: Stopping Availability of block devices...
Oct 29 01:00:37 home-server systemd[1]: Stopped target RPC Port Mapper.
Oct 29 01:00:37 home-server systemd[1]: Stopping Authorization Manager...
Oct 29 01:00:37 home-server systemd[1]: Stopped Stop ureadahead data collection 45s after completed startup.
Oct 29 01:00:37 home-server systemd[1]: Stopped target Graphical Interface.
Oct 29 01:00:37 home-server systemd[1]: Stopped QEMU KVM preparation - module, ksm, hugepages.
Oct 29 01:00:37 home-server systemd[1]: Stopped target Cloud-init target.
Oct 29 01:00:37 home-server systemd[1]: Stopped target Timers.
Oct 29 01:00:37 home-server systemd[1]: Stopped Daily Cleanup of Temporary Directories.
Oct 29 01:00:37 home-server systemd[1]: Stopped Daily apt upgrade and clean activities.
Oct 29 01:00:37 home-server systemd[1]: Stopped Daily apt download activities.
Oct 29 01:00:37 home-server systemd[1]: Stopped Execute cloud user/final scripts.
Oct 29 01:00:37 home-server systemd[1]: Stopped Apply the settings specified in cloud-config.
Oct 29 01:00:37 home-server systemd[1]: Stopped target Cloud-config availability.
Oct 29 01:00:37 home-server systemd[1]: Closed Load/Save RF Kill Switch Status /dev/rfkill Watch.
Oct 29 01:00:37 home-server systemd[1]: Stopped target Multi-User System.
Oct 29 01:00:37 home-server systemd[1]: Stopping LXC Container Initialization and Autoboot Code...
Oct 29 01:00:37 home-server systemd[1]: Stopping LSB: Record successful boot for GRUB...
Oct 29 01:00:37 home-server systemd[1]: Stopping Plex Media Server for Linux...
Oct 29 01:00:37 home-server systemd[1]: Stopping Samba SMB Daemon...
Oct 29 01:00:37 home-server systemd[1]: Stopping Deferred execution scheduler...
Oct 29 01:05:02 home-server snapd[1075]: stateengine.go:102: state ensure error: Get https://api.snapcraft.io/api/v1/snaps/sections: net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)
Oct 29 01:05:16 home-server systemd[1]: Starting Stop ureadahead data collection...
Oct 29 01:05:16 home-server systemd[1]: Started Stop ureadahead data collection.
Oct 29 01:05:49 home-server kernel: [  230.219975] audit: type=1400 audit(1540775149.721:50): apparmor="DENIED" operation="mount" info="failed flags match" error=-13 profile="lxc-container-default-cgns" name="/" pid=4254 comm="(an-start)" flags="rw, rslave"
Oct 29 01:17:01 home-server systemd[1]: Starting Cleanup of Temporary Directories...
Oct 29 01:17:01 home-server CRON[6232]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 29 01:17:01 home-server systemd[1]: Started Cleanup of Temporary Directories.
Oct 29 01:22:04 home-server kernel: [ 1204.854693]  raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear amdgpu chash radeon hid_generic i2c_algo_bit ttm aesni_intel drm_kms_helper aes_x86_64 syscopyarea crypto_simd cryptd glue_helper sysfillrect sysimgblt i2c_piix4 fb_sys_fops r8169 ahci libahci mii drm e1000e usbhid hid ptp pps_core
Oct 29 01:22:04 home-server kernel: [ 1204.854777] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./AM1H-ITX, BIOS P1.50 04/29/2015
Oct 29 01:22:04 home-server kernel: [ 1204.854789] RSP: 0018:ffff9d10fec03e58 EFLAGS: 00010286
Oct 29 01:22:04 home-server kernel: [ 1204.854797] RDX: 0000000000040400 RSI: 00000000000000f6 RDI: 0000000000000300
Oct 29 01:22:04 home-server kernel: [ 1204.854804] R10: ffff9d10fec03ee8 R11: 0000000000000000 R12: 0000000000000001
Oct 29 01:22:04 home-server kernel: [ 1204.854812] FS:  0000000000000000(0000) GS:ffff9d10fec00000(0000) knlGS:0000000000000000
Oct 29 01:22:04 home-server kernel: [ 1204.854819] CR2: 00007fff863fcf5c CR3: 000000029a0d4000 CR4: 00000000000406f0
Oct 29 01:22:04 home-server kernel: [ 1204.854828]  <IRQ>
Oct 29 01:22:04 home-server kernel: [ 1204.854850]  call_timer_fn+0x30/0x130
Oct 29 01:22:04 home-server kernel: [ 1204.854862]  ? ktime_get+0x43/0xa0
Oct 29 01:22:04 home-server kernel: [ 1204.854877]  __do_softirq+0xe4/0x2bb
Oct 29 01:22:04 home-server kernel: [ 1204.854891]  smp_apic_timer_interrupt+0x79/0x130
Oct 29 01:22:04 home-server kernel: [ 1204.854900]  </IRQ>
Oct 29 01:22:04 home-server kernel: [ 1204.854911] RSP: 0018:ffffffff9c603e10 EFLAGS: 00000246 ORIG_RAX: ffffffffffffff11
Oct 29 01:22:04 home-server kernel: [ 1204.854920] RDX: 0000011886eaca5e RSI: fffffffa4af077f4 RDI: 0000000000000000
Oct 29 01:22:04 home-server kernel: [ 1204.854927] R10: ffffffff9c603de0 R11: 0000000000000e92 R12: ffff9d10e67b3600
Oct 29 01:22:04 home-server kernel: [ 1204.854941]  cpuidle_enter+0x17/0x20
Oct 29 01:22:04 home-server kernel: [ 1204.854955]  do_idle+0x18c/0x1f0
Oct 29 01:22:04 home-server kernel: [ 1204.854969]  rest_init+0xae/0xb0
Oct 29 01:22:04 home-server kernel: [ 1204.854983]  x86_64_start_reservations+0x24/0x26
Oct 29 01:22:04 home-server kernel: [ 1204.854995]  secondary_startup_64+0xa5/0xb0
Oct 29 01:22:04 home-server kernel: [ 1204.855116] ---[ end trace d41bef67f41d6c1c ]---
Oct 29 01:22:04 home-server systemd-networkd[888]: enp4s0f1: Lost carrier
Oct 29 01:22:04 home-server systemd-networkd[888]: vlan10: Lost carrier
Oct 29 01:22:04 home-server systemd-networkd[888]: vlan30: Lost carrier
Oct 29 01:22:05 home-server systemd-networkd[888]: br30: Lost carrier
Oct 29 01:22:49 home-server kernel: [ 1249.912420] e1000e 0000:03:00.0 enp3s0f0: Reset adapter unexpectedly
Oct 29 01:22:49 home-server systemd-networkd[888]: enp3s0f0: Lost carrier
Oct 29 01:22:49 home-server systemd-networkd[888]: macvtap0: Lost carrier
Oct 29 01:24:09 home-server kernel: [ 1329.787086] e1000e 0000:04:00.0 enp4s0f0: Reset adapter unexpectedly
```

[SIZE=6]Update as of 10/29/18 6:16 PM Eastern Time[/SIZE]

Another round of logs:

```
Oct 26 22:15:17 home-server systemd-networkd[932]: enp4s0f0: Lost carrier
Oct 26 22:15:17 home-server kernel: [ 1671.911212] ------------[ cut here ]------------
Oct 26 22:15:17 home-server kernel: [ 1671.911220] NETDEV WATCHDOG: enp4s0f0 (e1000e): transmit queue 0 timed out
Oct 26 22:15:17 home-server kernel: [ 1671.911257] WARNING: CPU: 3 PID: 0 at /build/linux-39dmni/linux-4.15.0/net/sched/sch_generic.c:323 dev_watchdog+0x221/0x230
Oct 26 22:15:17 home-server kernel: [ 1671.911259] Modules linked in: macvtap vhost_net vhost tap devlink ebtable_filter ebtables veth 8021q garp mrp bridge stp llc ip6table_filter ip6_tables iptable_filter ipt_MASQUERADE nf_nat_masquerade_ipv4 iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack nls_iso8859_1 amd_freq_sensitivity edac_mce_amd kvm_amd kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec snd_hda_core input_leds fam15h_power snd_hwdep k10temp joydev snd_pcm snd_timer snd soundcore shpchp mac_hid sch_fq_codel ib_iser rdma_cm nfsd auth_rpcgss nfs_acl lockd grace iw_cm sunrpc ib_cm ib_core iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi macvlan ip_tables x_tables autofs4 btrfs zstd_compress raid10
Oct 26 22:15:17 home-server kernel: [ 1671.911340]  raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear amdgpu chash hid_generic radeon aesni_intel aes_x86_64 i2c_algo_bit crypto_simd usbhid cryptd glue_helper i2c_piix4 hid ttm e1000e r8169 mii ptp drm_kms_helper pps_core syscopyarea sysfillrect sysimgblt fb_sys_fops ahci drm libahci
Oct 26 22:15:17 home-server kernel: [ 1671.911386] CPU: 3 PID: 0 Comm: swapper/3 Not tainted 4.15.0-36-generic #39-Ubuntu
Oct 26 22:15:17 home-server kernel: [ 1671.911388] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./AM1H-ITX, BIOS P1.50 04/29/2015
Oct 26 22:15:17 home-server kernel: [ 1671.911393] RIP: 0010:dev_watchdog+0x221/0x230
Oct 26 22:15:17 home-server kernel: [ 1671.911395] RSP: 0018:ffff9f247ed83e58 EFLAGS: 00010286
Oct 26 22:15:17 home-server kernel: [ 1671.911399] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000000000006
Oct 26 22:15:17 home-server kernel: [ 1671.911401] RDX: 0000000000000007 RSI: 0000000000000092 RDI: ffff9f247ed96490
Oct 26 22:15:17 home-server kernel: [ 1671.911403] RBP: ffff9f247ed83e88 R08: 0000000000000001 R09: 0000000000000449
Oct 26 22:15:17 home-server kernel: [ 1671.911405] R10: ffff9f247ed83ee0 R11: 0000000000000000 R12: 0000000000000001
Oct 26 22:15:17 home-server kernel: [ 1671.911407] R13: ffff9f24653c0000 R14: ffff9f24653c0478 R15: ffff9f2465079080
Oct 26 22:15:17 home-server kernel: [ 1671.911410] FS:  0000000000000000(0000) GS:ffff9f247ed80000(0000) knlGS:0000000000000000
Oct 26 22:15:17 home-server kernel: [ 1671.911412] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 26 22:15:17 home-server kernel: [ 1671.911414] CR2: 0000000800bba980 CR3: 00000002cbf3c000 CR4: 00000000000406e0
Oct 26 22:15:17 home-server kernel: [ 1671.911417] Call Trace:
Oct 26 22:15:17 home-server kernel: [ 1671.911421]  <IRQ>
Oct 26 22:15:17 home-server kernel: [ 1671.911429]  ? dev_deactivate_queue.constprop.33+0x60/0x60
Oct 26 22:15:17 home-server kernel: [ 1671.911435]  call_timer_fn+0x30/0x130
Oct 26 22:15:17 home-server kernel: [ 1671.911440]  run_timer_softirq+0x3fb/0x450
Oct 26 22:15:17 home-server kernel: [ 1671.911444]  ? ktime_get+0x43/0xa0
Oct 26 22:15:17 home-server kernel: [ 1671.911449]  ? lapic_next_event+0x20/0x30
Oct 26 22:15:17 home-server kernel: [ 1671.911454]  __do_softirq+0xe4/0x2bb
Oct 26 22:15:17 home-server kernel: [ 1671.911460]  irq_exit+0xb8/0xc0
Oct 26 22:15:17 home-server kernel: [ 1671.911463]  smp_apic_timer_interrupt+0x79/0x130
Oct 26 22:15:17 home-server kernel: [ 1671.911467]  apic_timer_interrupt+0x84/0x90
Oct 26 22:15:17 home-server kernel: [ 1671.911468]  </IRQ>
Oct 26 22:15:17 home-server kernel: [ 1671.911473] RIP: 0010:native_safe_halt+0x6/0x10
Oct 26 22:15:17 home-server kernel: [ 1671.911475] RSP: 0018:ffffabbf4191fde8 EFLAGS: 00000246 ORIG_RAX: ffffffffffffff11
Oct 26 22:15:17 home-server kernel: [ 1671.911479] RAX: 0000000080000000 RBX: ffff9f2470997c00 RCX: 0000000000000034
Oct 26 22:15:17 home-server kernel: [ 1671.911481] RDX: 4ec4ec4ec4ec4ec5 RSI: ffffffff91b805c0 RDI: ffff9f2470997c64
Oct 26 22:15:17 home-server kernel: [ 1671.911482] RBP: ffffabbf4191fde8 R08: 00000000000000ad R09: 00000000000000a2
Oct 26 22:15:17 home-server kernel: [ 1671.911484] R10: ffffabbf4191fe38 R11: 00000000000000aa R12: ffff9f2470997c64
Oct 26 22:15:17 home-server kernel: [ 1671.911486] R13: 0000000000000001 R14: 0000000000000001 R15: 0000000000000000
Oct 26 22:15:17 home-server kernel: [ 1671.911493]  ? __next_timer_interrupt+0xae/0xe0
Oct 26 22:15:17 home-server kernel: [ 1671.911496]  acpi_safe_halt+0x20/0x30
Oct 26 22:15:17 home-server kernel: [ 1671.911500]  acpi_idle_do_entry+0x2f/0x40
Oct 26 22:15:17 home-server kernel: [ 1671.911504]  acpi_idle_enter+0x12f/0x2a0
Oct 26 22:15:17 home-server kernel: [ 1671.911511]  cpuidle_enter_state+0x74/0x2f0
Oct 26 22:15:17 home-server kernel: [ 1671.911515]  cpuidle_enter+0x17/0x20
Oct 26 22:15:17 home-server kernel: [ 1671.911520]  call_cpuidle+0x23/0x40
Oct 26 22:15:17 home-server kernel: [ 1671.911524]  do_idle+0x18c/0x1f0
Oct 26 22:15:17 home-server kernel: [ 1671.911527]  cpu_startup_entry+0x73/0x80
Oct 26 22:15:17 home-server kernel: [ 1671.911531]  start_secondary+0x1ab/0x200
Oct 26 22:15:17 home-server kernel: [ 1671.911536]  secondary_startup_64+0xa5/0xb0
Oct 26 22:15:17 home-server kernel: [ 1671.911539] Code: 38 00 49 63 4e e8 eb 92 4c 89 ef c6 05 59 e7 d8 00 01 e8 63 36 fd ff 89 d9 48 89 c2 4c 89 ee 48 c7 c7 48 90 79 91 e8 ff a6 80 ff <0f> 0b eb c0 90 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 44 00 00 55 
Oct 26 22:15:17 home-server kernel: [ 1671.911607] ---[ end trace dafee9f3c33e27cf ]---
Oct 26 22:15:17 home-server kernel: [ 1671.911639] e1000e 0000:04:00.0 enp4s0f0: Reset adapter unexpectedly
Oct 26 22:15:17 home-server kernel: [ 1671.912040] br10: port 1(enp4s0f0) entered disabled state
Oct 26 22:15:20 home-server kernel: [ 1673.959297] e1000e 0000:04:00.1 enp4s0f1: Reset adapter unexpectedly
```

[SIZE=6]Video:[/SIZE]

[https://www.youtube.com/watch?v=-_lJzS4eV_8](https://www.youtube.com/watch?v=-_lJzS4eV_8)

[SIZE=6]Summary:[/SIZE]

With all the information I have provided above, what can I do to resolve this issue? Please let me know if you need any more information as to help me solve the problem. In another note, I've had to wait 2 minutes per reboot due to "Waiting for network to be configured" message. I'll need to figure out what is going on behind-the-scenes. I'm wondering if I could increase a verbosity level to figure out why Netplan (or something else) is holding up.

I'm going to run an apt update after I do a reboot again. Been rebooting my server about 7 times already... Waiting for "Waiting for networking to be configured" about 2 minutes again...

Anyway, does my formatting help anyone gather information and try to help solve my issue at hand?

[SIZE=6]Updates[/SIZE]

[SIZE=4]1:07 AM:[/SIZE]

Shutdown of HP 4-Port Gigabit occurred again with the 4.15.0-38 kernel.

[SIZE=4]As of October 30, 12:03 AM EST[/SIZE]

Due to no responses in my thread, I have started my thread over at DSLReports.com.
[https://www.dslreports.com/forum/r32169640-HP-4-Port-Gigabit-NIC-and-e1000e-Adapter-Reset-Unexpectedly#32170046](https://www.dslreports.com/forum/r32169640-HP-4-Port-Gigabit-NIC-and-e1000e-Adapter-Reset-Unexpectedly#32170046)

So far, one advised me to swap out the card with a different card and one didn't read that I have an ASRock AM1H-ITX, which is an ITX motherboard. They also mentioned if I have tried other OSes besides Ubuntu Server 18.04. They mentioned Ubuntu Server 16.04, which is older than 18.04, but do have better drivers. Hmm... Maybe I should look into a possibility of trying Debian Testing as I need the latest LXC packages for my Linux containers and I run two KVM virtual machines. I can rule out overheating as overheating does not cause my HP 4-port gigabit card to shut down while still keeping my server running. So I thought I could suspect IRQ problems but according to /proc/interrupts, there are no conflicts. Each of the "enp" interfaces have their own IRQ numbers.

---

### Post by GraysonPeddie on 2018-10-30
It's been long that nobody has viewed my thread. Does anyone know of appropriate forum for getting help? I'm thinking about replacing Ubuntu 18.04 with Debian 9. Perhaps it might solve my problem. If not, then I'll have to wait for my birthday money to get a new 4-port card. PCIe x16 is the only slot in my Mini-ITX motherboard, so can't move the card to a different slot.

I apologize for bumping my thread, but I'm hoping to get attention from anyone.

Update: Tried Debian Stretch (4.9 Linux kernel) and Debian Testing (4.18) and both of them did not solve the problem. I'm out of ideas other than HP 4-Port Gigabit Card being a bad card...

---

### Post by GraysonPeddie on 2018-11-05
Solution: remove the burnt sticker from the 4-port Gigabit card and the problem is solved.

[IMG]https://i.dslr.net/syms/a9e4e8763e94a5a8a978f85cf947d2be.jpg[/IMG]
[IMG]https://i.dslr.net/syms/d919d6677ace4e84fbf8d1d8eb564168.jpg[/IMG]

---

