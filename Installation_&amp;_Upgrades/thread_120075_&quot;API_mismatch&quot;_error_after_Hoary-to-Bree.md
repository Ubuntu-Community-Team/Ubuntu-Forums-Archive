---
title: "&quot;API mismatch&quot; error after Hoary-to-Breezy upgrade"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by peruvianllama on 2006-01-20
I recently attempted to upgrade from Hoary to Breezy by using [the apt-get based guide at UbuntuGuide.org]("http://ubuntuguide.org/#upgradehoarytobreezy"). 

After letting 'sudo apt-get dist-upgrade' run its course, I rebooted, and was greeted with the error "Error: API mismatch: the NVIDIA kernel module is version 1.0.7174, but this X module is version 1.0.7667." I Google'd extensively for the error, and tried solving the problem myself in a couple different ways:

1) I tried uninstalling/reinstalling nvidia-glx and nvidia-settings per [the UbuntuGuide.org guide]("http://ubuntuguide.org/#installnvidiadriver")
2) Based on a Google result, I tried: $ sudo dpkg-reconfigure xserver-xorg
and accepted all of the default options, giving input only where I knew exactly what I was doing

After both of these steps I ran: $ sudo /etc/init.d/gdm restart
however the error has remained.

This is all the more frustrating because this is a dual-boot machine with Windows, and my XP installation recently gave out on me; so I had been using Ubuntu to make sure everything on my Windows partitions was properly backed up before re-installing. I guess I should have left well enough alone, and waited before trying to upgrade Ubuntu.

Alas - any help would be greatly appreciated. I don't mind reading man pages, or forums, or what have you, so even pointing me in the right direction could be helpful. I don't have any experience mucking about with the kernel however - this is the first time I've tried to upgrade from one version to another.

Cheers, and thanks in advance to any potential helpers!

---

