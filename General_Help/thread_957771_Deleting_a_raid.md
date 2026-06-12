---
title: "Deleting a raid"
date: 2008-10-24
forum: General Help
---

### Post by shadowers on 2008-10-24
When I was installing Kubuntu 8.04 with KDE4 I had three hard drives which are the following:

```

1 9GB scsi Drive (the boot drive / Swap)
2 250GB drives (These will be used in a software raid 1)

```

When installing Kubuntu I made the two 250Gb drives physical volumes for raid, and then proceeded to create the raid. The creating of the raid was not successful and told me some thing about it will not be recognized by linux. I didn`t think much of it and installed kubuntu anyways thinking to create the raid within kubuntu. I have been trying to set the raid up and when using fdisk to prepare the drives I get an error when saving the changes to the drive. The error is the following:

```

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.

```

Now I need to delete the raid created in the installation and a raid that was made somehow. The names of the devices are md0 and md1.

Now for the question. 

How do I delete a raid?

---

### Post by shadowers on 2008-10-24
Any Help???

---

### Post by Crossyboi on 2008-10-24
> **shadowers said:**
> When I was installing Kubuntu 8.04 with KDE4 I had three hard drives which are the following:

```

1 9GB scsi Drive (the boot drive / Swap)
2 250GB drives (These will be used in a software raid 1)

```

When installing Kubuntu I made the two 250Gb drives physical volumes for raid, and then proceeded to create the raid. The creating of the raid was not successful and told me some thing about it will not be recognized by linux. I didn`t think much of it and installed kubuntu anyways thinking to create the raid within kubuntu. I have been trying to set the raid up and when using fdisk to prepare the drives I get an error when saving the changes to the drive. The error is the following:

```


WARNING: Re-reading the partition table failed with error 16: Device or resource busy.

```

Now I need to delete the raid created in the installation and a raid that was made somehow. The names of the devices are md0 and md1.

Now for the question. 

How do I delete a raid?


The only raid ive ever set up was on a Dell Precision (Which was quite easy to delete), but your problem with the device being busy must be becuase kubuntu is accessing it, 
try setting up the raid without accessing any of the drives ie Before it boots to an OS, this is how i set up my raid, there was an option, CTRL-C i think, before the os loaded to enter and set up raid devices.

---

### Post by pdwerryhouse on 2008-10-24
The following should be enough:

```
mdadm --manage --stop /dev/md0
mdadm --manage --stop /dev/md1
```

---

### Post by fjgaude on 2008-10-24
After stopping the arrays, you might have to zero the superblocks on the two drives to permit **mdadm** to create new ones.

---

