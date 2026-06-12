---
title: "It's OK to copy testing Ubuntu partition into main partition, right?"
date: 2005-11-23
forum: General Help
---

### Post by ultranet on 2005-11-23
I'm thinking about formatting my FC5 partition, and copying the smaller testing partition w/ Ubuntu on it over, and then just update menu.list to point to the main partition, w/o reinstalling Ubuntu or bootloader. I expect this to work innocuously, but if you know something to the contrary, please speak up.

Thanks.

---

### Post by az on 2005-11-23
You can format the partition as ext3 (or whatever other linux filesystem that turns you on) and just copy the files there, or copy the data using parted.  You can also datadumpt (man dd) the partition, but I recently did that and now have a wierd ext3 partition that works fine but won't fsck, nor resize (!)


So, yes you can.  Do not forget to change fstab, too!

---

