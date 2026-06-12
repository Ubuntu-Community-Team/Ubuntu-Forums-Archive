---
title: "Speakers Audio not sound"
date: 2009-09-17
forum: Hardware
---

### Post by Tres_Iqus on 2009-09-17
The problem I have is that it does not sound the audio when I put the headphones

Notebook model Acer Aspire 5738Z-4025
OS Ubuntu 9.04

# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

# lshw -C sound
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel


best regards =)

---

### Post by MStuani on 2009-09-17
Hey whats`up?

I have almost the same problem withn my HP Pavilion Laptop...but the difference is that i can`t hear the sound from the speakers neither from headphones...if you can help me with that?
i`m a new user of Ubuntu 9.04 so I can`t help you...hahah

See ya

---

### Post by Tres_Iqus on 2009-09-21
Install
apt-get install linux-backports-modules-generic

and edit:
/etc/modprobe.d/alsa-base.conf

add
options snd-hda-intel model=auto

restart

"auto"	auto-config reading BIOS (default)
more info
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

---

### Post by gldalmaso on 2009-12-04
> **Tres_Iqus said:**
> Install
apt-get install linux-backports-modules-generic

and edit:
/etc/modprobe.d/alsa-base.conf

add
options snd-hda-intel model=auto

restart

"auto"    auto-config reading BIOS (default)
more info
[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt)

Thanks, I had the same problem and this solved it for me. Only I went to Synaptic and got linux-backports-modules-karmic-generic

---

### Post by whysea on 2009-12-06
It does not solve it for me tough. With ubuntu 9.10... it used to work for Ubuntu 9.04 (although headphones and speakers were either simultaneously on, or off). Now no sound., Furthermore, the speaker applet says: dummy output! And I hear the sea i.e. my speakers are on... any idea?

---

