---
title: "Problem with UserID"
date: 2008-09-04
forum: General Help
---

### Post by jimrazz on 2008-09-04
Hi,

I am an absolute newbie. Just installed xubuntu 7.04 alternate on a 11 year old dell laptop. I did not notice it was asking for a userid during installation. I did provide a password. Now in boot up it is asking it is asking for my userid. Can someone please help.

Thanks in advance,

Jim

---

### Post by sisco311 on 2008-09-04
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by louieb on 2008-09-04
Linux creates a folder /home/<userid>/ for each user.

Just need to find the name of that folder.

Select recover mode from GRUB.

and list list the folders in /home

```
ls /home
```

now you have the your userid and  can reboot 
```
reboot
```

If you have a live CD such as puppy  you can use that.

---

