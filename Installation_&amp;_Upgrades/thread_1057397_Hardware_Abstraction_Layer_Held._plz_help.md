---
title: "Hardware Abstraction Layer Held. plz help"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by Themaverick on 2009-02-01
I'm kinda a noob when it comes to entering commands into the terminal and such. but does any know the actual commands to enter the noauto option on each smbfs entry in /etc/fstab to get rid of the Hal booting problem.

This is the quotes i read from someone else

> yes, adding the noauto option on each smbfs entry in /etc/fstab does seem to avoid the hald hang problem in startup. Then, just using the sudo mount /mnt/share command to manually mount it with the options specified in the /etc/fstab also seems to work. Of course, I'm sure we all regard this as just a temporary work-around for use with the Dapper Beta. Is anybody aware of a fix to the smbfs that is work in progress? Will it be ready for the Dapper final release?

---

