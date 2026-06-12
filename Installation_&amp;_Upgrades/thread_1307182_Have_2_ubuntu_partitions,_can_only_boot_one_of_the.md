---
title: "Have 2 ubuntu partitions, can only boot one of them."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by rkylain24 on 2009-10-30
Here is the story. I have had ubuntu for quite some time. It was ext2 so i wanted to get on ext4. I upgraded to ubuntu 9.10 today. I backedup ubuntu using tar. Then i made an ext4 partition and restored the backup there. I never removed my ext2 partition. I can only boot from the ext2 partition. Even changing the boot flag to the ext4 partition won't help. Grub acts almost as if it can't see the ext4 partition. I have grub 1.5 btw. Maybe it can't identify ext4. Anyways i don't even want my ext2 partition, but now do you see why i kept it temporarily? I still plan on removing my ext2 partition, but thats my only bootable partition right now. 

My ext2 partition is /dev/sdb2
My ext4 partition is /dev/sdb4

Do i need to update grub? If so how?
How can i get my ext4 partition to boot?

I've never had to do any grub editing, so please keep that in mind when describing how to fix this problem.

Thanks in advance!

---

### Post by Sensiva on 2009-10-31
Are you sure that /dev/sdb4 is a **Primary** partition not a **Logical** partition?
Changing boot flag of a **Logical** partition won't make it boot

---

### Post by rkylain24 on 2009-10-31
I'm quite sure it's a primary partition. I don't even think gparted can make logical.

---

