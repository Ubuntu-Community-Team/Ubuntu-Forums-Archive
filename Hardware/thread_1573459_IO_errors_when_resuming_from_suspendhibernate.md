---
title: "I/O errors when resuming from suspend/hibernate"
date: 2010-09-12
forum: Hardware
---

### Post by BinaryMn on 2010-09-12
I'm running Lucid on a Toshiba A305D laptop. For months, suspending and hibernate my laptop has been unreliable at best. When resuming, I would encounter constant I/O errors and would have to hard reboot. I recently wrote a set of scripts to fix this problem. This should work with any suspend/hibernate solution. Personally, I'm using TuxOnIce.

For starters, the problem has to do with the amount of RAM in use. I came up with a script (/usr/bin/memclear) to be run as root to clear any cached RAM.

```
#!/bin/bash
sudo su <<-'.'
sync
echo 1 > /proc/sys/vm/drop_caches
echo 2 > /proc/sys/vm/drop_caches
echo 3 > /proc/sys/vm/drop_caches
.
```

For awhile, I would run this script by hand. As of late, I found a way to incorporate it into /usr/lib/pm-utils/sleep.d by using a setuid wrapper to run /usr/bin/memclear as root. I understand this is an insecure way to do this, but I couldn't think of any other way to do this. If someone reading this has a better way of implementing this, please post with detailed instructions.

At this point you're going to need a program called suid-wrap ([http://isptools.sourceforge.net/suid-wrap.html](http://isptools.sourceforge.net/suid-wrap.html)) unless you know how to write a binary setuid-wrapper. Then, as root, create a script in /usr/lib/pm-utils/sleep.d named 000memclear. Put in the following.

```
#!/bin/sh
case $1 in
	suspend)
	/usr/sbin/suid-wrap /usr/bin/memclear
;;
	hibernate)
	/usr/sbin/suid-wrap /usr/bin/memclear
;;
esac
```

Both scripts need to be owned by root and chmod 755. I'll be editing and updating this over time to expand these instructions.

Anyway, at this point, what should be happening is when you put your computer into suspend, the /usr/bin/memclear script is run, which clears out any cached RAM. Afterward, your computer should end up suspending. Hopefully, you should be able to resume without anymore I/O errors.

It's been close to a week since I implemented this in my own system and have had consistent results since. If you need instant help, I idle in Freenode and FOSSnet.

---

