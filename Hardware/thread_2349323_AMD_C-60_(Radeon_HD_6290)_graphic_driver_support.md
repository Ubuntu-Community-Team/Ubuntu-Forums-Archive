---
title: "AMD C-60 (Radeon HD 6290) graphic driver support ?"
date: 2017-01-13
forum: Hardware
---

### Post by didli2 on 2017-01-13
[B]Hi everyone ! 
[/B]It's been quite some time since I've used a netbook I've own, an *Acer Aspire one 722*. So when upgrading it a few days ago to xubuntu xenial, I'm now getting a little confused about graphic driver support on this thing, since there are now some changes around AMD drivers. For now, my only real issue is with the screen resolution being too low (1024x768 now vs previously 1366 x 768). 
Could you please point me on the right direction ? How would you configure this netbook in your opinion ? 
Thanks in advance !

---

### Post by Yellow Pasque on 2017-01-13
> How would you configure this netbook in your opinion?
The open source radeon driver should "just work" out of the box without additional hoops to jump through. Proprietary fglrx/Catalyst or AMDGPU-Pro drivers are not even an option for your GPU on Xenial.

> screen resolution being too low (1024x768 now vs previously 1366 x 768). 
Can you give us the /var/log/Xorg.0.log file? Use code tags or pastebin. My hunch is that you were using the proprietary fglrx/Catalyst driver when you upgraded and still have pieces of it interfering. Either that, or you're still booting in to the old kernel from your previous distro.

---

### Post by didli2 on 2017-01-13
Thank you Temüjin ! I've update myself ^^ to understand what happened between the ubuntu world and AMD, so for now the netbook will be just fine using the open source radeon, as you recommended it. And yes, I was previously using fglrx. I can't find anything installed related to fglrx, but I'm gonna keep looking anyway.
Everything's fine now using oilaf PPA.

---

### Post by pele2048 on 2017-01-19
didli2:

How are you finding the performance of the laptop before and after the Xenial upgrade?

I have a Compaq CQ58, which has the same APU/CPU/GPU combo; the AMD C60 Dual Core with Radeon 6290. (8GB of RAM and a Sandisk SSD installed.) I have a fresh install of Lubuntu 16.04 LTS 64BIt and it's annoyingly slow.
Like, Windows 8 which originally came on this laptop was faster.
Lubuntu X86/32 Bit 16.04 LTS on a Celeron single core 900 MHz with 2GB of RAM is slightly faster.

I was considering wiping it out and installing 14.04 so that I can have the proprietary ATI drivers, thinking that might improve performance.

---

