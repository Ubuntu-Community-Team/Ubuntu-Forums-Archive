---
title: "[SOLVED] Upgrading initramfs-tools trashed my system"
date: 2008-08-08
forum: General Help
---

### Post by kung fu buntu on 2008-08-08
I (stupidly) decided to upgrade initramfs-tools from 0.89 to 0.92e. The output was:
> Setting up initramfs-tools (0.92e) ...
Installing new version of config file /etc/initramfs-tools/update-initramfs.conf ...
update-initramfs: Generating /boot/initrd.img-2.6.26-1-amd64
Warning: LBA32 addressing assumed
Warning: /dev/sda1 is not on the first disk
Added Linux *
Added LinuxOLD
2 warnings were issued.


I reboot the system and surprise: grub was overwritten by lilo! I try to boot anyway... and another surprise:
```
ramdisk: couldn't find valid ram disk image starting at 0
list of all partitions:
no filesystem could mount root, tried:
kernel panic - not syncing: VFS: unable to mount root fs in unknown-block (8,1)
```
I was already sweating and wondering what to do with my life... no computer... no way to find how to fix this.
Fortunately there was LinuxOLD (my old 2.6.21), which I was able to boot to it.
However, kdm failed to start because I had no nvidia.ko (for my old kernel), so I had to edit xorg.conf.
I startx and end up in gnome...arhhh... what a nightmare.


1) how do I fix my current kernel/initrd images?

2) how do I get grub back?

3) how do I avoid future initramfs mess ups with lilo?

4) why the heck is gnome default? how do I set kde to default in startx?


Thankk you very much for any help.
(linux drives me crazy...)

PS: I don't want to mess my system even more... if I don't boot... I'm dead... no other computer with net to cry for help

---

### Post by phidia on 2008-08-08
Why is gnome default? Because you installed Ubuntu rather than kubuntu.

Try this "sudo dpkg-reconfigure gdm" and set kdm as default.

To get grub back "sudo grub-install (hdX) *usually X=0 but I don't know your set up.

I don't know how to fix your kernel or initramfs issues how did you do the upgrade?
Did you change your sources.list? You actually can go back to a previous version with debian based systems but it's not a sure fix nor necessarily recommended.

There's a page [here]("http://oldsite.debianhelp.org/Article3059.html") that discusses how to replace an upgraded package with a previous one.

---

### Post by mdsharp24 on 2008-08-08
"Upgrading initramfs-tools trashed my system"  This is just the thing *buntu doesn't need. I SERIOUSLY doubt upgrading initramfs-tools TRULY trashed your system.

This kind of posting turns others away. Try "Upgrading initramfs-tools didn't go well"

---

### Post by kung fu buntu on 2008-08-09
I have debian installed.

After I edited xorg.conf and rebooted it started kdm. It only goes to gnome if I'm in the console and type startx.
So it's a startx thing... would "sudo dpkg-reconfigure gdm" be the way to go?

I see a initrd image backup on /boot: initrd.img-2.6.26-1-amd64.bak
I will try renaming it, but this will leave the system uncoherent since it will be the product of a different initramfs-tools.
I can then try generating a new initrd file... but what is the correct command for that? I don't want another corrupt image.

---

### Post by kung fu buntu on 2008-08-09
I was able to fix my system with the help of Martin Michlmayr. 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=494422](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=494422) 

I updated lilo to 1:22.8-6. Then added the line "large-memory" in /etc/lilo.conf 
I was able to reboot the system using the new kernel :D

Then I installed grub on the first partition of my drive (some people will want it on the MBR isntead) 
grub-install /dev/sda1 

After another reboot I removed lilo. 

After all of this I'm unsure if I should upgrade grub or not :s 


Anyway, the bug is in lilo, not in initramfs-tools

---

### Post by phidia on 2008-08-09
> **kung fu buntu said:**
> I have debian installed.

Ok there was no way for anyone here to know that.

When asking questions about an operating system that's not specifically Ubuntu or variants it's preferred to use the [Other OS forum]("http://ubuntuforums.org/forumdisplay.php?f=147").

---

