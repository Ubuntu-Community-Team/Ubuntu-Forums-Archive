---
title: "www-data group is messed up"
date: 2008-11-23
forum: General Help
---

### Post by 5circles on 2008-11-23
I think I managed to mess up the www-data group, by using the graphical tool, and perhaps by incorrectly trying to copy from a 7.04 system

I think I deleted the group in the graphical tool.  At any rate, when I tried to run 'chown -R www-data:www-data' I got an error message.

At that point, the entry in /etc/passwd showed UID of 33 and GID of 65534 for www-data.  The 7.04 system has 33:33.

I recreated the group using 'groupadd -g 33 www-data', and was then able to do the chown.  But the entry in /etc/passwd is still 33:65534.  Is this something I need to worry about?  Is it to do with the mirroring of password files?

Thanks

---

