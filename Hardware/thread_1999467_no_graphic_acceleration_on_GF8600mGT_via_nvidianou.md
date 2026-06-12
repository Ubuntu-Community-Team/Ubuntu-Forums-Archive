---
title: "no graphic acceleration on GF8600mGT via nvidia/nouveau"
date: 2012-06-08
forum: Hardware
---

### Post by pacman401 on 2012-06-08
on ubuntu **uname -a**```
Linux hssm 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux
``` and distros witch have kernel compiled in nouveau driver i can't get graphic acceleration

my graphic card
**lspci -vknn|grep VGA**
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G84 [GeForce 8600M GT] [10de:0407] (rev a1) (prog-if 00 [VGA controller])
```

exactly I have acceleration on random boot-up average 1/15 bootups

nvidia drivers installed by "Additional Drivers" creator

adding "nouveau.blacklist=1" as kernel parameter still no graphic accel.

attempts to launch virtual consoles in higher res gfxmode 1024x768(grub2)/vga=773(grub-legacy) cuses black screen

**cat /var/log/Xorg.0.log**
[http://wklej.to/TWEX9/text]("http://wklej.to/TWEX9/text")

**lsmod**
```
Module                  Size  Used by
    rfcomm                 38139  0
    bnep                   17830  2
    parport_pc             32114  0
    ppdev                  12849  0
    dm_crypt               22528  1
    joydev                 17393  0
    btusb                  17912  0
    bluetooth             158438  11 rfcomm,bnep,btusb
    snd_hda_codec_realtek   174055  1
    snd_hda_intel          32765  1
    arc4                   12473  2
    snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
    snd_hwdep              13276  1 snd_hda_codec
    snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
    snd_seq_midi           13132  0
    snd_rawmidi            25424  1 snd_seq_midi
    snd_seq_midi_event     14475  1 snd_seq_midi
    snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
    iwl4965               117368  0
    iwl_legacy             71134  1 iwl4965
    mac80211              436455  2 iwl4965,iwl_legacy
    snd_timer              28931  2 snd_pcm,snd_seq
    snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
    cfg80211              178679  3 iwl4965,iwl_legacy,mac80211
    compal_laptop          19315  0
    r592                   17808  0
    memstick               15857  1 r592
    psmouse                72919  0
    serio_raw              13027  0
    snd                    62064  11 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
    wmi                    18744  0
    uvcvideo               67203  0
    videodev               86588  1 uvcvideo
    soundcore              14635  1 snd
    mac_hid                13077  0
    snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
    lp                     17455  0
    parport                40930  3 parport_pc,ppdev,lp
    usbhid                 41906  0
    hid                    77367  1 usbhid
    ums_cypress            12627  0
    uas                    17828  0
    usb_storage            39646  2 ums_cypress
    firewire_ohci          40172  0
    firewire_core          56906  1 firewire_ohci
    crc_itu_t              12627  1 firewire_core
    sdhci_pci              18324  0
    sdhci                  28241  1 sdhci_pci
    tg3                   141369  0
    video                  19068  0

```

on windows and previous ubuntu versions I have graphic accel. so graphic card is working properly

---

