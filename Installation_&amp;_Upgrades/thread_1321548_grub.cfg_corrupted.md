---
title: "grub.cfg corrupted"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by zi99y on 2009-11-10
I have been having problems with Karmic, firstly I installed on my desktop PC using WUBI. After rebooting and completing the installation, I was greeted by the grub> prompt with no clue as to why.

At this point I ran a full memtest and media test which both came back fine. I retried the install from Windows and it all went fine, and I have been using it for a week now.

However, last night I was working and decided to install some packages, the last one being DWM, which required me to relogin to use it, when I logged out the keyboard and mouse had frozen, alt+prtscr+k restarted xorg, but would not recover the input devices. At this point I ssh'd in from another pc and ran shutdown remotely. The screen on the desktop machine then went haywire in a flashy ascii pattern. Since then when I boot up I am greeted with the grub prompt again.

When I cat /boot/grub/grub.cfg I just see gibberish so it seems that file and maybe more have become corrupt. I have attempted to boot manually [using this method]("http://grub.enbug.org/Manual#head-4ec5b739d92a8fa63f77205a4a9818a094d943bb") but it just gets half way through boot up and hangs.

Suffice to say this is very inconvenient as I use this machine for work, and now I'm relegated to using Windows Fister again.

Primarily I would like to recover my home partition from the loopback filesystem, can anyone help me with this?

thanks,

Gez

---

