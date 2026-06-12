---
title: "Bluetooth adapter missing"
date: 2016-08-05
forum: Hardware
---

### Post by petwri on 2016-08-05
I got a gigabyte ga-h170n wifi mainboard, which has a combined bt/wifi module. However, the bt dongle doesn't appear when I activate bluetooth in system settings. Ubuntu tells me to connect a dongle. I'm on 16.04. Ideas?

---

### Post by jeremy31 on 2016-08-06
Please post the results for ```
lspci -nnk | grep -iA2 net; lsusb; lsmod | grep blue; dmesg | egrep -i 'blue|firm'
```

---

### Post by petwri on 2016-08-07
```


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8] (rev 3                                         1)
        Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection (2) I219-V [1458:e000]
        Kernel driver in use: e1000e
        Kernel modules: e1000e
--
04:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev                                          03)
        Subsystem: Gigabyte Technology Co., Ltd I211 Gigabit Network Connection [1458:e000]
        Kernel driver in use: igb
        Kernel modules: igb
05:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
        Subsystem: Intel Corporation Dual Band Wireless-AC 8260 [8086:0010]
        Kernel driver in use: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp.
Bus 001 Device 007: ID 05a4:9881 Ortek Technology, Inc. IR receiver [VRC-1100 Vista MCE Remote Control]
Bus 001 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 0ccd:00ab TerraTec Electronic GmbH
Bus 001 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bluetooth             520192  31 bnep,btbcm,btqca,btrtl,btusb,hci_uart,rfcomm,btintel
[    8.888034] Bluetooth: Core ver 2.21
[    8.888044] Bluetooth: HCI device and connection manager initialized
[    8.888047] Bluetooth: HCI socket layer initialized
[    8.888048] Bluetooth: L2CAP socket layer initialized
[    8.888052] Bluetooth: SCO socket layer initialized
[    8.895005] Bluetooth: HCI UART driver ver 2.3
[    8.895008] Bluetooth: HCI UART protocol H4 registered
[    8.895009] Bluetooth: HCI UART protocol BCSP registered
[    8.895009] Bluetooth: HCI UART protocol LL registered
[    8.895010] Bluetooth: HCI UART protocol ATH3K registered
[    8.895011] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    8.895028] Bluetooth: HCI UART protocol Intel registered
[    8.895036] Bluetooth: HCI UART protocol BCM registered
[    8.895037] Bluetooth: HCI UART protocol QCA registered
[    9.031334] Bluetooth: hci0: Firmware revision 0.0 build 90 week 25 2015
[    9.197291] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-8000C-20.ucode failed with error                                          -2
[    9.197424] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error                                          -2
[    9.197754] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error                                          -2
[    9.197764] iwlwifi 0000:05:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error                                          -2
[    9.212547] iwlwifi 0000:05:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   10.586291]  tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(OE) tbs                                         6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btusb tbs6                                         922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_nec_dec                                         oder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth intel_lpss_a                                         cpi intel_lpss acpi_pad acpi_als kfifo_buf tpm_infineon mac_hid industrialio parport_pc ppdev lp parpor                                         t autofs4 raid10 raid1 raid0 multipath linear hid_generic hid_logitech_hidpp hid_logitech_dj usbhid rai                                         d456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c uas usb_storage                                          psmouse e1000e igb dca ptp pps_core i915 ahci i2c_algo_bit libahci drm_kms_helper syscopyarea
[   98.834123] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   98.834126] Bluetooth: BNEP filters: protocol multicast
[   98.834128] Bluetooth: BNEP socket layer initialized
[  133.571852] Bluetooth: RFCOMM TTY layer initialized
[  133.571858] Bluetooth: RFCOMM socket layer initialized
[  133.571861] Bluetooth: RFCOMM ver 1.11
[  490.252683]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  491.121929]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  491.439798]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  492.175340]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  538.446164]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  543.663367]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  544.450200]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  544.753954]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  553.228781]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[  554.114676]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[19024.548091]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[19031.524434]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth
[19034.732228]  snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm aesni_                                         intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmid                                         i iwlmvm mac80211 snd_seq snd_seq_device snd_timer snd serio_raw iwlwifi soundcore cfg80211 joydev inpu                                         t_leds rc_tbs_nec(OE) ir_lirc_codec(OE) lirc_dev(OE) saa716x_tbs_dvb(OE) ir_mce_kbd_decoder(OE) tbs6982                                         fe(POE) tbs6680fe(POE) tbs6923fe(POE) tbs6985se(POE) ir_sony_decoder(OE) tbs6928se(POE) ir_jvc_decoder(                                         OE) tbs6982se(POE) tbs6991fe(POE) tbs6618fe(POE) tbs6983fe(POE) ir_rc6_decoder(OE) saa716x_core(OE) btu                                         sb tbs6922fe(POE) tbs6928fe(POE) tbs6991se(POE) btrtl ir_rc5_decoder(OE) tbs6290fe(POE) stv090x(OE) ir_                                         nec_decoder(OE) dvb_core(OE) mei_me rc_core(OE) mei shpchp hci_uart btbcm btqca btintel bluetooth



```

---

### Post by jeremy31 on 2016-08-09
Let see ```
dmesg | grep -i intel
```

---

### Post by petwri on 2016-08-09
> **jeremy31 said:**
> Let see ```
dmesg | grep -i intel
```

There you go:

```

dmesg | grep -i intel
[    0.000000]   Intel GenuineIntel
[    0.000000] ACPI: LPIT 0x0000000087C270F0 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000087C27188 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000087C273D0 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x0000000087C29F80 000C45 (v02 INTEL  Ther_Rvp 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x0000000087C2ABC8 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x0000000087C2AC00 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x0000000087C2AC58 000619 (v02 INTEL  xh_rvp10 00000000 INTL 20120913)
[    0.000000] ACPI: ASF! 0x0000000087C2C0D0 0000A5 (v32 INTEL   HCG     00000001 TFSM 000F4240)
[    0.000000] Reserving Intel graphics stolen memory at 0x89000000-0x8cffffff
[    0.088228] smpboot: CPU0: Intel(R) Pentium(R) CPU G4400T @ 2.90GHz (family: 0x6, model: 0x5e, stepping: 0x3)
[    0.088239] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.733398] intel_idle: MWAIT substates: 0x142120
[    0.733398] intel_idle: v0.4.1 model 0x5E
[    0.733399] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.756483] Intel P-state driver initializing.
[    0.756486] intel_pstate: HWP enabled
[    0.955927] igb: Intel(R) Gigabit Ethernet Network Driver - version 5.3.0-k
[    0.955929] igb: Copyright (c) 2007-2014 Intel Corporation.
[    0.965306] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    0.965307] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    0.984936] igb 0000:04:00.0: Intel(R) Gigabit Ethernet Network Connection
[    1.029380] fb: switching to inteldrmfb from VESA VGA
[    1.236885] fbcon: inteldrmfb (fb0) is primary device
[    1.236942] i915_bpo 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.466370] WARNING: CPU: 0 PID: 31 at /build/linux-5vkMGy/linux-4.4.0/ubuntu/i915/intel_pm.c:3671 skl_update_other_pipe_wm+0x16c/0x180 [i915_bpo]()
[    1.466373]  uas usb_storage psmouse e1000e(+) igb dca ptp pps_core i915_bpo intel_ips i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm ahci libahci video wmi i2c_hid hid pinctrl_sunrisepoint pinctrl_intel fjes
[    1.466441]  [<ffffffffc01f01ef>] ? intel_ddi_enable_transcoder_func+0x17f/0x260 [i915_bpo]
[    1.466451]  [<ffffffffc0162f2e>] intel_update_watermarks+0x1e/0x30 [i915_bpo]
[    1.466481]  [<ffffffffc01bdc0e>] ? intel_finish_crtc_commit+0xe/0x10 [i915_bpo]
[    1.466501]  [<ffffffffc01ce4d6>] intel_atomic_commit+0x5d6/0x14a0 [i915_bpo]
[    1.466564]  [<ffffffffc01e90ee>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915_bpo]
[    1.734823] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    8.336793] Bluetooth: HCI UART protocol Intel registered
[    9.510518] Intel(R) Wireless WiFi driver for Linux
[    9.510519] Copyright(c) 2003- 2015 Intel Corporation
[   10.523035] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[   10.570216] iwlwifi 0000:05:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[   10.604397] intel_rapl: Found RAPL domain package
[   10.604400] intel_rapl: Found RAPL domain core
[   10.604401] intel_rapl: Found RAPL domain uncore
[   10.604402] intel_rapl: Found RAPL domain dram
[   10.663067] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[   10.663109] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[   10.663147] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[   10.663187] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[   10.663225] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[   10.663262] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[   10.663298] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
[   10.663335] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
[   10.663370] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input18
[   10.663408] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input19

```

---

### Post by jeremy31 on 2016-08-10
Follow the guide [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078) and file a bug report on package linux

There is some support in the kernel source code but it doesn't appear to work correctly as usually Intel bluetooth devices need firmware and dmesg isn't showing any firmware being loaded or reporting firmware missing

---

