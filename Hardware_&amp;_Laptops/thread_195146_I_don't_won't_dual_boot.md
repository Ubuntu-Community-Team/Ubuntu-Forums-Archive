---
title: "I don't won't dual boot"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by chris9902 on 2006-06-12
Hi,

I have 2 hard drives, one has Windows on it and the other will have Ubuntu. Now the problem is my family uses this computer so I don't want the grub boot loader or anything else to show up when loading the computer.

What I want is Windows to load unless I load my bios boot menu and choose my other hard drive.

The problem is I installed Ubuntu linux and used Windows to do the "fixmbr" thing to get the windows boot loader back. Now when I try to load my other hdd it just says "Operating system failed to load" and I think it's to do with the fact grub does not load so I can't choose how to start it and hence it fails.

So, how do I install 2 operating system on 2 hard drives without one affecting the other?

Would it work if I removed the Windows hdd when installing linux, so it thinks that's the only thing?

thanks for any help or ideas you can provide.

---

### Post by xfile087 on 2006-06-12
Probably not the best solution.... Unplug the harddrive with winxp on. Install ubuntu. Plug in the windows hard drive. XP should boot unless you change the bios to boot from another drive? I think that would work

---

### Post by Patrick-Ruff on 2006-06-12
quite simple really, why not keep the grub boot loader? does your family hate linux? windows will still load the same, you can make grub load Windows by default. so there isant an issue, it will load the OS just fine.

---

### Post by chris9902 on 2006-06-12
[QUOTE=Patrick-Ruff]quite simple really, why not keep the grub boot loader? does your family hate linux? windows will still load the same, you can make grub load Windows by default. so there isant an issue, it will load the OS just fine.[/QUOTE]

i'm new here so I don't won't to be a jerk but that's not what I asked for. I know I can do that but I don't WON'T to do that.

thanks xfile087, i'll go try.

---

### Post by aysiu on 2006-06-12
Can't you just have Grub load up and have the timeout be 1 second and Windows be the default option?

---

### Post by ajmoncrief on 2006-06-12
The easiest way will probably go against one _small_ thing that you said you wanted...which is to go ahead and install ubuntu on your second drive while leaving the windows hard drive intact.  Once its all done you can then change your grub load options so that windows will be the default os, and ubuntu will only load if manually selected.  You can also change the grub option load time to something like 2-3 seconds if you want it to be done relatively fast.  (Im not sure, but I think the default time is something like 15 or 30 seconds), and I know for sure it selects ubuntu as the default os to load immediately post-install. (NOTE: if you still have this configuration on the drives, you shouldnt need to do a reinstall...it is pretty easy to reestablish the mbr and grub)

Another option is unplug the windows hard drive when you do install linux, and then plug them both back in after the ubuntu install.  Set your windows hd to primary master and the ubuntu as primary slave, then you will have to go through your bios settings to select ~ "boot primary master first" if you want windows to be the default and then every time you want to boot to ubuntu you would have to select "boot primary slave".  Will be very annoying after awhile!

I would highly recommend the first option though as I had to do this for awhile b/c my wife was stuck on windows and did want to have to do anything different to get to 'her stuff'.   It worked fine for me, but I no longer have this problem as I only use one os now.

---

### Post by aysiu on 2006-06-12
[QUOTE=chris9902]i'm new here so I don't won't to be a jerk but that's not what I asked for. I know I can do that but I don't WON'T to do that.

thanks xfile087, i'll go try.[/QUOTE] People are just trying to help. Sometimes people think they need some convoluted solution when a simpler one will solve the problem.

Can you at least explain why you don't want the Grub boot loader to load, even for one second?

P.S. You can change the Grub splashimage to look Windows-like. You don't have to go with the default white text on boring black screen.

---

### Post by HeavyAl on 2006-06-12
So, if I'm understanding correctly you dont want grub to handle the boot process? If this is the case then yeah, the only thing you can do is unplug the xp drive, install ubuntu to the drive thats left and the replug the xp drive and switch in the bios. A rather inelegant solution imo. Why not just modify grub to automatically boot xp instead? The file you want to look at is /boot/grub/menu.lst. Just make xp the default option and no one but you will know the difference.

---

### Post by ajmoncrief on 2006-06-12
Someone beat me to it :-)

---

### Post by aysiu on 2006-06-12
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

I think if you explain what you or your family has against Grub, people will stop suggesting you take the easy route instead of resorting to physically plugging and unplugging drives.

---

