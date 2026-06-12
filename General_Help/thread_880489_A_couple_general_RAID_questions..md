---
title: "A couple general RAID questions."
date: 2008-08-05
forum: General Help
---

### Post by Platypus Stan on 2008-08-05
Hello.  I just finished setting up a new Ubuntu-based file server and have some quick questions about the RAID array I hobbled together:

1) Is there a simple way to run it through its paces and test it out before I start filling it up?  Three of the four disks are brand new and none of them have been scanned for bad sectors or anything.

2) How feasible would it be to migrate the array to a new computer at some point in the future?  Is there a guide floating around out there for this scenario?

If it matters, I have four identical 1tb SATA drives in a RAID 5 array created manually with mdadm.  File system is reiserfs.

Thanks in advance.

---

### Post by fjgaude on 2008-08-05
> **Platypus Stan said:**
> Hello.  I just finished setting up a new Ubuntu-based file server and have some quick questions about the RAID array I hobbled together:

1) Is there a simple way to run it through its paces and test it out before I start filling it up?  Three of the four disks are brand new and none of them have been scanned for bad sectors or anything.

With the array unmounted you can run **fsck** to test:

```
sudo fsck -t reiserfs /dev/md[n]
```

with the n being your array number.

2) How feasible would it be to migrate the array to a new computer at some point in the future?  Is there a guide floating around out there for this scenario?

There no simple guide. But it is very easy to take the array to another motherboard, computer without problems. Simply make the physical change, boot the system, install **mdadm**, and then run:

```
sudo mdadm --assemble --scan
```

That creates the **mdadm.conf** file and you are ready to mount the array, put in the line in fstab to have it come up automatically at boot time.

Now if the computer already has mdadm on it, and if there is also a /etc/mdadm.conf file, remove them both.

If it matters, I have four identical 1tb SATA drives in a RAID 5 array created manually with mdadm.  File system is reiserfs.

Thanks in advance.

Let is know it you have any more questions. You might wish to study this pieces:

 [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study **/usr/share/doc/mdadm/FAQ.gz**  and **md.txt.gz**

Happy computing.

---

