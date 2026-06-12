---
title: "No HDMI output under 18.04 with HD 620 iGPU"
date: 2018-12-10
forum: Hardware
---

### Post by allcoms on 2018-12-10
I'm running 18.04 on a HP zbook g4 which uses a 7th gen core i7. It has both a Quadro M620 discrete GPU as well as a Intel HD 620 iGPU. I'm trying to drive an external 1080 monitor and HDMI output works for the Quadro but I've not been able to get it to work when I'm using the HD 620. I can use my external display with the Intel GPU via the SVGA port.

I have tried using the oibaf PPA drivers but they haven't made any difference, xrandr only ever reports my HDMI connection(s) are disconnected when I'm using the Intel driver.

I want to use the Intel GPU to experiment with GVT-G ie GPU virtualisation and I'd prefer to use HDMI over VGA. Currently, I have the GPU set to 'auto' in the BIOS so I'm manually disabling nouveau. I plan to try using the NV GPU for CUDA or passing it through to a VM.

Thanks

---

