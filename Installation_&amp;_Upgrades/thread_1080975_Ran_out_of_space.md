---
title: "Ran out of space?"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by wlbragg on 2009-02-26
I think I ran out of space after installing a package (mythTV). I'm new to Linux and am struggling. I have dual boot under Windows XP. Ubuntu Intrepid-Ibex 8.10.

```
		size	used	avail	use%	Mounted on /host/ubuntu/disks/root.disk
		13G	13G	0	100%	/
tmpfs 		505M 	0 	505M 	0% 	/lib/init/rw
varrun		505M 	208K	505M 	1% 	/var/run
varlock		505M 	0	505M 	0% 	/var/lock
udev		505M 	3.0K	502M 	1% 	/dev
tmpfs		505M 	332K	505M 	1% 	/dev/shm
/dev/sda1	77G 	40G	38G 	52% 	/host
lrm		505M 	2.0K	503M 	1% 	/lib/modules/2.6.27-11-generic/volatile

```			

After mythTV install I suddenly got a mysql error.

```
Warning: session_write_close() [function.session-write-close]: write failed: No space left on device (28) in /usr/share/phpmyadmin/libraries/common.lib.php on line 653

Warning: session_write_close() [function.session-write-close]: Failed to write session data (files). Please verify that the current setting of session.save_path is correct (/var/lib/php5) in /usr/share/phpmyadmin/libraries/common.lib.php on line 653

```

I can't start Synaptic Packager manager to uninstall

```
Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.
```

After reading [http://ubuntuforums.org/showthread.php?t=1079090](http://ubuntuforums.org/showthread.php?t=1079090)

I guess that's my best option? Is there a better way to fix this problem? I installed Ubuntu using Daemon Tools light on Ubuntu iso. Can I fix this using it again and running the partition program?

---

### Post by lykwydchykyn on 2009-02-26
You are out of space on the root partition.  df -h shows you each mounted partition and how much space is used.  The percentages aren't supposed to add up; they represent the percent of used space per partition.

Probably you can fix this with "sudo apt-get clean", which will clear out your package cache.

---

### Post by wlbragg on 2009-02-26
Thank you so much.

That got me back into Synaptic.

Should I be able to use gparted (System>Admin>Partition Editor) in the Ubunto ISO that I used to install with and resize root.disk?

---

### Post by lykwydchykyn on 2009-02-26
I believe so, but I have not actually ever tried it.  And I wouldn't do so without backing up your data first.

---

