---
title: "Getting sound in work in ubuntu"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by VTHokie on 2005-03-25
Hi all,
I'm new to ubuntu and fairly new to linux as well, the biggest problem I'm having with linux is that no matter what, I cannot get it to produce any sound whatsoever.  When I tested this computer initially with Windows everything was detected and sound was produced easily.  Ubuntu detected my sound cards easily which are two cards: a Soundblaster Live! and my onboard sound NVidia NForce2 but as always I can not seem to get any sound.  When I opened my /proc/asound/cards I see that the onboard card is 0 and the SB is 1 but I'm not sure if that should matter.  

My lsmod is:

Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230148  8
button                  6936  0
ac                      5132  0
battery                 9740  0
emu10k1_gp              3840  0
snd_emu10k1            80776  2
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9120  1 snd_emu10k1
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
snd_intel8x0           33068  3
snd_ac97_codec         59268  2 snd_emu10k1,snd_intel8x0
snd_pcm_oss            48296  0
snd_mixer_oss          16640  4 snd_pcm_oss
snd_pcm                85540  3 snd_emu10k1,snd_intel8x0,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc         11144  3 snd_emu10k1,snd_intel8x0,snd_pcm
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  2 snd_emu10k1,snd_mpu401_uart
snd_seq_device          7944  2 snd_emu10k1,snd_rawmidi
snd                    50660  16 snd_emu10k1,snd_util_mem,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  4 snd
forcedeth              16128  0
ehci_hcd               27780  0
ohci_hcd               19460  0
usbcore               104292  4 ehci_hcd,ohci_hcd
nvidia_agp              7580  1
agpgart                31784  1 nvidia_agp
analog                 10784  0
gameport                4736  3 emu10k1_gp,snd_intel8x0,analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
tsdev                   7168  0
evdev                   9216  0
mousedev               10124  1
psmouse                17800  0
ext3                  109672  1
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  3
amd74xx                13340  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26160  690
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

I've tried a number of times to work with alsa (going through the guides) but I'm really getting frustrated as this is the only thing I cannot get finished and I have not idea what to do anymore.  Thanks in advance for any help anyone can give me.

VTHokie

---

### Post by Jones on 2005-03-25
not sure if this will help, but it allowed me to get some sound.

Right click on the sound icon in the upper right of the screen and open volume controls. make sure that the device you are using isn't muted at all.

---

### Post by VTHokie on 2005-03-26
Ok, I tried to fiddle with the controls and I unmuted the Sound Blaster that had the master and pcm muted but I still didn't get any sound.  I tried muting the onboard sound but I still couldn't get any sound either.  Does anyone think that something is interfering with the sound card, maybe one or the other is preventing any from producing sound?  Thanks again for your help with this!  ;) 

VTHokie

---

### Post by mercurus on 2005-03-26
Hi there

[QUOTE=VTHokie]Ok, I tried to fiddle with the controls and I unmuted the Sound Blaster that had the master and pcm muted but I still didn't get any sound.  I tried muting the onboard sound but I still couldn't get any sound either.  Does anyone think that something is interfering with the sound card, maybe one or the other is preventing any from producing sound?  Thanks again for your help with this!  ;) [/quote]

Are you using the standard Warty kernel (2.6.8-1) or have you manually updated the kernel? If so, what is the new kernel version, and where did you obtain the packages ?

You have two sound cards ... do you need both ?
My advice would be to reboot your machine, enter the BIOS and disable the on-board nVidia sound card. The SB Live! is probably a better card, and it is well supported by the emu10k1 module. At least with only one soundcard in operation (ALSA and OSS emulation) you've got half as many potentially muted channels. Additionally, with only one card, you know which speaker jacks to use and it limits the potential for conflict between the two devices for the same sound channels :)

I would imagine that you have four tabs in your gnome-mixer panel at the moment. Once you've disabled one card you should only have two tabs there, and make sure that everything is appropriately unmuted. You can also use alsamixer from the command line - look out for "MM" above particular channels, and use the "M" key to unmute everything.

There was an issue with certain chipsets needing particular (unused) channels to be muted before sound was available in 2.6.10 and 2.6.11 (iirc). I simply searched google for my card's chipset (an Intel Centrino one) and I found a post to a kernel development mailing list on Gmane that set me straight.

---

### Post by VTHokie on 2005-03-26
Thanks a lot mercurus!  :grin:  
While I do not have sound fully working, but I disabled my onboard card in the bios and I can now hear system sounds when I couldn't before so I'm real close now.  I guess I just need to go through the gnome music control and figure out what needs to be muted and what doesn't because I sort of went back and forth on this muting and unmuting certain combos of things before.  Does it matter if everything is unmuted or will this be causing further complications because I've only tested an audio cd, but can't hear anything?  Thanks again for all the help as now I've almost got this OS fully functioning.  :-P 

VTHokie

---

### Post by franco on 2005-03-27
Hi,

I had the same problem. #-o  I have been deaf  :-$ for three months but today, due to your suggestions,  =D>  I solved the problem. I'm so happy that I wanted you to know about it.  :D 

Thank you mercurus and VTHokie. :-({|= 

Anyway, my motherboard is an ASUS P4P800 Deluxe and I do have a SoundBlaster as well. I hope that this could be useful to someone else.

---

