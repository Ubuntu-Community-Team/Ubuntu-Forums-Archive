---
title: "IdeaPad 5G-14Q8X05 support"
date: 2023-01-11
forum: Hardware
---

### Post by alfredino on 2023-01-11
Hi,
I am new here. I bought a lenovo IdeaPad 5G-14Q8X05 which has the qualcomm snapdragon 8cx gen 2 aka SC8180XP and as far as I know it is currently not supported by the linux kernel. While the snapdragon 8cx gen 3 aka [SC8280]("https://git.linaro.org/landing-teams/working/qualcomm/kernel.git/log/?qt=grep&q=SC8280") has complete support starting from linux 5.19+ and snapdragon 8cx gen 1 aka [SC8180X]("https://git.linaro.org/landing-teams/working/qualcomm/kernel.git/log/?qt=grep&q=SC8180X") should have it from [linux 6.1+]("https://git.linaro.org/landing-teams/working/qualcomm/kernel.git/commit/?id=40285e64c5654c956505dad34ed2ee4be163b1f0").
Once the snapdragon 8cx gen 2 has the kernel support, what about drivers? I read about this project [Porting Linux to AArch64 Laptops]("https://www.linaro.org/blog/porting-linux-to-aarch64-laptops/") which supports few [devices]("https://github.com/aarch64-laptops/build#device-status").
What is the status of Ubuntu? Are you planning to support it?
Thank you

---

### Post by TheFu on 2023-01-11
Nobody here works for Canonical.  We are hobbyists. Unpaid. Volunteers, imparting decades of knowledge.  Between the group, you'll find some excellent advice and sometimes not so great advice.  Sometimes I'm good and sometimes I shouldn't post on things I know little about.

You may find that ARM CPUs are 2nd class systems for compiled binaries.  You might wan to use a distro that supports many more platforms than Ubuntu does.  Whenever posting for help in the future, you'll want to be clear that it is an ARM CPU, not x86-64, so people don't make all sorts of assumptions. This thread was extremely clear on that. Thanks.

When the Linux kernel adds support, that means the kernel tree will include the drivers for the devices.  Linux is different from MS-Windows.  The last place anyone should look for device drivers is from the vendor.  If you want a trouble free linux experience, buy hardware that is extremely popular and has been available at least 12 months.  Then you'll want to pick the recent release that has the kernel version you need.

In general, the LTS with 5 yrs of support doesn't have the latest kernels, which means you'll have to run a release that only gets 6-9 months of support from the date it was released.  Do you want to be forced into mandatory OS replacement every 6 months? That's what awaits if you cannot run 22.04 or 22.04 HWE kernels.  The next LTS is 24.04 ... so over a year away.  22.10 --> 23.04 --> 23.10 --> 24.04 are the releases you'll need to migrate/fresh install until the next LTS.  Maybe you will find that fun?  I don't.

As your Linux expertise increases, you may want to run out of distro kernel versions.  That's fine.  There is a tool for that called 'mainline'.  **I don't know if mainline supports ARM CPUs.**  I wouldn't expect it, but IDK.   The 'mainline' tool shifts the maintenance of the kernel and drivers from the built-in package system to you.  You'll need to decide when a new kernel is needed. It won't happen automatically and it is easy for someone to run a kernel with large bugs and security issues indefinitely because they forgot to move to newer kernels every week.  Not for noobs.

So, 22.10 has this kernel:
```
$ uname -r
5.19.0-23-generic

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.10
Release:        22.10
Codename:       kinetic

```

Looks like 22.04.1 has:
```
$ uname -r ; lsb_release -a
5.15.0-57-generic
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

```
I know think I'm running the HWE version.  Let me see of an HWE upgrade helps to get a newer kernel.
I installed 'linux-generic-hwe-22.04' which only has 5.15.x kernels.  That won't help you.

BTW, there are other distros with newer kernels.

---

### Post by alfredino on 2023-01-12
> **TheFu said:**
> Nobody here works for Canonical.  We are hobbyists. Unpaid. Volunteers, imparting decades of knowledge.  Between the group, you'll find some excellent advice and sometimes not so great advice.  Sometimes I'm good and sometimes I shouldn't post on things I know little about.

Of course.

> **TheFu said:**
> 
You may find that ARM CPUs are 2nd class systems for compiled binaries.  You might wan to use a distro that supports many more platforms than Ubuntu does.  Whenever posting for help in the future, you'll want to be clear that it is an ARM CPU, not x86-64, so people don't make all sorts of assumptions. This thread was extremely clear on that. Thanks.

OK I thought it was quite clear since qualcomm snapdragons are ARM CPUs and since I wrote [AArch64 that is also known as arm64]("https://en.wikipedia.org/wiki/AArch64").

> **TheFu said:**
> 
When the Linux kernel adds support, that means the kernel tree will include the drivers for the devices.  Linux is different from MS-Windows.  The last place anyone should look for device drivers is from the vendor.  If you want a trouble free linux experience, buy hardware that is extremely popular and has been available at least 12 months.  Then you'll want to pick the recent release that has the kernel version you need.

I agree, but the laptop has been release almost [two years ago]("https://kelaptop.com/en/lenovo-ideapad-5g-14q8x05-82kf0001ix") and the [SoC/CPU more than three years ago]("https://en.wikipedia.org/wiki/List_of_Qualcomm_Snapdragon_systems_on_chips#Snapdragon_8cx_Compute_Platforms").

> **TheFu said:**
> 
As your Linux expertise increases, you may want to run out of distro kernel versions.  That's fine.  There is a tool for that called 'mainline'.  **I don't know if mainline supports ARM CPUs.**  I wouldn't expect it, but IDK.   The 'mainline' tool shifts the maintenance of the kernel and drivers from the built-in package system to you.  You'll need to decide when a new kernel is needed. It won't happen automatically and it is easy for someone to run a kernel with large bugs and security issues indefinitely because they forgot to move to newer kernels every week.  Not for noobs.

Of course, the linux kernel supports many [ARM ISAs]("https://www.kernel.org/doc/Documentation/devicetree/bindings/arm/cpus.txt"). Whereas, as you pointed out, ubuntu [mainline kernel]("https://www.kernel.org/") is older than the latest one 6.1, as it uses the latest long term support.

---

### Post by alfredino on 2023-01-21
[COLOR=#333333]Since a few days, the daily builds of debian unstable have the [6.1 kernel ]("https://packages.debian.org/bookworm/linux-headers-6.1.0-1-arm64")and thus support the SoC of the laptop. So it is now possible to start the installation in both GUI and text mode, but the keyboard and mouse do not work. U[/COLOR]nfortunately, only the Gen 3 is listed in the debian [firmware-qcom-soc]("https://packages.debian.org/sid/firmware-qcom-soc") while the Gen 1-2 SoC is not yet.

---

### Post by TheFu on 2023-01-21
> **alfredino said:**
> OK I thought it was quite clear since qualcomm snapdragons are ARM CPUs and since I wrote [AArch64 that is also known as arm64]("https://en.wikipedia.org/wiki/AArch64").


That's purely my ignorance.  snapdragon is filed in my "cell phone/tablet" area and I barely use either.  "AArch64" is a term I don't remember seeing before.  Again, my ignorance.

> **alfredino said:**
> I agree, but the laptop has been release almost [two years ago]("https://kelaptop.com/en/lenovo-ideapad-5g-14q8x05-82kf0001ix") and the [SoC/CPU more than three years ago]("https://en.wikipedia.org/wiki/List_of_Qualcomm_Snapdragon_systems_on_chips#Snapdragon_8cx_Compute_Platforms").

Not extremely popular, regardless.  Any ARM system that isn't what the Raspberry Pi foundation uses won't be extremely popular. There are many excellent little computers built with ARM CPUs, but they seem to be niche players.

> **alfredino said:**
> Of course, the linux kernel supports many [ARM ISAs]("https://www.kernel.org/doc/Documentation/devicetree/bindings/arm/cpus.txt"). Whereas, as you pointed out, ubuntu [mainline kernel]("https://www.kernel.org/") is older than the latest one 6.1, as it uses the latest long term support.
I suspect you are confusing the 'mainline' tool with a mainline kernel.
[https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/) is what I meant.  I've used it in situations where a specific level of new kernel was required to get support for specific hardware.  In my case, it was to get AMD GPU driver support on a Ryzen 5600 for a system running Ubuntu Server 18.04 as the base OS.  That system has been updated to 20.04 and has the HWE 5.15.x kernel now.  

Anyway, I though 'mainline' could get you a new kernel that provided the hardware support desired. Definitely worth a look, if you wish to use Ubuntu.

---

### Post by alfredino on 2023-01-21
> **TheFu said:**
> 
I suspect you are confusing the 'mainline' tool with a mainline kernel.
[https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/) is what I meant.  I've used it in situations where a specific level of new kernel was required to get support for specific hardware.  In my case, it was to get AMD GPU driver support on a Ryzen 5600 for a system running Ubuntu Server 18.04 as the base OS.  That system has been updated to 20.04 and has the HWE 5.15.x kernel now.
  
You are right, I missed the word tool and thought of the kernel.

> **TheFu said:**
> 
Anyway, I though 'mainline' could get you a new kernel that provided the hardware support desired. Definitely worth a look, if you wish to use Ubuntu.

The next LTS kernel should be the version 6.1 (this time I read properly). However, as I wrote in the previous post, I still need drivers provided by [firmware-qcom-soc]("https://packages.debian.org/sid/firmware-qcom-soc") derived from [linux kernel firmware]("https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/").

---

### Post by TheFu on 2023-01-21
> **alfredino said:**
>  The next LTS kernel should be the version 6.1.  

Since the next Ubuntu LTS release is over a year away, I have doubts about that specific kernel being used.  Perhaps 6.4.x or 6.5.x will be the stable kernel in that time period.

Already released Ubuntu LTS versions - 22.04 and 20.04 kernel updates are in 2 lines.  The original kernel shipped with the initial release, which is getting back-patched for security stuff (that doesn't interest you) and the HWE kernel line.  [https://ubuntu.com/kernel/lifecycle#support-lts](https://ubuntu.com/kernel/lifecycle#support-lts) doesn't show any 6.x kernels.    5.15 is the latest listed kernel, but it doesn't have 22.04 information.  My 22.04 server, fully patched is on a 5.15 kernel.
 
I suspect Debian Testing is a better fit for your needs over the next 12 months than Ubuntu, unless you install the PPA for mainline and use one of those kernels.  These are the available 6.x kernels for installation TODAY in the mainline tool.
6.1.7                            
6.1.6                            
6.1.5                            
6.1.4                            
6.1.1                            
6.0.19                           
6.0.18                           
6.0.9                            
6.0.8                            
6.0.7                            
6.0.6                            
6.0.5                            
6.0.4                            
6.0.3                            
6.0.1                            
6.0.0

---

### Post by alfredino on 2023-01-22
According to [wikipedia]("https://en.wikipedia.org/wiki/Linux_kernel_version_history"), there are usually 4 (sometimes 5) minor releases of the linux kernel between two LTS releases. If history repeats itself, version 6.1 will have 5 releases since the last 5.15 LTS release.
Ubuntu follows a different cycle. For example, for version 20.04 there are 5.8, 5.11, 5.13 and 5.15 LTS kernel releases, while the official Linux kernel LTS releases are 5.4, 5.10 and 5.15. I have read that the next minor release of ubuntu [22.04.2]("https://www.omgubuntu.co.uk/2023/01/ubuntu-22-04-2-point-release-delay") should support linux kernel 5.19 via HWE.

---

