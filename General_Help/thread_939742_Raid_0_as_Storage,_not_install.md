---
title: "Raid 0 as Storage, not install"
date: 2008-10-06
forum: General Help
---

### Post by GriFF3n on 2008-10-06
Hello,

I have Vista setup on a Raid 0 via software raid and have been wanting to move to Ubuntu. After reading the fakeraid how to, I've decided against installing the system on a raid 0. Instead I will be purchasing a VelociRaptor and dual boot from that. My question is, can i still setup the two drives as a raid 0 once i install the OS's on the VelociRaptor? I'd like to use them as storage for both Windows (NTFS) and Ubuntu (ext3). Is this possible? I decided against the Raid 0 install because I've read numerous posts about people having problems and I'd like to avoid that. Plus the fact that the VelociRaptors are faster than my two Seagate 250GB 7200.10 drives in raid makes me lean towards the single 10K drive. Thanks in advanced,

GriFF

---

### Post by octotracy on 2008-10-06
Hi,

I can't help, I've been trying to find out how to do this myself.  Unfortunately no one's yet responded to my thread.  Hope you have better luck :)

---

### Post by cariboo on 2008-10-06
HAve a look at this howto, is for an older version, but it should work:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

JIm

---

### Post by fjgaude on 2008-10-06
Sure what you wish can be done but it does rquire lots of detailed knowledge to pull it off... such knowledge is common! <smile>

First install Vista on the Raptor... then while in Vista cut back on the partition to a size you can live with, leaving the rest for the Ubuntu install.

Then install Ubuntu. Boot, and the grub menu will show two options, one to boot Ubuntu, the other for Vista.

Now while in Ubuntu, install **mdadm**. Using your two extra drives make the raid0, but first using **GParted**, format each of the drives to ext3, with flags as "raid". Use only one partition, i.e., partition the whole drive as sda1, sdb1, for example.

```
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```

Add the filesystem:

```
sudo mkfs -t ext3 /dev/md0
```

Then make a mountpoint for the array:

```
sudo mkdir /home/raid
```

Then mount the array at that mountpoint:

```
sudo mount /dev/md0 /home/raid
```

To have the array auto mount at boot time add this line as the last to your /etc/fstab file:

```
/dev/md0 /home/raid ext3 defaults 0 2
```

The raid0 will lose all data if one of the drives fail. **Backup all important data.**

Let us know how you are doing.

---

### Post by GriFF3n on 2008-10-06
> **fjgaude said:**
> Sure what you wish can be done but it does rquire lots of detailed knowledge to pull it off... such knowledge is common! <smile>

First install Vista on the Raptor... then while in Vista cut back on the partition to a size you can live with, leaving the rest for the Ubuntu install.

Then install Ubuntu. Boot, and the grub menu will show two options, one to boot Ubuntu, the other for Vista.

Now while in Ubuntu, install **mdadm**. Using your two extra drives make the raid0, but first using **GParted**, format each of the drives to ext3, with flags as "raid". Use only one partition, i.e., partition the whole drive as sda1, sdb1, for example.

```
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```

Add the filesystem:

```
sudo mkfs -t ext3 /dev/md0
```

Then make a mountpoint for the array:

```
sudo mkdir /home/raid
```

Then mount the array at that mountpoint:

```
sudo mount /dev/md0 /home/raid
```

To have the array auto mount at boot time add this line as the last to your /etc/fstab file:

```
/dev/md0 /home/raid ext3 defaults 0 2
```

The raid0 will lose all data if one of the drives fail. **Backup all important data.**

Let us know how you are doing.

Thanks fjgaude, The Raptor is in the mail right now so as soon as i have time I'll give your idea a try. One question though, will i be able to use the raid 0 in both windows and ubuntu to store data? If i format the whole raid 0 as ext3, windows won't see it correct?

GriFF

---

### Post by fjgaude on 2008-10-06
Well, you will be able to see NTFS data from the non-booted side while in Ubuntu. You can read and write to the Windows side.

Now if you wish to have two software raid0 partitions on the same pair of drives you will have to make one NTFS and the other ext3. But it's getting even more complex. Are you up to it?

So mucn to learn, eh?

---

### Post by octotracy on 2008-10-07
why do you have to format it as ext 3 at all?  Can't I just format it in NTFS so that windows will be able to read the info?

---

### Post by fjgaude on 2008-10-07
Okay, made one NTFS array and permit Ubuntu to read and write to it, using the ntfs-3g features of Ubuntu. All the data on the array will be NTFS... that works, AFAIK.

---

### Post by GriFF3n on 2008-10-29
Ok, so i have Ubuntu installed and Vista installed on my Velociraptor drive. I took my two old 250 GB Seagates and set them up as a raid 0 in Vista. I then partitioned them in Vista. I go into Ubuntu and it sees the Vista install on the Velociraptor drive, but it doesn't see the Raid 0. I can see the raid 0 in GParted, but i can not access the drive or its contents. Any body know what i can do to access those partitions?

GriFF

---

### Post by fjgaude on 2008-10-30
There's a program called **dmraid** that permits you to mount your Windows raid0 array. Use the man pages to learn its features.

---

