---
title: "Fan runs constantly (Asus 1215n)"
date: 2012-04-20
forum: Hardware
---

### Post by heorhiy on 2012-04-20
On my asus 1215n fan runs constantly on high speed, laptop is heating even when machine is idle.

Here is acpitool output
```

acpitool --cpu
  CPU type               : Intel(R) Atom(TM) CPU D525   @ 1.80GHz 
  CPU speed              : 0x107 MHz 
  Cache size             : 1799.978 KB
  Bogomips               : 3599.95 
  Bogomips               : 3599.98 
  Bogomips               : 3599.97 
  Bogomips               : 3599.98 
[B]  Function Show_CPU_Info : could not read directory /proc/acpi/processor/
  Make sure your kernel has ACPI processor support enabled.[/B]


```lsmod output 
```

lsmod
Module                  Size  Used by
joydev                 17393  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_hda_codec_realtek   174055  1 
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
binfmt_misc            17292  1 
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                72846  0 
serio_raw              13027  0 
nouveau               712294  0 
ath9k                 117326  0 
mac80211              436455  1 ath9k
ttm                    65344  1 nouveau
i915                  414603  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
drm_kms_helper         45466  2 nouveau,i915
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
drm                   197692  6 nouveau,ttm,i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  3 ath9k,mac80211,ath
mxm_wmi                12859  1 nouveau
i2c_algo_bit           13199  2 nouveau,i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  2 asus_wmi,mxm_wmi
mac_hid                13077  0 
video                  19068  2 nouveau,i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0 


```I would appreciate any help.

---

### Post by MonkeyPaw on 2012-04-20
Sounds like it's the ION2 that causes the issues. I can't help you, but this old thread might offer some further direction:

[http://ubuntuforums.org/showthread.php?t=1592121](http://ubuntuforums.org/showthread.php?t=1592121)

Looks like Project Bumblebee is a start. It's an attempt to get Optimus (auto switching nVidia/Intel graphics) working.

Good luck!

---

### Post by Fincer on 2012-04-26
Since I have the same laptop, I can confirm it's ION2/Optimus issue. I've got hardly any luck to get Optimus working and as a side effect my 1215n has exactly same symptoms: the fan is running almost all the time.

The reason why fan is running is heat, caused by enabled Optimus chip. Ironically, you're not able to utilize or configure Optimus without *bumblebee* or *ironhide* on Linux (or maybe kernels since version 3.1.5 which are claimed to support hybrid graphic features. I've got no luck, however).

Asus 1215n is one of those "hybrid graphic" laptops, including Intel & Nvidia graphic chips. However, only Intel's less effective chip is supported as default on Linux. Nvidia doesn't support Optimus on Linux. Due to lack of support, the conclusion is that Nvidia's Optimus graphics is like a dead rat on Linux: it uses system resources but gives nothing to you, except heat and greater power consumption.

As far as I've measured that redundant heat, the CPU temperature is slightly above 60 Celsius, varying between 60-70C on Asus 1215n.

The only way you can get rid of that heat is to
1) install bumblebee or ironhide
2) configure ACPI settings manually
3) try newer kernel versions (3.1.5 ->)
4) install M$ Windows (Optimus is officially supported)

Bumblebee is for Ubuntu's from 10.04 LTS ->
Ironhide is a further (newer) version of Bumblebee, targeted to 10.10 ->

---

### Post by lukeiamyourfather on 2012-04-26
> **Fincer said:**
> Since I have the same laptop, I can confirm it's ION2/Optimus issue. I've got hardly any luck to get Optimus working and as a side effect my 1215n has exactly same symptoms: the fan is running almost all the time.

The reason why fan is running is heat, caused by enabled Optimus chip. Ironically, you're not able to utilize or configure Optimus without *bumblebee* or *ironhide* on Linux (or maybe kernels since version 3.1.5 which are claimed to support hybrid graphic features. I've got no luck, however).

Asus 1215n is one of those "hybrid graphic" laptops, including Intel & Nvidia graphic chips. However, only Intel's less effective chip is supported as default on Linux. Nvidia doesn't support Optimus on Linux. Due to lack of support, the conclusion is that Nvidia's Optimus graphics is like a dead rat on Linux: it uses system resources but gives nothing to you, except heat and greater power consumption.

As far as I've measured that redundant heat, the CPU temperature is slightly above 60 Celsius, varying between 60-70C on Asus 1215n.

The only way you can get rid of that heat is to
1) install bumblebee or ironhide
2) configure ACPI settings manually
3) try newer kernel versions (3.1.5 ->)
4) install M$ Windows (Optimus is officially supported)

Bumblebee is for Ubuntu's from 10.04 LTS ->
Ironhide is a further (newer) version of Bumblebee, targeted to 10.10 ->

I have a ThinkPad T420 with the Optimus feature and had trouble with it at first. If you want to use the discreet graphics you still can, just switch the graphics mode in the BIOS to use only the discreet card. Linux or any other operating system will see it as a normal graphics card and completely disregard the Optimus feature.

---

### Post by Fincer on 2012-04-26
Yeah, Optimus laptop and Linux is a pretty bad configuration. It's sad that I bought 1215N instead of 1215B (I prefer the latter) but I just have to deal with it and all exotic features it has until my next laptop purchase.

Well, back to topic.

On Asus 1215n, it's not possible to change between graphics in BIOS. If it was possible, the solution would be pretty easy to carry out: simply disabled one card and enable another. However, both cards (Intel & Nvidia) are enabled on 1215n as default. The only way to disable one over another is to find a method with some ACPI tricks on OS. That's why bumblebee and ironhide exist.

---

### Post by lukeiamyourfather on 2012-04-26
> **Fincer said:**
> Yeah, Optimus laptop and Linux is a pretty bad configuration. It's sad that I bought 1215N instead of 1215B (I prefer the latter) but I just have to deal with it and all exotic features it has until my next laptop purchase.

Well, back to topic.

On Asus 1215n, it's not possible to change between graphics in BIOS. If it was possible, the solution would be pretty easy to carry out: simply disabled one card and enable another. However, both cards (Intel & Nvidia) are enabled on 1215n as default. The only way to disable one over another is to find a method with some ACPI tricks on OS. That's why bumblebee and ironhide exist.

That's lame. :-s

I just assumed everything with Optimus had that feature in the BIOS. Hopefully the software to handle Optimus in Linux improves as the feature becomes more popular.

---

