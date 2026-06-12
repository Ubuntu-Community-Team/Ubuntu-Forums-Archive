---
title: "Is it still: avoid ATI at all costs?"
date: 2011-06-08
forum: Hardware
---

### Post by MacUntu on 2011-06-08
I'm about to buy a new PC and the last part I'm missing is the graphics card. I have made good experiences with Intel and Nvidia, but haven't ever owned an ATI graphics card. All I can remember are people having nothing but trouble with their ATI cards and that the rule of thumb was to stay away from ATI if you are a Linux user.

Is this still true in 2011? Should ATI still be avoided if possible?

---

### Post by fioan89 on 2011-06-08
Well i think it's your choice ,so i won't give you any advice ,but i'm going to share with you some info and then you will decide what you will do.

On my notebook i have an Mobility Radeon HD 4570 , so not quite the latest ati card you could find.

For almost 2 years (Ubuntu 9.04,9.10,10.04) i had a lot of problems with video acceleration playback.Vaapi didn't work, and xvba from ati was no good.But starting 10.10 things changed,ati released their specification for xvba,vaapi for ati cards improved and now on my ubuntu 11.04 i can play 30 GB HD movie or BlueRay quite smooth.Of course you have to compile mplayer with vaapi support,and make a few tricks but you can find more info with google.The only problem is that vlc player with GPU hardware acceleration support crash every time i try to play a movie.But that i suppose is vlc fault(or at least i think so...)

On the composite part or should i say desktop effects ....no problems,especially with kde..it just run smooth,no artifacts ,no glitches.

If you are a developer and use OpenCL(not OpenGL) i must say i'm proud of ATI,they offer the latest specification of OpenCL,support for intel/amd cpus with amd gpu,wich i cannot say about NVIDIA.
So this is what i experienced with ati cards.You should think about it.ATI support is getting better by day ,and if you are thinking for some of the latest cards(abov HD 50..) than i think your on the good track.
Oh BTW all of the above are for proprietary driver,for the open-source driver i can't tell you much.

---

### Post by sanderd17 on 2011-06-08
I've had a laptop with an ATI card until January (sorry, I don't remember which one). With 9.04 and 9.10 it was rubbish. I had to use different kind of boot options to even get Ubuntu booted without hardware acceleration.

with the 10.04 release, everything worked though. I could use all compiz effects I wanted. And with 10.10 it worked too.

So ATI has become better, and if you see a good offer with an ATI card in it, I would buy it. But Intel and nVidea are still better supported.

---

### Post by mastablasta on 2011-06-08
i use opensorce ATI drivers. there were couple of issues on 10.10 when it came out but updates solved it all and now it's fast and smooth. I also tested live session on the other computer with a newer ATI card and everyhting runs well regarding graphics.
 
i think nvidia is also good choice.
 
i wouldn'T go intel (unles it's a notebook)

---

### Post by MacUntu on 2011-06-08
Thanks guys for your replies. So I deduce, that it's not as bad as it used to be, but Nvidia is still a safer bet. I mean, working Compiz is nice, but I don't need to buy a dedicated graphics card for *that*.

---

### Post by doas777 on 2011-06-08
> **MacUntu said:**
> Thanks guys for your replies. So I deduce, that it's not as bad as it used to be, but Nvidia is still a safer bet. I mean, working Compiz is nice, but I don't need to buy a dedicated graphics card for *that*.
yes, ati is much better than it used to be, but beware odd card models and all onboard ATI cards if possible. many of them are still not supported by the driver in the repository and require a manual installation of the latest from ati.com. between Karmic and Lucid most of my cards came into the fold as it were, but I've seen others talking about integrated cards that are still not supported.

---

### Post by acrazyplayer on 2011-06-08
Just thought I would add that some newer ATI GFX cards have a nice little feature called "tear free desktop" in which you will get no visual tearing with anything. 

however if you do not know what tearing is then dont even worry about it :D

---

