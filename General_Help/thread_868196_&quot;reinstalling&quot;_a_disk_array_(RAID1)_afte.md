---
title: "&quot;reinstalling&quot; a disk array (RAID1) after hardy upgrade"
date: 2008-07-23
forum: General Help
---

### Post by l3dx on 2008-07-23
I've just upgraded to 8.04 by doing a clean installation.
Previously I had two disks in raid1, and am now trying to get this up and running again.

This is what happens:

```

thomas@bravo:~$ sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 missing
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Tue Jan 15 22:07:46 2008


```

Should I just recreate the array, or is there a better way to "restore" the array.

Any chance of data loss if I just continue this operation?

---

### Post by fjgaude on 2008-07-24
I normally simply assemble an array moved to another machine:

```
sudo mdadm --assemble --scan
```

That usually does the trick. If you use --create and are successful, all data will be lost.

---

### Post by l3dx on 2008-07-26
Thanks you, fjgaude :)

---

### Post by ChrisNY on 2008-08-07
I will be facing the same task as well when I upgrade from 6.10 server to 8.04 server.  The information above will hopefully do the trick.  It's been a while since I've done an install, so would anyone be able to help me out with how I should proceed during the install with regard to selecting various options?  Do I need to make any selection during the reinstall to say that I will be setting up a RAID array or do I just reinstall and re-setup the RAID array after the fact?

I have 3 partitions, /boot, /swap and /home if that helps.

Thanks!

-Chris

---

### Post by fjgaude on 2008-08-07
No, nothing to do except after the upgrade make sure that you have deleted the /etc/mdadm/mdadm.conf file anf that mdadm is not installed, then install it. Then run the --assemble --scan command... you are up and running.

Let us know if you have any issues.

---

### Post by malarie on 2009-07-07
Just a quick reply..   Do you need do format the 2nd disk when you reinstall the array or sda1 will be  mirrored automaticaly on sdb1??

thanks

---

