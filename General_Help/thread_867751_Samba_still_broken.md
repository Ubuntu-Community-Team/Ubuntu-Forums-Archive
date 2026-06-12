---
title: "Samba still broken"
date: 2008-07-23
forum: General Help
---

### Post by Hamm on 2008-07-23
I am running 8.xx.xx and Samba still is broken. Is they any fixes at all, short of going back to 7.10?

---

### Post by DagMan on 2008-07-23
Mine was broken, removed windbind and restarted samba.  I have no idea what the winbind service is, but in my circumstance the machine is restricted to the LAN in my house so it isn't much of a concern for me.

---

### Post by danwood76 on 2008-07-23
There are a few things that cause samba issues.

As DagMan said winbind does, this service resolves netbios names so samba can use the IPs but its a bit buggy.
I have a feeling it has something to do with the problem I experianced also:

Another thing I found was OpenDNS, for some reason it attempts to locate samba servers accross the internet which causes samba to crash nautilus.
(It may happen with other DNS servers also)

To fix both of these at once you just need to tell samba not to use these services to lookup computers.

Open up the smb.conf file:
```

sudo gedit /etc/samba/smb.conf

```
Then look for a line that starts:
```

name resolve order

```
And if you find it change it to this or just create a new entry near the top of the config file:
```

name resolve order = lmhosts wins bcast

```
Then you will need to restart samba:
```

sudo /etc/init.d/samba restart

```

These are bugs due to the new gvfs which is a PITA (it also gives issues with ftp aswell)

---

