---
title: "Samba share not writable from Windows"
date: 2008-11-30
forum: General Help
---

### Post by Amaroku on 2008-11-30
and I think I know the problem, too.

From my /etc/samba/smb.conf :
```
[media]
        comment = media files
        path = /home/media
        writeable = yes
        browseable = yes
        valid users = chris, jon, jordan, ron
        write list = jordan, jon, chris, ron
```

and the permissions of the media share are:
```
drwxrwxr-x  1 root   media  20480 2008-11-30 20:18 media

```

The Windows computer hostname is doom.
From my /var/log/samba/log.doom
```
doom (10.0.0.5) connect to service media initially as user jordan (uid=1000, gid=46) (pid 11767)
```

Here's the problem:
The samba user is mapping as gid=46, but the media group to write to the media share is gid 200.  

**How do I change the group that the samba user authenticates with?!?**

---

### Post by Amaroku on 2008-12-01
Bump?

---

### Post by Arup on 2008-12-01
What is the format of your samba share? NTFS or efs?

---

### Post by Amaroku on 2008-12-01
It is an NTFS drive.
Here is the /etc/fstab line.
```
# /dev/sdb1
UUID=04C808DAC808CBBC /home/media     ntfs    defaults,dmask=002,fmask=113,gid=200 0       1
```

Attached are two pictures of the share details from the Windows machine.

---

### Post by Arup on 2008-12-01
Have you done a chown and chmod for the ntfs drive? Do a gksudo nautilus and navigate to /media and set total sharing with read and write permission, restart your session and see what happens.

---

### Post by Amaroku on 2008-12-01
When I tried that, Nautilus would automatically flip the setting back to it's previous settings.

Here is the stderr from the terminal:

```
Nautilus-Share-Message: unknown format for key 'media/usershare_acl' as it contains 'Everyone:R,'.  Assuming that the share is read-only
Nautilus-Share-Message: unknown format for key 'media/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
```

---

### Post by Amaroku on 2008-12-01
I also can't change the owner of the directory.  There is no error.  It just doesn't change.
Note about the system:
Ubuntu 8.10 with 2 hard drives.  One is the system drive on ext3, but the "media" drive here is NTFS and mounted to /home/media.

Is there anything wrong with my /etc/fstab?

---

### Post by Arup on 2008-12-01
> **Amaroku said:**
> I also can't change the owner of the directory.  There is no error.  It just doesn't change.
Note about the system:
Ubuntu 8.10 with 2 hard drives.  One is the system drive on ext3, but the "media" drive here is NTFS and mounted to /home/media.

Is there anything wrong with my /etc/fstab?

One more question, is ntfs-3g loaded? Have you named your ntfs partition.

For changing ownership do a sudo chown -R user:user /home/media

then do a sudo chmod -R 755 /home/media

In the user category, add whatever name you have logged in with.

---

