---
title: "Clearing Hard Drive Space Issues"
date: 2010-01-22
forum: Hardware
---

### Post by wwood on 2010-01-22
My hdd on my karmic desktop filled up, but then I cleared space. However, it seems that total minus taken doesn't equal available:
```

ben@ben:~$ df -h /
Filesystem            Size Used Avail Use% Mounted on
/dev/sda5             114G  109G     0 100% /

```
I read somewhere it might be an inode problem, but..
```

ben@ben:~$ df -i /
Filesystem            Inodes IUsed IFree IUse% Mounted on
/dev/sda5            7528448 1031451 6496997   14% /

```
So I apparently don't have enough googling skill to find someone else with the same problem. Any ideas?
Thanks in advance,
ben

---

