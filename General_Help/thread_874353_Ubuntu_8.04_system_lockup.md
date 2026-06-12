---
title: "Ubuntu 8.04 system lockup"
date: 2008-07-29
forum: General Help
---

### Post by thedevnull on 2008-07-29
Hey Everyone,

My patched as of today 07/29/08 Ubuntu Amd64 box is being "moody".  It seems to crash at random when I am listening to any MP3/OGG/Flac and the system completely locks.  Firefox is with some heavy ajax web apps sometimes running but there is no mention in any logs.  I am unable to get it to do anything at all - so I have to reboot.  Below are the /var/log/messages details....

EXAMPLE 1
Jul 25 23:36:31 oo pulseaudio[5936]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 25 23:36:31 oo pulseaudio[5936]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 25 23:36:31 oo pulseaudio[5936]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 22050 Hz.
Jul 25 23:36:31 oo pulseaudio[5936]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jul 25 23:53:27 oo -- MARK --
Jul 26 00:13:27 oo -- MARK --
Jul 26 00:17:34 oo kernel: [ 2126.248894] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Jul 26 00:17:34 oo kernel: [ 2126.248901] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Jul 26 00:17:34 oo kernel: [ 2126.444403] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Jul 26 00:17:34 oo kernel: [ 2126.444410] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Jul 26 00:17:35 oo kernel: [ 2127.047482] atkbd.c: Unknown key pressed (translated set 2, code 0xbf on isa0060/serio0).
Jul 26 00:17:35 oo kernel: [ 2127.047489] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Jul 26 00:17:35 oo kernel: [ 2127.305793] atkbd.c: Unknown key released (translated set 2, code 0xbf on isa0060/serio0).
Jul 26 00:17:35 oo kernel: [ 2127.305800] atkbd.c: Use 'setkeycodes e03f <keycode>' to make it known.
Jul 26 00:17:35 oo kernel: [ 2127.590910] atkbd.c: Unknown key pressed (translated set 2, code 0xc0 on isa0060/serio0).
Jul 26 00:17:35 oo kernel: [ 2127.590917] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Jul 26 00:17:35 oo kernel: [ 2127.865871] atkbd.c: Unknown key released (translated set 2, code 0xc0 on isa0060/serio0).
Jul 26 00:17:35 oo kernel: [ 2127.865877] atkbd.c: Use 'setkeycodes e040 <keycode>' to make it known.
Jul 26 00:33:27 oo -- MARK --
Jul 26 00:53:27 oo -- MARK --
Jul 26 01:13:27 oo -- MARK --
Jul 26 01:22:51 oo kernel: [ 5818.449446] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 26 01:22:53 oo exiting on signal 15
Jul 26 11:07:17 oo syslogd 1.5.0#1ubuntu1: restart.


EXAMPLE 2 -
Jul 26 11:07:24 oo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 26 11:07:24 oo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 26 11:07:24 oo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 26 11:07:24 oo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 26 11:07:26 oo kernel: [   45.791730] NET: Registered protocol family 10
Jul 26 11:07:26 oo kernel: [   45.791916] lo: Disabled Privacy Extensions
Jul 26 11:07:40 oo pulseaudio[5886]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 26 11:07:40 oo pulseaudio[5886]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 26 11:07:40 oo pulseaudio[5886]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 22050 Hz.
Jul 26 11:07:40 oo pulseaudio[5886]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jul 26 11:27:14 oo -- MARK --
Jul 26 11:32:30 oo syslogd 1.5.0#1ubuntu1: restart.
Jul 26 11:47:14 oo -- MARK --
Jul 26 12:07:14 oo -- MARK --
Jul 26 12:21:12 oo kernel: [ 2440.283865] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 26 12:21:14 oo exiting on signal 15


Any ideas?

---

### Post by Liquidtricity on 2008-08-15
Do you have a specialty sound card, or is this in a laptop? if so you may need to make sure that everything is configured correctly. Previously from what I have read in the past signal 15 exits normally have dealt with graphic drivers going ape, but it could be drivers in general.

---

