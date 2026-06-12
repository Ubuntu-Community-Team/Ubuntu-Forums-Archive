---
title: "new hard drive partion wont mount correctly"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by ninjaprawn on 2007-05-18
hi

ive just partitioned what used to be ntfs to ext3. i was using the ntfs-3g driver, so after partioned, i went to;
/etc/fstab

and just changed the driver from ntfs-3g to ext3, thinking that would change the  driver used.

it did, when i rebooted, i had my ext partition on my desktop, ready to use, 

i opened it up, obviously no data, so tried to create a new folder on it! it said i dont have the right permisions!!

thats where im stuck!!!!!!!!

i then went back into /etc/fstab to see, and in the code line for this partition, there was a part that said;
- ro     ->   so i changed it to    ->    - rw

i had copied the options from the line for the partion with the os on, but the drive only mounts with ro, not atall with rw!!

what is wrong???
thanks

---

### Post by ninjaprawn on 2007-05-18
ill post what my /etc/fstab looks like in a bit!

any ideas so far??

thanks

---

