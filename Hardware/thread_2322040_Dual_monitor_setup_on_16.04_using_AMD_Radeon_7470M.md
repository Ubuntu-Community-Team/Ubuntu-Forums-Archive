---
title: "Dual monitor setup on 16.04 using AMD Radeon 7470M?"
date: 2016-04-25
forum: Hardware
---

### Post by lazanet96 on 2016-04-25
As the title says, fglrx is not supported by new kernel, and Gallium driver cannot output to more than one monitor at the same time. Should I skip this edition, or there is some way I could make it work?

(Sorry for repost from [http://ubuntuforums.org/showthread.php?t=2321383](http://ubuntuforums.org/showthread.php?t=2321383) I think that I posted in wrong subforum)

---

### Post by QIII on 2016-04-26
Hello!

When you think you have posted in the wrong place, please use the "Report Post" button to ask the Staff to move it rather than creating a new thread.  I have closed the other.


I have had no trouble for many years getting three monitors running at one time using the Radeon driver.  

At install time, the installer will determine whether Radeon or AMDGPU should be used with your chipset.  When I first installed 16.04 with an R9 290X (Hawaii), which defaults to the Radeon driver, I got all three monitors.  When I installed with an R9 380X (Tonga), which defaults to the AMDGPU driver, I got all three monitors.

---

### Post by lazanet96 on 2016-04-26
Thanks for quick response 

I tried to remove post by myself, but it seems like that option is removed. If I make same mistake second time I will Report Post :)

I used Ubuntu 14.04, 15.04, 15.10 and 16.04 beta, and during all that time I was unable to output picture on multiple monitors at the same time (Laptop internal one, and VGA external). Only fix that worked for me was installation of fglrx driver (see [http://goo.gl/tkDtoQ](http://goo.gl/tkDtoQ)), and it was an option up until one 16.04 beta update broke compatibility with fglrx. In display options I could clearly see 2 monitors, however switching trough display modes would result one of them stop outputing picture. I filed a bug report, but since I needed to use this computer, I reverted two days later to 15.10 and have since been unable to answer to kernel related question ([https://goo.gl/7WGlLM](https://goo.gl/7WGlLM)). 

While using 16.04 live cd, I cannot get it to run anything other than Gallium, and it fails to output to multiple monitors, so I'm unsure should I waste my time trying to install 16.04 if it doesn't work on live cd (since 15.10 install with fglrx runs just fine)? Also I'm unsure if my graphics chip is (or will ever be) supported at all by new AMDGPU driver (since all relevant info I can find is on phoenix, not on manufacturer site, and is mostly based on speculations)?

Thanks in advance

---

### Post by lazanet96 on 2016-05-19
Ok, if I understood correctly this is the answer to my question:
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-SI-Experimental-Code](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-SI-Experimental-Code)

---

