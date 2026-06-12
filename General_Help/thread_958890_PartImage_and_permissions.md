---
title: "PartImage and permissions"
date: 2008-10-25
forum: General Help
---

### Post by stoppage on 2008-10-25
Hi, I have following problem with PartImage. I created image of my root partition from Feisty  (it calls itself &#8222;80gb.gz.000&#8220;) size 1,9GB and currently residing residing in my ext.partition in folder  /mnt/sda9/PartImagehda. I can't copy it, Ubuntu says &#8222;you do not have permissions to read it&#8220;. Terminal output for sda9 is... 
...s:/mnt/sda9$ ls

80GB                     HENRY                  NIX                      VIDEO

80GB BACKUPS             HENRY 
ACRONIS BACKUPS  Partimage300GB Complete

BACKUP QUICKSTART 300GB  lost+found             [B]PartImagehda 
[/B]
BACKUPS ACRONIS          MUSIC                  ROOT BACKUP 300GB



/mnt/sda9$ ls -l

total 64

drwxr-xr-x  2 tony tony     4096 2008-10-25 01:19 80GB

drwxr-xr-x  4 tony tony     4096 2008-10-22 20:57 80GB BACKUPS

drwxr-xr-x  2 tony tony     4096 2008-08-21 00:28 BACKUP QUICKSTART 300GB

drwxr-xr-x  2 tony tony     4096 2008-07-21 20:09 BACKUPS ACRONIS

drwxr-xr-x 12 tony tony     4096 2008-10-05 04:23 HENRY

drwxr-xr-x  2 tony tony     4096 2008-10-05 03:30 HENRY ACRONIS BACKUPS

drwxrwxrwx  2 root plugdev 16384 2008-05-15 19:31 lost+found

drwxr-xr-x 15 tony tony     4096 2008-10-22 14:35 MUSIC

drwxr-xr-x  3 tony tony     4096 2008-10-26 02:42 NIX

drwxr-xr-x  2 tony tony     4096 2008-10-23 11:16 Partimage300GB Complete

**drwxr-xr-x  2 tony tony     4096 2008-10-23 11:15 PartImagehda **

drwxr-xr-x  2  999     999  4096 2008-07-27 08:57 ROOT BACKUP 300GB

drwxr-xr-x  6 tony tony     4096 2008-08-14 03:41 VIDEO



I cant even &#8222;cd&#8220; into my backup folder, it just isnt recognised. Can somebody please help me out here?

---

