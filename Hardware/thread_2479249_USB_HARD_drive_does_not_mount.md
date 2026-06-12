---
title: "USB HARD drive does not mount"
date: 2022-09-19
forum: Hardware
---

### Post by nefartete on 2022-09-19
USB HARD drive does not mount

---

### Post by TheFu on 2022-09-19
> **nefartete said:**
> USB HARD drive does not mount

What file system does it use?  BTW, don't confuse a HDD with a partition.  File systems should always be placed onto partitions, not a whole drive.

Did you check the system logs?

Is the file system supported by the installed file system utilities? Not all are.

The DE and Ubuntu release would help people guess some ideas too.

And always remember that the power to mount is the power to destroy, so not allowing random USB storage to mount **is** an important security feature.  There are multiple ways to allow known USB storage to mount, which drastically reduces the attack vectors.

---

### Post by mIk3_08 on 2022-09-20
> **nefartete said:**
> USB HARD drive does not mount 
Use command below to mount your usb devices.
```
sudo mount /dev/sda,sdb,vda,vdb
 
```
and use the command below to know what you use for your root disk. Regards and cheers
```
lsblk
```

---

### Post by TheFu on 2022-09-20
What?
```
sudo mount /dev/sda,sdb,vda,vdb
```
Won't work for a number of reasons and in a number if situations.
I'm just confused.

Storage devices have partitions.  Trying to mount the entire device is an error.  Mounts need to point at there the file system is stored, which, for simple setups, would be on a partition.  Of course, knowing the correct partition is required AND providing a mount point is also required.  A mount point is a directory, usually empty.
vda, vdb devices are for virtual machines using the virtio driver.  Those are unlikely to be USB devices.  Plus, no partition number is included.  Error.

I get the feeling the OP was just frustrated and did a drive-by post.

---

### Post by mIk3_08 on 2022-09-20
> **TheFu said:**
> What?
```
sudo mount /dev/sda,sdb,vda,vdb
```
Won't work for a number of reasons and in a number if situations.
I'm just confused.

Sorry TheFu. My bad. I was just doing that just for an example. That should be,
```

sudo mount /dev/sda
or
sudo mount /dev/sdb
or
sudo mount /dev/vda
or
sudo mount /dev/vdb
```
Hope its clear now. Regards, cheers and peace.

---

### Post by TheFu on 2022-09-20
Can't believe we aren't understanding each other.

I hope, really, really, hope you remember to add the partition number and don't try to mount the entire storage device. 

You probably mean 
```
$ sudo mount /dev/sdb1 /mnt/1 
```
Since trying to mount a whole drive is an error and not providing the mount point is also an error.
Of course, if the file system **is** directly on the storage device, then you've got bigger issues.
Not providing the mount point (i.e. target directory), isn't an error, but only if the /etc/fstab already has the device and mount point for that device specified.  That's why 
```
sudo mount -a
```
works.

For fun, I plugged in a flash drive ... it has 2 partitions on it - a FAT32 and an ext4.
```
$ sudo mount /dev/sdc
mount: /dev/sdc: can't find in /etc/fstab.

$ sudo mount /dev/sdc1
mount: /dev/sdc1: can't find in /etc/fstab.
```

See what I mean by it is an error?

OTOH, 
```
$ sudo mount /dev/sdc1 /mnt/1
```
works, provided /mnt/1 exists.
Is that clearer?

Try your commands, please and post the results. Bet they don't work.

---

### Post by mIk3_08 on 2022-09-21
> **TheFu said:**
> 
```
$ sudo mount /dev/sdb1 /mnt/1 
```

Yeah this is what I mean. I know you cant just easily mount with the command below:
```
 sudo mount /dev/sdb1
```
It should have a destination name. with 
```
/mnt/1
```
My bad again. It's just that I haven't explain it too far more and detailed. I will try next time to be more careful, detailed and sensitive as you are. As this will create curiousness to the person evolved. Regards and cheers.

---

### Post by TheFu on 2022-09-21
> **mIk3_08 said:**
>  
My bad again. It's just that I haven't explain it too far more and detailed. I will try next time to be more careful, detailed and sensitive as you are. As this will create curiousness to the person evolved. Regards and cheers.

when showing incomplete commands, some notation needs to be provided for new users. Without it, they would type what you've posted, not get the desired results and become extremely frustrated with you, linux, these forums, and perhaps all computing.  Incorrect advice is worse than no advice. Please consider the OP's needs.

I fear we've run off  nefartete already.

---

