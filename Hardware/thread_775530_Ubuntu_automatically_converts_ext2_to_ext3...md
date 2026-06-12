---
title: "Ubuntu automatically converts ext2 to ext3?.."
date: 2008-04-30
forum: Hardware
---

### Post by Burillo on 2008-04-30
I have an external 500GB Harddrive partitioned with 50GB NTFS and 450GB ext2. The reason i keep ext2 is simple - although the only obvious difference between ext2 and ext3 is journalling, there is another thing - it is possible to undelete with ext2. The drawback is the need of running fsck after every crash, but that's just the price.

But for some reason Kubuntu 7.10 (recently upgraded to 8.04) keeps creating journal on that partition. I've probably converted that partition to ext2 a million times now, and the next time i mount it Kubuntu creates journal and then after another mount sees the partition as ext3. Any ideas?

---

