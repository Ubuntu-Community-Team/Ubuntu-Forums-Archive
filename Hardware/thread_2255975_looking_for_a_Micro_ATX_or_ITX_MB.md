---
title: "looking for a Micro ATX or ITX MB"
date: 2014-12-08
forum: Hardware
---

### Post by tekno62 on 2014-12-08
I have been researching AMD based motherboard in the small format for a project and was looking at the Asus A55BM-E, Asus A88X-Pro, Asus A78M-A, Asus AM1I-A, MSI AM1I but I have read that there are some problems with these boards have some problems with the new distribution 

So if anyone knows of a small format system that works please let me know. 


tek

---

### Post by newbie-user on 2014-12-10
I haven't used any of those specific boards, but I've had issues with AMD graphics drivers in the past and have since switched to Intel boards, which give me no problems. What kind of project are you doing and would you consider going Intel?

---

### Post by tekno62 on 2014-12-10
I picked the AMD due to the CPU price as well as I read that AMD open sourced the driver info. I plan on using the system for a DIY laser engraver

I didnt plan on using the on board graphics device but would add a Nvidia card

---

### Post by kurt18947 on 2014-12-11
A sample of one but I installed this setup for SWMBO:

[http://www.microcenter.com/product/424749/FM2A88M-HD_Socket_FM2-FM2_mATX_AMD_Motherboard](http://www.microcenter.com/product/424749/FM2A88M-HD_Socket_FM2-FM2_mATX_AMD_Motherboard)

with this processor:

[http://www.microcenter.com/single_product_results.aspx?sku=617811](http://www.microcenter.com/single_product_results.aspx?sku=617811)

and this memory:

[http://www.microcenter.com/product/382072/Ballistix_Sport_4GB_DDR3-1600_%28PC3-12800%29_CL9_Desktop_Memory_Module](http://www.microcenter.com/product/382072/Ballistix_Sport_4GB_DDR3-1600_%28PC3-12800%29_CL9_Desktop_Memory_Module)

She doesn't need super high performance - economical and stable are more important - and this combo has worked reliably for her.  I left the video installed by default alone, did not try to install any AMD drivers even though there was one available in additional drivers.  I have read that the AMD APUs benefits from faster RAM and DDR3-1600 is a practical minimum.

---

### Post by Yellow Pasque on 2014-12-11
Phoronix reviewed some AM1 mobos and didn't seem to have any Linux-specific issues:
[http://www.phoronix.com/vr.php?view=20301](http://www.phoronix.com/vr.php?view=20301)
[http://www.phoronix.com/vr.php?view=20238](http://www.phoronix.com/vr.php?view=20238)
[http://www.phoronix.com/vr.php?view=20208](http://www.phoronix.com/vr.php?view=20208)
[http://www.phoronix.com/vr.php?view=19893](http://www.phoronix.com/vr.php?view=19893)

> **tekno62 said:**
> but I have read that there are some problems with these boards have some problems with the new distribution

Be more specific. I can't tell you how much BS has been posted on these forums (and the internet in general) that begins with "I read..." or "I heard..."

>  I read that AMD open sourced the driver info

If you plan on using an Nvidia GPU, how is an open-source AMD graphics driver relevant? As far as AMD vs. Intel, Intel Bay Trail has some advantages (power consumption, performance per Watt), but AMD's AM1 platform is very competitive on price. If I was building a system like this, I would lean towards AMD, but only if noise wasn't a consideration. Otherwise, I would probably opt for Bay Trail since it's easier to cool passively.

> I didnt plan on using the on board graphics device but would add a Nvidia card

What are your graphic needs for this system? Unless you need to do gaming or something else that needs a lot of 3D power, the Nvidia GPU seems like overkill (regardless of whether you go for Intel or AMD CPU).

---

### Post by tekno62 on 2014-12-11
> **Temüjin said:**
> 

Be more specific. I can't tell you how much BS has been posted on these forums (and the internet in general) that begins with "I read..." or "I heard..." 

Actually it was from my search here on the above list mother boards plus Google and from one of the Debian forums ( I think it was from linuxquestions.org but not 100% sure) also from reading these forums I was giving the impression to just stay away from Gigabyte all to gather. I may have just misinterpreted what people had posted. 

Ubuntu Forum search 
A78M - [http://ubuntuforums.org/search.php?searchid=6454192](http://ubuntuforums.org/search.php?searchid=6454192)

A88X-Pro - [http://ubuntuforums.org/search.php?searchid=6454179](http://ubuntuforums.org/search.php?searchid=6454179)



Also these maybe one off problems 

MSI AM1I - [http://ubuntuforums.org/showthread.php?t=2227667&highlight=AM1I](http://ubuntuforums.org/showthread.php?t=2227667&highlight=AM1I)

[http://www.tomshardware.com/answers/id-2349938/asus-am1i-black-screen-single-beep.html](http://www.tomshardware.com/answers/id-2349938/asus-am1i-black-screen-single-beep.html)

Tek

---

### Post by Yellow Pasque on 2014-12-11
Your first two links are broken. The last link points to a faulty board (which can happen with any mobo) and I just skimmed it, but I didn't see any mention of Linux.

As for the sound issue, it's hard to say if that would affect you without more info. Specifically, I wonder if that person's issue would be fixed by a later kernel (or at least the latest sound driver/module).

---

### Post by tekno62 on 2014-12-11
sorry for the broken links I just search the forum for the MB model that is before the link. I would like to have one of the Asus board as for sound My OCD would take control and I would have to have it whether I used it or not.

---

### Post by kurt18947 on 2014-12-12
I just dealt with a problem that may be relevant to this thread.  I said in post #4 that we have this ASRock FM2A88M-HD+ with integral Radeon HD8470 video and it was working great.  Well, it was .... until yesterday. I ran the updater, rebooted and ............... no boot.  I'm running Ubuntu-gnome on it, I'd get the 3 dots, brief blank screen, 3 dots forever.  I initially suspected a Plymouth problem and tried some things there. I then said "okay, I'll try Xubuntu"  Installed that and same problem - fresh install and it booted fine. Run updates, reboot and nothing.  It turns out the open source AMD video driver appears borked.  If I went to recovery then resume with its warning about video drivers possibly not installing the machine booted and worked. Setting "nomodeset" in GRUB also seemed to work but the suspend/resume still failed.  My fix was to install AMD's proprietary driver and everything seems to work.

I've had a similar occurrence with the Nvidia open driver.  It caused suspend/resume problems. This problem was a little tougher tougher for me because the machine wouldn't even cold boot.

---

### Post by tekno62 on 2014-12-12
maybe I should just spend the cash and go with an Intel CPU MB -

---

### Post by QIII on 2014-12-12
Hello!

I think you still may be misinterpreting and jumping to conclusions.  I don't see any answers in this thread that indicate that either a Gigabyte board or an AMD chipset are necessarily problematic.

---

### Post by kurt18947 on 2014-12-12
> **tekno62 said:**
> maybe I should just spend the cash and go with an Intel CPU MB -

Not necessarily, though I have had better luck with Nvidia desktop graphics. AMD CPUs/APUs and Nvidia graphics can work together nicely.

---

### Post by Yellow Pasque on 2014-12-13
> I plan on using the system for a DIY laser engraver

For those of us not familiar with that, is that sort of thing demanding on the CPU or GPU? We had an old laser etcher at one of my previous workplaces. It ran off an original Pentium-era system running Windows 95...

---

