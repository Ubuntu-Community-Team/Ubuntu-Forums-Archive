---
title: "Dual Booting"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by ahddm on 2009-02-04
Ok, Lemme give you an intro lol. I had Ubuntu installed on my laptop taking up whole partition but I wanted to try windows 7, I used GParted CD to resize for Windows evertything went ok, I installed windows 7 on new partition ok all good. But now when I boot it goes straight to windows how can I add option for ubuntu :(

---

### Post by cariboo on 2009-02-04
Windows7 over wrote the mbr as all versions of windows do. To repair the mbr boot from your LiveCD and at the desktop open a Applications-->Accessories-->Termianl and type:

```
sudo grub
```

This will start the grub editor, next type:

```
find /boot/grub/stage1
```

the result should be something like this:

```
(hd0,2)
```

where the 2 would be the partition /boot/grub is located on. Next type:

```
root (hd0,2)
```

where (hd0,2) is the result of the find command, to setup the mbr type:

```
setup (hd0)
```

That should repair grub. Type:

```
quit
```

and reboot.

Jim

---

### Post by Bao2 on 2009-02-04
The best way of trying a new Operative System is add a new hard disk in your computer and select it in the Bios as the hard disk to boot. Then you install the new OS. When you want go back again to Linux you go to the Bios again and select the former hard disk to boot. I have four OS in my PC and I always go to the Bios first and choose the disk to boot (well, these two last months I am only running Linux so I didn't go to the Bios in two months :-)

---

### Post by ahddm on 2009-02-05
@Bao2
Kinda hard to install new hd in a laptop ;)

@cariboo907
Thanks for instructions Ill download new cd after im done gaming :-p dumb intel graphics drivers suck with ubuntu

---

