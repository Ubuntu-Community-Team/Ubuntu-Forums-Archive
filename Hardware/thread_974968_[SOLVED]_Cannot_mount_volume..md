---
title: "[SOLVED] Cannot mount volume."
date: 2008-11-08
forum: Hardware
---

### Post by Joner1 on 2008-11-08
Dear all, 

I'm a new user of ubuntu 8.10 and I want to go on my exeternal harddisk to get my files. This harddisk I had under Windows XP - ntfs formated. The following error message appears:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Can somebody help me to solve my problem?

regards
Joner1

---

### Post by Airfoot on 2008-11-08
Plug it back in to windows xp or vista and do a safe hardware eject (right click the taskbar icon that appears when you connect the drive, then select safely remove hardware(or device)), this should allow you to mount the volume.

---

### Post by NathanDC on 2008-11-08
I had the same problem!!! God I searched for ways to mount the damn thing and now it works!! Thanks..!

---

### Post by Airfoot on 2008-11-12
Also, if you are trying to mount an internal disk that is NTFS or FAT that has a windows OS you will not be able to mount it if you don't do a proper shut down(start menu > shut down, don't hold the power button).

---

### Post by hoggson on 2008-11-13
Is there any possible way around this?  I am currently trying to help someone I have converted from Vista to Ubuntu and they have installed it over the Windows partition, and now cannot access their NTFS drive with their documents and backups on. :(  Can you not force mount or something in partition manager (gparted)?

OK, good... found the answer.  Edit /etc/fstab to force mount it @ boot.  :)

---

### Post by Airfoot on 2008-11-15
To my knowledge there is no way around it, however you can do this at any windows machine (that is NT, Xp, or Vista) so you can do it at school or a library, all you have to do is plug it in, windows will automatically detect it, and safe remove.

---

### Post by Joner1 on 2008-11-17
> **Airfoot said:**
> Plug it back in to windows xp or vista and do a safe hardware eject (right click the taskbar icon that appears when you connect the drive, then select safely remove hardware(or device)), this should allow you to mount the volume.

Thanks a lot - great it works now. I mounted XP and safely removed it. Now it's now problem anymore and I'm happy!!!

thanks
Joner1:):):)

---

