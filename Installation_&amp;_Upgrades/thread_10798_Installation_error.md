---
title: "Installation error"
date: 2005-01-11
forum: Installation &amp; Upgrades
---

### Post by mip on 2005-01-11
I am getting the following error message when I attempt to install Ubuntu on my machine. 

```
The test of the file system with type ext3 in partition 2 of IDE1 found uncorrected errors
```

The partition in question is my /home partition. There are no errors on the disk as far as I know and it works perfectly with other distributons. During the Ubuntu install I chose "Manual partition" I then selected to keep the data in this partition and mount it as /home.

Any ideas what's going wrong?

Cheers, M.

---

### Post by feneks on 2005-01-11
If at this partition is only /home and nothing else I'd umount /home and do a fsck.ext3 then as root (if (s)he exists).

The other solution would be to boot with the Live-cd and do fsck.ext3.

hopefully this will fix the problem.

--edit--
To use your other distribution is an opportunity too.

--edit--
what do you think:
is root a 
[ ] he
[ ] she
[ ] it

---

### Post by mip on 2005-01-12
Ok. I'll give it a go. 

Thanks. M.

---

### Post by raymond on 2005-01-12
:?: Did this fix your error? :?:

---

### Post by mip on 2005-01-12
[QUOTE=raymond]:?: Did this fix your error? :?:[/QUOTE]

No. I'm still getting the same error message. Here's what I did (from ubuntu-live).

```
warty@ubuntu:~ $ sudo umount /mnt/hda2
warty@ubuntu:~ $ sudo fsck.ext3 /dev/hda2
e2fsck 1.35 (28-Feb-2004)
/home: clean, 11039/4997120 files, 7446506/9984397 blocks
warty@ubuntu:~ $
```

Any ideas?

---

### Post by feneks on 2005-01-12
/home/lost+found/ is empty?


e2fsck tells you that everything is okay... 

-> bug of installer?

---

### Post by mip on 2005-01-13
[QUOTE=feneks]/home/lost+found/ is empty?[/QUOTE]

There is no /home/lost+found/

[QUOTE=feneks]-> bug of installer?[/QUOTE]

I just managed to install Mandrake 10.1 without any problems. Is there anyway I can get around this problem?

---

### Post by mip on 2005-01-14
Anyone? I can't belive know one else has had this problem before.

---

### Post by feneks on 2005-01-16
It's just a guess

what happens when you create /home/lost+found/
```
sudo mkdir /home/lost+found
sudo chown root:root /home/lost+found 
```

---

