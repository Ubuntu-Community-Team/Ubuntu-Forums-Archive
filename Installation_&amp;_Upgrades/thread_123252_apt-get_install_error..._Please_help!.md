---
title: "apt-get install error... Please help!"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by chugru on 2006-01-29
Hi all...

As a newbie with Kubuntu, I seem to run into an error at each turn. :( 

I'm now having trouble with package installation from the command line:```
~$ sudo apt-get install eterm
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Does anyone have thoughts as to what this means and how I might fix it?

Thanks in advance! This forum has proven very helpful!

---

### Post by moephan on 2006-01-29
Are you running synaptic or another update program at the same time?

---

### Post by Esca on 2006-01-29
have the same problem / not running synaptic

after reboot i have installed 1 program with add aplications, after this sudo apt-get install seems to be impossible and i have the same error as the above

---

### Post by moephan on 2006-01-29
Youmight need to delete the lock file in var/lib/dpkg. This will most likely solve your problem. 

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=21418&highlight=apt-get+delete+lock+file](http://ubuntuforums.org/showthread.php?t=21418&highlight=apt-get+delete+lock+file)

If that seems like it might be related to your problem, then here's how you can fix it:
1. Make sure that synaptic or Add Applications is not running.
2. Make sure apt-get is not running.

3.
```

$cd /var/lib/dpkg
$sudo rm lock

```

This fix worked for me, but please read the thread above for caveats and warnings about how deleting certain files can cause problems for your system. I am not a dpkg expert!

Cheers, Rick

---

### Post by chugru on 2006-01-29
**moephan wrote:**

> If that seems like it might be related to your problem, then here's how you can fix it:
1. Make sure that synaptic or Add Applications is not running.

That, alone, was my problem. Adept was running in the background, causing the lock.

Shutting down Adept worked for me.

Thanks!

---

