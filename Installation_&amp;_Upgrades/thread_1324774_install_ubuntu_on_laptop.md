---
title: "install ubuntu on laptop"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by guidenhelp on 2009-11-12
hello friends,
i was using windows xp and ubuntu 9.04 on my laptop. i got samsung vm 8000, celeron with 256 SDRAM and 80GB hd. i have seen ubuntu 9.10 on my friend's laptop and decided to install stand alone on my laptop. so i have format and break partition and now i want to install ubuntu 9.10 only os on my computer. i know how to install it but what i don't know is how to make partitions for security purpose. by default ubuntu make two partition ext4 and swap, and i new that this is not enough for security. would any body will let me know that what other partition i need for 80GB hardisk for ubuntu 9.10? what is the partition size i should put for each partition that i will make? how manual partition give me security. well i have live with my few friends and we share home, so some times they use my laptop. so i will be not only user for that. i want to know that what is concept for multi partition.
Thanks,

---

### Post by Axos on 2009-11-12
I am not a security expert but here are a couple of pages to read on the subject:

[https://help.ubuntu.com/9.10/keeping-safe/C/index.html](https://help.ubuntu.com/9.10/keeping-safe/C/index.html)
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

Basically, I don't think you need to worry about creating lots of partitions for security. The default partitions will work fine.

You do need to understand how to use the chmod command to change the permissions on directories and/or files. By default, all the files in your home directory tree are readable by anyone else on the system. Even if you enable home directory encryption (second link above), your files are decrypted while you are logged in. If another user were to leave a process running after they logged out, they could access your files while you are logged in. So in addition to using encryption to protect your files while you are logged out, you need to use chmod to make your home directory (or certain subdirectories you wish to keep private within it) unreadable by other users. It's possible that this is taken care of automatically when you enable home directory encryption. I've never used it so I don't know.

Again, I'm not an expert. Just trying to point you in the right direction with those links.

---

### Post by tuxstesco on 2009-11-12
bookmarked and b back l8er,i need more info, :-)

---

