---
title: "Still having sound problems in Feisty!"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by Eddie Wilson on 2007-05-10
Good Day All,
Well I've finally got everything working properly in Feisty except for the sound. I've posted this problem before and had no solutions. Really I also had the same problem in Edgy and ended up having to go  back to Dapper. I won't do that again. I have a Sound Blaster Live 5.1 sound card that works great in Dapper, Mepis, and Win XP. On Edgy and  Feisty sometimes I have sound and sometimes I don't. You never know when its going to work. I've tried all the post in the forums that I can find and still can't get it to stay the same. It acts like its trying to switch sound cards and I only have one card. Hope someone can help me with this. 
Thank You,
Eddie

---

### Post by martijn_bakker on 2007-05-10
Does your motherboard chipset come with a builtin AC97 audio (which is disabled in BIOS)? (do something like "dmesg | grep Audio")?

I had similar problems, which I solved (for sound output) by:
1. Enabling the AC97 device in the BIOS configuration screen (Linux detected it anyway, so it might as well be there).
2. Using "asoundconfig" to configure my Audigy as my default sound card.
3. Check mixer and output settings to check that your SB-Live is outputting to the analog output and that no channels are muted.

Unfortunately, for input this does not work.

---

### Post by Eddie Wilson on 2007-05-10
> **martijn_bakker said:**
> Does your motherboard chipset come with a builtin AC97 audio (which is disabled in BIOS)? (do something like "dmesg | grep Audio")?

I had similar problems, which I solved (for sound output) by:
1. Enabling the AC97 device in the BIOS configuration screen (Linux detected it anyway, so it might as well be there).
2. Using "asoundconfig" to configure my Audigy as my default sound card.
3. Check mixer and output settings to check that your SB-Live is outputting to the analog output and that no channels are muted.

Unfortunately, for input this does not work.

Thanks for answering. Yes my motherboard does come with a built in AC97 audio which is disabled in the BIOS. I'm at work now but as soon as I get home I'll test your steps and see what happens. Again thank you for your response. Its been hard to get anyone to help me with this problem. I'll let you know what I  find out.
Eddie

---

### Post by Eddie Wilson on 2007-05-14
Well I finally got my sound and audio working properly. Ubuntu was detecting my built in audio on my motherboard and would  sometimes not pick out the proper audio system on bootup. I followed the guide for sound solutions in the forums and was able to resolve this audio issue. Thanks to everyone for their help with my problems.
Eddie

---

