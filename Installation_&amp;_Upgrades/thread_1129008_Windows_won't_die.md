---
title: "Windows won't die"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Kugerfang on 2009-04-18
Hello all.

After installing Service Pack 3 for Windows XP and it suddenly disabling my Wireless Card, I decided I couldn't put up with all the crap that Windows is giving me.

So I decided to install Ubuntu.

After making a bootable USB using Unetbootin and installing Ubuntu, I rebooted the system to find this error waiting for me:
[FONT="Fixedsys"]
Windows cannot find [system directory]\hal.dll[/FONT]

BUT I JUST FORMATTED THE HARD DRIVE WITH WINDOWS IN IT!

I do have this other hard drive though, it's 10 GB and I haven't formatted it yet. However, that 10 GB Drive doesn't have Windows on it. What happened?

---

### Post by Partyboi2 on 2009-04-18
Hi, maybe try something like [[COLOR=Blue]Dban[/COLOR]]("http://www.dban.org/") to wipe the hard drive.

---

### Post by Therion on 2009-04-18
> **Kugerfang said:**
> What happened?
Sounds like you partitioned instead of doing a full on reformat and reinstall.  It's an easy mistake to make.  Short solution:  Try reinstalling using the "Guided - Use entire drive" option during the Partitioning stage of the installer or, as suggested above, totally nuke the drive and then reinstall.

---

### Post by glotz on 2009-04-18
Sounds like you didn't overwrite the bootloader. NT loader is still haunting you. You need to install GRUB (or LILO).

Welcome to the tribe!

---

### Post by hesjnet on 2009-04-18
> **Therion said:**
> Sounds like you partitioned instead of doing a full on reformat and reinstall.  It's an easy mistake to make.  Short solution:  Try reinstalling using the "Guided - Use entire drive" option during the Partitioning stage of the installer or, as suggested above, totally nuke the drive and then reinstall.

Do what Therion said. Reinstall it and choose "Guided - Use entire drive".

On the other hand, shouldn't Grub be able to do a dual boot?

---

### Post by Kugerfang on 2009-04-18
I finally fixed the problem  by telling the BIOS to boot to "IDE1" instead of "IDE0".

However, I got a new problem.

Ubuntu gives me an error about X-Server not being able to start. I checked the output and it says something about Failsafe being executed in the last 30 seconds...

After that, it gives me a command line similar to that of the terminal.

I read some topics saying this was related to graphics cards, and it seems so, since I use my mobo's integrated card because my GeForce 5500 won't fit properly into the socket anymore.

I tried restarting GDM using that command line, but it says GDM is already running!

---

