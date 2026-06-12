---
title: "T23 Trackpoint speed/sensitivity non-working ?"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by marin.r on 2006-08-12
Hi All,

My trusty IBM T23 was laying around and I haven't used it in maybe 2-3 months at all. It was dual boot and I decided to wipe the XP as my HDD is only 30gigs and there's much more interesting stuff to put on it than a fallback os :)
So I installed the 6.06lts with its default options (erase hdd) as the manual partitioning didn't work (strange but not surprising) as it should.
And you've quessed it - I don't have any backups of config files.

I DO recall I used to set sensitivity and speed the way thinkwiki says it should be done. 

```

    # echo -n 120 > /sys/devices/platform/i8042/serio0/serio2/speed 
    # echo -n 250 > /sys/devices/platform/i8042/serio0/serio2/sensitivity 
```

However speed and sensitivity path on my machine is not the same. I have them both here:

```

/sys/devices/platform/i8042/serio0/input:mouse0

```

and here:

```

/sys/devices/platform/i8042/serio0/

```

Doesn't matter how hard I try to modify those settings they're still the same!
And I remember it worked before - on ubuntu breezy,fedora 5,slackware and I'm 99% sure it worked on 6.06 too before I reinstalled it.

Any help would be greatly appreciated :)

---

### Post by caldridge on 2007-04-14
I have an older X41 and second this.. I was able to get it up and running on 6.06 but 6.10 is not working.

---

