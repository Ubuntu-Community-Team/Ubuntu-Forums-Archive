---
title: "pre-init startup script"
date: 2008-08-25
forum: General Help
---

### Post by Wellconnected on 2008-08-25
Dear All,

I have happily and quite easily hacked Xubuntu be served from a TFTP server and NFS server in order to run Xubuntu on a few diskless hosts.

This is all going nicely to plan, the Xubuntu root directory is a ro NFS share, and I have a PERL script that I want to run at startup so that it merges a few TMPFS rw filesystems onto the ro root with unionfs so that the system boots up.

at the moment I am running my PERL script from /etc/init.d/ which is OK, but it is a bit late and it interferes a bit with the running of the system. I would ideally like it to run just after mounting the root partition.

I tried putting the script in:

/etc/initramfs-tools/scripts/init-bottom

and updating my initram disk, but when starting I get errors that the file doesn't exist.

could anyone either tell me how to build the initramfs correctly, or tell me how to make a script run really early in the boot up sequence?

Thanks,
wellconnected

---

### Post by Wellconnected on 2008-08-25
I think I found the answer - put the script to start in rc.S

This is very different from slackware - sorry for the confusion.

---

