---
title: "Can't &quot;make install&quot; in terminal"
date: 2008-11-14
forum: General Help
---

### Post by slapshots on 2008-11-14
Hey, I'm a pretty new user, and I've been trying to install mplayer, but every time I type 'make install' it comes up with an error saying permission not granted. I'm the only user on the computer and I'm marked as an administrator. The command 'make' works fine, but I've also tried 'make install' on other programs and it keeps coming up with the same error. help?

---

### Post by rampageoberon on 2008-11-14
You need root permissions for that. Use sudo

```
sudo make install
```

Personally i'd use the version in the repository or use checkinstall so that there is a record with aptitude.

---

### Post by mc4man on 2008-11-14
edit: redundant

you may want to keep keep your build folder around in case you wish to uninstall, in which case you'd cd to it and run 
sudo make uninstall

You can also run your app from the build folder without installing, useful to test your build or have multiple versions of same app.

---

### Post by slapshots on 2008-11-14
Thanks for the help, sudo solved the problems and I'll keep the install folders.

---

### Post by taurus on 2008-11-14
You know that mplayer is available from the repos, right?

```
sudo apt-get update
sudo apt-get install mplayer
```

---

