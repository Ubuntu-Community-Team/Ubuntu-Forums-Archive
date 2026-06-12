---
title: "How to display a different motd in SSH"
date: 2008-11-22
forum: General Help
---

### Post by redhotfire on 2008-11-22
If this is the wrong section, sorry, I'm new here and didn't know where else to put it. I am using Debian.

When I modify my motd in /etc/motd, it stays that way I modified it until I restart the machine. It then goes back to default. I was wondering where I would also change it so that it wouldn't do this. 

Thanks,
Red

---

### Post by lswb on 2008-11-22
See "man motd" for the answer. /etc/motd is actually a link to a file on /var/run that is rewritten at every boot. Permanent changes can be made by editing /etc/motd.tail, or by changing /etc/motd to link to a different file.

---

### Post by redhotfire on 2008-11-22
> **lswb said:**
> See "man motd" for the answer. /etc/motd is actually a link to a file on /var/run that is rewritten at every boot. Permanent changes can be made by editing /etc/motd.tail, or by changing /etc/motd to link to a different file.

Ok thanks, another question. How would I modify /etc/motd to link to a different file? :confused:

---

### Post by lswb on 2008-11-22
First remove the current link:

sudo rm /etc/motd

Then make a new symbolic link that points to the desired file:

sudo ln -s /path/to/file /etc/motd

---

### Post by redhotfire on 2008-11-22
Thank you for caring enough to post. :)

---

