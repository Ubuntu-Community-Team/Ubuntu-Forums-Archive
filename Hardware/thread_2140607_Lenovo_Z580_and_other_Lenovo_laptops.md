---
title: "Lenovo Z580 and other Lenovo laptops"
date: 2013-04-30
forum: Hardware
---

### Post by HugoNotte on 2013-04-30
There are several threads mentioning the same problem: Ubuntu booting only after a huge delay of up to 20 minutes. It seems like it always boils down to Lenovo laptops, many of them a variant of the Z580.
It seems like that Ubuntu based distributions (maybe Debian too?) have got a problem with the Firmware / BIOS handling the battery. Removing the battery before the boot up solves the problem, obviously one has to have the power cord plugged in. After boot up the battery can be put in and everything is fine. 
A more elegant solution has been posted here:[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217/comments/63However"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217/comments/63

[/URL]However, I feel Ubuntu being a very popular distro and many of the users happen to be new to Linux or at least not very technical, there should be a simpler solution than compiling and diving into the depth of grub configuration files. After all, distros like OpenSuse 12.2 &12.3 and Fuduntu do boot without problem. Could that be due to differences in their /sys/firmware/acpi/tables/DSDT files? 

I have tried for several months now and was hoping that Ubuntu 13.04 might solve the issue, but it doesn't. Since I have been working with Mint & Ubuntu for years now, I prefer those distros over OpenSuse, which has come a long way in ease of use. But the way things are done and the choice of software in the repositories for Ubuntu & Mint makes those my favorites. 

Any idea what can be done?

---

### Post by HugoNotte on 2013-05-05
no idea, any one?

---

### Post by facelikebambi on 2013-05-19
Completely agree. I've been having the same experience with my Z580 and was really hoping the new kernel in Ubuntu 13.4 would make a difference.

On the bug tracking thread you referred to, there seemed to be a ray of hope here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217/comments/103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217/comments/103)

But in the most recent update, the same author is less positive about things: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217/comments/107](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217/comments/107)

As that issue is still not assigned to anyone, I'm not optimistic about a proper fix for a while :(

---

### Post by nekoexmachina on 2013-05-19
[x] Don't buy cheap devices from Lenovo.

---

### Post by facelikebambi on 2013-05-19
> **nekoexmachina said:**
> [x] Don't buy cheap devices from Lenovo.

Yeah thanks for the constructive input.

---

### Post by flankerr on 2013-05-23
Try passing acpi=off to kernel parameters.
I have a Lenovo Z580 with Lubuntu 13.04, and it worked for me.

---

### Post by facelikebambi on 2013-05-25
Thanks. Turning ACPI off will disable some power-management  features in the kernel, and may also disable hyper-threading. But it has been widely reported to work, at least until a better fix comes out.

---

