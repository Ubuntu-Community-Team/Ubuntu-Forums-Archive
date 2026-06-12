---
title: "Dedicated graphics card vs onboard graphics"
date: 2012-09-09
forum: Hardware
---

### Post by oslub on 2012-09-09
I am buying a new desktop PC in early 2013. 

Even though I know there are some PC models specially designed to ship with  Ubuntu, which is the OS I use the most these days, still everyone else uses Windows and some software with unsupported versions for  Linux and not having a Windows license becomes a bit problematic.

This means that I will have to search for good options in the middle of Windows' PC market. The [certified hardware from Ubuntu website]("http://www.ubuntu.com/certification/") should help me choose a model with good compatibility with Ubuntu.

 This machine is not meant for gaming, and if I occasionally do it, I  can survive with minimum graphics. However I may need some heavy  multimedia edition or multitasking at times, so basically  my greatest  priority is a good processor and at least 4GB of RAM with possibility of expansion.

However, I am still unsure about the graphics card. In first place, accordingly with what I usually read around here and askubuntu, it is one of the main sources of trouble for Ubuntu users, together with  internal wireless adapters and printers. In second place, I have contradictory informations about the advantages of dedicated graphics over onboard graphics.

In fact, I read about Intel claiming that onboard graphics are satisfactory even for multimedia at high quality, but the mainstream opinion is that for the best performance, one must have a dedicated graphics card and some even claim that an average and cheap graphics card is superior to any onboard. On top of that, I've also read that when it comes to Ubuntu, Intel onboard graphics are more reliable and suitable, when compared with NVIDIA for example, so basically for Ubuntu usage, NVIDIA would be a waste of money.

I could not arrive to any trustworthy conclusion. I am confused about this and thus I am looking for some clarification in here. So, to run Ubuntu at its full potential, with some occasional multimedia and heavy multitasking involved, is an onboard graphics enough or even preferable over dedicated graphics cards, or is it the other way around?

Notice that this question has increased relevance for me because I was informed that Unity 2D [will be dropped on next release, 12.10]("http://www.omgubuntu.co.uk/2012/08/unity-2d-removed-from-ubuntu-12-10"), which I use regularly on my laptop to prevent overheating, so I want to have the best hardware to deal with the new unified Unity (my favourite interface of all OS I must say).

---

### Post by jerome1232 on 2012-09-09
This just my opinion:

Dedicated graphics all the way. Generally on-board chips borrow from system ram, which is incredibly slow compared to the vram used in dedicated cards. As long as your not going bleeding edge or dinosaur old, nvidia cards work very well in my experience. I have a Nvidia GTS 450 which is a 2 generations (maybe more now) old mid-range card. I got it for 19 bucks online, I can play any modern game I've thrown at it.

The drivers for my card where automatically loaded during the installation (you have to select the option that allows the installer to install proprietary drivers) and it has presented me with zero hassles.

---

### Post by oslub on 2012-09-13
> **jerome1232 said:**
> This just my opinion:

Dedicated graphics all the way. Generally on-board chips borrow from system ram, which is incredibly slow compared to the vram used in dedicated cards. As long as your not going bleeding edge or dinosaur old, nvidia cards work very well in my experience. I have a Nvidia GTS 450 which is a 2 generations (maybe more now) old mid-range card. I got it for 19 bucks online, I can play any modern game I've thrown at it.

The drivers for my card where automatically loaded during the installation (you have to select the option that allows the installer to install proprietary drivers) and it has presented me with zero hassles.

Thank you very much for your reply jerome.

I confess I was a little biased by NVIDIA bad reputation when it comes to Linux support, but I will consider your opinion as valid because you actually use Ubuntu with a NVIDIA card.

I assumed that performance is higher when using a dedicated graphics card, however while this was a fact for me on Windows, I was doubting if this would apply to Ubuntu as well, due to the mentioned bad reputation of NVIDIA.

Anyway, it is good to know that there is proper support to Ubuntu by now and I really only need an average graphics card, not too old, not too bleeding edge, so it's not really that much expensive (at least for a desktop PC) it fits the budget and now I know it will be compatible with Ubuntu, so I am glad I can have this considerable boost on system performance and rely on it for some occasional heavy multitasking while having the best experience with my favorite OS - Ubuntu :)

---

### Post by mastablasta on 2012-09-14
nvidia on **laptops** now mostly comes as hybrid (i.e. intel card that is inside core i chips and nvidia card). it's ment to work like so - when you use less intensive stuff intel card is on. this saves power and battery lasts longer. when you game nvidia turns itself on. now here is the catch. Nvidia Optimus (as htis combo is called) is not supported in linux.
 
there is a project called bumblebee that helps you disable nvidia when you dont' need it.
 
another thing is that AMD Hybrid graphics works the same way, but AMD supports it in linux. well at least on some models. have a look here: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
for some tested and supported models.
 
i believe some models with nvidia also work well using bumblebee. while others simply don't.

---

### Post by shreepads on 2012-09-14
Well I'm sure this won't be a popular opinion but IMHO dedicated graphics are a leading cause of Linux hardware incompatibility and source of hardware trouble for laptops...

My advice would be to go with the integrated graphics, but as another poster has mentioned, make sure you get enough (and more!) FAST RAM as the integrated graphics will share it...

Intel HD 3000 will be 'good enough' IMHO for what you want to do. 

My own experience: integrated Intel graphics are failsafe, while I do get glitches off and on with the NVidia card I have (details below).

---

### Post by jerome1232 on 2012-09-14
I missed that bit about it being a laptop, take note of that optimus stuff, above. My laptop is a little 'ole netbook with an intel chip.

---

