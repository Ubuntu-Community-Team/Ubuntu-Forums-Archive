---
title: "Ubuntu Linux Toolbox"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by fr3lonbrun on 2008-12-14
I'm new to Ubuntu-and to getting into command lines of any kind for that matter. I've been learning, albeit slowly, from a couple of books. In "Ubuntu Linux Toolbox," Negus has as a lesson the extracting of a .deb file to a tmp file using dpkg:
   sudo dpkg -x rsync_2.6.9-3ubuntu1_i386.deb /tmp/rsync_contents

When I did it, I got:

   dpkg-deb: failed to read archive `rsync_3.0.3-2ubuntu1_i386.deb': No such file or directory

    I changed the version, of course, using the current version for Intrepid, which is 3.0.3-2. Still, the same thing happened. I read about a bug that existed, but could find no fix. It sucks because he uses this example to explain some other things. What continually shows up is that there IS no such file or directory - and yet I use dpkg to confirm that there IS such an rsync_3.0.3-2ubuntu1 for i386. I've checked my syntax over and over, and I see no mistakes there. I even uninstalled it and then reinstalled it using dpkg to make sure a .deb file existed in the proper archive. So what gives? 
    By the way, to give as much info as possible, I checked and yes, my "/tmp/rsync_contents" file is where it should be. I'd appreciate some insight into what's wrong with my method, or what exactly I'm missing in understanding the bug description in the manpages. Thanks.

---

### Post by pp. on 2008-12-14
I don't know the commands involved. However, your problem description seems to imply that dpkg expects a file in your file system while you state that the named archive "existed". Existed where - on the archive server or in your local file system?

---

### Post by bapoumba on 2008-12-14
Moved to Installation & Upgrades.
What is the output of:
```
apt-cache policy rsync
```

---

