---
title: "Santa Cruz Driver/Sound Loss After Update"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by bzr on 2009-10-13
Hi All,
I've been searching the forums and Internet for the last few days for a solution but cannot find anything that will help. Let me preface my post by saying that the on-board  sound worked before the 2nd to last update but stopped working after I rebooted. I had a problem with my video card which forced me to use Win XP (dual boot) for a few days while i waited for the new vid card. Once the new vid card was installed, the sound worked again until the last update, then the sound stopped. This hasn't happened before, only recently. I have reinstalled my Santa Cruz sound card, which worked fine in 8 but can't get to work in 9.04.  I've tried installing ALSA from their website but keep getting errors on the command "cp /Downloads/alsa-driver-1.0.21.tar.bz2 .", says
"cp: cannot stat `/Downloads/alsa-driver-1.0.21.tar.bz2': No such file or directory"

I've tried installing OSS but why pay for a driver when the OS is free? I've also went back a few releases in GRUB (...15, ...14, ...13, etc.) but the sound isn't there.

I've lsmod'ed and aplay'ed according to all the threads I've found here and elsewhere but seem to be getting nowhere. Most posts were older and I haven't found anything up to date as far as this problem goes. I'm open to almost anything that will get this resolved. Please let me know what info is needed.

Here is "lsmod":
Module                  Size  Used by
binfmt_misc            16776  1 
input_polldev          11912  0 
video                  25872  0 
output                 11008  1 video
lp                     17156  0 
ac97_bus                9856  0 
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83844  1 snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            36352  0 
snd_seq_midi           14496  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57712  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            29984  1 snd_seq_midi
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                61972  0 
pcspkr                 10496  0 
snd_hwdep              15364  0 
snd                    67364  11 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi,snd_timer,snd_seq_device,snd_hwdep
soundcore              15200  1 snd
snd_page_alloc         17032  1 snd_pcm
nvidia               7233756  46 
atl2                   34328  0 
ppdev                  15620  0 
serio_raw              13444  0 
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usb_storage            99648  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

And "aplay -l":
aplay: device_list:217: no soundcards found...

I'd appreciate any help the forum can give. If needed, I don't have a problem reverting back to the on-board sound as I had read in older posts that the Santa Cruz isn't supported in Ubuntu. Not sure how accurate that is now.

Thanks,

---

### Post by Mark Phelps on 2009-10-14
Unless 4Front has changed their policies, their OSS drivers are still free for the downloading.  They have a commercial product, but that's different. 

Click the download button on the link below, click on the Open Sound System logo, select the DEB file for your system and download it:  [http://www.opensound.com/]("http://www.opensound.com/")

You can also go to their Forum and read about Linux installations.

---

### Post by bzr on 2009-10-14
Thanks, Mark.
I tried installing the .deb but keep running across an error stating "No packages found matching oss-linux-4.2-2000_i386.deb". That's the name of the file I downloaded. I followed the instructions but to no avail. I've also posted my issue on their forums, maybe it will get resolved soon.

---

### Post by Mark Phelps on 2009-10-15
bzr:

Sorry the .deb didn't work -- but I'm not terribly surprised.  Until ALSA finally had drivers for my sound card, I was using OSS and always had to build it from source.  

They have source available and instructions for building the drivers on their website.

---

