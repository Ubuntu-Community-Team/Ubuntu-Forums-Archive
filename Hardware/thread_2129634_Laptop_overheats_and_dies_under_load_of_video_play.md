---
title: "Laptop overheats and dies under load of video play and downloading"
date: 2013-03-26
forum: Hardware
---

### Post by gotnexusbluz on 2013-03-26
I know my hardware is still good (unless it's hardcoding failed to shut it off before damage could happen with the last incident), because I could boot this machine into Windows right now and load it with many more than the relatively few tasks which it was under when it failed under Xubuntu. Of course I would prefer to use Linux instead of Windows, so can anyone tell me wether there's a chance that a different Ubuntu flavor than Xfce may play nicer with my hardware, or if the problem is with Debian?

---

### Post by solarghost on 2013-03-27
I suspect it's your graphics card. Do you have a laptop with two graphics cards? One Intel and one Nvidia or ATI? There have been a few issues with overheating because of discreet graphics cards. If you do have two graphics cards have a look at installing drivers for discreet graphic cards, that will probably sort out your issue.

Also it would help if you provided your laptop make and model.

---

### Post by gotnexusbluz on 2013-03-28
> **solarghost said:**
> I suspect it's your graphics card. Do you have a laptop with two graphics cards? One Intel and one Nvidia or ATI? There have been a few issues with overheating because of discreet graphics cards. If you do have two graphics cards have a look at installing drivers for discreet graphic cards, that will probably sort out your issue.

Also it would help if you provided your laptop make and model.

> **solarghost said:**
> I suspect it's your graphics card. Do you have a laptop with two graphics cards? One Intel and one Nvidia or ATI? There have been a few issues with overheating because of discreet graphics cards. If you do have two graphics cards have a look at installing drivers for discreet graphic cards, that will probably sort out your issue.

Also it would help if you provided your laptop make and model.

Thanks for trying to shed some light on this issue! My laptop is a Toshiba Satellite L305-S5933. Since most Toshiba products aren't supported by the company for Linux by the, I hope there's a  site where somebody is at least trying to support them (so that Linux can rule the world, yahahaha):)

Can you direct me to that site?

---

### Post by gotnexusbluz on 2013-03-29
Hello, I cannot play flash video for more than 20 minutes without my Toshiba laptop overheating and dieing when it reaches the cutoff temperature. I hope there is a sort of driver available somewhere which can resolve this problem. 

I ran lsmod for my Satellite L305-S5933, but the output is much too cryptic for me to understand, so can somebody please take a look and tell me if you see what may cause a conflict with Ubuntu? Whatever it is, it doesn't stop Windows 7, which is a secondary installation on this laptop without manufacturer's drivers (unless MS pushes them through it's update server). Of course I would rather not use Windows for anything, and would be so happy if I could tell friends and family that I can get Ubuntu running on their machines too, so please help me out with this! Here is my lsmod output:
```

[SIZE=1][FONT=courier new]Module                  Size  Used by
dm_crypt               23012  1 
joydev                 17458  0 
arc4                   12530  2 
snd_hda_codec_realtek    78147  1 
rfcomm                 46620  4 
bnep                   18141  2 
parport_pc             32689  0 
snd_hda_intel          33492  4 
bluetooth             209249  10 rfcomm,bnep
snd_hda_codec         134213  2 snd_hda_codec_realtek,snd_hda_intel
ppdev                  17074  0 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
uvcvideo               76750  0 
snd_seq_midi           13325  0 
videobuf2_core         32852  1 uvcvideo
coretemp               13401  0 
snd_rawmidi            30513  1 snd_seq_midi
videodev              120310  2 uvcvideo,videobuf2_core
snd_seq_midi_event     14900  1 snd_seq_midi
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
ath5k                 150269  0 
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
ath                    23828  1 ath5k
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                95595  0 
mac80211              540032  1 ath5k
toshiba_acpi           18727  0 
sparse_keymap          13891  1 toshiba_acpi
serio_raw              13216  0 
snd                     78921  17  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              22804  0 
cfg80211              206797  3 ath5k,ath,mac80211
mac_hid                13206  0 
wmi                    19071  1 toshiba_acpi
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lp                     17760  0 
lpc_ich                17062  0 
parport                46346  3 parport_pc,ppdev,lp
ums_realtek            17950  0 
usb_storage            48834  1 ums_realtek
ahci                   25721  2 
libahci                31192  1 ahci
r8169                  61651  0 
i915                  520615  2 
drm_kms_helper         49113  1 i915
drm                   288721  3 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
video                  19391  1 i915
[/FONT][/SIZE]
```[FONT=system][FONT=courier new]


[/FONT][/FONT]
[FONT=system][FONT=courier new] [/FONT][/FONT]

---

### Post by mörgæs on 2013-03-29
Threads merged.
Please don't create multiple threads on the same subject.

---

### Post by gotnexusbluz on 2013-03-29
Oh,  thanks, Freddy - I was just trying to get this question in a more appropriate forum (maybe hardware) after discovering that it exists, and now that those here have stopped answering you stuck me here to die slowly! 

If you aren't going to help resolve the problem, then I really can't be causing anyone inconvenience. I don't wish to cause anyone that, and I mean that sincerely. But as one who does have the right not to be Canonical's guinea pig and spend all my time trying to work around its bugs (more time than it's worth to me for the cost of a paid system, potential destruction of my hardware), I should expect a more freindly and fair climate in that company's forum. Maybe they think that's too much to expect in the UK and South Africa, but here in America (where it's inroads are least) we feel differently.

---

### Post by Toz on 2013-03-29
This may be relevant (from the Arch wiki): [https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300]("https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300")

> It seems that most of the L300 and L305 series laptops come with the InsydeH2O BIOS version 1.50. This BIOS is faulty with Linux and results in a dead Fn key and an improperly controlled fan.

Which bios version do you have?

---

### Post by Mark Phelps on 2013-03-29
Your hardware is not the issue -- your choice of operating systems is the issue.  WHY?  Because you have Hybrid Graphics situation (mixture of onboard and added video chipsets) for which the ONLY working drivers come for Windows.  The suppliers of these PCs also supply Windows drivers -- which is why it works so well in Windows; unfortunately, they do NOT supply Linux drivers.  And the drivers supplied by AMD, generally speaking, do NOT work in Hybrid Graphics situations.

So basically, the best OS to use with this PC is the one it came with.  IF you insist on using something different, your performance is going to suffer -- not due to the hardware, but instead, due to the lack of drivers.

---

### Post by gotnexusbluz on 2013-03-29
> **Mark Phelps said:**
> Your hardware is not the issue -- your choice of operating systems is the issue.  WHY?  Because you have Hybrid Graphics situation (mixture of onboard and added video chipsets) for which the ONLY working drivers come for Windows.  The suppliers of these PCs also supply Windows drivers -- which is why it works so well in Windows; unfortunately, they do NOT supply Linux drivers.  And the drivers supplied by AMD, generally speaking, do NOT work in Hybrid Graphics situations.

So basically, the best OS to use with this PC is the one it came with.  IF you insist on using something different, your performance is going to suffer -- not due to the hardware, but instead, due to the lack of drivers.

Well, thanks for shedding light on this issue, however dark. What hardware would you recommend for Debian-based Linux?

Can anyone recommend a source to begin educating myself on the finer points of computer hardware, and particularly what works best with Linux? Most people who know me think I know more of this stuff than they do, but I have no idea what most of the lsmod output says of my system, and I'll bet that output isn't the half of it! Where does one go to start learning learning from the uncoded basics to the cryptic stuff which is displayed exclusively for the benefits of supergeeks?

---

### Post by Toz on 2013-03-29
> Because you have Hybrid Graphics situation
Are you sure you have hybrid graphics? According to the specs on that laptop model, it only contains one video card - an Intel GMA 4500M.

---

