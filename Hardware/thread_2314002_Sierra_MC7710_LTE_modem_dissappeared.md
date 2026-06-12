---
title: "Sierra MC7710 LTE modem dissappeared"
date: 2016-02-17
forum: Hardware
---

### Post by f-mike-y on 2016-02-17
Hello,


So, I have the MC7710 installed in my Thinkpad X230. For a while, I could see the modem in lsusb and lsmod grep sierra, although, I could never enable it. So, I unticked "Enable mobile broadband" in the network dropdown in the hopes that "switching it on and off again" would help, and now the modem has completely disappeared...


So, there are two problems really, the first is the missing modem and the second (when the first is fixed) is that I couldn't enable it. I'm a relatively new linux user, but have got my system setup ok, but this kind of stuff is outside my ability (I've searched the forums, and seen some AT commands, but I have no idea what they are or what a minicom is!), so I need some help. Here are some details:


uname -r
```
4.2.0-27-generic
```


rfkill list
```

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


lsusb
```

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 04f2:b2eb Chicony Electronics Co., Ltd 
Bus 003 Device 006: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller
Bus 001 Device 012: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 001 Device 011: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 010: ID 046d:0a44 Logitech, Inc. Wired headset
Bus 001 Device 009: ID 04a9:1747 Canon, Inc. 
Bus 001 Device 008: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 001 Device 007: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 006: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 001 Device 004: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


lsmod
```
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
hid_apple              16384  0
msr                    16384  0
usblp                  20480  0
hid_generic            16384  0
snd_usb_audio         176128  3
snd_usbmidi_lib        36864  1 snd_usb_audio
hid_sony               20480  0
ff_memless             16384  1 hid_sony
uvcvideo               90112  0
btusb                  45056  0
btrtl                  16384  1 btusb
videobuf2_vmalloc      16384  1 uvcvideo
btbcm                  16384  1 btusb
btintel                16384  1 btusb
videobuf2_memops       16384  1 videobuf2_vmalloc
bluetooth             516096  5 btbcm,btrtl,btusb,btintel
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
binfmt_misc            20480  1
pci_stub               16384  1
media                  24576  2 uvcvideo,videodev
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
qmi_wwan               24576  0
qcserial               20480  0
cdc_wdm                20480  1 qmi_wwan
usb_wwan               20480  1 qcserial
usbnet                 40960  1 qmi_wwan
mii                    16384  1 usbnet
usbserial              53248  2 qcserial,usb_wwan
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             167936  0
arc4                   16384  2
kvm                   512000  1 kvm_intel
crct10dif_pclmul       16384  0
iwldvm                233472  0
crc32_pclmul           16384  0
snd_hda_codec_hdmi     49152  1
mac80211              733184  1 iwldvm
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
joydev                 20480  0
input_leds             16384  0
iwlwifi               200704  1 iwldvm
serio_raw              16384  0
snd_hda_intel          36864  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_seq_midi           16384  0
cfg80211              548864  3 iwlwifi,mac80211,iwldvm
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
thinkpad_acpi          86016  1
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
nvram                  16384  1 thinkpad_acpi
snd_pcm               106496  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
shpchp                 36864  0
lpc_ich                24576  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
mei_me                 32768  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mei                    98304  1 mei_me
snd_timer              32768  2 snd_pcm,snd_seq
snd                    81920  26 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
soundcore              16384  1 snd
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_logitech_hidpp     20480  0
hid_logitech_dj        20480  0
usbhid                 49152  0
hid                   118784  7 hid_sony,hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp,hid_apple
i915                 1130496  6
i2c_algo_bit           16384  1 i915
psmouse               126976  0
drm_kms_helper        126976  1 i915
e1000e                237568  0
ahci                   36864  3
drm                   356352  8 i915,drm_kms_helper
libahci                32768  1 ahci
sdhci_pci              24576  0
ptp                    20480  1 e1000e
sdhci                  45056  1 sdhci_pci
pps_core               20480  1 ptp
wmi                    20480  0
video                  36864  2 i915,thinkpad_acpi




```

syslog after a restart and a sudo service network-manager restart
```

eb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[1]: Stopping User Manager for UID 119...
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Reached target Shutdown.
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Stopped target Default.
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Stopped target Basic System.
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Stopped target Sockets.
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Stopped target Timers.
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Stopped target Paths.
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Starting Exit the Session...
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[2768]: Received SIGRTMIN+24 from PID 8908 (kill).
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[1]: Stopped User Manager for UID 119.
Feb 17 21:49:08 mikepearce-ThinkPad-X230 systemd[1]: Removed slice user-119.slice.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 systemd[1]: Stopping Network Manager...
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  caught SIGTERM, shutting down normally.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  (wlp3s0): device state change: activated -> deactivating (reason 'unmanaged') [100 110 3]
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  (wlp3s0): device state change: deactivating -> unmanaged (reason 'unmanaged') [110 10 3]
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  (wlp3s0): canceled DHCP transaction, DHCP client pid 3411
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  (wlp3s0): DHCPv4 state changed bound -> done
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  (wlp3s0): canceled DHCP transaction
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Withdrawing address record for 192.168.0.72 on wlp3s0.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.72.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.957871] wlp3s0: deauthenticating from 7c:4c:a5:90:32:1d by local choice (Reason: 3=DEAUTH_LEAVING)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=7c:4c:a5:90:32:1d reason=3 locally_generated=1
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Withdrawing address record for fd66:82b3:b665:0:6e88:14ff:fe53:512c on wlp3s0.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fd66:82b3:b665:0:6e88:14ff:fe53:512c.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fd66:82b3:b665:0:e544:d554:2f3a:8d08.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Withdrawing address record for fd66:82b3:b665:0:e544:d554:2f3a:8d08 on wlp3s0.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fd66:82b3:b665:0:e544:d554:2f3a:8d08.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 avahi-daemon[970]: Interface wlp3s0.IPv6 no longer relevant for mDNS.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  Writing DNS information to /sbin/resolvconf
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dnsmasq[3089]: setting upstream servers from DBus
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver fd66:82b3:b665:0:7e4c:a5ff:fe90:321c#53
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987090] cfg80211: World regulatory domain updated:
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987095] cfg80211:  DFS Master region: unset
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987096] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987099] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987101] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987103] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987106] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987109] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987111] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987113] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 kernel: [  130.987115] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver fd66:82b3:b665:0:7e4c:a5ff:fe90:321c#53
Feb 17 21:49:11 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  Writing DNS information to /sbin/resolvconf
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dnsmasq[3089]: setting upstream servers from DBus
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver fd66:82b3:b665:0:7e4c:a5ff:fe90:321c#53
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dbus[881]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[839]: <info>  exiting (success)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 systemd[1]: Stopped Network Manager.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 systemd[1]: Starting Network Manager...
Feb 17 21:49:11 mikepearce-ThinkPad-X230 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 17 21:49:11 mikepearce-ThinkPad-X230 systemd[1]: Started Network Manager.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 gnome-session[3834]: (nm-applet:4086): GLib-CRITICAL **: Source ID 167 was not found when attempting to remove it
Feb 17 21:49:11 mikepearce-ThinkPad-X230 dbus[881]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 17 21:49:11 mikepearce-ThinkPad-X230 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  NetworkManager (version 1.0.4) is starting...
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Read config: /etc/NetworkManager/NetworkManager.conf
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  VPN: loaded org.freedesktop.NetworkManager.pptp
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  DNS: loaded plugin dnsmasq
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  init!
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  update_system_hostname
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>        interface-parser: parsing file /etc/network/interfaces
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>        interface-parser: finished parsing file /etc/network/interfaces
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  management mode: unmanaged
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25, iface: enp0s25)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25, iface: enp0s25): no ifupdown configuration found.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0, iface: wlp3s0)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0, iface: wlp3s0): no ifupdown configuration found.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  end _init.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded settings plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded settings plugin keyfile: (c) 2007 - 2015 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  SCPlugin-Ofono: init!
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <warn>  SCPlugin-Ofono: file doesn't exist: /var/lib/ofono
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  SCPlugin-Ofono: end _init.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded settings plugin ofono: (C) 2013 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ofono.so)
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (11541312) ... get_connections.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (11541312) ... get_connections (managed=false): return empty list.
Feb 17 21:49:11 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: nl80211: deinit ifname=wlp3s0 disabled_11b_rates=0
Feb 17 21:49:11 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  keyfile: new connection /etc/NetworkManager/system-connections/RRadio (444f984d-91a6-413c-a124-ee3c999a4b95,"RRadio")
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  keyfile: new connection /etc/NetworkManager/system-connections/Bumblebutt (e8781ae2-9659-4f2b-abb8-f3de44fa955c,"Bumblebutt")
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  keyfile: new connection /etc/NetworkManager/system-connections/Wintermute (c8047a6e-8e17-4491-8de4-78fe4135689f,"Wintermute")
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  SCPlugin-Ofono: (11299024) ... get_connections.
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  SCPlugin-Ofono: (11299024) connections count: 0
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  get unmanaged devices count: 0
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  monitoring kernel firmware directory '/lib/firmware'.
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  monitoring ifupdown state file '/run/network/ifstate'.
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill1) (driver iwlwifi)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMVxlanFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMVlanFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMVethFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMTunFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMMacvlanFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMInfinibandFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMGreFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMEthernetFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMBridgeFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMBondFactory (internal)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  WiFi enabled by radio killswitch; enabled by state file
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  WWAN enabled by radio killswitch; disabled by state file
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  WiMAX enabled by radio killswitch; enabled by state file
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Networking is enabled by state file
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): link connected
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): new Ethernet device (carrier: ON, driver: 'e1000e', ifindex: 2)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  keyfile: add connection in-memory (a9ac3e6a-4742-452f-8f1a-fea495598359,"enp0s25")
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  startup complete
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): Activation: starting connection 'enp0s25' (a9ac3e6a-4742-452f-8f1a-fea495598359)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (lo): link connected
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (lo): new Generic device (carrier: ON, driver: 'unknown', ifindex: 1)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): using nl80211 for WiFi device control
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): driver supports Access Point (AP) mode
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): new 802.11 WiFi device (carrier: UNKNOWN, driver: 'iwlwifi', ifindex: 3)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 kernel: [  131.094785] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 17 21:49:12 mikepearce-ThinkPad-X230 kernel: [  131.094993] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 17 21:49:12 mikepearce-ThinkPad-X230 kernel: [  131.101747] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 17 21:49:12 mikepearce-ThinkPad-X230 kernel: [  131.371951] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
Feb 17 21:49:12 mikepearce-ThinkPad-X230 kernel: [  131.378698] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 17 21:49:12 mikepearce-ThinkPad-X230 kernel: [  131.461294] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  urfkill disappeared from the bus
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  wpa_supplicant running
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Policy set 'enp0s25' (enp0s25) as default for IPv4 routing and DNS.
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Activation (enp0s25) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Feb 17 21:49:12 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: dbus: Failed to construct signal
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  dhclient started with pid 8953
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  ModemManager available in the bus
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  ofono is now available
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <warn>  failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): supplicant interface state: starting -> ready
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Device 'wlp3s0' has no connection; scheduling activate_check in 0 seconds.
Feb 17 21:49:12 mikepearce-ThinkPad-X230 kernel: [  131.548800] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 17 21:49:12 mikepearce-ThinkPad-X230 dhclient: DHCPDISCOVER on enp0s25 to 255.255.255.255 port 67 interval 3 (xid=0x2e00b914)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 dhclient: DHCPREQUEST of 192.168.0.71 on enp0s25 to 255.255.255.255 port 67 (xid=0x14b9002e)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 dhclient: DHCPOFFER of 192.168.0.71 from 192.168.0.1
Feb 17 21:49:12 mikepearce-ThinkPad-X230 dhclient: DHCPACK of 192.168.0.71 from 192.168.0.1
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    address 192.168.0.71
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    plen 24 (255.255.255.0)
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    gateway 192.168.0.1
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    server identifier 192.168.0.1
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    lease time 86400
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    nameserver '192.168.0.1'
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    domain name 'Home'
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): DHCPv4 state changed unknown -> bound
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): device state change: secondaries -> activated (reason 'none') [90 100 0]
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  NetworkManager state is now CONNECTED_SITE
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Feb 17 21:49:12 mikepearce-ThinkPad-X230 dhclient: bound to 192.168.0.71 -- renewal in 32617 seconds.
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Writing DNS information to /sbin/resolvconf
Feb 17 21:49:12 mikepearce-ThinkPad-X230 dnsmasq[3089]: setting upstream servers from DBus
Feb 17 21:49:12 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:12 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): Activation: successful, device activated.
Feb 17 21:49:12 mikepearce-ThinkPad-X230 nm-dispatcher: Dispatching action 'up' for enp0s25
Feb 17 21:49:13 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Activation (enp0s25) Beginning DHCPv6 transaction (timeout in 45 seconds)
Feb 17 21:49:13 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  dhclient started with pid 9082
Feb 17 21:49:13 mikepearce-ThinkPad-X230 dhclient: XMT: Info-Request on enp0s25, interval 1020ms.
Feb 17 21:49:14 mikepearce-ThinkPad-X230 dhclient: RCV: Reply message on enp0s25 from fe80::7e4c:a5ff:fe90:321c.
Feb 17 21:49:14 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    nameserver 'fd66:82b3:b665:0:7e4c:a5ff:fe90:321c'
Feb 17 21:49:14 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): DHCPv6 state changed unknown -> bound
Feb 17 21:49:14 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Writing DNS information to /sbin/resolvconf
Feb 17 21:49:14 mikepearce-ThinkPad-X230 dnsmasq[3089]: setting upstream servers from DBus
Feb 17 21:49:14 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:14 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver fd66:82b3:b665:0:7e4c:a5ff:fe90:321c#53
Feb 17 21:49:14 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): DHCPv6 client pid 9082 exited with status 0
Feb 17 21:49:14 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (enp0s25): DHCPv6 state changed bound -> done
Feb 17 21:49:14 mikepearce-ThinkPad-X230 nm-dispatcher: Dispatching action 'dhcp6-change' for enp0s25
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): supplicant interface state: ready -> inactive
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Auto-activating connection 'Wintermute'.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): Activation: starting connection 'Wintermute' (c8047a6e-8e17-4491-8de4-78fe4135689f)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): Activation: (wifi) connection 'Wintermute' has security, and secrets exist.  No new secrets needed.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Config: added 'ssid' value 'Wintermute'
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Config: added 'scan_ssid' value '1'
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Config: added 'auth_alg' value 'OPEN'
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Config: added 'psk' value '<omitted>'
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Config: set interface ap_scan to 1
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.719329] wlp3s0: authenticate with 7c:4c:a5:90:32:1d
Feb 17 21:49:15 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: SME: Trying to authenticate with 7c:4c:a5:90:32:1d (SSID='Wintermute' freq=2457 MHz)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.721477] wlp3s0: send auth to 7c:4c:a5:90:32:1d (try 1/3)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: Trying to associate with 7c:4c:a5:90:32:1d (SSID='Wintermute' freq=2457 MHz)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): supplicant interface state: inactive -> authenticating
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.724268] wlp3s0: authenticated
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.727789] wlp3s0: associate with 7c:4c:a5:90:32:1d (try 1/3)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.731799] wlp3s0: RX AssocResp from 7c:4c:a5:90:32:1d (capab=0x1411 status=0 aid=2)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: Associated with 7c:4c:a5:90:32:1d
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.749971] wlp3s0: associated
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.750032] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754826] cfg80211: Regulatory domain changed to country: DE
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754831] cfg80211:  DFS Master region: ETSI
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754833] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754837] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754840] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754843] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754846] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.754848] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=DE
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): supplicant interface state: associating -> 4-way handshake
Feb 17 21:49:15 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: WPA: Key negotiation completed with 7c:4c:a5:90:32:1d [PTK=CCMP GTK=TKIP]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 wpa_supplicant[2699]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 7c:4c:a5:90:32:1d completed [id=0 id_str=]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Wintermute'.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Activation (wlp3s0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  dhclient started with pid 9113
Feb 17 21:49:15 mikepearce-ThinkPad-X230 kernel: [  134.772842] wlp3s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 7c:4c:a5:90:32:1d
Feb 17 21:49:15 mikepearce-ThinkPad-X230 dhclient: DHCPREQUEST of 192.168.0.72 on wlp3s0 to 255.255.255.255 port 67 (xid=0x12affb35)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 dhclient: DHCPACK of 192.168.0.72 from 192.168.0.1
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    address 192.168.0.72
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    plen 24 (255.255.255.0)
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    gateway 192.168.0.1
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    server identifier 192.168.0.1
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    lease time 86400
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    nameserver '192.168.0.1'
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    domain name 'Home'
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): DHCPv4 state changed unknown -> bound
Feb 17 21:49:15 mikepearce-ThinkPad-X230 avahi-daemon[970]: Joining mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.72.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 avahi-daemon[970]: New relevant interface wlp3s0.IPv4 for mDNS.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 avahi-daemon[970]: Registering new address record for 192.168.0.72 on wlp3s0.IPv4.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 dhclient: bound to 192.168.0.72 -- renewal in 42937 seconds.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Writing DNS information to /sbin/resolvconf
Feb 17 21:49:15 mikepearce-ThinkPad-X230 dnsmasq[3089]: setting upstream servers from DBus
Feb 17 21:49:15 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:15 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver fd66:82b3:b665:0:7e4c:a5ff:fe90:321c#53
Feb 17 21:49:15 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:15 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): Activation: successful, device activated.
Feb 17 21:49:15 mikepearce-ThinkPad-X230 nm-dispatcher: Dispatching action 'up' for wlp3s0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_get_uint32: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_UINT32)' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_get_uint32: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_UINT32)' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_get_type: assertion 'value != NULL' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_type_is_subtype_of: assertion 'g_variant_type_check (type)' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_get_uint32: assertion 'g_variant_is_of_type (value, G_VARIANT_TYPE_UINT32)' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: (whoopsie:817): GLib-CRITICAL **: g_variant_unref: assertion 'value != NULL' failed
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:16 mikepearce-ThinkPad-X230 whoopsie[817]: [21:49:16] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Feb 17 21:49:17 mikepearce-ThinkPad-X230 avahi-daemon[970]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::6e88:14ff:fe53:512c.
Feb 17 21:49:17 mikepearce-ThinkPad-X230 avahi-daemon[970]: New relevant interface wlp3s0.IPv6 for mDNS.
Feb 17 21:49:17 mikepearce-ThinkPad-X230 avahi-daemon[970]: Registering new address record for fe80::6e88:14ff:fe53:512c on wlp3s0.*.
Feb 17 21:49:18 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Activation (wlp3s0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Feb 17 21:49:18 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  dhclient started with pid 9242
Feb 17 21:49:18 mikepearce-ThinkPad-X230 dhclient: XMT: Info-Request on wlp3s0, interval 920ms.
Feb 17 21:49:18 mikepearce-ThinkPad-X230 dhclient: RCV: Reply message on wlp3s0 from fe80::7e4c:a5ff:fe90:321c.
Feb 17 21:49:18 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>    nameserver 'fd66:82b3:b665:0:7e4c:a5ff:fe90:321c'
Feb 17 21:49:18 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): DHCPv6 state changed unknown -> bound
Feb 17 21:49:18 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  Writing DNS information to /sbin/resolvconf
Feb 17 21:49:18 mikepearce-ThinkPad-X230 dnsmasq[3089]: setting upstream servers from DBus
Feb 17 21:49:18 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:18 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver fd66:82b3:b665:0:7e4c:a5ff:fe90:321c#53
Feb 17 21:49:18 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver 192.168.0.1#53
Feb 17 21:49:18 mikepearce-ThinkPad-X230 dnsmasq[3089]: using nameserver fd66:82b3:b665:0:7e4c:a5ff:fe90:321c#53
Feb 17 21:49:18 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): DHCPv6 client pid 9242 exited with status 0
Feb 17 21:49:18 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  (wlp3s0): DHCPv6 state changed bound -> done
Feb 17 21:49:18 mikepearce-ThinkPad-X230 nm-dispatcher: Dispatching action 'dhcp6-change' for wlp3s0
Feb 17 21:49:19 mikepearce-ThinkPad-X230 avahi-daemon[970]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fe80::6e88:14ff:fe53:512c.
Feb 17 21:49:19 mikepearce-ThinkPad-X230 avahi-daemon[970]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fd66:82b3:b665:0:6e88:14ff:fe53:512c.
Feb 17 21:49:19 mikepearce-ThinkPad-X230 avahi-daemon[970]: Registering new address record for fd66:82b3:b665:0:6e88:14ff:fe53:512c on wlp3s0.*.
Feb 17 21:49:19 mikepearce-ThinkPad-X230 avahi-daemon[970]: Withdrawing address record for fe80::6e88:14ff:fe53:512c on wlp3s0.
Feb 17 21:49:20 mikepearce-ThinkPad-X230 avahi-daemon[970]: Registering new address record for fd66:82b3:b665:0:e544:d554:2f3a:8d08 on wlp3s0.*.
Feb 17 21:49:22 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  WiFi hardware radio set enabled
Feb 17 21:49:22 mikepearce-ThinkPad-X230 NetworkManager[8941]: <info>  WWAN hardware radio set disabled


```

dmesg
```

[    0.000000] ACPI: APIC 0x00000000DAFE3000 000098 (v01 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: MCFG 0x00000000DAFE2000 00003C (v01 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: ECDT 0x00000000DAFE1000 000052 (v01 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: FPDT 0x00000000DAFE0000 000064 (v01 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: ASF! 0x00000000DAFE7000 0000A5 (v32 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: UEFI 0x00000000DAFDF000 00003E (v01 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: UEFI 0x00000000DAFDE000 000042 (v01 PTL    COMBUF   00000001 PTL  00000001)
[    0.000000] ACPI: POAT 0x00000000DAFDD000 000055 (v03 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: SSDT 0x00000000DAFDC000 000C79 (v01 PmRef  Cpu0Ist  00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 0x00000000DAFDB000 000A83 (v01 PmRef  CpuPm    00003000 INTL 20061109)
[    0.000000] ACPI: DMAR 0x00000000DAFDA000 0000B8 (v01 INTEL  SNB      00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 0x00000000DAFD9000 0002A6 (v01 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: DBG2 0x00000000DAFD8000 0000E9 (v00 LENOVO TP-G2    00002520 PTL  00000002)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad X230
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021e5fffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x21e5f4000-0x21e5f8fff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216000000-ffff88021dbfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000021e5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009cfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
[    0.000000]   node   0: [mem 0x0000000020200000-0x0000000040003fff]
[    0.000000]   node   0: [mem 0x0000000040005000-0x00000000cec30fff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000021e5fffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000021e5fffff]
[    0.000000] On node 0 totalpages: 2019276
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13161 pages used for memmap
[    0.000000]   DMA32 zone: 842288 pages, LIFO batch:31
[    0.000000]   Normal zone: 18328 pages used for memmap
[    0.000000]   Normal zone: 1172992 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0xdba00000-0xdf9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcec31000-0xdae9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdae9f000-0xdaf9efff]
[    0.000000] PM: Registered nosave memory: [mem 0xdaf9f000-0xdaffefff]
[    0.000000] PM: Registered nosave memory: [mem 0xdafff000-0xdf9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdfa00000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed07fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed08000-0xfed08fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed09000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffbfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc00000-0xffffffff]
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88021e200000 s96728 r8192 d30248 u262144
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1987702
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-27-generic root=UUID=50f55f80-d6d6-4ca2-9c6b-4e13bd608d9c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7833508K/8077104K available (8154K kernel code, 1238K rwdata, 3804K rodata, 1460K init, 1292K bss, 243596K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2594.152 MHz processor
[    0.000032] Calibrating delay loop (skipped), value calculated using timer frequency.. 5188.30 BogoMIPS (lpj=10376608)
[    0.000035] pid_max: default: 32768 minimum: 301
[    0.000039] ACPI: Core revision 20150619
[    0.011092] ACPI: All ACPI Tables successfully acquired
[    0.011109] Security Framework initialized
[    0.011118] AppArmor: AppArmor initialized
[    0.011119] Yama: becoming mindful.
[    0.011585] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.013482] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.014324] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.014334] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.014516] Initializing cgroup subsys blkio
[    0.014518] Initializing cgroup subsys memory
[    0.014524] Initializing cgroup subsys devices
[    0.014527] Initializing cgroup subsys freezer
[    0.014528] Initializing cgroup subsys net_cls
[    0.014530] Initializing cgroup subsys perf_event
[    0.014532] Initializing cgroup subsys net_prio
[    0.014533] Initializing cgroup subsys hugetlb
[    0.014554] CPU: Physical Processor ID: 0
[    0.014555] CPU: Processor Core ID: 0
[    0.014559] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.014560] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.014901] mce: CPU supports 7 MCE banks
[    0.014911] CPU0: Thermal monitoring enabled (TM1)
[    0.014916] process: using mwait in idle threads
[    0.014919] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.014920] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.015323] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.018236] ftrace: allocating 30933 entries in 121 pages
[    0.031935] DMAR: Host address width 36
[    0.031938] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.031943] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.031945] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.031948] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.031949] DMAR: RMRR base: 0x000000da2ba000 end: 0x000000da2d0fff
[    0.031950] DMAR: RMRR base: 0x000000db800000 end: 0x000000df9fffff
[    0.031952] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.031953] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.031954] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.032234] DMAR-IR: Enabled IRQ remapping in x2apic mode
[    0.032236] x2apic enabled
[    0.032244] Switched APIC routing to cluster x2apic.
[    0.032703] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072422] TSC deadline timer enabled
[    0.072425] smpboot: CPU0: Intel(R) Core(TM) i5-3320M CPU @ 2.60GHz (fam: 06, model: 3a, stepping: 09)
[    0.072449] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.072468] ... version:                3
[    0.072469] ... bit width:              48
[    0.072470] ... generic registers:      4
[    0.072471] ... value mask:             0000ffffffffffff
[    0.072471] ... max period:             0000ffffffffffff
[    0.072472] ... fixed-purpose events:   3
[    0.072473] ... event mask:             000000070000000f
[    0.073213] x86: Booting SMP configuration:
[    0.073214] .... node  #0, CPUs:      #1
[    0.076849] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076939]  #2
[    0.078288] microcode: CPU2 microcode updated early to revision 0x1b, date = 2014-05-29
[    0.080855]  #3
[    0.084287] x86: Booted up 1 node, 4 CPUs
[    0.084290] smpboot: Total of 4 processors activated (20753.21 BogoMIPS)
[    0.087406] devtmpfs: initialized
[    0.090258] evm: security.selinux
[    0.090259] evm: security.SMACK64
[    0.090260] evm: security.SMACK64EXEC
[    0.090260] evm: security.SMACK64TRANSMUTE
[    0.090261] evm: security.SMACK64MMAP
[    0.090262] evm: security.ima
[    0.090263] evm: security.capability
[    0.090317] PM: Registering ACPI NVS region [mem 0xdae9f000-0xdaf9efff] (1048576 bytes)
[    0.090398] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.090469] pinctrl core: initialized pinctrl subsystem
[    0.090574] RTC time: 21:47:01, date: 02/17/16
[    0.090672] NET: Registered protocol family 16
[    0.095247] cpuidle: using governor ladder
[    0.099250] cpuidle: using governor menu
[    0.099350] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.099352] ACPI: bus type PCI registered
[    0.099353] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.099546] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.099549] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.099554] PCI: Using configuration type 1 for base access
[    0.099765] perf_event_intel: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.103582] ACPI: Added _OSI(Module Device)
[    0.103584] ACPI: Added _OSI(Processor Device)
[    0.103585] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.103586] ACPI: Added _OSI(Processor Aggregator Device)
[    0.103587] ACPI: Deleted _OSI(Windows 2012)
[    0.104862] ACPI : EC: EC description table is found, configuring boot EC
[    0.104875] ACPI : EC: EC started
[    0.108473] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.111897] ACPI: Dynamic OEM Table Load:
[    0.111908] ACPI: SSDT 0xFFFF880214530000 000A01 (v01 PmRef  Cpu0Cst  00003001 INTL 20061109)
[    0.112389] ACPI: Dynamic OEM Table Load:
[    0.112397] ACPI: SSDT 0xFFFF880214520C00 000303 (v01 PmRef  ApIst    00003000 INTL 20061109)
[    0.112824] ACPI: Dynamic OEM Table Load:
[    0.112830] ACPI: SSDT 0xFFFF880214538000 000119 (v01 PmRef  ApCst    00003000 INTL 20061109)
[    0.113629] ACPI: Interpreter enabled
[    0.113634] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.113638] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.113649] ACPI: (supports S0 S3 S4 S5)
[    0.113650] ACPI: Using IOAPIC for interrupt routing
[    0.113670] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.116192] ACPI: Power Resource [PUBS] (on)
[    0.116742] acpi PNP0C0A:01: ACPI dock station (docks/bays count: 1)
[    0.117619] acpi LNXIOBAY:00: ACPI dock station (docks/bays count: 2)
[    0.119696] acpi IBM0079:00: ACPI dock station (docks/bays count: 3)
[    0.120060] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.120130] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11)
[    0.120199] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.120267] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11)
[    0.120333] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.120402] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 9 10 11)
[    0.120470] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11)
[    0.120538] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11)
[    0.120612] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.120616] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.120706] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
[    0.120746] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
[    0.120748] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
[    0.120750] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
[    0.120751] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
[    0.120886] PCI host bridge to bus 0000:00
[    0.120889] pci_bus 0000:00: root bus resource [bus 00-3f]
[    0.120890] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.120892] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.120894] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.120895] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfebfffff window]
[    0.120897] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed4bfff window]
[    0.120903] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.120974] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.120985] pci 0000:00:02.0: reg 0x10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.120991] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.120995] pci 0000:00:02.0: reg 0x20: [io  0x5000-0x503f]
[    0.121074] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.121104] pci 0000:00:14.0: reg 0x10: [mem 0xf2520000-0xf252ffff 64bit]
[    0.121158] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.121184] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.121223] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.121254] pci 0000:00:16.0: reg 0x10: [mem 0xf2535000-0xf253500f 64bit]
[    0.121312] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.121369] pci 0000:00:16.3: [8086:1e3d] type 00 class 0x070002
[    0.121395] pci 0000:00:16.3: reg 0x10: [io  0x50b0-0x50b7]
[    0.121405] pci 0000:00:16.3: reg 0x14: [mem 0xf253c000-0xf253cfff]
[    0.121509] pci 0000:00:19.0: [8086:1502] type 00 class 0x020000
[    0.121534] pci 0000:00:19.0: reg 0x10: [mem 0xf2500000-0xf251ffff]
[    0.121543] pci 0000:00:19.0: reg 0x14: [mem 0xf253b000-0xf253bfff]
[    0.121551] pci 0000:00:19.0: reg 0x18: [io  0x5080-0x509f]
[    0.121595] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.121618] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.121655] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.121682] pci 0000:00:1a.0: reg 0x10: [mem 0xf253a000-0xf253a3ff]
[    0.121748] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.121774] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.121810] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.121836] pci 0000:00:1b.0: reg 0x10: [mem 0xf2530000-0xf2533fff 64bit]
[    0.121895] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.121925] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.121964] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.122078] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.122149] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.122264] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.122334] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.122445] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.122479] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.122518] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.122547] pci 0000:00:1d.0: reg 0x10: [mem 0xf2539000-0xf25393ff]
[    0.122613] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.122641] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.122675] pci 0000:00:1f.0: [8086:1e55] type 00 class 0x060100
[    0.122820] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.122843] pci 0000:00:1f.2: reg 0x10: [io  0x50a8-0x50af]
[    0.122850] pci 0000:00:1f.2: reg 0x14: [io  0x50bc-0x50bf]
[    0.122858] pci 0000:00:1f.2: reg 0x18: [io  0x50a0-0x50a7]
[    0.122866] pci 0000:00:1f.2: reg 0x1c: [io  0x50b8-0x50bb]
[    0.122873] pci 0000:00:1f.2: reg 0x20: [io  0x5060-0x507f]
[    0.122880] pci 0000:00:1f.2: reg 0x24: [mem 0xf2538000-0xf25387ff]
[    0.122906] pci 0000:00:1f.2: PME# supported from D3hot
[    0.122958] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.122975] pci 0000:00:1f.3: reg 0x10: [mem 0xf2534000-0xf25340ff 64bit]
[    0.122996] pci 0000:00:1f.3: reg 0x20: [io  0xefa0-0xefbf]
[    0.123180] pci 0000:02:00.0: [1180:e822] type 00 class 0x088001
[    0.123227] pci 0000:02:00.0: MMC controller base frequency changed to 50Mhz.
[    0.123254] pci 0000:02:00.0: reg 0x10: [mem 0xf1d00000-0xf1d000ff]
[    0.123419] pci 0000:02:00.0: supports D1 D2
[    0.123421] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.132989] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.132994] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.132999] pci 0000:00:1c.0:   bridge window [mem 0xf1d00000-0xf24fffff]
[    0.133007] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.133213] pci 0000:03:00.0: [8086:0085] type 00 class 0x028000
[    0.133485] pci 0000:03:00.0: reg 0x10: [mem 0xf1c00000-0xf1c01fff 64bit]
[    0.134060] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.140950] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.140957] pci 0000:00:1c.1:   bridge window [mem 0xf1c00000-0xf1cfffff]
[    0.141046] acpiphp: Slot [1] registered
[    0.141055] pci 0000:00:1c.2: PCI bridge to [bus 04-0b]
[    0.141060] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.141065] pci 0000:00:1c.2:   bridge window [mem 0xf1400000-0xf1bfffff]
[    0.141072] pci 0000:00:1c.2:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.141999] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.142055] ACPI : EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.142153] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.142155] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.142157] vgaarb: loaded
[    0.142158] vgaarb: bridge control possible 0000:00:02.0
[    0.142348] SCSI subsystem initialized
[    0.142389] libata version 3.00 loaded.
[    0.142409] ACPI: bus type USB registered
[    0.142425] usbcore: registered new interface driver usbfs
[    0.142432] usbcore: registered new interface driver hub
[    0.142447] usbcore: registered new device driver usb
[    0.142586] PCI: Using ACPI for IRQ routing
[    0.144285] PCI: pci_cache_line_size set to 64 bytes
[    0.144831] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.144833] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.144834] e820: reserve RAM buffer [mem 0xcec31000-0xcfffffff]
[    0.144835] e820: reserve RAM buffer [mem 0x21e600000-0x21fffffff]
[    0.144936] NetLabel: Initializing
[    0.144937] NetLabel:  domain hash size = 128
[    0.144938] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.144948] NetLabel:  unlabeled traffic allowed by default
[    0.145018] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.145023] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.147052] clocksource: Switched to clocksource hpet
[    0.152099] AppArmor: AppArmor Filesystem Enabled
[    0.152165] pnp: PnP ACPI init
[    0.152524] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.152526] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.152528] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.152529] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.152531] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.152532] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.152534] system 00:00: [mem 0x000d4000-0x000d7fff] has been reserved
[    0.152535] system 00:00: [mem 0x000d8000-0x000dbfff] has been reserved
[    0.152537] system 00:00: [mem 0x000dc000-0x000dffff] has been reserved
[    0.152538] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.152540] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.152541] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.152543] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.152544] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.152546] system 00:00: [mem 0x00100000-0xdf9fffff] could not be reserved
[    0.152548] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.152549] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
[    0.152553] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.152626] pnp 00:01: [Firmware Bug]: PNP resource [mem 0xfed10000-0xfed13fff] covers only part of 0000:00:00.0 Intel MCH; extending to [mem 0xfed10000-0xfed17fff]
[    0.152645] system 00:01: [io  0x0400-0x047f] could not be reserved
[    0.152647] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.152648] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.152650] system 00:01: [io  0x15e0-0x15ef] has been reserved
[    0.152652] system 00:01: [io  0x1600-0x167f] has been reserved
[    0.152654] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.152656] system 00:01: [mem 0xfffff000-0xffffffff] has been reserved
[    0.152658] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.152659] system 00:01: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.152661] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.152663] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.152664] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.152667] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.152708] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.152728] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.152746] pnp 00:04: Plug and Play ACPI device, IDs LEN0020 PNP0f13 (active)
[    0.152786] pnp 00:05: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.153307] pnp: PnP ACPI: found 6 devices
[    0.159663] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.159707] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.159713] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.159720] pci 0000:00:1c.0:   bridge window [mem 0xf1d00000-0xf24fffff]
[    0.159725] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.159734] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.159740] pci 0000:00:1c.1:   bridge window [mem 0xf1c00000-0xf1cfffff]
[    0.159752] pci 0000:00:1c.2: PCI bridge to [bus 04-0b]
[    0.159755] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.159761] pci 0000:00:1c.2:   bridge window [mem 0xf1400000-0xf1bfffff]
[    0.159765] pci 0000:00:1c.2:   bridge window [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.159775] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.159776] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.159778] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.159780] pci_bus 0000:00: resource 7 [mem 0xdfa00000-0xfebfffff window]
[    0.159781] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed4bfff window]
[    0.159783] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.159784] pci_bus 0000:02: resource 1 [mem 0xf1d00000-0xf24fffff]
[    0.159786] pci_bus 0000:02: resource 2 [mem 0xf0400000-0xf0bfffff 64bit pref]
[    0.159787] pci_bus 0000:03: resource 1 [mem 0xf1c00000-0xf1cfffff]
[    0.159789] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.159790] pci_bus 0000:04: resource 1 [mem 0xf1400000-0xf1bfffff]
[    0.159792] pci_bus 0000:04: resource 2 [mem 0xf0c00000-0xf13fffff 64bit pref]
[    0.159820] NET: Registered protocol family 2
[    0.159962] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.160094] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.160201] TCP: Hash tables configured (established 65536 bind 65536)
[    0.160224] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.160249] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.160302] NET: Registered protocol family 1
[    0.160318] pci 0000:00:02.0: Video device with shadowed ROM
[    0.160872] PCI: CLS 64 bytes, default 64
[    0.160920] Trying to unpack rootfs image as initramfs...
[    0.623265] Freeing initrd memory: 32784K (ffff880033fe8000 - ffff880035fec000)
[    0.623290] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.623292] software IO TLB [mem 0xcac31000-0xcec31000] (64MB) mapped at [ffff8800cac31000-ffff8800cec30fff]
[    0.623389] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.623390] hw unit of domain pp0-core 2^-16 Joules
[    0.623391] hw unit of domain package 2^-16 Joules
[    0.623391] hw unit of domain pp1-gpu 2^-16 Joules
[    0.623504] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x1b
[    0.623513] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x1b
[    0.623522] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x1b
[    0.623529] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x1b
[    0.623576] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.623652] Scanning for low memory corruption every 60 seconds
[    0.623992] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.624013] Initialise system trusted keyring
[    0.624036] audit: initializing netlink subsys (disabled)
[    0.624048] audit: type=2000 audit(1455745620.616:1): initialized
[    0.624379] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.625627] zpool: loaded
[    0.625628] zbud: loaded
[    0.625791] VFS: Disk quotas dquot_6.6.0
[    0.625819] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.626223] fuse init (API version 7.23)
[    0.626349] Key type big_key registered
[    0.626703] Key type asymmetric registered
[    0.626706] Asymmetric key parser 'x509' registered
[    0.626719] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.626761] io scheduler noop registered
[    0.626764] io scheduler deadline registered (default)
[    0.626802] io scheduler cfq registered
[    0.627242] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.627248] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.627275] vesafb: mode is 1366x768x32, linelength=5504, pages=0
[    0.627276] vesafb: scrolling: redraw
[    0.627278] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.627287] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90001000000, using 4160k, total 4160k
[    0.627396] Console: switching to colour frame buffer device 170x48
[    0.627412] fb0: VESA VGA frame buffer device
[    0.627429] intel_idle: MWAIT substates: 0x21120
[    0.627430] intel_idle: v0.4 model 0x3A
[    0.627431] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.627718] ACPI: AC Adapter [AC] (on-line)
[    0.627773] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.627883] ACPI: Lid Switch [LID]
[    0.627915] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.627918] ACPI: Sleep Button [SLPB]
[    0.627953] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.627955] ACPI: Power Button [PWRF]
[    0.629086] thermal LNXTHERM:00: registered as thermal_zone0
[    0.629088] ACPI: Thermal Zone [THM0] (58 C)
[    0.629111] GHES: HEST is not enabled!
[    0.629201] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.636522] ACPI: Battery Slot [BAT0] (battery present)
[    0.651178] 0000:00:16.3: ttyS4 at I/O 0x50b0 (irq = 19, base_baud = 115200) is a 16550A
[    0.651421] Linux agpgart interface v0.103
[    0.663450] tpm_tis 00:05: 1.2 TPM (device-id 0x0, rev-id 78)
[    0.738621] brd: module loaded
[    0.739402] loop: module loaded
[    0.739609] libphy: Fixed MDIO Bus: probed
[    0.739612] tun: Universal TUN/TAP device driver, 1.6
[    0.739613] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.739661] PPP generic driver version 2.4.2
[    0.739819] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.739825] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.740907] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[    0.740914] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.741004] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.741005] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.741007] usb usb1: Product: xHCI Host Controller
[    0.741008] usb usb1: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
[    0.741009] usb usb1: SerialNumber: 0000:00:14.0
[    0.741114] hub 1-0:1.0: USB hub found
[    0.741126] hub 1-0:1.0: 4 ports detected
[    0.741471] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.741474] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.741509] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.741510] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.741512] usb usb2: Product: xHCI Host Controller
[    0.741513] usb usb2: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
[    0.741514] usb usb2: SerialNumber: 0000:00:14.0
[    0.741607] hub 2-0:1.0: USB hub found
[    0.741618] hub 2-0:1.0: 4 ports detected
[    0.741981] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.741986] ehci-pci: EHCI PCI platform driver
[    0.742058] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.742062] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.742075] ehci-pci 0000:00:1a.0: debug port 2
[    0.745983] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.745995] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf253a000
[    0.755473] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.755512] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.755514] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.755515] usb usb3: Product: EHCI Host Controller
[    0.755517] usb usb3: Manufacturer: Linux 4.2.0-27-generic ehci_hcd
[    0.755518] usb usb3: SerialNumber: 0000:00:1a.0
[    0.755642] hub 3-0:1.0: USB hub found
[    0.755647] hub 3-0:1.0: 3 ports detected
[    0.755820] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.755825] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    0.755838] ehci-pci 0000:00:1d.0: debug port 2
[    0.759727] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.759737] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf2539000
[    0.771478] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.771510] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    0.771512] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.771513] usb usb4: Product: EHCI Host Controller
[    0.771514] usb usb4: Manufacturer: Linux 4.2.0-27-generic ehci_hcd
[    0.771515] usb usb4: SerialNumber: 0000:00:1d.0
[    0.771676] hub 4-0:1.0: USB hub found
[    0.771683] hub 4-0:1.0: 3 ports detected
[    0.771805] ehci-platform: EHCI generic platform driver
[    0.771816] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.771821] ohci-pci: OHCI PCI platform driver
[    0.771830] ohci-platform: OHCI generic platform driver
[    0.771837] uhci_hcd: USB Universal Host Controller Interface driver
[    0.771884] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.773605] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.773609] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.773850] mousedev: PS/2 mouse device common for all mice
[    0.774202] rtc_cmos 00:02: RTC can wake from S4
[    0.774344] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.774377] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.774385] i2c /dev entries driver
[    0.774461] device-mapper: uevent: version 1.0.3
[    0.774523] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.774540] Intel P-state driver initializing.
[    0.774682] ledtrig-cpu: registered to indicate activity on CPUs
[    0.774935] PCCT header not found.
[    0.775377] NET: Registered protocol family 10
[    0.775635] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.775758] NET: Registered protocol family 17
[    0.775785] Key type dns_resolver registered
[    0.776428] Loading compiled-in X.509 certificates
[    0.778163] Loaded X.509 cert 'Build time autogenerated kernel key: 9421ce78f7dd6932d7a71d3bab89bb036afa29eb'
[    0.778192] registered taskstats version 1
[    0.778230] zswap: loading zswap
[    0.778234] zswap: using zbud pool
[    0.778242] zswap: using lzo compressor
[    0.780568] Key type trusted registered
[    0.783302] Key type encrypted registered
[    0.783309] AppArmor: AppArmor sha1 policy hashing enabled
[    0.983806] evm: HMAC attrs: 0x1
[    0.984336]   Magic number: 4:716:803
[    1.004322] rtc_cmos 00:02: setting system clock to 2016-02-17 21:47:02 UTC (1455745622)
[    1.004476] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.004478] EDD information not available.
[    1.004551] PM: Hibernation image not present or could not be loaded.
[    1.004826] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    1.004828] Write protecting the kernel read-only data: 12288k
[    1.004991] Freeing unused kernel memory: 24K (ffff8800017fa000 - ffff880001800000)
[    1.005064] Freeing unused kernel memory: 292K (ffff880001bb7000 - ffff880001c00000)
[    1.012971] random: systemd-udevd urandom read with 8 bits of entropy available
[    1.041980] wmi: Mapper loaded
[    1.043487] pps_core: LinuxPPS API ver. 1 registered
[    1.043489] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.044799] sdhci: Secure Digital Host Controller Interface driver
[    1.044801] sdhci: Copyright(c) Pierre Ossman
[    1.045045] PTP clock support registered
[    1.046396] sdhci-pci 0000:02:00.0: SDHCI controller found [1180:e822] (rev 7)
[    1.046798] sdhci-pci 0000:02:00.0: No vmmc regulator found
[    1.046800] sdhci-pci 0000:02:00.0: No vqmmc regulator found
[    1.048961] [drm] Initialized drm 1.1.0 20060810
[    1.049013] ahci 0000:00:1f.2: version 3.0
[    1.049173] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.049367] mmc0: SDHCI controller on PCI [0000:02:00.0] using DMA
[    1.049692] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.5-k
[    1.049693] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    1.051666] usb 1-3: new high-speed USB device number 2 using xhci_hcd
[    1.063693] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    1.063698] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst 
[    1.067678] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.080165] scsi host0: ahci
[    1.080261] scsi host1: ahci
[    1.080347] scsi host2: ahci
[    1.080426] scsi host3: ahci
[    1.080505] scsi host4: ahci
[    1.080589] scsi host5: ahci
[    1.080637] ata1: SATA max UDMA/133 abar m2048@0xf2538000 port 0xf2538100 irq 27
[    1.080640] ata2: SATA max UDMA/133 abar m2048@0xf2538000 port 0xf2538180 irq 27
[    1.080641] ata3: DUMMY
[    1.080643] ata4: DUMMY
[    1.080645] ata5: SATA max UDMA/133 abar m2048@0xf2538000 port 0xf2538300 irq 27
[    1.080646] ata6: DUMMY
[    1.080814] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.083687] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    1.180147] usb 1-3: New USB device found, idVendor=0424, idProduct=2514
[    1.180150] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.180614] hub 1-3:1.0: USB hub found
[    1.180637] hub 1-3:1.0: 4 ports detected
[    1.200531] usb 3-1: New USB device found, idVendor=8087, idProduct=0024
[    1.200534] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.201031] hub 3-1:1.0: USB hub found
[    1.201279] hub 3-1:1.0: 6 ports detected
[    1.216228] usb 4-1: New USB device found, idVendor=8087, idProduct=0024
[    1.216232] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.216549] hub 4-1:1.0: USB hub found
[    1.216610] hub 4-1:1.0: 8 ports detected
[    1.267952] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.267955] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 3c:97:0e:96:8a:ce
[    1.267957] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.268005] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[    1.268615] e1000e 0000:00:19.0 enp0s25: renamed from eth0
[    1.269286] [drm] Memory usable by graphics device = 2048M
[    1.269289] checking generic (e0000000 410000) vs hw (e0000000 10000000)
[    1.269290] fb: switching to inteldrmfb from VESA VGA
[    1.269323] Console: switching to colour dummy device 80x25
[    1.269515] [drm] Replacing VGA console driver
[    1.275875] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.275877] [drm] Driver supports precise vblank timestamp query.
[    1.275942] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.309767] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.310523] acpi device:00: registered as cooling_device4
[    1.310576] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.310660] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    1.347946] usb 1-4: new high-speed USB device number 3 using xhci_hcd
[    1.375941] [drm] GMBUS [i915 gmbus dpb] timed out, falling back to bit banging on pin 5
[    1.399935] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.400744] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.400747] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.400866] ata1.00: ATA-9: CT480BX200SSD1, MU01.4, max UDMA/133
[    1.400868] ata1.00: 937703088 sectors, multi 2: LBA48 NCQ (depth 31/32), AA
[    1.401216] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.401219] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.401529] ata1.00: configured for UDMA/133
[    1.401662] scsi 0:0:0:0: Direct-Access     ATA      CT480BX200SSD1   .4   PQ: 0 ANSI: 5
[    1.401892] sd 0:0:0:0: [sda] 937703088 512-byte logical blocks: (480 GB/447 GiB)
[    1.401896] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.401972] sd 0:0:0:0: [sda] Write Protect is off
[    1.401975] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.402003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.402071] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.402462] fbcon: inteldrmfb (fb0) is primary device
[    1.402545] Console: switching to colour frame buffer device 170x48
[    1.402565] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.402567] i915 0000:00:02.0: registered panic notifier
[    1.402625]  sda: sda1 sda2 sda3
[    1.402981] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.472023] usb 3-1.2: new full-speed USB device number 3 using ehci-pci
[    1.477861] usb 1-4: config 1 has an invalid interface number: 8 but max is 3
[    1.477865] usb 1-4: config 1 has no interface number 1
[    1.479815] usb 1-4: New USB device found, idVendor=1199, idProduct=68a2
[    1.479818] usb 1-4: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[    1.479820] usb 1-4: Product: MC7710
[    1.479821] usb 1-4: Manufacturer: Sierra Wireless, Incorporated
[    1.479822] usb 1-4: SerialNumber: 352974027802909
[    1.548063] usb 1-3.1: new high-speed USB device number 4 using xhci_hcd
[    1.569114] usb 3-1.2: New USB device found, idVendor=046d, idProduct=c52b
[    1.569117] usb 3-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.569118] usb 3-1.2: Product: USB Receiver
[    1.569120] usb 3-1.2: Manufacturer: Logitech
[    1.573158] hidraw: raw HID events driver (C) Jiri Kosina
[    1.579802] usbcore: registered new interface driver usbhid
[    1.579806] usbhid: USB HID core driver
[    1.583689] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.2/input2
[    1.620188] tsc: Refined TSC clocksource calibration: 2594.107 MHz
[    1.620192] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x25647d583cf, max_idle_ns: 440795304232 ns
[    1.638518] usb 1-3.1: New USB device found, idVendor=2109, idProduct=2812
[    1.638525] usb 1-3.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.638529] usb 1-3.1: Product: USB2.0 Hub             
[    1.638532] usb 1-3.1: Manufacturer: VIA Labs, Inc.         
[    1.639109] hub 1-3.1:1.0: USB hub found
[    1.639491] hub 1-3.1:1.0: 4 ports detected
[    1.640066] usb 3-1.4: new full-speed USB device number 4 using ehci-pci
[    1.701216] input: Logitech M705 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.2/0003:046D:C52B.0003/0003:046D:101B.0004/input/input7
[    1.701466] logitech-hidpp-device 0003:046D:101B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech M705] on usb-0000:00:1a.0-1.2:1
[    1.720172] usb 1-3.4: new full-speed USB device number 5 using xhci_hcd
[    1.720190] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.723174] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.723923] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.725569] ata2.00: ATAPI: MATSHITADVD-RAM UJ8B2, SB01, max UDMA/100
[    1.728271] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.728959] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.730585] ata2.00: configured for UDMA/100
[    1.737766] usb 3-1.4: New USB device found, idVendor=0a5c, idProduct=21e6
[    1.737770] usb 3-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.737771] usb 3-1.4: Product: BCM20702A0
[    1.737772] usb 3-1.4: Manufacturer: Broadcom Corp
[    1.737773] usb 3-1.4: SerialNumber: F4B7E2CC56F9
[    1.738218] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8B2    SB01 PQ: 0 ANSI: 5
[    1.754032] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.754034] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.754164] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.754237] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.808226] usb 3-1.6: new high-speed USB device number 5 using ehci-pci
[    1.828321] psmouse serio1: synaptics: queried max coordinates: x [..5768], y [..5062]
[    1.850052] usb 1-3.4: New USB device found, idVendor=054c, idProduct=0268
[    1.850055] usb 1-3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.850057] usb 1-3.4: Product: PLAYSTATION(R)3 Controller
[    1.850058] usb 1-3.4: Manufacturer: Sony
[    1.859570] psmouse serio1: synaptics: queried min coordinates: x [1174..], y [790..]
[    1.908918] usb 3-1.6: New USB device found, idVendor=04f2, idProduct=b2eb
[    1.908921] usb 3-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.908922] usb 3-1.6: Product: Integrated Camera
[    1.908924] usb 3-1.6: Manufacturer: Chicony Electronics Co., Ltd.
[    1.921653] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd002a3/0x940300/0x123800/0x0, board id: 1611, fw id: 1099905
[    1.921674] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    1.928313] usb 1-3.1.2: new high-speed USB device number 6 using xhci_hcd
[    1.961200] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.072439] ata5: SATA link down (SStatus 0 SControl 300)
[    2.620923] clocksource: Switched to clocksource tsc
[    3.139956] usb 1-3.1.2: New USB device found, idVendor=046d, idProduct=082d
[    3.139959] usb 1-3.1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=1
[    3.139961] usb 1-3.1.2: Product: HD Pro Webcam C920
[    3.139962] usb 1-3.1.2: SerialNumber: 3B3F305F
[    3.225158] usb 1-3.1.4: new high-speed USB device number 7 using xhci_hcd
[    3.328186] usb 1-3.1.4: New USB device found, idVendor=2109, idProduct=2812
[    3.328189] usb 1-3.1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.328190] usb 1-3.1.4: Product: USB2.0 Hub             
[    3.328191] usb 1-3.1.4: Manufacturer: VIA Labs, Inc.         
[    3.328731] hub 1-3.1.4:1.0: USB hub found
[    3.329061] hub 1-3.1.4:1.0: 4 ports detected
[    3.362053] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.451093] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    3.458839] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    3.458956] systemd[1]: Detected architecture x86-64.
[    3.459192] systemd[1]: Set hostname to <mikepearce-ThinkPad-X230>.
[    3.532656] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    3.532687] systemd[1]: Reached target User and Group Name Lookups.
[    3.532709] systemd[1]: Created slice Root Slice.
[    3.532738] systemd[1]: Listening on udev Control Socket.
[    3.532766] systemd[1]: Listening on Journal Socket.
[    3.532834] systemd[1]: Created slice User and Session Slice.
[    3.532887] systemd[1]: Listening on Journal Audit Socket.
[    3.532939] systemd[1]: Created slice System Slice.
[    3.533950] systemd[1]: Starting Uncomplicated firewall...
[    3.534029] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    3.534431] systemd[1]: Starting Increase datagram queue length...
[    3.534851] systemd[1]: Started Read required files in advance.
[    3.535426] systemd[1]: Started Braille Device Support.
[    3.537165] systemd[1]: Starting Load Kernel Modules...
[    3.537609] systemd[1]: Starting Setup Virtual Console...
[    3.537663] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    3.538079] systemd[1]: Mounting POSIX Message Queue File System...
[    3.538137] systemd[1]: Listening on udev Kernel Socket.
[    3.538624] systemd[1]: Starting udev Coldplug all Devices...
[    3.539085] systemd[1]: Mounting Debug File System...
[    3.539105] systemd[1]: Reached target Slices.
[    3.539184] systemd[1]: Listening on Journal Socket (/dev/log).
[    3.539295] systemd[1]: Created slice system-getty.slice.
[    3.539936] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    3.539963] systemd[1]: Reached target Encrypted Volumes.
[    3.539993] systemd[1]: Reached target Remote File Systems (Pre).
[    3.540620] systemd[1]: Mounting Huge Pages File System...
[    3.540677] systemd[1]: Listening on fsck to fsckd communication Socket.
[    3.540737] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    3.542198] systemd[1]: Started Uncomplicated firewall.
[    3.542395] systemd[1]: Started Setup Virtual Console.
[    3.545873] systemd[1]: Mounted POSIX Message Queue File System.
[    3.545924] systemd[1]: Mounted Huge Pages File System.
[    3.546370] systemd[1]: Mounted Debug File System.
[    3.546629] systemd[1]: Started Increase datagram queue length.
[    3.546937] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    3.552740] systemd[1]: Starting Create Static Device Nodes in /dev...
[    3.552796] systemd[1]: Listening on Syslog Socket.
[    3.553621] systemd[1]: Starting Journal Service...
[    3.558783] lp: driver loaded but no devices found
[    3.561617] ppdev: user-space parallel port driver
[    3.565146] systemd[1]: Started Load Kernel Modules.
[    3.565754] systemd[1]: Starting Apply Kernel Variables...
[    3.566406] systemd[1]: Mounting FUSE Control File System...
[    3.569101] systemd[1]: Mounted FUSE Control File System.
[    3.576707] systemd[1]: Started Apply Kernel Variables.
[    3.579699] systemd[1]: Started Create Static Device Nodes in /dev.
[    3.580223] systemd[1]: Starting udev Kernel Device Manager...
[    3.601444] systemd[1]: Started udev Coldplug all Devices.
[    3.601577] systemd[1]: Started Journal Service.
[    3.625345] usb 1-3.1.4.1: new full-speed USB device number 8 using xhci_hcd
[    3.728769] usb 1-3.1.4.1: New USB device found, idVendor=046d, idProduct=c049
[    3.728777] usb 1-3.1.4.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.728780] usb 1-3.1.4.1: Product: USB Gaming Mouse
[    3.728783] usb 1-3.1.4.1: Manufacturer: Logitech
[    3.728906] usb 1-3.1.4.1: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    3.778150] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.788445] systemd-journald[252]: Received request to flush runtime journal from PID 1
[    3.813482] usb 1-3.1.4.2: new high-speed USB device number 9 using xhci_hcd
[    3.888661] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\_SB_.PCI0.LPC_.PMIO) (20150619/utaddress-254)
[    3.888667] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.888675] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x000000000000057F (\_SB_.PCI0.LPC_.LPIO) (20150619/utaddress-254)
[    3.888678] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.888679] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000057F (\_SB_.PCI0.LPC_.LPIO) (20150619/utaddress-254)
[    3.888723] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.889277] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000057F (\_SB_.PCI0.LPC_.LPIO) (20150619/utaddress-254)
[    3.889283] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.889284] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.889323] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    3.894322] random: nonblocking pool is initialized
[    3.900575] Non-volatile memory driver v1.3
[    3.909264] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[    3.909267] thinkpad_acpi: http://ibm-acpi.sf.net/
[    3.909268] thinkpad_acpi: ThinkPad BIOS G2ET92WW (2.52 ), EC unknown
[    3.909270] thinkpad_acpi: Lenovo ThinkPad X230, model 2325B15
[    3.911532] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[    3.912190] thinkpad_acpi: radio switch found; radios are enabled
[    3.912218] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[    3.912219] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[    3.913797] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    3.914201] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[    3.916522] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input9
[    3.918889] usb 1-3.1.4.2: New USB device found, idVendor=04a9, idProduct=1747
[    3.918893] usb 1-3.1.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.918895] usb 1-3.1.4.2: Product: MP495 series
[    3.918896] usb 1-3.1.4.2: Manufacturer: Canon
[    3.918898] usb 1-3.1.4.2: SerialNumber: 025655
[    3.937873] Intel(R) Wireless WiFi driver for Linux
[    3.937877] Copyright(c) 2003- 2015 Intel Corporation
[    3.938070] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.946514] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    3.949251] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC269VC: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.949256] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.949258] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=2 (0x15/0x1b/0x0/0x0/0x0)
[    3.949260] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    3.949261] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    3.949264] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[    3.949266] snd_hda_codec_realtek hdaudioC0D0:      Dock Mic=0x19
[    3.949267] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    3.969342] AVX version of gcm_enc/dec engaged.
[    3.969345] AES CTR mode by8 optimization enabled
[    3.984768] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    3.984816] input: HDA Intel PCH Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    3.984856] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    3.984908] input: HDA Intel PCH Dock Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    3.984970] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    3.986842] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    3.986925] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    3.991102] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.991105] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.991107] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.991110] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    3.991251] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.001617] usb 1-3.1.4.3: new full-speed USB device number 10 using xhci_hcd
[    4.023990] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.109636] usb 1-3.1.4.3: New USB device found, idVendor=046d, idProduct=0a44
[    4.109639] usb 1-3.1.4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.109641] usb 1-3.1.4.3: Product: Logitech USB Headset
[    4.109642] usb 1-3.1.4.3: Manufacturer: Logitech
[    4.122078] intel_rapl: Found RAPL domain package
[    4.122082] intel_rapl: Found RAPL domain core
[    4.122084] intel_rapl: Found RAPL domain uncore
[    4.122260] cfg80211: World regulatory domain updated:
[    4.122263] cfg80211:  DFS Master region: unset
[    4.122264] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    4.122266] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    4.122268] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    4.122270] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    4.122272] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    4.122274] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    4.122276] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    4.122278] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    4.122279] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    4.140622] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.156715] Adding 8000508k swap on /dev/sda2.  Priority:-1 extents:1 across:8000508k SSFS
[    4.197754] usb 1-3.1.4.4: new high-speed USB device number 11 using xhci_hcd
[    4.306161] usb 1-3.1.4.4: New USB device found, idVendor=05ac, idProduct=1006
[    4.306169] usb 1-3.1.4.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.306172] usb 1-3.1.4.4: Product: Keyboard Hub
[    4.306176] usb 1-3.1.4.4: Manufacturer: Apple, Inc.
[    4.306178] usb 1-3.1.4.4: SerialNumber: 000000000000
[    4.306472] hub 1-3.1.4.4:1.0: USB hub found
[    4.306502] hub 1-3.1.4.4:1.0: 3 ports detected
[    4.578005] usb 1-3.1.4.4.2: new low-speed USB device number 12 using xhci_hcd
[    4.629275] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    4.633192] [drm:intel_set_pch_fifo_underrun_reporting [i915]] *ERROR* uncleared pch fifo underrun on pch transcoder A
[    4.633211] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[    4.672199] usb 1-3.1.4.4.2: New USB device found, idVendor=05ac, idProduct=0250
[    4.672203] usb 1-3.1.4.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.672205] usb 1-3.1.4.4.2: Product: Apple Keyboard
[    4.672207] usb 1-3.1.4.4.2: Manufacturer: Apple Inc.
[    4.672338] usb 1-3.1.4.4.2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    4.672343] usb 1-3.1.4.4.2: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    4.758434] audit: type=1400 audit(1455745626.247:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=640 comm="apparmor_parser"
[    4.758440] audit: type=1400 audit(1455745626.247:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=640 comm="apparmor_parser"
[    4.760941] audit: type=1400 audit(1455745626.247:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=640 comm="apparmor_parser"
[    4.760946] audit: type=1400 audit(1455745626.247:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=640 comm="apparmor_parser"
[    4.760949] audit: type=1400 audit(1455745626.247:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=640 comm="apparmor_parser"
[    4.760961] audit: type=1400 audit(1455745626.247:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=640 comm="apparmor_parser"
[    4.771481] audit: type=1400 audit(1455745626.259:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=640 comm="apparmor_parser"
[    4.771487] audit: type=1400 audit(1455745626.259:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=640 comm="apparmor_parser"
[    4.771501] audit: type=1400 audit(1455745626.259:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=640 comm="apparmor_parser"
[    5.240813] usbcore: registered new interface driver usbserial
[    5.240828] usbcore: registered new interface driver usbserial_generic
[    5.240835] usbserial: USB Serial support registered for generic
[    5.252173] usbcore: registered new interface driver cdc_wdm
[    5.253951] usbcore: registered new interface driver qcserial
[    5.253968] usbserial: USB Serial support registered for Qualcomm USB modem
[    5.256299] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[    5.256615] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0
[    5.257970] qcserial 1-4:1.2: Qualcomm USB modem converter detected
[    5.260211] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB1
[    5.261444] qcserial 1-4:1.3: Qualcomm USB modem converter detected
[    5.261580] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB2
[    5.266921] qmi_wwan 1-4:1.8: cdc-wdm1: USB WDM device
[    5.267263] qmi_wwan 1-4:1.8 wwan0: register 'qmi_wwan' at usb-0000:00:14.0-4, WWAN/QMI device, c6:b4:15:e8:b8:da
[    5.268084] usbcore: registered new interface driver qmi_wwan
[    5.393407] cgroup: new mount options do not match the existing superblock, will be ignored
[    5.409685] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[    5.421600] vboxdrv: Found 4 processor cores
[    5.448794] vboxdrv: TSC mode is Invariant, tentative frequency 2594106793 Hz
[    5.448797] vboxdrv: Successfully loaded version 5.0.14_Ubuntu (interface 0x00240000)
[    5.458568] VBoxNetFlt: Successfully started.
[    5.478354] VBoxNetAdp: Successfully started.
[    5.493586] VBoxPciLinuxInit
[    5.500336] vboxpci: IOMMU not found (not registered)
[    5.505195] media: Linux media interface: v0.10
[    5.527657] Linux video capture interface: v2.00
[    5.567075] Bluetooth: Core ver 2.20
[    5.567097] NET: Registered protocol family 31
[    5.567107] Bluetooth: HCI device and connection manager initialized
[    5.567736] Bluetooth: HCI socket layer initialized
[    5.567741] Bluetooth: L2CAP socket layer initialized
[    5.567748] Bluetooth: SCO socket layer initialized
[    5.605171] usbcore: registered new interface driver btusb
[    5.611627] Bluetooth: hci0: BCM: chip id 63
[    5.612562] Bluetooth: hci0: BCM20702A1 (001.002.014) build 0000
[    5.613020] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21e6.hcd failed with error -2
[    5.613025] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0a5c-21e6.hcd not found
[    5.639215] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[    5.659172] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b2eb)
[    5.662626] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.6/3-1.6:1.0/input/input17
[    5.662791] uvcvideo: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
[    5.666634] input: HD Pro Webcam C920 as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.1/1-3.1.2/1-3.1.2:1.0/input/input18
[    5.668521] usbcore: registered new interface driver uvcvideo
[    5.668525] USB Video Class driver (1.1.1)
[    5.759487] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.4/1-3.4:1.0/0003:054C:0268.0005/input/input19
[    5.759923] sony 0003:054C:0268.0005: input,hiddev0,hidraw2: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:14.0-3.4/input0
[    5.879051] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[    5.881969] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    5.882085] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.889321] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    6.049004] usb 1-4: USB disconnect, device number 3
[    6.049009] qcserial ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[    6.049045] qcserial ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[    6.049125] qcserial ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[    6.049141] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[    6.049154] qcserial 1-4:1.0: device disconnected
[    6.049166] qcserial ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[    6.049276] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
[    6.049283] qcserial 1-4:1.2: device disconnected
[    6.049400] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
[    6.049412] qcserial 1-4:1.3: device disconnected
[    6.049465] qmi_wwan 1-4:1.8 wwan0: unregister 'qmi_wwan' usb-0000:00:14.0-4, WWAN/QMI device
[    6.086482] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    6.159283] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    6.166380] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    6.244166] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.294537] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[    6.339195] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.456496] usbcore: registered new interface driver snd-usb-audio
[    6.981840] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.1/1-3.1.4/1-3.1.4.1/1-3.1.4.1:1.0/0003:046D:C049.0006/input/input20
[    6.982023] hid-generic 0003:046D:C049.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:14.0-3.1.4.1/input0
[    6.982888] hid-generic 0003:046D:C049.0007: hiddev0,hidraw4: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:14.0-3.1.4.1/input1
[    6.983627] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.1/1-3.1.4/1-3.1.4.3/1-3.1.4.3:1.3/0003:046D:0A44.0008/input/input21
[    7.091908] hid-generic 0003:046D:0A44.0008: input,hidraw5: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:14.0-3.1.4.3/input3
[    7.098324] usblp 1-3.1.4.2:1.1: usblp3: USB Bidirectional printer dev 9 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1747
[    7.098387] usbcore: registered new interface driver usblp
[    7.361814] e1000e: enp0s25 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[    7.361821] e1000e 0000:00:19.0 enp0s25: 10/100 speed: disabling TSO
[    7.362295] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[    7.472779] input: Apple Inc. Apple Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.1/1-3.1.4/1-3.1.4.4/1-3.1.4.4.2/1-3.1.4.4.2:1.0/0003:05AC:0250.0009/input/input22
[    7.528296] apple 0003:05AC:0250.0009: input,hidraw6: USB HID v1.11 Keyboard [Apple Inc. Apple Keyboard] on usb-0000:00:14.0-3.1.4.4.2/input0
[    7.528806] input: Apple Inc. Apple Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3.1/1-3.1.4/1-3.1.4.4/1-3.1.4.4.2/1-3.1.4.4.2:1.1/0003:05AC:0250.000A/input/input23
[    7.584139] apple 0003:05AC:0250.000A: input,hidraw7: USB HID v1.11 Device [Apple Inc. Apple Keyboard] on usb-0000:00:14.0-3.1.4.4.2/input1
[    9.471687] wlp3s0: authenticate with 7c:4c:a5:90:32:1d
[    9.474345] wlp3s0: send auth to 7c:4c:a5:90:32:1d (try 1/3)
[    9.477220] wlp3s0: authenticated
[    9.481216] wlp3s0: associate with 7c:4c:a5:90:32:1d (try 1/3)
[    9.485281] wlp3s0: RX AssocResp from 7c:4c:a5:90:32:1d (capab=0x1411 status=0 aid=2)
[    9.504080] wlp3s0: associated
[    9.504119] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[    9.506553] cfg80211: Regulatory domain changed to country: DE
[    9.506555] cfg80211:  DFS Master region: ETSI
[    9.506556] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    9.506558] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    9.506559] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    9.506560] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    9.506562] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
[    9.506563] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[    9.556962] wlp3s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 7c:4c:a5:90:32:1d
[   12.168360] audit_printk_skb: 48 callbacks suppressed
[   12.168364] audit: type=1400 audit(1455745633.651:27): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=3821 comm="serial" capability=21  capname="sys_admin"
[   12.247656] usblp3: removed
[   12.250370] usblp 1-3.1.4.2:1.1: usblp3: USB Bidirectional printer dev 9 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1747
[   19.188814] wlp3s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 7c:4c:a5:90:32:1d
[   49.416881] wlp3s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 7c:4c:a5:90:32:1d
[   59.155286] usb 1-3.1.2: reset high-speed USB device number 6 using xhci_hcd
[  130.957871] wlp3s0: deauthenticating from 7c:4c:a5:90:32:1d by local choice (Reason: 3=DEAUTH_LEAVING)
[  130.987090] cfg80211: World regulatory domain updated:
[  130.987095] cfg80211:  DFS Master region: unset
[  130.987096] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  130.987099] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  130.987101] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  130.987103] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[  130.987106] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  130.987109] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  130.987111] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[  130.987113] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[  130.987115] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[  131.094785] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  131.094993] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  131.101747] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  131.371951] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  131.378698] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  131.461294] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  131.548800] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  134.719329] wlp3s0: authenticate with 7c:4c:a5:90:32:1d
[  134.721477] wlp3s0: send auth to 7c:4c:a5:90:32:1d (try 1/3)
[  134.724268] wlp3s0: authenticated
[  134.727789] wlp3s0: associate with 7c:4c:a5:90:32:1d (try 1/3)
[  134.731799] wlp3s0: RX AssocResp from 7c:4c:a5:90:32:1d (capab=0x1411 status=0 aid=2)
[  134.749971] wlp3s0: associated
[  134.750032] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  134.754826] cfg80211: Regulatory domain changed to country: DE
[  134.754831] cfg80211:  DFS Master region: ETSI
[  134.754833] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  134.754837] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  134.754840] cfg80211:   (5150000 KHz - 5250000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  134.754843] cfg80211:   (5250000 KHz - 5350000 KHz @ 80000 KHz, 200000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  134.754846] cfg80211:   (5470000 KHz - 5725000 KHz @ 160000 KHz), (N/A, 2698 mBm), (0 s)
[  134.754848] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[  134.772842] wlp3s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 7c:4c:a5:90:32:1d

```

---

### Post by f-mike-y on 2016-02-17
OK, I've also now stoped network manager, deleted networkmanager.state, started network manager and rebooted - it's still not showing up anywhere. :( Although syslog now says enabled by killswitch and enabled by state.

---

