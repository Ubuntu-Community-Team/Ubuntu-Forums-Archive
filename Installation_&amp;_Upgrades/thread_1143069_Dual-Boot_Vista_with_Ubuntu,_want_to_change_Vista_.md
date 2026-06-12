---
title: "Dual-Boot Vista with Ubuntu, want to change Vista to XP"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by EVA01 on 2009-04-29
I'm running Ubuntu 8.10 on my Dell Latitude D630, dual-booting with Windows Vista Business Edition. However, some kind of serious error is plaguing Windows to the point where it is unusable. I highly doubt it is a hardware issue, since Ubuntu can still read the Windows partitions and manipulate the files without any errors. So what I'd like to do is either:
1) reinstall Vista, keeping my dual-boot setup
2) uninstall Vista and change to Windows XP (still keeping a dual-boot setup)

Does anyone know if I could just reinstall Windows Vista without messing with my set up? I was currently considering erasing the partitions that hold Windows using gparted and then reinstall Vista/install XP hopefully without seriously messing anything up. Any suggestions as to the best way to do this?

---

### Post by lisati on 2009-04-29
It's usually easier to install Windows first then Ubuntu, due to the different ways they handle the presence of another OS on the system (Windows likes to be the ONLY OS)

Having said that, it is possible to (re)install Windows after Ubuntu. Things to watch for include making sure that you point the Windows installer at the partition you want Windows in, and tell it not to repartition. You will likely have to reinstall Grub as well.

Other forum users may be able to give more detailed advice.

Oh, by the way, it's a good idea to make a backup of important data before actually doing anything else.

---

### Post by EVA01 on 2009-04-29
OK, I think I could be careful enough to only direct Windows to the correct partition. However, how exactly does one reinstall GRUB? (I assume what you mean is that when Windows is reinstalled, it wants to use its own bootloader, so the nice little menu I have when I start my computer will go away. Is that correct?)

---

### Post by Paidhima on 2009-04-29
Before you go reinstalling Windows, what seems to be the trouble in Vista?

---

### Post by graysky on 2009-04-29
> **Paidhima said:**
> Before you go reinstalling Windows, what seems to be the trouble in Vista?

Vista is the trouble with Vista, no :)

> **EVA01 said:**
> How exactly does one reinstall GRUB? (I assume what you mean is that when Windows is reinstalled, it wants to use its own bootloader, so the nice little menu I have when I start my computer will go away. Is that correct?)

Boot to the live CD after you get windows up and running and reinstall grub from a shell.

See my post #12 in [this thread](http://gparted-forum.surf4.info/viewtopic.php?id=13281).  Reinstalling grub is trivial (and [google is your friend](http://justfuckinggoogleit.com/)):

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by EVA01 on 2009-04-29
OK, thanks a lot.
As for the problem with Vista (besides that it is Vista haha):
It works fine when I'm in safe mode. No problems at all. However, if I log in normally, after a few minutes of usage, things get extremely slow and stop responding. If I press CTRL+ALT+DEL, nothing happens for a while, and then the screen goes black and a popup about security and logon and something or another comes up, and the computer goes back to the desktop, still frozen. Anyone know what could be causing this?

---

### Post by Paidhima on 2009-04-29
You've probably got some malware.  Chances are it's one of the smitfraud variants.  Here's my recommendation:

1.  Boot to Ubuntu, search for and download super antispyware (Windows version).  I found this to be particularly good at getting rid of that stubborn malware.  Place it on your Windows partition somewhere.

2.  Boot to Vista safe mode and install the application.  If you can boot to safe mode with networking, you can update it as well.

3.  Run a scan in safe mode, delete all entries found.

4.  Reboot to safe mode, run the scan again.

5.  Reboot to normal mode, run the scan again.

6.  Reboot.

If it's what I think it is, that should get rid of it, and will prevent you from having to reinstall applications and redo all of your settings.

---

### Post by EVA01 on 2009-04-29
Thanks for the suggestion! I tried it out, but what happened is the scan hung at a file called "sbscmp20_perfcounter.dll" for about an hour. I'm not quite sure what that file is though.

---

### Post by Paidhima on 2009-04-30
That's part of the .net environment.  You may want to try uninstalling .net and run the scan again.

---

