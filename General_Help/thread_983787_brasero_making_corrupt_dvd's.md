---
title: "brasero making corrupt dvd's"
date: 2008-11-16
forum: General Help
---

### Post by k00ks on 2008-11-16
i'm trying to burn a .iso thought brasero and it writes fine. then i gotta insert it for it to check for integrity then it says that it's corrupt.

I really need this dvd burned. What's up??

Thanks to all

k00ks

---

### Post by taurus on 2008-11-16
Try another burner like k3b, gnomebaker, etc.

---

### Post by k00ks on 2008-11-16
> **taurus said:**
> Try another burner like k3b, gnomebaker, etc.

Okay cool thanks. I'm dling k3b right now.

---

### Post by k00ks on 2008-11-16
Another error when using k3b. Check the screenshot for the problem

Why is this happening for both brasero and k3b???corrupt file??

---

### Post by taurus on 2008-11-16
Are you sure the file is not corrupted some way?  See if you can mount it from a terminal.

```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
ls -la /media/iso
```

You can unmount it with

```
sudo umount /media/iso
```

---

### Post by k00ks on 2008-11-16
Well the ISO was on my flash driver then i transfered to the desktop. So that /media/iso wont work as i tried in terminal but it says no such thing.

---

### Post by taurus on 2008-11-16
The /media/iso is called a mount point, not your file.  If it's in your ~/Desktop, you need to change to that directory first before you try to mount it.

```
cd ~/Desktop
sudo mkdir /media/iso  <-- Created a mount point to mount your ISO image.
sudo mount -t iso9660 filename.iso /media/iso -o loop
(Replace filename.iso with the actual name of your file.)
ls -la /media/iso
```

---

### Post by alwayshere on 2008-11-16
right click the iso file and choose 
'write to disk "

---

### Post by rbmorse on 2008-11-16
What's the original source from which the .iso was made?  Is it a commercial game or application?

---

### Post by k00ks on 2008-11-16
Okay I'll try that thanks for the clear up.  A bit of a noobie in linux here.

to rbmorse: It's a operating system.

It couldn't find the file again. I made sure that there were no spaces and everything was correctly copied

i tried out that alwaysshere and it worked. But for other burners is what only when it needed to check for integrity that it would fail. This way that you showed me doesnt' do it so I think thats why it worked.

---

### Post by exploder on 2008-11-16
alwayshere's solution is how I deal with this problem. Following his advice should take care of the problem.

---

### Post by k00ks on 2008-11-16
okay cool. Thanks

---

