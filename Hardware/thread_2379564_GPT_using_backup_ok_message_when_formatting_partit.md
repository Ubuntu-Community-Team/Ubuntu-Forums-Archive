---
title: "GPT using backup ok message when formatting partitionless 2x3TB RAID10 to ext4"
date: 2017-12-07
forum: Hardware
---

### Post by harrisoftware on 2017-12-07
as the title suggests, I created a partitionless RAID10 with two new 3TB drives (will likely expand it later by adding 1 or two more) and successfully created, initialized it.

when I went to format it ext4, I got the message "corrupt GPT backup ok using it instead" or something to that effect.

it mounts fine
copied 2.5TB to it.

Do I need to be concerned? Anyone out there familiar with this? It seems weird because there is no partition table - i always use partitionless for my RAID setups.

Warren

---

### Post by gordintoronto on 2017-12-07
When I Googled RAID 10 this is what I got: "A RAID 10 configuration requires a minimum of four disks, and stripes data across mirrored pairs...."

Did you mean to set up a RAID 1 array?

To the best of my knowledge, to use disk storage, you must have partitions. Do you have a reference which says something different?

---

### Post by harrisoftware on 2017-12-07
[https://unix.stackexchange.com/questions/14010/the-merits-of-a-partitionless-filesystem](https://unix.stackexchange.com/questions/14010/the-merits-of-a-partitionless-filesystem)

RAID10 with two disks is actually RAID1E
[https://www.techrepublic.com/article/non-standard-raid-levels-primer-raid-1e/](https://www.techrepublic.com/article/non-standard-raid-levels-primer-raid-1e/)

---

### Post by gordintoronto on 2017-12-07
Good to learn something new, such as partitionless.

Your RAID 1E reference says this: "Whereas RAID levels 0 and 1 each require a minimum of two disks, RAID 1E requires a minimum of three disks."

But you only have two disks.

---

### Post by harrisoftware on 2017-12-07
true. but you only need three or more disks if you want to to reap the speed benefits of raid1E/10. i do plan to add more later. What concerned me was the warning message when I went to format it. I need a sysop guru's opinion on this I think.

update: I ran fsck -b 32768 /dev/md0
on the filesystem and it fixed a lot of free block errors and now it mounts without complaining. 
still. not sure why this happened as both disks were new.

---

