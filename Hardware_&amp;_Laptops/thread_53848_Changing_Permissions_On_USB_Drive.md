---
title: "Changing Permissions On USB Drive"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by alec on 2005-08-02
Hi.

I am using Kubuntu. I have just re-partitioned, and formatted an external USB drive using qtparted. However because this was done using kdesu not in a root acount, the drive now shows that it belongs to root, not user alec which is me.

In other words the drive is now useless to me because I have to be logged on as root to use it or change permissions.

How in ubuntu/kubuntu do you change permissions on the drive if you cannot log on as root?

---

### Post by dave9191 on 2005-08-02
You can still issue root commands. As it said in the installation instructions and the guides about sudo. If you want to run a command as root, then just put sudo before it. Or you can type sudo bash for a root console. You can then change the ownership of the files back to you. 

sudo chown -r username:usergroup /dir/to/files

that should be it. 

Dave

---

