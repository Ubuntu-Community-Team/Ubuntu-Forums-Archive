---
title: "Can not login: wrong passwd file"
date: 2008-09-12
forum: General Help
---

### Post by registerme on 2008-09-12
It's my bad, I copied a different passwd file from another computer to my ubuntu's /etc/passwd, now I can not login. Is there a way to recover it?

---

### Post by aysiu on 2008-09-12
Does everything else work? It's just the user who can't log in?

---

### Post by chrisccoulson on 2008-09-12
If you're lucky, then you might find a backup of your old one at /var/backups/passwd.bak. /etc/passwd gets backed up by a daily cron job :)

You just need to hope that cron job hasn't executed since you copied the different file from the other computer.

---

### Post by aysiu on 2008-09-12
> **chrisccoulson said:**
> If you're lucky, then you might find a backup of your old one at /var/backups/passwd.bak. /etc/passwd gets backed up by a daily cron job :)

You just need to hope that cron job hasn't executed since you copied the different file from the other computer.
Cool. I never knew that.

It also keeps a backup of the /etc/shadow file (/var/backups/shadow.bak)

---

### Post by registerme on 2008-09-12
> **aysiu said:**
> Does everything else work? It's just the user who can't log in?

I restarted ubuntu since the passwd file was changed, and of course nothing worked since I can not login at all.

---

### Post by registerme on 2008-09-12
> **chrisccoulson said:**
> If you're lucky, then you might find a backup of your old one at /var/backups/passwd.bak. /etc/passwd gets backed up by a daily cron job :)

You just need to hope that cron job hasn't executed since you copied the different file from the other computer.

I am pretty sure the cron job hasn't executed since I restarted immediately after the passwd file was copied. I had the old one backed up by myself, the problem was that I just could not login at all to do anything.

---

### Post by todak on 2008-09-12
Use a live CD to hunt for it, then copy it over.

---

### Post by registerme on 2008-09-16
> **todak said:**
> Use a live CD to hunt for it, then copy it over.

What kind of "live CD"? Would a ubuntu install DVD work? I tried but since I am using VMWare, it would not boot from the DVD/image.

---

### Post by chrisccoulson on 2008-09-16
> **registerme said:**
> I am pretty sure the cron job hasn't executed since I restarted immediately after the passwd file was copied. I had the old one backed up by myself, the problem was that I just could not login at all to do anything.

If you're sure that the cron job hasn't executed, then you should be able to boot to recovery mode, and then do the following:
```
cp /var/backups/passwd.bak /etc/passwd
```

If you can't boot in to recovery mode, then boot the Ubuntu Live CD, mount your root filesystem and restore the backup. It might be safer this way as there is no chance of the cron job running (I can't remember if cron runs in recovery mode). You can do this by doing the following from the live CD environment:
```
sudo mkdir /target
sudo mount -t ext3 /dev/sdxx /target
sudo cp /target/var/backups/passwd.bak /target/etc/passwd
sudo reboot
```
...where */dev/sdxx* is the device node for your root filesystem (eg, /dev/sda1).

Hope that helps

---

### Post by mike2357 on 2008-09-16
If you are copying old files from /var/backups, there are two files that need to be copied:  passwd.bak and shadow.bak.  The actual passwords are in shadow.bak.

The commands are:

cd /var/backups
sudo cp passwd.bak /etc/passwd
sudo cp shadow.bak /etc/shadow

If you had recently made changes to groups, or added or deleted groups, you'd also need to:

sudp cp group.bak /etc/group

---

### Post by Iowan on 2008-09-16
I've used [tomsrtbt]("http://www.toms.net/rb/") to flush passwords from a used linux system I got at surplus.

---

### Post by registerme on 2008-09-16
Boot into recovery mode works. I copied the passwd.bak file back and it worked. There is files like 'passwd-', 'group-' and 'shadow-' there, what are these files?

tomsrtbt looks interesting, but the computer does not have a floppy disk. Is there a floppy image utility around?

---

### Post by mike2357 on 2008-09-17
The "man" pages for passwd, group and shadow have a lot of good information.  The commands:

man 5 passwd
man 5 group
man 5 shadow

---

