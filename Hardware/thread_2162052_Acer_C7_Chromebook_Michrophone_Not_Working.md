---
title: "Acer C7 Chromebook Michrophone Not Working"
date: 2013-07-12
forum: Hardware
---

### Post by Cero121 on 2013-07-12
Hi, I downloaded Skype on my Acer C7 Chromebook running Ubuntu 12.04. The mic isn't working. I used "alsamix" in the command terminal and put Mic to 100%, but it still won'twork. Can anyone help me? Thanks in advance!

---

### Post by praseodym on 2013-07-13
Please show
[B]
lsmod[/B]
Deactivate "activate automatic sound settings" in Skype. Is the package "pavucontrol" installed?

---

### Post by Cero121 on 2013-07-13
**lsmod**:

Module                  Size  Used by
fuse                   59885  2 
rfcomm                 25259  0 
snd_hda_codec_hdmi     29062  1 
snd_hda_codec_realtek    49177  1 
memconsole             12352  0 
uvcvideo               59368  0 
videodev               81368  1 uvcvideo
videobuf2_core         25280  1 uvcvideo
videobuf2_vmalloc      12313  1 uvcvideo
videobuf2_memops       12475  1 videobuf2_vmalloc
ath9k                 118119  0 
joydev                 16409  0 
mac80211              318094  1 ath9k
btusb                  16409  0 
bluetooth             143138  13 rfcomm,btusb
ath9k_common           12689  1 ath9k
ath9k_hw              351731  2 ath9k,ath9k_common
rtc_cmos               16409  0 
nm10_gpio              12313  0 
snd_hda_intel          24601  3 
snd_hda_codec          71435  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              12351  1 snd_hda_codec
ath                    21105  3 ath9k,ath9k_common,ath9k_hw
snd_pcm                61468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sdhci_pci              16409  0 
sdhci                  25037  1 sdhci_pci
mmc_core               71579  2 sdhci_pci,sdhci
tg3                   118809  0 
snd_timer              21055  1 snd_pcm
cfg80211              141223  3 ath9k,mac80211,ath
snd_page_alloc         12757  2 snd_hda_intel,snd_pcm

Where is active automatic sounds and settings?



pavucontrol is not installed. Should install it?

---

### Post by praseodym on 2013-07-14
Yes, please install it.

You may want to show the following outputs for sound problems:
```

lsb_release -d
uname -r
cat /proc/asound/cards
aplay -l
aplay /usr/share/sounds/alsa/Noise.wav
lspci -nnk | grep -iA2 audio 
ps -C esd
ps -C arts
ps -C pulseaudio
grep "^audio" /etc/group | grep "$USER" | wc -l
lsmod | grep "snd"
head -n 3 /proc/asound/card0/codec#0
head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs
cat ~/.asoundrc
cat ~/.asoundrc.asoundconf
cat /etc/asound.conf
```
Did you install all the codecs?
[https://wiki.ubuntu.com/EasyCodecInstallation](https://wiki.ubuntu.com/EasyCodecInstallation)

---

### Post by Cero121 on 2013-07-14
Now, the mic was detected, and I can use it,but it is very quiet. I went into System Settings,then Sounds, and clicked on "Input." I turned the input valume to max. It is still quiet. Is there anyway to make my voice sound louder?Or do i just have to speak louder?

---

### Post by praseodym on 2013-07-14
Check your alsamix settings again

---

### Post by Cero121 on 2013-07-14
I did. Mic and Mic Boost are both 100%. Also, whenever I put the input to 100%, when I restart the computer it goes back. Is there anyway to save the changes?

---

