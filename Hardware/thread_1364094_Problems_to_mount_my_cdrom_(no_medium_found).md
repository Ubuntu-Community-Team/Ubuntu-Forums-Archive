---
title: "Problems to mount my cdrom (no medium found)"
date: 2009-12-25
forum: Hardware
---

### Post by THXTom on 2009-12-25
```
$ sudo cat /dev/scd0
cat: /dev/scd0: No medium found
thomas@thomas-desktop:~$ 

```Heres some screen shots.

Got this Dell380 from PC repair shop for a song to get into Linux.
Tried installing from Ubuntu 9.10 CD and it was nogo. Had to use a USB.

Been  getting used to Ubuntu and just started researching CD problem.

Being new to Linux just want to make sure I'm not missing something.

Thanks, T

---

### Post by sgtGarcia on 2009-12-25
Why U are using /dev/scd0 while You have /dev/sr0 ??

---

### Post by THXTom on 2009-12-25
Hmmm, I'll try it again

---

### Post by THXTom on 2009-12-25
~$ sudo cat /dev/sr0
cat: /dev/sr0: No medium found
thomas@thomas-desktop:~$

no luck

---

### Post by sgtGarcia on 2009-12-25
Maybe this gonna be a stupid question, but:

Did You put CD/DVD inside the drive?? Did You tried with more CD's/DVD's??

Cause I get this error only when there's no disc in drive.

If YES, than can you post how /etc/fstab file look like??

---

### Post by THXTom on 2009-12-25
Well, its fixed....
 
Had a Puppy linux cd iso in the drive...swapped in a cd with some [photos]("http://forums.techguy.org/#") on it and can browse the disk.
 
Wonder why it didn't pick up the big iso file???
 
 
Thanks for your help Sarge

Later, T

---

### Post by IcarusR on 2009-12-26
Probably a 'bad copy' CD.
Try burning another copy of the iso but at **slow** speed.

---

