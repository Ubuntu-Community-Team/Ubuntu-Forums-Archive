---
title: "Problem with preseed partitioning"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Linuxspider on 2009-06-30
Hi,

I am running into a problem when I want to install a system via a preseed config file. The system is a HP Proliant DL380 G5, using SmartArray. 

The problem is that there probably is a syntax issue in the partition part of the preseed file. However, the installer doesn't give a blink and installs the default partition scheme, which I do not want. The parition scheme in the preseed file looks like this:

d-i partman-auto/method string regular
d-i partman-auto/disk /dev/cciss/c0d0
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-auto/expert_recipe string \
                   boot-root ::                                         \
                        2048 50 2048 ext3                               \
                        $primary{ }                                     \
                        method{ format } format{ }                      \
                        use_filesystem{ } filesystem{ ext3 }            \
                        mountpoint{ / }                                 \
                        .                                               \
                        2048 50 2048 linux-swap                         \
                        $primary{ } method{ swap } format{ }            \
                        .                                               \
                        4096 50 4096 ext3                               \
                        method{ format } format{ }                      \
                        use_filesystem{ } filesystem{ ext3 }            \
                        mountpoint{ /usr }                              \
                        .                                               \
                        4096 50 4096 ext3                               \
                        method{ format } format{ }                      \
                        use_filesystem{ } filesystem{ ext3 }            \
                        mountpoint{ /var }                              \
                        .                                               \
                        2048 50 2048 ext3                               \
                        method{ format } format{ }                      \
                        use_filesystem{ } filesystem{ ext3 }            \
                        mountpoint{ /tmp }                              \
                        .                                               \
                        4096 50 1000000000 ext3                         \
                        method{ format } format{ }                      \
                        use_filesystem{ } filesystem{ ext3 }            \
                        mountpoint{ /data }                             \
                        .
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
       select Finish partitioning and write changes to disk
d-i partman/confirm boolean true


So, can someone tell me where I go wrong, or what I can do to fix this ?

thanks,
Andy

---

### Post by Linuxspider on 2009-07-01
I've solved the problem myself...

It appears that the installer can't handle the partition recipe when escape chars are used (for sake of readability). Once I left them out and pout the recipe on one line, it worked like a charm.:p:p

cheers,
Linuxspider

---

