---
title: "Enemy Territory install Trouble"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by Philabrow on 2009-08-25
I'm Having trouble insalling enemy territory, I followed everything at this link for a fresh install of the game: [https://help.ubuntu.com/community/EnemyTerritory#Making%20Startup%20Scripts%20More%20Friendly](https://help.ubuntu.com/community/EnemyTerritory#Making%20Startup%20Scripts%20More%20Friendly)

But no matter where I download it from it's just doing this 
```
philip@philip-laptop:~$ sudo sh ./et-linux-2.60.x86.run
[sudo] password for philip: 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................................................................
Extraction failed.
Signal caught, cleaning up

```Please any help would be appreciated, I wanna play this kickass game!:) Now I am using a pretty poor computer and I'm running netbook remix. I don't know if thats why, hope not :(.

---

### Post by Partyboi2 on 2009-08-25
Hi, have you checked that the md5sum matches?
It should be 
```
md5sum et-linux-2.60.x86.run
``````
2d2373f29f02e18d365d7f1860eee435
```

---

### Post by Philabrow on 2009-08-25
Yer the code matches...

---

### Post by Partyboi2 on 2009-08-25
Have you got enough free space in the location that you are extracting it to?

---

### Post by Philabrow on 2009-08-25
How much free space do I need, I've got about 2 gig left on my machine

---

