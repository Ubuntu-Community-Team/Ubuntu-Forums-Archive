---
title: "Bluetouth not detected on 14.04.1 LTS"
date: 2015-10-10
forum: Hardware
---

### Post by madino55 on 2015-10-10
Hello,
I installed the LTS 14.04.03 initially , but following problems with NVIDIA graphics card on 14.O4.3 LTS , I have installed the 14.04.01 LTS , but now I have  problem with the Bluetooth , it detects nothing and is not detected;
I did :

```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux jaouad-Inspiron-3442 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I got 
```

06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: wl
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:0652]
    Kernel driver in use: r8169
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 004: ID 0c45:6a04 Microdia 
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   11.553794] Bluetooth: Core ver 2.17
[   11.553806] Bluetooth: HCI device and connection manager initialized
[   11.553813] Bluetooth: HCI socket layer initialized
[   11.553814] Bluetooth: L2CAP socket layer initialized
[   11.553817] Bluetooth: SCO socket layer initialized
[   11.755561] Bluetooth: can't load firmware, may not work correctly
[   13.753862] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.753866] Bluetooth: BNEP filters: protocol multicast
[   13.753875] Bluetooth: BNEP socket layer initialized
[   13.758552] Bluetooth: RFCOMM TTY layer initialized
[   13.758564] Bluetooth: RFCOMM socket layer initialized
[   13.758568] Bluetooth: RFCOMM ver 1.11
[  106.589116] Modules linked in: bbswitch(OX) rfcomm bnep snd_hda_codec_hdmi snd_hda_codec_realtek joydev hid_rmi dell_wmi sparse_keymap mxm_wmi rts5139(C) uvcvideo videobuf2_vmalloc videobuf2_memops btusb videobuf2_core bluetooth videodev intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm dell_laptop dcdbas crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd wl(POX) serio_raw cfg80211 snd_hda_intel snd_hda_codec snd_seq_midi snd_seq_midi_event snd_rawmidi snd_hwdep snd_seq snd_pcm i915 snd_seq_device snd_page_alloc lpc_ich snd_timer shpchp i2c_hid snd mei_me mei soundcore drm_kms_helper drm i2c_algo_bit parport_pc ppdev video dw_dmac i2c_designware_platform dw_dmac_core i2c_designware_core wmi lp mac_hid parport hid_generic usbhid hid ahci libahci r8169 mii [last unloaded: nvidia]
[    0.140389] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   11.755044] usb 1-1.6: Direct firmware load failed with error -2
[   11.755561] Bluetooth: can't load firmware, may not work correctly
[   13.159001] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
bluetooth             391136  22 bnep,btusb,rfcomm
jaouad@jaouad-Inspiron-3442:~$ Linux jaouad-Inspiron-3442 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

can you help me? thanks

---

### Post by jeremy31 on 2015-10-10
It looks like it is just missing firmware and a search found this
```
wget https://www.dropbox.com/s/9ryy3ir1tby6wrf/fw-0a5c_21d7.hcd
sudo cp fw-0a5c_21d7.hcd /lib/firmware/
sudo modprobe -r btusb
sudo modprobe btusb
```

And bluetooth should function

---

### Post by madino55 on 2015-10-10
YES, All is OK, Thank you very much

---

