---
title: "Busybox, Fstab missing?"
date: 2008-09-03
forum: General Help
---

### Post by mmzdaniel on 2008-09-03
Hey,
Me again, after the last thread in which the problem was after installing the Fingerprint usplash theme, i managed to screw something up again. Whenever I boot, I get some text on the screen and eventually it gives me BusyBox instead of Ubuntu.
It also gives me this error:
```
error while loading shared libraries: libfuse.so.2
```

when i type exit and hit enter, i get this:

```
mount: mounting /root on /host failed: invalid argument
```

when i type this in busybox:

```
mount /root on /host
```

i get this

```
mount: cannot read /etc/fstab: no such file or directory
```

I am using Wubi to mount the 64bit ubuntu.
I just did a chkdsk /r on windows but it didn't work.
Help me :(

---

### Post by ago on 2008-09-04
The issue is the inability to load libfuse

error while loading shared libraries: libfuse.so.2

That should be under 

/lib/libfuse.so.2 which in turns is a link to libfuse.so.2.X.Y

(X Y being the version)

---

### Post by mmzdaniel on 2008-09-04
Yeah it did say that it cant load that library.
i cant check if its there cause i simply have no access to it or anything in ubuntu. i cant access it with a liveCD either, because it doesnt have a different partition, its in wubi. what can i do about it?

---

### Post by ago on 2008-09-04
You should be able to check the /lib content at the busybox prompt once the boot fails.

---

### Post by mmzdaniel on 2008-09-05
Ok i just checked the Lib dir, Libfuse.so.2 isn't there. what can i do about it? :(

---

### Post by ago on 2008-09-05
try to boot with an older kernel/initrd, then regenerate the initrd

---

### Post by mmzdaniel on 2008-09-05
No matter what i use to boot (i got the recovery mode, an older kernel, and the older kernel's recovery) they all boot into busybox. just for the record how would i build the initrd... thanks for the replays so far, too bad its still not working :(

---

### Post by ago on 2008-09-05
Once in ubuntu the command is 

sudo update-initramfs -c -k $(uname -r)

-k specifies the kernel version for which an initrd will be created, by using $(uname -r) you are specifying the current kernel version

---

### Post by mmzdaniel on 2008-09-05
Oh ok... i still have no idea how to fix ubuntu though...
If i cant get it working, ill have to switch back to M$ permanently...

---

### Post by ago on 2008-09-05
You can explore the initrd by booting via live CD and unpacking the initrd into a folder

---

### Post by niceangelbaby on 2008-09-07
just been browsing and came across  [www.watchesshopping.net](http://www.watchesshopping.net) there prices seem to be way lower that standard. All of the watches seem to be priced around $200 to $300. Are they fakes? The site seems to look quite legit.

---

### Post by mmzdaniel on 2008-09-07
when using wubi, i cannot access the files of my ubuntu partition.
its because ubuntu is on my windows partition. so, no, i cant access it via liveCD, unless you meant i should do that with the LiveCD's initrd...

---

### Post by mmzdaniel on 2008-09-08
...bump? :(

---

