---
title: "Install of 9.04 on 2 PCs, different results"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by DenysT on 2009-04-23
Ok, this really has to do with networking but I installed 9.04 on an older Compaq laptop and clean installed 9.04 on custom built PC in which I had royally messed up 8.10. (Hey it was my learning system for Ubuntu) :P

Still I had to manually configure the network so that Samba shares were available and Windows could access them. Also so I could browse the network with out getting that dreaded message "Failed to retrieve available shares" or whatever it is. (I did this by *sudo gedit /etc/samba/smb.conf* and changing just two lines before I accessed the network.

1. Change the workgroup = myworkgroupname
2. Uncomment name resolve order = lmhosts hosts wins bcast

Still I got different results on each machine, the laptop only shows the Windows Workgroup icon and I have to drill down to the computers but at least I can get all the shares. The PC shows the other computers plus the Windows Workgroup! Damifino.

Now as matter of installing why doesn't Ubuntu install ask for this information during installation like Windows does (don't have a hissy fit about this please)? It seems to me that the biggest failing right now is the lack of info needed for setting up the network causes a lot of problems after install and should not be that way. Just my 2 cents folks.

---

