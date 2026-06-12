---
title: "AMD drivers not working in 20.04"
date: 2021-04-14
forum: Hardware
---

### Post by kenohara on 2021-04-14
I have an interesting issue here on a workstation build i took over. 

I have working currently amdgpu-pro-20.10-1048554-ubuntu-18.04 in Ubuntu 20.04 build (a slightly hacked install to fool driver into thinking it's 18.04) 

However when i uninstall and say install the AMD 20.20 version for Ubuntu 20.04 i cannot use my GPU and all tools to access fail like clinfo shows 0 devices available. Ive tried 20.40 and 20.45 amdgpu-pro versions same each time. 

Anyone suggest how i may fix this? 


Thanks.

---

### Post by CelticWarrior on 2021-04-14
Welcome.

Why do you think you need the proprietary overlay? The open source amdgpu is already installed by default and it works even with Secure Boot enabled, unlike the unnecessary driver that you're trying to install (it's probably failing due to Secure Boot).

There's no reason whatsoever to install amdgpu-pro outside of very specific professional applications.

---

### Post by kenohara on 2021-04-14
Hi thanks for your reply, well of course the reason being the GPU i am using is a newer version hence why AMD make newer versions available to support the newer chipsets? 

Releases such as 20.10 20.20 20.40 20.45 etc. 

Specifics helps to enhance graphic and mining performance. 

Anyway my question is more about why an apparent non compatible version is working with Ubuntu 20.04 from AMD work but the actual 20.04 version of that driver from AMD doesn't. 

How does Secure boot prevent this? I see no indication in syslogs etc only errors when initialising the AMD GPU and the driver set that should work.


This is the guide i was using 

[https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation](https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation)

---

### Post by CelticWarrior on 2021-04-14
> **kenohara said:**
> Hi thanks for your reply, well of course the reason being the GPU i am using is a newer version hence why AMD make newer versions available to support the newer chipsets?

Ubuntu and any major Linux distro already have amdgpu which usually is ONLY what users need. No additional user action needed and it works beautifully. Of course, you you have a brand new AMD card released after the kernel version running, you need a newer kernel (amdgpu included) and/or a newer release.

> Releases such as 20.10 20.20 20.40 20.45 etc.

Specifics helps to enhance graphic and mining performance.


It gives NO enhancements for any typical usage, including gaming, all the opposite. Mining? Maybe, but that's dumb and an  environment problem anyway so...

> Anyway my question is more about why an apparent non compatible version is working with Ubuntu 20.04 from AMD work but the actual 20.04 version of that driver from AMD doesn't.

How does Secure boot prevent this? I see no indication in syslogs etc only errors when initialising the AMD GPU and the driver set that should work.
Secure Boot prevents loading unsigned drivers which is exactly what you installed. The included amdgpu isn't so it works with or without Secure Boot.,

---

### Post by kenohara on 2021-04-14
What an arrogant response. 
So to summarise revision of drivers are of no use or advantage. 
Its absolutely does offer advantages or AMD wouldn't bother to offer improved architecture and improved drivers to address that new architecture. 

Go away back into your hole. 

'Mining..that's dumb' just about sums up your level of maturity.

---

### Post by CelticWarrior on 2021-04-14
[https://www.youtube.com/watch?v=bcXCYCaLh1I](https://www.youtube.com/watch?v=bcXCYCaLh1I) -> 2018 - the current situation is pretty much the same which isn't, at all, surprising, because the [amdgpu]("https://en.wikipedia.org/wiki/AMDGPU") driver is open source but developed by AMD themselves, unlike its counterpart for Nvidia (nouveau) which is develeped by the community with zero input from Nvidia. So yes, AMD does offer "[COLOR=#000000]improved architecture and improved drivers" both in amdgpu and amdgpu-pro and AMD's adherence and commitment to the open source model now is commendable after all those years releasing poor closed source drivers that always lagged behind those of Windows. [/COLOR]

A more in-dept and recent analysis by real experts with real, verifiable data: [https://www.phoronix.com/scan.php?page=article&item=amd-drivers-sep20&num=1](https://www.phoronix.com/scan.php?page=article&item=amd-drivers-sep20&num=1)

There's anecdotal evidence about amdgpu-pro performing slightly better for Matlab, 3D rendering and the likes. Is it better for crypto mining? I'm really not sure and that is a purely technical opinion irrespective of [other considerations]("https://www.gizmodo.com.au/2018/11/mining-bitcoin-can-be-more-of-an-energy-drain-than-actual-mining/"). And you can't argue against facts, nobody can right now earn more than they waste in electricity costs, especially if using a consumer grade machine with one or two GPUs. People of a certain age and maturity usually have no other option than to pay their own very expensive electrical bills, I know I do. Only the people who don't pay for their own electricity and/or are of certain ideological persuasions may think mining is a good idea.

---

