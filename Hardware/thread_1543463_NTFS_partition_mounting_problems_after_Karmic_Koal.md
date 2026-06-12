---
title: "NTFS partition mounting problems after Karmic Koala boot in Windows Standby"
date: 2010-08-01
forum: Hardware
---

### Post by Holli3 on 2010-08-01
Hej,

The trouble began when I borrowed my laptop to a friend of mine. She  used the Windows - Installation on my NTFS partition, that I need for my  job.
Instead of shutting Windows down after using it, she just closed the laptop so it went only down to Standby, what I didn't know.
Well, as usual I chose Karmic Koala in GRUB, when I started my computer the next time.

I couldn't access the NTFS partition from Karmic Koala which I use to mount automatically with the fstab line

/dev/sda1 /media/System ntfs-3g auto,users,umask=000 0 0

So the next thing I did was to reboot Windows and shut it down  completely. After a reboot of Karmic Koala, the error still exists.

I checked fstab, but the entry hadn't changed, so I simply tried

sudo su
mount /dev/sda1

and got the message "The Resource is temorarily not available."

There is still an entry in the Locations menu for the partition System, but clicking on it results in the message:

"Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged"

I changed the entry in System - Administration - Users and Groups, to  allow all users to use FUSE but the error message is still there.


Finally trying to access email on this NTFS partition using Mozilla Thunderbird from Karmic Koala ends in the message:
"Thunderbird is already running but not responding" allthough there is in fact no thunderbird process running.


I only can assume, that starting Ubuntu 9.10 while Windows was in  standby mode produced an "in use" entry somewhere which was not deleted  when I shut down Windows thereafter.

Does anyone know where I could find such an entry and how to change it  manually? Or do you have other ideas what could have happened?

Maybe I should add that Windows runs without any problems. So I suppose,  that the error must be solved from the Linux side of my computer.

My OS are
Ubuntu 9.10 Karmic Koala and
Windows XP Professional

Just tell me if you need further info to help me (this is my first entry to an Ubuntu forum)

Thanks a lot in advance!

PS: If this problem has already been solved somewhere, I didn't find it. Sorry.

---

### Post by efflandt on 2010-08-01
I suspect it went into hibernate instead of suspend when the lid was closed.  You might try booting Windows, closing the lid and waiting until it powers down, the boot into Windows so it resumes.  That might clear up the issue.

Otherwise, have Windows check and fix its partition when it boots (maybe Linux thinks the ntfs partion is not clean).

---

### Post by Holli3 on 2010-08-01
I'm sorry, but your suggestions didn't solve the problem. Do you have other ideas?

---

