---
title: "Brightness Issues with 2 Laptops"
date: 2011-06-24
forum: Hardware
---

### Post by thattypicalnerd on 2011-06-24
Alright, I have two laptops, a Samsung Q430-11 (i5 450M, nVidia 310M, some Intel chipset, Ubuntu 11.04, the problem still persists on 10.10), and a Thinkpad T61 (the model with the Quadro graphics, not the X1300, Ubuntu 10.10). Both of these laptops have issues with brightness control.

I'll start with the Q430-11, since it has the bigger problem. I can't adjust brightness at all on this one, no matter what I do. Locked on full, all the time. Funny thing is, it happens on all Unix based systems (Mac OS X has the same problem, so do Fedora, OpenSUSE, and Mint), so I think it has something to do with the graphics. I get full acceleration on all OS's.

The Thinkpad though, is a different story. The brightness control works for the most part, but only goes up to max when using the FN + Home key combo. If I go into Power Management preferences, or try to use the slider, it resets the brightness down to a lower level. I can push it back up with the FN + Home key combo again, but it's quite annoying. Also, the slider in Power Management doesn't work. At all.

I also have another issue with the Thinkpad that is also related to the graphics card. The animations are VERY laggy when minimizing and maximizing windows with medium desktop effects. I don't think the graphics are working properly, as I remember that it handled Windows XP relatively well with all graphic effects and could render 720p with relative ease. Plus, the card isn't that low end :P

So does anyone have any suggestions?

---

### Post by Toz on 2011-06-24
What does ```
lsmod
``` return?

For the Q430, here is an interesting article: [http://www.voria.org/forum/viewtopic.php?f=4&t=834]("http://www.voria.org/forum/viewtopic.php?f=4&t=834"). Apparently he fixed the problem by using the **mbp_nvidia_bl** module (note he uses Arch and its called nvidia_bl there). According to those instructions, he also needed to remove two modules, video and samsung_backlight. Posting back your modules via lsmod will let us see if they are loaded and what they are called.

Also for the 430, if you have an **/etc/X11/xorg.conf** file, adding: ```
Option "RegistryDwords" "EnableBrightnessControl=1"
```to the Device section of this file might work.


Other things to try include the kernel parameters **"acpi_osi=\"Linux\""** and **"acpi_backlight=vendor"**. See: [https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot") for instructions on how to test the parameters.

---

### Post by thattypicalnerd on 2011-06-25
> **Toz said:**
> What does ```
lsmod
``` return?

For the Q430, here is an interesting article: [http://www.voria.org/forum/viewtopic.php?f=4&t=834]("http://www.voria.org/forum/viewtopic.php?f=4&t=834"). Apparently he fixed the problem by using the **mbp_nvidia_bl** module (note he uses Arch and its called nvidia_bl there). According to those instructions, he also needed to remove two modules, video and samsung_backlight. Posting back your modules via lsmod will let us see if they are loaded and what they are called.

Also for the 430, if you have an **/etc/X11/xorg.conf** file, adding: ```
Option "RegistryDwords" "EnableBrightnessControl=1"
```to the Device section of this file might work.


Other things to try include the kernel parameters **"acpi_osi=\"Linux\""** and **"acpi_backlight=vendor"**. See: [https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot]("https://help.ubuntu.com/community/Grub2#Editing%20the%20GRUB%202%20Menu%20During%20Boot") for instructions on how to test the parameters.

lsmod returns-
```
Module                  Size  Used by
rfcomm                 40755  4 
binfmt_misc             7984  1 
sco                     9954  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
parport_pc             30086  0 
ppdev                   6804  0 
nvidia              10221046  41 
joydev                 11363  0 
snd_hda_codec_analog    80317  1 
pcmcia                 40944  0 
snd_hda_intel          26019  2 
arc4                    1497  2 
snd_hda_codec         100919  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
thinkpad_acpi          78535  0 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
iwlagn                202721  0 
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
iwlcore               146875  1 iwlagn
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           24279  0 
tpm_tis                 9894  0 
mac80211              266657  2 iwlagn,iwlcore
led_class               3393  1 thinkpad_acpi
tpm                    16013  1 tpm_tis
nvram                   7990  1 thinkpad_acpi
tpm_bios                6426  1 tpm
snd                    64117  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10357  1 yenta_socket
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  22176  0 
btusb                  12929  2 
output                  2527  1 video
bluetooth              59213  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              170293  3 iwlagn,iwlcore,mac80211
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
intel_agp              32080  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
firewire_ohci          24679  0 
ahci                   21857  0 
libahci                26167  4 ahci
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
e1000e                151787  0 

```

... on the Thinkpad. Trying out the other stuff for the Q430 in a bit.

---

