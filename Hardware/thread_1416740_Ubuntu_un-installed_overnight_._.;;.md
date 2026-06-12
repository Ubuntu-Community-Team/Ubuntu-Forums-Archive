---
title: "Ubuntu un-installed overnight? ._.;;"
date: 2010-02-26
forum: Hardware
---

### Post by ShadowsOfSilver on 2010-02-26
I don't know what happened...

Last night I installed Ubuntu 9.10, from my home-made installation DVD. I had made it Un-install Windows XP, because I got the BSOD. I shut it off last night, after playing with the RT2870 Linksys WUSB600N driver for Linux, followed instructions, but didn't finish. I turned it off, the turned it back on this morning. It said "No Operating System found. Re-boot and try again?" So I did that. 5 times. I threw in the installation DVD again, and it showed the install options. I didn't know what was going on, so I used Live CD, hoping it would pick up my files. Nope. It just went to the default. I tried installing it, but at Step 4, a partition thing comes up. Why? I don't know, there's no other Operating Systems on there. Another strange this is that I can't select anything, it's grayed out.



Any Help?


:-k

---

### Post by wilee-nilee on 2010-02-26
With the live CD look in home at the side panel and see if the installed version shows a partition or open gparted to see whats there.

---

### Post by ShadowsOfSilver on 2010-02-26
Thank you so much. What do I do? I found 3 Partitions. Should I delete them and then re-install Ubuntu?

---

### Post by wilee-nilee on 2010-02-26
> **ShadowsOfSilver said:**
> Thank you so much. What do I do? I found 3 Partitions. Should I delete them and then re-install Ubuntu?

You could delete all and reinstall, that is probably a fast method, but you may be able to easily fix what you have. From the live cd terminal post
sudo fdisk -l

So since your using 9.10 you have the grub2 boot loader here is a link you may need in the future.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by ShadowsOfSilver on 2010-02-26
Thanks a ton! I used the "sudo fdisk -|" code and the grub code, and I got back in! Thanks again!

---

