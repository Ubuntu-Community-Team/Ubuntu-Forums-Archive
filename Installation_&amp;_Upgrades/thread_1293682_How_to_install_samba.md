---
title: "How to install samba"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by watsonsun on 2009-10-17
Pse help me to install samba.  I have done the following:

/ect/init.d/samba restart
bash: /ect/init.d/samba: No such file or directory
root@watson-desktop:/etc/samba# 

When I tried to download n install
sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also ran the following commands
apt-get install
apt-get update
apt-get upgrade
then reinstall samba again, but unsuccessful
(I have no idea whether these would help,  but everybody is alway advising to do this)

Would appreciate any help

Thanks

---

### Post by Haegin on 2009-10-17
> **watsonsun said:**
> 
/ect/init.d/samba restart
bash: /ect/init.d/samba: No such file or directory


You misspelled the path. It should be /etc/init.d/samba, not /ect...

---

### Post by Arifa on 2010-12-29
Hi,

I have problems installing samba-common in my device (Haramattan)
The error I get is 
" ucf: Unable to determine The new file "

Could you please help me out in this.

Arifa

---

### Post by Rock89 on 2010-12-30
I am using Linux ES 4, and am attempting to  workaround some problems but it doesn't seem to be working thus far.What should i do?need some help

---

### Post by karthick87 on 2010-12-30
[https://help.ubuntu.com/8.04/serverguide/C/installing-samba.html](https://help.ubuntu.com/8.04/serverguide/C/installing-samba.html)

---

