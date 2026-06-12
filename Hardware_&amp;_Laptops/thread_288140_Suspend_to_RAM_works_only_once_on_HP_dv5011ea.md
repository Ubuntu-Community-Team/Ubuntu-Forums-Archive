---
title: "Suspend to RAM works only once on HP dv5011ea"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by fa2k on 2006-10-29
Hi, my laptop is now almost 100% set up correctly, but I have a weird problem with Suspend to RAM:

After tweaking the /etc/default/acpi-support file, I get the laptop to suspend and resume. But only once, the second time I try, it locks up and I need to kill it by holding the power button;

The state seems to be unchanged after the first resume, i.e. all the same processes are running, all the same modules are loaded. The VMWare interfaces are brought down, but I can't see that that is a problem.

I have tried all the options in the /etc/default/acpi-support, and also selectively chmod -x'ing some of the suspend/resume scripts (obviously without success).

When it locks up, the system is started, LEDs go on, screen remains black, AFAIK the disk is not accessed, the WLAN adapter is not started, and the computer is completely unresponsive.

I hope anyone can help me ;)

Also, if it is "unfixable", short of modifying the kernel, do you think it will be fixed in a later version, even if it is a relatively old laptop?

EDIT: One more thing, is there any way to get detailed log output from the resume process stored in a file or such?

---

### Post by Leppiz on 2006-11-04
I've got a similar problem with my HP/Compaq nx6110. Suspend or hibernate works correctly only once per boot.

My behavior for the second try is that the suspend just seems to lock the screen and doesn't work. Surprisingly the suspend script seems to stay running somehow and it activates after a shutdown is initiated later. The computer goes to sleep in the middle of shutdown and resumes afterwards just to finish the previously initiated shutdown. ](*,)

---

### Post by sedd on 2006-11-06
Do you guys have sata hard drives?  I have an hp nw9440 and I've almost got suspend working (the first time. we'll see about resuming from the second suspend.)  Everything except the disk seems to come back ok.  I get kernel errors, something to the tune of "io error on /dev/sda1"   it tries to switch to read-only and that fails too.  

I found some old forum posts saying this was supposed to be fixed in the 2.6.15 kernel, but I've got 2.6.17, so I don't know whats up.

---

### Post by fa2k on 2006-11-07
It works in Windows, so it is definetly possible. I'm going to try OpenSUSE and FC6 to see if any of those distros get it right, and either stick with them or try to "backport" the fix into Ubuntu.

One more thing, when I resume, there is sometimes something wrong with the keyboard; a lot of strange characters appear when I type. Also sometimes "screen locking" does not occur, so that means that the resume script never finishes (i.e., it locks up somewhere). I can't find it in ps though.

@Leppiz: I don't have a S-ATA drive, so this is a different problem.

---

### Post by Leppiz on 2006-11-07
I haven't got a SATA drive.

I found out today, that the suspend isn't so deterministic that I'd thought. It seems to hang sometimes when trying to resum from the first suspend, but on the other hand I got it to suspend for the 3rd time after boot. Sometimes my USB stick won't mount after coming back from suspend.

---

### Post by fa2k on 2006-11-17
I tried it on FreeBSD; it didn't even recover once. On Fedora I seem to have the same problem as on Ubuntu, and I havent tried SUSE extensively yet, only the Live DVD. I hope that SUSE's s2ram may be able to help me (evn thoungh Novell are officially evil now;)

---

### Post by 56phil on 2006-11-17
I have a Gateway M680 and it suspends and resumes ok. Perhaps it's a HP problem. Good luck.

---

### Post by fa2k on 2006-11-23
I experimented with the acpi_sleep options in SUsE, but no success (s3_bios locked up on first; s3_acpi on second as usual). Sadly, I am far from qualified enough to patch the 
kernel, much less troubleshoot such advanced problems, so I can't fix it myself. There is no way I'm going to trust Microsoft with my data, so I guess I'll never get STR working :( I'll need another laptop then...

3.5 more questions.
- Is there a chance may work on a different display driver in X, and (how) can I change the framebuffer driver (if that may help)? The laptop locks up when x is not started.
- Is there any way to disable devices, to eliminate them as causing the problem (like pulling out PCI cards, only in software)
- Is there any chance that my only modification to the machine, increasing RAM to 1.1GB, may have caused the problem?

(sorry for the bumpyness of this post;)

---

### Post by lewiz on 2006-11-25
I can only recover from the first suspend or hibernate.  I *do* have a SATA harddisk and this is what fails to come back after a second suspend/hibernate.
It's a hand-built PC but has an Intel 805D chip in an Asus motherboard.
My Sony Vaio X505 (no SATA disk) works beautifully with suspend and hibernate.

Does anybody have any further suggestions?  I am quite happy to give some kernel patching a shot if we can fix this one.

---

### Post by lewiz on 2006-11-25
After messing with all of the BIOS settings and ACPI settings I could find I got no further.
Interestingly I can hibernate/resume my system more than once without any apparent problems.
For the time being I'm happy with this... I just wanted some way to power my desktop off when I go to work :)

---

### Post by pgilmon on 2006-11-25
I have an HP dv5161 (I guess it's similar to yours) and it hibernates well. See [http://www.ubuntuforums.org/showpost.php?p=1722432&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1722432&postcount=2)
I have also set the screensaver to a non 3d one, since it seemed to hang from time to time after resuming (the screensaver is activated before hibernating/sleeping)


Edit: It still crashes sometimes, even if the screensaver is not a 3D one :(

---

### Post by captainzerocool on 2006-11-25
I have never got the suspend/Hibernate function to work on my Dell b120.

---

### Post by fa2k on 2006-11-28
It's a different computer (man, I hate HP's regional product codes..). Mine uses an ATI Radeon M200 Xpress card. The vbetool POST is configurable through /etc/defaults/acpi-support, and already tried. I will try to boot in text mode and also to remove the framebuffer drivers, but if it doesn't work, I won't post, because I have already "bump"ed this thread enough. Thanks for all the help!!

---

### Post by fa2k on 2007-01-20
The problem is now fixed :D :D :D :D :D :D :D :D 

The BIOS update on HP's page did the trick. I really appreachiate the fact that HP fixed it, even though it wasn't a problem on any version of windows (including Vista). I haven't done extensive testing, but it is obvious that it works now where it didn't work before.

---

### Post by redskinsfan on 2007-03-05
I'm still experiencing this problem on a dell latitude d800.  The suspend works the first time (after some tweaking with xorg.conf and acpi-support), but the second time, the screen freezes.  If I restart the x-server after the first suspend/restart (ctrl+alt+backspace), then suspend continues to work.  Anyone have a fix for this problem?

Thanks,

---

### Post by i speak in math on 2008-05-29
I have the same behavior. (compaq c714nr). Suspend works okay once and everything appear normal after resuming. But second time i try to suspend, resuming results in a hard lock up. No caps light toggle. After a while, my fan spins up as the cpu hits threatening temperatures. Need to do a hard shut down. Still hoping desperately for a fix. Unfortunately, I can't update the bios without reinstalling Vista as HP/compaq seem to have a windows only installer.

---

