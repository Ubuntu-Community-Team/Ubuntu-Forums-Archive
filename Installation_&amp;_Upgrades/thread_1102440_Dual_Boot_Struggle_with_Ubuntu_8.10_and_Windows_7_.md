---
title: "Dual Boot Struggle with Ubuntu 8.10 and Windows 7 Beta (boot loader problem)"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by pablorpm on 2009-03-21
So after much struggle I don't know what to do next.  I am currently running Windows 7 Beta and am trying to install Ubuntu 8.10 inside windows.  I have already tried both downloading and installing through the wubi.exe file as well as installing with the actual ISO (desktop-amd64.iso).  They both install the exact same way, but after rebooting my system I am not prompted with the Windows Boot Loader but launched directly into Windows 7.

My system is set up with two physical hard drives with Windows entirely on one drive.  I have partitioned the second to 40 GB for just Ubuntu.  I have had trouble trying to Uninstall whatever portion of Ubuntu I have installed each time I start from scratch so I end up deleting the Ubuntu volume and repartitioning/reformatting each time.  

I have referenced both of the following threads which have deemed very useful but still can't figure it out.

[http://ubuntuforums.org/showthread.php?t=1098906&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=1098906&highlight=dual+boot)

[http://ubuntuforums.org/showthread.php?t=983302](http://ubuntuforums.org/showthread.php?t=983302)


I have followed the steps of the 2nd thread and am now successful in viewing the Windows Boot Loader and launch, but when selecting the Ubuntu it gives an error saying:

"Windows failed to start.  A recent hardware or software change might be the cause.

File   \NST\nst_grub.mbr
Info   The selected entry could not be loaded because the application is missiong or corrupt"

In the first thread mentioned above, the user ended by saying he/she placed the menu.lst file in the NST folder but I didn't know where this file existed.  Any thoughts?  Suggestions?

Thanks in advance!

---

### Post by awechris on 2009-03-21
> **pablorpm said:**
> So after much struggle I don't know what to do next.  I am currently running Windows 7 Beta and am trying to install Ubuntu 8.10 inside windows.  I have already tried both downloading and installing through the wubi.exe file as well as installing with the actual ISO (desktop-amd64.iso).  They both install the exact same way, but after rebooting my system I am not prompted with the Windows Boot Loader but launched directly into Windows 7.

My system is set up with two physical hard drives with Windows entirely on one drive.  I have partitioned the second to 40 GB for just Ubuntu.  I have had trouble trying to Uninstall whatever portion of Ubuntu I have installed each time I start from scratch so I end up deleting the Ubuntu volume and repartitioning/reformatting each time.  

I have referenced both of the following threads which have deemed very useful but still can't figure it out.

[http://ubuntuforums.org/showthread.php?t=1098906&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=1098906&highlight=dual+boot)

[http://ubuntuforums.org/showthread.php?t=983302](http://ubuntuforums.org/showthread.php?t=983302)


I have followed the steps of the 2nd thread and am now successful in viewing the Windows Boot Loader and launch, but when selecting the Ubuntu it gives an error saying:

"Windows failed to start.  A recent hardware or software change might be the cause.

File   \NST\nst_grub.mbr
Info   The selected entry could not be loaded because the application is missiong or corrupt"

In the first thread mentioned above, the user ended by saying he/she placed the menu.lst file in the NST folder but I didn't know where this file existed.  Any thoughts?  Suggestions?

Thanks in advance!

Hello there Pablo. Check this link, it's a step-by-step guide :)
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5")

---

