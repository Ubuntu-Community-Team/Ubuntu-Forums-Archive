---
title: "keep nvidia card or switch to radeon/amd eventually?"
date: 2018-01-22
forum: Hardware
---

### Post by ubunt72 on 2018-01-22
I'm looking at the nvidia and amd/radeon drivers in Linux and I haven't kept track or been following it lately.

Previously, nvidia (proprietary) drivers were best for having things 'work' but the caveat was that you had binary blobs and it was a nuisance to maintain - although distros like Ubuntu were improving at managing it.   At one point, you had to manually configure it or at least, it was better in a way since you would 'see' what was going on - and could configure it for whatever kernel and packages you had installed.

The PPA packages made it more convenient still and was yet another option.

But, now I am reading about Wayland and it is on its way to replacing (supplementing?) xorg and X11 (?) and supposedly, this is to be a simpler system (eventually).

I read that having newer Intel (graphics chip on the processor) supports Wayland and newer AMD cards support Wayland (is that true)?   So, would an AMD Radeon RX 460 - 480 or RX 550 and up be good for using Wayland in Ubuntu 17.10+?   

My current gpu is an Nvidia GTX 750 - so it is still okay but getting long in the tooth?   I don't think it's good for 4K video or at least I think I was told that.   Also, I'm not sure how long it'll be when I have problems with driver support?   But, most of all, I don't know if I should want to use Wayland.   Will Nvidia eventually support Wayland?   What would I gain by waiting?  

I don't play games, currently.  Maybe, I might in the future but it's not the priority.   The only concern I have with AMD Radeon cards isn't the driver (support) in Linux because it sounds like it's really improving.   It just seems that power consumption and temps are a bit high compared to equivalent/similar Nvidia cards.   I use my computer for streaming and htpc use so it's kinda beneficial to have a low power/low temp. card?   I thought maybe the RX 550 or 560 would only be a bit higher in power and temps - but would offer more performance should I want/need it?   I don't think I need anything more powerful but then is it worth it spending that much (no idea how much these cards go for - the mining/bitcoin rage has resulted in overinflated prices on these radeon cards?) to have a 'future' card and something compatible with Wayland?

Thoughts?   Should I save/plan for a Radeon card or should I wait and see what happens?

---

### Post by oldfred on 2018-01-22
Some comparisions.
 Radeon vs. NVIDIA With Windows 10 & Ubuntu Linux Dec 2017
[https://www.phoronix.com/scan.php?page=article&item=nv-radeon-win10ubuntu&num=1](https://www.phoronix.com/scan.php?page=article&item=nv-radeon-win10ubuntu&num=1) 
      
 Intel vs. Radeon vs. NVIDIA OpenGL/Vulkan Linux Driver Performance  Games June 2017
[URL="http://www.phoronix.com/scan.php?page=article&item=intel-radv-nvidia-13&num=1"]http://www.phoronix.com/scan.php?page=article&item=intel-radv-nvidia-13&num=1
[/URL]
 Mesa 17.1-dev vs. AMDGPU-PRO 16.60 vs. NVIDIA 378 Linux Gaming Tests
[http://www.phoronix.com/scan.php?page=article&item=mesa171-pro60-nvidia&num=1](http://www.phoronix.com/scan.php?page=article&item=mesa171-pro60-nvidia&num=1)
AMDGPU/RadeonSI Linux 4.10 + Mesa 17.1-dev vs. NVIDIA 378.09 Performance
[http://www.phoronix.com/scan.php?page=article&item=nvidia-378-amdgpu&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-378-amdgpu&num=1) 

      
 Linux 4.15 is what's tentatively slated as the default kernel for Ubuntu 18.04 LTS, among other distribution releases in H1'2018. 
Linux 4.15 Is A Huge Update For Both AMD CPU & Radeon GPU Owners
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.15-AMD-Mega)

I do not game and find the default Intel video with newer processors more than what I need.

---

