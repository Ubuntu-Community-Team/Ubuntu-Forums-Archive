---
title: "Wanting second Hard Drive as Slave for Ubuntu"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by jono2009 on 2009-02-13
New PC, I have Ubuntu installed on my first Hard Drive, the second has not been used. I want to access this from Ubuntu and use as a Slave Drive( is that the correct name?), to store movies etc.

How do I do this. Thank you for the help.

---

### Post by Taemojitsu on 2009-02-13
since it has no data on it you want to save, you can just format it onto a filesystem that Linux likes (altho it can probably already use the current filesystem). Go to Admin \ Partition Editor, make sure you are selecting the correct drive (!!), delete the current partition if necessary and create an ext3. There's really no reason to create multiple partitions, and nothing else needs to access the drive so ext3 isn't a problem.

If you want it to mount automatically you'll have to edit /etc/fstab, which goes into crazy UUID stuff if you want it to happen automatically and easily. You can do it without UUID and it should work fine.. unless you start installing new hardware storage drives (even CD drives might show up as scsi). If you DON'T add it to /etc/fstab, then once you format it (and assuming hardware is set up correctly) it will show up like a USB drive would, except that since it's an internal drive you'll have to give authorization to mount it unless you change authorization permissions.

---

### Post by logos34 on 2009-02-13
Here's a [simple tutorial.]("http://www.psychocats.net/ubuntu/mountlinux")

Get the UUID with 

sudo blkid 

and add it to fstab

---

### Post by jono2009 on 2009-02-13
logos34 and Taemojitsu thanks for your help, I'm on to it. Post once I have everything sorted and solved by this new noob.
      :popcorn:

---

