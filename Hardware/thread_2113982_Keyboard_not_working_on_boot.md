---
title: "Keyboard not working on boot"
date: 2013-02-08
forum: Hardware
---

### Post by willdebug on 2013-02-08
Okay so I built this computer and installed Ubuntu 10.10 LTS on it all was working fine until eventually my main drive died. I put in two new drives equaling up to 250 GB. Now I boot it into anything and my keyboard stops working. It works in BIOS. And it works in Windows. I've checked to see if it is being powered by BIOS and I know it isn't supposed to and it isn't. But it still doesn't work.
I know this might be of use:

81.9 GB Primary Master
81.9 GB Primary Slave
80 GB Secondary Slave
DVD RW Secondary Master
1 GB RAM
AMD ATHLON CPU

Fixed it Problem was the BIOS thought it was DOS and USB was not enabled for DOS Operating systems.

---

### Post by MartianTek3 on 2013-02-08
If i were you I would sudo apt-get upgrade to 12.10 

The Latest and greatest Quantal Quetzal 

The minimum memory requirement for Ubuntu 12.10 is 768 MB of memory and 5 GB of disk space for Ubuntu Desktop. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal; however, it will complete successfully, and the system will perform adequately once installed.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#Upgrading_from_Other_Releases](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop#Upgrading_from_Other_Releases)

Surely this simple problem will be solved then

sudo apt-get update && sudo do-release-upgrade 

-MartianTek3

---

### Post by willdebug on 2013-02-08
No I can't I'm trying to install Ubuntu on the computer but it wont install because the keyboard doesn't work
And it was working And btw I am not having "my first cup of Ubuntu" I have been using it for what seems to be 9 years

---

### Post by willdebug on 2013-02-08
Im running a memtest I have found out a USB mouse doesn't work either going to see if USB is disabled

---

### Post by Mark Phelps on 2013-02-09
It shouldn't matter, as your keyboard and mouse were working before you changed the drives, but you could check the BIOS and see if it has a "legacy" setting (as in USB 1.x) and if that is disabled, then enable it.

If you have more than one USB port, you can try the other.

And yeah, you've probably already tried BOTH of these (since you aren't new to this) -- so please don't be insulted by my suggestions.

---

### Post by willdebug on 2013-02-09
> **Mark Phelps said:**
> It shouldn't matter, as your keyboard and mouse were working before you changed the drives, but you could check the BIOS and see if it has a "legacy" setting (as in USB 1.x) and if that is disabled, then enable it.

If you have more than one USB port, you can try the other.

And yeah, you've probably already tried BOTH of these (since you aren't new to this) -- so please don't be insulted by my suggestions.

Fixed it simple problem of BIOS thinking live CD's are DOS and not letting DOS use USB ports

---

