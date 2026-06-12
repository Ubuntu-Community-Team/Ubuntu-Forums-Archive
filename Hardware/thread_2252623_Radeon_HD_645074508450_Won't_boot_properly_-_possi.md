---
title: "Radeon HD 6450/7450/8450: Won't boot properly - possible video driver issue"
date: 2014-11-13
forum: Hardware
---

### Post by Nagle75 on 2014-11-13
A couple months ago after an update I began to have problems with booting up. When I start up, it hangs at a purple screen & does not finish booting. The only way that I can get it to boot is to choose "previous linux versions" from the GRUB  boot list, & at the next screen choose "recovery console", which sends me to another screen where I have to choose "Resume...", & then "OK" & from there it will finish booting. I found another thread here that lead me to believe that this is some kind of video card driver issue, because I had never previously had any problems like this. [http://ubuntuforums.org/showthread.php?t=2012657](http://ubuntuforums.org/showthread.php?t=2012657) My skill level is beginner so I need some guidance on how to proceed. Please note that I work long hours so I may not respond until 6pm (EST) this evenin'. Thanks in advance for your help. :)

---

### Post by kc1di on 2014-11-13
Hi Nagle75 , 

I believe your problem is video card driver related, but it would help us to help you if we had a little more information on your video card.

If it's nvidia - which I also have - the Kernel modesetting parameter is at fault. and you must boot with nomodeset parameter and then install the correct nvidia propritory driver for your
card. 

In any event please give us a little more info to go on. 
What version of ubuntu are you using also? 

Thanks :)

---

### Post by Nagle75 on 2014-11-13
Hello, thanks for responding, :) I'm using Ubnutu Precise 12.04 & the video card I'm currently using is:
sudo lshw -C video | grep product:
       product: Caicos [Radeon HD 6450/7450/8450]

---

### Post by kc1di on 2014-11-14
Hello Again Nagle75,

Unfortunately I have limited experience with AMD/ATI video cards , but I seem to remember there was a problem with the drivers at about Ubuntu 12.04.2 or .5 Xorg changed I think and the drivers no longer worked correctly , but maybe someone with more knowledge will chime in here. 

In the meantime could you list the output of
```
lsmod
```

---

### Post by Nagle75 on 2014-11-14
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180113  10 rfcomm,bnep
binfmt_misc            17540  1 
lp                     17799  0 
snd_hda_codec_hdmi     36724  1 
snd_hda_codec_realtek    46287  1 
snd_emu10k1_synth      17293  0 
snd_emux_synth         42825  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      17854  1 snd_emux_synth
snd_hda_intel          39374  5 
snd_emu10k1           157352  3 snd_emu10k1_synth
snd_hda_codec         192702  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_ac97_codec        134869  1 snd_emu10k1
ac97_bus               12730  1 snd_ac97_codec
snd_util_mem           14117  2 snd_emux_synth,snd_emu10k1
snd_hwdep              17764  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_pcm                97275  5 snd_hda_codec_hdmi,snd_hda_intel,snd_emu10k1,snd_hda_codec,snd_ac97_codec
fglrx                8076470  128 
snd_seq_midi           13324  0 
snd_rawmidi            30748  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
snd_seq                61929  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              29990  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14540  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79081  28 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_emux_synth,snd_seq_virmidi,snd_hda_intel,snd_emu10k1,snd_hda_codec,snd_ac97_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18529  3 snd_hda_intel,snd_emu10k1,snd_pcm
soundcore              15091  1 snd
ppdev                  17113  0 
parport_pc             32866  1 
parport                46562  3 lp,ppdev,parport_pc
serio_raw              13211  0 
dm_multipath           23275  0 
mac_hid                13253  0 
raid10                 35489  0 
raid456                58482  0 
async_pq               13187  1 raid456
async_xor              12879  2 raid456,async_pq
async_memcpy           12529  1 raid456
async_raid6_recov      12824  1 raid456
usbhid                 47238  0 
hid                    99883  1 usbhid
firewire_ohci          41000  0 
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  62190  0 
raid6_pq               88382  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  35572  1 
raid0                  17229  0 
multipath              13145  0 
linear                 12894  0 
dm_raid45              78155  0 
xor                    12894  2 async_xor,dm_raid45
dm_mirror              22203  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash

---

### Post by Nagle75 on 2014-11-20
Does anyone have any ideas on how to fix this issue? Would updating to the latest release fix this issue, or would it only complicate matters? If someone would be so kind to respond here... thanks so much :)

---

