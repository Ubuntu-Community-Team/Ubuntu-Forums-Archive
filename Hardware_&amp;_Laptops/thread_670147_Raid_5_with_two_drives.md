---
title: "Raid 5 with two drives"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by jumentous on 2008-01-17
I realise that raid 5 is designed for at least 3 disks however i have data on one of the three disks. what i would like to do is create a raid 5 array nominating 2 disks then copy all the data from the 3rd disk over to the new array and then add that drive to the array.

I know i can nominate the number of drives and i'm pretty sure you can force it to do 2 drives, but will this work?

---

### Post by LenzM on 2008-01-17
From the mdadm man page
> To  create a "degraded" array in which some devices are missing, simply give the word "missing" in place of a device name.

So your create command would look something like this: 
```

sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 missing /dev/sdc1

```

Then once you are done copying the data and want to add the third drive:
```

mdadm /dev/md0 --add /dev/sdb1

```

---

### Post by jumentous on 2008-01-17
Thanks LenzM

---

