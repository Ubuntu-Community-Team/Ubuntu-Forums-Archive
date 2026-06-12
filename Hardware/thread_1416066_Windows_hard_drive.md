---
title: "Windows hard drive"
date: 2010-02-25
forum: Hardware
---

### Post by krellmk on 2010-02-25
Can i remove my D drive hard drive from my windows box and install it in my linux box without reformatting under linux

---

### Post by dabl on 2010-02-25
Yes, but I don't know why you would do that, except maybe one time to copy data off of it.  ext3 or ext4 are better performing, and more reliable, than NTFS.

---

### Post by krellmk on 2010-02-25
I'm done with windows that the reason why i wanna transfer my hard drives to my new linux box.

---

### Post by dabl on 2010-02-25
> **krellmk said:**
> I'm done with windows that the reason why i wanna transfer my hard drives to my new linux box.

OK.

So, you can mount it as a ntfs-3g filesystem, then copy your data off of it.    Then use GParted to format it to ext4 and use it for saving your data under Linux.

---

