---
title: "No audio on Ubuntu 20.04.2 LTS"
date: 2021-06-10
forum: Hardware
---

### Post by geragiglio88 on 2021-06-10
Hello everyone, i'm new on Linux, i installed Ubuntu 20.04.2 LTS, i  installed all the drivers but i only got sound on headphones, i also  need sound on the line out but it looks like Ubuntu doesn't detect  drivers or sound device. My motherboard is Gigabyte GA-Z170X-Gaming 3.  Any ideas on how i can resolve this problem? Thanks and sorry for my bad  english.

---

### Post by TheFu on 2021-06-11
How did you determine the drivers weren't loaded and working?

I would use either **inxi -Ax** or **lshw -C multimedia**

For example:
```
$ lshw -C multimedia
  *-multimedia              
       description: Audio device
       product: GP108 High Definition Audio Controller
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:08:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: [COLOR="#00FF00"]driver=snd_hda_intel[/COLOR] latency=0
       resources: irq:84 memory:f6080000-f6083fff
  *-multimedia
       description: Audio device
       product: Family 17h (Models 00h-0fh) HD Audio Controller
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 0.3
       bus info: pci@0000:0a:00.3
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: [COLOR="#00FF00"]driver=snd_hda_intel[/COLOR] latency=0
       resources: irq:86 memory:f6800000-f6807fff
```

Or
```
$ inxi -Ax
Audio:     Card-1 Advanced Micro Devices [AMD] Family 17h (Models 00h-0fh) HD Audio Controller
           [COLOR="#00FF00"]driver: snd_hda_intel[/COLOR] bus-ID: 0a:00.3
           Card-2 NVIDIA GP108 High Def. Audio Controller [COLOR="#00FF00"]driver: snd_hda_intel[/COLOR] bus-ID: 08:00.1
           Sound: Advanced Linux Sound Architecture v: k5.4.0-74-generic
```
If the audio card isn't in the list, then it wasn't recognized.  As you can see above, I have 2 audio controllers - the one of the motherboard and another in the GPU.  Guess which one works with HDMI connections? Hint: the GPU.  All the others, which are what I actually use via analog speakers or headphones or USB devices go through the motherboard audio controller.

---

### Post by geragiglio88 on 2021-06-11
I'm so very new at Linux, i don't really sure if the card it's on the list, i think it is but it seems like theres a problem with the drivers... this is the name of the card in the MB i think and the data i can get from Gigabyte site: **Realtek ALC1150 115dB SNR HD Audio**

This is what i got:
> inxi -Ax
Audio:     Device-1: Intel 100 Series/C230 Series Family HD Audio vendor: Gigabyte driver: snd_hda_intel v: kernel 
           bus ID: 00:1f.3 
           Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] vendor: PC Partner Limited 
           driver: snd_hda_intel v: kernel bus ID: 02:00.1 
           Sound Server: ALSA v: k5.8.0-55-generic 


> $ sudo lshw -C multimedia
  *-multimedia              
       description: Audio device
       product: Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:143 memory:dfe60000-dfe63fff
  *-multimedia
       description: Audio device
       product: 100 Series/C230 Series Chipset Family HD Audio Controller
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:142 memory:dff20000-dff23fff memory:dff00000-dff0ffff

---

### Post by TheFu on 2021-06-11
So, it seems the driver is loaded.  

To validate whether it is a driver version issue or not, boot into any **Try Ubuntu** flash drive - basically that is just the same flash drive you used to install the OS.  Does sound work in that environment?  If it does not, then there could be a hardware problem.  If it does work, then it is either 
[LIST]
[*]kernel version
[*]settings
[/LIST]

Try booting into the last kernel (grub Advanced page). Does that work?  Keep track of the kernel versions that do and don't work.

Figuring out settings issues is harder.  I'd start by creating a new Linux userid, logout, then login under that new username.  Does sound work or not?  If it does, then the most likely issue is settings. Check whether the output accidentally was muted or turned way down.  I've posted about **pavucontrol** here a few times the last few weeks.  Be systematic. Follow what those other posts suggest.

Each of these options assume you've done the prior testing first.  No reason to work on settings if the kernel is the issue.

---

### Post by geragiglio88 on 2021-06-12
I follow the instructions here: [https://www.youtube.com/watch?v=Mn_CqNZaZB8](https://www.youtube.com/watch?v=Mn_CqNZaZB8)
It seems Auto-Mute was enabled on Alsamixer. Problem solved!
Thanks!

---

