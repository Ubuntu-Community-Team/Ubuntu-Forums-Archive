---
title: "Program to Check on What's Chewing Up the I/O."
date: 2008-08-27
forum: Hardware
---

### Post by Gen2ly on 2008-08-27
Hi all.  I got a bit of a problem with an evasive action.  One program every now and then just chews up the I/O, it takes over the computer and lasts a couple minutes.  I have an older computer so when that disk output is running, it puts my pc in a terrible bog.  Now I can look at gnome-system-monitor but it only gives me CPU and NICE values which aren't at all helping.  Any thoughts ideas that can help track this down?

---

### Post by sdennie on 2008-08-27
It's possible that it's the locate database update.  When it happens you might be able to see what's causing it with:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

And then looking at the syslog with:

```

tail -f /var/log/syslog

```

To turn the log spamming of disk activity off again, use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by Gen2ly on 2008-08-30
Thanks Vor, this is exactly what I needed!  FYI (if your curious) the huge amount of I/O was from Firefox.  Apparently 3.01 is gobbling up memory alot more than the 3.0-beta-5.  So Firefox-3.01 is doing alot of page in and page out (almost twice as much as beta-5) and it is overflowing directly to the disk swap.  Looks like I'm going to have to go back to beta-5.

If it's not too much of a bother, do you mind if I put this on my blog?  It's a good tip and 'till now haven't found any program that can do it better.

---

### Post by sdennie on 2008-08-30
Of course not.  It's a very useful tip for many situations.  Glad you were able to get the information you needed from it.

---

