---
title: "Ubuntu Home Folder"
date: 2008-10-16
forum: General Help
---

### Post by Terry Jones on 2008-10-16
What is the public folder used for in a user's home directory?
Also is it possibe to set home folders to privite so the if a user goes into another user folder they will get access denide for read.

---

### Post by jerome1232 on 2008-10-16
It's used to store all of your personal files (similiar to My Documents in xp, Users in Vista) you can also install programs that are just for your user here.

If you want to set it as only browseable/readable by you then this will do it, you shouldn't have to make the command recursive.

```
chmod -o-rx ~/
```

---

### Post by armageddon08 on 2008-10-16
Just go to /home. There you will find a folder with your username. Right click it, select 'Properties', goto tab 'permissions'. Under "Others", select None. That should do it.

The public folder is for sharing with other users. Just like the "Shared" folder in Windows.

---

### Post by Terry Jones on 2008-10-16
Is the public folder a local shared folder or networked shared  folder or both?

---

### Post by geirha on 2008-10-16
There's no public folder created automatically, so that's a folder you or the system administrator has created. It's common to have a folder called public_html though, in each home directory, if the system runs a web server.

---

### Post by Ms_Angel_D on 2008-10-16
> **geirha said:**
> There's no public folder created automatically, so that's a folder you or the system administrator has created. It's common to have a folder called public_html though, in each home directory, if the system runs a web server.

Both hardy and Ibex have folders named public created by default in the home folder as well I just finished installing gutsy on virtualbox and there is also a default public folder in the home folder.

---

### Post by geirha on 2008-10-16
> **MetalHellsAngel said:**
> Both hardy and Ibex have folders named public created by default in the home folder as well I just finished installing gutsy on virtualbox and there is also a default public folder in the home folder.

Oh, my system doesn't create those, though my system was originally edgy, and I've been upgrading to Hardy since then, so there's probably still configuration files from previous releases hanging around. If you say so, I believe you, and I stand corrected :)

---

### Post by Ms_Angel_D on 2008-10-16
> **geirha said:**
> Oh, my system doesn't create those, though my system was originally edgy, and I've been upgrading to Hardy since then, so there's probably still configuration files from previous releases hanging around. If you say so, I believe you, and I stand corrected :)

;) I figured as much I believe it's only on fresh installs (strange as that may be)

Lucky you being able to upgrade without many troubles, I hope I have the same luck going from hardy to ibex :D

---

### Post by jerome1232 on 2008-10-16
And it's not shared over the nework or anything, that's just it's purpose of existence, it's permissions aren't set any differently than the other folders in your ~/

---

