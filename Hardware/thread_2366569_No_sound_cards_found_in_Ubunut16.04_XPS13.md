---
title: "No sound cards found in Ubunut16.04 XPS13"
date: 2017-07-19
forum: Hardware
---

### Post by hamzamalik0123 on 2017-07-19
Hi,

I had an issue with my Dell XPS 13 where the sound would stop working suddenly and would start again after reboot. I tried to fix this issue by following some online instructions and now I dont have any sound, system says no soundcards found and my sound settings shows Dummy Output. Please help!

---

### Post by CatKiller on 2017-07-19
"Following some online instructions" is not at all indicative of what steps you took to break your sound.

---

### Post by hamzamalik0123 on 2017-07-19
It was purging and reinstalling alsa I think ...

---

### Post by hamzamalik0123 on 2017-07-19
If this helps ... 
```


!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Wed Jul 19 15:51:33 UTC 2017


!!Linux Distribution
!!------------------

Ubuntu 16.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04.2 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial


!!DMI Information
!!---------------

Manufacturer:      Dell Inc.
Product Name:      XPS 13 9360
Product Version:   
Firmware Version:  1.3.5
Board Vendor:      Dell Inc.
Board Name:        0PF86Y


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ACPI0003:00/status 	 15
/sys/bus/acpi/devices/ACPI000C:00/status 	 15
/sys/bus/acpi/devices/DLL075B:01/status 	 15
/sys/bus/acpi/devices/DLLK075B:00/status 	 15
/sys/bus/acpi/devices/INT33A1:00/status 	 15
/sys/bus/acpi/devices/INT33D2:00/status 	 11
/sys/bus/acpi/devices/INT33D3:00/status 	 15
/sys/bus/acpi/devices/INT33D4:00/status 	 15
/sys/bus/acpi/devices/INT33D5:00/status 	 15
/sys/bus/acpi/devices/INT33D6:00/status 	 15
/sys/bus/acpi/devices/INT3400:00/status 	 15
/sys/bus/acpi/devices/INT3403:00/status 	 15
/sys/bus/acpi/devices/INT3403:01/status 	 15
/sys/bus/acpi/devices/INT3403:02/status 	 15
/sys/bus/acpi/devices/INT3403:03/status 	 15
/sys/bus/acpi/devices/INT340E:00/status 	 15
/sys/bus/acpi/devices/INT344B:00/status 	 15
/sys/bus/acpi/devices/INT3F0D:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 1
/sys/bus/acpi/devices/LNXPOWER:01/status 	 1
/sys/bus/acpi/devices/LNXPOWER:02/status 	 1
/sys/bus/acpi/devices/LNXPOWER:03/status 	 1
/sys/bus/acpi/devices/LNXPOWER:04/status 	 1
/sys/bus/acpi/devices/LNXPOWER:05/status 	 1
/sys/bus/acpi/devices/LNXPOWER:06/status 	 1
/sys/bus/acpi/devices/LNXPOWER:07/status 	 1
/sys/bus/acpi/devices/LNXPOWER:08/status 	 1
/sys/bus/acpi/devices/LNXPOWER:09/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0a/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0b/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0c/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0d/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0e/status 	 1
/sys/bus/acpi/devices/LNXPOWER:0f/status 	 1
/sys/bus/acpi/devices/LNXPOWER:10/status 	 1
/sys/bus/acpi/devices/LNXPOWER:11/status 	 1
/sys/bus/acpi/devices/LNXPOWER:12/status 	 1
/sys/bus/acpi/devices/LNXPOWER:13/status 	 1
/sys/bus/acpi/devices/MSFT0101:00/status 	 15
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:03/status 	 3
/sys/bus/acpi/devices/PNP0C02:05/status 	 3
/sys/bus/acpi/devices/PNP0C09:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 15
/sys/bus/acpi/devices/PNP0C0F:00/status 	 11
/sys/bus/acpi/devices/PNP0C0F:01/status 	 11
/sys/bus/acpi/devices/PNP0C0F:02/status 	 11
/sys/bus/acpi/devices/PNP0C0F:03/status 	 11
/sys/bus/acpi/devices/PNP0C0F:04/status 	 11
/sys/bus/acpi/devices/PNP0C0F:05/status 	 11
/sys/bus/acpi/devices/PNP0C0F:06/status 	 11
/sys/bus/acpi/devices/PNP0C0F:07/status 	 11
/sys/bus/acpi/devices/device:09/status 	 15
/sys/bus/acpi/devices/device:6c/status 	 15
/sys/bus/acpi/devices/device:7a/status 	 11


!!Kernel Information
!!------------------

Kernel release:    4.7.0-040700-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.7.0-040700-generic
Library version:    1.1.0
Utilities version:  1.1.0


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:9d71 (rev 21) (prog-if 80)
	Subsystem: 1028:075b


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Jul 19 11:59 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jul 19 11:59 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:268: no soundcards found...

ARECORD

arecord: device_list:268: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
cmac
btusb
btrtl
snd_hda_intel
snd_hda_codec
snd_hda_core
snd_hwdep
snd_pcm
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
snd
soundcore
ctr
ccm
ecb
ecryptfs
cbc
encrypted_keys
arc4
ath10k_pci
ath10k_core
ath
mac80211
cfg80211
rfcomm
fuse
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
hid_multitouch
bnep
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_v4l2
videobuf2_core
videodev
media
nvram
msr
i2c_designware_platform
dell_laptop
i2c_designware_core
dell_wmi
sparse_keymap
dell_smbios
dcdbas
tpm_crb
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm_intel
kvm
irqbypass
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
hmac
drbg
ansi_cprng
aesni_intel
aes_x86_64
lrw
glue_helper
ablk_helper
cryptd
xts
gf128mul
dm_crypt
binfmt_misc
joydev
serio_raw
nls_utf8
nls_cp437
vfat
efi_pstore
efivars
dm_mod
fat
rtsx_pci_ms
memstick
shpchp
mei_me
mei
idma64
virt_dma
intel_lpss_pci
intel_pch_thermal
processor_thermal_device
intel_soc_dts_iosf
battery
hci_uart
btbcm
btqca
btintel
soc_button_array
bluetooth
rfkill
int3403_thermal
intel_lpss_acpi
intel_lpss
int340x_thermal_zone
int3400_thermal
acpi_thermal_rel
ac
tpm_tis
acpi_pad
tpm
acpi_als
evdev
kfifo_buf
industrialio
parport_pc
ppdev
lp
parport
efivarfs
autofs4
ext4
crc16
jbd2
mbcache
btrfs
xor
raid6_pq
mmc_block
hid_generic
usbhid
rtsx_pci_sdmmc
mmc_core
i915
crc32c_intel
psmouse
i2c_algo_bit
drm_kms_helper
nvme
xhci_pci
nvme_core
xhci_hcd
rtsx_pci
drm
usbcore
mfd_core
usb_common
thermal
wmi
i2c_hid
hid
video
button
fjes


!!ALSA/HDA dmesg
!!--------------

[   10.443952] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.498317] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   10.498476] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   10.606281] EFI Variables Facility v0.08 2004-May-17
[   10.612461] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[   10.613599] pstore: Registered efi as persistent store backend
[   10.613971] FAT-fs (nvme0n1p1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[   10.614002] snd_hda_intel 0000:00:1f.3: no codecs found!
[   10.635847] device-mapper: uevent: version 1.0.3
--
[   33.332740] FAT-fs (mmcblk0p1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  752.615882] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[  752.727891] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[  752.729554] snd_hda_intel 0000:00:1f.3: no codecs found!
[ 1680.464715] SUPR0GipMap: fGetGipCpu=0x3
--
[ 9363.976038] Modules linked in:
[ 9363.976040]  cmac btusb btrtl snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore ctr ccm ecb ecryptfs cbc encrypted_keys arc4 ath10k_pci ath10k_core ath mac80211 cfg80211 rfcomm fuse pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) hid_multitouch bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core videodev media nvram msr i2c_designware_platform dell_laptop i2c_designware_core dell_wmi sparse_keymap dell_smbios dcdbas tpm_crb intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel hmac drbg ansi_cprng aesni_intel aes_x86_64 lrw glue_helper ablk_helper cryptd xts gf128mul dm_crypt binfmt_misc
[ 9363.976079]  joydev serio_raw nls_utf8 nls_cp437 vfat efi_pstore efivars dm_mod fat rtsx_pci_ms memstick shpchp mei_me mei idma64 virt_dma intel_lpss_pci intel_pch_thermal processor_thermal_device intel_soc_dts_iosf battery hci_uart btbcm btqca btintel soc_button_array bluetooth rfkill int3403_thermal intel_lpss_acpi intel_lpss int340x_thermal_zone int3400_thermal acpi_thermal_rel ac tpm_tis acpi_pad tpm acpi_als evdev kfifo_buf industrialio parport_pc ppdev lp parport efivarfs autofs4 ext4 crc16 jbd2 mbcache btrfs xor raid6_pq mmc_block hid_generic usbhid rtsx_pci_sdmmc mmc_core i915 crc32c_intel psmouse i2c_algo_bit drm_kms_helper nvme xhci_pci nvme_core xhci_hcd rtsx_pci drm usbcore mfd_core usb_common thermal wmi i2c_hid hid video button fjes [last unloaded: btrtl]
--
[12947.585741] Modules linked in:
[12947.585743]  cmac btusb btrtl snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore ctr ccm ecb ecryptfs cbc encrypted_keys arc4 ath10k_pci ath10k_core ath mac80211 cfg80211 rfcomm fuse pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) hid_multitouch bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core videodev media nvram msr i2c_designware_platform dell_laptop i2c_designware_core dell_wmi sparse_keymap dell_smbios dcdbas tpm_crb intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel hmac drbg ansi_cprng aesni_intel aes_x86_64 lrw glue_helper ablk_helper cryptd xts gf128mul dm_crypt binfmt_misc
[12947.585791]  joydev serio_raw nls_utf8 nls_cp437 vfat efi_pstore efivars dm_mod fat rtsx_pci_ms memstick shpchp mei_me mei idma64 virt_dma intel_lpss_pci intel_pch_thermal processor_thermal_device intel_soc_dts_iosf battery hci_uart btbcm btqca btintel soc_button_array bluetooth rfkill int3403_thermal intel_lpss_acpi intel_lpss int340x_thermal_zone int3400_thermal acpi_thermal_rel ac tpm_tis acpi_pad tpm acpi_als evdev kfifo_buf industrialio parport_pc ppdev lp parport efivarfs autofs4 ext4 crc16 jbd2 mbcache btrfs xor raid6_pq mmc_block hid_generic usbhid rtsx_pci_sdmmc mmc_core i915 crc32c_intel psmouse i2c_algo_bit drm_kms_helper nvme xhci_pci nvme_core xhci_hcd rtsx_pci drm usbcore mfd_core usb_common thermal wmi i2c_hid hid video button fjes [last unloaded: btrtl]
--
[15789.560874] Modules linked in:
[15789.560876]  cmac btusb btrtl snd_hda_intel snd_hda_codec snd_hda_core snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore ctr ccm ecb ecryptfs cbc encrypted_keys arc4 ath10k_pci ath10k_core ath mac80211 cfg80211 rfcomm fuse pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) hid_multitouch bnep uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core videodev media nvram msr i2c_designware_platform dell_laptop i2c_designware_core dell_wmi sparse_keymap dell_smbios dcdbas tpm_crb intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel hmac drbg ansi_cprng aesni_intel aes_x86_64 lrw glue_helper ablk_helper cryptd xts gf128mul dm_crypt binfmt_misc
[15789.560922]  joydev serio_raw nls_utf8 nls_cp437 vfat efi_pstore efivars dm_mod fat rtsx_pci_ms memstick shpchp mei_me mei idma64 virt_dma intel_lpss_pci intel_pch_thermal processor_thermal_device intel_soc_dts_iosf battery hci_uart btbcm btqca btintel soc_button_array bluetooth rfkill int3403_thermal intel_lpss_acpi intel_lpss int340x_thermal_zone int3400_thermal acpi_thermal_rel ac tpm_tis acpi_pad tpm acpi_als evdev kfifo_buf industrialio parport_pc ppdev lp parport efivarfs autofs4 ext4 crc16 jbd2 mbcache btrfs xor raid6_pq mmc_block hid_generic usbhid rtsx_pci_sdmmc mmc_core i915 crc32c_intel psmouse i2c_algo_bit drm_kms_helper nvme xhci_pci nvme_core xhci_hcd rtsx_pci drm usbcore mfd_core usb_common thermal wmi i2c_hid hid video button fjes [last unloaded: btrtl]


```

---

### Post by Yellow Pasque on 2017-07-19
I see that you're using a custom 4.7 mainline kernel. Is there a reason for that?

```
[  752.615882] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[  752.727891] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[  752.729554] snd_hda_intel 0000:00:1f.3: no codecs found!
```

That's not good. You can try playing with probe_mask to overcome this error, but I have a feeling that even if you do that, you will still lose sound randomly, because there are kernel faults in your dmesg (where it prints "Modules linked in" at the end of your alsa info). More info will be needed (like tail end of dmesg) if you want to see what's causing the faults. But again, you're using a custom kernel, so I don't know how much help you're going to get troubleshooting the errors.
I think my sugggestion to you would be to try a LiveUSB of Ubuntu 17.04 and see if you have  the same issue(s) there.

---

### Post by hamzamalik0123 on 2017-07-21
Someone suggested updating the kernal might fix the sound. Thats why its  on 4.7 generic. Im really new to ubuntu or say linux. Still sound not working.

---

### Post by vasa1 on 2017-07-21
> **hamzamalik0123 said:**
> ... Still sound not working.
Did you do what Temüjin suggested or not?> I think my sugggestion to you would be to try a LiveUSB of Ubuntu 17.04 and see if you have the same issue(s) there.

---

### Post by hamzamalik0123 on 2017-07-24
Yes, i did try that. It didnt change anything. I'm thinking to reinstall ubuntu 16.04. Hopefully that will help.

---

### Post by Yellow Pasque on 2017-07-24
> **hamzamalik0123 said:**
> Yes, i did try that. It didn't change anything.

Be more specific. When you tried the Live USB, did you have no sound at all or did you at least have sound after reboot?

---

### Post by hamzamalik0123 on 2017-07-25
> **Temüjin said:**
> [COLOR=#000000]You can try playing with probe_mask to overcome this error[/COLOR] probing manually didnt work. But the live usb worked perfectly fine. So I reinstalled ubuntu 16.04 and everything was back to normal. Thanks!

---

