---
title: "Very poor overall performance on Pavilion 15 d006ed"
date: 2014-05-14
forum: Hardware
---

### Post by Simon_Woolf on 2014-05-14
I'm really struggling with Ubuntu 14.04 on a brand new HP Pavilion 15 d006ed. Install from USB (in EFI mode) was straightforward, although Grub didn't manage to take control of the boot process. I removed the windows folders from the EFI partition, so that grub is the only boot option.

This should fly, with an i5 processor and 4GB RAM, but it's crawling. The most basic operations in Thunderbird (replying to an email, opening a calendar event) take up to 10 seconds to complete, and wifi performance is miserable. OK, the disk drive is slow (750GB 5400RPM) but I can't believe that is causing all the problems.

The wireless card (Realtek RTL8188EE) is known to be problematic and I've tried all recommended fixes (upgraded the kernel to 3.14.1, swapped out the driver for the opensource one, disabled IPv6, disabled 8011.2n mode, etc etc). Nothing has managed to get the speed above a barely usable crawl.

This machine is for a non-techie member of staff in our organisation and they are about ready to kill me. I've even offered to let them boot into windows 8. It's that bad!

Can anyone help? I've installed Ubuntu on 4-5 different machines over the past 3 years, have never seen it bomb so badly in terms of performance. Kind of embarrassing as I'm trying to persuade my entire organisation to change platform.

---

### Post by olliemonster on 2014-05-14
Hi Simon
Have you installed the intel graphics card drivers because unity will be slow if you are using mesa also have you tried any of the remixes because if lubuntu is slow it is probally a problem with ubuntu and your hardware rather than something you ahven't done.

---

### Post by mastablasta on 2014-05-15
to change to linux platform it is good to have compatible hardware first. there are many HP laptops that come linux preloaded. or that are certified for ubuntu.

what are your system specs? Are proprietary graphics drivers installed?

---

### Post by Yellow Pasque on 2014-05-15
Before you folks mention graphics drivers, you should do a quick google on the model number. This system probably has Intel HD4000 graphics, which should have the correct open-source drivers working "out of the box" on modern distros. If user attempts to install some kind of different or updated graphics driver on this system, the chances of a borked system are far greater than any improvement.

@Simon: please post output of:
```
lspci -k
glxinfo
```

---

### Post by Simon_Woolf on 2014-05-20
It does indeed have the HD4000 graphics card, and I didn't need to install anything proprietary. Also, no additional drivers are available in the software and updates tab.
I know from reading that the Realtek RTL8188EE wireless card is problematic, but others seemed to be able to resolve the issue by updating the kernel and making other tweaks. I've done everything but I'm still left with an extremely unstable card (it drops the connection frequently) and performance that seems throttled by 50% or more.

I don't have access to the machine for the next few days, but I will post the output next week.

---

