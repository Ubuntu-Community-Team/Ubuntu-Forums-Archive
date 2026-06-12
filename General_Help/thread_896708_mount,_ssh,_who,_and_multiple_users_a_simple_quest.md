---
title: "mount, ssh, who, and multiple users: a simple question."
date: 2008-08-21
forum: General Help
---

### Post by Drostie on 2008-08-21
Hi. I've got a remote computer running Ubuntu, which I can log into with ssh. One of its drives is encrypted, and holds useful files that I'll probably transfer with sftp. However, there is a catch: That computer also has another user on it, and I am not okay with him having access to my files. Also, there's a bunch of files, so I can't just check his login status with "who" and then transfer away. (Which I might not have been able to do anyway -- he has a tendency to turn off the computer when he's not using it.)

Since he's not technically apt, I think I can retrieve my files, so long as *my* "mount" command does not display an icon on *his* desktop. But I don't know whether it does or not. Do any of you know more details about how gnome displays mounted drives, and ways to stop it from doing so? Is it sufficient that we have different login accounts? Can I mount to some place other than /media to get around the autodisplay?

Thanks in advance.

---

### Post by Drostie on 2008-08-23
(Just in case someone googles this thread or something, I never got an answer to my question. So I did the next best thing: used chmod to make myself the only one able to read/write/perform directory listings. That's not a *great* strategy, but it's better than nothing. If gnome just automatically creates a new mount point on the desktop whenever a new device appears in /media or whenever mount executes for some user, that's a bit crap, but at least they'll have to google chmod and sudo and look up the sudo password first. Probably, for the sudo password, they'll call me, and I can umount the drive via ssh. It's not a great strategy, certainly not foolproof, but it's *something*.)

---

