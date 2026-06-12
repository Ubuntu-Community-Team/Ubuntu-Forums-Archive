---
title: "Last night's updates seems to have broken Intrepid"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by bull8042 on 2009-02-18
I am running Kubuntu Intrepid with KDE 4.2 on a Dell E1505, 2.0Ghz Core 2 Duo, Radeon Mobility X1400.
I installed last night's updates which I remember included xorg stuff, fglrx, amdccle, etc. When I booted my computer this morning, it booted normally. The taskbar stuff loaded and it connected to the wireless network. Then after 1 - 2 minutes, it locked up completely, the wireless LED went on solid and the CAPS and SCROLL LEDs started flashing. The mousepad and external USB mouse won't respond and the only button on the keyboard that does anything is holding the power button for 4 seconds!
Anyone have any ideas where to go from here?

---

### Post by bull8042 on 2009-02-18
I have reinstalled the ATI drivers which brought my display back to the proper resolution. But it still locked up after a minute or two. I get the same results whether I boot into kernel 2.6.27-7 or 2.6.27-11.

I have disabled all desktop effects and killed KNetworkManager, but without any success resolving my problem.

Something is starting or stopping about 1 minute after kde is up and running. It is not random at all.
I managed to copy my fstab file to my ~ directory before it locked up. So, unless someone is able to offer some sort of suggestion soon, I guess I will begin reinstalling Intrepid after lunch.

---

### Post by bull8042 on 2009-02-18
Just bumping this back up. If anyone has any suggestions, I am more than willing to give them a shot before I re-install the OS.
Anyone?!?! (crickets chirping in background....)

---

### Post by wannadumpwindows on 2009-02-18
For future reference, wait a little longer to bump your thread next time. At least 12 hours. If you need immediate help, use the irc channel.

This is a forum, not dedicated tech support. People need time to find your thread, and possibly to look for info or a solution to help you out. We all think our problem is the most important.

Be a little more patient.

---

### Post by bull8042 on 2009-02-18
> **wannadumpwindows said:**
> For future reference, wait a little longer to bump your thread next time. At least 12 hours. If you need immediate help, use the irc channel.

This is a forum, not dedicated tech support. People need time to find your thread, and possibly to look for info or a solution to help you out. We all think our problem is the most important.

Be a little more patient.


Ooohhh! Patience... Sorry, I am not the most patient person, but I will try. Thank you for at least acknowledging my post. I will not bump it again. I mean, after THIS one. :D
Thanks...

---

### Post by wannadumpwindows on 2009-02-18
No problem. Sorry I can't offer more help.

Although it sounds exactly like a kernel panic. Usually when all your keyboard lights light up like that, it's a kernel panic. At least that's been my experience. It just doesn't make much sense that it happens in both of your kernels now.

Not that it helps you any, but I have an ATI chipset also, and so far haven't noticed any issues with mine. *crosses fingers*

---

### Post by bull8042 on 2009-02-18
> **wannadumpwindows said:**
> No problem. Sorry I can't offer more help.

Although it sounds exactly like a kernel panic. Usually when all your keyboard lights light up like that, it's a kernel panic. At least that's been my experience. It just doesn't make much sense that it happens in both of your kernels now.

Not that it helps you any, but I have an ATI chipset also, and so far haven't noticed any issues with mine. *crosses fingers*

OH, now THIS is screwed up!!!! I just completed a reinstall with a freshly downloaded copy of Kubuntu. It booted up after the install, I connected to the network..... and the MF #!*$ piece O' *#!$!** locked up tight as a drum!!!
I even renamed my old home directory before I reinstalled so it wouldn't use the same config files, and I formatted the / directory...... WTF is going on!?!?
This is just freaky... I booted into Windoze XP and it runs fine with no lock ups, so that seems to eliminate a hardware issue.

---

### Post by mykmelez on 2009-02-18
I don't know if it's related, but I upgraded Ubuntu 8.04 to 8.10 yesterday on a virtual machine running under VMware Fusion on a Mac OS X host OS, and ever since the upgrade I've been getting regular "Virtual machine kernel stack fault (hardware reset)" errors that hang the machine.  Sometimes the machine also hangs without that error appearing.

---

### Post by bull8042 on 2009-02-18
Well, I am beginning to think I have a HDD going south. I reinstalled from the Intrepid CD I burned a few weeks ago, and it froze after I installed the base system but hadn't done any updates at all.
I ended up formatting the root partition as fat32 from Windoze, running chkdsk. Then reinstalling Intrepid and letting it format the root partition as ext3. I have done all of the updates and reinstalled my programs and it hasn't frozen yet!
Makes me wonder if I should just go ahead and buy a new HDD to be on the safe side. I keep everything backed up to 2 external drives anyway, but it would be a real inconvenience to live without my laptop while waiting on the drive.

---

### Post by mykmelez on 2009-02-19
> **mykmelez said:**
> I don't know if it's related, but I upgraded Ubuntu 8.04 to 8.10 yesterday on a virtual machine running under VMware Fusion on a Mac OS X host OS, and ever since the upgrade I've been getting regular "Virtual machine kernel stack fault (hardware reset)" errors that hang the machine.  Sometimes the machine also hangs without that error appearing.

Things seem to be better for me since I disabled paravirtualization in my virtual machine, so probably I'm experiencing a different problem.

---

