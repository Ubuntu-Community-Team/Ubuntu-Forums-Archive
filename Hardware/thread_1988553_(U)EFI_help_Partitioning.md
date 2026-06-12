---
title: "(U)EFI help: Partitioning"
date: 2012-05-27
forum: Hardware
---

### Post by Axxon95 on 2012-05-27
Hey, I've been trying one thing after another to get Ubuntu 12.04 x86_64 to run correctly on my computer, I have had a good amount success but I'm still having some issues.

I've gotten it installed( *by plugging my external video card into my main monitor, and the on-board video card into another monitor, and actually getting video, but through the on-board video instead... *), and when I tried to install NVIDIA Drivers from the Ubuntu-X PPA( *always worked perfectly for me before, and on this same computer in Ubuntu 10.04, which runs perfectly* ) and its not registering my external video card at all(* which I think is a (U)EFI issue *).
(*this post isn't about the video card drivers* *just the video cards in general *)
I'm starting to think a little that is the (U)EFI messing me up here. And I don't think I can turn off my on-board video completely...

The question: **How should I set up my HDD partition table to get Ubuntu compatible with my MB/Hardware?**
I have read that (U)EFI has to do with your hardware talking to the MB and/or the OS itself, still new to it... and not liking it. Also attempting to boot Ubuntu in (U)EFI mode doesn't work at all.
I only have 1 PS/2 port on my MB so I can't do Legacy Bios, which doesn't support USB for some reason.
System Info:
Asus P8H61-m LE/CSM (U)EFI Asus EZ BIOS
Intel HD Graphics(on-board)
EVGA GTX 460(External)
Testing on a 40GB HDD I had laying around.

BTW: I'm not trying to get dual-graphics to work.

---

### Post by wilee-nilee on 2012-05-27
Couple of links for you to look at, two courtesy of a mod.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

[http://ubuntuforums.org/showpost.php?p=11509699&postcount=2](http://ubuntuforums.org/showpost.php?p=11509699&postcount=2)

[http://ubuntuforums.org/showthread.php?t=1987011](http://ubuntuforums.org/showthread.php?t=1987011)

---

### Post by Axxon95 on 2012-05-27
I finally have it installed, I had to almost constantly switch back in forth from iGPU to Auto(which brings me to my External video adapter).

Still (U)EFI mode still doesn't boot, but at least I have Ubuntu 12.04 x86_64 working on my computer.

---

