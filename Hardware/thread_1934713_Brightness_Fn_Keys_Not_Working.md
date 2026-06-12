---
title: "Brightness Fn Keys Not Working"
date: 2012-03-02
forum: Hardware
---

### Post by dwh1996 on 2012-03-02
I have read various threads addressing issues like mine with nvidia graphics cards, but I have not wanted to try them because I have an intel HD 3000. I am running ubuntu on a samsung series 3 laptop. Everything works fine except the Fn keys for the brightness. I can change the brightness by going into the system settings. When I press the Fn keys it will only let me lower the brightness by one level. The Fn keys work for volume just fine.

---

### Post by Toz on 2012-03-09
Hello and welcome to the forums.

Can you provide some more information about your system? Open a terminal window, type in the following commands, and post back the results:

1. Show your kernel boot command line:
```
cat /proc/cmdline
```

2. Show your system model:
```
sudo dmidecode -s system-product-name
```
...note, you'll need to enter your password to get access to this info.

3. Show what backlight interfaces you have available:
```
ls /sys/class/backlight
```

4. Show which modules you have loaded:
```
lsmod
```

---

### Post by Aragant on 2012-03-25
> **Toz said:**
> Hello and welcome to the forums.

Can you provide some more information about your system? Open a terminal window, type in the following commands, and post back the results:

1. Show your kernel boot command line:
```
cat /proc/cmdline
```



BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=565606ba-b7f7-4f9e-99a8-c1d6c66b5c8d ro quiet splash vt.handoff=7


2. Show your system model:
```
sudo dmidecode -s system-product-name
```...note, you'll need to enter your password to get access to this info.

Aspire 5755G

3. Show what backlight interfaces you have available:
```
ls /sys/class/backlight
```

acpi_video0


4. Show which modules you have loaded:
```
lsmod
```

Module                  Size  Used by
aesni_intel            17758  2
cryptd                 19801  1 aesni_intel
aes_i586               16956  1 aesni_intel
aes_generic            38023  2 aesni_intel,aes_i586
binfmt_misc            13213  1
parport_pc             32111  0
ppdev                  12849  0
snd_hda_codec_hdmi     27479  1
snd_hda_codec_realtek   255820  1
snd_hda_intel          24140  4
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
arc4                   12473  2
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  450944  2
nouveau               621970  1
ath9k                 103633  0
mac80211              257001  1 ath9k
ttm                    65184  1 nouveau
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
drm_kms_helper         40745  2 i915,nouveau
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
drm                   180037  6 i915,nouveau,ttm,drm_kms_helper
uvcvideo               66851  0
videodev               75143  1 uvcvideo
xhci_hcd               68062  0
ath                    19141  2 ath9k,ath9k_hw
i2c_algo_bit           13184  2 i915,nouveau
psmouse                73312  0
serio_raw              12990  0
cfg80211              156212  3 ath9k,mac80211,ath
video                  18951  2 i915,nouveau
sparse_keymap          13666  0
lp                     13349  0
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0
uas                    17676  0
sdhci_pci              13623  0
ahci                   21591  2
tg3                   131476  0
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci



Having same issue that will be kind of anyone who help me in this
Jazak-Allah

---

### Post by Aragant on 2012-03-25
posted same again sorry

---

### Post by Toz on 2012-03-25
Can you try these possible kernel parameters:

**acpi_osi=Linux**
**acpi_backlight=vendor**
**acpi_osi=Linux acpi_backlight=vendor**

Here are instructions on how to test them: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

Add those parameters, _one at a time_, to the end of the line starting "linux...", then press Ctrl+x to continue the boot process. Once you've booted in, for each command:
1. check whether the function keys work _and_
2. Save the results of:
```
cat /proc/cmdline
```

Post back your findings.

---

### Post by mind_exploit on 2013-01-18
Hey, there :)

I did many attempts to make the function keys - and most of all - the brightness ones - work ... with no success ... 
as a result - the line in /etc/default/grub, that starts with GRUB_CMDLINE_LINUX_DEFAULT is:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```so ... do you have any idea what I can do about it? ... 
I'm with Ubuntu 12.04 on Toshiba P855-108.

Thanks in advance ;)

---

