---
title: "Moving /var to separate partition"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by emyr42 on 2009-10-09
I had 9.04 32bit installed with separate /home and /var partitions (I wanted my MySQL data and Apache docroot both in an easy to backup location.)

I've installed 9.10 Beta 64bit (finally, 4GB usable RAM!), and reused the /home partition. I didn't mount my old /var partition as /var because I was scared I might lose the easy-to-backup stuff I hadn't backed up yet. I mounted the old /var partition as /oldvar.

Once everything was installed again I copied my stuff from /oldvar/lib/mysql and /oldvar/www into the new /var (which is on the main partition), and made sure my localhost testing website  still worked.

Then I deleted everything from /oldvar, and coped everything except 'run' from /var into /oldvar.

Then I rebooted onto the LiveCD, deleted /var, renamed /oldvar to /var and edited /etc/fstab to mount the partition as /var instead of /oldvar.

Now I get an error on boot, which I forgot to write down. Any suggestions on what I did wrong?

---

### Post by scragar on 2009-10-09
Did you keep the directory /var? Fstab won't mount it unless the directory exists.

---

### Post by emyr42 on 2009-10-09
Whilst in the LiveCD, I removed /var, then renamed the /oldvar/ dir which the fs mounted onto to /var, so yeah, the /var directory still exists.

---

### Post by emyr42 on 2009-10-12
Full error message is:

> init: sreadahead main process (445) terminated with status 1

---

