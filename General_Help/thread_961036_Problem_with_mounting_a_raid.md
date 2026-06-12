---
title: "Problem with mounting a raid"
date: 2008-10-27
forum: General Help
---

### Post by shadowers on 2008-10-27
When I try to mount my raid, /dev/md0, after I reboot it unmounts. What do I do?

---

### Post by fjgaude on 2008-10-28
I believe all you have to do is put a line in your /etc/fstab file, something like this:

```
gksu gedit /etc/fstab
```

Then add this:

```
/dev/md0 /home/raid ext3 defaults 0 2
```

where /home/raid is your mountpoint.

You make it first:

```
sudo mkdir /home/raid
```

Reboot and that should do it.

Let us know how you are doing.

---

