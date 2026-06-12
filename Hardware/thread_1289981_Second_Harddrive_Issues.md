---
title: "Second Harddrive Issues"
date: 2009-10-13
forum: Hardware
---

### Post by AnimeFreak on 2009-10-13
hello all is me again with the same harddrive  but different issue

after playing around a bit i managed to be able to see it in the computer folder as what i called it "HotSpot" or to get its actual name its "sdb"

ok heres my problem i can now see it but i want to make it a blank hard drive for storage but when i try to do so it tells me that i do not have permission to add files because i dot own the drive after i i format, restart and then mount.

the reason i restart is because i can't see it after i format it only after i restart....if i am doing something wrong please tell me.

any way that  is the only issue i have now so any imput is greatly appreciated 

p.s. if it helps i will answer any questions about what i did to get this far..

---

### Post by nzadLithium on 2009-10-13
What partition format did you use?
How are you mounting it? paste your mount command or your line from fstab.

---

### Post by AnimeFreak on 2009-10-13
> **nzadLithium said:**
> What partition format did you use?
How are you mounting it? paste your mount command or your line from fstab.

ext3

not sure what u mean by "haw are u mounting it" 

and how do i find my mount camand

---

### Post by AnimeFreak on 2009-10-13
all i did was remember what te format was when it worked (fat32)

so i formated it to that and poof it works

---

### Post by nzadLithium on 2009-10-13
That'll be because your computer was already setup to mount a fat32 partition, if you format the partition to ext3 you would then have to modify the line in fstab so it was mounting an ext3 partition. Theres also the thing that fat32 partitions do not support file permissions, you can't make a file accessible to one user but not accessible to another, while ext3 partition do support it. So you have to set the permissions differently across the different filesystems.

---

