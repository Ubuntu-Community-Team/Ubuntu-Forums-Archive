---
title: "Backup before install Hardy"
date: 2008-07-24
forum: General Help
---

### Post by carverj on 2008-07-24
Hi,
   I am about to install Hardy Heron 64 bit desktop, and would like to backup my Gutsy personal data first in order to copy it back once complete.
Is it best to use tar for backing up /home?:

```
tar cvpzf backup.tgz /home
```

Or better to copy all:

```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

Thanks all.

---

### Post by hyper_ch on 2008-07-24
well, the /home folder contains your user stuff. the /etc folder contains some server-wide configs (like xorg.conf etc). If you run mysql you want to backup the databases.... if you run a webserver you might want to backup /var/www
....

---

