---
title: "Is Ubuntu using GPU"
date: 2010-10-28
forum: Hardware
---

### Post by beew on 2010-10-28
Hi,

I experience a lot of choppiness and frozen frames when playing higher definition video (say 720P, it is fine with lower resolution videos) I notice that CPU usage is very high in those instances.  I am wondering if Ubuntu is using the GPU or putting all the load on the CPU. How do I find out, and if it is the case how to fix it?

I have a Nvidia Geforce4 Ti 4200 Go graphic card with 64M memory. Screen resolution is 1680X1050(I have tried lower resolutions with no improvement)

The system cpu: 2.2GHz, 512M of ram and swappiness set to 10 (which has improved performance somewhat comparing to the default swappiness value of 60)

Thanks.

P.S. The Nvidia driver (nvidia-96) is installed and activated. Compiz is disabled and I switch to openbox while playing (or trying to) high resolution videos

---

### Post by SeijiSensei on 2010-10-28
Your hardware doesn't support GPU decoding of video even with its NVIDIA card.  Support for the "VDPAU" method of off-loading video decoding to the GPU began with the 8xxx series of NVIDIA adapters.

Usually this problem arises with video encoded with the H.264 codec.  When I had a machine that couldn't decode these smoothly, I took to transcoding them to XviD in the AVI container with mencoder.  There's a slight loss in quality but decoding XviD doesn't put the same demands on the hardware.

---

### Post by Surachinen on 2010-10-28
wow. i thought specs had to be higher for 720/1080 playback.....

has hi-def playback worked on said machine prior to this? i mean the sub-gig of ram and low shader memory makes me arch my eyebrow if it had....

even when running windows seven i thought an nvidia 8400 with 512 texture memory was a bare minimum (my processor was an overclocked athlon 5000+, running at 2.99ghz) and even then it was straining.

but to get right to a nitty gritty answer to your EXACT question. i do no belive ubuntu has a say in what processing unit gets used, i think the application decides that.

---

### Post by Grenage on 2010-10-28
Aye, no VDPAU there.  Perhaps a cheap card on e-bay would get you up to that level?

> **Surachinen said:**
> wow. i thought specs had to be higher for 720/1080 playback.....

has hi-def playback worked on said machine prior to this? i mean the sub-gig of ram and low shader memory makes me arch my eyebrow if it had....

even when running windows seven i thought an nvidia 8400 with 512 texture memory was a bare minimum (my processor was an overclocked athlon 5000+, running at 2.99ghz) and even then it was straining.

but to get right to a nitty gritty answer to your EXACT question. i do no belive ubuntu has a say in what processing unit gets used, i think the application decides that.


The RAM isn't really a factor; the GPU only comes into play if the CPU can't offload.

---

### Post by beew on 2010-10-28
> **SeijiSensei said:**
> Your hardware doesn't support GPU decoding of video even with its NVIDIA card.  Support for the "VDPAU" method of off-loading video decoding to the GPU began with the 8xxx series of NVIDIA adapters.

Usually this problem arises with video encoded with the H.264 codec.  When I had a machine that couldn't decode these smoothly, I took to transcoding them to XviD in the AVI container with mencoder.  There's a slight loss in quality but decoding XviD doesn't put the same demands on the hardware.

Thanks, it is good to know that so I am not wasting my time.

 For lower resolution actually there is no problem at all. I just removed PulseAudio, now  I can play video, with multiple instances of firefox opened and running compiz at the same time and the cpu can still handle it.

---

### Post by beew on 2010-10-28
> **Surachinen said:**
> wow. i thought specs had to be higher for 720/1080 playback.....

has hi-def playback worked on said machine prior to this? i mean the sub-gig of ram and low shader memory makes me arch my eyebrow if it had....

even when running windows seven i thought an nvidia 8400 with 512 texture memory was a bare minimum (my processor was an overclocked athlon 5000+, running at 2.99ghz) and even then it was straining.

but to get right to a nitty gritty answer to your EXACT question. i do no belive ubuntu has a say in what processing unit gets used, i think the application decides that.

Actually I don't know the answer to that. This is a hand me down machine which I use basically for experimenting.

It came with Windows NT and it was very, very slow so I installed XP on it (that was before my Ubuntu days, :)) I don't know whether it could play hig def and never tried (I gave it to a friend and just got it back because he got a new machine) I uninstalled XP and installed Ubuntu  as soon as I got the machine back. But I remember it was very slow on  Xp and freezes a lot as well. In Ubuntu it seems that it runs very smoothly after I changed the swappiness and removed PulseAudio.

There is no way to put windows 7 in this thing even if you can find the drivers, even Vista is impossible, will kill it right the way. :)

---

