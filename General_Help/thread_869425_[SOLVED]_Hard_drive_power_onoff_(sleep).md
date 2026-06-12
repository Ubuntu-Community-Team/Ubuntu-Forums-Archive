---
title: "[SOLVED] Hard drive power on/off (sleep?)"
date: 2008-07-24
forum: General Help
---

### Post by Cool Javelin on 2008-07-24
I read in another post how to make my hard drive sleep when it isn't being used. The command was:

sudo hdparm -S24 /dev/sda
and
sudo hdparm -S25 /dev/sbd

This works fine, the drives spin down after 2 minutes.

But, Xubuntu (or Linux) accesses the drive, like every 5 minutes or so spinning the drive back up.

How can I stop this?

I assume Linux is doing some kind of housekeeping, how do I find out what it is doing and alter it's behavior?

It wouldn't be so bad if it did so every hour (or couple of hours.)

I believe I am using Xubuntu 8.04 using Gnome. Not exactly sure, I downloaded it about 2 weeks ago. How do I find out for sure?

Also, this is a Pentium II 300MHz with 2ea. 2gb drives. (Sda has a small windows partition, and sdb has the Xubuntu that spills over onto sda for part of itself.)

To be sure, I don't know wh HD is causing the issue. Upon listening to it, maybe only one drive is spinning down and the other may be active enough that it never stops spinning, or, perhaps it is inactive enough that it doesn't restart.

I chose 2 different delays so I could tell one from the other, but it is difficult.

One of the 2 drives is rather noisy, and that is the one I hear power cycling. The other may be quiet enough that I just don't notice if it ever stops spinning.

Thanks, Mark.

---

### Post by sdennie on 2008-07-24
You could try using this:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then, to see all disk activity:

```

tail -f /var/log/syslog

```

To later turn off the logging of that information run:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

If you are using ext3 for your filesystems, without some tweaking, it will be difficult to get both disks to sleep.  There is a guide for generally reducing disk activity that might help a bit but, it's not really designed to keep the disks completely spun down for large periods of time: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

---

