---
title: "preseeding raid with partman-auto-raid"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by joe-mac on 2009-01-09
Is anybody on earth using this functionality? It is mentioned in the docs, but for some reason the udeb (partman-auto-raid) isn't in the server install. So I added it to my pxe install, rebuilt the Packages file yaddaya and I still cannot get this functionality to work... I've been on the channels and no one seems to really know.

---

### Post by joe-mac on 2009-02-28
BUMP. Come on somebody has to have done this successfully. In the 8.04 docs it shows preseeding raid, but I just simply cannot get it to work. Here is my section on it:

```
# Partition the disks
d-i     partman-auto/method string raid
d-i     partman-auto/disk   string /dev/sda /dev/sdb

d-i partman-auto/expert_recipe string multiraid :: \
   100    100        150   raid   $primary{ } $bootable{ } method{ raid } . \
  4096   4096       4096   raid   method{ raid } . \
 10000  10000      10000   raid   method{ raid } . \
100000 100000 1000000000   raid   method{ raid }

d-i partman-auto-raid/recipes string \
   1 2 0 ext3 /boot /dev/sda1#/dev/sdb1 . \
   1 2 0 swap -     /dev/sda2#/dev/sdb2 . \
   1 2 0 ext3 /     /dev/sda3#/dev/sdb3 . \
   1 2 0 ext3 /opt  /dev/sda4#/dev/sdb4 .

# This makes partman automatically partition without confirmation.
d-i     partman-md/confirm              boolean true
d-i     partman/confirm_write_new_label boolean true
d-i     partman/choose_partition        select  finish
d-i     partman/confirm                 boolean true

# Install grub to both partitions
d-i     grub-installer/bootdev  string (hd0,0) (hd1,0)


```



I am preseeding non-raid setups just fine. This is a requirement for a our physical systems though, so preseeding is basically unusable ATM for physical systems. The udeb is not in the server cd, which is kinda worrisome, and it's in the 'universe' repo, but i enable universe in my apt-setup, so I would assume the d-i would go out and grab it if it's a dependency...

---

### Post by mhalligan on 2009-04-27
Clearly at least 2 other people besides myself are having this problem. How many before this is important enough to fix? Is there a Bounty system where I can pay to have this fixed?


> **joe-mac said:**
> BUMP. Come on somebody has to have done this successfully. In the 8.04 docs it shows preseeding raid, but I just simply cannot get it to work. Here is my section on it:

```
# Partition the disks
d-i     partman-auto/method string raid
d-i     partman-auto/disk   string /dev/sda /dev/sdb

d-i partman-auto/expert_recipe string multiraid :: \
   100    100        150   raid   $primary{ } $bootable{ } method{ raid } . \
  4096   4096       4096   raid   method{ raid } . \
 10000  10000      10000   raid   method{ raid } . \
100000 100000 1000000000   raid   method{ raid }

d-i partman-auto-raid/recipes string \
   1 2 0 ext3 /boot /dev/sda1#/dev/sdb1 . \
   1 2 0 swap -     /dev/sda2#/dev/sdb2 . \
   1 2 0 ext3 /     /dev/sda3#/dev/sdb3 . \
   1 2 0 ext3 /opt  /dev/sda4#/dev/sdb4 .

# This makes partman automatically partition without confirmation.
d-i     partman-md/confirm              boolean true
d-i     partman/confirm_write_new_label boolean true
d-i     partman/choose_partition        select  finish
d-i     partman/confirm                 boolean true

# Install grub to both partitions
d-i     grub-installer/bootdev  string (hd0,0) (hd1,0)


```

I am preseeding non-raid setups just fine. This is a requirement for a our physical systems though, so preseeding is basically unusable ATM for physical systems. The udeb is not in the server cd, which is kinda worrisome, and it's in the 'universe' repo, but i enable universe in my apt-setup, so I would assume the d-i would go out and grab it if it's a dependency...

---

