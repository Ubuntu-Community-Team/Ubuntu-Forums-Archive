---
title: "Thinkpad x61 sleep not working (10.04)"
date: 2010-05-02
forum: Hardware
---

### Post by guyspencer on 2010-05-02
When I try to put my x61 to sleep, either by Function+F4 or Suspend from the top bar, the sleep light (crescent shaped) flashes, but the system does not sleep.

---

### Post by sikli on 2010-05-04
I have the exact same problem. Started when I installed 10.04. Im on x61s. I cant resume at all, the scrren is blank and I have to do a hard reset.

---

### Post by thecount1 on 2010-05-06
ditto on a clean install from final release, fully updated,

worked fine under 9.10

---

### Post by sliverstorm on 2010-06-07
b-bump! I have a x61 tablet with the exact same problem.

---

### Post by colsandurz on 2010-06-15
I have the same problem too and [this]("http://ubuntuforums.org/showthread.php?t=1444822") thread didn't help :(

---

### Post by iskatyel on 2010-06-15
I too have the blinking sleepy moon of doom.  The backlight remains on, but the monitor goes black and the fan is still running.  Here is the relevant section of syslog:
```
Jun 15 18:13:58 skitalets anacron[2772]: Anacron 2.3 started on 2010-06-15
Jun 15 18:13:58 skitalets anacron[2772]: Normal exit (0 jobs run)
Jun 15 18:13:59 skitalets NetworkManager: <info>  Sleeping...
Jun 15 18:13:59 skitalets NetworkManager: <info>  (eth0): now unmanaged
Jun 15 18:13:59 skitalets NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Jun 15 18:13:59 skitalets NetworkManager: <info>  (eth0): cleaning up...
Jun 15 18:13:59 skitalets NetworkManager: <info>  (eth0): taking down device.
Jun 15 18:13:59 skitalets kernel: [ 4093.904097] usb 3-2: USB disconnect, address 2
Jun 15 18:13:59 skitalets kernel: [ 4093.904982] btusb_intr_complete: hci0 urb e11ed200 failed to resubmit (19)
Jun 15 18:13:59 skitalets kernel: [ 4093.904999] btusb_bulk_complete: hci0 urb e11ed700 failed to resubmit (19)
Jun 15 18:13:59 skitalets bluetoothd[1201]: HCI dev 0 down
Jun 15 18:13:59 skitalets bluetoothd[1201]: Adapter /org/bluez/1181/hci0 has been disabled
Jun 15 18:13:59 skitalets bluetoothd[1201]: Stopping security manager 0
Jun 15 18:13:59 skitalets kernel: [ 4093.905990] btusb_bulk_complete: hci0 urb e11ed880 failed to resubmit (19)
Jun 15 18:13:59 skitalets kernel: [ 4093.906129] btusb_send_frame: hci0 urb ddf04700 submission failed
Jun 15 18:13:59 skitalets NetworkManager: <info>  (wlan0): now unmanaged
Jun 15 18:13:59 skitalets NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 37)
Jun 15 18:13:59 skitalets NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Jun 15 18:14:00 skitalets bluetoothd[1201]: HCI dev 0 unregistered
Jun 15 18:14:00 skitalets bluetoothd[1201]: Unregister path: /org/bluez/1181/hci0
Jun 15 18:14:00 skitalets NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2197
Jun 15 18:14:00 skitalets kernel: [ 4094.209148] wlan0: deauthenticating from 00:13:10:78:09:5e by local choice (reason=3)
Jun 15 18:14:00 skitalets NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Jun 15 18:14:00 skitalets avahi-daemon[1185]: Withdrawing address record for 192.168.87.113 on wlan0.
Jun 15 18:14:00 skitalets avahi-daemon[1185]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.87.113.
Jun 15 18:14:00 skitalets avahi-daemon[1185]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 15 18:14:00 skitalets NetworkManager: <info>  (wlan0): cleaning up...
Jun 15 18:14:00 skitalets NetworkManager: <info>  (wlan0): taking down device.
Jun 15 18:14:00 skitalets avahi-daemon[1185]: Withdrawing address record for fe80::213:e8ff:feb1:2795 on wlan0.
Jun 15 18:14:00 skitalets wpa_supplicant[1337]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jun 15 18:14:00 skitalets kernel: [ 4094.299385] ------------[ cut here ]------------
Jun 15 18:14:00 skitalets kernel: [ 4094.299425] WARNING: at /build/buildd/linux-2.6.32/net/wireless/core.c:614 wdev_cleanup_work+0xa7/0xd0 [cfg80211]()
Jun 15 18:14:00 skitalets kernel: [ 4094.299432] Hardware name: 7764CTO
Jun 15 18:14:00 skitalets kernel: [ 4094.299436] Modules linked in: iptable_filter ip_tables x_tables nls_iso8859_1 nls_cp437 vfat fat binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev vboxnetadp vboxnetflt vboxdrv snd_hda_codec_analog snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm thinkpad_acpi snd_seq_dummy snd_seq_oss snd_seq_midi arc4 pcmcia snd_rawmidi mmc_block snd_seq_midi_event yenta_socket iwlagn snd_seq rsrc_nonstatic iwlcore snd_timer sdhci_pci pcmcia_core sdhci snd_seq_device mac80211 btusb ohci1394 snd ieee1394 snd_page_alloc psmouse e1000e cfg80211 bluetooth soundcore led_class serio_raw lp parport nvram sha256_generic aes_i586 aes_generic dm_crypt fbcon tileblit font bitblit softcursor vga16fb vgastate i915 drm_kms_helper drm intel_agp i2c_algo_bit agpgart video output
Jun 15 18:14:00 skitalets kernel: [ 4094.299596] Pid: 9, comm: events/0 Not tainted 2.6.32-22-generic #36-Ubuntu
Jun 15 18:14:00 skitalets kernel: [ 4094.299602] Call Trace:
Jun 15 18:14:00 skitalets kernel: [ 4094.299620]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
Jun 15 18:14:00 skitalets kernel: [ 4094.299640]  [<f8682ea7>] ? wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Jun 15 18:14:00 skitalets kernel: [ 4094.299660]  [<f8682ea7>] ? wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Jun 15 18:14:00 skitalets kernel: [ 4094.299669]  [<c014c41a>] warn_slowpath_null+0x1a/0x20
Jun 15 18:14:00 skitalets kernel: [ 4094.299689]  [<f8682ea7>] wdev_cleanup_work+0xa7/0xd0 [cfg80211]
Jun 15 18:14:00 skitalets kernel: [ 4094.299699]  [<c016369e>] run_workqueue+0x8e/0x150
Jun 15 18:14:00 skitalets kernel: [ 4094.299719]  [<f8682e00>] ? wdev_cleanup_work+0x0/0xd0 [cfg80211]
Jun 15 18:14:00 skitalets kernel: [ 4094.299729]  [<c01637e4>] worker_thread+0x84/0xe0
Jun 15 18:14:00 skitalets kernel: [ 4094.299739]  [<c0167740>] ? autoremove_wake_function+0x0/0x50
Jun 15 18:14:00 skitalets kernel: [ 4094.299748]  [<c0163760>] ? worker_thread+0x0/0xe0
Jun 15 18:14:00 skitalets kernel: [ 4094.299756]  [<c01674b4>] kthread+0x74/0x80
Jun 15 18:14:00 skitalets kernel: [ 4094.299764]  [<c0167440>] ? kthread+0x0/0x80
Jun 15 18:14:00 skitalets kernel: [ 4094.299773]  [<c0104087>] kernel_thread_helper+0x7/0x10
Jun 15 18:14:00 skitalets kernel: [ 4094.299780] ---[ end trace 292f52ab04ea2c9a ]---
Jun 15 18:14:00 skitalets vpnc[2696]: select: Interrupted system call
Jun 15 18:14:00 skitalets vpnc[2696]: terminated by signal: 15
Jun 15 18:14:00 skitalets NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jun 15 18:14:00 skitalets nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
```
To me it looks related to Network Manager, USB or bluetooth, but the kernel is clearly unhappy.  None of the ctrl+alt+f[0-12] does anything.  The only solution seems to be to hard power it off.  I'm going to experiment some more with disabling various bits and see if I can get it working.

---

### Post by iskatyel on 2010-06-16
Okay, everything is up-to-date and rebooted at the moment and I am able to get suspend working IF the SD card is not mounted.  It can be plugged in, but if it's mounted suspend will freeze the system with the blinking moon of death.

---

### Post by YossXP on 2010-06-29
[CENTER][LEFT][LEFT]@Iskatyel -  Thanks, you've just gave me the answer for my blinking moon of death..
any idea how to prevent Ubuntu from auto-mounting the SD card ? it's not  in the /etc/fstab

Thanks

[/LEFT]
[/LEFT]
[/CENTER]

---

