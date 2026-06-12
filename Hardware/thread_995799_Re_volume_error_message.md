---
title: "Re volume error message"
date: 2008-11-28
forum: Hardware
---

### Post by patrick alfonso on 2008-11-28
Hello. I am new to this site. I started using Linux via Linux Ubuntu 7.1. I am now using Linux Ubuntu 8.10. I have a recent problem. I have a compaq cq40 laptop with a 160gb harddisk drive. I alternately use windows xp and linux ubuntu via dual boot. In windows I made two partitions of my hard disk. In Linux I constructed a 20gb partition for my linux os. In linux, whenever I try to mount the other partitions , I get the follwing message:

Unable to mount the volume 76.2 Gb media.

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Mount point cannot contain the following characters:newline, G_DIR_SEPARATOR(usually /)
  
What do I do?

Patrick

---

### Post by RumorsOfWar on 2008-11-28
It may just be that Windows was shut down incorrectly. I don't know why, but I can't access my Windows partition if I had to power down from a bsod. 
If that doesn't help, then you may need to run from windows command " chkdsk C:/ r ". ( It may need to reboot to run the repair during startup.)
   I can't say why this sometimes works, but it fixed that problem for me when I first dual booted.

---

