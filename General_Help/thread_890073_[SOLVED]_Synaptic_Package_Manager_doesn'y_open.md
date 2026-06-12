---
title: "[SOLVED] Synaptic Package Manager doesn'y open"
date: 2008-08-14
forum: General Help
---

### Post by greenco on 2008-08-14
I just clicked on my Ubuntu 8.04 Synaptic Package Manager, to run it and I received this error message. What is it telling me? It was working OK yesterday.

E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Thanks

---

### Post by damis648 on 2008-08-14
Looks like you have no more space on your / partition. Try System>Administration>System Monitor and check the "File Systems" tab to make sure.

---

### Post by greenco on 2008-08-14
Yes, that shows me that "/" does not have any available space. It shows the partition size as 18.5 GiB, Free as 16.6 GiB and Available as 0 bytes. What could have caused this and how can I correct it?

---

### Post by mali2297 on 2008-08-14
Try
```

sudo apt-get clean

```
That clears out downloaded packages.

---

### Post by greenco on 2008-08-14
mali2297, 
does that mean I would have to add everything back (IE. MPlayer, KDE DVD/CD program, Nvidia graphics driver and etc.)? Or are you talking about different types of programs?

---

### Post by mali2297 on 2008-08-14
> **greenco said:**
> mali2297, 
does that mean I would have to add everything back (IE. MPlayer, KDE DVD/CD program, Nvidia graphics driver and etc.)? Or are you talking about different types of programs?

Packages are downloaded as deb files. After a program has been installed, the deb files are kept in a cache directory but they are no longer needed. The command that I gave just clears out this cache. It's safe.

---

### Post by greenco on 2008-08-14
mali2297, that worked great!!!!

I will put this little item in my help archive, for future reference.

Is this cache folder something I can look at, from time to time, to see if it is filling up?

Thanks a million.

---

### Post by mali2297 on 2008-08-14
You probably have more unnecessary files that fill up space. I think there is a graphical disk usage analyzer available in the menus, check under *Applications &#8212;> Accessories &#8212;> Disk Usage Analyser*.

---

### Post by greenco on 2008-08-14
NEW Problem

I just looked at the System Monitor again and I noticed this entry that talked about a gvfs-fuse-daemon. I listed the coulmns vertically, because they are too wide to fit horizontally. I can't find this ".gvx" in the /home/coleman folder. How can I get rid of it? I believe this is the reason I can't open movie files. Everything worked OK yesterday.

Device		   						  	    	
gvfs-fuse-daemon 

Directory
/home/coleman/.gvx

Type
fuse.gvs-fuse-daemon

Total
18.5 GiB

Free
219.5 MiB

Available
0 Bytes

Used
18.3 GiB

---

### Post by greenco on 2008-08-14
I just used sudo su to unmount the /home/coleman/.gvfs and the entry went away. I would still like to know what caused it in the first place.

Thanks again

---

