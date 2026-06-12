---
title: "Linux killed my laptop"
date: 2009-11-11
forum: Hardware
---

### Post by crackerizer on 2009-11-11
Hello all ubuntu users,

I have started this thread in Arch forum (As I use arch). But I think I would get more suggestion in this forum (As I was a ubuntu user :). As this problem is crucial. Please have a look at my problem and share your experience.

------------------------------------------------------------------------
I'd like to report something bad happened to my laptop. My intention is not to blame arch or linux world. This is just a caution when you run linux on your laptop. I'm not quite sure what is the cause but I will investigate it when my laptop returned. Here is my story.

I bought my laptop 2.5 years ago. It was preinstalled with vista. here is its specs:
- Acer Aspire 5580
- Core 2 Duo 1.66Ghz
- Geforce 7300Go
- 2GB DDR2-667
- 250 Gb HDD
- the rests are not important

Vista was replaced by Ubuntu since the first day i got my laptop. I lived happy with it since then. About 10 months ago, I moved to Arch. I'm happier with arch. But, since then, I have to return my laptop for repair 3 times (4 including this time), each time ended up with mainboard replacement (And I think I'll get a replacement this time too). The problem is alway related with the video card. When you turn it on, there are HDD & LED activities like normal, but nothing on the screen. At first, I thought it was acer fault (they gave me bad mainboards). But for this time, there were signs before it's broken. About 2 weeks ago (~2months since the last replacement), my screen statred to flickering when first turn on. It stays like that for a couple minutes and then back normal. And then, today, my laptop crashed twice. The second crash broke my laptop with the same symptom, nothing on the screen. At the first crash I can turn it on and work as normal for hours and I started to investigate the problem since then. After hours of investigation, I think it is heating problem. Actually, I feel since the very first time I installed arch that my laptop runs hotter. The cooling fan run very slow and will only blow hard when it gets VERY hot. I dont know if this is normal and I don't remember how it works in Ubuntu. So, I can't be conclusive.

There is a thing that I should note, I always use a workaround to run the video card in the full speed mode. This is for solving the black screen bug in the nvidia driver. I don't know if this is related but this also applied with ubuntu (without problem for year).

My last suggestion is, check your thermal tripping in the ACPI or find a way to better understanding how your laptop fan is controlled.

Please share your experience here. I'd like to hear from somebody who have the same problem.

Tony

---

### Post by howefield on 2009-11-11
> **crackerizer said:**
> I'd like to hear from somebody who have the same problem.

Go have a cup of tea whilst you wait, don't think there are too many "Linux killed my laptop" threads around here.

It isn't hard to figure out that running your "high performance" graphic card to the max all the time would generate significant amounts of heat, computers generally hate heat...

---

### Post by crackerizer on 2009-11-11
> **howefield said:**
> Go have a cup of tea whilst you wait, don't think there are too many "Linux killed my laptop" threads around here.

It isn't hard to figure out that running your "high performance" graphic card to the max all the time would generate significant amounts of heat, computers generally hate heat...

Yes, I know. I aways aware of that. Next time, I would try it again with ubuntu to see what will happen. As I mention, I use that for a year and a half with ubuntu with out problem. But 4 mainboards with arch is something that need to be investigated, at least for me.

---

### Post by howefield on 2009-11-11
> **crackerizer said:**
> But 4 mainboards with arch is something that need to be investigated, at least for me.

Well. it seems that Arch runs a close second around here in terms of users, so I'd expect you'll get some feedback shortly.

---

### Post by kerry_s on 2009-11-11
i personally think "acer" is just a bad brand. i've had countless problems with different acer products from laptop to lcd monitor. i now avoid that brand.

---

### Post by John Bean on 2009-11-11
Some distributions seem to misbehave with the fan control on my HP 6735s laptop too. Jaunty is fine, but if I boot the "System Rescue" CD (Gentoo based) it shuts down the fan and the CPU gets quite hot, as I see in the temperature monitor when I boot back into Ubuntu. I have no idea whether Arch behaves like that with yours but it's a possibility.

I always monitor temperatures routinely but even without the numbers it becomes pretty obvious when the temperature is getting too high - especially as in your case you forced it to run at maximum performance without adequate cooling. There are external coolers available for laptops to cover this very situation... 

Perhaps this thread should have been more appropriately titled "I meddled and killed my laptop but let's blame Linux anyway" ;-)

---

### Post by myromance123 on 2009-11-11
> I always use a workaround to run the video card in the full speed mode.

How was this done? You may very well have switched off/changed something that was extremely relevant to your laptops survival.

 I don't think its the OS but what you did and not truly knowing what that thing you did does beyond what you comprehend it as being able to do that caused several deaths in a row.

 Try and recap, what exactly did you do? What codes did you mess around with? Then maybe others can point to the exact problem point instead of having to infer on what you said :)

 Anyways, good luck ;)

---

