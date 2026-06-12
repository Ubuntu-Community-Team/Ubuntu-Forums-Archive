---
title: "Auto mount"
date: 2008-11-30
forum: General Help
---

### Post by kaygeezo on 2008-11-30
am a new user of ubuntu( linux systems as well) i want my Data partition formated by windows NTFS to be mounted automatically when i log in..i have tried to use configurator editor gconf -editor ,but the portion says the key is read only and cant be overwritten!.need help on this:lolflag:

---

### Post by Elfy on 2008-11-30
Install ntfs-config - from a terminal

```
sudo apt-get install ntfs-config
```

It will have a menu item in System Tools I believe - that will setup your ntfs partitions for automount

---

### Post by kaygeezo on 2008-11-30
> **forestpixie said:**
> Install ntfs-config - from a terminal

```
sudo apt-get install ntfs-config
```

It will have a menu item in System Tools I believe - that will setup your ntfs partitions for automount

E:Could not get lock /var/lib/dpkg/lock -open( 11 resourse temporarily unavailable)
E: unable to lock the administration directoey (/var/lib/dpkg/), is another process using it?


thats what happened after execution the command

---

### Post by Elfy on 2008-11-30
Usually means you have add/remove or synaptic open or are already using apt-get or aptitude in another terminal.

Close all the other's and try again.

---

