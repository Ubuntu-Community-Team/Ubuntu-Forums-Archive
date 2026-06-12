---
title: "removing unneeded services"
date: 2008-10-27
forum: General Help
---

### Post by hammeraxe on 2008-10-27
my comp is a 600 MHz PIII with 256 MB RAM. it runs xubuntu 8.04 and it is pretty usable. yet it could be faster. i tried to look for ways to speed the whole thing up.
i installed boot-up manager to remove unwanted services, for instance power saving for laptops (as this is a desktop) but there are a lot of other services and im not really sure what they do and do i actually need them.

is there a list explaining which services are crucial and which are not?

do you have any other suggestions regarding the speedup of this machine?

---

### Post by ddrichardson on 2008-10-27
```
sudo update-rc.d daemon_name remove
```

Will remove a daemon, there is also a [guide]("http://ubuntuforums.org/showthread.php?t=89491") on the forums to speeding up boot time by removing daemons.

---

