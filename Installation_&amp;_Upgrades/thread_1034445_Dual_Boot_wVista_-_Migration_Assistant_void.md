---
title: "Dual Boot w/Vista - Migration Assistant void"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by Dragon Smaug on 2009-01-08
I am attempting to install Ubuntu desktop 8.04 in a Dual Boot configuration with Windows Vista.  I am following a set of directions, the 3rd page of which is here [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3) .

On this third page you will note how it says "*In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)". *"

When I followed the directions and began installing it, on the "Ready to Install" screen, under Migration Assistant appeared nothing.  Fearfull, I cancelled the installation.  Was I overreacting?  If Ubuntu not realizing that Vista was there is a problem, what could be causing it?

---

### Post by Pumalite on 2009-01-08
Did you allocate space for Ubuntu with the Vista partitioner first?
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by mikewhatever on 2009-01-08
> **Dragon Smaug said:**
> 
On this third page you will note how it says "[I]In the summary under Migrate Assistant, it should say "Windows Vista/Longhorn (loader)".

No, in fact, it says 'There were no users or OSs sutable for importing from'. The loader part refers to the bootloader menu, which you see after the installation is done and the computer is rebooted. I'd advise backing up your personal files, and reading the guide a couple more times to get familiar with. If you need more help, do not hesitate to ask.

---

### Post by Dragon Smaug on 2009-01-08
Yes. I shrunk one of the Vista partitions.  There is now almost 30 GB of unallocated space.

---

### Post by Dragon Smaug on 2009-01-08
It's a freshly installed Vista, so I have nothing to backup.  Really, my computer just crashed and this is a new hard drive.  I thought I'll turn this to my advantage and make it an opportunity to go linux.  I just want to make sure that going ahead with the installation would still have worked and not messed Vista up.  Are you saying that it is OK and I have nothing to worry about?

---

### Post by mikewhatever on 2009-01-08
> **Dragon Smaug said:**
> It's a freshly installed Vista, so I have nothing to backup.  Really, my computer just crashed and this is a new hard drive.  I thought I'll turn this to my advantage and make it an opportunity to go linux.  I just want to make sure that going ahead with the installation would still have worked and not messed Vista up.  Are you saying that it is OK and I have nothing to worry about?

That may explain why there is nothing to import. The importer usually offers to import bookmarks, email settings, and such stuff. I think you should go on, just be careful.

---

### Post by Pumalite on 2009-01-08
I hope you formatted those 30 GB. Ubuntu cannot be installed in unallocated space. Another solution is to go 'Manual'.

---

### Post by Dragon Smaug on 2009-01-08
If I format it in Vista, won't it become considered part of Vista? How do I format it without that occuring?

---

### Post by mikewhatever on 2009-01-09
The installer will format the unallocated space for you, just stick with the way outlined in the guide.

---

### Post by qQChtIhpk1 on 2009-01-10
i have the same problem installing U 8.1.  The Migration Assistant canNOT be bypassed because the window is too big for the screen.  The screen resolution is 800x600.  This prevents me from seeing and clicking the OK or whatever icon would move to the next step in the installation process. i tried enter, but nothing happens, as installation has apparently stopped (hard disk and install disk not being accessed).  i tried to resize the window without success.
Many installs, but no success so far.

i have nothing to migrate.  How do i get past this screen?

Thanks!

FOUND THE ANSWER!  Use the "Character Installer" when selecting the install option for U.  It does not even have a Migration Assistant.  First working Ubuntu 8.1 install!  i must have tried 15 times.  Best Wishes to all!

Chazbo

---

