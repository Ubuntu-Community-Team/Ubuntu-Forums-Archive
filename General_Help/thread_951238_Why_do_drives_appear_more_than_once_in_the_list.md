---
title: "Why do drives appear more than once in the list?"
date: 2008-10-17
forum: General Help
---

### Post by Pro-reason on 2008-10-17
Why are certain drives coming up more than once?

```

# blkid
/dev/sda1: TYPE="swap" UUID="21bbabd1-1b2d-43e0-8eb9-9513ed4c5edb"
/dev/sda2: UUID="9ACC9F03CC9ED8B9" LABEL="Windows" TYPE="ntfs"
/dev/sda3: UUID="688644aa-a168-4298-9c03-3721c1b023c8" TYPE="reiserfs" LABEL="Kubuntu"
[B]/dev/sda7: TYPE="swap" UUID="21bbabd1-1b2d-43e0-8eb9-9513ed4c5edb"
/dev/sda8: TYPE="swap" UUID="21bbabd1-1b2d-43e0-8eb9-9513ed4c5edb"[/B]
/dev/sdb1: TYPE="swap" UUID="b793bd32-eb43-4f92-9a70-0a7b52456e77"
/dev/sdb5: LABEL="Files" UUID="b1d5011b-f544-4c19-b895-e8ba52f4aa54" TYPE="ext3" SEC_TYPE="ext2"
/dev/sdb6: UUID="ca6e5bbf-6d48-4ffb-bd85-5fb7f8e024ef" TYPE="ext2" LABEL="Puppy"
/dev/sdb7: LABEL="Extra" UUID="3a63d751-e88a-4ae7-9eb6-c5906232476c" TYPE="jfs"
**/dev/sdb8: LABEL="Extra" UUID="ca19c720-3930-4bcf-a5a8-c91c57a835b2" TYPE="jfs"**
/dev/sdc1: UUID="879c29ff-91fb-4073-9b54-517b0b3d614b" TYPE="xfs" LABEL="Green"
**/dev/sdd1: UUID="879c29ff-91fb-4073-9b54-517b0b3d614b" TYPE="xfs"**
/dev/ramzswap0: TYPE="swap"

```

Superfluous entries are in bold.  

This is making swap spaces fail to work if I use UUIDs.

Linux chameleon 2.6.27-7-generic #1 SMP Tue Oct 14 18:40:44 UTC 2008 i686 GNU/Linux (Kubuntu 8.10 Intrepid Ibex).

---

### Post by plucky on 2008-10-18
> Why are certain drives coming up more than once?



Did you upgrade from Hardy?

I was getting the same problem on Ubuntu 8.10,which I upgraded from Hardy,but on the same machine I have a clean install of Xubuntu beta and that does not have the problem.

To fix the problem from a terminal```
cd /etc
sudo mv blkid.tab blkid.old
sudo blkid
```

The last command should recreate a blkid.tab file,which should have the correct entries.

Good Luck

---

### Post by Pro-reason on 2008-10-18
I did a clean upgrade to Intrepid.

I'm still getting some superfluous entries:

```

/dev/sda1: UUID="21bbabd1-1b2d-43e0-8eb9-9513ed4c5edb" TYPE="swap"
/dev/sda2: UUID="9ACC9F03CC9ED8B9" LABEL="Windows" TYPE="ntfs"
/dev/sda3: UUID="688644aa-a168-4298-9c03-3721c1b023c8" LABEL="Kubuntu" TYPE="reiserfs"
[B]/dev/sda7: UUID="21bbabd1-1b2d-43e0-8eb9-9513ed4c5edb" TYPE="swap"
/dev/sda8: UUID="21bbabd1-1b2d-43e0-8eb9-9513ed4c5edb" TYPE="swap[/B]"
/dev/sdb1: UUID="b793bd32-eb43-4f92-9a70-0a7b52456e77" TYPE="swap"
/dev/sdb5: LABEL="Files" UUID="b1d5011b-f544-4c19-b895-e8ba52f4aa54" TYPE="ext3"
/dev/sdb6: LABEL="Puppy" UUID="ca6e5bbf-6d48-4ffb-bd85-5fb7f8e024ef" TYPE="ext2"
/dev/sdb7: LABEL="Extra" UUID="3a63d751-e88a-4ae7-9eb6-c5906232476c" TYPE="jfs"
/dev/sdc1: LABEL="Green" UUID="879c29ff-91fb-4073-9b54-517b0b3d614b" TYPE="xfs"

```

---

