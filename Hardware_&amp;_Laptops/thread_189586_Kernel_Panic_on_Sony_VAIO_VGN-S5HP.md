---
title: "Kernel Panic on Sony VAIO VGN-S5HP"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by txusinho on 2006-06-05
Hi all,

I've a problem installing Ubuntu (and any other GNU/Linux distro) and I think It's related to the sata disk. I've googled for 1 week and I've done at least 10 or 12 installations of any flavour of GNU/Linux, and I know I'm not the only one that has the same problem.

(*) Installing breezy I had an "ata1... blah blah" error: Which I've seen documented. I've donde the solution provided (like passing the argument "nodma" to the grub, but force is not with me.
(*) If I try to install Dapper, the graphical installer freezes at 15%.
(*) If I try to install Dapper server, it seems to install but rebooting freezes "Booting the kernel...."
(*) If I try to install Dapper alternate (downloaded today), I've been able to boot once, but now I have a:  "kernel panic - not syncing : Fatal error in interrupt"
(*) I've even try to install a Fedora Core 5, but I was unlucky, too

Could anyone help me?

Thanks in advance

---

### Post by kemeris on 2006-06-07
I'm having same kind of problems with Dapper and VGN-S5HP/B. At the moment it seems I can only confirm your findings:

-When using the normal/live-cd, the graphical install freezes at about 15% and only hard reset will do.

-With the alternate cd, the install goes all the way through without any (visible) problems, but after reboot the startup ends with hdd activity led lighting up for an relatively long perioid and then "Kernel panic - not syncing..." message. Also boot with recovery mode ends up with the same error. 

This most definitely is a software issue, since both install cds and laptop itself are tested to be ok. I've also searched for possible solutions since I discovered that neither Breezy or Dapper Flight 4 would install on this system and hoped that the final Dapper release version would be more Vaio-friendly, but no such luck. Any help or good guesses from anyone would be appreciated since I really would like to upgrade from Hoary to Dapper :???:.

---

### Post by Patsoe on 2006-06-08
I think this would best go into a bug report, not sure in which section though. You can report the bug at [https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/)

---

### Post by Zathrus on 2006-06-08
Hi guys, I've got a VGN-S58GP Vaio, so very similar to yours, I'll post pretty much what I did in my last post.

I've also been having lost of problems installing linux on this laptop and from what I can tell it has a lot to do with the sata drives in these things, I have also had problems when the pcmcia tries to start up. The distros I've tried are Ubuntu, Red Hat, Suse 10, Knopix, Mandriva and Debian.

First let me preface everything I'm about to say with "I'm a total amateur" these are just things I've noticed and found to work or not for the most case.

I've narrowed down my problems to two things, firstly I sometimes have problems when pcmcia is being loaded, this was a problem for Debian and Knopix at least, seemed to work with SUSE 10 though. Secondly the SATA drive in these laptops seem to be different maybe a different chipset I dont know but I've had problems with it when trying SUSE 10, Debian and Ubuntu, Mandriva and Fedora. I did a bit of googling and found that pre kernel 2.6.8 SATA support is poor or non-existent and post linux kernel 2.6.12 SATA support takes a bit of a nose dive. This version of ubuntu is using linux kerenel 2.6.15 which I've been reading some people have had problems with this and their SATA drives. I was hoping to install this version of Ubuntu if the SATA support had been fixed but it seems it's not from what you've said.

The one linux distribution I did have success with (I'm running it right now with no problems) is an old version of Debian testing net install using kernel 2.6.12-1-386. This works fine with my HDD but using a newer version of Debian net install (2.6.15 i think) says it cant find my HDD when it comes time to setup my partitions. One little caveat being I had to disable pcmcia from being loaded before I could boot properly. Now I'm stilling mucking around with this installation, can kind of get power management going and cant get wireless running but I'm not an expert so you may have better luck but at least it is a running version of linux. I did find one guy that claims to have a working install boot CD for debain running 2.6.15 with some hacks to get the HDD working but I couldn't find out what he did.

I dont know if this helps you at all but hopefully it might shed a bit of light on what's going wrong.

---

### Post by txusinho on 2006-06-09
[QUOTE=kemeris]
 anyone would be appreciated since I really would like to upgrade from Hoary to Dapper :???:.[/QUOTE]

Does this mean that Hoary works in this laptop? Because I've probed Gentoo, Fedora, Dapper, Breezy, Sarge, Etch. I'd like just install any Linux on my laptop.

Upgrades can wait...:) 

Regards

Txus

---

### Post by kemeris on 2006-06-12
[QUOTE=txusinho]Does this mean that Hoary works in this laptop? Because I've probed Gentoo, Fedora, Dapper, Breezy, Sarge, Etch. I'd like just install any Linux on my laptop.

Upgrades can wait...:) 

Regards

Txus[/QUOTE]
Yes, it installed and worked fine for me. That said, I didn't test it very thoroughfully, so I'm not 100% sure for example PCMCIA support and such since I dont have any PCMCIA devices. But surely, "for any linux", it will be fine. ;)

---

### Post by txusinho on 2006-06-14
Hi kemeris,

Thank you for the advice. Hoary worked fine for me too. I disabled the framebuffer at the install and the pcmia too.

I think the problem is with the new version of lvm2 or udev (i'm not sure). I think this, because when upgraded, i came back to the old kernel (because the new one crashed) and it failed too. And not the kernel nor the modules changed, so the problem must be in the access to these places.

Anyway, I'm not an expert and maybe I'm wrong. I'm not a Linux expert, just an user. 

Does anyone now how notify this to the ubuntu or Linux Kernel developers?

---

### Post by Patsoe on 2006-06-14
[QUOTE=txusinho]Does anyone now how notify this to the ubuntu or Linux Kernel developers?[/QUOTE]

See my post above; [https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/) - and also, I found that you can report a bug and say that you don't know in which package it is. I suppose that's useful here.

---

### Post by txusinho on 2006-06-16
Ok, I can tell you that it's not a problem with the kernel. I've compiled the newest vanilla kernel (the one from kernel.org), exactly this one [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.20.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.20.tar.bz2) and I've had no problem.

So as far as I can tell you is that the problem is not in the kernel but with any of the programs that works with the modules of the kernel. I say this because after compiling the kernel and rebooting the system, I've had no problem. After that I've done an apt-get clean and I've added the sources of debian sarge. When I've updated and rebooted the problems have arrived again. In this case, the e1000 module (the one for the LAN interface) didn't load properly.

I'll post the bug when I'll be able to have the error clearer.

---

### Post by effemme8 on 2006-12-22
I have Sony Vaio VGN-s5HP

....isn't possible to upgrade from  BREEZY ( but always to use 2.6.10.6 kernel )

---

### Post by kernst on 2008-02-29
There is a slight chance (if you have the same problem I did) that you *may* be able to short-circuit the problem at the 15% mark by looking for a process called '[FONT="monospace"]01unmount_busy[/FONT]' (using 'top' at the command line or *System -> Administration -> System Monitor*) and killing it. Please note that you will have to be root to kill this process (either using 'sudo' at the command line, or 'gksudo' to run the graphical "System Monitor" program [*Alt + F2 -> gksudo gnome-system-monitor -> ENTER*]).

The purpose of [FONT="monospace"]01unmount_busy[/FONT] seems to be to wait for busy filesystems to become free before continuing with the installer, so **please make sure that any mounted filesystems are *definitely* safely unmounted before performing the above action.**

If you see a process in 'top' or "System Monitor" called "01unmount_busy" that seems to be taking more than its fair share of CPU while the installer is stuck at 15%, you can follow the step-by-step I posted at [http://ubuntuforums.org/showthread.php?p=4429985]("http://ubuntuforums.org/showthread.php?p=4429985#post4429985"), which may allow you to progress past that point.

There are several launchpad bugs ([113237]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/113237"),  [112828]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/112828"), and [67723]("https://launchpad.net/ubuntu/+bug/67723"), for instance) tracking this issue, and I've tried to add as much detail to them as I could, so maybe this one will be fixed in the next release.

---

