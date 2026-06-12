---
title: "How can I tell if both my gfx cards are on?"
date: 2010-12-10
forum: Hardware
---

### Post by Jengu on 2010-12-10
I have a Thinkpad 410s which has nvidia optimus, so when run under a supporting OS it will use the onboard intel graphics during low load and the nvidia card during high load. Is there a way to tell if both cards are being powered? I know Ubuntu doesn't support switchable graphics yet and will only use one for rendering, but my concern is whether the second card is consuming battery. Even if it's idle I think it consumes power unless it's powered off.

I've seen posts by other users who have wanted to force their nvidia/ati card to be used all the time, but I'd actually prefer to stick to the intel card for the better battery life because if I want to play a 3D game I reboot to Windows anyway.

I can tell from glxinfo that the Intel card is being used:

$ glxinfo | grep render

direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT

But if I run lsmod I see some nouveau listings:

$ lsmod | grep nouveau
nouveau               568848  0 
ttm                    68212  1 nouveau
drm_kms_helper         32836  2 i915,nouveau
drm                   206161  5 i915,nouveau,ttm,drm_kms_helper
i2c_algo_bit            6208  2 i915,nouveau

Does nouveau being here mean the card is being powered? If so, will blacklisting nouveau be sufficient to make sure the nvidia card is powered down?

---

### Post by tonus on 2011-05-23
With the nouveau,i915 combination on natty, I was having race condition like issues with suspend (would not suspend but hang every other 4 tries or so) and battery shortage, so I simply turned off the nvidia part in the bios on my Thinkpad T410 by setting it to 'Integrated' under Display. When you reboot to windows a lot this might not be ideal, but at least you're sure it's turned off completely.

---

