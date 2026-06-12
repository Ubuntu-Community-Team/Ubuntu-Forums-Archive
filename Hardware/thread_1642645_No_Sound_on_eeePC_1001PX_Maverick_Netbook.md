---
title: "No Sound on eeePC 1001PX Maverick Netbook"
date: 2010-12-10
forum: Hardware
---

### Post by djxcon on 2010-12-10
After several hours of troubleshooting, I give up and am turning to the community for help. I recently bought a eeePC and installed Lucid Remix. I had to start with Lucid because Maverick crashed on the install. I did an in-place upgrade to 10.10 and have no sound. I had no sound in Lucid either. 

Now, I did notice that in the Maverick live disc, the computer had perfect sound. 

Here is what I have tried thus far:

Installed pavucontrol no luck.

Checked alsamixer and unmuted everything and turned the volume up on all channels

The pavucontrol shows the audio meter hopping so I know the system "sees" the audio...it just doesn't play it.

Tried this:
> sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
 sudo apt-get update && sudo apt-get dist-upgrade
 sudo apt-get install linux-alsa-driver-modules-$(uname -r)

Tried reinstalling pulse/alsa packages (while removing the .pulse folder) no luck.

Added this line to alsa-base.conf...no luck (options snd-hda-intel model=auto)

Here are some system stats: PLEASE please help...I am going crazy!

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

> kristin@kristin-laptop:~$ lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:f7cf8000-f7cfbfff


---

### Post by ronferds on 2011-01-08
I too have this issue with my Asus eepc R101-PX. No sound. Any suggestions.

---

### Post by ophysis on 2011-01-19
Same here. Anyone?

---

### Post by ronferds on 2011-01-22
has anyone rectified this issue. I am stumped, no sound as well as no microphone working :'(

---

### Post by snesreviews on 2011-02-08
This is far from ideal but I came across this problem too. For me anyway, Alsamixer had no effect on the sound card despite appearing to detect volume levels. I don't know for certain but I would guess this is because it's a dual-purpose port which may be a microphone or headphones.
 
Anyway, this flies in the face of my principles but for now anyway, adding the indicator applet to a panel and using that for volume control worked fine for me (none of the alsa based tools worked for me, but admittedly I didn't fight that much).
 
This is extremely annoying because on an eeepc, space in your panels is a commodity and I hate their mail notification icon and the huge gap between each icon. Yes I know there's probably a gconf setting to disable but I shall duel with that one later.

---

### Post by angryswede on 2011-03-09
This is interesting.  I was having similar issues with this netbook, with a fresh install of the desktop edition; however, with a fresh install of the netbook edition the speakers work fine (But I hate unity taking up so much screen real estate.  Anyway I had the same kernel on both, and ran all the latest updates, so not sure what the difference between the two is.  Anyone have any insight?

---

### Post by JMED106 on 2011-04-21
It seems to be a bug:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498)

---

