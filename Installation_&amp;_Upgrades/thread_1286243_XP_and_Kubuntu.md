---
title: "XP and Kubuntu"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by themattbeballin on 2009-10-08
Hey,

Okay here's my situation..

I have two hard drives and then my terabyte (The terabyte is always disabled during my installs due to it carrying vital information.) The two HDD's are 160GB each. 

I have XP installed on my 160 Primary.
I found out I really liked Kubuntu to I was going to install that on my secondary..

I get through the Kubuntu install and I reboot, but it still boots to XP.

No GRUB boot loader whatsoever. 

What am I doing wrong?

---

### Post by mikewhatever on 2009-10-08
You might need to boot from the second hdd with Kubuntu. Check the boot order in the BIOS.

---

### Post by themattbeballin on 2009-10-08
I figured out my issue with a couple of links.. 

GRUB wasn't chosen on ANY of my drives. 

So I went and told GRUB where to go.

With the help of these links, I was able to figure it out:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)
[http://ubuntuforums.org/archive/index.php/t-210019.html](http://ubuntuforums.org/archive/index.php/t-210019.html)

---

