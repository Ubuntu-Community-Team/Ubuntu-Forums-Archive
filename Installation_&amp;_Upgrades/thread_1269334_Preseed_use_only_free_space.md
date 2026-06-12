---
title: "Preseed use only free space"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by korax on 2009-09-18
I have been working on a ubuntu restore partition that sits at the start of the drive that will do an automatic install using preseed

I have ran in to a bit of a wall with doing the partition

What I am wanting to do is leave sda1 (restore partition) intact  and use the rest of the disk for the install

eg.
/dev/sda1 ~1gig restore [leave as-is]
/dev/sda2 max ext3 /
/dev/sda5 ~2gig swap


This is what I have got so far:
```

#Remove partitions other then sda1
d-i partman/early_command string for i in 8 7 6 5 4 3 2 ; do if [ "`fdisk -l /dev/sda | grep /dev/sda$i`" ]; then echo -e "d\n$i\nw\n" | fdisk /dev/sda ; fi ; done; exit 0;

d-i partman-auto/init_automatically_partition select biggest_free

d-i partman-auto/method string regular

d-i partman-auto/expert_recipe string                         \
      partceo ::                                              \
              1000 10000000 -1 ext3                           \
                      $primary{ }                             \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ / }                         \
              .                                               \
              96 1024 200% linux-swap                          \
                      method{ swap } format{ }                \
              .

d-i partman-auto/choose_recipe select partceo

```

With the recipe it seems to ignore the "init_automatically_partition select biggest_free"
(using recipe atomic it does a similar thing aswell)
eg.
/dev/sda1 max ext3 /
/dev/sda5 ~2gig swap

Without the recipe it creates the / partition as extended 
eg.
/dev/sda1 ~1gig restore
/dev/sda5 max ext3 /
/dev/sda6 ~2gig swap


Any suggestions on how to use a recipe with only using free space?



EDIT: Found the problem. I also had
```
d-i partman-auto/method string regular
```
Which was causing it to ignore the "select biggest_free"

---

