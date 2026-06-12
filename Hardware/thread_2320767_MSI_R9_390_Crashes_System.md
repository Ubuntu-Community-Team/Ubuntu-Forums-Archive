---
title: "MSI R9 390 Crashes System"
date: 2016-04-17
forum: Hardware
---

### Post by spit4520 on 2016-04-17
Hello,

I am a new ubuntu user who has installed Ubuntu on my primary system which is a gaming/workstation I have the R9 390 and I have experienced countless black screens with unresponsive lockups in 14.04 15.10 and 16.04 I have been reluctant to make a post as I was hoping for the issue to be solved but now I have no choice the system is unusable. after about 20 minutes my whole system locks up and the screen goes black. I have the Hawaii firmware on board because I cannot find the Grenada firmware I know that the cards are very similar but not the same. I also know that there are hundreds of posts like this all across the internet I just need help with my specific case. I will be able to attach any log file that is requested. I just dont understand how some users do and others do not encounter this issue with Grenada Pro cards 


Best Regards 

scott

---

### Post by Petro Dawg on 2016-04-17
Just a couple questions to aid in troubleshooting... Does it occur when you use generic video drivers? The problem you describe could be caused by various hardware issues. Such as bad capacitors and/or faulty CPU or GPU. How have you narrowed it down to the graphics card? Have you made any other component changes recently?

---

### Post by spit4520 on 2016-04-17
Thank you for responding. I have removed the video card completely and everything worked perfectly. The system was not stable a few months ago when I tried 14.04 for the first time and then I tried to find a solution then to no avail. I moved then to 15.10 and the solution was actually worse. I am using the AMDGPU along side the Radeon drivers. I have tried the AMD proprietary drivers and they actually crashed the system all three times on install. I am for-certain that it is something inside of either AMDGPU or Radeon, also I do not have a bin file for the grenada chip set inside of the radon file i only have the Hawaii the chips are again similar but not the same to my understanding.

Thanks

Scott

---

### Post by Petro Dawg on 2016-04-17
The fact that you can get it to run for 20 min before it freezes/crashes suggests a possible graphics card hardware issue to me, especially since the computer works perfectly without the card installed. 

Is this a dual boot system with Windows? I wonder if it works with all the proper windows Radeon drivers installed.

Is the powersupply sized correctly for use with this card? Can you do anything to force the freeze? Such as running a specific program or exposing it to an excessive graphics load. I would try installing and running glmark2 to see if it crashes repeatedly at one particular test or determine if seems to crash at random. The more random the crashing, the more likely it is heat related or some other sort of hardware issue.

---

### Post by spit4520 on 2016-04-17
I am dual booting, but I am using a completely separate solid state drive for my linux instillation because I did not want to run the risk of tanking my whole machine. I have run this card under multiple different stress tests in windows and it appears to be running just fine to me I have had the card since November of 2015 and I am more than happy with the performance in Windows. I know that at this time Ubuntu will not give me the same performance, But I am aware of that and I want the challenges that come along with it so I can learn from them and hopefully one day give back to the community.

I have heard that the AMDGPU-PRO driver is going to be released is that another version of the proprietary driver from AMD?

---

### Post by QIII on 2016-04-18
AMDGPU PRO is a significant revolution from fglrx.  It will likely not work with your R9 390X because AMDGPU works with the Volcanic Islands chipsets.  The R9 380 has such a chip.

Add to that the fact that fglrx will not work - and is not even included - with 16.04 and you have some frustration.

The open source community has long called for AMD to help with producing a genuinely good open source driver and a good proprietary driver.  They listened.  For several years AMD has been working with the open source community (specifically Canonical) to make that happen.  At the same time, they have been pressing forward with their Vulkan technology.  They have been busy.

The upshot is that we will have what we asked for, but it will be rough while we get there.  The plan is for everything to be shaken out by the end of this summer.

---

### Post by spit4520 on 2016-04-18
What do you suggest that I do in the mean time? the integrated graphics in the i5-6600 are more than sufficient for most things, but what about the hundreds of people effected by this issue and also gaming?

I believe this issue is souly related to a heating issue. I was able to run my system from a cold boot for almost an hour before the system fell over, but the issue is that its not just the graphics card that falls over the entire system falls over with it. I was unable to SSH into my desktop nor could any of my services continue not continue for example spotify began to play the last track on a 2 second loop over and over again. my system is more than sufficiently cooled though the fans on my graphics card never turned.

---

### Post by skinner345 on 2016-07-31
I have an R9 M395x and Whenever i install the AMDGPU-Pro drivers X will crash (blinking curser after the Ubuntu logo) 

My hardware is supported. Open Source alternatives work.

---

