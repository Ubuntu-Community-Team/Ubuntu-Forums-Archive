---
title: "Installing Ubuntu using Preseed"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by alegr44 on 2009-11-04
Hi, 

I need some help creating a unattended installation with ubuntu 9.04. I have two problems,

The first one is creating the partitions: 

This is my seed:

```
#d-i partman-auto/init_automatically_partition select custom

d-i partman-auto/disk string /dev/sda

d-i partman-auto/method string regular

d-i partman-lvm/device_remove_lvm boolean true

d-i partman-md/device_remove_md boolean true

d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              2048 50 2048 ext3                               \
                      $primary{ }                            \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
              .                                               \
              500 10000 1000000000 ext3                       \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ / }                         \
              .                                               \
              64 512 300% linux-swap                          \
                      method{ swap } format{ }                \
              .
```

Basically,I need to create 3 partitions, one for swap, another for for / (dev/sda1), and the last one is not mount but need to have 2GB (/dev/sda2).

With this recipe if I run the installation using debug-ubiquity and get the partition part of the installation it's shows me the partitions ok, but as soon as I used the automatic-ubiquity it's tells me that the root partition (/) is too small. 

What could be the problem? I had also tried putting the recipe in one single name. If i use the atomic recipe works like a charm, but i need this specific configuration.

The second problem is:

```
d-i preseed/late_command string sudo chroot /target chmod +x /etc/init.d/jboss;
```
or 
```
ubiquity/success_command string sudo chroot /target chmod +x /etc/init.d/jboss;
```

Neither works. I need to run this command at the end of the installation but never works. I check the target and the jboss's file exists.

Any tips or tricks to do this? 

I have read a lot of information, but I'm missing something, so please can anybody give me a hand on this.

Thanks a lots.

Alejandro

---

### Post by sebthemonster on 2011-02-25
Hello alegr44,

have you resolved your problem because I have the same and I have more difficulties to run my preseed/late_commands.

Thanks for your response

---

### Post by OpenThinking on 2011-08-30
Hi!

This command format worked for me in Ubuntu 11.04:
```
d-i preseed/late_command string df > /target/home/df.txt
```

These were the disk filesystems available during late preseed:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   254000       148    253852   0% /dev
/dev/sr0                723414    723414         0 100% /cdrom
/dev/sda1             20125340   2106856  16996176  11% /target
/dev/sda1             20125340   2106856  16996176  11% /dev/.static/dev
tmpfs                   254000       148    253852   0% /target/dev
/dev/sr0                723414    723414         0 100% /target/media/cdrom
```

Regards, Tobias

---

