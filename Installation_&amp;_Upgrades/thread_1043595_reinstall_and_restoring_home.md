---
title: "reinstall and restoring /home"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by icarid_17 on 2009-01-18
hello,i have looked around and i could not find a post that had the answer i really need. here's my problem:
I have reinstalled Ubuntu ultimate and preserved my /home partition, sda9, how do i restore all my settings from that? or make it my home partition, rather that the default?

---

### Post by albinootje on 2009-01-18
> **icarid_17 said:**
>  or make it my home partition, rather that the default?

Is you username the same as before ?
If so, boot into "recovery mode", choose "drop to root shell prompt", and edit /etc/fstab :
```

nano /etc/fstab

```
create a new line :
```

/dev/sda9 /home ext3 relatime 0 2

```
Save the file, and reboot.

---

### Post by icarid_17 on 2009-01-19
awesome, will try when i get home. one question though, will i retain all the new compiz functionality of Ubuntu Ultimate 2.0? or will i have to reinstall compiz, i'm thinking i won't but i would like to be prepared

---

### Post by albinootje on 2009-01-19
> **icarid_17 said:**
> awesome, will try when i get home. one question though, will i retain all the new compiz functionality of Ubuntu Ultimate 2.0? or will i have to reinstall compiz, i'm thinking i won't but i would like to be prepared

No idea, I don't use compiz, hopefully someone else has an answer on this for you.

---

### Post by icarid_17 on 2009-01-19
> **albinootje said:**
> No idea, I don't use compiz, hopefully someone else has an answer on this for you.

turns out that i can export my compiz preferences to a file

---

### Post by icarid_17 on 2009-01-19
> **albinootje said:**
> Is you username the same as before ?
If so, boot into "recovery mode", choose "drop to root shell prompt", and edit /etc/fstab :
```

nano /etc/fstab

```
create a new line :
```

/dev/sda9 /home ext3 relatime 0 2

```
Save the file, and reboot.

turns out that doesn't do what i want, it certainly worked properly in that it reverted me to my old /home but it also brought along the problems that getting ubuntu ultimate 2.0 has fixed.
is it possible to bring my wine stuff and some other programs over to my ubuntu 2.0 /home partition?, i can mount the old partition while running in  the new partition, in case that has some bearing on what i can do.

---

### Post by icarid_17 on 2009-01-20
can anyone help?

---

