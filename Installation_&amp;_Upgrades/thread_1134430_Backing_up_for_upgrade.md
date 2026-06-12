---
title: "Backing up for upgrade"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by phantom3113 on 2009-04-23
With Jaunty now released (and currently being torrented by yours truly) I'm looking into back-up methods. I was planning on using PartImage, but I'm a little confused on the details from the PsychoCats page that gives the howto. Will this work with multiple partitions, and if so how? Do I even need to backup / ? My current setup is about 9.4 Gb for / , 217 Gb for /home, and 4 Gb for swap (total of a 250 Gb Hdd, #'s are estimated). Finally, here is the output for "sudo fdisk -l":

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4288399

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246       30401   234195570    5  Extended
/dev/sda5            1246       29903   230195353+  83  Linux
/dev/sda6           29904       30401     4000153+  82  Linux swap / Solaris
```

How would one read this?

---

### Post by ahbart on 2009-04-23
Before an upgrade I do make an image of the root partition, using partimage on 'system rescue disk'. I rename my /home/user folder on the home partition, and make a backup of this whole /home/user folder to an external disk. 
After that I normally do a clean install on the root partition and use the home partition. 
After install I copy back everything I need, of will miss, like:
.mozilla, .thunderbird, etc.

---

### Post by phantom3113 on 2009-04-23
When you say, "copy back everything I need", are you referring to the root directory? I assume so since you said you would be using the /home directory which tells me you'll be mounting it (which I plan on doing). Also, when using PartImage, if I have it back up "/", will it only back up that partition since / and /home are separate?

---

### Post by ahbart on 2009-04-23
No no. Sorry. I did not make myself clear. 
If you do a clean install of Ubuntu, during installation you can choose to auto mount your existing home partition on /home. Because you renamed the /home/username directory, there will be a new /home/username directory created during installation. 

After installation you copy back the needed files and config files from the /home/old-username to /home/username. 
Partimage does not see any /. It just makes a copy of an entire partition. If your root partition is on sda1, you make an image of sda1. 

An image of your home partition is useful as a temporary backup before a upgrade. But you can not easily extract a single files from this image. But you can restore an entire home partition if anything is going wrong during installation.

---

### Post by phantom3113 on 2009-04-23
If I'm just automounting /home anyway, could I leave it how it is? If I understand correctly, if you tell it which partition to automount, it'll do just that and nothing else and then continue with installing the new root partition. Is this correct, or does the install manger on the cd format a partition even though it's already there?

---

