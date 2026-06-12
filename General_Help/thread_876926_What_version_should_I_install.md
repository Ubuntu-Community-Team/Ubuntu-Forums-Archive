---
title: "What version should I install?"
date: 2008-08-01
forum: General Help
---

### Post by kcav45 on 2008-08-01
Have 10 PCs that have Pentium 3 processors and 128MG RAM.  What version of Ubuntu should I install?

---

### Post by rahmath on 2008-08-01
For that configuration, i suggest to go for Ubuntu Gutsy 7.x

---

### Post by kcav45 on 2008-08-01
Thank you.
KC

---

### Post by chris4585 on 2008-08-01
me personally.. i'd install xubuntu with the alternative cd, or fluxbuntu possibly

but in all honesty i'd just do a server or minimal install and add onto what i want, but with 10 computers... staying consistent may be a problem

---

### Post by tuxxy on 2008-08-01
If you could double up the RAM in one of the 10, then you could probably run Hardy, with GNOME the standard Ubuntu install if you wanted.

---

### Post by silkstone on 2008-08-01
I think you will struggle to install or run Ubuntu on those machines, unless you upgrade the RAM. Xubuntu may be OK, but PuppyLinux or DSL would probably be better.

See this for a description of Linux distros for low-spec machines...

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by geirha on 2008-08-01
I would advice against ubuntu for your system. The [system-requirements]("http://www.ubuntu.com/getubuntu/releasenotes/710") for ubuntu 7.10 states: > The minimum memory requirement for Ubuntu 7.10 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.)

Even xubuntu is a bit too heavy with [system-requirements]("http://www.xubuntu.org/get#hardy") > To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

[fluxbuntu]("http://wiki.fluxbuntu.org/index.php?title=FAQ") seems like your best choice with > Fluxbuntu uses 35-46mb of ram. If you have 64MB of ram we would definitely recommend having adequate swap space.

---

### Post by billgoldberg on 2008-08-01
> **kcav45 said:**
> Have 10 PCs that have Pentium 3 processors and 128MG RAM.  What version of Ubuntu should I install?

Certainly not Ubuntu 7.10.

Ubuntu 8.04 (LTS -> long term support).

I don't know why someone suggested it, but 8.04 runs on the same specs and is better.

But those specs are too high for you machines.

Gnome, kde and xfce are a no-go for those specs.

Fluxbox should run smoothly on those babies.

There is a fluxbuntu distro [here]("http://fluxbuntu.org/").

I would use that to get speed and still have the greatness that is Ubuntu.

---

### Post by linux_tech on 2008-08-01
The best choice is to upgrade the ram at least to 256Mb
If the memory only 128, then you should also make sure the rest of the hardware meets minimum reqs.. hdspace, cpu, etc.

re: version- depends on where you want to be between the minimum reqs vs the recommended reqs.  You will need to use the text based  - alternate install 

Given the low RAM, I would install Xubuntu 

below are links for low memory installs-
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
 [https://blueprints.launchpad.net/ubuntu/+spec/low-memory-install](https://blueprints.launchpad.net/ubuntu/+spec/low-memory-install)

---

### Post by w0ng on 2008-08-01
Last year I was running a laptop: p4 3ghz, 1gb ram and found that ubuntu was too slow. xubuntu ran much smoother with lower demanding apps e.g. gnumeric/abiword instead of openoffice

---

### Post by chris4585 on 2008-08-01
> **w0ng said:**
> Last year I was running a laptop: p4 3ghz, 1gb ram and found that ubuntu was too slow. xubuntu ran much smoother with lower demanding apps e.g. gnumeric/abiword instead of openoffice

O_o i have a laptop intel centrino 2.2ghz 3.5gbs of ram and it flys with ubuntu

---

### Post by FakeOutdoorsman on 2008-08-01
An alternative use for these machines would be using them as thin clients with LTSP:
> To the user, a thin client behaves like a regular desktop computer. To the administrator, a thin client has no storage of its own, is easy to maintain, and can give the user a modern computing experience even with ancient hardware.

A thin client is a computer in client-server architecture network which depends primarily on the central server for processing activities, and mainly focuses on conveying input and output between the user and the remote server where the application program is actually being executed. The thin client computer functions as a very smart graphic terminal.

From [Thin Client Howto]("https://help.ubuntu.com/community/ThinClientHowto") at Ubuntu Community Documentation.  Also see [Ubuntu LTSP Quick Install]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall").

---

### Post by snowpine on 2008-08-03
I would recommend something lighter than Xubuntu for those computers, like Crunchbang or Fluxbuntu (assuming you want to stay in the Ubuntu family). Crunchbang has a script-based alternate install method that might be ideal for your situation (installing on 10 computers at once): [http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation](http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation)

---

