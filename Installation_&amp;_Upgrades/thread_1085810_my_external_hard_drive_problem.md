---
title: "my external hard drive problem"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by crazlaw151 on 2009-03-03
hey guys, by now I'm sure you've heard this before and I did take some time to look up the answer I still need some help.

I have a maxtor external 750gb hard drive that says "unable to mount volume" when I try to plus it in and view my files on there.  I have a lot of stuff on there and don't want to lose it if possible.  I need to know how I can get the computer to open it and let me view the files.  It already shows that it is there, just not able  to mount.  Thanks in advance.

---

### Post by taurus on 2009-03-03
Maybe you want to connect it back to a windows machine and use the safely remove hardware option to unmount it before you unplug it. 

Otherwise, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by crazlaw151 on 2009-03-04
I do that and it pulls up the info for it, but still says unable to mount.  I'll try hooking it up to a windows machine tonight and trying but in case that doesn't work what else could I try?

Like i said i would love to not have to reformat so I don't lose everything thats on it because thats where i backed up all my files before I switched to Ubuntu.  Thanks again.

---

### Post by taurus on 2009-03-04
While the drive is plugged in, post the outputs of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

