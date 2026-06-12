---
title: "Problem booting due to battery dying"
date: 2011-03-27
forum: Hardware
---

### Post by Onyx1 on 2011-03-27
I have an Asus eePc netbook and have been running ubuntu 10.10 on it for around a week. Today I left my computer on and it went into hibernate mode( I'm assuming I wasn't sitting there watching) when i came back i turned it back on and it immediately died so I assumed dead battery.I plugged it up and it went through the boot process. About half way through the boot process it just stopped. The screen has the built in shell on it and is saying my computer name login like when you run the shell by clicking ctrl+F2 so i typed in what I thought was my sign in and it didn't work. I tried twice and also tried ctrl+F7 because that is how you get to gui when computer is running. I then forcefully rebooted my computer and when it was loading it just stopped and this is what is on screen.
```
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help for a list of built-in commands.

(initramfs)
```
this is not everything that is on screen this is the last 7 lines. After where it says (initramfs) is my courser and i assume i'm suppose to type in a command but I don't know what to put in.

---

### Post by dandnsmith on 2011-03-28
Sounds like something may be corrupted and need fixing.
It's just possible that a period spent charging up may get things back to normal - else you'll need to be able to boot from some other media to effect a repair of your installation (do you have something ready? I assume that, with a netbook, you'll need either a bootable USB stick or have a USB-connectable external CD/DVD drive to allow booting from CD).

I don't have a 'ritual' for fixing things from such a state - have to feel my way, so perhaps someone else will be needed for advice.

---

### Post by Onyx1 on 2011-03-29
I found another forum that fixed it. Thank You for trying to help because no one else seemed to care haha. For anyone else who needs it here is the thread. [http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946) Post number 4 from laerub18 has everything needed to fix it.

---

