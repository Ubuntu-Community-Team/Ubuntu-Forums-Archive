---
title: "unmount virtual drive"
date: 2009-02-18
forum: Hardware
---

### Post by sridarshan on 2009-02-18
i just learned the command to mount virtual drive in some site as
sudo mount -o loop /data/filename.iso /mnt
but i dont know how to unmount that virtual drive
please help....thanx in advance

---

### Post by Fire_Chief on 2009-02-18
Simply execute the umount command with the mount point.
```
sudo umount /mnt
```
Also, you should normally use a subdirectory in /mnt as the mount point, not /mnt itself (i.e.  /mnt/newmountpoint)

Cheers!

---

### Post by sridarshan on 2009-02-18
thank you very much;)

---

