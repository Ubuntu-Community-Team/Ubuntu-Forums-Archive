---
title: "Expanding RAM under Ubuntu 10.04"
date: 2011-03-16
forum: Hardware
---

### Post by LynxUser on 2011-03-16
Hi all,

I currently have 1GB of RAM (2x512MB of DDR2@533MHz) on my PC running Ubuntu 10.04. I have defined a swap of 2GB during OS installation. My motherboard (Intel D915GEV) can support up to 4GBs of RAM (@533MHz). I am looking into buying 4GBs of RAM (2x2GB DDR2@800MHz).

I was wondering if this new RAM would be recognized by the system and will the Ubuntu use it straightaway? Furthermore, do I need to expand my swap (due to the expanded RAM) and how do I do that? 

I was told that the 800MHz RAM will work in the 533MHz slot without the problem, only at the 533MHz speed. This is fine for me if it's true?! My main concern is: should I need to expand swap, upgrade BIOS, or do something else once I install the new RAM. I would like to clarify this before I actually buy the RAM.

I should mention that I am not an experienced Linux user. 
Thanks in advance!

---

### Post by Fire_Chief on 2011-03-16
For the new RAM sticks, your board supports two types...PC2-3200 and PC2-4300. This should be your guide for what kind of RAM to get. It's easier to keep track this way than to say what clock speed the RAM runs at.

Secondly, Ubuntu 32-bit will in theory use up to 4 GB of RAM (in practice you'll likely see 3+ GB listed as usable (3.25, 3.5, etc.). This is often due to the onboard graphics card using some of the system RAM. You'll still have a definite improvement in the performance though.

With that additional RAM, you're much less likely to dip into swap space at all, let alone use up the 2 GB you have allocated. I would not worry about expanding the swap space unless you are looking to do some heavy app related work (video editing, virtualization, etc.).

Cheers!

---

### Post by LynxUser on 2011-03-16
Thanks very much for this info! Now I know what to look for.
It would seem to me a waste of RAM if Linux (as well as my WinXP on dual boot) could not recognize full 4GB? Maybe I should buy only 2GB instead? What do you think? I should mention that I have a nVidia graphics card that I use. Additionally, I haven't been using much of the swap as it is now (it normally registers very low swap usage). Do I need to update BIOS? Thanks again for the help!

---

### Post by Artemis3 on 2011-03-16
64 bit editions recognizes and allow individual programs to use more than 2g of ram just fine (nobody should be using 32 bit unless their cpu can't handle 64 bit).

Your swap must be slightly bigger than your ram if you want to hibernate.

---

### Post by LynxUser on 2011-03-17
Thanks guys for the clarification!
I am using 32bit version of the Ubuntu 10.04 (due to the fact that this has been recommended to me) as well as the 32bit version of the WinXP. I've been told to stick with 32bit editions of Linux distros (have switched from openSuse)?! Am I doing this wrong? Any thoughts would be appreciated.
Thanks again for the help.

---

### Post by ipsi on 2011-03-17
XP was, to the best of my knowledge, only really stable with 32bit. The 64 bit edition had some fairly serious issues with stability and drivers, I believe (sorry, just hearsay - no citations).

I'm using Ubuntu 10.04 64bit on my work laptop, and I've had very few issues, apart from with older software that doesn't work with a 64bit OS. Funnily enough, that's all been proprietary so far.

I've also installed 10.10 64bit on my home desktop which has 16GB of RAM. While it's a brand-new machine which I haven't used much yet, I can't imagine having any problems with it.

---

### Post by LynxUser on 2011-03-17
Thanks ipsi for the info. Thanks guys for the help.

---

