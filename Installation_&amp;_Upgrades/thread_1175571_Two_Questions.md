---
title: "Two Questions:"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by ron3090 on 2009-06-01
First, I thought I had everything upgraded in my system. I do regular [FONT="Courier New"]apt-get upgrade[/FONT]s, and thus assumed I had the latest distro of xubuntu. But when checking out my system info today, I found it says I still have Hardy Heron. What's going on? I thought the upgrades kept my system up-to-date.

Second, I found a 10GB hard drive, and had an idea it would be neat to install Windows on that, to run what Wine can't. Before I install it, though, I need to know if viruses I download on linux can affect windows, and vice versa. It's not the executables I'm worried too much about, it's the viruses you can get from just surfing the internet. *Should* I be worried?

---

### Post by raymondh on 2009-06-01
> **ron3090 said:**
> First, I thought I had everything upgraded in my system. I do regular [FONT="Courier New"]apt-get upgrade[/FONT]s, and thus assumed I had the latest distro of xubuntu. But when checking out my system info today, I found it says I still have Hardy Heron. What's going on? I thought the upgrades kept my system up-to-date.

Second, I found a 10GB hard drive, and had an idea it would be neat to install Windows on that, to run what Wine can't. Before I install it, though, I need to know if viruses I download on linux can affect windows, and vice versa. It's not the executables I'm worried too much about, it's the viruses you can get from just surfing the internet. *Should* I be worried?

Hello,

To upgrade distributions, the command is dist-upgrade.  Sudo apt-get upgrade will only upgrade the apps and system files you have in your current distribution. I know, it does sound like update as well.

If you do plan to upgrade distributions, you will need to go 8.04 > 8.10 > 9.04.  Check you sources list to ensure that you have distribution upgrades enabled ... and you will be notified by the update manager. A lot of folks (me included) will prefer a clean install.  However, some guys have reported success in a network upgrade of distributions.  YMMV.  As you know by now, back-up your files.

As a side note, try the liveCD of distribution you want to make sure your hardware will work.  It usually is a good indicator.

Viruses will affect your windows install/files.

Regards,

---

### Post by leandromartinez98 on 2009-06-01
> **ron3090 said:**
> First, I thought I had everything upgraded in my system. I do regular [FONT="Courier New"]apt-get upgrade[/FONT]s, and thus assumed I had the latest distro of xubuntu. But when checking out my system info today, I found it says I still have Hardy Heron. What's going on? I thought the upgrades kept my system up-to-date.

That procedure applies updates to the current version of the packages
of your system, but it will not update your distribution. By the way,
If you don't have issues with Hardy, stick with it and keep it that
way. If you want to fully upgrade your distribution (from Hardy to
Intrepid, and thereon) you have to do something like this (twice):


[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

first from Hardy do Intrepid, then from Intrepid to Jaunty. But really,
unless you have some important reason to do so, don't do it, Hardy
is the Long Term Support version. You will be able to update it directly
to the next LTS version in 2011.

---

### Post by mcduck on 2009-06-01
> **raymondhenson said:**
> Hello,

To upgrade distributions, the command is dist-upgrade.  Sudo apt-get upgrade will only upgrade the apps and system files you have in your current distribution. I know, it does sound like update as well.

If you do plan to upgrade distributions, you will need to go 8.04 > 8.10 > 9.04.  Check you sources list to ensure that you have distribution upgrades enabled ... and you will be notified by the update manager. A lot of folks (me included) will prefer a clean install.  However, some guys have reported success in a network upgrade of distributions.  YMMV.  As you know by now, back-up your files.

As a side note, try the liveCD of distribution you want to make sure your hardware will work.  It usually is a good indicator.

Viruses will affect your windows install/files.

Regards,

"dist-upgrade" won't upgrade to next distribution release either, it's pretty much the same as "upgrade" with a bit more options for solving dependencies.

- "update" updates information about available packages.
- "upgrade" installs available new package versions, plus possible new required packages.
- "dist-upgrade" installs available new package versions, plus new required packages, but can also remove installed packages if that's required to solve the dependencies.

To actually upgrade to new distribution release with apt-get you'll have to first edit your sources.list to use repositories for the new release, and after that "apt-get update" and "apt-get dist-upgrade" will do the job.

For doing command-line release upgrades it's best to use the "**do-release-upgrade**"-command.

---

### Post by Therion on 2009-06-01
Up*dates* are one thing, up*grades* are another.

---

### Post by ron3090 on 2009-06-01
Thanks all for the responses! I think I'll just stick with Hardy, then.

However, I'm now having trouble installing Windows on the 10gb slave drive. Linux does not detect the drive, although I can see it in the startup BIOS. When I tried running the Windows installer from the Windows ME CD, it said there weren't enough drive letters available. How do I go about installing Windows, then?

---

