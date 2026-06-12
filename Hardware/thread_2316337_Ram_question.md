---
title: "Ram question"
date: 2016-03-07
forum: Hardware
---

### Post by seal308 on 2016-03-07
Hello
I am using an eeebox 1006 running lubuntu.
It works a lot better than it did with xp or ubuntu however it still lags, can't use things like youtube, and isn't as snappy as a regular computer.
I'm just wondering if increasing the ram will really make a difference?
It currently has 1gb of ram and I ran dmidecode and it says the max it can take is 4gb. 
The cpu is a Intel atop n270 1.60 Ghz processor. 
I ran lspci and got this for the graphics card:
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v]

Thanks

---

### Post by sudodus on 2016-03-07
I think that video playing is limited by the CPU and GPU performance with Lubuntu and 1 GB RAM (I don't think it is swapping). You can install ***htop*** to monitor the CPU load and RAM usage while playing video with different resolution.

```
sudo apt-get install htop
```

But an extra gigabyte RAM will be good for the overall performance, for example, you can have more tabs open in your web browser, and several other tasks work without swapping. You will notice, when it starts to swap, because the computer gets very slow.

---

### Post by QLee on 2016-03-07
> **seal308 said:**
> Hello
It currently has 1gb of ram and I ran dmidecode and it says the max it can take is 4gb. 
Thanks

A word of caution to check ASUS specs on the eeebox carefully before you buy a 4GB RAM stick. It may only be able to use 2GB. The eeePC's, netbooks, of that era were only able to take 2GB.

---

### Post by seal308 on 2016-03-07
> **QLee said:**
> A word of caution to check ASUS specs on the eeebox carefully before you buy a 4GB RAM stick. It may only be able to use 2GB. The eeePC's, netbooks, of that era were only able to take 2GB.

Yes I looking into it online and the max ram is 2gb. Is there are reasons why dmidecode gave me a different max ram?

---

### Post by seal308 on 2016-03-07
> **sudodus said:**
> I think that video playing is limited by the CPU and GPU performance with Lubuntu and 1 GB RAM (I don't think it is swapping). You can install ***htop*** to monitor the CPU load and RAM usage while playing video with different resolution.

```
sudo apt-get install htop
```

But an extra gigabyte RAM will be good for the overall performance, for example, you can have more tabs open in your web browser, and several other tasks work without swapping. You will notice, when it starts to swap, because the computer gets very slow.

Ok thx, I can only have 2 or 3 tabs at the moment and heavyweight webpages give me lag.
I think I will upgrade.
Thank you.

---

### Post by QLee on 2016-03-08
> **seal308 said:**
> Yes I looking into it online and the max ram is 2gb. Is there are reasons why dmidecode gave me a different max ram?

Well, I'm sure there is a reason but I can't give you a definitive answer. However, I will state that I ran dmidecode on my netbook and got the same answer as you even though the specs for it online show as 2GB too.

---

