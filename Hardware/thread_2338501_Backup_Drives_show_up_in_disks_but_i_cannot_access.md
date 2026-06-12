---
title: "Backup Drives show up in disks but i cannot access them"
date: 2016-09-28
forum: Hardware
---

### Post by Mike E Tomlinson on 2016-09-28
My system:
p9x79 delux mainboard
gforce 760
6 HD's  4 quick removable internal drives two external esata drives.
p190 antec Case
Two DVD drives one is blue Ray. 

I run Win 10 on one of my drives. I switch drives and run Ubuntu 16.04
or Ubuntu 15
The other drives are for backup. 
The problem started when I activated the drives when I had windoze running. 
After that  I couldn't access them with ubuntu 16.04 LTS. Even with Wine on my ubuntu 15 lts

---

### Post by Bashing-om on 2016-09-28
Mike E Tomlinson; Hello;

As a place to start.
Booted up on ubuntu, problem drives connected and to a terminal.
what returns:
```

sudo blkid -c /dev/null -o list
sudo parted -l

```

and we see what tale is told
[INDENT][INDENT]where we go from here
[/INDENT][/INDENT]

---

### Post by reese1379 on 2016-09-28
Maybe you have  [fast boot]("http://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/") running under Windows and it is locking the drivers.

---

