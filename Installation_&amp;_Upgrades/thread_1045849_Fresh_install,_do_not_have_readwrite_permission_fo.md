---
title: "Fresh install, do not have read/write permission for /media partitions"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by bg1256 on 2009-01-20
Tonight, I did a fresh install of Hardy to completely eliminate Windows from my machine.

I have two HDDs, and I set up the partitions like so:

First HDD:
1st partition: root
2nd partition: /media/Multimedia

Second HDD:
1st partition: /home
2nd partition: /media/Documents
3rd partition: swap


Ubuntu recognizes and mounts both /media partitions; however, I (the only user) do not have read/write permission. When I right click -> properties -> permissions, it shows root as the user.

If I launch, gksudo nautilus, I can change the permission of the entire partition, but each time I create a new folder, I do not have access without re-launching nautilus as root. 

Is there a solution to this? I want to have read/write access as a normal user, not superuser...

---

### Post by sowelie on 2009-01-20
Do a chown -R on the partitions to either yourself, or to a group you belong to.

ex: sudo chwon -R youruser:yourgroup /media.

---

### Post by bg1256 on 2009-01-20
Thanks for your quick reply, but that did not work for me.

---

### Post by bg1256 on 2009-01-20
Actually, it worked halfway.

It worked for /media/Multimedia

However, I still do not have read/write access to /media/Documents

---

### Post by bg1256 on 2009-01-20
Well, back to square one. After a reboot, I can't access either partition... And I mean I can't access them at all as a normal user.

---

### Post by bg1256 on 2009-01-20
Now, to complicate it one step further:

Running chown gives me read/write access to the folders, but only if I type /media/Multimedia or Documents into the address bar of Nautilus. 

Clicking them from -> Places won't allow me to access them. I'm totally confused here.

---

### Post by pastalavista on 2009-01-20
Try rebooting in recovery mode and select the repair option. Then drop to the root terminal and try the chown commands again. Also check [this page]("http://www.psychocats.net/ubuntu/fixsudo")

edit: I just noticed you have two /media partitions ! Which one do your removable drives show up in?

---

### Post by bg1256 on 2009-01-20
I've taken the long way around, but I solved it by deleting the partitions, creating new partitions with gparted, and following the guide here:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

