---
title: "manual hdd mount work but not auto mount"
date: 2014-12-17
forum: Hardware
---

### Post by cosy2 on 2014-12-17
i got a HDD that i want to be on auto mount so on gnome-disks i just turn the auto mount option ON and dont change any parameter and when the system boots the auto mount is not working

---

### Post by Bashing-om on 2014-12-17
cosy2; Hello ;

> **cosy2 said:**
> i got a HDD that i want to be on auto mount so on gnome-disks i just turn the auto mount option ON and dont change any parameter and when the system boots the auto mount is not working

That ability is performed by an addition to the 'fstab' file.
See:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <-bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336) <-Manualy edit fstab - why(Morbius1)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by cosy2 on 2014-12-17
thx for the links


oh i did solve this problem i did expect the parameters on the gome-disks to be relevenat to me setups 

before
```
/dev/disk/by-uuid/xxxxxxx    /stuff auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
after 
```
UUID=xxxxxx   /stuff ext4 defaults 0  2
```

the intresting part for me
one of the HDD do auto mount using the before setup, imo this is because is still windows hdd

the second HDD that dint auto mount was formated using ubuntu and it seams for odd reason it did keep the irrelevant paramethers

---

### Post by Bashing-om on 2014-12-17
cosy2; Good deal ;

Yep, all in telling the operating system what is, and what to do.

[INDENT][INDENT]all in the care a feeding of
[INDENT][INDENT][INDENT]your 'buntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

