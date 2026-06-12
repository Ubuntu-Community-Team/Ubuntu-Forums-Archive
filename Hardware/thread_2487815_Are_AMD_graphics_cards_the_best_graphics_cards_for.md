---
title: "Are AMD graphics cards the best graphics cards for Linux?"
date: 2023-06-15
forum: Hardware
---

### Post by SpaceManJack on 2023-06-15
So I'm having issues with NVidia drivers so I'm just thinking about installing an AMD graphics card in my PC, I'm thinking maybe that would fix my problems right there? To understand the problems I'm having with my NVidia graphics card you can check this out [https://ubuntuforums.org/showthread.php?t=2487814](https://ubuntuforums.org/showthread.php?t=2487814)

So yeah my PC was built in 2015, it's got a GTX 750 Ti, an Intel quad core CPU, and I think 16 gigs of ram. I've found this cheap Radeon RX 580 graphics card on amazon that I'm thinking about getting [https://www.amazon.com/AISURIX-Graphic-Express-Desktop-Computer/dp/B0BLCRNCX9/ref=sr_1_3?crid=F18G9OFFFS7&keywords=amd+graphics+card&qid=1686853509&refinements=p_36%3A1253506011&rnid=386442011&s=electronics&sprefix=%2Caps%2C178&sr=1-3&ufe=app_do%3Aamzn1.fos.f5122f16-c3e8-4386-bf32-63e904010ad0](https://www.amazon.com/AISURIX-Graphic-Express-Desktop-Computer/dp/B0BLCRNCX9/ref=sr_1_3?crid=F18G9OFFFS7&keywords=amd+graphics+card&qid=1686853509&refinements=p_36%3A1253506011&rnid=386442011&s=electronics&sprefix=%2Caps%2C178&sr=1-3&ufe=app_do%3Aamzn1.fos.f5122f16-c3e8-4386-bf32-63e904010ad0)
So this RX 580 would be totally fine to just drop-in to my PC, it wouldn't cause any compatibility problems? I'm a newb bear with me.

So yeah I'm assuming AMD GPUs are the best for Linux right? So the NVidia cards are closed-source but AMD isn't?

Thanks.

---

### Post by Autodave on 2023-06-16
Personally, I have never had an issue with nVidia cards.  I do understand that if you are using ones that are older, the proper driver may no longer be available.  But, having said that, my wife's machine is running a 12 year old nVidia with no issues at all.

This machine is running an RTX 3080 and my other machine an RTX 2070: neither has ever had a problem.

---

### Post by #&amp;thj^% on 2023-06-16
I'm guessing that that card is a Fake:
To check use, and paste back this:
```
sudo lspci -d 10de:*

```
Mine will report:
```
01:00.0 VGA compatible controller: NVIDIA Corporation TU117M [GeForce GTX 1650 Ti Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 10fa (rev a1)

```
I'll wager it's a bios modified GTS450, GF116, a current Nvidia card would help tons
But your question is very subjective, I prefer nVidia, others AMD/Radeon and others just good old Intel.

---

### Post by Yellow Pasque on 2023-06-17
> **scott130 said:**
> 
So this RX 580 would be totally fine to just drop-in to my PC, it wouldn't cause any compatibility problems? I'm a newb bear with me.


The card you linked to is a gamer's GPU. If you don't do heavy gaming, then it isn't the card for you. It may not fit your case (it's dual slot) and it requires an 8 pin power connector, and it is not as power-efficient as the GTX750. The Polaris-based GPU's like that work well on Linux, but I would shop around for a different card based on what you use your computer for.

EDIT: An RX550 might be a better and cheaper choice: [https://www.amazon.com/AISURIX-Graphics-Computer-DirectX-Express/dp/B0C3LFMFRW?ref_=ast_sto_dp&th=1](https://www.amazon.com/AISURIX-Graphics-Computer-DirectX-Express/dp/B0C3LFMFRW?ref_=ast_sto_dp&th=1)

---

### Post by SpaceManJack on 2023-06-19
> **Yellow Pasque said:**
> The card you linked to is a gamer's GPU. If you don't do heavy gaming, then it isn't the card for you. It may not fit your case (it's dual slot) and it requires an 8 pin power connector, and it is not as power-efficient as the GTX750. The Polaris-based GPU's like that work well on Linux, but I would shop around for a different card based on what you use your computer for.

EDIT: An RX550 might be a better and cheaper choice: [https://www.amazon.com/AISURIX-Graphics-Computer-DirectX-Express/dp/B0C3LFMFRW?ref_=ast_sto_dp&th=1](https://www.amazon.com/AISURIX-Graphics-Computer-DirectX-Express/dp/B0C3LFMFRW?ref_=ast_sto_dp&th=1)

[https://www.amazon.com/RX-550-Computer-Graphics-DisplayPort/dp/B08VHWFWSD/ref=sr_1_2?crid=293VHZN0YKB7W&keywords=amd+gpu&qid=1687213234&sprefix=amd+gpu%2Caps%2C201&sr=8-2](https://www.amazon.com/RX-550-Computer-Graphics-DisplayPort/dp/B08VHWFWSD/ref=sr_1_2?crid=293VHZN0YKB7W&keywords=amd+gpu&qid=1687213234&sprefix=amd+gpu%2Caps%2C201&sr=8-2)

This is the one I ended up getting. Yeah I realized my PSU doesn't even have enough power for the 580. I'm a total newb here so I'm just now learning about all of this stuff. But I got the 550 in the mail and I easily swapped it out with the NVidia 750 ti and guess what, it seems that all the problems I was having are now gone! So yeah it seems the bugs I was experiencing were all due to the stupid NVidia GPU. I had no idea that Linux had such problems with NVidia's closed source GPUs. I was having bugs with the 750 ti and now that there's an AMD RX 550 in my PC they're gone. So now I've got an AMD CPU and and AMD GPU in my PC and everything as of right now is working pretty good. 

I've learned my lesson here, no more NVidia for me. I'm sticking with AMD from now on, I had no idea the support from the Linux community was so strong with AMD compared to NVidia.

---

### Post by mIk3_08 on 2023-06-20
> **scott130 said:**
> So I'm having issues with NVidia drivers so I'm just thinking about installing an AMD graphics card in my PC, I'm thinking maybe that would fix my problems right there? 
Thanks.
In my case, all my Linux Ubuntu Desktop PC uses AMD graphics card and I haven't encounter any issues in all of these machines. I'm not advertising my graphics card but its true. I never experience any issues in my system machine display. So far so good. Regards and cheers.

---

