---
title: "Problem with installation ubuntu 9.04 from hard disk"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by colau on 2009-05-06
Hi,
Reading this article
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

I copied all from the iso to a ext3 partition and trying to install 9.04.
During installation ,at the stage of partition a message is shown.
[html]
Your installation medium is on /dev/sda7. 
You will not be able to create, delete, or 
resize partitions on this disk, but you may be 
able to install to existing partitions there.
[/html]
Can't go on from there.

---

### Post by rannday on 2009-05-06
How large is the partition you installed it on?

Did you dual boot it with something else?

How many partitions do you have on the hard disk which you installed Jaunty on?

Just some questions I would ask myself after an issue as such.

What type of file system did you use on the partition which you installed Jaunty? 

Did you perform a checksum on the image file you downloaded? To make sure you downloaded a proper distribution?

All I can think of on the spot at-the-moment. Researching any of these subjects might help you with your issue.

---

### Post by colau on 2009-05-06
> **rannday said:**
> How large is the partition you installed it on?

Did you dual boot it with something else?

How many partitions do you have on the hard disk which you installed Jaunty on?

Just some questions I would ask myself after an issue as such.

What type of file system did you use on the partition which you installed Jaunty? 

Did you perform a checksum on the image file you downloaded? To make sure you downloaded a proper distribution?

All I can think of on the spot at-the-moment. Researching any of these subjects might help you with your issue.

The extracted iso is in /dev/sda7(5GB).

Now on the live session of ubuntu.
df -h
[html]
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  120K  497M   1% /var/run
varlock               497M  4.0K  497M   1% /var/lock
udev                  497M  164K  497M   1% /dev
tmpfs                 497M  648K  497M   1% /dev/shm
rootfs                497M   61M  437M  13% /
/dev/sda7             5.0G  838M  4.0G  18% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 497M   12K  497M   1% /tmp
[/html]

---

### Post by thewolfman on 2009-05-06
When trying to install; which method are you choosing: Automatic, guided or manual.

It might help if you can use a partition tool and set-up the partitions before you start the install then select manual install and set your partitions that way.

---

### Post by colau on 2009-05-06
> **thewolfman said:**
> When trying to install; which method are you choosing: Automatic, guided or manual.

It might help if you can use a partition tool and set-up the partitions before you start the install then select manual install and set your partitions that way.
Clicking install from desktop ,going forward ,during partition setup there is not option like manual,guided,automatic.

---

### Post by colau on 2009-05-06
If i click install a message is shown
[html]
The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?
[/html]
Then goes back to the partition window.

---

### Post by mickey12gauge on 2009-05-08
Same issue.

---

### Post by logos34 on 2009-05-08
solution --> [here]("http://ubuntuforums.org/showthread.php?t=1152319").

---

### Post by colau on 2009-05-08
> **logos34 said:**
> solution --> [here]("http://ubuntuforums.org/showthread.php?t=1152319").
Many thanks.It worked like a charm.
```

sudo umount -l -r -f /dev/sda7

```

---

