---
title: "Please check specs for an Ubuntu box"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by eoren1 on 2007-11-11
I'm building a new HTPC/NAS which I plan to boot with LinuxMCE (on top of Ubuntu 7.10) and Win XP.
My current plan is:
GIGABYTE GA-73UM-S2H LGA 775 NVIDIA GeForce 7150 HDMI Micro ATX Intel Motherboard (GeForce 7150/nForce 630i chipsets)
Intel Pentium Dual-Core E2140 (1.6GHz 65W 1MB L2)
2 gigs DDR2-533 Ram
2 SATA HDDs (320+500)
Antec NSK2480 case with 380W PSU.
PVR-150 TV card.
Will the motherboard work well with Ubuntu or are the chipsets too new?
Thanks a lot!
E

---

### Post by LifeZagger on 2007-11-11
I was checking out the same mobo last night in looking at a new system.  In searching the forum and the internet in general, I couldn't find any reference to anyone installing linux with that mobo.  I did find some people having issues with the 7150 video, but that was on laptops.  

Personally, I wouldn't mind if the hdmi out didn't work, but I wouldn't want to have any issues with the dual video out as I like to run dual screen on my desktop.

---

### Post by eoren1 on 2007-11-11
The board is awesome - literally everything I could imagine.  Only problem is the chipset is so new that drivers might take a while.
E

---

### Post by Bartender on 2007-11-15
> **eoren1 said:**
> The board is awesome - literally everything I could imagine.  Only problem is the chipset is so new that drivers might take a while.
E

Do you mean you like the motherboard regardless, or do you mean you installed Ubuntu and it's working?

---

### Post by eoren1 on 2007-11-15
The motherboard itself seemed too good to pass up.  Just got it but am waiting on the case to arrive.  I'll post again Wednesday with the results.

---

### Post by tylercal on 2007-11-16
I bought this motherboard too. My case arrived yesterday (I couldn't pass up the Antec Fusion). So far I can't get any support for the on-board graphics or sound. Everything works in Vista with media center great though. NVIDIA just released Vista drivers 10 days ago, hopefully they won't be too much further behind with Linux support. The last Linux driver was released September 18th. Sounds like they're due for an update to me.

---

### Post by eoren1 on 2007-11-16
That sucks....so are you able to do anything or is there no video output at all?  I guess I'll load up vista in one partition and see about linux mce in another.  Please keep me updated with what you discover.  My email is my username at hotmail.
Thanks!
E

---

### Post by tylercal on 2007-11-16
Basic video output works, so max resolution of 800x600, but no hardware acceration or anything like that. I think the sound is having the same problem as the video card in that you need drivers for the chipset which is brand new. I'll post anything I find, but it sounds like its just going to be a waiting game =(

---

### Post by eoren1 on 2007-11-16
Looks like beta drivers are out:
[http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

Can you check them out and report back? 
Thanks,
E

---

### Post by sreyan on 2007-11-24
I too bought a 7150/630i motherboard with hdmi. Running Gusty and the beta 169.04 nvidia drivers works well. I still cannot get onboard sound, though gentoo folk say that using the hda_intel module should work. I tried modprobe snd_hda_intel but I still have no sound. I am running kernel-2.6.22-14-generic

---

### Post by sreyan on 2007-11-24
Ahh looking at the kernel config in ubuntu i see that the intel hd audio module is not included in the kernel. 

Using these instructions
[http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/](http://symbolik.wordpress.com/2007/11/10/vanilla-kernel-26231-on-gutsy-gibbon/)
and kernel 2.6.23.8, i have everything working onboard! 

note that i only added the intel hd audio module and did not mess with the timer or anything else.

---

### Post by sreyan on 2007-11-24
better way that recompiling a kernel

just install linux-modules-backports :)


perfect HTPC!

---

### Post by sdukas on 2007-12-12
It seems I've been having the same problems as the rest here. No audio through HDMI. 

I just tried placing in the linux-backports-modules like was suggested. Now the sound driver seems to load and I can actually access alsamixer. 

Yet still no sound out of the HDMI. I'm wondering if you did anything else within the /etc/modprobe.d or anything like that to make it work? Or is there anything in the BIOS I should be checking on or off?

Thanks for any response.

---

### Post by w116tjb on 2007-12-21
Wondering-Same-Thing-Bump.

---

### Post by sdukas on 2007-12-26
I'm going to try and upgrade to the new Ubuntu 8.04 Alpha sometime in these next couple of days. It now uses the 2.6.24 kernel so I'm hoping to have better luck there. 

I'll post my results later.

---

### Post by sdukas on 2008-01-04
Status Update..nothing yet from the Ubuntu 8.04 Alpha. I'll try playing around with the settings and see if anything kicks in.

---

### Post by sofamensch on 2008-02-01
I am about to order a board with onboard 7150 too.. so please keep me up to date how the drivers and kernels are working. Won't buy it without my beloved compiz running on it ;-D

---

### Post by sdukas on 2008-02-01
I believe that with the driver compilation on the old kernel that all my graphics properties and what you would need for compiz worked fine. The only thing that didn't work for me them was the audio through HDMI. Since then nvidia has released new drivers. Still haven't had much of a chance to do anything with it though. I'll try to keep you informed.

---

### Post by sdukas on 2008-02-11
Ok so I finally had a break to toy with this again. I wiped my system and started fresh with an install of Ubuntu 8.04 Alpha 4. It seems Alpha 4 has better sound control for the drivers of this board. Though still no audio through the HDMI. 

Graphics drivers worked perfectly through the proprietary driver setup. It uses the 169.09 driver it seems (which was a pleasure to see).

At this point, I've resorted to using normal Analog RCA L+R outs from the board. Once I find my optical cable I will test that too. 

So in all....things work well with the new Ubuntu Alpha release but as of yet i have not found a way to get the HDMI audio working.

---

