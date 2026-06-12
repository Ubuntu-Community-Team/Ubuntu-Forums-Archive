---
title: "Ubuntu 10.10 laptop shutdown powerdown issues"
date: 2011-03-12
forum: Hardware
---

### Post by lch503 on 2011-03-12
Hello
I have a zoostorm laptop (a rebranded mitac 8207D) with the latest BIOS. The problem I have is that the laptop will not powerdown when I shutdown. The hard disk spins down, the network turns off (at least the light does (see later)) but the fans, the screen and the power LED remains on.
I have tried adding the following in GRUB but these have not helped:
acpi=force --no change
acpi=off --have to use recovery as ubuntu will not start. Have to recompile GRUB
acpi=off noapic --Ubuntu does not startup the first time, however after this it does. The shutdown procedure dowever does not change, it still does not powerdown.

Trouble is I dont really know what these are doing, I only have a basic knowledge in ubuntu. Any explanations of these would be fantastic, as well as fix!
In short, I have tried all from the following forum thread:

[http://ubuntuforums.org/showthread.php?t=623237](http://ubuntuforums.org/showthread.php?t=623237)

including changing the /etc/module files.

I tried jerrylamos post on page 6 of this forum and the network adapter had a [fail] when shutting down the laptop, hence I dont know if this has anything to do with the error.

I have since changed everything back to the stock files and recompiled GRUB.
Any help with this would be great!
Thanks.

---

### Post by lch503 on 2011-03-14
It sometimes does shutdown properly, but it seems random.
Any suggestions?

---

