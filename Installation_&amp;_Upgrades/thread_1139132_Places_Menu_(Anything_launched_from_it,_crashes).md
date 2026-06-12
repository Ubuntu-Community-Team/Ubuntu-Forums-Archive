---
title: "Places Menu (Anything launched from it, crashes)"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by rip_it on 2009-04-26
For some reason, 2 days after I installed Jaunty 9.04, most everything in the "Places" menu wont launch. Tried opening "Documents", Pictures, now even my external harddrive wont launch.  Anyone else having this problem?
Im getting brasero errors in syslog and messages in the logfile viewer. 

Apr 26 20:30:09 jonathan kernel: [   13.429552] usbcore: registered new interface driver uvcvideo
Apr 26 20:30:09 jonathan kernel: [   13.429586] USB Video Class driver (v0.1.0)
Apr 26 20:30:09 jonathan kernel: [   13.511741] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 26 20:30:09 jonathan kernel: [   13.576912] usbcore: registered new interface driver snd-usb-audio
Apr 26 20:30:09 jonathan kernel: [   13.894182] lp: driver loaded but no devices found
Apr 26 20:30:09 jonathan kernel: [   13.941736] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgent XTreme 4115 PQ: 0 ANSI: 4
Apr 26 20:30:09 jonathan kernel: [   13.944591] sd 4:0:0:0: [sdc] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
Apr 26 20:30:09 jonathan kernel: [   13.946077] sd 4:0:0:0: [sdc] Write Protect is off
Apr 26 20:30:09 jonathan kernel: [   13.949521] sd 4:0:0:0: [sdc] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
Apr 26 20:30:09 jonathan kernel: [   13.952179] sd 4:0:0:0: [sdc] Write Protect is off
Apr 26 20:30:09 jonathan kernel: [   13.952195]  sdc: sdc1
Apr 26 20:30:09 jonathan kernel: [   13.969539] sd 4:0:0:0: [sdc] Attached SCSI disk
Apr 26 20:30:09 jonathan kernel: [   13.969635] sd 4:0:0:0: Attached scsi generic sg4 type 0
Apr 26 20:30:09 jonathan kernel: [   14.061542] Adding 9823708k swap on /dev/sdb5.  Priority:-1 extents:1 across:9823708k
Apr 26 20:30:09 jonathan kernel: [   14.627709] EXT3 FS on sdb1, internal journal
Apr 26 20:30:09 jonathan kernel: [   15.734288] type=1505 audit(1240792207.876:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2136
Apr 26 20:30:09 jonathan kernel: [   15.789540] type=1505 audit(1240792207.932:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2140
Apr 26 20:30:09 jonathan kernel: [   15.789670] type=1505 audit(1240792207.932:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2140
Apr 26 20:30:09 jonathan kernel: [   15.789723] type=1505 audit(1240792207.932:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2140
Apr 26 20:30:09 jonathan kernel: [   15.789772] type=1505 audit(1240792207.932:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2140
Apr 26 20:30:09 jonathan kernel: [   15.943265] type=1505 audit(1240792208.085:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2145
Apr 26 20:30:09 jonathan kernel: [   15.943452] type=1505 audit(1240792208.085:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2145
Apr 26 20:30:09 jonathan kernel: [   15.976678] type=1505 audit(1240792208.121:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2149
Apr 26 20:30:11 jonathan kernel: [   19.348505] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 26 20:30:11 jonathan kernel: [   19.348510] Bluetooth: BNEP filters: protocol multicast
Apr 26 20:30:11 jonathan kernel: [   19.380155] Bridge firewalling registered
Apr 26 20:30:12 jonathan kernel: [   20.655536] ppdev: user-space parallel port driver
Apr 26 20:30:17 jonathan kernel: [   24.874460] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 26 20:30:17 jonathan pulseaudio[3356]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Apr 26 20:30:20 jonathan kernel: [   27.874327] eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
Apr 26 20:30:27 jonathan kernel: [   35.178134] nautilus[3571]: segfault at 9494008 ip b5f9b7dd sp b5f89fc0 error 4 in libbrasero-media.so.0.1.1[b5f8b000+1e000]
Apr 26 20:32:53 jonathan kernel: [  181.586342] nautilus[3625]: segfault at 8962000 ip b5ef27dd sp b5ee0fc0 error 4 in libbrasero-media.so.0.1.1[b5ee2000+1e000]
Apr 26 20:35:23 jonathan kernel: [  331.090779] nautilus[3665]: segfault at 978f008 ip b5dd37dd sp b5dc1fc0 error 4 in libbrasero-media.so.0.1.1[b5dc3000+1e000]

I did run an update for Wine, and a bunch of others yesterday.

---

### Post by rip_it on 2009-04-27
Brascero the free cd burner in Ubuntu was causing the segfault crashes with Nautilus.  I just had to uninstall Brascero and everything is back to normal.  It was causing anything in the "Places' menu not to work.  And even videos like on cnn.com not to work.  Soon as I uninstalled, its all back to normal.

---

