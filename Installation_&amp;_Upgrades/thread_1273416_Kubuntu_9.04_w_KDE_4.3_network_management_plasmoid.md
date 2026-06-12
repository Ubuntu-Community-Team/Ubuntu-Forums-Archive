---
title: "Kubuntu 9.04 w/ KDE 4.3 network management plasmoid issues"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by at165db on 2009-09-23
My desktop was installed with Kubuntu 8.10 and KDE 4.1.  I upgraded to the backported KDE 4.2 at some point.  When Kubuntu 9.04 shipped, I upgraded to that (also KDE 4.2) and had no issues.

I just followed the kubuntu.org directions to upgrade my 9.04 with KDE 4.3.

It had issues with the plasma-widget-network-manager, but nothing else.  I removed that package, re-ran
sudo apt-get update
sudo apt-get dist-upgrade
and it installed\upgraded a bunch of packages.  Everything seems to be working, but I have no network management plasmoid.  I know plasma-widget-network-manager is not supported anymore.  I have a VM image that was a fresh 9.04 install, and it did the KDE upgrade fine.  It also let me add a Network Managemnt plasmoid that is new/different that the brokenish one that KDE 4.2 had.

Why dosen't my desktop have the new network manager plasmoid?  How can I manually install or add it to the system tray like it is on my VMWare install?

Thanks!

---

### Post by rreese6 on 2009-09-23
Dist-upgrade will not reinstall the package. it only upgrades what you already have installed or lack to complete the upgrade.
just reinstall plasma-widget-network-manager through Synaptic or by using "sudo apt-get install plasma-widget-network-manager" in a terminal.
I am not too sure about the last command, since I am currently on a P2 400mhz machine running 8.04 Xubuntu.
Let me know how it works out.

---

### Post by at165db on 2009-09-23
The plasma-widget-network-manager is not supposed to be used in KDE 4.3.  Or so my vmware image install told me when it did the upgrade. There is a replacement thing in the system tray now, and not in the normal widget space. It works fine on my vm image, but is missing on my desktop.

---

### Post by rreese6 on 2009-09-23
The replacement thing in the systray is most likely knetworkmanager (the older version).
From what I have been able to find is that the Network system in KDE4.3 is still in alpha stage and buggy.
Some others have had success by installing the older knetworkmanager.
Give that a shot and see what happens.
is your connection wired or wireless?

Sorry about the replies delays...work keeps getting in my way :)

---

### Post by at165db on 2009-09-23
Thanks,
So I can confirm it is in fact knetworkmanager that I was looking for.  For some reason, on my vmware install (32 bit also) knetworkmanager is new, and fits in with KDE 4.  I'm not sure why knetworkmanager is different between my two systems.

On my desktop, knetworkmanager is now in my system tray, but has the old KDE 3.5 look and feel.  It is at least working for what I need it to do however, so that is a plus.

---

### Post by Syniurge on 2009-09-25
Hi,

Why isn't the plasmoid supported anymore ? :confused:
It was more convenient than the autostarting systray, since you could remove it.
The systray can't even be closed unless you terminate its process..

Is there a developers discussion somewhere that could shed some light ?

---

