---
title: "What's accessing my CD drive?"
date: 2008-08-08
forum: General Help
---

### Post by ialdobaeth on 2008-08-08
I'm running 64-bit Hardy on an HP Pavilion dv9000 laptop, first installed back in early July.  Everything is working beautifully (getting the wireless working was not exactly enjoyable, but at least it works).  

When I first log into X, and periodically during a session, something is accessing my CD drive.  I hear it grind a bit (even when empty), and occasionally the drive tray will pop open.

I watch my processes closely, keeping the top 10 visible in Conky, and see nothing abnormal there when the cd drive suddenly grinds.  Nothing relevant appears in syslog.

If the cd rom accessing would continue for a minute or so, I could probably track this down, but this only occurs for a second or so at irregular intervals sometimes separated by hours.

How do I find out what process is accessing my cd drive?  

Thanks,
-charles

---

### Post by yeaitsdark on 2008-08-08
You could run:

```
lsof /media/cdrom
```

To get a small idea perhaps of what is accessing files on your cdrom. I'm wondering if maybe it's apt. 

System > Administration > Software Sources.

Perhaps it's checking to see if theres an Ubuntu CD in the drive.

---

### Post by ialdobaeth on 2008-08-08
> **yeaitsdark said:**
> You could run:

```
lsof /media/cdrom
```

To get a small idea perhaps of what is accessing files on your cdrom. I'm wondering if maybe it's apt. 

Nope.  Apt was the first thing I checked.  It would also have thrown an error the first time I ran apt-get update, which is what usually reminds me I've forgotten to edit the sources list.

lsof returns nothing.  My gut feeling is that the process accessing the cd rom is only doing so for about a second, so by the time I get to running lsof, the process has already terminated. 

-charles

---

### Post by yeaitsdark on 2008-08-08
Any CD burner utilities installed? Honestly, thinking about it I wonder if mine does it too and I just don't know it.

---

### Post by ialdobaeth on 2008-08-09
> **yeaitsdark said:**
> Any CD burner utilities installed? Honestly, thinking about it I wonder if mine does it too and I just don't know it.

Well, I must admit that I'm somewhat paranoid by nature, so YMMV. :)

I have the k3b and brasero installed, as well as whatever comes with a multitude of other apps (amarok, nautilus).

---

### Post by yeaitsdark on 2008-08-10
Any progress on this? I mentioned the CD burner applications because maybe one of them is running on startup and checking the CD-Rom.

---

