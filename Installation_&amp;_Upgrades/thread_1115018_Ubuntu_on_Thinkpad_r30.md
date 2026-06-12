---
title: "Ubuntu on Thinkpad r30"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by kahootbot on 2009-04-03
Hello :)

I've installed Ubuntu through Wubi on my main PC, so I'm not completely a new user. I'd like to get it installed on my Thinkpad R30.

I downloaded the Latest Ubuntu 8.10 ISO, burned it, and went through the "install ubuntu" on the CD with my laptop. As it's loading, I noticed I/O errors, I managed to type one of them before it went off-screen
> 
aufs au_xino_do_write:242gdm[6693]: I/O Error, write failed

Anyway, after it finishes loading I get:
> 
Loading, please wait...
Linux Ubuntu 2.6.27-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686

The programs included with Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

To access offical Ubuntu documentation, please visit: [http://help.ubuntu.com/](http://help.ubuntu.com/)
To run a command as administrator (user "root"), use "sudo <command>". See "man sudo_root" for details.

ubuntu@ubuntu:~$

At this point I'm at a command line, and can type anything in. Trying to boot from the live CD yields the same thing.

At this point I got to questioning if the memory of my r30 (should be 128 MB) or some other component could possibly be insuffiecnt for the Live CD. It is, after all an older laptop.

I decided to try Xubuntu, which may be a better idea for older systems because it has a lighter weight window maneger (is this true?) Anyway, so I got the alternate CD which should be better for systems with low memory, and tried installing in text mode.

I set the BIOS settings to auto-detect the IRQ settings. I'm not sure if this is related to my next problem or not, but I noticed it doing "disabling IRQ 15#" as it was booting to the installer.
> 
irq 15; nobody cared (try booting with the "irqpoll" option handlers) 
Anyway, it boots to the installer in text mode. I select English, then American Keyboard.

Then, at the Auto-Detect CD-ROM drive it can't detect it and wants me to load a module manually. I've tried it several times and sometimes it even freezes while trying to detect. I'm unsure what to do or how to know which module.

I bought the laptop used, and the hard drive was bad, and I replaced it with another hard drive from another r30 I have for spare parts. It boots to windows just fine from the other r30 windows installation! I know I need to reformat that before I move on.

I also found someone with a similar problem here:

[http://www.techspot.com/vb/topic92968.html](http://www.techspot.com/vb/topic92968.html)

I apologize if this post is a bit long-winded, my main motive for using such an older laptop it trying assembly language optimizations on the pentium 3 for hobby reasons. Big thanks in advance for any help. :)

---

### Post by ajgreeny on 2009-04-03
If you really do only have 128 MB of ram, it is not enough to run ubuntu.  get more ram or try one of the linux distros that will run in small amounts of ram, eg DSL, Puppy.  Have a look in [distrowatch]("http://distrowatch.com/")

---

