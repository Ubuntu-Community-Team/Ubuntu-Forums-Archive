---
title: "Thinkpad UltraBay hotswap not working"
date: 2008-11-01
forum: Hardware
---

### Post by trism on 2008-11-01
Hello,

I just installed Ubuntu 8.10 the other day on a new Lenovo Thinkpad W500. I've been pleasantly surprised at how well everything worked right off the bat, except for one thing: the UltraBay. It just doesn't want to work.

I've tried following the [ThinkWiki HowTo (http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices)]("http://www.thinkwiki.org/wiki/How_to_hotswap_UltraBay_devices"), but it didn't work. I've spent more than a whole day messing around with different permutations of those scripts. The best I can do is to use the following commands to undock and dock the hard-drive adapter manually, but they don't power down the drive bay, so I'm fairly apprehensive about it.

To undock:
```
echo 1 | sudo tee /sys/class/scsi_device/1:0:0:0/device/delete
echo eject | sudo tee /proc/acpi/ibm/bay
```

To redock:
```
echo 0 0 0 | sudo tee /sys/class/scsi_host/host1/scan
```

What I would like to be able to do is flip the switch on the UltraBay and have whatever is in the bay be unmounted and powered down automatically, which is what those ThinkWiki scripts suggest they do. I have a hard-drive bay adapter, a DVD drive and a battery. Ideally all three would work without issue.

Has anyone else been able to do this and can they help me out with it?

Keep in mind, though, that I'm brand new to Ubuntu and relatively new to Linux (I used Fedora 7 & 8 for about 4 months at my last job), so try to be specific in any instructions. (For example, the ThinkWiki page says to "check if CONFIG_xxxx is enabled in my kernel" a few times, but I'm not exactly sure what that means and have no idea how to do it.)

Any help would be greatly appreciated. This is the last thing keeping me from using Ubuntu as my primary OS.

Thank you!

---

### Post by Franko30 on 2008-11-09
Hi,

this thread

[http://ubuntuforums.org/showthread.php?t=37774&highlight=multibay](http://ubuntuforums.org/showthread.php?t=37774&highlight=multibay)

recommends installing "hotswap".

EDIT: Sorry, this is totally outdated as we use SATA now...

I was searching for multibay, because taking out the DVD/battery out of the mutlibay on my Thinkpad R61 completely freezes the system. But this "howswap" seems to be needed only for IDE stuff, not batteries...

Cheers

Franko30

---

