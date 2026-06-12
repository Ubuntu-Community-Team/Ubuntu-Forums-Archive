---
title: "I'm never buying another ATI product"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by cinematography on 2007-10-30
I'm so sick of this crap. For the last 2+ weeks I've been trying to enable 3D acceleration on my ATI Xpress 1100 card. I've looked through all the manuals and threads, and tried many solutions, and now I'm getting this stupid "Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor." error. I'm not a programmer. I don't know what the hell this means, and I don't want to beg people to tell me what this means.

I shouldn't have to deal with this kind of grief with hardware I spent money on. I notice others here are having similar problems with ATI products, and there are long threads with long explanations and fixes on how to get ATI cards to work. None of this should be necessary. If it can just work in Windows, it should be able to just work in Linux.

I'm never buying another ATI product again. The crap I've gone through with this card and Linux has pissed me off entirely too much. My next graphics card will be from Nvidia.

---

### Post by scrooge_74 on 2007-10-30
It is sad indeed, that ATI is not as forthcomming as other manufacturers with their drivers.

---

### Post by cinematography on 2007-10-30
> **scrooge_74 said:**
> It is sad indeed, that ATI is not as forthcomming as other manufacturers with their drivers.
Very sad indeed.

---

### Post by pieisgood4589 on 2007-10-30
> **cinematography said:**
> Very sad indeed.



Well then why in the fuc#ing hel! would you switch to NVIDIA? They are even worse than fuc#ing ATI. ATI is meant to be compatible with Windows, and I have a CRAPPY ATI Rage Mobility Laptop graphics gard, that is VERY old and has only 64 mb of Video Memory, but Compiz Fusion works like a dream. (3D desktop even works!) I have had numerous troubles with my NVIDIA card, and also, they aren't as good as ATI. I tried doing the 3D effects with NVIDIA, but it is VERY CHOPPY. That NVIDIA card had 256 mb of Video Memory. DON'T SWITCH!!!! :-({|= *plays sad serenade* RIP NVIDIA

---

### Post by Anonii on 2007-10-30
> **cinematography said:**
> I'm so sick of this crap. For the last 2+ weeks I've been trying to enable 3D acceleration on my ATI Xpress 1100 card. I've looked through all the manuals and threads, and tried many solutions, and now I'm getting this stupid "Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor." error. I'm not a programmer. I don't know what the hell this means, and I don't want to beg people to tell me what this means.

I shouldn't have to deal with this kind of grief with hardware I spent money on. I notice others here are having similar problems with ATI products, and there are long threads with long explanations and fixes on how to get ATI cards to work. None of this should be necessary. If it can just work in Windows, it should be able to just work in Linux.

I'm never buying another ATI product again. The crap I've gone through with this card and Linux has pissed me off entirely too much. My next graphics card will be from Nvidia.


Many parts of your post are wrong but your main point is right. 
Yes, I agree that ATI's Linux support sucks, and I'm always recommending nVidia to my friends instead of ATI but still:

> I'm not a programmer. I don't know what the hell this means,

AFAIK, your model is supported and you probably did something wrong. That's why you are getting that error. Unfortunately, I can't help you because I have an ATI 9600XT (Using the fglrx closed-source driver), but I'm sure that it can be done if you read the "documentation" a bit more carefully.

> , and I don't want to beg people to tell me what this means.

First of all, your case is probably already mentioned somewhere in these chaotic forums.
Secondly, you don't "beg" people. You ask for support. That's the reason these forums exist (well not really, but what the hell!).
Also, by "begging" not only you solve your problem, but you also solve the problem of others when they use the search function to find answers on how to setup their "ATI Xpress 1100 card".

> 
I shouldn't have to deal with this kind of grief with hardware I spent money on.
**and**
None of this should be necessary. If it can just work in Windows, it should be able to just work in Linux.


I can bet my *** that ATI never promised you Linux functionality. Actually, you won't be able to find the word Linux or *nix in the whole manual. They didnt' trick you or anything, they just don't provide support for Linux (Aw well, they "opened" their drivers for the latest r500 and r600 models recently, so the ATI driver developing is going better.).

Also, the fact that the driver works on Windows doesn't mean that it will work on Linux. Or well, not just that easily. The driver needs to be ported to Linux and companies (ATI too) have been doing that for some time now. It's just that ATI is not really... trying.

---

### Post by scrooge_74 on 2007-10-30
> **pieisgood4589 said:**
> Well then why in the fuc#ing hel! would you switch to NVIDIA? They are even worse than fuc#ing ATI. ATI is meant to be compatible with Windows, and I have a CRAPPY ATI Rage Mobility Laptop graphics gard, that is VERY old and has only 64 mb of Video Memory, but Compiz Fusion works like a dream. (3D desktop even works!) I have had numerous troubles with my NVIDIA card, and also, they aren't as good as ATI. I tried doing the 3D effects with NVIDIA, but it is VERY CHOPPY. That NVIDIA card had 256 mb of Video Memory. DON'T SWITCH!!!! :-({|= *plays sad serenade* RIP NVIDIA

Going around the language filter dont you? :)

In the end Nvidia has better support than ATI, that is the sad true, if you get better results with older cards is most likely because people have been working on those drivers a lot longer.

---

### Post by obscur156 on 2007-10-30
Hi,have you tried ENVY to install your ATI driver?
IF not,there is the link.
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Choose automatic install.

IF you have tvout,i will help you make it work,just come back and i will help or just use this thread.
[http://ubuntuforums.org/showthread.php?t=583836]("http://ubuntuforums.org/showthread.php?t=583836")

I hope this will help,good luck budy.
Best regards.

---

### Post by julian67 on 2007-10-30
ATI is now part of AMD. In September they announced their intention to produce open source drivers for ATI cards, so switching to nVidia might not be the smart move long term.

last week ATI released new proprietary drivers which support AIGLX, they might be worth looking at.

I changed my ATI Radeon 9600 Pro a few months ago for a very cheap GeForce 6200....might be tempted to swap back to my old card now.

---

### Post by cinematography on 2007-10-30
> **pieisgood4589 said:**
> Well then why in the fuc#ing hel! would you switch to NVIDIA? They are even worse than fuc#ing ATI.
I have a Nvidia card on my other computer and it works beautifully with Ubuntu 7.04 and 7.10.

> **Anonii said:**
> AFAIK, your model is supported and you probably did something wrong. That's why you are getting that error.
I probably did do something wrong while going down the LONG list of instructions I had to go through. My point is that I didn't have to do this in Windows. ATI barely tired to make things easy for Linux users. That aggravates me.

> Secondly, you don't "beg" people. You ask for support. That's the reason these forums exist (well not really, but what the hell!).
Trying to word the perfect post in hopes of getting a quality reply on a forum has become very stressful. And I'm lucky if I get a reply at all. It has been a long hard road switching over from Windows to Linux, and my journey is almost complete. The only thing left on my list is a new Nvidia video card and I'll be set. :)

> I can bet my *** that ATI never promised you Linux functionality.
They should have. Windows isn't the only operating system people use on their computers.

> **obscur156 said:**
> Hi,have you tried ENVY to install your ATI driver?
IF not,there is the link.
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Choose automatic install.
To be honest with you, I'd rather just throw my ATI card out the window than try another solution. But after I calm down a bit I'll probably give this program a try. I've never seen it before. Thank you for the link.

> **julian67 said:**
> last week ATI released new proprietary drivers which support AIGLX, they might be worth looking at.
Thank you for the suggestion.

---

### Post by criskat777 on 2007-11-04
You relay should give Envy a try it worked for me on a ati 9600 pro. sure i still need to get visual effects to work but if it work out of the box then i would not have any tinkering to do on the OS :lolflag:

---

### Post by steveneddy on 2007-11-04
> **cinematography said:**
> 
**I'm never buying another ATI product again. **The crap I've gone through with this card and Linux has pissed me off entirely too much. My next graphics card will be from Nvidia.

I learned this lesson early on and look on in empathy as others wrestle with their ATI cards. One must eventually give in to the fact that nVidia just works better.

Good luck.

:popcorn:

---

### Post by Tosa on 2007-11-05
Somehow I've always preferred Ati to nVidia. I guess it was the same thing as preferring AMD to Intel, Linux to Windows...

But the nightmare to make Ati work, and a gamble weather it would work upon next boot finally made me get a nVidia.

(Un)fortunately, everything worked like charm. I still prefer Ati, but the bottom line is that I want my computer working for me, not the opposite...

---

