---
title: "8,10 32-bit Regular Install on ZEN Vision M 60gb"
date: 2008-11-16
forum: General Help
---

### Post by octaedro7 on 2008-11-16
Edit2: I solved myself. Disk Manager kept a backup of fstab. I booted into safe mode and restored the original fstab. After rebooting all problems gone away. Apparently I should have restarted the system after installing Disk Manager.
Hope all my stupidity serves somebody :lolflag:! 

Hi,
I've done a regular install of Ubuntu 8.10 32-bits on my Crestive Zen Vision M. I created 2 ext3, 1 swap and 1 fat32 partition. The wizard warned me that I needed to provide a mount point for the fat32 partition otherwise it would not be available. I chose the mount point offered (/media/windows). Everything went fine but I'm not able to see or mount this fat32 partition. I installed Disk Manager. When I launch the application a popup asks if I want to remove unknown devices from the configuration file (see attached screencap)

Is there a way to solve this?

Thanks in advance

Edit:  I was confused and not seeing something that was right in front of my nose. I found the "windows" folder. I thought "ok, i'm done, let's transfer some music from an external hard drive to it". The drive was listed in Nautilus but when I tried to open it the system complained that the drive cannot be mounted because of a faulty unmount (is what I remember of the popup). Stupidly I thought that it might be related to the message thrown by disk manager, so I clicked ok to remove those entries.  After that the message of unable to mount kept popping up. So I restarted the pc and after passing the login window, Ubuntu complained about not finding the home folder.
So I am more screwed up than in the beginning.

I repeat the question, is there a way to revert this?

Thanks again in advance

---

