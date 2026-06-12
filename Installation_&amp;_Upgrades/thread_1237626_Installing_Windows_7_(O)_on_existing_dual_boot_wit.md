---
title: "Installing Windows 7 (:O) on existing dual boot with Ubuntu using Grub"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by JohnCaver on 2009-08-11
Hi,

I currently have a dual boot set up, using GRUB, which allows me to boot to Win XP or Ubuntu.
I will probably want to upgrade my Win XP to Windows 7 fairly soon - how do I do this with my existing dual boot setup? Is it possible without having to reinstall Ubuntu?

Thanks

---

### Post by merlinus on 2009-08-11
You can install 7 into the partition where xp is currently, and then restore grub easily:

Boot from live cd, open a terminal and enter these commands one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use hd and numbers from the previous command
setup (hd0)  #use hd and its number from the previous command
quit 
```

Remove the cd and restart.

---

