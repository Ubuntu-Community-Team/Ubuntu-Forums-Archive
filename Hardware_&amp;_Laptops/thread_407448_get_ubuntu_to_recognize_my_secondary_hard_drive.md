---
title: "get ubuntu to recognize my secondary hard drive"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by Benifited on 2007-04-12
i just switched over from vista. and i have a 80g hd that i keep my stuff in. ubuntu doesn't recognize it and i was wondering if i got get it to work and still keep my stuff in it. 


thx for any help possible.

---

### Post by mac.ryan on 2007-04-12
If you have changed from Vista, so you don't need to have that partition accessible from a windows system any more, I would suggest to convert it to EXT3 filesystem (maybe you could mount that entire partition as your /home, a very useful configuration, in case of system breaks/updates).

If you can't or want not to do the above, here there is an how-to on how to mount win partition into ubuntu:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

EDIT: furthermore, if you mount a NTFS into ubuntu, you will need / might wish to make it writable as well. I used this how-to months ago... but I think it is still up-to-date now: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Benifited on 2007-04-12
oh man thx a lot worked like a charm. btw where does the trash go

---

### Post by mac.ryan on 2007-04-13
> **Benifited said:**
> oh man thx a lot worked like a charm. btw where does the trash go

Happy it worked (I assume you kept the NTFS format). As for the trash, I don't share partitions any more (as I converted everything to GNU/Linux now). You might have a look if any directory called ".Trash" on your NTFS drive have been created (this is the name of the trash directory on EXT3 partitions), but I am not sure if the trash function is implemented on NTFS...

---

