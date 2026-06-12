---
title: "nForce4 integrated Realtek AC97 issues"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by GazaM on 2005-05-27
I have an MSI K8N Neo4 Platinum motherboard. It is an nForce4 motherboard and has an integrated Realtek AC97 sound card. The problem (more of an annoyance really) is that in the sound options, there are two devices for me to choose from when there should just be the Realtek. They are listed as follows:

0: Realtek ALC850 rev 0 (OSS Mixer)
1: NVidia CK804 (ALSA Mixer)

I currently use the NVidia selection as I've heard that ALSA is superior to OSS, but if anyone knows why I get 2 cards detected could you please explain it to me? Also, I have the same problems as everyone else with integrated audio seems to have with multiple sounds and the such. I've tried a guide for getting nForce2 integrated audio working, but sound is crackly and multiple sounds still won't work so if anyone could point me towards fixing these problems I'd be greatful.

---

### Post by benqbasic on 2005-08-23
Hey follow this guide and muilt sounds should work: [http://www.ubuntuforums.org/showthread.php?t=44753&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=44753&page=2&pp=10)

I still get crackly sounds and cant use all 8 channels (only 1).

The two sound cards that are detected are ok.
One is the chipset and the other is the actual device. Alsa and OSS just see different things. I ?think? alsa is a bit more ?generic?(going by the driver support on there website.).

Any help on the crackly sounds and the "single channel problem ](*,) " would be great though.

Thanks.

---

### Post by ry_ry on 2005-08-23
Hi benqbasic.
I had cracking sounds too, but after I followed this guide I now get no cracking or pops. Hope this helps.

How to: Hear multiple sounds using both ESD & ALSA guide
[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=hear+multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=hear+multiple+sounds)

---

### Post by benqbasic on 2005-08-27
Hey,

Thanks for that it worked!!!! 

It was still crackly on AMD64 but on i386 it worked great.

I think the problem on 64bit is that the library is not offically ported to 64bit its done by a guy on the ubuntu forums.

Does anyone have any information on getting 8 channels working on the realtek ac97 chipset.

My mobo is:

DFI Lanparty SLI-DR with the realtek ALC850 (nvidia CK804).

Running ubuntu hoary i386 and AMD64


Thanks,

---

### Post by Jvaldezjr on 2005-08-27
I have the same problem- only my board is an NForce3 board with the same Realtek audio device.  I've even install the NForce and the Realtek drivers, and I can't get 8 channel sound- I only get 2 channel.

---

