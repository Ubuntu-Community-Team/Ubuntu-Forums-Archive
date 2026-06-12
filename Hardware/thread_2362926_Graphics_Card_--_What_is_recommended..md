---
title: "Graphics Card -- What is recommended."
date: 2017-06-03
forum: Hardware
---

### Post by wrightpt on 2017-06-03
Hi,

I love Ubuntu and have recently taken on a role where I have to be extremely intimate with my screen. I mean look at it for hours on end and comb through text and flip through windows. Oh the joy!. I actually love it.

But I want to know in order to know i am getting the optimal viewing experience. What is the best graphics card to get?

I tried Invidia, installing the propriety drivers but that was not pleasant at all. 

I currently have an AMD RX 570 and do not install the graphics from AMD's site. I use the one that comes with Ubuntu. Is this the best route to go? Who maintains the AMD graphics driver for Ubuntu?  

I guess i just want the low down on how it all works. The drivers and what is the best route to take?

Thank you so much.

Patrick

---

### Post by lash5402 on 2017-06-03
There is a public driver maintained by the public and an AMD official driver maintained by AMD themselves. Don't use AMD's driver as they are still working out some issues with it from what I understand. You can try it though, it might be a lot better since the last time I saw news about it as they have gotten pretty good at updating their drivers pretty regularly. Either way you can always switch to the public driver if it doesn't work out and you should be just fine.

---

### Post by wrightpt on 2017-06-04
Thank you so much. I have had bad luck with propriety drivers from both AMD and Invidia on Ubuntu. I cant seem to get away from the system though. it allows me to explore computing in a way that allows me to be most comfortable with the systems i interact with. Currently I have my graphic card installed and have not installed any drivers and its the best viewing experience to date.  Do you know who maintains the public AMD driver for Ubuntu? I would like to think them and make sure they have a source of income to continue there work if possible. Also, if possible learn what they are doing that allows them to update the drivers in a way that AMD is not. 

It would be awesome to speak to someone in that area.

Thanks again.

Patrick

---

### Post by QIII on 2017-06-04
With that GPU on any release from 16.04 onward, the default open source driver installed will be AMDGPU.  That is maintained by AMD.  The current proprietary driver is AMDGPU-PRO, which is the AMDGPU driver with a proprietary overlay for further features.

In short:  AMD's proprietary driver is based on their open source driver!

The open source Radeon driver (installed by default on systems with older AMD graphics) is still maintained by the open source community.

---

### Post by wrightpt on 2017-06-04
Great input. I installed the ppa from padoka and it is such a better experience for me. Better than when the experience I had when using the driver that came with the system or using the driver that i get when downloading from AMD's website and installing.  Less eye strain and overall a better visual experience. I was wondering what he did in this ppa and how can i do the same when Vega comes out to have an even better experience?

Here is an overview of the two repositories: 
[https://www.epicgames.com/unrealtournament/forums/unreal-tournament-discussion/ut-development-bug-reports-qa/linux-troubleshooting/14891-how-to-update-open-source-graphic-driver-in-ubuntu](https://www.epicgames.com/unrealtournament/forums/unreal-tournament-discussion/ut-development-bug-reports-qa/linux-troubleshooting/14891-how-to-update-open-source-graphic-driver-in-ubuntu)

The padoka one that I installed is here:

[https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa)

I want the best viewing experience possible and currently do not have it but feel that i am definetely in route to it. 

Why would amd not do what padoka is doing. Anyway, as I find out more i will post.

---

