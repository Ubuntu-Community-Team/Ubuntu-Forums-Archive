---
title: "Copying Files to seperate partition"
date: 2009-01-24
forum: Hardware
---

### Post by MikeyUbun2 on 2009-01-24
i made a seperate EXT3 partition on my harddisk to store my files while i install 8.10 but i cant copy anything bacause i have no permission.
so i went into permissions and it said:
Owner : root (create/delete files)
Group : root (access files)
Others:      (access files)
i cant change permissions because the drop downs are disabled.

as i write that last sentence there it made me realize that i wont be able to do it the GUI way so i remembered haw to do the same thing in the terminal!!! this was totally one of those :shock::-o:idea: holy crap EUREEKA!!! moments so here is wat i did
I use:
```
sudo chmod 777 /media/Files
```
so now i can write files!

i am still posting this anyways to help some peepz out if they have these problems.

---

### Post by taurus on 2009-01-24
Or you can change the ownership of /media/Files from root to your login name so you can write to it anytime you want.

```
sudo chown -R *username*:*username* /media/Files
```
But whichever makes you happy.

---

