---
title: "Hard disk LED blinks constantly with no reason"
date: 2008-11-01
forum: Hardware
---

### Post by rodrigolautaro on 2008-11-01
Hi folks.

Two days ago I made the routine system update trough Synaptic and til now the HD light wont stop blinking all the time with apparently no reason. I've googled it and some other people had the same problem as well, but no solutions at all.

When I first noticed this I checked the gnome-system-monitor if it was using an excesive amount of RAM and begining to use the swap, but i was using only 350 MB RAM with Firefox and Compiz fusion working.

Then I thought it could be some process using lots of CPU and therefore accessing more often to the HD, but both CPUs are around 8% usage, and the process that use more memory is at the moment the gnome system monitor.

Then I remember that I was skipping the hd scaning at the system loading, so last night I let the computer make it, and nothing

Then I thougt it might be the HD that someway was indexing files, so I let the computer on all night on the gdm, without starting any session.

The light keeps blinking even without connecting to internet.

Now it even made the system a little slower, wich I notice when watching hdtv videos.

Oh and I killed the trackerd process at the gnome system monitor and nothing.


PLease help.:confused:

---

### Post by rodrigolautaro on 2008-11-01
I'm sorry for not posting my system specs, but here they are:

Dell Inspiron 1525
Core 2 Duo 1.83 GHz
2 GB RAM
120 GB Hard Disk

Ubuntu Hardy Heron (up to date), using compiz.

---

### Post by sdennie on 2008-11-01
Are you sure this wasn't always the behavior and you never noticed it before?  By default, an Ubuntu install with the ext3 filesystem will generally write the disk every 5 seconds.  You can change this behavior though: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

### Post by rodrigolautaro on 2008-11-01
:) Thanks for replying

Absolutely sure, I'm always aware of the LEDs, the fan function, etc.
And the light blinks like 4-5 times a second, pretty regularly although.

---

### Post by sdennie on 2008-11-01
> **rodrigolautaro said:**
> :) Thanks for replying

Absolutely sure, I'm always aware of the LEDs, the fan function, etc.
And the light blinks like 4-5 times a second, pretty regularly although.

4-5 times a second is fairly extreme for an idle machine.  Try this:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then:

```

tail -f /var/log/syslog

```

That should tell you what is accessing the disk and hopefully lead you in the right direction to fix the problem.  To turn off the logging use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by rodrigolautaro on 2008-11-01
The output to the second command is this 

[http://pastebin.com/f3f8ee728](http://pastebin.com/f3f8ee728)
It stays like this and can't see no more events.

---

### Post by ktp on 2008-11-02
Thanks for the info...I have noticed the led flashing also...am not 100% sure but this seems like new to me also.

---

### Post by rodrigolautaro on 2008-11-04
Help please! This thing is driving me nuts!] (*,)

---

### Post by rodrigolautaro on 2008-12-07
I've solved it by reinstalling the system. I only formatted the root partition so I kept all of my configurations in the /home partition. I think what caused the problem was installing some packages in synaptics.

---

### Post by fadumpt on 2009-02-18
Thanks for the commands
It showed the MythTV Backend Constantly tearing in to the hard drive.
uninstalled it and it went away :-D

It popped in there accidentally when I was grabbing random apps to screw around with a finicky ipod nano.

---

### Post by Leafie on 2009-05-28
> **fadumpt said:**
> MythTV Backend Constantly tearing in to the hard drive.

I found this was caused by mythtvbackend constantly trying to connect to mysql when either it wasn't there or the database credentials were wrong.

---

