---
title: "problem writing truecrypt container"
date: 2005-11-24
forum: General Help
---

### Post by inhetep on 2005-11-24
Hi,

after installing and mounting a tc container I am unable to write any data on it.
I am mounting it with the following line as 'normal user'

 sudo truecrypt /media/truecrypt/MyData.tc  /share/truecrypt --mount-options 'umask=000,uid=1000,gid=100' 

or as root with 

truecrypt /media/truecrypt/MyData.tc  /share/truecrypt

Read access is possible.

What could be the problem?

Help would really be appreciated.

---

### Post by inhetep on 2005-11-25
Problem solvedthe container had as fs ntfs. After changing it to vfat everything works like a charme.

---

