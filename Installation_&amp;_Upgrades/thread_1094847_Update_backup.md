---
title: "Update backup"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by rules on 2009-03-13
Hi all

I want to revert back to Hardy (had less problems there) but I would like to backup the 250Mb update that I had to do yesterday so that if I install Intrepid again I don't have to do it all over again.

Any ideas?

Actually just thought of another solution in case the above mentioned isn't possible. I usually install linux into a root partition and into a home partition. Is there a way of combining them without having to reinstall (move home to same partition as root)? Then I can use the other partition for Hardy and triple boot.

---

### Post by cariboo on 2009-03-13
You are going to have to do a complete reinstall of Hardy, as there is no way to revert to a previous version. If you want to backup up the updates, they are located in /var/cache/apt/archives, unless you have run:

```
sudo apt-get clean
```

since you installed Interpid, there may be packages for programs you installed after you finished installing Intrepid, so be aware that there will be more files in the directory than just the updates.

Jim

---

