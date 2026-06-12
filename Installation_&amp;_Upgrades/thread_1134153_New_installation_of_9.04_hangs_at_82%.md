---
title: "New installation of 9.04 hangs at 82%"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by ghostu on 2009-04-23
Hi, my new installation of Jaunty is hanging at 82% "Configuring Apt - Scanning the security updates repository...".  I guess this is because it is trying to download the latest updates and due to the increased traffic, it is just hanging.  I also read a way around this is to unplug the ethernet cable, but since my installation has been already running, I don't think this will help.

Any idea what to do now?  Is it safe to just do a hard shutdown of my system and redo installation (during the initial installation I was modifying my partition table, so I don't know if this will need to be redone)?  I do a hard shutdown and redo the install, any pointers to get past this 82% mark?

Thanks!
ghost

---

### Post by wpshooter on 2009-04-23
May not be the most desirable solution but my recommendation would be to WAIT awhile before attempting to download and install 9.04 until after the big rush is over with !!!

---

### Post by JK3mp on 2009-04-23
> **wpshooter said:**
> May not be the most desirable solution but my recommendation would be to WAIT awhile before attempting to download and install 9.04 until after the big rush is over with !!!

Im downloading it right now. But i think im just gonna put it on a diffrent partition and test it for a while. Once everything works and they get some  updates flowing, then i'll install and use it as primary.

---

### Post by Garrovick on 2009-04-23
Mine hung up at 82% for several really long minutes. I just left it alone and it started up again.

---

### Post by ghostu on 2009-04-23
Mine is still stuck an hour later.  :(

Should I just continue to wait?

---

### Post by KennyUnger on 2009-04-28
My install too seems to be hanging at 82% (Configuring apt - Scanning the mirror...) I'm installing on an Asus F8SP-X1 Laptop. Configured as dual boot with EXT4 partition. Any thoughts?

---

### Post by ghostu on 2009-04-28
> **KennyUnger said:**
> My install too seems to be hanging at 82% (Configuring apt - Scanning the mirror...) I'm installing on an Asus F8SP-X1 Laptop. Configured as dual boot with EXT4 partition. Any thoughts?

I fixed my issue by doing the installation over.  I first booted to the LiveCD and got to the desktop.  After that, I turned off the wired network (just disable the network by right clicking on the network icon).  Once that was done, install 9.04 by clicking on the icon on your desktop.  You should be good to go.

---

### Post by KennyUnger on 2009-04-28
Yeah. I was just getting ready to post that I tried the install again without going to the desktop first (bypassing all network activity) and it installed without a hitch. Thanks though!

---

### Post by ghostu on 2009-04-28
Glad that it worked out!

---

