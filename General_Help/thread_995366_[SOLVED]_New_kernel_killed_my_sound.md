---
title: "[SOLVED] New kernel killed my sound"
date: 2008-11-27
forum: General Help
---

### Post by x1a4 on 2008-11-27
Hi,

I just updated Hardy which included a kernel update and restricted modules.  The old kernel is 2.6.24-21-generic and the new is 2.6.24-22-generic.  

When I booted to the new kernel Xubuntu didn't recognize my sound card.  I tried adding the modules manually using modprobe and received a fatal error stating that one of the modules was not found.  The missing module is snd-emu10k1-synth.  The other modules are: snd-emu10k1x snd-emu10k1 snd-ca0106.  The sound card is a SoundBlaster Live 24-bit. When I booted to the previous kernel everything is working well.  

Any ideas?

Thank you.

EDIT: I just installed the 2.6.24-22-386 kernel and everything seems to be working well, so I'll stick with that.  

BTW what happened to the 686-optimized kernels?

---

