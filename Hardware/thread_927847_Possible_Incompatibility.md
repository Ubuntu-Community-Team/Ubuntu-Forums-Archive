---
title: "Possible Incompatibility?"
date: 2008-09-23
forum: Hardware
---

### Post by acidboot3r on 2008-09-23
It has got quite annoying lately and I'm not sure I can take it anymore. I think that debian based distributions such as Ubuntu just isn't 100% compatible with my Dell PC. If I try a different distribution such as OpenSuse, it works fine, but how come Ubuntu is different?

Even using the LiveCD is a pain. Most of the time it doesn't boot up correctly. It will just lead me to the busybox command line screen. When the livecd does boot up correctly and I've installed Ubuntu, it still won't boot up normally. I have to boot up in a really specific way to make it work properly.

To explain my problem in detail:

1. Every time I try to boot up from Ubuntu, it goes to the loading screen with the bar, but nothing happens. It just keeps loading. This also happens if I try to use the LiveCD.

2. I have to boot up in a specific way to use Ubuntu. 

People have said that I should change my BIOS settings from IDE to RAID. I did that and that solved the Ubuntu problem. But now it wouldn't allow me to boot up into Vista. So how can I resolve this booting up problem?

PC Specifications:

Dell Inspiron 530
ATI HD RADEON 2400 Graphics Card.
Intel Duo Core Processor.

---

### Post by ModelM on 2008-09-23
Try adding

```
all_generic_ide
```

to the boot options at boot time.

---

### Post by acidboot3r on 2008-09-24
Are you 100% sure that adding that will not make my main operating system (Vista) unbootable?

---

### Post by ModelM on 2008-09-24
The short answer to your question is, no.

It's difficult to imagine, though, how a change to the Grub Linux boot options would have any effect on Windows. I'd be surprised to learn that Windows reads the Linux boot options when it boots. A change to the BIOS SATA setting, however, would be seen by Windows (and any other operating system) and might have unintended consequences.

I have an Inspiron 530 with an e7200 processor. I got the same error when trying to boot Ubuntu from the CD. That addition to the boot options & no changes in the BIOS allowed the machine to boot from the disk.

In my research of this error I also found the BIOS change. I didn't want to use that method, continued searching & found this which seemed to work for folks with no BIOS changes.

After install, I saw that that boot option is a permanent part of the boot options in /boot/grub/menu.lst.

I don't know anything about how Windows boots on this machine. I haven't used a Microsoft operating system for many years & this machine has never had Windows on it. It was purchased with Ubuntu Linux installed. Had I looked I probably would have found all_generic_ide as part of the boot options in the factory install. I simply didn't look for it because I had never experienced or heard of this boot problem.

I was merely trying to give you an alternative to changing the SATA/RAID setting in the BIOS. Feel free to ignore my advice - I've been married so I'm used to it.

---

