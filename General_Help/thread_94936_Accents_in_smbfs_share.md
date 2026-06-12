---
title: "Accents in smbfs share"
date: 2005-11-25
forum: General Help
---

### Post by jferrando on 2005-11-25
The server of my company runs debian.etch with smbfs. Both server and Windows workstations seems to work with the same charset:

jferrando@pcjordi:~/surera$ ls -l
total 28
dr-xr-xr-x  1 jferrando jferrando 4096 2005-11-25 15:07 [COLOR="Red"]**ajá**[/COLOR]

When I mount the system with my kubuntu/desktop workstation, I can't see the files with accents properly:

jferrando@pcjordi:~/surera$ ls -l
total 28
dr-xr-xr-x  1 jferrando jferrando 4096 2005-11-25 15:07 **[COLOR="Red"]aj?[/COLOR]**

Any idea?

---

### Post by jferrando on 2006-01-26
I have it working now, though I have some questions:
Seems that samba taks **utf8** to local filesystem, but **unicode** on the wire.
I use utf8 in my kubuntu system locales.
I mount the filesystem with:

*mount -t smbfs //192.168.8.5/datos /home/jferrando/surera -o credentials=/etc/smbc.jordi,uid=1000,gid=1000,codepage=unicode,iocharset=utf8**[COLOR="Red"],unicode[/COLOR]***

and it works, I see the same chars (Acci**[COLOR="Red"]ó[/COLOR]**n.txt, Espa**[COLOR="Red"]ñ[/COLOR]**ol.txt, etc) in windows clients and in kubuntu client, though I don't understant the last "[COLOR="Red"],unicode[/COLOR]" parameter.

I used to have the filesystems mounted in fstab, with auto option, but it does not work with the codepage and iocharset parameters with fstab.

*//192.168.8.5/datos  /home/jferrando/surera  smbfs  credentials=/etc/smbc.jordi,uid=1000,gid=1000,noauto,codepage=unicode,iocharset=utf8,unicode  0  0*

Any ideas?

---

### Post by beastie on 2006-01-31
I have a similar problem, using Ubuntu 5.10 as a server (no desktop installed).

I try to mount smb shares, hosted on windows workstations, on my ubuntu box, but i can't seem to get the accents right. i have tried a big number of combinations, and have been stuck with this problem for weeks now. I have posted details in [another thread]("http://www.ubuntuforums.org/showthread.php?t=33039&highlight=charset+hell") about this.

When accessing the share using smbclient, accents show correctly, but when mounting within the filesystem using mount -t smbfs, i can't seem to get characters to show up correctly. I'm using fr_CA.UTF-8 locale.

```
root@feanor:/mnt# locale
LANG=fr_CA.UTF-8
...
```

Here's an example of when I try to mount my smb share:

```
root@feanor:/mnt# mount -t smbfs //somestation/someshare /mnt/thatshare -o credentials=/etc/samba/.smbcredentials,uid=1000,gid=1000,iocharset=utf8,codepage=unicode
```

if anybody understands that kind of stuff, that'd really help me out...

thanks.

---

### Post by jferrando on 2006-05-20
Try to mount using CIFS instead of smbfs:

# mount -t cifs //192.168.11.2/datos /home/jferrando/datos -o username=jordi,password=xxxx,uid=1000,gid=1000,iocharset=utf8

---

### Post by adamkane on 2006-05-20
NTFS uses the CP850 codepage.

---

### Post by adamkane on 2006-05-20
See here:
[http://www.ubuntuforums.org/showthread.php?p=1035950](http://www.ubuntuforums.org/showthread.php?p=1035950)

---

