---
title: "[SOLVED] Mount External HD with Full Rights"
date: 2008-09-26
forum: Hardware
---

### Post by slimx3m on 2008-09-26
hey guys,

i really didn't want to post this in here but i've try everything and nothing really is working.  what i am trying to do is to mount an external hard drive with full privileges (777). so i mount it as a root and try to chmod 777 and it didn't take it... try to ```
chown root:users /media/external_disk
``` and it gives an "Operation not permitted" and i am the ROOT.  the /etc/fstab is setup as ```
/dev/sdc1 /media/external_disk vfat rw 0 0
``` and still nothing works... any thoughts?! i am going crazy here.

is like everything i do he doesn't want to take it. also... in the mtab same information is there.

thanx in advance

---

### Post by IcarusR on 2008-09-27
Is the drive USB ??
I have a USB drive that is auto mounted when plugged in. I have not added it to fstab. I can write to this drive as normal user. 
Having said that my normal user is member of group root.
Drive is owned by normal user & group of root.
```
drwx------ 12 andy root 4096 2008-09-27 10:20 PORT-A-DISK

```
Also if I go System > Administration > Users & Groups > unlock & check my users Properties under Privilages "acess external storage devices automatically" is checked.

Hope some of this helps.

---

### Post by slimx3m on 2008-09-27
yes, thank you.  i am part of those devices already :(

the problem is that i am not able to change the root privileges as a root :(. when ever i change it wouldn't take it.

---

### Post by slimx3m on 2008-11-03
solve.  vfat doesn't read any type of permissions if you give it.  if you are using a samba server and you are trying to connect to that drive you will not be able to.  what i did was format my drive from vfat to ext3 and i was able to change the permissions with no problem.

---

