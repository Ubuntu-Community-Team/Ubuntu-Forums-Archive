---
title: "NTFS Support? Can I mount a NTFS partition? (read only)"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by veraction on 2005-04-08
Just installed Ubuntu 5.04 today. I'm new to Ubuntu. I used to use Fedora Core 3 - but I'm still a relative newbie to linux. Anyways

I'm trying to mount my NTFS drive. It seems like I can mount it, however I cannot view whats in the mnt directory where its mounted. When I try to open the folder using File Browser, it says I don't have permission to view the contents.

I've successfully mounted two FAT32 drives. I've also done some mounting in FC3 (I needed to download the NTFS kernel modules for that)

**Do I need to download special NTFS kernel modules in order to read a NTFS partition?**

I ran the command, ```
cat /proc/filesystems 
```, and it listed NTFS - so I assumed that I should be able to read NTFS mounts..

Help Please :)

---

### Post by jiyuu0 on 2005-04-08
though this 4.10 guide, but it should work on 5.04 too.
[http://ubuntuguide.org/4.10/index.html#windows](http://ubuntuguide.org/4.10/index.html#windows)

will put in this section to 5.04 later

---

### Post by telmo on 2005-04-08
If you already know which partition it is, just do this:

```
sudo mkdir /media/<partition name>
```

and add this line (edit it first) to you /etc/fstab

```
/dev/<partition>       /media/<partition name>  ntfs    user,umask=0222      0       0
```

with

```
sudo gedit /etc/fstab
```

For example... My Windows ntfs partition is in /dev/hda1, so i do:

```
sudo mkdir /media/Windows
```

then i....

```
sudo gedit/etc/fstab
```

to add this line

```
/dev/hda1       /media/windows  ntfs    user,umask=0222      0       0
```

Now just do

```
sudo mount -a
```

to refresh the mounting thing... :)

---

### Post by veraction on 2005-04-08
Ah, Thanks a lot. I guess my problem was cause I was using defaults, rather than ```
user,umask=0222
```

Now I just have to find a video player which actually plays movies (VLC probably) and music player for mp3s (gotta find that plugin for XMMS)  :)

Thanks again

---

### Post by Gandalf on 2005-04-14
[QUOTE=veraction]Ah, Thanks a lot. I guess my problem was cause I was using defaults, rather than ```
user,umask=0222
```

Now I just have to find a video player which actually plays movies (VLC probably) and music player for mp3s (gotta find that plugin for XMMS)  :)

Thanks again[/QUOTE]
 i would use
```

/dev/hda1       /media/windows  ntfs    ro,user,umask=0222      0       0

``` to force read only, because if for some reason a root tried to write, you will have a damaged hard disk

---

### Post by exodus on 2006-04-13
thx m8... works like a charm...

---

