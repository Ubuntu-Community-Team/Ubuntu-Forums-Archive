---
title: "Uninstall WindowsXP"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by rktompsett on 2009-08-11
I am ready to dump Windows, I'm running Ubuntu 8.04 on a separate internal drive, dual booted through GRUB. How do I uninstall WindowsXP without screwing up my Ubuntu installation?

---

### Post by merlinus on 2009-08-11
You can format the xp partition, and then remove its entry from /boot/grub/menu.lst.

You also should look at hdd boot order in bios to see which is first.

It will be easy to restore grub should the mbr be formatted as well.

Boot from live cd, open a terminal and enter these commands one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use hd and numbers from the previous command
setup (hd0)  #use hd and its number from the previous command
quit 

```Remove the cd and restart.

---

### Post by rktompsett on 2009-08-11
Thankyou for the reply.

---

