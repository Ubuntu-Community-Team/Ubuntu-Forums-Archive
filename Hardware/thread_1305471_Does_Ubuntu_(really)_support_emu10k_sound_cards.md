---
title: "Does Ubuntu (really) support emu10k sound cards?"
date: 2009-10-29
forum: Hardware
---

### Post by Eddward on 2009-10-29
Hi,

Does Ubuntu support the EMU10K sound cards.  Note, this is a loaded question.  If I were to ask "Does Ubuntu support my 3D accelerator video card?" and the answer were "Yes, it just won't let you use any of the hardware acceleration and will force all rendering to be done in software." then honestly, the answer should be "No."

The emu10k does mixing of sound streams in hardware and ALSA allows it to. At one time these were among the best sounds cards that worked under Linux. I have an emu10k running under Jaunty with pulse audio disabled so ALSA can be used directly.   Ubuntu being a pulse audio only distribution, this is of course unsupported.  

My understanding is that pulse audio hobbles the system's ability to utilize sound cards by forcing all sound mixing and processing to occur in software, preventing the user from being allowed to take advantage of hardware features like the hardware sound mixing in emu10k regardless of what the card is actually capable of.

So, back to my question.  


[LIST]
[*] Does Ubuntu support my (or any) hardware accelerated sound card?
[*] Does Ubuntu Studio?
[*] Do I at least have a choice with Ubuntu to enable support at the expense of losing features I might decide I do not need or would never use?
[*] Is there perhaps a place I can send these question to get a decisive answer?
[/LIST]
 
Thanks,
Edd

---

