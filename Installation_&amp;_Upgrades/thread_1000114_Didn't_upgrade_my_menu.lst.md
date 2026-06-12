---
title: "Didn't upgrade my menu.lst"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by detrate on 2008-12-02
When I upgraded 8.04 to 8.10 I made the mistake of saying "no" to replacing my menu.lst file for grub.  Now I fail to boot properly into x and the only solution I have is the following commands:
```
sudo rmmod nvidia
sudo modprobe nvidia
startx
```

just to get into a "working" environment.

[This blog post](http://sonicfrog.net/?p=942) exhibits a similar issue but I don't know what my UUID would be and I can't go stabbing in the dark.

Which package do I need to reinstall to get that menu.lst generated again and/or how can I fix my major oopsie?

---

### Post by cariboo on 2008-12-02
You couid probably reconfigure /boot/grub/menu.lst by running:

```
dpkg-reconfigure linux-image-2.6.xx-x-generic 
```

Where 2.6.xx-x = the kernel version you want to set up. If you're not sure which kernel it was, you can always look in /var/cache/apt/archives to see which kernel was downloaded. In a termeinal cd to /var/cache/apt/archives then type:

```
ls -l linux-image*
```

This will list all the kernel files, choose the newest one to configure.

Jim

---

### Post by detrate on 2008-12-02
Still failing :-\

```

kinit: name_to_dev_t(/dev/disk/by-uuid/08...) = sda6(8,6)
kinit: trying to resume from /dev/disk/by-uuid/08...
kinit: No resume image, doing normal boot.

```

Then I'm stuck in the terminal unless I do the above 3 commands.

If I just do "startx" it tells me it failed to initialize the nvidia kernel module.

---

### Post by detrate on 2008-12-02
So to fix this (part) of my problem, I backed up my menu.lst, then deleted it and generated a new one:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo rm /boot/grub/menu.lst
sudo update-grub

```

Then I installed start up manager and ran it to configure/verify my menu.lst with a GUI:
```

sudo aptitude install startupmanager
gksu startupmanager

```

Then I rebooted
```
sudo reboot
```

--- Up to this should fix this in most cases ---

My kernel was looking for a different driver still, 177.80 vs. 177.82 so I did a little search on my laptop and pulled the drivers to my desktop (this machine).

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run
sh NVIDIA-Linux-x86-177.80-pkg1.run
```

rebooted again and yay :D, first GUI login I've seen in a little over a week :)

This machine is in for a fresh install in the near future.  I'm just happy I've got it back to somewhat stable.  In the future, I'll try to be less impulsive :).  OMG NEW THINGS!

---

