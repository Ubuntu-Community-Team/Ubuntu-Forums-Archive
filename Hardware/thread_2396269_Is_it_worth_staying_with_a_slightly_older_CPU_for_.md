---
title: "Is it worth staying with a slightly older CPU for 18.04 LTS?"
date: 2018-07-13
forum: Hardware
---

### Post by Ice-Tea on 2018-07-13
My days of distro hopping and upgrading the point release every 6 months is over as i only browse the web and watch media so unless Ubuntu moves to a rolling release i've decided just to stick with the latest LTS from now on.

I've just started looking at parts for a Coffee lake machine but as LTS uses an older Kernel and backports and patches can take ages (sometimes years) i wondered if it would be best to stay with slightly older hardware like Haswell or Skylake?

---

### Post by Ice-Tea on 2018-07-13
Maybe this thread would be better in either the Hardware or the General Help section........

Could a Mod move it please?

Thanks

---

### Post by oldfred on 2018-07-13
Moved to hardware, but since not specific may be better in discussion.

I have both a Haswell & Skylake systems. With the Skylake I built it in Feb 2016, but had to install 16.04 before released to have it work. And that worked well.

       Coffeelake 8700 & 8400
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1) 
            ASUS PRIME Z370-A Running Great On Linux, needs i915.alpha_support=1 or Linux 4.15 kernel
[https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1](https://www.phoronix.com/scan.php?page=article&item=asus-prime-z370a&num=1)
ASRock Z370M-ITX/ac: Mini-ITX Motherboard With Dual NICs, WiFi, Triple Display For ~$130 USD Oct 2017
[https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1](https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1) 
    
But Phoronix often uses ppa to install newest kernel & support software.
       [https://www.phoronix.com/scan.php?page=news_item&px=Intel-2018Q1-Gfx-Recipe](https://www.phoronix.com/scan.php?page=news_item&px=Intel-2018Q1-Gfx-Recipe)
The 2018Q1 Intel Graphics Stack Recipe for a recommended configuration is using the Linux 4.16 kernel, Mesa 18.0, xf86-video-intel 2.99.917, libdrm 2.4.91, libva 2.1.0, VA-API Intel Driver 2.1.0, Cairo 1.15.10, and X.Org Server 1.20 RC1.
[https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe](https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe)

---

### Post by Ice-Tea on 2018-07-14
Thanks [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")  , I think you're right that it would be best as a general discussion as it's not a specific problem.

Thank you all so for taking the time to post up all those links and information , i'll be using a Nvidia card so the intel graphics shouldn't be a problem.

---

### Post by kevin160 on 2018-07-14
There is lots of older hardware that still isn't well supported.  I think it's probably more important to look closely at all the components (chipsets) in a new system to see what driver support will be like.  

If you want good Linux support, sticking with Linux-friendly vendors (Intel for ethernet, Atheros for wifi, nvidia for graphics) helps a lot both with new-ish hardware and over the long term.

---

### Post by Ice-Tea on 2018-07-15
I've changed the topic as it was misleading with the term Hardware , I meant staying with an older CPU for the older Kernel of LTS ,  oldfred knew what i meant. :)

Sorry about that.

---

### Post by Yellow Pasque on 2018-07-15
The big takeaway from the Phoronix review is that the CPU worked fine in Ubuntu 17.10. I wouldn't worry about using a Coffeelake CPU in 18.04, especially if you're not using the iGPU.

> I think it's probably more important to look closely at all the components (chipsets) in a new system to see what driver support will be like.

+1 to that

---

### Post by Ice-Tea on 2018-07-18
Thanks all for the feedback. :)

I wish Ubuntu would move over to a rolling format rather than the current LTS and point release.

---

