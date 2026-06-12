---
title: "[Solved] Compatibility with wide-screen display"
date: 2019-01-03
forum: Hardware
---

### Post by davide445 on 2019-01-03
When the new PC components will arrive will install on it Kubuntu 18.04 LTS.

Will pair it with a new wide-screen display, 21:9 aspect ratio, 2560x1080 resolution, HDMI interface. 
As GPU will use an old AMD HD 7950 Boost (Thaiti generation, so no AMDGPU drivers) or a Nvidia GTX 1070 (depends if I will be able to use the amd to control the display and Nvidia for compute, or I will be forced to use only one GPU, will be Nvidia). 

Before purchasing it want to know if someone experienced problems with this kind of display and Ubuntu 18.04 release.

---

### Post by mikasu on 2019-01-03
I don't know if the HD 7950 can output that resolution, but if it does, it should do ok. With AMD GPUs you are pretty far from problems with display as the drivers are the kernel itself and mesa (as you may know). With nVidia though, I personally don't have a problem with it on my laptop with a GeForce 840M. It works as expected since the optimus GPUs do not work in the optimus way unless you want to give up on Vulkan(which I'm not). Some people have certain issues with it but I think that most case uses it works. I think you should be fine trying that. Just have to plug the monitor to the HD 7950. Though, if you are still uncertain, the nVidia GPU might do well alone too.

May I know what's your CPU? Because that might open some possibilities. Also, is it for mining or you're going to use CUDA and OpenCL?

---

### Post by davide445 on 2019-01-03
Thanks @mikasu

Yes HD 7950 can manage that resolution on HDMI so at least this part will be not a problem. Mesa drivers are in fact my only option for AMD, glad to know they are preloaded on Ubuntu. 

CPU will be Ryzen 5 2600X, 
mobo Asus Prime B450-Plus ATX, 
RAM DDR4 32GB PC 3200 CL16 G.SKILL KIT (2X16GB) 32GVR RIPJAWS F4-3200C16D-32GVK

---

### Post by mikasu on 2019-01-03
That's a pretty strong build. If the HD 7950 can output this resolution, then you'll be alright. Do you know about oibaf's graphics drivers ppa?

---

### Post by davide445 on 2019-01-03
No idea what's this...
It's not for mining but data science, using cuda for computing.

---

### Post by mikasu on 2019-01-03
There is the classic graphics drivers ppa for nVidia drivers, it's still the best. But Oibaf made his own and this one has better up-to-date drivers for AMD/ATI GPUs and Intel iGPUs. You might want to look at Oibaf's graphics ppa. You'll most probably need the classic one too for your GTX 1070.

---

### Post by davide445 on 2019-01-03
You mean the nouveau drivers? Tested them and Nvidia 390 release, both working.
About Oibaf might be better than Mesa and Nouveau?
My concern is also if I will be able to use both Mesa drivers for AMD card + only cuda for Nvidia. Will use Nvidia card only for compute so will not need display drivers.

---

### Post by mikasu on 2019-01-03
Oibaf is about more up-to-date mesa, it's not another driver. Nouveau driver is terrible, it's replaced by mesa in general (I think). I'll check for the coexistence of AMD and nVidia GPUs on Ubuntu

---

### Post by mikasu on 2019-01-03
About the two in the same system, you might run into issues but there is a forum thread about that. Apparently, it's doable, I also think it's quite common practice for Linux gamers with exotic gaming ways, like Windows virtual machines for Windows games. The forum thread is below, hopefully that will help you if you run into issues. Were you buying both GPUs? By the way, you will need the display driver for the GTX but you wont use it, if that makes sense. You'll need the nVidia driver to have the CUDA driver but you wont use you GTX's display output. Still, if you're buying both GPUs, I think you would be better of buying only the GTX 1070. If the HD 7950 is a GPU you already own, then I think you can go ahead and buy your nVidia GPU and if it doesn't work, keep only the GTX. Buying a HD 7950 is close to a waste of money nowadays(not judging your choices. My reason of thinking is that it will be very hard to re-sell afterwards).

  [URL="https://askubuntu.com/questions/892532/nvidia-card-for-cuda-and-amd-card-for-display-on-ubuntu-16-04"]https://askubuntu.com/questions/892532/nvidia-card-for-cuda-and-amd-card-for-display-on-ubuntu-16-04
[/URL]

---

### Post by davide445 on 2019-01-03
I already own the HD 7950 from a previous PC, already purchased the GTX 1070 just since I need CUDA for computing.
Using both my thinking is I can offload to the older AMD GPU all the graphics part (is perfectly capable of managing it) and reserve all the resources of the Nvidia for the only heavy task is devoted to, computing. 
Thanks for the link to the new thread, I suppose I can proceed in purchasing the wide screen display and now concentrate in how create this double gpu setup.

---

### Post by mikasu on 2019-01-03
Good luck! Happy that I helped you! :)

---

