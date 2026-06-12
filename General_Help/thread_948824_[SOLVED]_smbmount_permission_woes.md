---
title: "[SOLVED] smbmount permission woes"
date: 2008-10-15
forum: General Help
---

### Post by skelooth on 2008-10-15
Hi all. I'm sure this must be something people have encountered before by maybe I'm searching in a weird way because I can't seem to find an answer that actually works.

Basically here's the situation: I use smbmount to mount a share on a windows server. Everything works fine, but when I touch a file it defaults its permissions to 744, and I would REALLY like them to default to 766. When I run chmod -R 766 mounted/* for some reason the permissions turn into rwxrwSrwx .... what is that S?. So chmodding them works, but I am not familiar with the S.

Can I somehow mount the drive so creating files defaults to rwxrw-rw- ?

---

### Post by mssever on 2008-10-15
> **skelooth said:**
> Hi all. I'm sure this must be something people have encountered before by maybe I'm searching in a weird way because I can't seem to find an answer that actually works.

Basically here's the situation: I use smbmount to mount a share on a windows server. Everything works fine, but when I touch a file it defaults its permissions to 744, and I would REALLY like them to default to 766. When I run chmod -R 766 mounted/* for some reason the permissions turn into rwxrwSrwx .... what is that S?. So chmodding them works, but I am not familiar with the S.

Can I somehow mount the drive so creating files defaults to rwxrw-rw- ?
I don't remember for sure what the S is. Maybe the sticky bit? At any rate, Linux permissions are incompatible with Windows permissions, so you can't set permissions on a Samba share. And when you mount a partition, its permissions override the permissions of the mount point. You have to set the umask and/or uid/gid in the mount options (such as in /etc/fstab).

---

### Post by skelooth on 2008-10-15
> **mssever said:**
> I don't remember for sure what the S is. Maybe the sticky bit? At any rate, Linux permissions are incompatible with Windows permissions, so you can't set permissions on a Samba share. And when you mount a partition, its permissions override the permissions of the mount point. You have to set the umask and/or uid/gid in the mount options (such as in /etc/fstab).

Thank you for responding mssever. This is the line I'm using in my fstab:
```
//192.168.0.242/websites /mnt/supercube smbfs rw,user=***,pass=***,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1001,gid=1001,fmask=777,dmask=777,guest

```

I have also tried different variations (removing/adding things) in a vain attempt to make a difference. It mounts rw correctly, but doesn't let me create files with the right permissions, I always have to run chmod before I can edit them.

---

### Post by mssever on 2008-10-15
> **skelooth said:**
> Thank you for responding mssever. This is the line I'm using in my fstab:
```
//192.168.0.242/websites /mnt/supercube smbfs rw,user=***,pass=***,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1001,gid=1001,fmask=777,dmask=777,guest

```I have also tried different variations (removing/adding things) in a vain attempt to make a difference. It mounts rw correctly, but doesn't let me create files with the right permissions, I always have to run chmod before I can edit them.
I don't think your fmask and dmask settings are correct. The digits of the mask are subtracted from 7 to produce the permissions. So a mask of 022 results in permissions of 755. Or a mask of 777 produces permissions 000. :)

I also don't understand why you want 766 permissions. You want to execute all the files along with rw permission, plus give other users rw permission but not execute permisson? I'm wondering if what you really mean is a fmask of 111 and dmask of 000.

Also, I doubt it's a good idea to specify both a mode and a mask.

---

### Post by Iowan on 2008-10-15
Probably a bit off-topic, but you should realize that SMBFS has been replaced by CIFS.  Doubt that's the problem, but [this]("http://ubuntuforums.org/showthread.php?t=288534") might be useful information.

---

### Post by skelooth on 2008-10-16
Thank you for the help, I solved the issue but it was more a case of me being negligent than mounting incorrectly. 

Before I started getting desperate and inserting anything I could into the fstab entry my original fstab looked like this:
```

//192.168.0.242/websites /mnt/supercube cifs rw,user=pat,pass=XXX,iocharset=utf8,file_mode=0777,file_mode=0777,dir_mode=0777

```

I was frustrated because touching files wasn't giving me write access w/o a chmod. Then, in a glaring moment of logic, I looked at who the owners of the file were.... they all belonged to root. So duh.

I put uid=myusername at the end of the options and now it's all good.

Thanks again for the help.

---

