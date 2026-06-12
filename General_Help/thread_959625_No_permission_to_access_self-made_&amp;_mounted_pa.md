---
title: "No permission to access self-made &amp; mounted partition"
date: 2008-10-26
forum: General Help
---

### Post by Gnu32 on 2008-10-26
Greetings,

On my internal drive I have two partitions: a swap and the ubuntu partition in a 10 GB space. Because I now use an external drive for swap I decided to convert the internal one into a 10 GB fat32 partition for VirtualBox to use.

I used gparted to do this task and it was successful. The partition is /dev/sda1 (never understood why it's not hda*) and I created the folder /media/virtual for this partition. I chmod' it to a+rwx and chown'd it to my user name and group. Then I setup the following entry on /etc/fstab:

```
/dev/sda1 /media/virtual vfat defaults,utf8 0 0
```

And finally mounted it. The problem here however that is it's behaving like a locked partition. I can't access it within ROX-Filer or terminal unless i'm using sudo. Using [FONT="System"]ls -al[/FONT] on /media/ revealed:

```
d---------  2 root  root  8192 1970-01-01 04:00 virtual
```

When unmounted:

```
drwxrwxrwx  2 gnu32 gnu32  4096 2008-10-26 01:46 virtual
```

I tried all sorts of solutions and fixes in fstab like the following:

```
/dev/sda1 /media/virtual vfat defaults,utf8,umask=777 0 0
/dev/sda1 /media/virtual vfat defaults,utf8,user,umask=777,uid=gnu32 0 0
/dev/sda1 /media/virtual vfat defaults,utf8,dmask=777,fmask=777 0 0

```

All to no avail. Some had the effect of making the partition actually browsable by normal user but not writable unless in sudo.

There is something painfully obvious here and I remember having this problem before but I just can't figure out what the solution is. Any pointers?

---

### Post by geirha on 2008-10-26
umask and dmask works the "opposite" way of chmod. They say which permissions should NOT be set, so 777 gives all files and folders of the mounted fat filesystem 000 permissions.

Try with these options: umask=002,fmask=113,uid=yourusername,gid=admin 

It will make all files and directories owned by yourusername:admin and all directories will have mode 775 and all files will have mode 664.

EDIT: And keep the defaults,utf8 too

---

### Post by Gnu32 on 2008-10-26
Guh, bizzare that. Haha, cheers loads!

---

