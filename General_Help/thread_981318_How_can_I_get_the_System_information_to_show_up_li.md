---
title: "How can I get the System information to show up like in intrepid"
date: 2008-11-13
forum: General Help
---

### Post by cmsimike on 2008-11-13
I've just SSH'ed into my friend's newly upgraded Intrepid box. I got this very cool status screen:

  System information as of Thu Nov 13 13:40:02 PST 2008

  System load:  1.23              Swap usage:  2%     Users logged in: 1
  Usage of /:   23.4% of 1.35TB   Temperature: 40 C
  Memory usage: 19%               Processes:   195

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

which he says just started appearing after the upgrade. I was curious what I can install to get this to show when I ssh into my Hardy box.

Thanks!

---

### Post by JoeLinux117 on 2008-11-14
Install "landscape-common"

---

### Post by loomsen on 2008-11-14
You could combine some simple commands as well... Your OS shipd with them anyway, why not use them...


something like that for instance:
```

me@tiffany:~$ date;sudo smartctl --all /dev/sda | grep -i temp|cut -d "(" -f1 | cut -d "-" -f2;uptime;

Sat Nov 15 03:49:47 CET 2008
       39 
 03:49:47 up  1:22,  2 users,  load average: 1.10, 0.92, 0.79

```

Conky could be what you want maybe.

---

