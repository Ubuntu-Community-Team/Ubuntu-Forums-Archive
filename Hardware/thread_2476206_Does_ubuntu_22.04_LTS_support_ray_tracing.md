---
title: "Does ubuntu 22.04 LTS support ray tracing?"
date: 2022-06-19
forum: Hardware
---

### Post by WHK on 2022-06-19
I have a AMD Radeon RX 6800 XT and Ubuntu 22.04 LTS with native amdgpu driver. I have searched for some ray tracing demos on the internet but unfortunately almost all of them are only available for windows, the few that I found compatible with linux do not compile (by example [https://github.com/GPSnoopy/RayTracingInVulkan/issues/58](https://github.com/GPSnoopy/RayTracingInVulkan/issues/58) ). I have installed through Steam a game called "Bright MEmory Infinite Ray Tracing Benchmark" that when trying to run it says that my hardware does not support ray tracing. Quake 2 RTX on Steam does not work, says: "No ray tracing capable GPU found".

I don't know if my operating system really doesn't support ray tracing or I haven't been able to find a suitable demo. Do you know if ubuntu 22.04 LTS supports ray tracing for AMD 6800 GPUs?

---

### Post by TheFu on 2022-06-20
It isn't the OS.  I'd check the GPU driver details.  Do you have Vulkan stuff installed? Does the program use the Vulkan interface?

> Hopefully soon AMD will at least work on posting the ray-tracing support for the open-source AMDVLK Vulkan driver but so far I haven't received confirmation on when they plan on enabling AMDVLK support for Vulkan RT.

People often confuse the OS with GUI stuff, though they aren't really related at all.  Drivers make hardware features available. Libraries allow access to the drivers.  Programs access the drivers through libraries and APIs.  The OS also has APIs, libraries, which programs can access.  The most basic example is the open() function which opens files.  Almost everything on a Unix-like OS is a file, so understanding the open() function is core to not just file stuff (like we end users think about "files"), but for accessing all the hardware in the system.  Drivers create the "files" so we can communicate with the different hardware using the normal file nomenclature. It is very elegant. 

[https://www.gamingonlinux.com/2021/09/ray-tracing-on-linux-with-amd-gpus-gets-closer-with-multiple-games-working/](https://www.gamingonlinux.com/2021/09/ray-tracing-on-linux-with-amd-gpus-gets-closer-with-multiple-games-working/)
[https://www.phoronix.com/scan.php?page=news_item&px=Radeon-Software-21.10](https://www.phoronix.com/scan.php?page=news_item&px=Radeon-Software-21.10)
I used a web search tool to find those articles.

It is possible to run Ubuntu without any GPU at all. That's how I know the GPU driver isn't part of the core OS.

---

### Post by WHK on 2022-06-20
Thanks, but the links use amdgpu-pro for ubuntu 16, the download page of 6800 series driver download the normal amdgpu. I understand that the operating system is not part of the development of the gpu drivers, but the ubuntu distribution should provide what is necessary for these drivers to work correctly in an official way. I wanted to know if I should ask canonical, amd for help or is it a configuration problem.

I installed vulkan-sdk package from lunar repository but I've still had trouble running demo applications.

---

### Post by TheFu on 2022-06-20
Drivers are the responsibility of the hardware vendor, not the OS.  When/if the hardware vendor makes those drivers compatible with Canonical's policies on redistribution and they pass compatibility testing, then is when I'd look for them as part of the default drivers provided.

Canonical has never created any GPU drivers. Neither has Redhat.  The drivers come from F/LOSS project teams or the vendors.

If AMD has support, like forums, I'd ask there.

---

### Post by QIII on 2022-06-20
Just to make it clear:  Windows does not support any vendor's drivers.  Redmond does not lift a finger to help hardware OEMs.

It is ***all ***on the OEM to ensure that their drivers work on Windows.  If they don't, they don't get included in the driverbase.  

It's pretty simple:  If you don't make your driver work with Windows, you go out of business.  If your Linux driver does not work well ... meh.  You lose 2% of users.

---

