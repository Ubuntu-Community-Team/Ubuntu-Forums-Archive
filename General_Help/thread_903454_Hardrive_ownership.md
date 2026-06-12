---
title: "Hardrive ownership"
date: 2008-08-28
forum: General Help
---

### Post by Wickd on 2008-08-28
Hi there I have the following partition setup:

1) 250 gb SATA: 7 gb windows (NTFS)
               17 gb linux
                1 gb Swap
              222 gb fat 32

Current I cannot write to my fat 32 drive, because it is owned by the root. How do I change the ownership to ivan (me). it mounts under /media/sda4

Thanks in Advance

---

### Post by drs305 on 2008-08-28
NTFS and fat32 partition ownership is determined at the time of mounting, so the way to do this for an internal hard drive is to add the partition to fstab:

```

sudo cp /etc/fstab /etc/fstab.old
gksu gedit /etc/fstab
/dev/sda4 /media/sda4 vfat  users,uid=1000,gid=100,umask=022 0 0  
sudo umount /dev/sda4
sudo mount -a

```

Technical note gibberish: The umask=022 provides 755 permissions (read/write/execute for you, read-execute for groups/others). You also can substitute fmask and dmask values for umask if desired - read the man pages for these settings and what they do. The gid=100 (group id can be set to whatever you want. If you want it to be your usergroup, set it to 1000. 100 is normally the group 'users').

---

