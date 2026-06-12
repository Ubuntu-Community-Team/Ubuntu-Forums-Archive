---
title: "[SOLVED] How to organize my server?"
date: 2008-10-25
forum: General Help
---

### Post by ARhere on 2008-10-25
I want an opinion from the advanced Linux system administrators out there.

My new Web/Print/File/Mail Server is pretty kewl, an Intel Atom motherboard that only consumes 4 watts!!!  <-- no kidding!  It has 500GB dual drives set up as a soft mirror.

The question is, how do I mount/organize the 500GB partition?
The data is pictures, movies, and other junk plus I usually mount the other computers /home/<user> to the server.

Should I mount the 500GB mirror as /home?  If I do that, then I have to create...
/home/<users>
/home/music
/home/taxes
/home/movies
/home/data
...etc.. about 8 different folders.

Is this not bad karma to create folders in /home that are not users?  Any other suggestions on how I should do this?

-AR

---

### Post by dcstar on 2008-10-25
> **ARhere said:**
> 
.........
Should I mount the 500GB mirror as /home?  If I do that, then I have to create...
/home/<users>
/home/music
/home/taxes
/home/movies
/home/data
...etc.. about 8 different folders.

Is this not bad karma to create folders in /home that are not users?  Any other suggestions on how I should do this?

-AR

As long as you don't **ever** create user accounts with those names, you should be fine - but be aware that /home is the assumed place for user directories.

---

### Post by berriop on 2008-10-25
have a look in this Debian manual
[http://d-i.alioth.debian.org/manual/en.i386/apc.html](http://d-i.alioth.debian.org/manual/en.i386/apc.html)

---

### Post by ARhere on 2008-10-25
> **berriop said:**
> have a look in this Debian manual
[http://d-i.alioth.debian.org/manual/en.i386/apc.html](http://d-i.alioth.debian.org/manual/en.i386/apc.html)

I have thought about partitioning up the 500GB, but I am not sure how my data will grow.  Sometimes we are into pictures and taking lots, sometimes I am saving every Linux iSO I come across, and sometimes my wife and I are making lots of movies.  (*NO, not **those** movies... sick'o*)

Plus, I do not think I can make 8 different partitions

How do other people organize all pf their important data?

-AR

---

### Post by bab1 on 2008-10-25
I don't think you should use /home at all.  See:
[[COLOR="Blue"][SIZE="2"]here[/SIZE][/COLOR]]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") and [[COLOR="Red"][SIZE="2"]here[/SIZE][/COLOR]]("http://http://www.pathname.com/fhs/")

---

### Post by geirha on 2008-10-25
Any directory may be a mount point, so why not create a partition and mount it as /home/yourusername/Music and another partition mounted at /home/yourusername/Video etc ... ?

A filesystem can also be mounted several times, so you can mount the music partition in all homes ...

EDIT: Oh and perhaps mount-binding is also a nice option. Make a huge partition and mount it at /mnt/something, then create folders like Music, Video, Photo etc inside /mnt/something, then mount those directories to other places:

```
sudo mount -o bind /mnt/something/Video /home/yourusername/Video
```

---

### Post by ARhere on 2008-10-28
> **geirha said:**
> Any directory may be a mount point, so why not create a partition and mount it as /home/yourusername/Music and another partition mounted at /home/yourusername/Video etc ... ?

A filesystem can also be mounted several times, so you can mount the music partition in all homes ...

EDIT: Oh and perhaps mount-binding is also a nice option. Make a huge partition and mount it at /mnt/something, then create folders like Music, Video, Photo etc inside /mnt/something, then mount those directories to other places:

```
sudo mount -o bind /mnt/something/Video /home/yourusername/Video
```

Binding is not a bad idea at all.  Can I do something like this...
mount /dev/sda1 --> /data
bind /data/music --> /home/<user>/Music
bind /data/<user>/files --> /home/<user>/files

???   -AR

---

### Post by geirha on 2008-10-28
Yes. The entries in /etc/fstab would look something like this.
```
/dev/sda1 /data ext3 defaults 0 2
/data/music /home/user1/Music ext3 bind 0 0
/data/music /home/user2/Music ext3 bind 0 0
/data/user1/files /home/user1/files ext3 bind 0 0
/data/user2/files /home/user2/files ext3 bind 0 0

```

---

### Post by ARhere on 2008-10-29
You rock.

I knew about this but I just never thought to use it like this.

Thank you,
-AR

---

