---
title: "Ubuntu 9.10 fails to shutdown-restart computer"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by gvor54 on 2009-10-29
Hi!

I've just upgraded to Ubuntu 9.10.

I cannot shutdown or restart my computer ! Stand-by works OK though.

I always get the message:

 Buffer I/O error on device loop0, logical block 2056561.

Thanks in advance for helping me.

Gvor54

---

### Post by lushd on 2009-10-31
Hi Same problem here but the command line shutdown doesn't work either!  Any suggestions?

---

### Post by CaKiwi on 2009-10-31
I have the same problem, no solution yet

[http://ubuntuforums.org/showthread.php?t=1308198](http://ubuntuforums.org/showthread.php?t=1308198)

CaKiwi

---

### Post by solmisation on 2009-10-31
Hi
I have upgraded to karmic Koala on both my desktop and laptop, both have this same problem.

---

### Post by skyiscrying on 2009-10-31
I had same problem with the upgrade. So when the final 9.10 was released a day or so ago, I installed that and almost everything is ok. Well, it shuts down as normal and reboots quick. I am not running with any other OS at this point in time.

---

### Post by solmisation on 2009-10-31
Both my installs are via Wubi from within Xp and Vista respectively,  do you think this may be part of the problem?

---

### Post by grar05 on 2009-10-31
It seems it only happens with wubi installation. There are lots of reports at launchpad of this bug, and also a lot of forums opened talking abaout it. There is no solution yet I think. Do you think that it'll be solved with an actualization?

---

### Post by CaKiwi on 2009-10-31
My original install of Jaunty was also with Wubi. Hopefully, there will be a fix in a future update.

---

### Post by kixome on 2009-10-31
> **grar05 said:**
> It seems it only happens with wubi installation. There are lots of reports at launchpad of this bug, and also a lot of forums opened talking abaout it. There is no solution yet I think. Do you think that it'll be solved with an actualization?

not quite, I installed it a week before release, and I had the same problem. It was an upgrade from jaunty.

---

### Post by grar05 on 2009-10-31
So the problem is not about wubi, it's about the upgrade? And if is it, why some people works and some other have the problem?
And I also installed Jaunty with Wubi and then upgraded inside Ubuntu to Karmic.

---

### Post by solmisation on 2009-11-01
I have just done a clean install of karmic, again via Wubi, and all went well.

---

### Post by grar05 on 2009-11-01
Yes it seems to work if you do a clean installation, the problem is if you can't do the installation, as in my case. I have no time right now to uninstall, reinstall and configure all so I still shuting down manually... Till some actualizations solves it or reinstalling when i find time. I hope an actualization will arrive before it!

---

### Post by WildSioux on 2009-11-02
I have the same problem on my Gateway Desktop.  I did a fresh install of Kubuntu 9.10 though.  I installed it on a different partition because I also have LinuxMint 7 (Jaunty) KDE CE installed.

I am able to shutdown properly from the KDE GUI.  But restarting is where it freezes after exiting KDE and after the Kubuntu splash it drops to text and shows what it is doing.  It always freezes on this:

```
8262.0883491 Restarting System
```

Holding down the power button is the only way to shut it down at this point.

I tried changing things with ACPI in grub.  While that fixed the restarting issue and it restarted fine.  It also would not let me shutdown.

I am seeing a lot of problems with restart/shutdown in 9.10.  Other than this problem everything is running great.
[B]
Should I start a new thread with my issue? [/B] I really do hope someone finds a fix for this because I don't want to go back to Jaunty (no problems on shutdown/restart).

---

### Post by yojimbo72 on 2009-11-02
I'm having issues with shutting down as well but only after upgrading to Ubuntu 9.10 the error code I'm getting reads  "899.610065 buffer I/O error on device loop logical block 187199"    Some have suggested that this is because it detects a floppy drive and I should disable it, then restart. Haven't tried this yet since I don't have a floppy drive installed on my system..however there is a 3.5 bay where one could be installed. Any other reason I would get this error when attempting to shut down?

---

### Post by mosug on 2009-11-02
**!!This is not a workaround!!**

I'm still new to linux and I'm still trying to understand what's going on, so DON'T follow. I'm just trying to give some hints to those who is working on a fix to this problem. And this is **definitely not** a fix nor a workaround.

Here is my findings.
I found that the new lupin-support (0.27) doesn't contain the script "lupin-sysctl".
After reading the changelog, there's a line like this.

> lupin (0.22) intrepid; urgency=low

  * Disabling lupin-sysctl since its functionality has been replaced by
    syncio (LP: #204133). Lupin-sysctl is not actively removed if
    already installed since syncio also requires a change to menu.lst.

Also a line in lupin-support 0.23

> lupin (0.23) karmic; urgency=low
.....skip.....
  * Removed old lupin sysctl file

So I try to remove lupin-sysctl and karmic does shut down or reboot normally (at least the last time), but the buffer I/O warnings are still there.
Since those fresh install of Karmic won't contain this script, it does explain why this only happens to those upgrading from old versions of ubuntu, like me. So maybe the problem is caused by some old files being left behind after upgrading?

By the way, may those having a fresh karmic help to see if there's any buffer I/O warnings before their PC turns off?
Maybe the I/O error is another problem at all.

---

### Post by CaKiwi on 2009-11-03
The following solution corrected the problem for me

On the terminal:

sudo gedit /etc/init.d/halt

Add the following line to the end of the halt script:

rmmod snd-hda-intel

Proceed to a successful shutdown.

I found it in this thread

[http://ubuntuforums.org/showthread.php?t=1306789&page=2](http://ubuntuforums.org/showthread.php?t=1306789&page=2)

CaKiwi

---

### Post by WildSioux on 2009-11-03
BTW...

This is how I fixed my restart problem (separate thread by me, post #2)...
[http://ubuntuforums.org/showthread.php?t=1311191&highlight=restart]("http://ubuntuforums.org/showthread.php?t=1311191&highlight=restart")

Since I was able to shutdown correctly, I didn't need to change any acpi stuff.

Hope that helps someone!

---

### Post by CaKiwi on 2009-11-04
I was too hasty with my previous post. I was able to shutdown only once after applying it. But I found this fix in another thread. Post #19

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589)

---

