---
title: "How to change arcihve server?"
date: 2008-10-31
forum: General Help
---

### Post by Usta_AsH on 2008-10-31
hi I'm using 6.06
when I try to download it downloads from:
[http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) 
this site.
this is too slow, it's downloading like 2000B/sc that equals to 2 kb/sc. How can I change that archive, I want to use european archive(like from germany)

---

### Post by geirha on 2008-10-31
Been a while since I've used Dapper ... In Hardy at least, you go to System -> Administration -> Software Sources to change the repository mirror to use. Not sure if it's the same in Dapper though.

---

### Post by Usta_AsH on 2008-10-31
> **geirha said:**
> Been a while since I've used Dapper ... In Hardy at least, you go to System -> Administration -> Software Sources to change the repository mirror to use. Not sure if it's the same in Dapper though.

How can I do that from ssh? I only use ssh at this time...

---

### Post by geirha on 2008-10-31
Through ssh, I guess editing /etc/apt/sources.list manually is the easiest. There's a list of mirrors here: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

```
sudo vim /etc/apt/sources.list
```

---

### Post by Usta_AsH on 2008-10-31
There's a problem which is I cannot edit that file. It is protected or something doesn't overwrite.

---

### Post by geirha on 2008-10-31
> **Usta_AsH said:**
> There's a problem which is I cannot edit that file. It is protected or something doesn't overwrite.

It should only be writeable to root, so you need to use sudo to edit it. What's its permissions anyway?
```
ls -l /etc/apt/sources.list
```

---

