---
title: "won't boot unless plugged in"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by chiefofthejojos on 2005-12-14
I'm sure it's VERY unlikely that this issue has anything to do with ubuntu but I don't know where else to ask.
I just got this laptop two days ago (Asus A6U).  It came with no hard drive, memory, or cpu, so I installed that stuff and then I installed Breezy on it.  No problem.  I unplugged it while it was running and it detects the battery and keeps running.  So far everything is fine.
But, when I try to start the laptop when it is not plugged in it shows the first screen, where the IDE drives are detected and allows me to go into BIOS setup.  But, if I try to let it boot past that first screen, the lcd just goes blank -- it doesn't even print anything about loading grub.  The disk and the fan keep spinning, but it doesn't seem to be going anywhere.  I can't even boot to cd!  The boot order is:
External Devices
CDROM
Hard Drive
...

Has anyone seen anything like this before?
Any ideas for troubleshooting?
I need to find out if this is just a hardware problem because if it is, I'll be sending the hardware back.
I really appreciate any help anyone can give me.
Thanks,
Brad

---

### Post by jml on 2005-12-14
To find out if it is a hardware issue or an Ubuntu issue, you might want to try booting with a live cd from a different distro, like knoppix.  If that runs on battery, then its likely that it is a configuration issue within Ubuntu.  If your computer boots when it is plugged in you might want to boot with ACPI disabled.  This application is not supported by a lot of older laptops and seems to cause a variety of problems.  By the way, how does one get a laptop without CPU, Hard drive or memory?

Joe

---

### Post by chiefofthejojos on 2005-12-15
after looking around at the asus website, it seems that the problem is that 62 watt cpus are not supported.  It works find after boot, but it won't boot without being plugged in.  I've issued a request that they update the BIOS.
Thanks for your suggestions, jml.
I got my laptop from TheNerds.net.  Asus makes a lot of barebone notebooks.  Most sites that you buy them from will force you to configure with at least a cpu and ram, but there are some that allow you to purchase them completely bare.  I chose the A6U because of the built in webcam and because it supports amd64.

---

### Post by jml on 2005-12-15
Thanks for the info.

---

