---
title: "New Ubuntu PC Advice Needed"
date: 2009-09-03
forum: Hardware
---

### Post by GreenPanda on 2009-09-03
Hey everyone,

    I'm fairly new to the Linux community and am planning to put together a desktop, and I am not entirely sure if everything would be compatible with Ubuntu. I would also extremely appreciate some comments or advice on my choice of (or lack of) components. 

   I'm not too much of a gamer. I just have an EVE account going, and a few fleeting games. I do intend to go into some 3D-modeling/rendering, as well as some video work. 

Here is the current basic plan, it's not too detailed but I just wanted to get some input:

CPU: Intel Core i7 920  or Intel Core i7 860 (value for money is the decision maker between these two)

HD: Western Digital 1.5TB 

RAM: 4-8 gigs of something, I've always gone with Kingston. I'm sure there's a better brand, if someone knows anything I would really love the help. Oh and, DDR3 or DDR2?

GPU: GTX 260 (not very knowledgeable with GPU's, but wanted a good single one)

MOBO: I was actually hoping someone here could help me out with this. I have absolutely no idea about what mobo would be good. Sure I could go out and just buy any mobo that my components would be compatible with, but I would really appreciate any advice from anyone.

PSU: I was assuming this would need around 700w psu. I do wan't to use less power so if anyone knows any better I would very much like the help.

Thats about it for the hardware, the rest is pretty simple.

As for the OS, I am planning to install Ubuntu x86 64-bit on it to make use of the 4-8gigs of ram. Although I have read about alot of problems with the 64-bit architecture, especially with Adobe Flash. But this has happened before with the move from 16-32 and such. 

My question is, will I have any problems installing any of this hardware and having them compatible with Ubuntu, such as attaining drivers and such? Is that videocard going to cause me problems? Should I not bother with a video card like that as many people tell me it's a bit of a waste without directx10?

Hopefully there are a few out there with monster linux systems that could help me out with my quetsions.

I apologize for the length of my post, and humbly thank anyone who helps.

---

### Post by stefangr1 on 2009-09-03
The Core i7-860 seems to be slightly faster than the core i7-920 according to most (premature) benchmarks. I think, because of the TURBO feature which clocks the 860 to 3.46Ghz, it is likely to be significantly faster with the regular processor intensive tasks (where single core performance is still important). On tasks where all cores are used, the difference is going to be minimal. The i7-860 is also more energy efficient, with a TDP of 95W vs. 130W for the i7-920.

You need DDR3 RAM for the Core i7, I think 1333Mhz gives you the best value (be sure NOT to buy a triple-channel package for the i7-860).

The GTX-260 is a very fast GPU. You can program it with the CUDA extention for C, which could result in programs that run more than 10-times faster than when on your CPU. For regular gaming, however, it's likely to be an overkill. But still, nice, so it really depends on what you want.

For the PSU you have to check the power that is drawn from the 12V line by the GPU. Make sure you buy a quality PSU that has sufficient power on that line. Otherwise, the 700W overall isn't that neccesary unless you plan to put multiple GPU's in it in the future.

The 64-bits Ubuntu is the obvious choice I would say, the Flash problems are solved now for as far as I can tell. I have not yet experienced any 64-bits problems at all, after switching 6 months ago.

I think most 1.5 and 2TB disks work with 5400rpm, and thus have a slightly lower performance, I'd advice you to buy a 7200rpm disk. 2x Samsung Spinpoint F2 is a good choice. One of the advantages of having two separate disks is that your system won't slowdown when you're video editing etc. (if you do that on the second disk).

---

### Post by GoldenSun on 2009-09-03
I would wait on buying a computer.  The i5 comes out soon, same with the nvidia 300 series cards.  If you still want this build, then the prices will be lower.  If I'm not mistaken,the i5's come out within the month?  

Also I read that the i5 oc's like crazy.

---

### Post by stefangr1 on 2009-09-03
> **GoldenSun said:**
> I would wait on buying a computer.  The i5 comes out soon, same with the nvidia 300 series cards.  If you still want this build, then the prices will be lower.  If I'm not mistaken,the i5's come out within the month?  

Also I read that the i5 oc's like crazy.

The i5-750 (I wouldn't buy that one: it has no hyperthreading, lacks certain virtualization features, is slower, and you save only some 50 euro's on the price of a complete system), i7-860 and i7-870 are available from next monday, so you have to wait untill then before you can buy one :D .

---

### Post by GreenPanda on 2009-09-04
> **stefangr1 said:**
> 
You need DDR3 RAM for the Core i7, I think 1333Mhz gives you the best value (be sure NOT to buy a triple-channel package for the i7-860).

The GTX-260 is a very fast GPU. You can program it with the CUDA extention for C, which could result in programs that run more than 10-times faster than when on your CPU. For regular gaming, however, it's likely to be an overkill. But still, nice, so it really depends on what you want.


Is the DDR3 RAM required for the Corei7? Or can I go with DDR2?

Also, would you suggest an ATI card over the GTX-260? Which one would that be?

---

### Post by stefangr1 on 2009-09-04
> **GreenPanda said:**
> Is the DDR3 RAM required for the Corei7? Or can I go with DDR2?

Yes, the core i7's work only with DDR3-RAM. It's still about 1/3rd more expensive than DDR2-RAM.

> **GreenPanda said:**
> Also, would you suggest an ATI card over the GTX-260? Which one would that be?

No, NVIDIA is a good choice. The point I wanted to make is that you probably don't need a GTX-260 card, for example a 9600GT would also serve you perfectly well. But then again: the fact that you don't need it doesn't mean that you shouldn't buy it, the GTX-260 is one of the fastest cards currently available and definitively a nice piece of technology to have.

---

