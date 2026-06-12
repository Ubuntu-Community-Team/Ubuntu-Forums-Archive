---
title: "Safest way to switch and remove kernel?"
date: 2008-11-04
forum: General Help
---

### Post by shaggy999 on 2008-11-04
I ran into an interesting error that would have left my system bootless if I wasn't paying attention.

Step 1: Install Ubuntu 8.04.1 Server
Step 2: Update Apt cache
Step 3: apt-get install linux-generic
Step 4: apt-get --purge remove linux-server
Step 5: apt-get dist-upgrade

When I ran step 5 I noticed it wanted to update my linux-<version>-server kernel, which was odd. I figured by removing the linux-server package it would have removed that. I let the update continue and then:

Step 6: dpkg --get-selections | grep linux
Step 7: apt-get --purge remove <anything having to do with a server kernel>

During this process some messages complained about /initrd.img and /vmlinuz not pointing to anything valid and it removed them. Eventhough I had the linux-generic kernel installed! The solution was easy, I just had to make symlinks to the appropriate files in /boot, but had I not been paying attention or some newbie tried this they would have ended up with an unbootable system. I should note that I never rebooted once during this process. I was still running the linux-server kernel included on the 8.04.1 disc during this whole process, eventhough I was removing it. Perhaps that led to part of the problem.

Anyway, is there a safer way to do this?

---

