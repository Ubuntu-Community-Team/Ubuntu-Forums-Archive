---
title: "[SOLVED] permissions change clonezilla file"
date: 2008-10-27
forum: General Help
---

### Post by stoppage on 2008-10-27
Hi, Im looking for a method to change permissions or owner of a „CloneZilla“ image file...“ 2008-10-27 -05-img“  so that I can burn it to disk with k3b. Could somebody please give me the instruction to do this?
Its location..../mnt/sda9.
Obliged

---

### Post by unutbu on 2008-10-27
To make yourself the owner:
```
chown $USER "2008-10-27-05-img"
```

To give yourself read/write permissions:
```
chmod u=rw "2008-10-27-05-img"
```

---

### Post by stoppage on 2008-10-27
This is strange, image not recognised...

:~$ chown tony 2008-10-27-05-img

chown: cannot access `2008-10-27-05-img': No such file or directory

and same for chmod


....s:/mnt/sda9$ ls

2008-10-27 -05-img                       
HENRY ACRONIS BACKUPS

2008-10-27-07-img                        
KDE-Four-Live.i686-1.1.0.iso

80GB                                     
lost+found

80GB BACKUPS                             MUSIC

backup hda5.gz.000                       NIX

BACKUP QUICKSTART 300GB                  pi5a10f985.tmp

BACKUPS ACRONIS                          ROOT BACKUP 300GB

clonezilla-live-1.2.0-25.iso             SUPER GRUB DISK_0.9654.iso

clonezilla-sysresccd-full-mod-2.6.0.iso  systemrescuecd-x86-1.0.4.iso

HENRY                                    VIDEO

tony@youhits:/mnt/sda9$

---

### Post by unutbu on 2008-10-27
Is there a space in the filename:
```
2008-10-27 -05-img 
```

If so, you will need quotation marks to protect the space:
```

chown tony "2008-10-27 -05-img"
```

Also check that there is no space(s) at the end or beginning of the filename.

If that's not the problem, please post the output of 
```

ls -l 
```

---

### Post by stoppage on 2008-10-27
Sorry, panic and a stupid syntax error on my side..$ sudo chown -R tony /"mnt/sda9/2008-10-27-05-img" did it. Thanks for your patience and the prompt reply

---

