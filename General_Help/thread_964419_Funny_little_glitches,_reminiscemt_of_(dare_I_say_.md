---
title: "Funny little glitches, reminiscemt of (dare I say it) Windows."
date: 2008-10-30
forum: General Help
---

### Post by bilijoe on 2008-10-30
I have been having trouble with my 8.04.1 install getting progressively more and more sluggish.  Thought I had that one solved when it was suggested I turn off visual effects.  That did fix it, for about two days--now it's slowing down again (reminiscent of the old Windows registry problems).  

Now I have a new, all too Windows-like glitch.  This morning, when I turned my system on, after I logged in and everything seemed to be going normally, I found that all the icons in my upper panel (I've got a lot of them), were now in a somewhat scrambled order, and all were slid as far to the right as they could go.  Wazzup wi dat?  

In the interest of getting my productivity back in the black, I fear I'm going to have to pull the old Windows trick of Blast and [re]Build (i.e., format and reinstall).  I REALLY don't want to have to do that--this is Linux, after all, and I have WAY too many preferences set, ad-ins and widgets installed, etc., etc.  But I just cannot put up with this slow thing much longer, and I have kind of lost trust in the integrity of the system, after all my icons migrated on me.  Anyone have any ideas, or advice, before I make the commitment and reformat the drive?

Does anyone know, if I save a copy of my Home directory, and write it over the new Home directory, after the reinstall, will I get all my settings back?  Or will I just be asking for trouble?

---

### Post by cariboo on 2008-10-30
Instead of doing a re-install, check to see if you are running out od hard drive space, because that is what your problem could be. For a quick check open a Applications-->Accessories-->Terminal and type:

```
df -h
```

The output will be similar to this:

```
jimk@alexis:~/downloads/iso$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              15G  4.9G  8.9G  36% /
tmpfs                 989M     0  989M   0% /lib/init/rw
varrun                989M  100K  989M   1% /var/run
varlock               989M     0  989M   0% /var/lock
udev                  989M  2.9M  986M   1% /dev
tmpfs                 989M  244K  989M   1% /dev/shm
lrm                   989M  2.4M  987M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6             133G   32G   95G  25% /home
```

If any of the percentages are in the 90's, it's time free up some space on the hard drive.

Jim

---

### Post by Pro-reason on 2008-10-30
Is the sluggishness in Firefox or in everything?

If unnecessary processes are running, you can see them by running the command “top” in a terminal.

To make sure that your buttons don't move around on your panels, right click on them and choose “Lock to panel”.

---

### Post by bilijoe on 2008-10-31
I've got a relatively recently installed 250Gb HDD.  the highest percentage was 19%,, most were single digits, so I don't think it's HDD space.  Good thought though.

I've run TOP.  Doesn't seem to be anything unusual there.  And, all the Icons were locked to the panel.  They still are, just in a different place.

The sluggishness is not limited to FireFox, but seems to be most evident when scrolling through anything long.  Documents, folder content listings, web pages, anything long, but FF doesn't even have to be running for it to happen.

---

### Post by Pro-reason on 2008-10-31
It sounds like giving up, but since Ubuntu 8.10 is out today, I'd just upgrade to it (with a fresh installation).

---

### Post by bilijoe on 2008-10-31
That's about how I've been thinking.  Just finished downloading 8.10.

---

### Post by 3rdalbum on 2008-10-31
Reinstall, and this time put /home on a seperate partition, or better yet a different internal hard disk. Faster speeds will abound.

Every once in a blue moon my panel icons will be messed up too; it's **not** a sign that things are going Catestrophically Wrong.

---

### Post by bilijoe on 2008-10-31
> **3rdalbum said:**
> Every once in a blue moon my panel icons will be messed up too; it's **not** a sign that things are going Catestrophically Wrong.Well, I'm glad to know it's not a sign of impending doom.  Thanks.

---

