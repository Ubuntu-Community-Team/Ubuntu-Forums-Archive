---
title: "System boots after hibernate"
date: 2008-11-18
forum: General Help
---

### Post by zacktu on 2008-11-18
After resizing and moving my swap file 

[http://ubuntuforums.org/showthread.php?t=984057](http://ubuntuforums.org/showthread.php?t=984057)

I found that my system would no longer hibernate properly.  When I return from hibernate the system goes through the boot sequence, rather than following the resume sequence.

The file /etc/log/pm-suspend.log shows that everything in the hibernate sequence worked fine.  The log should be twice as big as it is because each of the actions shown in the log is supposed to "thaw" in reverse order.  Clearly, that doesn't happen.  

Apparently, something has happened to pm-utils.  What to do now?

<><><><><><><>  log from a hibernate  <><><><><><><>

zack@mozart:/var/log$ more pm-suspend.log
Initial commandline parameters: 
Tue Nov 18 12:23:17 EST 2008: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/00clear hibernate: success.
/usr/lib/pm-utils/sleep.d/05led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager hibernate: success.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/50modules hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate: success.
Tue Nov 18 12:23:21 EST 2008: performing hibernate
zack@mozart:/var/log$

---

### Post by conxorxa on 2008-11-20
Try #5 in this thread:
[http://ubuntuforums.org/showthread.php?t=781809]("http://ubuntuforums.org/showthread.php?t=781809")

and note the missing step mentioned in #7.

---

### Post by unutbu on 2008-11-20
zacktu, this may or may not solve your problem, but it is something to check:

Open a terminal (Applications>Accessories>Terminal) and
run```

blkid
```
In the output you will see a line like this:```

/dev/sda5: TYPE="swap" UUID="33b7e11e-5bdb-4e98-b626-671b1c4d18eb" 
``` You might see many lines, so look for the line which says TYPE="swap". This line shows the UUID (Universally Unique Identifier) for the swap partition. 

Next, type```

cat /etc/initramfs-tools/conf.d/resume
```
This command simply prints the contents of the file to the terminal. The output should look similar to this:```

RESUME=UUID=33b7e11e-5bdb-4e98-b626-671b1c4d18eb
```

Check that the UUID listed in /etc/initramfs-tools/conf.d/resume matches the UUID listed by blkid.

If the UUID's don't match, edit 
/etc/initramfs-tools/conf.d/resume so the UUID listed there is the same as that reported by blkid.

Explanation: If during the resizing/moving of the swap partition the swap partition was destroyed and recreated, the act of recreating the partition gives it a new UUID.
That would explain why the above change is needed.

---

### Post by zacktu on 2008-11-20
Thanks for the suggestions, conxorxa and unutbu.  Changing the UUID for resume is one of the things I had already done.  That change that solved the problem of hibernate saying that it couldn't find the swap partition.  It appears that the contents of memory is being copied to the swap partition.  Now the problem is how to get it back.

---

