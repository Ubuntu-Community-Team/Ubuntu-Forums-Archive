---
title: "How to make a non-persistent /home ?"
date: 2008-09-06
forum: General Help
---

### Post by haragog on 2008-09-06
After years of searching around these forum, making and adapting (mostly) others problems and solutions into my own, this is my first question.

After being tired of screwing up ubuntu instalation, and having to reinstall over and over, (manly nowadays because of a problem of permissions with .dmrc in home), and after searching (yes I did search) I would like to know if there is a away to make your /home non-persistent, and only when you want to, persistent.
I do have a /home in a separate partition. (and I do not use home much)

If there is...tell me about it!If it does not...thank you anyway!:lolflag:

---

### Post by Vivaldi Gloria on 2008-09-06
I don't know what you mean by persistent.

I prefer NOT to make a home partition but I make a seperate storage partition as I expained here:

[http://ubuntuforums.org/showthread.php?t=911729](http://ubuntuforums.org/showthread.php?t=911729)

I symlink my storage partition inside home.

I like having fresh /home and config files when I reinstall/upgrade ubuntu but also keeping my files intact on a seperate storage partition.

In a future install I can mount that partition as /home if I want to.

---

### Post by haragog on 2008-09-06
I mean like this: (in this case, sandbox a cloned user)
[http://www.howtoforge.com/safe_mirror_unionfs_chroot]("http://www.howtoforge.com/safe_mirror_unionfs_chroot")

in ubuntu?

---

### Post by Vivaldi Gloria on 2008-09-06
> **haragog said:**
> I mean like this: 

Sorry, too advanced for me. ;)

---

### Post by haragog on 2008-09-07
Thank you anyway.
I followed the instructions in that site almost exactly (the only change I did was instead of: groupadd -g 27 uniongroup, (it said 27 wasnt an unique gid) I added: groupadd -g 27 **-o** uniongroup so that the gid group was doubled).
But I ended with a normal user....not a sandbox one!Help?Is there another solution?

---

