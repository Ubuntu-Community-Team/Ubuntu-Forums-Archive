---
title: "Separate partitions for root, home, var, tmp, usr?"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by Shampyon on 2009-02-27
I've just put together a nice little machine. Intel Core2 Duo E8400 CPU, 2GB RAM and a 640GB HDD. I'm planning on installing Kubuntu 8-10. I was reading the Ubuntu Documentation online and saw the recommended partitioning stats:

[COLOR="Red"]/[/COLOR]______250MB
[COLOR="Red"]/user[/COLOR]______6GB
[COLOR="Red"]/var[/COLOR]______3GB
[COLOR="Red"]/tmp[/COLOR]______100MB
[COLOR="Red"]/home[/COLOR]______(if only one user account) remainder of drive
[COLOR="Red"]swap [/COLOR]______(equal to RAM)

With the size of my drive, I was thinking of using this setup:

[COLOR="Red"]/[/COLOR]______5GB
[COLOR="Red"]/user[/COLOR]______10GB
[COLOR="Red"]/var[/COLOR]______5GB
[COLOR="Red"]/tmp[/COLOR]______10GB
[COLOR="Red"]/home[/COLOR]______remainder of drive
[COLOR="Red"]swap [/COLOR]______4GB (in case I buy more RAM down the track)

I install a LOT of extra software though, and not all of it from the repos. I do a fair bit of DVD ripping/encoding, I download a lot of podcasts, and I occasionally edit video and audio (just basic stuff, nothing fancy). Does they look like adequate partition sizes?

---

### Post by smani on 2009-02-27
Usually you will save all those data in your home partition, the rest of the filesystem structure usually is only touched through the package manager and the kernel, with the exception of the tmp folder, opt (historically being used for software that is not installed through the package management) and var (where you might store a website or a database).
For what concerns opt, you can also install those programs in a folder in your home directory, say ~/Programs.
Further on, you don't necessarily have to create all those folders as separate partitions, those kind of structures are mostly used on larger networks where say all clients share the same /usr folder. For a private PC I would recomment creating separate partitions for / (10 GB should be more than enough), /boot (150-200MB), clearly swap (2GB) and then the rest /home.

---

