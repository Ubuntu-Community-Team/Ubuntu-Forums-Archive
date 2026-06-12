---
title: "Unstable Installer"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by isilmeraumo on 2006-01-03
Ok, I first tried Ubuntu way back with version 5.02 or so, forget now, and it was the easiest thing to install.   It just worked.  15 minutes and you had a fully installed Linux system.  I'm trying to do a new install, as back then I was more interested in tinkering so I chose Gentoo, however I am hitting a rediculously unstable installer, it doesn't just work.  It took 3 install attempts to get a partly working system.  The first one the base installer would fail, so I repartitioned, formatted and tried again.  The second time it installed ok, or so I thought until I rebooted and I no longer had a volume group so that failed.  I tried it for a third time, this time it installed and when it rebooted it had a volume group however it is hanging at the Installing packages ncurses screen.  What is with this?  I decided to use Ubuntu because I no longer wanted to deal with a multi-day install process as is what Gentoo requires due to package build times, however, at least there it just works.  I am very frustrated as you can see, so if anyone has any ideas as to why this installer fails so miserably and maybe why there are so many issues with the 5.10 installer, they'd be greatly appreciated.  This does not bode well for Ubuntu when the forums are littered with installer problems and it seems its extremely unstable.

---

### Post by isilmeraumo on 2006-01-03
Well, I am stuck.  I believe the issue with the configuration during firstrboot is that my work is blocking apt-get or just dropping the packets.  Is there anyway around this?  I do not know of any proxy server as I have never needed to find out since Gentoo's emerge works fine.  I believe the network just ignores anything thats not ftp or http going in or out of the external gateway and since emerge uses wget which makes use of http/ftp it never had a problem.  Is there any way to get apt-get to use wget or at least use http/ftp as its means of acquiring packages?

---

### Post by isilmeraumo on 2006-01-03
Ok, apt-get is fine, the Ubuntu Configuration was just not able to get the packages it wanted for some unknown reason as I killed the apt-get processes until the configuration script started aptitude which worked fine however I am unsure as to what packages it was trying to download and whether or not I will need them.

---

