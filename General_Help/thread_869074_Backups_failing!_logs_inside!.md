---
title: "Backups failing! logs inside!"
date: 2008-07-24
forum: General Help
---

### Post by rugbert on 2008-07-24
```

0  3    * * 5   root    /bin/tar cpf /backupmnt/full/fri/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backupmnt --exclude=/mnt --exclude=/media --exclude=/sys /

```

its worked perfectly till about last week.

now it chooses random days to fully run. tuesday and friday I got my full 7.4 gigs but every other day caps out at about 1.4 gigs

the tail end of error.log gives me this:
> 
-- resuming normal operations
[Tue Jul 22 05:25:24 2008] [notice] caught SIGTERM, shutting down
[Tue Jul 22 05:25:34 2008] [notice] ModSecurity for Apache 2.1.2 configured
[Tue Jul 22 05:25:35 2008] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c configured -- resuming normal operations
[Wed Jul 23 05:25:20 2008] [notice] caught SIGTERM, shutting down
[Wed Jul 23 05:25:32 2008] [notice] ModSecurity for Apache 2.1.2 configured
[Wed Jul 23 05:25:33 2008] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c configured -- resuming normal operations
[Thu Jul 24 05:25:25 2008] [notice] caught SIGTERM, shutting down
[Thu Jul 24 05:25:36 2008] [notice] ModSecurity for Apache 2.1.2 configured
[Thu Jul 24 05:25:37 2008] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c configured -- resuming normal operations


so the apache server is restarting at 5:25 am, but that wouldnt stop the backup would it? it looks like it almost ALWAYS restarts about that time. just to be sure i changed today's backup to 3am and the backup failed even worse (not even a gig).

what other logs should I grab to help solve this problem?

---

### Post by rugbert on 2008-07-25
bump

---

