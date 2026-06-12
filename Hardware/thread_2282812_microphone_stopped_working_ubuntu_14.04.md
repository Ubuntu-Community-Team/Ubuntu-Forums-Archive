---
title: "microphone stopped working ubuntu 14.04"
date: 2015-06-17
forum: Hardware
---

### Post by raffi_1970 on 2015-06-17
Hi!
I have an ASUS X552E. I just got it and for a short time the microphone worked fine in Skype and then one day it suddenly stopped working.

I did what was suggested here
[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

and 
[https://www.youtube.com/watch?v=tULmqpe5Yos](https://www.youtube.com/watch?v=tULmqpe5Yos)

and nothing has changed...

I don't know if this has anything to do with it, but I had been using a bluetooth headset (photive) prior...and I can't seem to get that headset working again either...
any suggestions??

this is my lsmod 

```
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69509  8 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
snd_hda_codec_realtek    77514  1 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
uvcvideo               81073  0 
snd_hda_intel          30469  6 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_controller     30228  1 snd_hda_intel
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
arc4                   12608  2 
ath9k                 137283  0 
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
snd_hwdep              17698  1 snd_hda_codec
asus_nb_wmi            21128  0 
media                  21903  2 uvcvideo,videodev
amd_freq_sensitivity    12615  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
ath9k_common           25638  1 ath9k
kvm_amd                60328  0 
ath9k_hw              446521  2 ath9k_common,ath9k
kvm                   452047  1 kvm_amd
radeon               1412941  5 
snd_pcm               104112  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              652777  1 ath9k
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
aesni_intel           152552  3 
snd_timer              29562  2 snd_pcm,snd_seq
btusb                  32497  0 
aes_x86_64             17131  1 aesni_intel
bluetooth             446409  22 bnep,btusb,rfcomm
ttm                    93588  1 radeon
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
wmi                    19193  1 asus_wmi
drm_kms_helper         61574  1 radeon
drm                   311018  8 ttm,drm_kms_helper,radeon
snd                    79468  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
edac_core              56549  0 
6lowpan_iphc           18702  1 bluetooth
joydev                 17393  0 
shpchp                 37047  0 
fam15h_power           13142  0 
k10temp                13144  0 
serio_raw              13483  0 
i2c_algo_bit           13413  1 radeon
edac_mce_amd           22578  0 
soundcore              15047  2 snd,snd_hda_codec
i2c_piix4              22166  0 
video                  20128  1 asus_wmi
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
psmouse               106722  0 
sdhci_pci              23301  0 
sdhci                  43685  1 sdhci_pci
ahci                   34062  3 
r8169                  71694  0 
libahci                32424  1 ahci
mii                    13934  1 r8169
```

---

### Post by Tsahre on 2015-06-17
The link you sent cannot be looking for. So I have no idea what you did. Can you hear sound or just cannot record sound? Have you tried another jack? Try to update the drivers..

---

### Post by wildmanne39 on 2015-06-17
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by raffi_1970 on 2015-06-20
I can hear sound, but I can't record it.

What I've done thus far:
-check the volume
- check Alsa Mixer
- reinstalled Alsa and Pulse Audio
- installed Ubuntu Audio Development team driver
and [COLOR=#333333][FONT=Roboto]Open terminal and paste "sudo gedit /etc/modprobe.d/alsa-base.conf", hit Enter. It will open a file alsa-base.conf. scroll to the end of the file and add the this "options snd-hda-intel position_fix=1" as a new line, save the file and reboot.[/FONT][/COLOR]


How can I update the drivers?  I think they are all updated.

Also, when I go into the sound settings and increase the volume of the mic it'll register the mic for a split second then nothing.

---

### Post by johnnyzee on 2015-06-26
I have a similar problem. It started a couple months ago. Pulse audio and resident sound programs show that my microphone works. But when using Skype it does not work with or without headset. Also works with Google Hangouts.

My system distro is 14.04 on 64 bit System 76 pc. I am thinking of uninstalling Skype and reloading but I cannot figure out how to do that either. Any hints appreciated.

---

### Post by raffi_1970 on 2015-06-27
to uninstall skype perhaps try this
[http://ubuntuforums.org/showthread.php?t=1695589](http://ubuntuforums.org/showthread.php?t=1695589)

and then [http://www.howopensource.com/2012/10/to-install-skype-4-0-0-8-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/to-install-skype-4-0-0-8-in-ubuntu-12-10-12-04-using-ppa/)

---

