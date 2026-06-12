---
title: "Move externally mounted directories back into root drive"
date: 2011-08-10
forum: Hardware
---

### Post by its_me_gb on 2011-08-10
When i set up my system i seperated out some of the folders into their own partitions. i have since realiased that i provisioned the partitions way too much space. i know i could resize them to gain the space back, but what i would like to do instead is move the folders back into the filesystem but on the root partition.

Currently i have this setup:
```

sdd
   1 - /
   5 - /tmp
   6 - /var
   7 - /usr
```

Is there an easy way for me to move /tmp, /var and /usr back into the / partition? or will i have to boot into a live disc so they aren't mounted and then copy the folders onto the root partition and then remove their entries from the fstab?

---

### Post by coffeecat on 2011-08-10
> **its_me_gb said:**
> 
Is there an easy way for me to move /tmp, /var and /usr back into the / partition? or will i have to boot into a live disc so they aren't mounted and then copy the folders onto the root partition and then remove their entries from the fstab?

You've answered your own question! :wink: The easy way is to boot into a live CD, copy the contents of the /tmp, /var and /usr partitions into the /temp, /var and /usr directories of the root partition and then edit /etc/fstab.

You won't be able to do that from "inside" your permanent installation, because if you try to copy the files from the /usr partition (for example) into the /usr folder (in which your /usr partition is mounted), you'll be attempting a circular copy, since the system will be trying to copy the files back onto themselves. I guess the process would error out.

By the way, use the command "sudo cp -av" for the copy. Option -a for recursion and permissions perservation among other things (check man cp for details) , and option -v to get visual feedback. The /usr copy in particular is going to take some time.

---

### Post by its_me_gb on 2011-08-10
Heh, i though i might have!

Thanks for your advice regarding the cp command. i'll give this a go tonight.

---

