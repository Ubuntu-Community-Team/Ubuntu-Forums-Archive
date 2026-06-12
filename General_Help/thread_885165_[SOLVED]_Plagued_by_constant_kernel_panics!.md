---
title: "[SOLVED] Plagued by constant kernel panics!"
date: 2008-08-09
forum: General Help
---

### Post by damis648 on 2008-08-09
Okay:

About 20-30 Minutes ago I had a crash/lockup... specifically a kernel panic (Num and Caps lights blinking) on my XPS M1530. Now, it's just constant! Usually within 60 seconds after X starts to load (I have had it crash when my cursor first appeared... and also 4 minutes after booting... so it seems relatively random?), another crash. I have had a look at /var/log/messages with tail -f and nano in recovery mode... nothing sticks out at me as an error or warning though. The only change I made to my system recently was update Virtualbox (Closed Source not the OSE; downloaded the DEB from thier site) so my best guess would be it's the virtualbox kernel module, but I have no idea really so I am posting here. So far I have had I think 5 or six crashes/panics. If anyone can offer any solutions or help in any way, thank you in advance. My computer is unusable right now, I am on another Windows machine. If anyone would like me to post any of my system logs, ask and I will post what is requested. Thanks! I would appreciate any help.

---

### Post by spiderbatdad on 2008-08-09
Are you dual booting, and have you "cleanly" shut down windows prior to booting into Ubuntu?
Just occurred to me that might be a silly question, as you have been using ubuntu for a while. How about attaching dmesg to a pastebin?

---

### Post by damis648 on 2008-08-09
> **spiderbatdad said:**
> Are you dual booting, and have you "cleanly" shut down windows prior to booting into Ubuntu?

I am not dual booting. I am running only Ubuntu with the newest -19 kernel from the repos.

---

### Post by phidia on 2008-08-09
See if you can boot up completely by choosing failsafe or failsafe/recovery kernel from the grub menu. 
If it works ok doing that take a look at your /var/log/xorg.0.log (dmesg, messages & syslog too).

---

### Post by spiderbatdad on 2008-08-09
You might try disconnecting power and battery for 15 minutes or so, maybe something stored is ram is causing the crash...or defective ram. Sorry, kernel panic is tricky issue.

---

### Post by Habbit on 2008-08-09
If you suspect the VirtualBox kernel module is to blame, try blacklisting it by adding a "blacklist module_name" line in /etc/modprobe.d/blacklist and then reboot. If the crashes stop, then it was either the VBox module itself or some bad interaction it caused - the morale would be "go open source again".

---

### Post by damis648 on 2008-08-09
> **phidia said:**
> See if you can boot up completely by choosing failsafe or failsafe/recovery kernel from the grub menu. 
If it works ok doing that take a look at your /var/log/xorg.0.log (dmesg, messages & syslog too).

Well, recovery works fine, I entered the shell prompt as root. I didn't find anything in the dmesg log, or the messages or syslog. The most I found was an <WARN> from networkmanager saying that It failed to execute the child process "/usr/sbin/nscd" because it didn't exist. I also had a look around Xorg.0.log and really didn't find anything; but honestly for any of these logs, I do not really know what to look for except anything saying WARN or ERROR or something. I hadn't had a panic yet, so I decided to enter runlevel 5 and login (using telinit 5). I have been running for ten minutes so far with no panic, but an interesting error: I have the CPU Frequency Scaling Monitor in my top panel, and I use it to throttle down my CPU from time to time, but when I logged it, it threw an error that my CPU doesn't support scaling, which it most certainly does. My CPU is not running full-speed-ahead. Could the scaling monitor be the culprate? Or is that just a side effect of what I have just done? I will now reboot and see if I get any panics.

---

### Post by spiderbatdad on 2008-08-09
> **Habbit said:**
> If you suspect the VirtualBox kernel module is to blame, try blacklisting it by adding a "blacklist module_name" line in /etc/modprobe.d/blacklist and then reboot. If the crashes stop, then it was either the VBox module itself or some bad interaction it caused - the morale would be "go open source again".

This might work if you know how to boot and mount your installed file system from the live cd.

---

### Post by damis648 on 2008-08-09
> **spiderbatdad said:**
> This might work if you know how to boot and mount your installed file system from the live cd.

Of course, but I can still use recovery mode... it is something in the second part of the boot process causing this I suspect. I will try blacklisting it once I try your suggestion, removing power for about 15 minutes.

---

### Post by damis648 on 2008-08-09
> **spiderbatdad said:**
> How about attaching dmesg to a pastebin?

Sorry, but I have no idea what a pastbin means... do you just want me to attach my dmesg?

---

### Post by spiderbatdad on 2008-08-09
sure. it may be too large and you will have to right click on the file and select create an archive. then upload the archive.```
dmesg > ~/Desktop/dmesg.txt
```

pastebins are hosted sites for posting program codes or large files:
[http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/)

after you post to a pastebin and save, you will get a unique url that you can post as a link:
[http://pastebin.ubuntu.com/36056/](http://pastebin.ubuntu.com/36056/)

---

### Post by damis648 on 2008-08-09
Okay... interestingly enough I just rebooted after removing the battery for a while and I have not gotten a panic for a couple minutes now. I will not mark it as solved, for as all i might know It might not work in the morning, but for now, I can at least manage to post my dmesg:
[http://pastebin.ubuntu.com/36057/](http://pastebin.ubuntu.com/36057/)

---

### Post by spiderbatdad on 2008-08-09
possibly a malfunctioning program in cmos. clearing the ram can fix a kernel panic if the ram is still good.

---

### Post by spiderbatdad on 2008-08-09
```
 Kernel command line: root=UUID=(#'s) ro quiet splash i8042.nomux=1

```
This is an interesting option. For thinkpad?
Did you add this as defoptions or append it to the kernel line. I believe the former is recommended.

---

### Post by damis648 on 2008-08-09
> **spiderbatdad said:**
> ```
 Kernel command line: root=UUID=(#'s) ro quiet splash i8042.nomux=1

```
This is an interesting option. For thinkpad?
Did you add this as defoptions or append it to the kernel line. I believe the former is recommended.

I simply appended it to all kernels in menu.lst. I need this option for my trackpad with my new BIOS version otherwise it will just jump all around the screen and start clicking everywhere and go completely crazy... quite annoying, as you could imagine ;-).Thanks for the help, so far it seems to be fine... I am going to shut down and watch a movie, but I will be back in the morning to see if everything is still working. Thanks for the help!

---

### Post by damis648 on 2008-08-10
> **spiderbatdad said:**
> possibly a malfunctioning program in cmos. clearing the ram can fix a kernel panic if the ram is still good.

Thank you so much for that suggestion... I woke up this morning and found my computer to be working with no kernel panics so clearing the ram seemed to have worked. I am marking this as solved until further notice.:popcorn:

Thanks again.:guitar:

---

### Post by damis648 on 2008-08-11
I am not going to mark this unsolved, but it started happening again. I did, however, figure out the problem. It WAS the virtualbox kernel module and I blacklisted it, so everything is running smoothly. A warning to Anyone wanted to update their Virtualbox CSE, do not. There are no new features... if you do not count kernel panics ;-). [UNSOLVED].. and now [RE-SOLVED] Thanks again for the help!

---

