---
title: "Nvidia Driver Help"
date: 2008-07-28
forum: General Help
---

### Post by SunThief on 2008-07-28
I downloaded a .run file of an nvidia driver from nvidia's site that says it was for Linux, and it won't run.  What do I do?

---

### Post by tuxxy on 2008-07-28
Open a terminal

Navigate to the directory of the .run file, For example if on your desktop type 

```
cd Desktop
```

Now edit the permissions,

```
chmod +x example.run
```

Now run the installer by entering;

```
./example.run
```

---

### Post by SunThief on 2008-07-28
It says it can't find the file.

---

### Post by tuxxy on 2008-07-28
Make sure you rename it to your filename and location, I just used the desktop and that filename as an example.

Also you may need to run it as root,

```
sudo ./example.run
```

---

### Post by psyopper on 2008-07-29
Have you tried ```
sh example.run
```

---

### Post by Bender2k14 on 2008-07-29
I do not use Xubuntu, but does Xubuntu have EnvyNG?...have you tried using that to get your driver?  (For me, EnvyNG is in Applications->System Tools->EnvyNG)

---

