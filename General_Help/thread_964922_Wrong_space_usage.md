---
title: "Wrong space usage ?"
date: 2008-10-31
forum: General Help
---

### Post by ercdvs on 2008-10-31
Tell me if this is a stupid question, or if i'm reading things wrong..

I have 2 drives in this system a 200gb and a 500gb ..

500gb is mounted /home
200gb is mounted /  and is the boot drive

Looking at the totals from df -h i notice something funny:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             181G  708M  171G   1% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  260K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.7M  502M   1% /dev
tmpfs                 505M     0  505M   0% /dev/shm
/dev/sdb1             459G  199M  435G   1% /home

I understand fully that a 500gb is 459gb formatted, but how does a 459gb drive with 199M used have 435gb left?   This is on a freshly installed 8.10 server, with one user.  the home directories are empty save for what is there by default.  Same with with /  

Can someone explain this ?

---

### Post by bryonak on 2008-10-31
With every file system, you will lose hard drive space in two ways:

1. The file system itself has a structure, which in turn introduces overhead. Things like journaling metadata further increase this overhead, with ext3 the "loss" is typically 9.1% - 9.2% (about the same as OSX default file system HFS+).
The result is what you see when installing a system on a drive labeled as 500GB and then having only 459GB.
Without a file system mapped to it, it would actually have it's full 500GB, but this raw space couldn't be accessed in a efficient (modern) way.

2. Your file system is divided into 'blocks', which have a typical size between 1KB and 4KB, depending on how you set it up (I think Ubuntu's default is 4KB). This is a necessary consequence of the file system's design and functionality.
The drawback is that every inode (single file you save on your drive) will take such a block for it self, or more if it's size exceeds the block size... so you will have a file of 0.5KB taking up 4KB. The same goes for folders, because the information about the folder has to be saved somewhere, even if it's empty.
This is usually not much of a problem, since you have less than a few thousand files smaller than 4KB on a typical system, so their total won't be more than a few MB.
Big files (everything over a few dozen KB) on the other hand obviously use about the same disc space as their content.

I'm not sure whether these two factors are strictly separated, i.e. maybe some of the info about folders is stored in the default file system structure, etc... but I hope you get the basic idea.

So... your question isn't dumb at all, and your reading skills don't seem to be lacking either as far as I can tell ;)
Just a hint: next time use the [code ][/code ] tags instead of [quote ] for such output, because they preserve spacing.

---

### Post by ercdvs on 2008-10-31
> **bryonak said:**
> With every file system, you will lose hard drive space in two ways:

1. The file system itself has a structure, which in turn introduces overhead. Things like journaling metadata further increase this overhead, with ext3 the "loss" is typically 9.1% - 9.2% (about the same as OSX default file system HFS+).
The result is what you see when installing a system on a drive labeled as 500GB and then having only 459GB.
Without a file system mapped to it, it would actually have it's full 500GB, but this raw space couldn't be accessed in a efficient (modern) way.

2. Your file system is divided into 'blocks', which have a typical size between 1KB and 4KB, depending on how you set it up (I think Ubuntu's default is 4KB). This is a necessary consequence of the file system's design and functionality.
The drawback is that every inode (single file you save on your drive) will take such a block for it self, or more if it's size exceeds the block size... so you will have a file of 0.5KB taking up 4KB. The same goes for folders, because the information about the folder has to be saved somewhere, even if it's empty.
This is usually not much of a problem, since you have less than a few thousand files smaller than 4KB on a typical system, so their total won't be more than a few MB.
Big files (everything over a few dozen KB) on the other hand obviously use about the same disc space as their content.

I'm not sure whether these two factors are strictly separated, i.e. maybe some of the info about folders is stored in the default file system structure, etc... but I hope you get the basic idea.

So... your question isn't dumb at all, and your reading skills don't seem to be lacking either as far as I can tell ;)
Just a hint: next time use the [code ][/code ] tags instead of [quote ] for such output, because they preserve spacing.

I am aware that the 'on the box' 500gb is not actual space when the file system is applied.

Your block size idea has merit.. but I have no files actually on the system.  the 500gb drive is dedicated to /home, and that snapshot was taken literally just after the system came up for the first time, with one user.

---

### Post by geirha on 2008-10-31
> **ercdvs said:**
> I am aware that the 'on the box' 500gb is not actual space when the file system is applied.

Your block size idea has merit.. but I have no files actually on the system.  the 500gb drive is dedicated to /home, and that snapshot was taken literally just after the system came up for the first time, with one user.

When you create a user, some hidden configuration files will be copied to the home-folder. Though 199MiB sounds a bit much ...

This command, run in a terminal, should give you an idea of where that space has gone
```
du -x -h --max-depth=1 $HOME/
```

---

### Post by bryonak on 2008-10-31
Right, your space "loss" really is rather big.
Try ```
du -sch --block-size=1
``` in your home folder, which will give you the disk usage of your blocks.

Just an offshoot, though I think you did that already... but to rule out this trivial possibility: make sure there's no "shadow" partition, unpartitioned space, etc...


EDIT: hehe, didn't see geirha's posting... he's right, for instance there is a folder called Examples, I don't know how big it is because I deleted it, but it contains some movies/audio files. Then again, maybe not, because you said you're using the server edition.

---

### Post by ercdvs on 2008-11-02
I actually followed a posting on the reserved space for root on an ext3 system.   Typically 5% (!!) is reserved for root, but can go as low as 1% ..

```
tune2fs -m 1 /dev/sda1
```

fixed me right up, and recovered a large amount of my missing space.

---

### Post by mdurham on 2008-11-02
> **ercdvs said:**
> I actually followed a posting on the reserved space for root on an ext3 system.   Typically 5% (!!) is reserved for root, but can go as low as 1% ..

```
tune2fs -m 1 /dev/sda1
```

fixed me right up, and recovered a large amount of my missing space.

If you are adjusting the 500 mb drive, why not tune2fs -m 0? As you don't need any reserved space.

---

### Post by ercdvs on 2008-11-03
> **mdurham said:**
> If you are adjusting the 500 mb drive, why not tune2fs -m 0? As you don't need any reserved space.

I was under the impression 1 was the lowest ... but since its /home .. that makes more sense ..

its 500 GB btw.

---

