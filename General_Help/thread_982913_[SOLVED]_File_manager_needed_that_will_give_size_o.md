---
title: "[SOLVED] File manager needed that will give size of directory structure."
date: 2008-11-15
forum: General Help
---

### Post by DoctorBeaver on 2008-11-15
I've got Studio and at the moment I'm using the bog standard file manager. I often use my 2Gb USB memory stick to transfer files between PCs. However, more often than not I want to transfer an entire directory structure.

The problem is I don't know how big the structure is so I have no way of knowing whether the entire structure will fit in 1 go unless I work through the whole lot summing the sizes of files manually. That's a real pain as many of the structure have 20 or more sub-folders and hundreds of individual files.

Is there a file manager that will go through the entire structure for me and display the total number of bytes?

---

### Post by nothingspecial on 2008-11-15
Don`t know if this is what you want but
```

du -hs /path/to/directory
```

---

### Post by philinux on 2008-11-15
Not on buntu just now but IIRC nautilus prefs include directories will do the trick.

---

### Post by DoctorBeaver on 2008-11-15
philinux - no, it doesn't.

nothingspecial - I don't know much about command line entry. What does that command do?

---

### Post by nothingspecial on 2008-11-15
It tells you the size of a directory so eg

Say you have a external hard drive called disk with your music on it and have sgt pepper by the beatles in a directory called mp3.
```

du -hs /media/disk/mp3/beatles/sgt_pepper
```will tell you how big the sgt pepper album is.

```
du -hs /media/disk/mp3/beatles
```
will tell you how big your beatles directory is (you may have other beatles albums)

```
du -hs /media/disk/mp3
```
will tell you how big your entire mp3 directory is and so on.

---

### Post by Carl Hamlin on 2008-11-15
> **DoctorBeaver said:**
> Is there a file manager that will go through the entire structure for me and display the total number of bytes?

In nautilus you can get to a 'properties' dialogue via the right-click context menu which will recurse subdirectories and give you a size total. I've found this total to be slightly off in the past, but it's a reasonable estimate.

---

### Post by DoctorBeaver on 2008-11-15
nothingspecial - by the time I've typed that in a few times, it would be no quicker than using Right-Click->Properties. But thanks anyway.

Carl Hamlin - I'm aware of that, but it still only gives me 1 figure at a time.

Scenario:-

I have a 4 level directory structure with, say, 5 folders at each level. I've got 2Gb on my memory stick. I look at the properties of the main directory and it tells me the whole structure is 3.6Gb. I therefore have to leave out 1.6Gb when I copy the structure.

Using properties again for the 2nd level directories I'd have to do it for each 1 to find the best to leave off. What I want is to be able to see at a glance the sizes of the sub-directories.

I do this sort of thing quite a lot so it's not just a 1-off problem. On WinXP I used FreeCommander which did exactly what I want but it doesn't seem to be available for Linux.

---

### Post by SamNSane on 2008-11-15
Would Disk Usage Analyzer (baobab) work for you? I use it for similar purposes.

---

### Post by DoctorBeaver on 2008-11-15
> **SamNSane said:**
> Would Disk Usage Analyzer (baobab) work for you? I use it for similar purposes.

Well that certainly helps. At least I can see the sizes of all the directories. It's a great improvement on what I was having to do.

Thanks for that.

(Pity it can't copy & paste the files for me)

---

### Post by nothingspecial on 2008-11-16
I see what you want to do, in that case```

```

cd into the top directory say it`s your video folder
```

cd Videos
```

Then add a star,this will give youthe size of every folder in there -

```
du -hs *
```

du -a will give you the size of every single file although that would make alot of reading.  Use the gui if you like, this is just for info.

---

### Post by DoctorBeaver on 2008-11-16
nothingspecial - thanks.

---

### Post by SamNSane on 2008-11-16
> **DoctorBeaver said:**
> Well that certainly helps. At least I can see the sizes of all the directories. It's a great improvement on what I was having to do.

Thanks for that.

(Pity it can't copy & paste the files for me)

Yeah, I just use side-by-side instances of disk usage analyzer and nautilus on systems other than my own. On my own systems I use commercial software (the ONLY commercial software, besides  restricted drivers in a couple of cases, on my Linux systems) called Beyond Compare Pro. It's the best folder / file comparison software I've ever seen, and it and ImgBurn were the only software in Windows that I couldn't really find replacements for. (BC is available for Linux now, and ImgBurn runs in WINE.) BC would definitely do the job for you, but -- unless you have use for its other features -- might be overkill for your purposes.

---

### Post by sdowney717 on 2008-11-16
check into kdirstat

And there is another I cant remember what it is called. it shows a directory tree structure that when you click on items it expands and reveals size and location in extreme detail.

---

### Post by DoctorBeaver on 2008-11-16
sdowney717 - that looks like what I'm after. Thank you.

I've just started using it & it's perfect. Thank you again.

---

