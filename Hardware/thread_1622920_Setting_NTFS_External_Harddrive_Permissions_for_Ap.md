---
title: "Setting NTFS External Harddrive Permissions for Apache"
date: 2010-11-16
forum: Hardware
---

### Post by meltingwax on 2010-11-16
I have an NTFS external harddrive connected to my computer and I have been automounting it with Nautilus.

I desire to use Apache to serve data off of this harddrive. I have set up the proper alias in the apache2.conf, but I get a forbidden error in my browser and a permission error in the error log when I try access it. I suspect this is because of the that the drive is mounted to give permissions to only my user:

```
daniel@wrath:~$ ll /media/Elements/music/
total 56
drwx------ 1 daniel daniel 57344 2010-11-15 08:33 music.daniel
drwx------ 1 daniel daniel     0 2010-09-06 16:59 music.zach

```

Can anyone help me set up this hard drive so it mounts with permissions that apache can use? "chmod -R 755" doesn't work.

Thanks in advance!

---

### Post by meltingwax on 2010-11-16
bump..

---

### Post by meltingwax on 2010-11-16
Found a solution by changing the permissions in /etc/fstab:

```
/dev/hda1       /media/windows  ntfs    ro,defaults,user,gid=1000,umask=0222 0       0
```

Source: [http://www.linuxforums.org/forum/debian-linux/34923-mounted-ntfs-permissions-ubuntu.html](http://www.linuxforums.org/forum/debian-linux/34923-mounted-ntfs-permissions-ubuntu.html)

---

