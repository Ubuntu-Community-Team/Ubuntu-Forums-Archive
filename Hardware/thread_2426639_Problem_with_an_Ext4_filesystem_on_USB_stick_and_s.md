---
title: "Problem with an Ext4 filesystem on USB stick and suspend"
date: 2019-09-11
forum: Hardware
---

### Post by georgesgiralt on 2019-09-11
Hello,
I've an Asus VivoBook 12_ASUS Laptop E203MA laptop. As it is a small form factor laptop, everything is on the motherboard and soldered. So I've to make go with the small Eemc memory installed and keep the Windows operating system on it during the warranty time.
I've installed an Ubuntu 18.04 LTS on it and put the home filesystem on an USB stick formatted with Ext4 filesystem. So far so good.
But after a suspend, the stick is initialized because it has lost it's power and thus become /dev/sdb instead of the /dev/sda it was on boot. So the /dev/sda1 partition mounted on /home has errors, being inaccessible. 
At first, I though tha mounting /home using it's UUID will solve the problem but it is not. 
After a return from sleep, the /home is still mounted using /dev/sda1 ... 
Here are the fstab line I use : 
```

UUID=3d3d5f1b-e7d2-4e86-9755-e709273df16f       /home           ext4   defaults     0    

```
and the corresponding mount output line :
```
 
/dev/sda1 on /home type ext4 (rw,relatime,data=ordered)

```


Could you please help me find a way to have either the mount point identical on awakening from suspend or a way to avoid the USB stick to re-init itself and thus become /dev/sdb ? 
Many thanks in advance for your help and support.

---

### Post by oldfred on 2019-09-11
Sleep may not reset everything.
Is issue there after a reboot?

Or is issue there after this?
sudo mount -a

You may want to mount with noatime, so reads do not also do a write.
See parameter description:
man mount

---

### Post by georgesgiralt on 2019-09-11
> **oldfred said:**
> Sleep may not reset everything.
Is issue there after a reboot?
No everything is fine if I reboot the machine
> Or is issue there after this?
sudo mount -a
This produce an error after sleep because sda1 is not available anymore and sdb1 is said to be read only .
If the machine is on after a fres start, mount -a produce nothing (no error nor message)

> You may want to mount with noatime, so reads do not also do a write.

See parameter description:
man mount
Will try it tomorrow, now it is time for sleep ;-) pun intended ... 
Thanks a lot for your answer !

---

### Post by oldfred on 2019-09-11
You should not be using device like sda & sdb, only use UUID or you can use labels as long as you keep labels unique. 
But many systems change device order, that was why years ago they changed to using UUIDs for mount & identifying a device uniquely. 

If using labels see alternative ways section.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by georgesgiralt on 2019-09-12
> **oldfred said:**
> You should not be using device like sda & sdb, only use UUID or you can use labels as long as you keep labels unique. 
But many systems change device order, that was why years ago they changed to using UUIDs for mount & identifying a device uniquely. 

If using labels see alternative ways section.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Actually, this is what I do, see the fstab line above. But the problem is that the mount thread in the kernel becomes invalid because the device it links to has disappeared on awake.

---

