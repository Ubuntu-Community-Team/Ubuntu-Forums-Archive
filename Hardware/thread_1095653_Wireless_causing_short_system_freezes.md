---
title: "Wireless causing short system freezes"
date: 2009-03-14
forum: Hardware
---

### Post by Tmo11 on 2009-03-14
I know there are similar issues but this seems somewhat differen't
Asus m50sv notebook w/ intel 4965: freezing does _not_ have blinking caps lock/scroll 


I installed a fresh version of ubuntu 8.10, got everything up an running smooth 'cept a few Fn keys. Wireless worked great for a few minutes, then start noticing that the system freezes on average every half minute, sometimes more or less. Then internet connection quits working even though it says I have full signal strength. The freezes are short (<5 sec on usual) and annoying.
When I disable wireless in any way, the system goes back to normal with no freezes and using an ethernet chord provides uninterrupted internet access

I have an Intel 4965 ag/n internal card, which should be working fine but for strange reason isnt.
It shouldn't be a hardware problem because I tested the wireless on XP without issue.

So I sudo dmesg
part of my output goes:
[ 12.573659] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 12.573662] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[ 12.573782] iwlagn 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 12.573815] iwlagn 0000:05:00.0: setting latency timer to 64
[ 12.573861] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[ 12.628345] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[ 12.628504] iwlagn 0000:05:00.0: PCI INT A disabled
[ 12.628815] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 12.658507] Linux video capture interface: v2.00
[ 12.852154] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (174f:5a31)
[ 12.897618] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/input/input8
[ 12.917145] usbcore: registered new interface driver uvcvideo
[ 12.917148] USB Video Class driver (v0.1.0)
[ 13.073154] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 13.073178] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 13.254350] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x280b1, caps: 0xb04713/0x60040d
[ 13.308009] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[ 13.480215] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
[ 13.480262] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 14.113007] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x020c0000
[ 14.113015] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[ 14.904909] lp: driver loaded but no devices found
[ 15.016699] Adding 5863684k swap on /dev/sda5. Priority:-1 extents:1 across:5863684k
[ 15.544937] EXT3 FS on sda3, internal journal
[ 16.390275] type=1505 audit(1236925945.603:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4342
[ 16.512300] type=1505 audit(1236925945.723:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4347
[ 16.512429] type=1505 audit(1236925945.723:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4347
[ 16.625958] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 17.059519] ACPI: WMI: Mapper loaded
[ 17.709162] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[ 17.745265] apm: BIOS not found.
[ 17.885184] ppdev: user-space parallel port driver
[ 19.848326] Bluetooth: L2CAP ver 2.11
[ 19.848338] Bluetooth: L2CAP socket layer initialized
[ 19.872251] Bluetooth: SCO (Voice Link) ver 0.6
[ 19.872263] Bluetooth: SCO socket layer initialized
[ 19.893301] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 19.893311] Bluetooth: BNEP filters: protocol multicast
[ 19.926170] Bridge firewalling registered
[ 19.969044] Bluetooth: RFCOMM socket layer initialized
[ 19.969069] Bluetooth: RFCOMM TTY layer initialized
[ 19.969075] Bluetooth: RFCOMM ver 1.10
[ 24.256117] sky2 eth0: enabling interface
[ 24.261602] iwlagn 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 24.261681] iwlagn 0000:05:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 24.261833] firmware: requesting iwlwifi-4965-2.ucode
[ 24.509261] Registered led device: iwl-phy0:radio
[ 24.509914] Registered led device: iwl-phy0:assoc
[ 24.509969] Registered led device: iwl-phy0:RX
[ 24.510009] Registered led device: iwl-phy0:TX
[ 24.598433] NET: Registered protocol family 17
[ 52.458942] CPU0 attaching NULL sched-domain.
[ 52.458960] CPU1 attaching NULL sched-domain.
[ 52.459152] CPU0 attaching sched-domain:
[ 52.459161] domain 0: span 0-1 level MC
[ 52.459168] groups: 0 1
[ 52.459181] CPU1 attaching sched-domain:
[ 52.459187] domain 0: span 0-1 level MC
[ 52.459194] groups: 1 0
[ 62.850160] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 62.852056] wlan0: authenticated
[ 62.852068] wlan0: associate with AP 00:0f:66:dc:f7:a8
[ 62.855400] wlan0: RX AssocResp from 00:0f:66:dc:f7:a8 (capab=0x411 status=0 aid=5)
[ 62.855410] wlan0: associated
[ 66.150680] NET: Registered protocol family 10
[ 66.151181] lo: Disabled Privacy Extensions
[ 66.151651] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 76.872044] wlan0: no IPv6 routers present
[ 81.613161] iwlagn: Microcode SW error detected. Restarting 0x82000000.
[ 83.616655] wlan0: failed to restore operational channel after scan
[ 83.616769] iwlagn: No space for Tx
[ 83.616773] iwlagn: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 83.814582] Registered led device: iwl-phy0:radio
[ 83.814774] Registered led device: iwl-phy0:assoc
[ 83.815235] Registered led device: iwl-phy0:RX
[ 83.816185] Registered led device: iwl-phy0:TX
[ 83.824355] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 83.826355] wlan0: authenticated
[ 83.826365] wlan0: associate with AP 00:0f:66:dc:f7:a8
[ 83.829568] wlan0: RX ReassocResp from 00:0f:66:dc:f7:a8 (capab=0x411 status=0 aid=5)
[ 83.829575] wlan0: associated
[ 121.617227] iwlagn: Microcode SW error detected. Restarting 0x82000000.
[ 123.622489] wlan0: failed to restore operational channel after scan
[ 123.622531] iwlagn: No space for Tx
[ 123.622539] iwlagn: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 123.822367] Registered led device: iwl-phy0:radio
[ 123.825558] Registered led device: iwl-phy0:assoc
[ 123.825962] Registered led device: iwl-phy0:RX
[ 123.826336] Registered led device: iwl-phy0:TX
[ 123.834643] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 123.837108] wlan0: authenticated
[ 123.837121] wlan0: associate with AP 00:0f:66:dc:f7:a8
[ 123.839715] wlan0: RX ReassocResp from 00:0f:66:dc:f7:a8 (capab=0x411 status=0 aid=5)
[ 123.839726] wlan0: associated
[ 181.621175] iwlagn: Microcode SW error detected. Restarting 0x82000000.
[ 183.622693] wlan0: failed to restore operational channel after scan
[ 183.622702] iwlagn: No space for Tx
[ 183.622704] iwlagn: Error sending REPLY_TX_PWR_TABLE_CMD: enqueue_hcmd failed: -28
[ 183.817823] Registered led device: iwl-phy0:radio
[ 183.817867] Registered led device: iwl-phy0:assoc
[ 183.817903] Registered led device: iwl-phy0:RX
[ 183.817939] Registered led device: iwl-phy0:TX
[ 183.826523] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 183.828398] wlan0: authenticated
[ 183.828410] wlan0: associate with AP 00:0f:66:dc:f7:a8
[ 183.830810] wlan0: RX ReassocResp from 00:0f:66:dc:f7:a8 (capab=0x411 status=0 aid=5)
[ 183.830822] wlan0: associated
[ 261.626394] iwlagn: Microcode SW error detected. Restarting 0x82000000.
[ 263.629764] wlan0: failed to restore operational channel after scan
[ 264.132071] iwlagn: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[ 264.144527] iwlagn: Microcode SW error detected. Restarting 0x2000000.
[ 264.644086] iwlagn: Error sending REPLY_ADD_STA: time out after 500ms.
[ 265.144093] iwlagn: Error sending REPLY_ADD_STA: time out after 500ms.
[ 265.629092] wlan0: No ProbeResp from current AP 00:0f:66:dc:f7:a8 - assume out of range
[ 265.644096] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 265.644107] iwlagn: Error setting new RXON (-110)
[ 266.144091] iwlagn: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[ 266.144102] iwlagn: REPLY_CT_KILL_CONFIG_CMD failed
[ 266.144177] Registered led device: iwl-phy0:radio
[ 266.144217] Registered led device: iwl-phy0:assoc
[ 266.144255] Registered led device: iwl-phy0:RX
[ 266.144292] Registered led device: iwl-phy0:TX
[ 266.644096] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 266.644107] iwlagn: Error setting new RXON (-110)
[ 267.144090] iwlagn: Error sending REPLY_RXON: time out after 500ms.
[ 267.144100] iwlagn: Error setting new RXON (-110)
[ 269.143083] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 269.340224] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 269.341558] Registered led device: iwl-phy0:radio
[ 269.342054] wlan0: authenticated
[ 269.342065] wlan0: associate with AP 00:0f:66:dc:f7:a8
[ 269.343935] Registered led device: iwl-phy0:assoc
[ 269.343987] Registered led device: iwl-phy0:RX
[ 269.344050] Registered led device: iwl-phy0:TX
[ 269.346601] wlan0: RX ReassocResp from 00:0f:66:dc:f7:a8 (capab=0x411 status=0 aid=5)
[ 269.346614] wlan0: associated
[ 269.359415] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 269.361358] wlan0: authenticated
[ 269.361372] wlan0: associate with AP 00:0f:66:dc:f7:a8
[ 269.363704] wlan0: RX ReassocResp from 00:0f:66:dc:f7:a8 (capab=0x411 status=0 aid=5)
[ 269.363715] wlan0: associated
[ 355.029794] iwlagn: Microcode SW error detected. Restarting 0x82000000.
[ 355.029895] wlan0: failed to restore operational channel after scan
[ 355.029907] iwlagn: TX Power requested while scanning!
[ 357.234015] Registered led device: iwl-phy0:radio
[ 357.234497] Registered led device: iwl-phy0:assoc
[ 357.234931] Registered led device: iwl-phy0:RX
[ 357.235299] Registered led device: iwl-phy0:TX
[ 357.244159] wlan0: authenticate with AP 00:0f:66:dc:f7:a8
[ 357.246102] wlan0: authenticated
[ 357.246114] wlan0: associate with AP 00:0f:66:dc:f7:a8
[ 357.249331] wlan0: RX ReassocResp from 00:0f:66:dc:f7:a8 (capab=0x411 status=0 aid=5)
[ 357.249341] wlan0: associated


^looks like something is screwed up with that driver but I don't know what it all means.
I need help: ndiswrapper uses cpu to 50% at all times so that workaround is useless, and I don't know what do do as far as linux drivers go.
Thanks in advance

---

