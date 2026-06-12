---
title: "[SOLVED] Backing up files to Samba"
date: 2008-08-25
forum: General Help
---

### Post by suzypeppercorn on 2008-08-25
I'm looking for a program that can backup files to my network drive. I have tried countless programs but none support samba shares from what i can see.

It seems like it'd be easy to find but i have been looking all day and come up with nothing.

Anyone? Thanks

---

### Post by tramir on 2008-08-25
How would you want the program to "support" samba shares? In the sense of mounting it for you? Or in the sense of being able to preserve the permissions of the files?

If it's the first, you can always make a bash script that first mounts the share and then runs the backup program. You can easily automate Unison, for instance, like this.

If it's the second, the only thing I found until now (other than "archive everything into a tar") was Ukopp, which saves the permissions into a file that it can use for restoring them later.

Hope this answers your question :d

---

### Post by dmizer on 2008-08-25
You can use rsync too.  As long as the share is mounted by /etc/fstab you should be able to use any backup tool available to Ubuntu.

---

### Post by suzypeppercorn on 2008-08-25
> **dmizer said:**
> You can use rsync too.  As long as the share is mounted by /etc/fstab you should be able to use any backup tool available to Ubuntu.

i was looking into this. But i didnt think i would be able to get it done. when i browse to my network drive the address bar says this.

smb://student/gilberjp$/

how would i make this work. i have read your great tutorial btw. would student be the netbios name?

---

### Post by y@w on 2008-08-25
Yes, student would be the netbios name. With Samba on Linux, I've found that using the IP is much more reliable than netbios, however. (as long as you're using static IPs that is)

---

### Post by suzypeppercorn on 2008-08-25
thanks guys! i got everything working correctly with the mounting portion and i will be able to get everything with the backing up soon but i have a question.

if i am away from my network will i get an ugly error message saying that it can't connect to my network share. if so would there be a way to disable that?

---

### Post by dmizer on 2008-08-25
> **suzypeppercorn said:**
> if i am away from my network will i get an ugly error message saying that it can't connect to my network share. if so would there be a way to disable that?

Nope, no ugly message at all. There would be a message in dmesg if you cared to look at the output, but nothing annoying.

---

### Post by suzypeppercorn on 2008-08-25
thanks again for the help guys

---

