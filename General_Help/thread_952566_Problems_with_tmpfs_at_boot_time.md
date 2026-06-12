---
title: "Problems with tmpfs at boot time"
date: 2008-10-19
forum: General Help
---

### Post by avgjoe64 on 2008-10-19
Hi everybody,

I have set up a home server that uses a CF card as its main drive (using a CF<->IDE adapter). Because I have limited space, and I don't want to wear out the card to early, I have decided to use tmpfs for /var/log (as well as /tmp and /var/tmp).

The problem is that, at boot time, I get a bunch of messages about various /var/log/whatever files not existing. Also, apt complains about /var/log/apt not existing, so I added an entry in fstab to use tmpfs for /var/log/apt as well (like the Ubuntu Eee site suggests), but at boot, the system cannot mount /var/log/apt because the mount point doesn't exist.

So I need to populate /var/log at boot time, to create the various empty log files and the /var/log/apt directory. How should I go about doing this?

(I apologize for my not so good English.)

---

### Post by avgjoe64 on 2008-10-20
Alright, I created a script that is run at boot-time, right after /var/log is mounted, to create the various log files and directories.

The problem is, /var/log/apt still cannot be mounted. mountall.sh mounts everything in fstab in a single command.

I could simply re-run "mount /var/log/apt" from my custom tmp-init.sh script, but I would still get an annoying error message at boot. Isn't there any way to automatically create the mount point? I'm pretty sure it works fine on my EeePC with Ubuntu-Eee.

---

### Post by kerry_s on 2008-10-20
yeah logs are a pain, but your doing it wrong. /tmp is still written to disk and cleaned at shutdown, what you want to do is create a ramdisk in memory and mount that as /tmp. as for the logs your best bet is just to disable them in /etc/syslog.conf, just # them out.

from the top of google:
[http://surfer.nmr.mgh.harvard.edu/partition/ramdisk.html](http://surfer.nmr.mgh.harvard.edu/partition/ramdisk.html)

---

### Post by avgjoe64 on 2008-10-21
> **kerry_s said:**
> tmp is still written to disk and cleaned at shutdown, what you want to do is create a ramdisk in memory and mount that as /tmp.
/tmp is mounted as a tmpfs. tmpfs behaves more or less like a ramdisk. From Wikipedia: "tmpfs (previously known as shmfs) distinguishes itself from the Linux ramdisk device by allocating memory dynamically and by allowing less-used pages to be moved onto swap space."

I'm not using any swap space (that would kinda defeat the point of not wearing out the CF card) so I think I'm safe here.

> **kerry_s said:**
> as for the logs your best bet is just to disable them in /etc/syslog.conf, just # them out.
Good point. Since this is going to be a machine with (hopefully) long uptimes, I guess logs could potentially fill up the memory.

Anyway, to answer my own question, there is no need to mount /var/log/apt separetely. I can just use my script to create /var/log/apt and it should work fine.

I'll post my script and mark this post as solved, maybe it'll help someone else.

---

