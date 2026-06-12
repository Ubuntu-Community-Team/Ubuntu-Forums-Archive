---
title: "No sound"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by kevin1 on 2005-04-23
I have no sound from applications or system, except from the microphone input.

Motherboard is PcChips M848 ALU. 

Onboard sound is described as 'C-Media AC97 Audio Device' and lspci gives:

'0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)'.

lsmod gives: 

snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

No sound card is listed in /etc/modules, but I am not sure whether I need to add anything & if so, what.

When I insert an audio CD the default CD player starts and the progress slider moves ... but no sound.

All volume control sliders are at max.

Multimedia Systems Selector settings are as follows:

Default sink output: ESD - Enlightenment sound daemon, Pipeline: esdsink.
When I click 'Test' the test proceeds ... but without sound.

Default source: ESD - Enlightenment sound daemon, Pipeline: esdmon.
When I click 'Test' the test proceeds ... but without sound.

If I select any other permutation of sink and source, when I click test I get a message 'Failed to construct test pipeline ...', and if I insert an audio CD the default CD player starts, but the progress slider does not move ... and of course, no sound!

I have tried killall esd, but still get nothing via alsa or oss.

I'd really appreciate advice from anyone running V5.04 on this motherboard who has managed to get sound working.

Thanks,

Kevin

---

