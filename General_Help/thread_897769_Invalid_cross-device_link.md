---
title: "Invalid cross-device link"
date: 2008-08-22
forum: General Help
---

### Post by ArsNatura on 2008-08-22
Hello,

I'm trying to do:
```
sudo ln /var/run/mysqld/mysqld.sock /var/spool/postfix/var/run/mysqld/mysqld.sock

```

But I have this error:
```
Invalid cross-device link
```

I think ***/var/run*** and ***/var/spool*** are in the same partition.

Can anybody help me? :confused:

Thanks a lot!

---

### Post by HalPomeranz on 2008-08-22
Actually on most Ubuntu systems /var/run is actually a separate partition:

```

$ **df /var/run /var/spool**
Filesystem           1K-blocks      Used Available Use% Mounted on
varrun                 1988620       164   1988456   1% /var/run
/dev/sda8              3937220    570184   3167032  16% /var

```

Have you tried using symlinks?

```

sudo ln -s /var/run/mysqld/mysqld.sock /var/spool/postfix/var/run/mysqld/mysqld.sock

```

symlinks will allow you to link files across partitions, but they may not work for this application.  Postfix may simply refuse to follow the symlink.

Are you trying to get Postfix to run chroot()ed or something?  symlinks definitely won't work in this case.

---

### Post by ArsNatura on 2008-08-22
It's true!

```

**$ df /var/run /var/spool**
Filesystem           1K-blocks      Used Available Use% Mounted on
varrun                  257724        76    257648   1% /var/run
/dev/sda1              7913216   1388292   6126112  19% /


```

Yes, I'm trying to get Postfix to run chroot()ed. The symlinks don't work for this purpose. Have you another solution?

Thanks again!

---

### Post by HalPomeranz on 2008-08-22
> **ArsNatura said:**
> 
Yes, I'm trying to get Postfix to run chroot()ed. The symlinks don't work for this purpose. Have you another solution?


The easiest thing to do would be to have Postfix talk to MySQL over the network on localhost:3306, rather than trying to communicate via the Unix domain socket.

Failing that, you might be able to configure MySQL to create a copy of  mysqld.sock under the chroot() area (you can do this with syslogd, for example).  I haven't ever tried to do this with MySQL, so I don't have a recipe for you unfortunately.

Failing that, you could simply reconfigure MySQL so that the default socket location was under the chroot() area.  Non-chroot() apps on the same machine should be able to access the socket in the new location.

---

### Post by ArsNatura on 2008-08-22
Finaly I've switched the connection mode, for use the TCP 3306 way and all work fine.
```

hosts=127.0.0.1

```

Thank you very much! :D

---

