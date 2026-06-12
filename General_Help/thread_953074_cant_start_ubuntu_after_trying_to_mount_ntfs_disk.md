---
title: "cant start ubuntu after trying to mount ntfs disk"
date: 2008-10-19
forum: General Help
---

### Post by tiggsy on 2008-10-19
i amended fstab in accordance with some instructions in a thread i cant now find (as i have no favorites or anything available, im only able to boot from floppy).

Previously, it was terminating with the orange line under Ubuntu about a quarter way through, saying something about /dev/sdb1 has been mounted and efsck had terminated with status 8 or something like that 

So, i reinstated fstab back to what it was before and i THINK that has been sorted (i don't have to hit control-D any more) but it still won't do a complete boot. it drops out with the orange line about 3/4 over, and i get all this stuff, some off the top of the screen i cant see, but these lines have [fail] after them:

```
start-stop-daemon: Unable to start /sbin/klogd: Permission denied (Permission denied)
```

```
Avahi mDNS/DNS-SD Daemon avahi-daemon Timeout Could not receive return value from daemon process
```

```
Starting MySQL database server mysqld
```

Well, i guess the third one ain't that vital, but the other 2 are worrying

Then it goes through some other stuff succcessfully, gets to something about "Hardware Abstraction Layer hald" and sits there for a bit before saying it's starting ubuntu, but actually dropping me in what seems to be a full screen terminal without the ability to scroll back up to see what's off the screen.

This is very bad news. any help would be much appreciated.

it might be useful to know that i had installed ntfs-config and run it, and it had changed fstab. perhaps it changed something else as well, i dont know...

Oh, i don't seem to be able to access /etc on the main boot disk, as im using a floppy for access, the user is ubuntu@ubuntu instead of my usual

---

### Post by tiggsy on 2008-10-20
The first thing i did this morning, without checking for a reply here (which would obviously have been a waste of time, anyway), was to run an install of Gutsy on the ntfs disk which caused the problem.

All seemed to work well until I rebooted after the install, and ended up in exactly the same place. It seems odd that, even though the former ntfs disk is in fact sda, the system is still booting (or not) from sdb...

How do i get this to work?

---

