---
title: "Kernel panic after updating"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by quirijnquintus on 2009-03-05
Dear reader,
Recently my friend introduced me with Ubuntu and I wanted to try for myself. I wanted a dual boot so cleared space of my HDD of my laptop. 
My Dvd/cd drive doesn't really work anymore (ticking sound when a cd-rom is read) So I decided to do a installation from a USBstick, which I made via my friends laptop, which runs Ubuntu.

The installation went fine and soon I had Kernel 2.6.27-7 on my system. After the first boot there are 262 updates which have to be installed. This takes a while. At 2/3 of the installed updates it suddenly restarts the system from grubloader but then this Kernel Panic occurs:

**Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)**

So I turn the laptop off and on and see in the Grub loader that there is another kernel aswell: kernel 2.6.7-11

I presume this is the latest one where the updates are being installed so press enter en then the kernel panic occurs again.

Press off and on and try kernel 2.6.7-7. This version works, but on start up there is a message saying: Instal Problem: The configuration defaults for GNOME power manager have not been installed correctly.

How do I fix this problem?

I am running a 1.60ghz Celeron 512mb RAM. 80GB HDD, in 3 partitions, on one is windowsXP, on the other some programs and the 3th and largest (42GB) was reserved for Ubuntu.

---

### Post by itix on 2009-03-06
I find it very odd that the laptop would reboot on it's own. I've never heard of that before.

What I would guess has happened is that it has updated the kernel itself but not it's headers or some kind of modules and therefor the kernel makes illegal calls fot things that does not exist.

If it isn't too much trouble, I'd ask you to reinstall the system. That would be the simplest thing to do.

Just let it update on it's own and after that and you'll hopefully be good to go again.

---

### Post by quirijnquintus on 2009-03-07
I did that and the same problem occurs. Can there be a fault in the USBdrive installation version?

---

### Post by itix on 2009-03-09
It might actually be that. If possible, do an integrity check with md5sums (the on-disc tool doesn't always detect problems).

I don't understand why it needs to mount a root file system (I think the boot loader is trying to reach one of your other partitions, but I don't see why as a new install on 43 Gb wouldn't need that as it has plenty of space to do the updates).

There might be some problems with that kernel as well, but I'm not sure.

If nothing else helps, try to do "sudo apt-get update"  and post any errors here and we'll see if we can understand what the hell is going on here.

---

### Post by quirijnquintus on 2009-03-10
OK what I did in the mean while was to enter recovery mode of the first 27-7 and do a fdmr recovery. This had the effect that it installed the rest of the updates I guess? Because after that the Kernel 27-11 worked again and I think it is working OK right now. It is stable and all the updates are done.

---

### Post by itix on 2009-03-10
I have no idea what fmd recovery mean, but if it's working, I guess I won't be needed anymore.

I still don't get why rebooted in the middle of an update though... Good luck with the rest.

---

### Post by Neo_The_User on 2009-03-10
I get that error too a lot when compiling kernels under 700K but you're using a stock kernel. I don't know what the problem is but add me to the club.

"Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)"

---

### Post by quirijnquintus on 2009-03-12
> **itix said:**
> Good luck with the rest. THanx!
I'll need it.. Still have a few problems while my switch to ubuntu.. But it appears that this is because I have a shitty laptop :(

---

