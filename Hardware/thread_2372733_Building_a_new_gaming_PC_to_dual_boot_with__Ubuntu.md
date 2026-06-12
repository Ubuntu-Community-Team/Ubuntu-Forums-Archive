---
title: "Building a new gaming PC to dual boot with  Ubuntu. Anything I should avoid?"
date: 2017-09-28
forum: Hardware
---

### Post by thepie2 on 2017-09-28
I just want to build a decent gaming PC that will work well with Ubuntu. I want to  order the parts Saturday. Planning to spend under $1000. Leaning toward AMD Ryzen. I can update this  post later with specific parts. Until then, advice  on what  to look for and what to  avoid is welcome. Thanks.

detailed parts list work in progress

AMD Ryzen 5 1600 Processor
[https://www.amazon.com/dp/B06XNRQHG4/](https://www.amazon.com/dp/B06XNRQHG4/)

ASRock AB350 PRO4 ATX Motherboard
[https://www.amazon.com/dp/B06WWF165R/](https://www.amazon.com/dp/B06WWF165R/)

PowerColor AMD Radeon RX 560 Red Dragon 2GB Graphics Card
[https://www.amazon.com/dp/B071NXBPMY](https://www.amazon.com/dp/B071NXBPMY)

G.SKILL 16GB (2 x 8GB) Ripjaws V Series DDR4 PC4-25600 3200MHz
[https://www.amazon.com/dp/B017RKV4N2/](https://www.amazon.com/dp/B017RKV4N2/)

2 X WD Blue 1TB SATA 7200 RPM Hard Drive (WD10EZEX)
[https://www.amazon.com/dp/B0088PUEPK/](https://www.amazon.com/dp/B0088PUEPK/)

NZXT S340 Mid Tower Computer Case
[https://www.amazon.com/dp/B00NGMIBUU/](https://www.amazon.com/dp/B00NGMIBUU/)

SeaSonic G Series 550-Watt ATX12V/EPS12V Power Supply
[https://www.amazon.com/dp/B00918MEZG/](https://www.amazon.com/dp/B00918MEZG/)

---

### Post by Autodave on 2017-09-28
Personal opinion only: Nvidia GPUs are much easier to set up and update.

Again, my opinion only: I am sure some others will disagree.

---

### Post by thepie2 on 2017-09-28
Intel is kind of scary right now. Am I wrong?

[https://www.eff.org/deeplinks/2017/05/intels-management-engine-security-hazard-and-users-need-way-disable-it](https://www.eff.org/deeplinks/2017/05/intels-management-engine-security-hazard-and-users-need-way-disable-it)

---

### Post by Autodave on 2017-09-28
I have never had a problem getting an Nvidia card running correctly. Hoever, I have 2 Radeon cards here that I gave up on.

---

### Post by thepie2 on 2017-09-28
Is Ubuntu incompatible with all Radeon cards?

---

### Post by QIII on 2017-09-28
I have never had an issue with AMD graphics cards.  Never an issue with Nvidia, either.

If you get a GCN 2.0 or later AMD card, you don't even have to install a driver.  16.04 and later will install the appropriate driver when you install the OS.

The cards listed at [http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx) are supported by AMDGPU-PRO, which is the proprietary overlay for AMDGPU.  You can be sure that these will work and that the AMDGPU driver will be installed.  I can't say for sure, but I suspect that since RX 480s are supported, RX 5xx would be.  But do your homework.  Please visit my blog for an article about supported (or soon to be supported) cards.

If the card is not supported by AMDGPU, Radeon will be installed.

It's becoming automatic for AMD.

Even in the days of the fglrx driver, 90% or more of the difficulties people ran into had to do with either not first uninstalling an Nvidia driver or failing to initialize fglrx.  I have hundreds of posts on the forum directing people to do tbose two things.

---

### Post by thepie2 on 2017-09-28
Are "AMDGPU-PRO" and "AMDGPU" drivers which I'll have to install. How would I know if I need them? If I do need them, how will I install them?

---

### Post by QIII on 2017-09-28
If your card is supported by AMDGPU, it will be installed when you install Ubuntu.  You can only install the AMDGPU-PRO overlay if AMDGPU is installed.  If your card is not supported by AMDGPU, the Radeon driver will be installed.

It's automagic now.  You don't need to do anything unless you have a need or pressing desire for the overlay-- for instance if you need Vulkan support. In that case, AMD has a script that will take care of it.

---

### Post by gordintoronto on 2017-09-28
I was in your position a few years ago. I made extensive use of the reviews at newegg, basically requiring each component to be at least 80% in the top two categories.

A couple of things which many people ignore are the case and the power supply. I spent a little extra on both. I have never cut my hands, while building the computer or modifying it. The case is big, with good airflow. The power supply has never caused any grief.

Tom's Hardware is another resource which is worth checking out. Many people prefer motherboards not made by asrock.

A specific suggestion: get a Samsung SSD for the OS. It doesn't need to be huge, unless you like trying lots of different distros.

My approach was a success. The computer is still wonderful after seven years. (I've upgraded memory, an SSD and the optical drive.)

Plan on using the latest and greatest OS with the latest hardware. That means 17.10. When I built my computer, the Ethernet port and CPU temperature sensors were not supported, but support was just six months away.

---

### Post by thepie2 on 2017-10-01
I intend  to stick with mechanical hard disks for the moment.  I'll decide later how badly I really want the performance benefits an SSD might offer me.  Thank you.

---

### Post by efflandt on 2017-10-03
Not sure how inflated prices are with graphics cards right now in cryptocurrency craze (or performance of Ryzen CPU's), but I have been partial to Nvidia since earlier issues with AMD drivers in Linux Steam. According to gpuboss.com a 4 GB GTX 1050 Ti would be somewhat faster than a 4 GB RX 560 (and you are looking at 2 GB) and 6 GB GTX 1060 is significantly faster. I am running a 3 GB GTX 1060 which due to texture compression only uses about half of its RAM max (and 95-100% GPU max) when run by an old i7 870 (slower than newer i5) at about 60% max for Steam games I play in Linux.

4GB RX 560 is often compared with 4 GB GTX 1050 Ti
4GB RX 570 is often compared with 3 GB GTX 1060 (or 6 GB GTX 1060 which likely has little difference over 3 GB @ 1080p)
It is difficult to find direct comparison of 2 GB RX 560 with 3 GB GTX 1060

---

### Post by adelpozoman-f on 2018-04-28
You could wait a little bit to see if you can find a good offer on a rx 570 or even a 580. Also I would opt for and SSD instead of one of the 2 HDD

---

### Post by oldfred on 2018-04-28
I found SSD makes it a lot faster to install, boot , and initial load of programs. It has not improved my typing speed which seems to be the remain major bottleneck in my system. :)

 ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu) 

 Asus Prime X399-A  with AMD Ryzen 1950X  Ubuntu 16.04.3
[https://ubuntuforums.org/showthread.php?t=2380798](https://ubuntuforums.org/showthread.php?t=2380798) 
      
 The Fastest Linux Distribution For Ryzen: A 10-Way Linux OS Comparison On Ryzen 7 & Threadripper
[https://www.phoronix.com/scan.php?page=article&item=ryzen-linux-10way&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-linux-10way&num=1)

---

### Post by sp40140 on 2018-04-28
I suggest you go with SSD. Even the cheapest one will give you very noticeable performance jump. Platter HDDs have been bottleneck for long time. And since you plan to game.. it will make loading games quick as well.
Small SSD (which can hold two os) don't cost much these days and it doesn't make sense NOT to go with SSD at least for OS.

---

