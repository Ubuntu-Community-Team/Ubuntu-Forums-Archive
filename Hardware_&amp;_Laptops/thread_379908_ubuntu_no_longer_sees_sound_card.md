---
title: "ubuntu no longer sees sound card"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by jkeidel on 2007-03-09
hi all

I have an inspiron 600m set up to dual-boot XP and ubuntu.  for a long time sound worked fine.  now, all programs (e.g., mplayer, xmms etc.) claim that no sound card is installed.  however, sound works fine in windows.  the sound card is an intel 8280, according to the ubuntu device manager.

I should note that simultaneous with the loss of sound two other things happened with my computer:

1) the mount options for the windows and shared vfat partitions were changed so that they could not be accessed (umask was changed)--I changed that back in /etc/fstab easily enough.

2) when I click the system->administration drop-down menu, there are now only 5 options.  no synaptic, no anything except for:

device manager
network tools
printing
system log
system monitor

I have not been able to fix this.

thanks in advance for any and all help you can offer!

---

