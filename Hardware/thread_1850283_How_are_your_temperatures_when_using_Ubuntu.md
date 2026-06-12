---
title: "How are your temperatures when using Ubuntu?"
date: 2011-09-26
forum: Hardware
---

### Post by domfliss on 2011-09-26
Hi guys,

I am thinking of changing Windows 7 for Ubuntu.  I am not sure yet, which version to go for (LTS or 11.04). 

My only concern and it's a big concern, is that in the past my laptops have got a lot hotter in Linux than in Windows.  I have also seen numerous posts expressing concern about heat, so if I was wondering if you guys could give me a heads up with your experiences.  The laptop I have is a G550 Lenovo with the Intel 4500 integrated graphics.  

I don't really care about games as I use my iMac for that (2011), but any input regarding heat would be really appreciated in regards to laptop experience.

Many thanks

---

### Post by -Shuji- on 2011-09-26
> **domfliss said:**
> Hi guys,

I am thinking of changing Windows 7 for Ubuntu.  I am not sure yet, which version to go for (LTS or 11.04). 

My only concern and it's a big concern, is that in the past my laptops have got a lot hotter in Linux than in Windows.  I have also seen numerous posts expressing concern about heat, so if I was wondering if you guys could give me a heads up with your experiences.  The laptop I have is a G550 Lenovo with the Intel 4500 integrated graphics.  

I don't really care about games as I use my iMac for that (2011), but any input regarding heat would be really appreciated in regards to laptop experience.

Many thanks

I think heat depends on how well your hardware was designed to dissipate heat and sometimes dust that gets stuck in the exhaust vent.  Newer models are better and don't get too hot.  I use 11.04 because it has better hardware support for my laptop.  I suggest you try 11.04.  I tried 10.04 and 10.10 but had problems with it.

Shuji

---

### Post by domfliss on 2011-09-26
Thanks for the reply.

The laptop is only 4 months old and it's Lenovo which are pretty good.  Would you suggest the 32 bit version or 64 bit?

---

### Post by sanderd17 on 2011-09-26
For a new laptop, certainly 64-bit.

And for the temperature, some people do indeed have problems with it. Most problems come from an unsupported graphical card. In that case, the CPU has to take over the image rendering, and that makes the CPU quite hot while the image is still stuttering.

---

### Post by domfliss on 2011-09-26
Thanks.  It's an Intel 4500m. 

I know it's not quick, but it's around in great numbers, lol.  Do you think it will give me problems?  Windows 7 is great for running cool, but it's Microsoft.  

I'm a mac user by heart and just can't stand Windows, lol.

---

### Post by SecretCode on 2011-09-26
I've had the opposite experience - laptops running cooler in Linux than in Windows. But the point about support for the graphics card is an important one - it makes a huge difference to CPU load, and a busy CPU can quickly heat up my laptop.

Unfortunately my general impression is that support for on-board Intel GPUs isn't great. For my current laptop I looked only at models with Nvidia, whose support is good.

Can only suggest you make a partition and install Ubuntu alongside Windows - that works well (back up your data first in case of an unlikely failure) - and see how it runs.

---

### Post by collisionystm on 2011-09-26
Run the live-cd and check your CPU usage.

---

### Post by SecretCode on 2011-09-26
The reason I didn't suggest live CD is that (in my experience) you can't install the proprietary graphics card drivers in a live CD ... because you have to reboot ... and it doesn't have persistence. 

A live USB should work, though.

---

### Post by domfliss on 2011-09-26
Thanks.  In the past I had only used the LiveCD to try out Ubuntu.  It ran around 44 degrees at idle.  If I go for an install, do you think it would be cooler?

---

### Post by SecretCode on 2011-09-26
It certainly wouldn't be hotter with a full install. It might run cooler if there's a proprietary driver that gives better Intel GPU support (or any updates help) ... but I don't know if there is.

---

### Post by .... on 2011-09-26
Linux can use more power than Windows, especially with recent kernels. [http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1)
I would try 11.04 first, and if power consumption is an issue, try using the pcie_aspm=force trick mentioned in the article.

> **SecretCode said:**
> The reason I didn't suggest live CD is that (in my experience) you can't install the proprietary graphics card drivers in a live CD
That's not applicable to Intel GPU's...

> I've had the opposite experience - laptops running cooler in Linux than in Windows.
The fan could be running faster in Linux too. Temperature really isn't a good measure of power consumption. Battery life is a better indicator.

> I think heat depends on how well your hardware was designed to dissipate  heat and sometimes dust that gets stuck in the exhaust vent.
Yes, but that's independent of the OS.

>  my general impression is that support for on-board Intel GPUs isn't great.
Could you be a little more vague please? ;P

---

### Post by maul9999 on 2011-09-26
> **domfliss said:**
> Hi guys,

I am thinking of changing Windows 7 for Ubuntu.  I am not sure yet, which version to go for (LTS or 11.04). 

My only concern and it's a big concern, is that in the past my laptops have got a lot hotter in Linux than in Windows.  I have also seen numerous posts expressing concern about heat, so if I was wondering if you guys could give me a heads up with your experiences.  The laptop I have is a G550 Lenovo with the Intel 4500 integrated graphics.  

I don't really care about games as I use my iMac for that (2011), but any input regarding heat would be really appreciated in regards to laptop experience.

Many thanks

It is not really hot.  All i need to control my fan is BIOS.  I wouldn't want any linux fan controller program on my computer.

---

### Post by .... on 2011-09-26
> **maul9999 said:**
> All i need to control my fan is BIOS.
That's great if your BIOS has good fan control, but the fancontrol script allows more control than most BIOS fan controllers. Also, laptops tend to use ACPI for fan control, and there are lots of issues with that on non-Windows OS's if the vendor only tested in Windows and/or has a shoddy ACPI implementation in the BIOS. Sadly, that's all too common.

---

### Post by maul9999 on 2011-09-26
> **.... said:**
> That's great if your BIOS has good fan control, but the fancontrol script allows more control than most BIOS fan controllers. Also, laptops tend to use ACPI for fan control, and there are lots of issues with that on non-Windows OS's if the vendor only tested in Windows and/or has a shoddy ACPI implementation in the BIOS. Sadly, that's all too common.

Yeah.  You're right.  Ubuntu can't replace windows or mac as most stable OS ever.  Sometime sound problem.

---

