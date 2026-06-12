---
title: "[SOLVED] Filesystem boots read only after crash"
date: 2008-07-23
forum: General Help
---

### Post by kidux on 2008-07-23
Forgive me for not being entirely verbose, but I don't have the actual machine with me.

Last night, something happened where it hard locked on me with a funky screen. It's a laptop, so it had gone into suspend mode, but when I opened the lid, the screen was white and the caps lock light was flashing. It's a Toshiba Sattelite A215, with an ATI (I hate that part) video card. It was running XFCE with compositing enabled, with AWN, conky and stalonetray running.

After I hard booted it, the xserver was hosed, and wouldn't boot into GDM. After logging in via the command line, it gives the message that it's a read only filesystem, and chmod will not allow me to change it. /home is not accessible, nor does it see any users folders in there.

It was running kernel 2.x.19-generic on Ubuntu 8.04, and I think that may be part of the problem, as this is the second time it's happened, and I've seen numerous posts about Hardy hard locking, especially on laptops. Last time I re-installed Ubuntu as there was nothing on there, but now I have a bunch of stuff that I don't really want to go back and setup, so what I need is to figure out how to get the filesystem back to read-write.

If anyone has any clues, I would be most appreciative, thanks!

---

### Post by WRDN on 2008-07-23
First, try fixing the X Server, by booting into the Recovery Mode and selecting "Fix X Server". Then, if you boot into the command line again, try using the command "startx" to start the X Server.
Also, are you able to boot from the Ubuntu LiveCD/ other OS to check the user files are still there?

---

### Post by jimv on 2008-07-23
I've had this happen to be before, and running a diskcheck from the live cd fixed the problem.

The easy way to check your partition from the livecd is once you are booted from the cd, go to System>Administration>Partition Editor, then right click on your Ubuntu partition and click Check.

---

### Post by kidux on 2008-07-23
> **WRDN said:**
> First, try fixing the X Server, by booting into the Recovery Mode and selecting "Fix X Server". Then, if you boot into the command line again, try using the command "startx" to start the X Server.
Also, are you able to boot from the Ubuntu LiveCD/ other OS to check the user files are still there?

I tried that but it doesn't work because it keeps putting the filesystem into read only, so it can't do anything to the xorg.conf file, or any other file for that matter.

I'll try to boot from a live CD to check, it but my wife just called to tell me our desktop went down now, which was running 8.04 as well. I think I'm gonna go back to 7.10, at least until they can get these issues worked out.

---

### Post by jimv on 2008-07-23
> **kidux said:**
> I tried that but it doesn't work because it keeps putting the filesystem into read only, so it can't do anything to the xorg.conf file, or any other file for that matter.

I'll try to boot from a live CD to check, it but my wife just called to tell me our desktop went down now, which was running 8.04 as well. I think I'm gonna go back to 7.10, at least until they can get these issues worked out.

That's odd

I haven't had any issues like this with Hardy...the last time this happened to me was in Feisty.

---

### Post by kidux on 2008-07-23
I never had any problems with Feisty. I actually think it's a problem with the kernel. My desktop didn't have any issues until the kernel upgrade a week or so ago, then when it restarted it had issues with kernel panic not syncing to something or other. I let it sit last time for a while and it seemed to correct itself, but this time my wife was fiddling with it for a bit and it wouldn't get past the panic, so downgrading the kernel is going to be the course of action on both machines once I get them back up, I think.

---

### Post by kidux on 2008-07-25
> **jimv said:**
> I've had this happen to be before, and running a diskcheck from the live cd fixed the problem.

The easy way to check your partition from the livecd is once you are booted from the cd, go to System>Administration>Partition Editor, then right click on your Ubuntu partition and click Check.

Thanks, this worked beautifully.

---

