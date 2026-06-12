---
title: "Intel HD Audio codecs error"
date: 2008-05-02
forum: Hardware
---

### Post by JKT7 on 2008-05-02
I'm having trouble getting my sound card to work in Hardy. I had this problem in Gutsy as well and was hoping that upgrading to Hardy would fix the problem.

Alsa says that no sound cards are found:
```
$ aplay -l
aplay: device_list:205: no soundcards found...
```

But the card is being detected, with this entry in lspci:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: fast devsel, IRQ 16
        Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
```

The module is loaded:
```
$ lsmod | grep -i snd
snd_hda_intel         344728  0
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

After inspecting the system log, I found this error:
```
[73847.367178] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1113: hda-intel: no codecs initialized
```

Some more information:
```
$ uname -a
Linux torpedo 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Apr 21 2008 for kernel 2.6.24-16-generic (SMP).
```

Anyone have any idea what the "no codecs initialized" error means and how I can resolve it? I'm using the latest alsa, and I had tried compiling alsa manually in Gutsy with no luck.

---

### Post by JKT7 on 2008-05-04
Anyone have any idea? Any help would be greatly appreciated.

---

### Post by jocko on 2008-05-05
This looks like a [bug]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382") I have problems with aswell.
Try one more thing.
What happens when you run alsamixer in a terminal?
If it does work, I can't help you, but if it fails with this error I might be able to help:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

You could try to rebuild the alsa modules:
```
sudo apt-get install module-assistant
sudo module-assistant auto-install alsa
```
The second command will take a while (for me it takes 10-15 minutes).
Reboot when it's finished.

Until the developers fix this bug, this will have to be done after kernel updates and probably if alsa is updated as well. I'm not sure why they haven't fixed it yet, the developers don't seem to care about the [bug report]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382").

---

### Post by JKT7 on 2008-05-05
> **jocko said:**
> This looks like a [bug]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382") I have problems with aswell.
Try one more thing.
What happens when you run alsamixer in a terminal?
If it does work, I can't help you, but if it fails with this error I might be able to help:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

I do get this error when I run alsamixer.

> **jocko said:**
> 
You could try to rebuild the alsa modules:
```
sudo apt-get install module-assistant
sudo module-assistant auto-install alsa
```
The second command will take a while (for me it takes 10-15 minutes).
Reboot when it's finished.

Until the developers fix this bug, this will have to be done after kernel updates and probably if alsa is updated as well. I'm not sure why they haven't fixed it yet, the developers don't seem to care about the [bug report]("https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382").

I ran this and rebooted, and I have no change.

---

### Post by JKT7 on 2008-05-06
Anyone else have any idea what I could try to get this working, or what's causing the "no codecs initialized" error?

---

### Post by JKT7 on 2008-05-09
No one? There must be some way to fix this?

---

### Post by JKT7 on 2008-05-19
bump
Any ideas?

---

### Post by Vraaq on 2008-05-21
Hey, same problem here. Same card, same outcomes. I don't have the "no codecs initialized" error though. Not of much help I'm afraid, haven't found a solution yet. 

Pulseaudio works fine though, zo if I realy want sound I can play it through my husbands computer :D

I assume your soundcard isn't listed in thesoundpreferences either?

---

### Post by JKT7 on 2008-05-27
I just updated to kernel 2.6.24-17 and everything is still the same.

---

### Post by Trollslayer on 2008-05-27
What soundcard do you have? Yes, it sounds silly but there are some very new devices which take time to get drivers for.

---

### Post by JKT7 on 2008-05-27
Sorry, I thought that was clear from my lspci above:
Intel Corporation 82801H (ICH8 Family) HD Audio Controller
is my sound card chipset.

It's an integrated, onboard, Intel ICH8 chipset in a Dell Dimension 9200.

---

### Post by JKT7 on 2008-06-12
Still the same behavior on 2.6.24-18.

---

### Post by zgornel on 2008-06-12
I strongly recommend recompiling the kernel and double checking the options for the sound drivers in the kernel configuration menus. This is an excellent guide on how to do it: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) . I strongly recommend disabling all the options/modules you do not need, the kernel will be smaller and it will take less time to compile. Try also re-configuring the package with ```
sudo dpkg-reconfigure alsa-base linux-sound-base
```. I have the same sound board (but rev. 03) and no probs ...

---

