---
title: "[SOLVED] Ok, need some help..."
date: 2008-09-27
forum: General Help
---

### Post by finalrequiem on 2008-09-27
I have been having trouble with my wireless and wired internet connection just disappearing after a reboot.  I just happened to hit "esc" and go into the grub menu just a second ago and found that I had like 20 different options for some reason (-generic, like 5 different ones not including the recovery modes, -virtual,-openvz,-server,-rt).  I picked a random -generic and my wireless was working again...  Where did these come from and what are they?  How do I get rid of them...

apparently kernel 2.6.24-19-386 is what was loading automatically and wasn't allowing my network devices to work... just a guess...

---

### Post by SBJ95 on 2008-09-27
There are two ways you can remove them.  The easy way is to open up a command line, and type 'sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bac' and then 'sudo gedit /boot/grub/menu.lst'.  Scroll down until you find the kernel entries.  One might look something like this:

```
title Ubuntu 8.04.1, kernel 2.6.24-19-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-386 root=/dev/sda3 ro quiet
initrd /boot/initrd.img-2.6.24-19-386
quiet
savedefault
boot
```

Then you go through and comment the lines you do not want out.  To do that, you put a # in front of them, so it will look like this:

```
# title Ubuntu 8.04.1, kernel 2.6.24-19-386
# root (hd0,0)
# kernel /boot/vmlinuz-2.6.24-19-386 root=/dev/sda3 ro quiet
# initrd /boot/initrd.img-2.6.24-19-386
# quiet
# savedefault
# boot
```

Save and exit.

**MAKE SURE YOU LEAVE AT LEAST ONE KERNEL AND ONE RECOVERY KERNEL!**

The other way, which actually isn't that hard, has you uninstalling the kernels.  You can do this either through Synaptic or the command line.  If you're using Synaptic, you find the packages that contain the extra kernels, and you remove them, again making sure you leave at least one kernel.

If you prefer to use the command line, the command would probably be 'sudo apt-get purge linux-2.6.24-19-386 linux-2.6.24-19-server' and so on.  (The naming might be different, you can look for them using 'apt-cache search server | grep 1.6.24' or something like that.)

The first way may not be permanent if upgrades come, but is a great way to see if everything works with them 'removed'.  The second way will remove them unless you have a package that depends on them.

Hope this helps!

---

### Post by finalrequiem on 2008-09-27
Thanks!  Come to find out, I've been running the 32 bit version on my 64 bit system so I just wiped everything and started over with the 64 bit version but now I'll know what to do. Thanks again!

---

