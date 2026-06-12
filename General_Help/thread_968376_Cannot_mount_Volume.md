---
title: "Cannot mount Volume"
date: 2008-11-02
forum: General Help
---

### Post by markomk on 2008-11-02
hi
i have a little problem
few days ago a icons shows on my desktop, from other OS' XP NTFS partition 
and i deleted from desktop :S now i can't open xp partition :(

solution pls :)
tnx

---

### Post by eotakos on 2008-11-02
how about the places menu; there should be an option somewhere underneath the computer icon

---

### Post by markomk on 2008-11-02
> **eotakos said:**
> how about the places menu; there should be an option somewhere underneath the computer icon

Cannot mount volume
Unable to mount the volume

its same.

---

### Post by eotakos on 2008-11-05
have you tried to mount the volume from console? 

to get info about your drives and the devs they are assigned to, you can use   

sudo fdisk -l

if you recognize the volume you are interested in from the right column and the size of it, you can then use the mount command with the /dev/??? device you see on the left.

---

