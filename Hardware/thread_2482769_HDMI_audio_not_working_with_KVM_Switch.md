---
title: "HDMI audio not working with KVM Switch"
date: 2023-01-10
forum: Hardware
---

### Post by jav0 on 2023-01-10
Hello, 

I am using Ubuntu 22.04 LTS and I am unable to get sound no matter what I try. The problem comes because I am using a TESmart KVM switch to share 2 monitors and the keyboard + mouse with two PCs (my laptop and my desktop, the last one is where I have Ubuntu installed). The KVM connects all the stuff via HDMI and USB. On Windows I have audio 

I have read dozens of posts, forums, etc, all the stuff with pacmd listing sinks, cards, profiles, with pavucontrol tweaks, with pulseaudio killing and restarting daemons, with alsamixer, with modprobe stuff, and nothing works.

If I list the cards with pacmd it seems that the internal audio card is detected correctly (HDA Intel PCH), but no idea if the problems comes with the configuration of sinks, sources or pacmd clients, or with alsa, or whatever.

Can someone please help me? I would be very grateful.

Thanks.

---

### Post by jav0 on 2023-01-12
Just to provide more info, this is my current configuration:

Monitor 1: HDMI <------> KVM: HDMI
Monitor 2: HDMI <------> KVM: HDMI

Laptop (Monitor 1): USB-C to HDMI <------> KVM: HDMI
Laptop (Monitor 2): HDMI <------> KVM: HDMI

Destkop (Monitor 1): HDMI <------> KVM: HDMI
Destkop (Monitor 2): DisplayPort to HDMI <------> KVM: HDMI

And the sound from KVM is connected directly to my speakers via 3.5 jack.

One thing that I consider extremely important is that some months ago I installed Debian stable in my Desktop and the sound worked! However, when I switched to Debian testing (because Debian stable is tooo old) sound stopped working. So my guess is that there is something related to new Linux/Debian/Ubuntu versions/kernels/firmwares/configurations/whatever that made the sound work before, but not afterwards.

Any ideas please? I'm a lot of months without being able to use Ubuntu and I need it for work.

Thank you very much

---

