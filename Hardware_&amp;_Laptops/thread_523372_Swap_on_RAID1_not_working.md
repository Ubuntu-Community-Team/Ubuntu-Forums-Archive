---
title: "Swap on RAID1 not working"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by Luke.Hoersten on 2007-08-11
I have 2 harddrives RAID1. One partition on the raid is for swap (/dev/md1). My /dev/md1 (swap partition) is not working though. I have 4 gigs for it but when I mkswap, it fails:

> 
sudo mkswap -v /dev/md1 
mkswap: error: swap area needs to be at least 40kB

> cat /proc/mdstat 
Personalities : [raid1] 
md1 : active raid1 sdb3[1] sda3[0]
      3903680 blocks [2/2] [UU]


dmesg is complaining:
> Unable to find swap-space signature

Also, blkid doesn't output the UUID of /dev/md1, only the other drives.
> /dev/sda1: UUID="00a92b3a-c00c-40e3-8136-71cb007e6a24" TYPE="jfs" 
/dev/sda2: UUID="dc41d945-9978-4ef8-ad25-48153b77356f" TYPE="jfs" 
/dev/sda3: UUID="76847f11-b90a-43eb-a71f-abce13081b6c" TYPE="swap" 
/dev/sdb1: UUID="00a92b3a-c00c-40e3-8136-71cb007e6a24" TYPE="jfs" 
/dev/sdb2: UUID="dc41d945-9978-4ef8-ad25-48153b77356f" TYPE="jfs" 
/dev/sdb3: UUID="76847f11-b90a-43eb-a71f-abce13081b6c" TYPE="swap" 
/dev/md2: UUID="00a92b3a-c00c-40e3-8136-71cb007e6a24" TYPE="jfs" 
/dev/md3: UUID="dc41d945-9978-4ef8-ad25-48153b77356f" TYPE="jfs" 


Here is my mdadm.conf:
> # definitions of existing MD arrays
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=46c004ae:64194c2a:59cbb14a:d9cb6217
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=c89964e6:fb5e648f:c05c29cf:1bc2888a
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=458ac06e:d3c9cdbc:9273208c:74ebfb58


Any reason my swap raid drive isn't working?

---

### Post by Luke.Hoersten on 2007-08-11
The problem was that in my partition tables, I had my swap partitions marked as Linux Raid partitions and apparently because the Linux kernel already RAID-0s all swap partitions, swap partitions shouldn't be marked as raid. They should be marked as swap.

---

### Post by ronny_d on 2007-08-12
.

---

### Post by ronny_d on 2007-08-12
.Sorry, i posted on your thread accidentally. :confused: Forgive me.

---

### Post by Midahed on 2007-08-12
> **Luke.Hoersten said:**
> The problem was that in my partition tables, I had my swap partitions marked as Linux Raid partitions and apparently because the Linux kernel already RAID-0s all swap partitions, swap partitions shouldn't be marked as raid. They should be marked as swap.
That's true, but the decision to raid or not raid swap partitions really depends what you want to achieve.  

I have two swap partitions located on two different drives marked as raid and they work fine.  You're quite right that if you declare two identical swap partitions with equal priorities and declare them as swap, the kernel will effectively use them as raid0 (striped) partitions for improved performance under heavy-swap conditions.  However you can also declare them as raid devices and set-up a software raid1 (mirror) environment.  That's what I've done.  Having a raid1 swap is commonplace on 'non-stop' systems.

Mike

---

