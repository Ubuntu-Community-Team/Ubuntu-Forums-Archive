---
title: "/dev/zero vs /dev/null"
date: 2008-08-06
forum: General Help
---

### Post by sulekha on 2008-08-06
Hi,

 what exactly is the subtle difference between /dev/zero and /dev/null ?

the following is what i got when i gave the command man zero on the terminal

 Data written on a null or zero special file is discarded.

       Reads  from  the  null  special file always return end of file, whereas
       reads from zero always return \0 characters.

       null and zero are typically created by:

              mknod -m 666 /dev/null c 1 3
              mknod -m 666 /dev/zero c 1 5
              chown root:root /dev/null /dev/zero

---

### Post by mcduck on 2008-08-06
Well, you pretty much already said the difference in your post. Reading from /dev/zero provides you with zeroes, while reading from /dev/null provides no data.

So you can use /dev/zero to create empty files of certain sizes, or to overwrite disks with zeroes, while /dev/null wouldn't work for this kind of purposes.

---

