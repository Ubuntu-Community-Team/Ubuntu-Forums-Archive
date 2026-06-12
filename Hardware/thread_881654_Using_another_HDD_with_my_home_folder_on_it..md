---
title: "Using another HDD with my home folder on it."
date: 2008-08-06
forum: Hardware
---

### Post by DarkAmbient on 2008-08-06
Been trying to get this to work propertly for weeks now without any success so i guess i could use some help.

I got 3 harddrives in my stationary computer, one with Ubuntu on it. 2nd with my home folder which i mount in /home/*name* and third which i got only movies on and mount in /home/*name*/Video.

Thing is that when i mount my home folder partition every file under home is owned by root. And it wont work using sudo nautilus to change filerights, nor chown -hR *name* on my homefolder. Ubuntu set root as owner direcly again. I guess the problem is in how I auto mount the partition in /etc/fstab? right now i got this in fstab (partition is of ntfs)

/dev/blabla /home/*name* ntfs-3g auto,user,rw 0 2

but ive tryed alot of other setups. Right now i still can use the computer but some applications wont work propertly as they require me to be the owner of home and not root.

I'd rly would appreciate help on this one with how to setup /etc/fstab or to solve this problem in any other way so i can set myself to owner of my home folder and keep it that way.

Thanks
\oo/
//Ambient

---

### Post by Lod on 2008-08-06
You could try mount the disk as /home, not as /home/<<user>>, and create a user folder on it.
However, according to your fstab line it is a ntfs file system? I don't believe it's possible to assign specific user rights on a ntfs folder, it's not linux native. Only root has access and probably with rwxrwxrwx file permissions (777).
Either use Fat (with the limited filesize) or use a linux native filesystem like ext3. There are tools to access ext3 from Windows.

---

### Post by ilrudie on 2008-08-06
What are you trying to do that would cause you to have a ntfs home partition in the first place?

---

### Post by DarkAmbient on 2008-08-06
> **ilrudie said:**
> What are you trying to do that would cause you to have a ntfs home partition in the first place?

i had TinyXP before i installed Ubuntu on my stationary, and I didnt want to format the disk(s) as i got tons of files i need to keep but no space to move them to temporarily for a filesystem change.

But this would work alot better if i had ext2 or ext3 then?

---

### Post by Archmage on 2008-08-06
> **DarkAmbient said:**
> But this would work alot better if i had ext2 or ext3 then?

You should get ext3. And to answer your first question: Yes, it would work better, if you would have ext3 as your home-partition.

---

### Post by ilrudie on 2008-08-06
+1 for ext3

---

### Post by DarkAmbient on 2008-08-09
ok, i'll look into switching filesystem to ext3. Thanks alot guys!

---

