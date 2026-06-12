---
title: "Help uninstalling ubuntu"
date: 2008-11-08
forum: General Help
---

### Post by kris07LX on 2008-11-08
Ok so a little while back i was surfing the web and heard some good stuff about ubuntu so i decided to try it out i downlaoded a copy put it on a cd booted into ubuntu from the disk and had the little pogram thingie do the bual booting for me. So my computer doesnt have a very large hard drive so pertty soon i began to run out of room. So im wondering how can i uninstal ubuntu without messing up windows and in addition how can i do it without deleting anything on windows since i have a lot of stuff id rather not have be deleted any help would be great thank you:confused:

P.S. excuse my lack of periods commas etc i wrote this pretty hastily lol :D

---

### Post by DGortze380 on 2008-11-08
> **kris07LX said:**
> Ok so a little while back i was surfing the web and heard some good stuff about ubuntu so i decided to try it out i downlaoded a copy put it on a cd booted into ubuntu from the disk and had the little pogram thingie do the bual booting for me. So my computer doesnt have a very large hard drive so pertty soon i began to run out of room. So im wondering how can i uninstal ubuntu without messing up windows and in addition how can i do it without deleting anything on windows since i have a lot of stuff id rather not have be deleted any help would be great thank you:confused:

P.S. excuse my lack of periods commas etc i wrote this pretty hastily lol :D

If I understand correctly, you have a dual boot system with Ubuntu and Windows. You have not changed any of the default options. If this is the case continue, if not, please provide us with the output of 
```

df -l

```

1) Back up all important data on both OS's
2) Boot your Live CD
3) Open a Terminal and type
```

sudo gparted

```
4) Delete the only partition that is formatted as ext3
5) Delete the only partition that is formatted as SWAP

You now have two options. If you have appropriate backups, I suggest step 6. Otherwise choose step 7. Do not do both.

6) Select the only partition formatted NTFS and resize it to utilize our newly created free space. This will take a long time. Your C:\ partition in windows should now have all that extra space added back to it.
7) Select you newly created free space. Select new partition. Format it as NTFS. This should show up in Windows as D:\ (or similar)
8 ) Close GParted. Reboot remembering to remove the Live CD from your drive.

---

### Post by bodhi.zazen on 2008-11-08
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927) 
 
    wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by kris07LX on 2008-11-10
wait should i boot my ubuntu live cd or windows?

---

### Post by kris07LX on 2008-11-10
ok nvm i did it but when i try to delte ext3 it says "please unmount any logical partitions having a number higher than five" and it wont even let me delte swap it has some key icon next to its name

---

