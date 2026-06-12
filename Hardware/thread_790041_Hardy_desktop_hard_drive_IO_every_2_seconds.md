---
title: "Hardy desktop hard drive IO every 2 seconds"
date: 2008-05-11
forum: Hardware
---

### Post by blastus on 2008-05-11
Why is Hardy accessing my hard drive about every 2 seconds and how can I fix this? About every 2 seconds there is hard drive activity and I'm not doing anything with the computer--this is continuous. At the login screen this does not seem to happen.

---

### Post by sdennie on 2008-05-11
Is it closer to every 5 seconds?  I think ext3 writes the journal every 5 seconds.

You might be able to see what's causing the problem doing the following:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"
tail -f /var/log/syslog

```

After watching it for a while Ctrl-C and do a:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by blastus on 2008-05-11
The hard drive led is flashing about every 2 seconds. Here's a sample from /var/log/syslog. How can I fix this? I don't recall this being an issue in previous versions of Ubuntu.

```
May 11 02:00:09 userver kernel: [  242.705120] pdflush(184): WRITE block 718060024 on sda1
May 11 02:00:09 userver kernel: [  242.705143] pdflush(184): WRITE block 718107704 on sda1
May 11 02:00:09 userver kernel: [  242.705162] pdflush(184): WRITE block 718104888 on sda1
May 11 02:00:09 userver kernel: [  242.705176] kjournald(2700): WRITE block 718059536 on sda1
May 11 02:00:09 userver kernel: [  242.705231] kjournald(2700): WRITE block 718060016 on sda1
May 11 02:00:09 userver kernel: [  242.705235] kjournald(2700): WRITE block 718059544 on sda1
May 11 02:00:09 userver kernel: [  242.705611] syslogd(5135): dirtied inode 22438387 (kern.log) on sda1
May 11 02:00:09 userver kernel: [  242.705617] syslogd(5135): dirtied inode 22438387 (kern.log) on sda1
May 11 02:00:09 userver kernel: [  242.705622] syslogd(5135): dirtied inode 22438385 (debug) on sda1
May 11 02:00:09 userver kernel: [  242.705626] syslogd(5135): dirtied inode 22438385 (debug) on sda1
May 11 02:00:09 userver kernel: [  242.705629] syslogd(5135): dirtied inode 22438385 (debug) on sda1
May 11 02:00:09 userver kernel: [  242.708239] kjournald(2700): WRITE block 14576 on sda1
May 11 02:00:09 userver kernel: [  242.708245] kjournald(2700): WRITE block 14584 on sda1
May 11 02:00:09 userver kernel: [  242.708249] kjournald(2700): WRITE block 14592 on sda1
May 11 02:00:09 userver kernel: [  242.708251] kjournald(2700): WRITE block 14600 on sda1
May 11 02:00:09 userver kernel: [  242.708254] kjournald(2700): WRITE block 14608 on sda1
May 11 02:00:09 userver kernel: [  242.708256] kjournald(2700): WRITE block 14616 on sda1
May 11 02:00:09 userver kernel: [  242.708867] kjournald(2700): WRITE block 14624 on sda1
```

---

### Post by sdennie on 2008-05-11
That sample only covers 1 second.  Does it just do that over and over?

---

### Post by blastus on 2008-05-11
There are variations but it is pretty much repetitive every 4 to 5 seconds (sometimes 10.) Every 2 seconds the hard drive led flashes, but I only hear the hard drive every 5 to 10 seconds or so.

I found this thread: [kjournald constantly accessing disk ](http://ubuntuforums.org/showthread.php?t=369759) and issued the command ```
hal-disable-polling --device /dev/scd0
```

The hard drive led only flashes every 5 to 10 seconds now (instead of every 2.) This is consistent with me not hearing the hard drive every time the led flashes. This helped but the constant 5 to 10 second hard drive writes are quite annoying!

---

### Post by sdennie on 2008-05-11
The constant 5-10 second accessing is normal. If it really bothers you, one thing you could try would be to change the journal commit time on your partitions.  To test it:

```

sudo mount -o remount,commit=60 /

```

You'd have to do that for all your mounted filesystems that are using ext3.  That's not a permanent change, and, you'd have to add the commit=60 part to /etc/fstab if you choose to keep the option.

---

### Post by blastus on 2008-05-11
Thanks vor :) I'll give that a try.

---

### Post by Rui Pais on 2008-05-11
> **blastus said:**
> There are variations but it is pretty much repetitive every 4 to 5 seconds (sometimes 10.) Every 2 seconds the hard drive led flashes, but I only hear the hard drive every 5 to 10 seconds or so.

I found this thread: [kjournald constantly accessing disk ](http://ubuntuforums.org/showthread.php?t=369759) and issued the command ```
hal-disable-polling --device /dev/scd0
```

The hard drive led only flashes every 5 to 10 seconds now (instead of every 2.) This is consistent with me not hearing the hard drive every time the led flashes. This helped but the constant 5 to 10 second hard drive writes are quite annoying!


Hi,
hard drive access should not be much audible (unless your HD is very old...), thats sounds more like HD parking (5 sec period).
If that's a laptop you may be experience a famous issue with 2.6 kernels on laptop mode. Check some threads here:
[http://ubuntuforums.org/showthread.php?t=331418](http://ubuntuforums.org/showthread.php?t=331418)
[http://ubuntuforums.org/showthread.php?t=79055](http://ubuntuforums.org/showthread.php?t=79055)

Most of people solve that issue (kind of dangerous for HD health and longevity) by doing:
```
sudo hdparm -B254 /dev/sda
```
(change /dev/sda for what ever your case is, like hda for non sata drives...)

Not sure, of course, if thats it's really your problem, but may deserve a try.

---

