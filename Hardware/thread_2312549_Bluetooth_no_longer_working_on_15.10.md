---
title: "Bluetooth no longer working on 15.10"
date: 2016-02-05
forum: Hardware
---

### Post by Peter_Willemsen on 2016-02-05
Hi guys,


I have an asus transformer book t300 chi, it works fine with ubuntu 14.04 (bluetooth as well) but when I try run 15.10 it can recognize my keyboard but can't connect to it.
I tried the following: [http://askubuntu.com/questions/613614/bluetooth-not-working-in-ubuntu-15-04/613622#613622](http://askubuntu.com/questions/613614/bluetooth-not-working-in-ubuntu-15-04/613622#613622)
But no success :( I was hoping you guys know what's going on.

The reason for me for upgrading is because Intel has suspended support for ubuntu 14.04 drivers (normally I like to stick to LTS but that's no longer an option)

Here are my bluetooth details:
```

ubuntu@ubuntu:~$  uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux ubuntu 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5100]
    Kernel driver in use: iwlwifi
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 06cb:11ef Synaptics, Inc. 
Bus 001 Device 004: ID 0bda:57d2 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 13fe:1e00 Kingston Technology Company Inc. Flash Drive 2 GB [ICIDU 2 GB]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   19.331055] Bluetooth: Core ver 2.20
[   19.331075] Bluetooth: HCI device and connection manager initialized
[   19.331080] Bluetooth: HCI socket layer initialized
[   19.331084] Bluetooth: L2CAP socket layer initialized
[   19.331090] Bluetooth: SCO socket layer initialized
[   19.464497] Bluetooth: hci0: read Intel version: 370810011003110e00
[   19.544252] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[   19.779106] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   20.511939] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.511942] Bluetooth: BNEP filters: protocol multicast
[   20.511946] Bluetooth: BNEP socket layer initialized
[   21.735720] Modules linked in: bnep intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel uvcvideo arc4 kvm videobuf2_vmalloc videobuf2_memops videobuf2_core joydev snd_hda_codec_realtek asus_nb_wmi crct10dif_pclmul crc32_pclmul snd_hda_codec_generic ghash_clmulni_intel snd_hda_codec_hdmi v4l2_common asus_wmi iwlmvm aesni_intel videodev sparse_keymap snd_hda_intel snd_hda_codec mac80211 aes_x86_64 lrw gf128mul hid_multitouch media glue_helper snd_hda_core ak8975 btusb ablk_helper snd_hwdep snd_pcm btrtl btbcm input_leds btintel snd_seq_midi cryptd iwlwifi snd_seq_midi_event serio_raw bluetooth snd_rawmidi snd_seq cfg80211 inv_mpu6050 industrialio_triggered_buffer snd_seq_device i2c_mux snd_timer snd processor_thermal_device intel_soc_dts_iosf int3403_thermal soundcore iosf_mbi dw_dmac
[   29.717807] Bluetooth: RFCOMM TTY layer initialized
[   29.717817] Bluetooth: RFCOMM socket layer initialized
[   29.717824] Bluetooth: RFCOMM ver 1.11
[  251.781097] Bluetooth: hci0 urb ffff8802153126c0 failed to resubmit (2)
[  251.886269] Bluetooth: hci0: read Intel version: 370810011003110e0f
[  251.886272] Bluetooth: hci0: Intel device is already patched. patch num: 0f
[   19.343033] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-15.ucode failed with error -2
[   19.343066] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-14.ucode failed with error -2
[   19.432983] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[   19.544252] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[   19.779106] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated

```

---

### Post by Peter_Willemsen on 2016-02-07
Anyone please? :(

---

### Post by tokyobadger on 2016-02-07
[A solution is proposed in this thread](http://ubuntuforums.org/showthread.php?t=1479056) and confirmed by other users to work.

Caveat #1: I'm not using any bluetooth devices in linux
Caveat #2: the solution is not specific to your device
Caveat #3: the thread is over 5 years old
Caveat #4: Ubuntu 15.04 just went EOL

---

### Post by Peter_Willemsen on 2016-02-12
Crap did I say 15.04? I meant 15.10! Sorry I change the title! I thought 15.04 was the latest version

---

