---
title: "[SOLVED] Lost users after upgrading to 8.10"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by adm1968 on 2008-12-08
[FONT="Georgia"]Strange!
Upgraded 8.04 to 8.10
Several things stopped working, the most worrying:

1  My wife's and son's users cannot be accessed anymore
   Only my own user can be accessed (the one selected for the installation)
   Their home directories are still there, but their users are not shown
   If I try to create them, the system complains: 
      'Please use a different home directory'

????

I've searched, but it seems nobody has published anything of this sort[/FONT]

---

### Post by ghantoos on 2008-12-08
Did you try adding the users from a terminal?
```
ghantoos@blabla:~$ sudo adduser user1
Adding user `user1' ...
Adding new group `user1' (1001) ...
Adding new user `user1' (1001) with group `user1' ...
The home directory `/home/user1' already exists.  Not copying from `/etc/skel'.
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for user1
Enter the new value, or press ENTER for the default
    Full Name []: 
    Room Number []: 
    Work Phone []: 
    Home Phone []: 
    Other []: 
Is the information correct? [Y/n] 
ghantoos@blabla:~$ su user1 
Password: 
user1@blabla:/home/ghantoos$ cd
user1@blabla:~$ pwd
/home/user1
user1@blabla:~$ exit
```Hope this helps,
Cheers,

---

### Post by adm1968 on 2008-12-08
[FONT="Georgia"]Cheers, Ghantoos!
Unfortunately it did not work
Lots of 'things' were ignored when trying to open a graphical session with the 'new' user

BTW, any idea why existing users are lost after upgrading to 8.10?[/FONT]

---

### Post by ghantoos on 2008-12-08
I have no idea why this happened. The upgrade shouldn't mess up with your existing users list.

---

### Post by unutbu on 2008-12-08
Please post the output of 
```

cat /etc/fstab
sudo fdisk -l
mount
ls -l /home

```

The first command will tell us what partitions get mounted where.
The second tells us how your hard drive(s) is(are) partitioned.
The third tells us which partitions are currented mounted.
The fourth tells us what directories are in /home.

In the above commands '-l' is a minus lower case L.

If your wife's user name is 'mom', then type
```

grep mom /etc/passwd
```
The output should look something like this:```

mom:x:1001:1001:,,,:**/home/mom**:/bin/bash
```
Note in particular, it shows the location of the home directory for mom. Please report if it says something other than /home/mom.

---

### Post by adm1968 on 2008-12-08
The output for all those commands:

[I]**art@Pavilion:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d683cdbe-f373-48bb-9395-38eccc1eb076 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=53cebf81-3eda-46c9-ada7-81e428a170b5 /home           ext3    relatime        0       2
# /dev/sda7
UUID=5f5ae884-68d0-48da-8038-8069fef72186 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


**art@Pavilion:~$ sudo fdisk -l**
[sudo] password for art: 

Disco /dev/sda: 360.0 GB, 360080695296 bytes
255 cabezas, 63 sectores/pista, 43777 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x1549f232

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS
/dev/sda2           42460       43777    10584000    7  HPFS/NTFS
La partición 2 no termina en un límite de cilindro.
/dev/sda3            7296       42459   282454830    5  Extendida
/dev/sda5            7296        9119    14651248+  83  Linux
/dev/sda6            9120       42382   267185016   83  Linux
/dev/sda7           42383       42459      618471   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco


**art@Pavilion:~$ mount**
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/art/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=art)

**art@Pavilion:~$ ls -l /home**
total 32
drwxr-xr-x 69 art      art       4096 2008-12-08 23:39 art
drwxr-xr-x 26 teresa   teresa    4096 2008-09-10 12:16 guille
drwxr-xr-x 35 invitado invitado  4096 2008-12-08 21:48 invitado
drwx------  2 root     root     16384 2008-06-18 19:40 lost+found
drwxr-xr-x 43 invitado invitado  4096 2008-11-01 00:38 teresa

**art@Pavilion:~$ grep teresa /etc/passwd**
teresa:x:1002:1002:Teresa LOPEZ-OCON,,,:/home/teresa:/bin/bash[/I]


Any ideas?

---

### Post by ghantoos on 2008-12-08
It seems your ownerships are messed up.

The teresa's home folder is owned by invitado, and guille's is owned by teressa.

Try:
```
sudo chown teresa:teressa /home/teresa
sudo chown guille:guille /home/guille
```Cheers,

---

### Post by adm1968 on 2008-12-08
> **ghantoos said:**
> It seems your ownships are messed up.

The teresa's home folder is owned by invitado, and guille's is owned by teressa.

Tyr:
```
sudo chown teresa:teressa /home/teresa
sudo chown guille:guille /home/guille
```Cheers,

Great!
That sounds just like it
Will try it out tomorrow (time to go to sleep)

Thanks very much to both of you

---

### Post by adm1968 on 2008-12-09
> **ghantoos said:**
> It seems your ownerships are messed up.

The teresa's home folder is owned by invitado, and guille's is owned by teressa.

Try:
```
sudo chown teresa:teressa /home/teresa
sudo chown guille:guille /home/guille
```Cheers,


I did just that, but it did not work ...
(did apply 'Teresa' with one 's' ;)
:confused:

---

### Post by ghantoos on 2008-12-09
Can you try apply it recursively?
```
sudo chown -R teresa:teressa /home/teresa
```

Hope this does the trick,
Cheers,

---

### Post by adm1968 on 2008-12-09
> **ghantoos said:**
> Can you try apply it recursively?
```
sudo chown -R teresa:teressa /home/teresa
```

Hope this does the trick,
Cheers,

YES!
It did the trick
The user profile now loads perfectly (fingers crossed)
Thanks!!

---

