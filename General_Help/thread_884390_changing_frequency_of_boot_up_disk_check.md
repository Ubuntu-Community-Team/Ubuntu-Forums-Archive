---
title: "changing frequency of boot up disk check"
date: 2008-08-08
forum: General Help
---

### Post by AvengingAngel718 on 2008-08-08
ubuntu recently decided to start forcing a check of the hard drive at every boot. how do i schedule it to instead run, say, every 40 boot cycles?

thanks

---

### Post by dcstar on 2008-08-09
> **AvengingAngel718 said:**
> ubuntu recently decided to start forcing a check of the hard drive at every boot. how do i schedule it to instead run, say, every 40 boot cycles?

thanks

```
man tune2fs
```

---

### Post by prshah on 2008-08-09
> **AvengingAngel718 said:**
> ubuntu recently decided to start forcing a check of the hard drive at every boot. 


By default, the fsck (hard disk check) runs every 30 times the system is mounted. If you have not changed any settings, and yet ubuntu runs fsck on every startup, it means:

a) The system is not being shutdown properly
b) You're not letting the check complete; If you don't let the check complete, it will try again next mount.
c) There's something wrong with the hard disk- Bad sectors would be my first guess. 

If the tune2fs command doesn't work for you (and I have my doubts), then post back on how to check point c. The resolution for points a & b is obvious!

---

### Post by AvengingAngel718 on 2008-08-09
well it quit doing it so my guess is i just had to let it do it's thing for once. i was just unsure about it because it didnt show the message i'm used to about being mounted X times and needing the do a fsck

---

### Post by asuastrophysics on 2009-06-23
how do i use tune2fs to check an EXT4 filesystem?

does it work? it says in the docs that it's only for ext2/3....

---

