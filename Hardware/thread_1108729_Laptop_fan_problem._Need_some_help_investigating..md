---
title: "Laptop fan problem. Need some help investigating."
date: 2009-03-28
forum: Hardware
---

### Post by swinky on 2009-03-28
I have scoured the internet looking for a solution to my problem, but have not found a solution. I've decided to start digging into things for myself, but since I don't know a whole lot about the inner workings of Linux, I'm going to need some assistance.

The basics of my problem is that the fan in my laptop, a Toshiba Satellite L305-S5891, does not spin up in Linux, and the brightness keys don't work. I have tested this under Ubuntu 8.10 (32-bit), Debian Lenny (64-bit, at the time it was still the testing distro), Arch 64-bit, Fedora 10 64-bit(Live CD), and today I tried Ubuntu 9.04 Beta 64-bit(Live CD) and Fedora 11 Alpha 64-bit(Live CD), these functions work in none of them. They DO work in Windows Vista and Windows 7 Beta.

The omnibook module is installable to get these to work, however from what I have heard, there is a somewhat common problem that with the omnibook module enabled, the laptop will turn itself on 3-10 minutes after being shut down. I have tried the omnibook module in all of the above mentioned distros other than the live CDs, and sure enough, I have that problem on each of them.

The exception to all of this is when I boot into the kernel that was installed with 8.10 Beta (kernel 2.6.27-4-generic.) Somehow, when I boot into this kernel, the fan and the brightness keys work (though there is a bit of a delay with the brightness keys) AND the computer does not turn itself back on. The same computer also has three newer kernels that have been installed, but the fan/brightness works in none of these. So I know it is possible to do it, but not set up by default, and if I ever want to upgrade/reinstall anything other than 8.10 Beta on my laptop, I need to figure it out.

I have already done a side-by-side comparison of modules that are running in each kernel, but found that they are no differences. What are the chances that it might be something compiled into the one kernel but not the others? If so, would it be possible to find? What other possibilities exist, if it is not a difference in modules?

There is one other thing of note between different kernels. When I load 2.26.27-4, I get two notices that come up before the usplash screen loads, when I load any other kernels (including from other distros) I only get one of them. The one I get no matter the kernel says:
> pci 0000:02:00.0: unsupported PM cap regs version (7)
The notice I get ONLY when I load 2.26.27-4 says:
> ACPI: EC: GPE storm detected, disabling EC GPE
Since ACPI handles stuff like fans and brightness and the like, could that line about the EC GPE be significant? I tried to look more into GPE but it all got pretty far over my head pretty quickly.

I'd really like to get to the bottom of this, but am totally unsure where to start. Any help would be extremely appreciated! I was hoping newer versions of Ubuntu or Fedora would have fixed it, but it doesn't seem to be the case, and I'd rather not depend entirely on a single copy of Ubuntu 8.10 Beta if I ever need to reinstall.

---

