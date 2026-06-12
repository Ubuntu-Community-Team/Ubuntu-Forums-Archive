---
title: "Dont have permission to executing simple|complex C program BUT it have!! and more"
date: 2008-11-28
forum: General Help
---

### Post by SuckerBlood on 2008-11-28
Hi,

Before all i think I have all packages needed to compile installed... :S

In firts time I have to execute a GTK SIMPLE program but... I have this output:

```
bash: ./hola: Permiso denegado
```

After, i try with simple program in C:
```
#include <stdio.h>

int main(){
printf("hola");
return 0;
}
```

BUT... it compiles CORRECTLY without errors but when I try to execute it I have and error, and **PERMISSION ERROR!** The same of the others :(!!


Days ago I can compile c++ programs... but now I can't execute o_O

[I put this in launchpad]("https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/303312")

I don't have idea that what's that... please! I need to compile. Gimme Suggestion :(

PS: I'm Spanish and my English level is so poor.

--->PS: The programs... have permissions.:(

---

### Post by SuckerBlood on 2008-11-28
hi!!

I have more information. I have something.

If I copy the file in **/bin/ path** (for example) and I write the name of the executable it RUN!! (it shows "hola" weee....)

So... thinking i have thank... if I put './' in $PATH it should work!!:
```
$ export PATH=$PATH:./
```

BUT, don't work :(.

**Please, help me :(**

---

### Post by SuckerBlood on 2008-11-28
more information in [launchpad-bug]("https://bugs.edge.launchpad.net/bugs/303312") and [questions]("https://answers.edge.launchpad.net/ubuntu/+source/gcc-defaults/+question/52893")

---

### Post by SuckerBlood on 2008-11-28
> **SuckerBlood said:**
> more information in [launchpad-bug]("https://bugs.edge.launchpad.net/bugs/303312") and [questions]("https://answers.edge.launchpad.net/ubuntu/+source/gcc-defaults/+question/52893"), hehe... the same information xD :(:(

---

### Post by jpeddicord on 2008-11-28
In the folder where your C application is, could you run the following commands and paste the output here?

```
id
```
```
ls -al
```

Hopefully we'll be able to figure out what's not set right.

---

### Post by SuckerBlood on 2008-11-28
Yes and tnx! This is the output:

```
$ id
uid=1000(bloodsucker) gid=1000(bloodsucker) grupos=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(bloodsucker)

```

and..

$ ls -al
total 64
drwxr-xr-x  2 bloodsucker bloodsucker  4096 2008-11-29 02:16 .
drwxr-xr-x 12 bloodsucker bloodsucker  4096 2008-10-30 01:40 ..
-rw-r--r--  1 bloodsucker bloodsucker   208 2008-09-28 16:49 base.c~
-rwxrwxrwx  1 bloodsucker bloodsucker 16971 2008-11-29 03:27 helloworld
-rw-r--r--  1 bloodsucker bloodsucker   265 2008-11-29 01:36 helloworld.c
-rw-r--r--  1 bloodsucker bloodsucker   266 2008-11-29 01:28 helloworld.c~
-rwxr-xr-x  1 bloodsucker bloodsucker  9042 2008-11-29 02:16 hola
-rw-r--r--  1 bloodsucker bloodsucker    60 2008-11-29 02:15 hola.c
-rw-r--r--  1 bloodsucker bloodsucker    22 2008-11-29 02:05 hola.c~
-rw-r--r--  1 bloodsucker bloodsucker   248 2008-09-28 16:14 simple.c~

This directory is one of don't work (It does not work either)

---

### Post by jpeddicord on 2008-11-28
Weird, that looks fine. Have you tried signing out and back in again? Sometimes system permission changes won't apply until you login the next time.

---

### Post by SuckerBlood on 2008-11-28
> **jacobmp92 said:**
> Weird, that looks fine. Have you tried signing out and back in again? Sometimes system permission changes won't apply until you login the next time.

Yes. I reboot various times. Including creating a new user... and compiling and executing the binary :(

I run LiveCD too and... works :(
Please.. some ideas... :(:(

---

### Post by jpeddicord on 2008-11-28
> **SuckerBlood said:**
> Yes. I reboot various times. Including creating a new user... and compiling and executing the binary :(

I run LiveCD too and... works :(
Please.. some ideas... :(:(

Let's check to see if the filesystem can execute. Run and paste the result of these:

```
cat /etc/fstab
```
```
mount
```

---

### Post by SuckerBlood on 2008-11-28
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda6
UUID=77a4b66a-a367-4446-be32-b8741d864281  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=572ab93e-6a85-42c8-ac53-f54456adbe33  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/MD      ext3         errors=remount-ro,users     0  0  

```

```
$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-10-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /media/MD type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bloodsucker/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bloodsucker)

```

kisses :) hehe

---

### Post by SuckerBlood on 2008-11-28
OH MY GOD!!!!

I THINK THE PROBLEM IS HERE!!

I copy files (executable) in Desktop... and... IT WORKKKSSS!!!!!!

How can we change this to /media/MD directory (HD disk)?

:guitar::guitar: :KS:KS

edit:
the disk-partition is: **/dev/sdb1**

jurls... its the 4:15 am... xD I need sleep :( thanks! :D :)

---

### Post by jpeddicord on 2008-11-28
> **SuckerBlood said:**
> ```
$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-10-generic/volatile type tmpfs (rw,mode=755)
**/dev/sdb1 on /media/MD type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)**
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bloodsucker/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bloodsucker)

```

noexec is what is causing problems; the filesystem there for some reason doesn't allow you to run anything from the drive. If it's a USB drive, try unmounting it (from the file manager or your desktop), remove it, and plug it back in.

---

### Post by SuckerBlood on 2008-11-28
> **jacobmp92 said:**
> noexec is what is causing problems; the filesystem there for some reason doesn't allow you to run anything from the drive. If it's a USB drive, try unmounting it (from the file manager or your desktop), remove it, and plug it back in.


It is a HD disk. It is mounted automatically in the start up of the system.
I configure it with **pysdm** (a disk manager). I don't see this "property" to disable (or enable). How can I correct this manually? :)

---

### Post by jpeddicord on 2008-11-28
Open Pysdm, find your drive, then click the Assistant button. Click the Special Files tab, and make sure "Permit execution of binaries" is enabled.
Close and apply. Restart if needed. Click the screenshot below for an example.

[ATTACH]94543[/ATTACH]

---

### Post by SuckerBlood on 2008-11-28
> **jacobmp92 said:**
> Open Pysdm, find your drive, then click the Assistant button. Click the Special Files tab, and make sure "Permit execution of binaries" is enabled.
Close and apply. Restart if needed. Click the screenshot below for an example.

[ATTACH]94543[/ATTACH]

hi jacobmp92,
I see this option :( and it active before.
In "Options box" entrie dont appear "noexec" if this option is enable (naturally) and yes if it is disable (naturally).
The problem... are that this option is **enable** and I umount and mount the partition. But $ mount says that this partition have "noexec" active :(

Exist a command as "noexec" but... that this "permits exec" ak "exec"? hehe :)

---

### Post by jpeddicord on 2008-11-28
I'm not sure what to do at this point, I'm just going to let a drive ninja step in. ;)

I've moved this thread to General Help.

---

### Post by SuckerBlood on 2008-11-28
I resolve the problem :D I found a *property*: **exec**

This is the ¬noexec functionality!! :D :D

Thanks for you, thanks!!!! :) :) :) :) :)

But... this is a bug of **pysdm**, no?
tnx!

---

### Post by jpeddicord on 2008-11-28
> **SuckerBlood said:**
> I resolve the problem :D I found a *property*: **exec**

This is the ¬noexec functionality!! :D :D

Thanks for you, thanks!!!!

But... this is a bug of **pysdm**, no?
tnx!

Glad you got it working. :)

I don't know if it would be a bug or not, it's probably just a different option that was needed.

---

